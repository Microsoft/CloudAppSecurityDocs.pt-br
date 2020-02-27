---
title: Habilitar o coletor de logs por trás de um proxy-Cloud App Security | Microsoft Docs
description: Este artigo fornece informações sobre como habilitar o Cloud App Security Cloud Discovery coletor de logs por trás de um proxy.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 8/6/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 2b6d888c90a3e21ee98002372c16484f6a471610
ms.sourcegitcommit: d340917143d37ded0dd342a277a1b6ad267f9a7a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77618446"
---
# <a name="enable-the-log-collector-behind-a-proxy"></a>Habilitar o coletor de logs por trás de um proxy

Depois de configurar o coletor de logs, se você estiver executando por trás de um proxy, o coletor de logs poderá ter problemas para enviar dados para Cloud App Security. Isso pode acontecer porque o coletor de logs não confia na autoridade de certificação raiz do proxy e não é capaz de se conectar ao Microsoft Cloud App Security para recuperar sua configuração ou carregar os logs recebidos.

>[!NOTE]
> Para obter informações sobre como alterar os certificados usados pelo coletor de logs para syslog ou FTP e para resolver problemas de conectividade dos firewalls e proxies para o coletor de logs, consulte [configuração de FTP do coletor de logs](log-collector-ftp.md).
>

## <a name="set-up-the-log-collector-behind-a-proxy"></a>Configurar o coletor de logs por trás de um proxy

Certifique-se de que executou as etapas necessárias para executar o Docker em um computador Windows ou Linux e baixe com êxito a imagem do Docker Cloud App Security no computador. Para obter mais informações, consulte [Configurar o upload de log automático para relatórios contínuos](discovery-docker.md).

### <a name="validate-docker-log-collector-container-creation"></a>Validar a criação do contêiner do coletor de logs do Docker

No Shell, verifique se o contêiner foi criado e se está em execução usando o seguinte comando:

```bash
docker ps
```

![Docker PS](media/docker-1.png)

### <a name="copy-proxy-root-ca-certificate-to-the-container"></a>Copiar certificado de AC raiz de proxy para o contêiner

Em sua máquina virtual, copie o certificado de autoridade de certificação para o contêiner de Cloud App Security. No exemplo a seguir, o contêiner é chamado de *Ubuntu-LogCollector* e o certificado de autoridade de certificação é denominado *proxy-ca. CRT*.
Execute o comando no host do Ubuntu. Ele copia o certificado para uma pasta no contêiner em execução:

```bash
docker cp Proxy-CA.crt Ubuntu-LogCollector:/var/adallom/ftp/discovery
```

### <a name="set-the-configuration-to-work-with-the-ca-certificate"></a>Definir a configuração para trabalhar com o certificado de autoridade de certificação

1. Vá para o contêiner, usando o comando a seguir. Ele abrirá o bash no contêiner do coletor de logs:

    ```bash
    docker exec -it Ubuntu-LogCollector /bin/bash
    ```

2. Do bash dentro do contêiner, vá para a pasta Java *JRE* . Para evitar um erro de caminho relacionado à versão, use este comando:

    ```bash
    cd "$(find /opt/jdk/*/jre -name "bin" -printf '%h' -quit)"
    ```

3. Importe o certificado raiz que você copiou anteriormente, da pasta de *descoberta* para o repositório de chaves Java e defina uma senha. A senha padrão é "changeit". Para obter informações sobre como alterar a senha, consulte [como alterar a senha do repositório de chaves Java](#how-to-change-the-java-keystore-password).

    ```bash
    ./keytool --import --noprompt --trustcacerts --alias SelfSignedCert --file /var/adallom/ftp/discovery/Proxy-CA.crt --keystore ../lib/security/cacerts --storepass <password>
    ```

4. Valide se o certificado foi importado corretamente para o repositório de chaves da CA, usando o comando a seguir para procurar o alias fornecido durante a importação (*SelfSignedCert*):

    ```bash
    ./keytool --list --keystore ../lib/security/cacerts | grep self
    ```

    ![keytool](media/docker-2.png "keytool")

Você deve ver seu certificado de autoridade de certificação de proxy importado.

### <a name="set-the-log-collector-to-run-with-the-new-configuration"></a>Definir o coletor de logs para ser executado com a nova configuração

O contêiner agora está pronto.

Execute o comando **collector_config** usando o token de API que você usou durante a criação do coletor de logs:

![Token de API](media/docker-3.png "Token de API")

Ao executar o comando, especifique seu próprio token de API:

```bash
collector_config abcd1234abcd1234abcd1234abcd1234 ${CONSOLE} ${COLLECTOR}
```

![Atualização de configuração](media/docker-4.png "Atualização de configuração")

O coletor de logs agora é capaz de se comunicar com Cloud App Security. Depois de enviar dados para ele, o status será alterado de **íntegro** para **conectado** no portal de Cloud app Security.

![Status](media/docker-5.png "Status")

>[!NOTE]
> Se você precisar atualizar a configuração do coletor de logs para adicionar ou remover uma fonte de dados, por exemplo, normalmente precisará **excluir** o contêiner e executar as etapas anteriores novamente. Para evitar isso, você pode executar novamente a ferramenta de *collector_config* com o novo token de API gerado no portal de Cloud app Security.

## <a name="how-to-change-the-java-keystore-password"></a>Como alterar a senha do repositório de chaves Java

1. Interrompa o servidor do repositório de chaves Java.
1. Abra um shell bash dentro do contêiner e vá para a pasta *AppData/conf* .
1. Altere a senha do repositório de chaves do servidor usando este comando:

    ```bash
    keytool -storepasswd -new newStorePassword -keystore server.keystore
    -storepass changeit
    ```

    > [!NOTE]
    > A senha padrão do servidor é *changeit*.

1. Altere a senha do certificado usando este comando:

    ```bash
    keytool -keypasswd -alias server -keypass changeit -new newKeyPassword -keystore server.keystore -storepass newStorePassword
    ```

    > [!NOTE]
    > O alias do servidor padrão é *servidor*.

1. Em um editor de texto, abra o arquivo *Server-install\conf\server\secured-installed.Properties* e, em seguida, adicione as linhas de código a seguir e salve as alterações:
    1. Especifique a nova senha do repositório de chaves Java para o servidor: `server.keystore.password=newStorePassword`
    1. Especifique a nova senha de certificado para o servidor: `server.key.password=newKeyPassword`
1. Inicie o servidor.

## <a name="next-steps"></a>{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}

> [!div class="nextstepaction"]
> [Políticas de atividade do usuário](user-activity-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]

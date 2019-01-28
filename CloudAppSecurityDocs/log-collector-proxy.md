---
title: Habilitar o coletor de logs por trás de um proxy – Cloud App Security | Microsoft Docs
description: Este artigo fornece informações sobre como habilitar o coletor de logs do Cloud App Security Cloud Discovery por trás de um proxy.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/29/2019
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 6bde2a6c-60cc-4a7d-9e83-e8b81ac229b0
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: d69444a4baa4e861c1ffa14c081f77a584911431
ms.sourcegitcommit: c24732bc40350c3cf416640b7d15f3c6f7be371d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2019
ms.locfileid: "55086576"
---
# <a name="enable-the-log-collector-behind-a-proxy"></a>Habilitar o coletor de logs por trás de um proxy

Depois de configurar o coletor de logs, se você estiver executando por trás de um proxy, o coletor de logs poderá ter problemas para enviar dados ao Cloud App Security. Isso pode ser causado porque o coletor de logs não confia na autoridade de certificado raiz do proxy e não consegue se conectar ao Microsoft Cloud App Security para recuperar sua configuração ou carregar os logs recebidos.

>[!NOTE] 
> Saiba mais sobre como alterar os certificados usados pelo coletor de logs para Syslog ou FTP e como resolver problemas de conectividade de firewalls e proxies para o coletor de logs em [Solucionar problemas da implantação do Microsoft Cloud App Security Cloud Discovery](troubleshoot-docker.md).
>

## <a name="set-up-the-log-collector-behind-a-proxy"></a>Configurar o coletor de logs por trás de um proxy

Verifique se você executou as etapas necessárias, executou o Docker em um computador Windows ou Linux e fez o download da imagem do Docker do Cloud App Security corretamente na máquina. Saiba mais em [Configurar upload de log automático para relatórios contínuos](discovery-docker.md).

### <a name="validate-docker-log-collector-container-creation"></a>Validar a criação de contêiner do coletor de logs do Docker

No shell, verifique se o contêiner foi criado e está em execução usando o seguinte comando:

    bash
    docker ps


![docker ps](./media/docker-1.png "docker ps")

### <a name="copy-proxy-root-ca-certificate-to-the-container"></a>Copie o Certificado de Autoridade de Certificação raiz do proxy para o contêiner

De sua máquina virtual, copie o Certificado de Autoridade de Certificação para o contêiner do Cloud App Security. No exemplo a seguir, o contêiner é denominado *Ubuntu LogCollector* e o Certificado de Autoridade de Certificação é denominado *Proxy-CA.crt*.
Execute o comando no host do Ubuntu e copie o certificado para uma pasta no contêiner em execução:

    bash
    docker cp Proxy-CA.crt Ubuntu-LogCollector:/var/adallom/ftp/discovery


### <a name="set-the-configuration-to-work-with-the-ca-certificate"></a>Defina a configuração para trabalhar com o Certificado de Autoridade de Certificação

1. Vá para o contêiner, usando o comando a seguir. Ele abrirá o bash no contêiner do coletor de logs:

        bash
        docker exec -it Ubuntu-LogCollector /bin/bash

2. Do bash dentro do contêiner, vá para o diretório JRE do Java. Para evitar um erro de caminho relacionado com a versão, use este comando:

       bash
       cd 'find /opt/jdk/*/jre -iname bin'

3. Importe o certificado raiz que você copiou anteriormente da pasta *descoberta* para o repositório de chaves do Java e defina uma senha. A senha padrão é "changeit":

       bash
       ./keytool --import --noprompt --trustcacerts --alias SelfSignedCert --file /var/adallom/ftp/discovery/Proxy-CA.crt --keystore ../lib/security/cacerts --storepass changeit


4. Valide que o certificado foi importado corretamente para o repositório de chaves da Autoridade de Certificação, usando o comando a seguir para procurar o alias que você forneceu durante a importação (*SelfSignedCert*):

       bash
       ./keytool --list --keystore ../lib/security/cacerts | grep self


![keytool](./media/docker-2.png "keytool")

Você deve ver seu Certificado de Autoridade de Certificação importado do proxy.

### <a name="set-the-log-collector-to-run-with-the-new-configuration"></a>Definir o coletor de logs para ser executado com a nova configuração

O contêiner está pronto. 

Execute o comando **collector_config** usando o token da API que você usou durante a criação de seu coletor de logs:

![Token da API](./media/docker-3.png "Token da API")

Quando você executar o comando, especifique seu próprio token da API:

      bash
      collector_config abcd1234abcd1234abcd1234abcd1234 ${CONSOLE} ${COLLECTOR}


![Atualização da configuração](./media/docker-4.png "Atualização da configuração")

O coletor de logs consegue agora se comunicar com o Cloud App Security. Depois de enviar dados a ele, o status será alterado de **Íntegro** para **Conectado** no portal do Cloud App Security.

![Status](./media/docker-5.png "Status")

>[!NOTE]
> Se você precisar atualizar a configuração do coletor de logs, para adicionar ou remover uma fonte de dados, por exemplo, normalmente precisará **excluir** o contêiner e executar as etapas anteriores novamente. Para evitar isso, você pode executar novamente a ferramenta *collector_config* com o novo token da API gerado no portal do Cloud App Security.



 
  
## <a name="next-steps"></a>Próximas etapas 
[Políticas de atividade de usuário](user-activity-policies.md)   

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
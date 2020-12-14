---
title: Gerenciamento de coletor de logs avançado
description: Este artigo fornece informações sobre como as tarefas de gerenciamento avançadas para Cloud App Security coletores de log de Cloud Discovery.
ms.date: 12/14/2020
ms.topic: how-to
ms.openlocfilehash: dd8ab619f7284bde404bbe90a44d346595e2b99a
ms.sourcegitcommit: d3f243593f86e0f13a1fbc67702a99c23af5a45a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97386553"
---
# <a name="advanced-log-collector-management"></a>Gerenciamento de coletor de logs avançado

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Este artigo fornece informações sobre as seguintes opções de configuração avançadas para Cloud App Security coletores de log de Cloud Discovery:

- [Modificar a configuração de FTP do coletor de logs](#modify-the-log-collector-ftp-configuration)
- [Habilitar o coletor de logs por trás de um proxy](#enable-the-log-collector-behind-a-proxy)
- [Mover o coletor de logs para uma partição de dados diferente no Linux](#move-the-log-collector-to-a-different-data-partition-on-linux)
- [Inspecione o uso do disco do coletor de logs no Linux](#inspect-the-log-collector-disk-usage-on-linux)
- [Mover o coletor de logs para um host acessível](#move-the-log-collector-to-an-accessible-host)
- [Definir portas personalizadas para receptores de syslog e FTP para coletores de log no Linux](#define-custom-ports-for-syslog-and-ftp-receivers-for-log-collectors-on-linux)
- [Validar o formato de tráfego e de log recebido pelo coletor de logs no Linux](#validate-the-traffic-and-log-format-received-by-log-collector-on-linux)

## <a name="modify-the-log-collector-ftp-configuration"></a>Modificar a configuração de FTP do coletor de logs

Use estas etapas para modificar a configuração de seu Cloud App Security Cloud Discovery Docker.

### <a name="docker-deployment"></a>Implantação do Docker

Talvez seja necessário modificar a configuração para o Cloud App Security Cloud Discovery Docker.

#### <a name="changing-the-ftp-password"></a>Alterar a senha do FTP

1. Conecte-se ao host do coletor de logs.

1. Execute `docker exec -it <collector name> pure-pw passwd <ftp user>`

    1. Insira a nova senha.
    1. Insira a nova senha novamente para confirmação.

1. Execute o `docker exec -it <collector name> pure-pw mkdb` para aplicar a alteração.

    ![alterar a senha do FTP](media/log-collector-advanced-tasks/ftp-connect.png)

#### <a name="customize-certificate-files"></a>Personalizar arquivos de certificado

Siga este procedimento para personalizar os arquivos de certificado que você usa para conexões seguras com o Docker Cloud Discovery.

1. Abra um cliente de FTP e conecte-se ao coletor de logs.

    ![Conecte-se ao cliente de FTP](media/log-collector-advanced-tasks/ftp-connect.png)

1. Navegue até o diretório `ssl_update`.
1. Carregue novos arquivos de certificado no diretório `ssl_update` (os nomes são obrigatórios).

    ![Carregar arquivos de certificado](media/log-collector-advanced-tasks/new-certs.png)

    - **Para FTP:** apenas um arquivo é necessário. O arquivo tem os dados de chave e de certificado, nessa ordem, e é denominado **pure-ftpd.pem**.
    - **Para o syslog:** Três arquivos são necessários: **ca. pem**, * * Server-Key. pem e **Server-CERT. pem**. Se um dos arquivos estiver ausente, a atualização não ocorrerá.

1. Em uma janela de terminal, execute: `docker exec -t <collector name> update_certs` . O comando deve produzir uma saída semelhante à mostrada na captura de tela a seguir.

    ![Atualizar arquivos de certificado](media/log-collector-advanced-tasks/update-certs.png)

1. Em uma janela de terminal, execute: `docker exec <collector name> chmod -R 700 /etc/ssl/private/` .

## <a name="enable-the-log-collector-behind-a-proxy"></a>Habilitar o coletor de logs por trás de um proxy

Depois de configurar o coletor de logs, se você estiver executando por trás de um proxy, o coletor de logs poderá ter problemas para enviar dados ao Cloud App Security. Isso pode acontecer porque o coletor de logs não confia na autoridade de certificado raiz do proxy e não consegue se conectar ao Microsoft Cloud App Security para recuperar sua configuração ou carregar os logs recebidos.

Use estas etapas para habilitar o coletor de logs por trás de um proxy.

>[!NOTE]
> Para obter informações sobre como alterar os certificados usados pelo coletor de logs para syslog ou FTP e resolver problemas de conectividade de firewalls e proxies para o coletor de logs, consulte [Modificar a configuração de FTP do coletor de logs](#modify-the-log-collector-ftp-configuration).
>

### <a name="set-up-the-log-collector-behind-a-proxy"></a>Configurar o coletor de logs por trás de um proxy

Verifique se você executou as etapas necessárias, executou o Docker em um computador Windows ou Linux e fez o download da imagem do Docker do Cloud App Security corretamente na máquina. Saiba mais em [Configurar upload de log automático para relatórios contínuos](discovery-docker.md).

#### <a name="validate-docker-log-collector-container-creation"></a>Validar a criação de contêiner do coletor de logs do Docker

No shell, verifique se o contêiner foi criado e está em execução usando o seguinte comando:

```bash
docker ps
```

![docker ps](media/log-collector-advanced-tasks/docker-1.png)

#### <a name="copy-proxy-root-ca-certificate-to-the-container"></a>Copie o Certificado de Autoridade de Certificação raiz do proxy para o contêiner

De sua máquina virtual, copie o Certificado de Autoridade de Certificação para o contêiner do Cloud App Security. No exemplo a seguir, o contêiner é denominado *Ubuntu LogCollector* e o Certificado de Autoridade de Certificação é denominado *Proxy-CA.crt*.
Executar o comando no host do Ubuntu. Copia o certificado em uma pasta no contêiner em execução:

```bash
docker cp Proxy-CA.crt Ubuntu-LogCollector:/var/adallom/ftp/discovery
```

#### <a name="set-the-configuration-to-work-with-the-ca-certificate"></a>Defina a configuração para trabalhar com o Certificado de Autoridade de Certificação

1. Vá para o contêiner, usando o comando a seguir. Ele abrirá o bash no contêiner do coletor de logs:

    ```bash
    docker exec -it Ubuntu-LogCollector /bin/bash
    ```

1. Em uma janela bash dentro do contêiner, vá para a `jre` pasta Java. Para evitar um erro de caminho relacionado à versão, use este comando:

    ```bash
    cd "$(find /opt/jdk/*/jre -name "bin" -printf '%h' -quit)"
    cd bin
    ```

1. Importe o certificado raiz que você copiou anteriormente, da pasta de *descoberta* para o repositório de chaves Java e defina uma senha. A senha padrão é "changeit". Para obter informações sobre como alterar a senha, consulte [como alterar a senha do repositório de chaves Java](#how-to-change-the-java-keystore-password).

    ```bash
    ./keytool --import --noprompt --trustcacerts --alias SelfSignedCert --file /var/adallom/ftp/discovery/Proxy-CA.crt --keystore ../lib/security/cacerts --storepass <password>
    ```

1. Valide que o certificado foi importado corretamente para o repositório de chaves da Autoridade de Certificação, usando o comando a seguir para procurar o alias que você forneceu durante a importação (*SelfSignedCert*):

    ```bash
    ./keytool --list --keystore ../lib/security/cacerts | grep self
    ```

    ![keytool](media/log-collector-advanced-tasks/docker-2.png "keytool")

Você deve ver seu Certificado de Autoridade de Certificação importado do proxy.

#### <a name="set-the-log-collector-to-run-with-the-new-configuration"></a>Definir o coletor de logs para ser executado com a nova configuração

O contêiner está pronto.

Execute o comando **collector_config** usando o token da API que você usou durante a criação de seu coletor de logs:

![Token da API](media/log-collector-advanced-tasks/docker-3.png "Token da API")

Quando você executar o comando, especifique seu próprio token da API:

```bash
collector_config abcd1234abcd1234abcd1234abcd1234 ${CONSOLE} ${COLLECTOR}
```

![Atualização da configuração](media/log-collector-advanced-tasks/docker-4.png "Atualização da configuração")

O coletor de logs consegue agora se comunicar com o Cloud App Security. Depois de enviar dados a ele, o status será alterado de **Íntegro** para **Conectado** no portal do Cloud App Security.

![Status](media/log-collector-advanced-tasks/docker-5.png "Status")

>[!NOTE]
> Se você precisar atualizar a configuração do coletor de logs, para adicionar ou remover uma fonte de dados, por exemplo, normalmente precisará **excluir** o contêiner e executar as etapas anteriores novamente. Para evitar isso, você pode executar novamente a ferramenta *collector_config* com o novo token da API gerado no portal do Cloud App Security.

### <a name="how-to-change-the-java-keystore-password"></a>Como alterar a senha do repositório de chaves Java

1. Interrompa o servidor do repositório de chaves Java.

<!-- /opt/jdk/amazon-corretto-8.222.10.1-linux-x64/jre/lib/security -->

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

## <a name="move-the-log-collector-to-a-different-data-partition-on-linux"></a>Mover o coletor de logs para uma partição de dados diferente no Linux

Muitas empresas têm a necessidade de mover dados para uma partição separada. Use estas etapas para mover suas imagens do coletor de logs do Cloud App Security Docker para uma partição de dados em seu host Linux.

As etapas a seguir descrevem a movimentação de dados para uma partição chamada *datastore* e pressupõe que você já montou a partição.

> [!NOTE]
> Adicionar e configurar uma nova partição em seu host Linux não está no escopo deste guia.

![Lista de partições do Linux](media/log-collector-advanced-tasks/move-lc-new-partition-linux-disk-list.png)

1. Pare o serviço do Docker usando este comando:

    ```bash
    service docker stop
    ```

1. Mova os dados do coletor de logs para a nova partição usando este comando:

    ```bash
    mv /var/lib/docker /datastore/docker
    ```

1. Remova o antigo diretório de armazenamento do Docker (/var/lib/Docker) e crie um link simbólico para o novo diretório (/datastore/Docker).

    ```bash
    rm -rf /var/lib/docker && ln -s /datastore/docker /var/lib/
    ```

1. Inicie o serviço do Docker usando este comando:

    ```bash
    service docker start
    ```

1. Opcionalmente, verifique o status do seu coletor de logs usando este comando:

    ```bash
    docker ps
    ```

## <a name="inspect-the-log-collector-disk-usage-on-linux"></a>Inspecione o uso do disco do coletor de logs no Linux

Use estas etapas para examinar o local e o uso do disco do coletor de logs.

1. Identifique o caminho para o diretório em que os dados do coletor de logs são armazenados usando este comando:

    ```bash
    docker inspect <collector_name> | grep WorkDir
    ```

    ![Identificar o diretório do coletor de logs](media/log-collector-advanced-tasks/inspect-lc-linux-disk-usage-directory.png)

1. Obtenha o tamanho em disco do coletor de logs usando o caminho identificado sem o sufixo "/Work":

    ```bash
    du -sh /var/lib/docker/overlay2/<log_collector_id>/
    ```

    ![Obter tamanho do coletor de logs no disco](media/log-collector-advanced-tasks/inspect-lc-linux-disk-usage-size.png)

    > [!NOTE]
    > Se você precisar saber o tamanho em disco, poderá usar este comando: `docker ps -s`

## <a name="move-the-log-collector-to-an-accessible-host"></a>Mover o coletor de logs para um host acessível

Em ambientes regulamentados, o acesso a hubs do Docker em que a imagem do coletor de logs está hospedada pode ser bloqueado. Isso impede Cloud App Security de importar os dados do coletor de logs e podem ser resolvidos em mover a imagem do coletor de logs para um host acessível.

Use estas etapas para baixar a imagem do coletor de logs usando um computador que tenha acesso ao Hub do Docker e importe-o para o host de destino.

> [!NOTE]
>
> - A imagem baixada pode ser importada em seu repositório privado ou diretamente em seu host. As etapas a seguir orientarão você no download da sua imagem do coletor de logs para seu computador Windows e, em seguida, usará o WinSCP para mover o coletor de logs para o host de destino.
> - Para instalar o Docker em seu host, baixe o sistema operacional desejado:
>   - https://download.docker.com/linux/ubuntu
>   - https://download.docker.com/linux/centos/
>   - https://download.docker.com/linux/rhel/
>
> Após o download, use o [Guia de instalação offline](https://docs.docker.com/engine/install/binaries/) para instalar o sistema operacional.

Inicie o processo [exportando a imagem do coletor de logs](#export-the-log-collector-image-from-your-docker-hub) e, em seguida, [importe a imagem para o host de destino](#import-and-load-the-log-collector-image-to-your-destination-host).

### <a name="export-the-log-collector-image-from-your-docker-hub"></a>Exportar a imagem do coletor de logs do Hub do Docker

Use as etapas relevantes para o sistema operacional do Hub do Docker onde a imagem do coletor de logs está localizada.

#### <a name="exporting-the-image-on-linux"></a>Exportando a imagem no Linux

1. Em um computador Linux que tenha acesso ao Hub do Docker, execute o comando a seguir. Isso instalará o Docker e baixará a imagem do coletor de logs.

    ```bash
    curl -o /tmp/MCASInstallDocker.sh https://adaprodconsole.blob.core.windows.net/public-files/MCASInstallDocker.sh && chmod +x /tmp/MCASInstallDocker.sh; /tmp/MCASInstallDocker.sh
    ```

1. Exportar a imagem do coletor de logs.

    ```bash
    docker save --output /tmp/mcasLC.targ mcr.microsoft.com/mcas/logcollector
    chmod +r /tmp/mcasLC.tar
    ```

    > [!NOTE]
    > É importante usar o parâmetro de **saída** para gravar em um arquivo, em vez de *stdout*.

1. Baixe a imagem do coletor de logs em seu computador Windows em `C:\mcasLogCollector\` usando o WinSCP.

    ![Baixar o coletor de logs para um computador Windows](media/log-collector-advanced-tasks/move-lc-to-accessible-host-download-linux-winscp.png)

#### <a name="exporting-the-image-on-windows"></a>Exportando a imagem no Windows

1. Em um computador com Windows 10 que tenha acesso ao Hub do Docker, instale o [Docker desktop](https://docs.docker.com/docker-for-windows/install/).

1. Baixe a imagem do coletor de logs.

    ```dos
    docker login -u caslogcollector -p C0llector3nthusiast
    docker pull mcr.microsoft/mcas/logcollector
    ```

1. Exportar a imagem do coletor de logs.

    ```dos
    docker save --output C:\mcasLogCollector\mcasLC.targ mcr.microsoft.com/mcas/logcollector
    ```

    > [!NOTE]
    > É importante usar o parâmetro de **saída** para gravar em um arquivo, em vez de *stdout*.

### <a name="import-and-load-the-log-collector-image-to-your-destination-host"></a>Importar e carregar a imagem do coletor de logs para o host de destino

Use estas etapas para transferir a imagem exportada para o host de destino.

1. Carregue a imagem do coletor de logs em seu host de destino em `/tmp/` .

    ![Carregar o coletor de logs no host de destino](media/log-collector-advanced-tasks/move-lc-to-accessible-host-upload-host-winscp.png)

1. No host de destino, importe a imagem do coletor de logs para o repositório de imagens do Docker usando este comando:

    ```bash
    docker load --input /tmp/mcasLC.tar
    ```

    ![Importar imagem do coletor de logs para o repositório do Docker](media/log-collector-advanced-tasks/move-lc-to-accessible-host-import-docker-repo.png)

1. Opcionalmente, verifique se a importação foi concluída com êxito usando este comando:

    ```bash
    docker image ls
    ```

    ![Verificação da importação da imagem do coletor de logs bem-sucedida](media/log-collector-advanced-tasks/move-lc-to-accessible-host-verify-docker-image.png)

    Agora você pode continuar a [criar seu coletor de logs](discovery-docker.md) usando a imagem do host de destino.

## <a name="define-custom-ports-for-syslog-and-ftp-receivers-for-log-collectors-on-linux"></a>Definir portas personalizadas para receptores de syslog e FTP para coletores de log no Linux

Algumas organizações têm um requisito para definir portas personalizadas para serviços de syslog e FTP.
Ao adicionar uma fonte de dados, Cloud App Security coletores de log usa números de porta específicos para escutar logs de tráfego de uma ou mais fontes de dados.

A tabela a seguir lista as portas de escuta padrão para receptores:

| Tipo de receptor | Portas |
| --- | --- |
| syslog | \* UDP/514-UDP/51x<br />\* TCP/601-TCP/60x |
| FTP | \* TCP/21 |

Use estas etapas para definir portas personalizadas.

1. Em Cloud App Security, clique no ícone de configurações seguido por **coletores de log**.

1. Na guia **coletores de logs** , adicione ou edite um coletor de logs e, depois de atualizar as fontes de dados, copie o comando executar da caixa de diálogo.

    ![Copiar comando de execução do assistente do coletor de logs](media/log-collector-advanced-tasks/define-lc-custom-ports-copy-default-run-command.png)

    > [!NOTE]
    > Se usado conforme fornecido, o comando fornecido pelo assistente a seguir configura o coletor de logs para usar as portas 514/UDP e 515/UDP.
    >
    > ```bash
    > (echo <credentials>) | docker run --name LogCollector1 -p 514:514/udp -p 515:515/udp -p 21:21 -p 20000-20099:20000-20099 -e "PUBLICIP='10.0.0.100'" -e "PROXY=" -e "SYSLOG=true" -e "CONSOLE=machine.us2.portal.cloudappsecurity.com" -e "COLLECTOR=LogCollector1" --security-opt apparmor:unconfined --cap-add=SYS_ADMIN --restart unless-stopped -a stdin -i mcr.microsoft.com/mcas/logcollector starter
    > ```
    >
    > ![Executar comando do assistente do coletor de logs](media/log-collector-advanced-tasks/define-lc-custom-ports-default-run-command.png)

1. Antes de usar o comando no computador host, modifique o comando para usar suas portas personalizadas. Por exemplo, para configurar o coletor de logs para usar as portas UDP 414 e 415, altere o comando da seguinte maneira:

    ```bash
    (echo <credentials>) | docker run --name LogCollector1 -p 414:514/udp -p 415:515/udp -p 21:21 -p 20000-20099:20000-20099 -e "PUBLICIP='10.0.0.100'" -e "PROXY=" -e "SYSLOG=true" -e "CONSOLE=machine.us2.portal.cloudappsecurity.com" -e "COLLECTOR=LogCollector1" --security-opt apparmor:unconfined --cap-add=SYS_ADMIN --restart unless-stopped -a stdin -i mcr.microsoft.com/mcas/logcollector starter
    ```

    ![Executar comando personalizado em seu host](media/log-collector-advanced-tasks/define-lc-custom-ports-custom-run-command.png)

    > [!NOTE]
    > Somente o mapeamento do Docker é modificado. As portas atribuídas internamente não são alteradas, permitindo que você escolha qualquer porta de escuta no host.

## <a name="validate-the-traffic-and-log-format-received-by-log-collector-on-linux"></a>Validar o formato de tráfego e de log recebido pelo coletor de logs no Linux

Ocasionalmente, talvez seja necessário investigar problemas como os seguintes:

- **Os coletores de logs estão recebendo dados**: valide se os coletores de logs estão recebendo mensagens de syslog de seus dispositivos e não estão bloqueados por firewalls.
- Os **dados recebidos estão no formato de log correto**: valide o formato de log para ajudá-lo a solucionar problemas de análise de erros comparando o formato de log esperado pelo Cloud app Security e aquele enviado pelo seu dispositivo.

Use estas etapas para validar o tráfego recebido por coletores de logs.

1. Entre no servidor que hospeda o contêiner do Docker.

1. Valide se o coletor de logs está recebendo mensagens de syslog usando qualquer um dos seguintes métodos:

    - Usando *tcpdump* ou um comando semelhante para analisar o tráfego de rede na porta 514:

        ```bash
        tcpdump -Als0 port 514
        ```

        Se tudo estiver configurado corretamente, você deverá ver o tráfego de rede de seus dispositivos.

        ![Comando analisar o tráfego de rede tcpdump](media/log-collector-advanced-tasks/validate-traffic-and-log-format-tcpdump-analyze-traffic.png)

    - Usando *netcat* ou um comando semelhante para analisar o tráfego de rede no computador host:

        1. Instale o *netcat* e o *wget*.

        1. Baixe e, se necessário, unzip, um log de exemplo, da seguinte maneira:
            1. No portal de Cloud App Security, clique em **descobrir** e, em seguida, clique em **criar relatório de instantâneo**.
            1. Selecione a **Fonte de dados** da qual você deseja carregar os arquivos de log.
            1. Clique em **Exibir e verifique** e clique com o botão direito do mouse em **baixar log de exemplo** e copie o link de endereço de URL.
            1. Clique em **fechar**
            1. Clique em **Cancelar**.

        ```bash
        wget <URL_address_to_sample_log>
        ```

        1. Execute `netcat` para transmitir os dados para o coletor de logs.

        ```bash
        cat <path_to_downloaded_sample_log>.log | nc -w 0 localhost <datasource_port>
        ```

        Se o coletor estiver configurado corretamente, os dados de log estarão presentes no arquivo de mensagens e, logo depois disso, serão carregados no portal de Cloud App Security.

    - Inspecionando arquivos relevantes dentro do contêiner Cloud App Security Docker:
        1. Faça logon no contêiner usando este comando:

        ```bash
        docker exec -it <Container Name> bash
        ```

        1. Determine se as mensagens do syslog estão sendo gravadas no arquivo de mensagens usando este comando:

        ```bash
        cat /var/adallom/syslog/<your_log_collector_port>/messages
        ```

        Se tudo estiver configurado corretamente, você deverá ver o tráfego de rede de seus dispositivos.

        > [!NOTE]
        > Esse arquivo continuará a ser gravado até atingir 40 KB de tamanho.

        ![Comando analisar gato de tráfego de rede](media/log-collector-advanced-tasks/validate-traffic-and-log-format-cat-analyze-traffic.png)

1. Examine os logs que foram carregados para Cloud App Security no `/var/adallom/discoverylogsbackup` diretório.

    ![Examinar arquivos de log carregados](media/log-collector-advanced-tasks/validate-traffic-and-log-format-review-uploaded-logs.png)

1. Valide o formato de log recebido pelo coletor de logs, comparando as mensagens armazenadas no `/var/adallom/discoverylogsbackup` formato de log de exemplo fornecido no assistente de Cloud app Security **criar coletor de logs** .

> [!NOTE]
> Se você quiser usar seu próprio log de exemplo, mas não tiver acesso ao dispositivo, use os comandos a seguir para gravar a saída do arquivo de *mensagens* (localizado no diretório syslog do coletor do Ogon) em um arquivo local no host.
>
> ```bash
> docker exec CustomerLogCollectorName tail -f -q /var/adallom/syslog/<datasource_port>/messages > /tmp/log.log
> ```
>
> Compare o arquivo de saída ( `/tmp/log.log` ) com as mensagens armazenadas em `/var/adallom/discoverylogsbackup` .

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Implantar o Cloud Discovery](set-up-cloud-discovery.md)

> [!div class="nextstepaction"]
> [Políticas de atividade de usuário](user-activity-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]

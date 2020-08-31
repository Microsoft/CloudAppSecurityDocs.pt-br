---
title: Configurar o upload de log automático usando o Docker local
description: Este artigo descreve o processo de configuração do carregamento de log automático para relatórios contínuos no Cloud App Security usando um Docker no Linux em um servidor local.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 06/02/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 575028a9df41f8340c4a7a398fb05b5264ee93bb
ms.sourcegitcommit: 1554e381acc1e58de113d3b427f4e9de91b98488
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89148719"
---
# <a name="docker-on-linux-on-premises"></a>Docker no Linux local

*Aplica-se a: Microsoft Cloud App Security*

Você pode configurar o upload de log automático para relatórios contínuos no Cloud App Security usando um Docker em um servidor Ubuntu, Red Hat Enterprise Linux (RHEL) ou CentOS local.

## <a name="prerequisites"></a>Pré-requisitos

* sistema operacional:
    * Ubuntu 14, 4, 16, 4 e 18, 4
    * RHEL 7,2 ou superior
    * CentOS 7,2 ou superior

* Espaço em disco: 250 GB

* CPU: 2

* RAM: 4 GB

* Defina o firewall conforme descrito nos [Requisitos de rede](network-requirements.md#log-collector)

> [!NOTE]
> Se você tiver um coletor de logs existente e quiser removê-lo antes de implantá-lo novamente, ou se simplesmente quiser removê-lo, execute os seguintes comandos:
>
> ```console
> docker stop <collector_name>
> docker rm <collector_name>
> ```

## <a name="log-collector-performance"></a>Desempenho do coletor de logs

O coletor de logs pode lidar com êxito com a capacidade de logs de até 50 GB por hora. Os principais gargalos no processo de coleta de logs são:

* Largura de banda da rede – a largura de banda da rede determina a velocidade de upload do log.

* Desempenho de e/s da máquina virtual-determina a velocidade na qual os logs são gravados no disco do coletor de logs. O coletor de logs tem um mecanismo de segurança interno que monitora a taxa na qual os logs chegam e a compara à taxa de upload. Em casos de congestionamento, o coletor de logs começa a remover os arquivos de log. Se a configuração geralmente excede 50 GB por hora, recomendamos que você divida o tráfego entre vários coletores de logs.

## <a name="set-up-and-configuration"></a>Instalação e configuração  

### <a name="step-1--web-portal-configuration-define-data-sources-and-link-them-to-a-log-collector"></a>Etapa 1 — Configuração do portal da Web: definir fontes de dados e vinculá-las a um coletor de logs

1. Acesse a página de configurações **Upload automático de logs**.

    1. No portal do Cloud App Security, clique no ícone de configurações antes de **Coletores de log**.

    ![Ícone de configurações](media/settings-icon.png)

1. Para cada firewall ou proxy do qual você deseja fazer upload de logs, crie uma fonte de dados correspondente.

    1. Clique em **Adicionar fonte de dados**.  
    ![Adicionar uma fonte de dados](media/add-data-source.png)
    1. Atribua o **Nome** do proxy ou firewall.  
    ![Nome da fonte de dados](media/ubuntu1.png)
    1. Selecione o dispositivo na lista **Fonte**. Se você selecionar **Formato de log personalizado** para trabalhar com um dispositivo de rede que não esteja listado, confira [Trabalhando com o analisador de log personalizado](custom-log-parser.md) para obter instruções de configuração.
    1. Compare seu log com o exemplo do formato de log esperado. Se o formato de arquivo de log não corresponder a este exemplo, adicione sua fonte de dados como **Outros**.
    1. Definir o **Tipo de destinatário** como **FTP**, **FTPS**, **Syslog – UDP** ou **Syslog – TCP** ou **Syslog – TLS**.

    > [!NOTE]
    > A integração com protocolos de transferência segura (FTPS e Syslog – TLS) geralmente requer configuração adicional ou seu firewall/proxy.

    f. Repita esse processo para cada firewall e proxy cujos logs podem ser usados para detectar o tráfego na rede. É recomendável configurar uma fonte de dados dedicada por dispositivo de rede para permitir que você:

    * Monitore o status de cada dispositivo separadamente, para fins de investigação.
    * Explore o Shadow IT Discovery por dispositivo, se cada dispositivo for usado por um segmento de usuários diferente.

1. Vá para a guia **Coletores de logs** na parte superior.

    1. Clique em **Adicionar coletor de logs**.
    1. Dê um **nome**ao coletor de logs.
    1. Insira o **Endereço IP de host** do computador que você usará para implantar o Docker. O endereço IP do host pode ser substituído pelo nome do computador, caso haja um servidor DNS (ou equivalente) que resolverá o nome do host.
    1. Selecione todas as **fontes de dados** que você deseja conectar ao coletor e clique em **Atualizar** para salvar a configuração.

    ![Selecionar fontes de dados para se conectar](media/ubuntu2.png)

1. Mais informações sobre a implantação serão exibidas. **Copiar** o comando de execução na caixa de diálogo. Use o ícone Copiar para área de transferência. ![ícone Copiar para área de transferência](media/copy-icon.png)

1. **Exportar** a configuração de fonte de dados esperada. Essa configuração descreve como você deve definir a exportação de log em seus dispositivos.

    ![Crie o coletor de logs](media/windows7.png)

    > [!NOTE]
    >
    > * Um único coletor de logs pode lidar com várias fontes de dados.
    > * Copie o conteúdo da tela, pois você precisará das informações ao configurar o Coletor de Logs para se comunicar com o Cloud App Security. Se você selecionou Syslog, essa informação incluirá informações sobre qual porta o ouvinte do Syslog está escutando.
    > * Para usuários que enviam dados de log via FTP pela primeira vez, é recomendável alterar a senha para o usuário de FTP. Para obter mais informações, consulte [alterando a senha de FTP](log-collector-ftp.md#changing-the-ftp-password).

### <a name="step-2--on-premises-deployment-of-your-machine"></a>Etapa 2 – Implantação local de seu computador

As etapas a seguir descrevem a implantação no Ubuntu. As etapas de implantação para outras plataformas são ligeiramente diferentes.

1. Abra um terminal em seu computador Ubuntu.

1. Altere para privilégios de raiz usando o comando:`sudo -i`

1. Para ignorar um proxy na sua rede, execute os dois comandos a seguir:

    ```bash
    export http_proxy='<IP>:<PORT>' (e.g. 168.192.1.1:8888)
    export https_proxy='<IP>:<PORT>'
    ```

1. Se aceitar os [termos de licença de software](https://go.microsoft.com/fwlink/?linkid=862492), desinstale as versões antigas e instale o Docker CE executando o seguinte comando:

    ```bash
    curl -o /tmp/MCASInstallDocker.sh https://adaprodconsole.blob.core.windows.net/public-files/MCASInstallDocker.sh && chmod +x /tmp/MCASInstallDocker.sh; /tmp/MCASInstallDocker.sh
    ```

    > [!NOTE]
    > Se esse comando não conseguir validar seu certificado de proxy, execute o comando usando `curl -k` no início.

    ![Comando para instalar o Docker](media/ubuntu5.png)

1. Implante a imagem do coletor no computador de hospedagem importando a configuração do coletor. Importe a configuração copiando o comando de execução gerado no portal. Caso precise configurar um proxy, adicione o endereço IP do proxy e o número da porta. Por exemplo, se os detalhes de proxy são 192.168.10.1:8080, seu comando de execução atualizado é:

    ```bash
    (echo 6f19225ea69cf5f178139551986d3d797c92a5a43bef46469fcc997aec2ccc6f) | docker run --name MyLogCollector -p 21:21 -p 20000-20099:20000-20099 -e "PUBLICIP='192.2.2.2'" -e "PROXY=192.168.10.1:8080" -e "CONSOLE=tenant2.eu1-rs.adallom.com" -e "COLLECTOR=MyLogCollector" --security-opt apparmor:unconfined --cap-add=SYS_ADMIN --restart unless-stopped -a stdin -i microsoft/caslogcollector starter
    ```

    ![Crie o coletor de logs](media/windows7.png)

1. Verifique se o coletor está sendo executado corretamente com o seguinte comando: `docker logs <collector_name>`

Você verá a mensagem: **concluído com êxito!** 
 ![ Comando para verificar se o Docker está sendo executado corretamente](media/ubuntu8.png)

### <a name="step-3---on-premises-configuration-of-your-network-appliances"></a>Etapa 3 — Configuração local de seus dispositivos de rede

Configure seus firewalls de rede e proxies para exportar periodicamente os logs para a porta de syslog dedicada ou o diretório de FTP de acordo com as instruções na caixa de diálogo. Por exemplo:

```bash
BlueCoat_HQ - Destination path: \<<machine_name>>\BlueCoat_HQ\
```

### <a name="step-4---verify-the-successful-deployment-in-the-cloud-app-security-portal"></a>Etapa 4 — Verificar a implantação bem-sucedida no portal do Cloud App Security

Verifique o status do coletor na tabela **Coletor de logs** e verifique se o status é **Conectado**. Se for **Criado**, talvez a conexão do coletor de logs e a análise não tenham sido concluídas.

![Verificar a implantação bem-sucedida do coletor de logs](media/ubuntu9.png)

Você também pode acessar o **Log de governança** e verificar se os logs estão sendo carregados periodicamente no portal.

Se houver problemas durante a implantação, confira [Solução de problemas do Cloud Discovery](troubleshooting-cloud-discovery.md).

### <a name="optional---create-custom-continuous-reports"></a>Opcional – Criar relatórios contínuos personalizados

Verifique se os logs estão sendo carregados no Cloud App Security e se os relatórios são gerados. Após a verificação, crie relatórios personalizados. Crie relatórios de descoberta personalizados com base em grupos de usuários do Azure Active Directory. Por exemplo, caso deseje ver o uso de nuvem de seu departamento de marketing, importe o grupo de marketing usando o recurso Importar grupo de usuários. Em seguida, crie um relatório personalizado para esse grupo. Você também pode personalizar um relatório com base na marca do endereço IP ou intervalos de endereços IP.

1. No portal de Cloud App Security, sob as configurações engrenagem, selecione Cloud Discovery configurações e, em seguida, selecione **relatórios contínuos**.
1. Clique no botão **Criar relatório** e preencha os campos.
1. Em **Filtros**, você pode filtrar os dados de acordo com a fonte de dados, por [grupo de usuários importados](user-groups.md) ou por [marcas e intervalos de endereços IP](ip-tags.md).

![Relatório contínuo personalizado](media/custom-continuous-report.png)

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Configuração de FTP do coletor de logs](log-collector-ftp.md)

[!INCLUDE [Open support ticket](includes/support.md)]

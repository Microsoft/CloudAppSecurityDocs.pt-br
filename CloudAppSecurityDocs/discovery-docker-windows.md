---
title: Distribuir relatórios contínuos do Cloud App Security usando um Docker no Windows | Microsoft Docs
description: Este artigo descreve o processo de configuração de upload automático de log para relatórios contínuos no Cloud App Security usando um Docker no Windows em um servidor local.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 11/19/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: b22d84e2d640a596dda11e13d416f7fec558d377
ms.sourcegitcommit: aa227a88d09eff15953d10663386f85ff68095b3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74203463"
---
# <a name="docker-on-windows-on-premises"></a>Docker no Windows local

*Aplica-se ao: Microsoft Cloud App Security*

Você pode configurar o upload automático de log para relatórios contínuos no Cloud App Security usando um Docker no Windows.

## <a name="prerequisites"></a>Pré-requisitos

* OS: **Windows 10** (fall creators update) or Windows Server **version 1709+**

* Espaço em disco: 250 GB

* CPU: 2

* RAM: 4 GB

* Defina o firewall conforme descrito nos [Requisitos de rede](network-requirements.md#log-collector)

* A virtualização no sistema operacional deve ser habilitada com o Hyper-V

> [!IMPORTANT]
> A user must be signed in for Docker to collect logs. We recommend advising your Docker user's to disconnect without signing out.

> [!NOTE]
> If you have an existing log collector and want to remove it before deploying it again, or if you simply want to remove it, run the following commands:
>
> ```console
> docker stop <collector_name>
> docker rm <collector_name>
> ```

## <a name="log-collector-performance"></a>Desempenho do coletor de logs

O coletor de logs pode lidar com êxito com a capacidade de logs de até 50 GB por hora. Os principais gargalos no processo de coleta de logs são:

* Largura de banda da rede – a largura de banda da rede determina a velocidade de upload do log.

* Desempenho de E/S da máquina virtual – determina a velocidade em que os logs são gravados no disco do coletor de logs. O coletor de logs tem um mecanismo de segurança interno que monitora a taxa na qual os logs chegam e a compara à taxa de upload. Em casos de congestionamento, o coletor de logs começa a remover os arquivos de log. Se a configuração geralmente excede 50 GB por hora, recomendamos que você divida o tráfego entre vários coletores de logs.

## <a name="set-up-and-configuration"></a>Instalação e configuração

### <a name="step-1--web-portal-configuration-define-data-sources-and-link-them-to-a-log-collector"></a>Etapa 1 — Configuração do portal da Web: definir fontes de dados e vinculá-las a um coletor de logs

1. Acesse a página de configurações **Upload automático de logs**.

    1. No portal do Cloud App Security, clique no ícone de configurações antes de **Coletores de log**.

    ![ícone de configurações](media/settings-icon.png)

1. Para cada firewall ou proxy do qual você deseja fazer upload de logs, crie uma fonte de dados correspondente.

    1. Clique em **Adicionar fonte de dados**.  
    ![Add a data source](media/add-data-source.png)
    1. Atribua o **Nome** do proxy ou firewall.  
    ![ubuntu1](media/ubuntu1.png)
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
    1. Atribua um **nome** ao coletor de logs.
    1. Insira o **Endereço IP de host** do computador que você usará para implantar o Docker. O endereço IP do host pode ser substituído pelo nome do computador, caso haja um servidor DNS (ou equivalente) que resolverá o nome do host.
    1. Select all **Data sources** that you want to connect to the collector, and click **Update** to save the configuration.
    ![ubuntu2](media/ubuntu2.png)

1. Mais informações sobre a implantação serão exibidas. **Copiar** o comando de execução na caixa de diálogo. You can use the copy to clipboard icon, ![copy to clipboard icon](media/copy-icon.png). Você precisará dele mais tarde.

1. **Exportar** a configuração de fonte de dados esperada. Essa configuração descreve como você deve definir a exportação de log em seus dispositivos.

    ![Crie o coletor de logs](media/windows7.png)

    > [!NOTE]
    >
    > * Um único coletor de logs pode lidar com várias fontes de dados.
    > * Copie o conteúdo da tela, pois você precisará das informações ao configurar o Coletor de Logs para se comunicar com o Cloud App Security. Se você selecionou Syslog, essa informação incluirá informações sobre qual porta o ouvinte do Syslog está escutando.
    > * For users sending log data via FTP for the first time, we recommend changing the password for the FTP user. For more information, see [Changing the FTP password](log-collector-ftp.md#changing-the-ftp-password).

### <a name="step-2--on-premises-deployment-of-your-machine"></a>Etapa 2 – Implantação local de seu computador

As etapas a seguir descrevem a implantação no Windows. As etapas de implantação para outras plataformas são ligeiramente diferentes.

1. Abra um terminal do PowerShell como administrador em seu computador Windows.

1. Run the following command to download the Windows Docker installer PowerShell script file: `Invoke-WebRequest https://adaprodconsole.blob.core.windows.net/public-files/LogCollectorInstaller.ps1 -OutFile (Join-Path $Env:Temp LogCollectorInstaller.ps1)`

    To validate that the installer is signed by Microsoft, see [Validate installer signature](#validate-signature)

1. To enable PowerShell script execution, run `Set-ExecutionPolicy RemoteSigned`

1. Run: `& (Join-Path $Env:Temp LogCollectorInstaller.ps1)` This installs the Docker client on your machine. Durante a instalação do contêiner do coletor de logs, o computador será reiniciado duas vezes e você precisará fazer logon novamente. **Make sure the Docker client is set to use Linux containers.**

1. After each restart, open a PowerShell terminal as an administrator on your machine, re-run: `& (Join-Path $Env:Temp LogCollectorInstaller.ps1)`

1. Antes da conclusão da instalação, você precisará colar o comando de execução que copiou anteriormente.

1. Implante a imagem do coletor no computador de hospedagem importando a configuração do coletor. Importe a configuração copiando o comando de execução gerado no portal. Caso precise configurar um proxy, adicione o endereço IP do proxy e o número da porta. Por exemplo, se os detalhes de proxy são 192.168.10.1:8080, seu comando de execução atualizado é:

    ```console
    (echo db3a7c73eb7e91a0db53566c50bab7ed3a755607d90bb348c875825a7d1b2fce) | docker run --name MyLogCollector -p 21:21 -p 20000-20099:20000-20099 -e "PUBLICIP='192.168.1.1'" -e "PROXY=192.168.10.1:8080" -e "CONSOLE=mod244533.us.portal.cloudappsecurity.com" -e "COLLECTOR=MyLogCollector" --security-opt apparmor:unconfined --cap-add=SYS_ADMIN --restart unless-stopped -a stdin -i microsoft/caslogcollector starter
    ```

    ![Crie o coletor de logs](media/windows7.png)

1. Verifique se o coletor está sendo executado corretamente com o seguinte comando: `docker logs <collector_name>`

Você deverá ver a mensagem **Concluído com êxito!**

![ubuntu8](media/ubuntu8.png)

### <a name="step-3---on-premises-configuration-of-your-network-appliances"></a>Etapa 3 — Configuração local de seus dispositivos de rede

Configure os proxies e os firewalls de rede para periodicamente exportar logs para a porta do Syslog dedicada do diretório de FTP de acordo com as instruções na caixa de diálogo. Por exemplo:

```console
BlueCoat_HQ - Destination path: \<<machine_name>>\BlueCoat_HQ\
```

### <a name="step-4---verify-the-successful-deployment-in-the-cloud-app-security-portal"></a>Etapa 4 — Verificar a implantação bem-sucedida no portal do Cloud App Security

Verifique o status do coletor na tabela **Coletor de logs** e verifique se o status é **Conectado**. Se for **Criado**, talvez a conexão do coletor de logs e a análise não tenham sido concluídas.

![ubuntu9](media/ubuntu9.png)

Você também pode acessar o **Log de governança** e verificar se os logs estão sendo carregados periodicamente no portal.

Se houver problemas durante a implantação, confira [Solução de problemas do Cloud Discovery](troubleshooting-cloud-discovery.md).

### Opcional – criar relatórios contínuos personalizados <a name="continuous-reports"></a>

Verifique se os logs estão sendo carregados no Cloud App Security e se os relatórios são gerados. Após a verificação, crie relatórios personalizados. Crie relatórios de descoberta personalizados com base em grupos de usuários do Azure Active Directory. Por exemplo, caso deseje ver o uso de nuvem de seu departamento de marketing, importe o grupo de marketing usando o recurso Importar grupo de usuários. Em seguida, crie um relatório personalizado para esse grupo. Você também pode personalizar um relatório com base na marca do endereço IP ou intervalos de endereços IP.

1. No portal do Cloud App Security, na engrenagem Configurações, selecione Configurações do Cloud Discovery e, em seguida, **Relatórios contínuos**.
1. Clique no botão **Criar relatório** e preencha os campos.
1. Em **Filtros**, você pode filtrar os dados de acordo com a fonte de dados, por [grupo de usuários importados](user-groups.md) ou por [marcas e intervalos de endereços IP](ip-tags.md).

    ![Relatório contínuo personalizado](media/custom-continuous-report.png)

### Opcional – Validar a assinatura do instalador <a name="validate-signature"></a>

Para verificar se o instalador do Docker é assinado pela Microsoft:

1. Clique com o botão direito do mouse no arquivo e selecione **Propriedades**.
1. Clique em **Assinaturas Digitais** e verifique se a mensagem **Esta assinatura digital está correta** é exibida.
1. Verifique se **Microsoft Corporation** está listada como a única entrada em **Nome do signatário**.

    ![Assinatura digital válida](media/digital-signature-successful.png)

Se a assinatura digital não for válida, ela indicará **Esta assinatura digital não é válida**:

![Assinatura digital não válida](media/digital-signature-unsuccessful.png)

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Log collector FTP configuration](log-collector-ftp.md)

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/)

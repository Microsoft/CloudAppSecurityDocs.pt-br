---
title: Distribuir relatórios contínuos para Cloud App Security usando um Docker no Windows | Microsoft Docs
description: Este artigo descreve o processo de configuração do carregamento de log automático para relatórios contínuos no Cloud App Security usando um Docker no Windows em um servidor local.
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
ms.openlocfilehash: 9122a5c5cdde5f2a1ed02946970825b75155acc2
ms.sourcegitcommit: 4f3883a9e85d0aaf2802b10433b221c3f1838d88
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79285580"
---
# <a name="docker-on-windows-on-premises"></a>Docker no Windows local

*Aplica-se a: Microsoft Cloud App Security*

Você pode configurar o upload de log automático para relatórios contínuos no Cloud App Security usando um Docker no Windows.

## <a name="prerequisites"></a>Prerequisites

* Sistema operacional: **Windows 10** (atualização para criadores de outono), Windows Server **versão 1709 +** (SAC) ou **Windows Server 2019 (LTSC)**

* Espaço em disco: 250 GB

* CPU: 2

* RAM: 4 GB

* Defina o firewall conforme descrito em [requisitos de rede](network-requirements.md#log-collector)

* A virtualização no sistema operacional deve ser habilitada com o Hyper-V

> [!IMPORTANT]
> Um usuário deve estar conectado para que o Docker colete logs. Recomendamos que os usuários do Docker se desconectem sem sair.

> [!NOTE]
> Se você tiver um coletor de logs existente e quiser removê-lo antes de implantá-lo novamente, ou se simplesmente quiser removê-lo, execute os seguintes comandos:
>
> ```console
> docker stop <collector_name>
> docker rm <collector_name>
> ```

## <a name="log-collector-performance"></a>Desempenho do coletor de logs

O coletor de logs pode lidar com êxito com a capacidade de logs de até 50 GB por hora. Os principais gargalos no processo de coleta de logs são:

* Largura de banda de rede-sua largura de banda de rede determina a velocidade de carregamento do log.

* Desempenho de e/s da máquina virtual-determina a velocidade na qual os logs são gravados no disco do coletor de logs. O coletor de logs tem um mecanismo de segurança interno que monitora a taxa na qual os logs chegam e a compara à taxa de upload. Em casos de congestionamento, o coletor de logs começa a remover os arquivos de log. Se a configuração normalmente excede 50 GB por hora, é recomendável dividir o tráfego entre vários coletores de logs.

## <a name="set-up-and-configuration"></a>Instalação e configuração

### <a name="step-1--web-portal-configuration-define-data-sources-and-link-them-to-a-log-collector"></a>Etapa 1 — Configuração do portal da Web: definir fontes de dados e vinculá-las a um coletor de logs

1. Vá para a página Configurações de **carregamento de log automático** .

    1. No portal de Cloud App Security, clique no ícone de configurações seguido por **coletores de log**.

    ![ícone de configurações](media/settings-icon.png)

1. Para cada firewall ou proxy do qual você deseja carregar logs, crie uma fonte de dados correspondente.

    1. Clique em **Adicionar fonte de dados**.  
    ![adicionar uma fonte de dados](media/add-data-source.png)
    1. Atribua o **Nome** do proxy ou firewall.  
    ![ubuntu1](media/ubuntu1.png)
    1. Selecione o dispositivo na lista **Fonte**. Se você selecionar o **formato de log personalizado** para trabalhar com um dispositivo de rede que não está listado, consulte [trabalhando com o Log Parser personalizado](custom-log-parser.md) para obter instruções de configuração.
    1. Compare seu log com o exemplo do formato de log esperado. Se o formato do arquivo de log não corresponder a este exemplo, você deverá adicionar sua fonte de dados como **outra**.
    1. Defina o **Tipo de destinatário** como **FTP**, **FTPS**, **Syslog – UDP** ou **Syslog – TCP** ou **Syslog – TLS**.

    > [!NOTE]
    > A integração com protocolos de transferência segura (FTPS e Syslog – TLS) geralmente requer seu firewall/proxy ou configurações adicionais.

    f. Repita esse processo para cada firewall e proxy cujos logs podem ser usados para detectar o tráfego na rede. É recomendável configurar uma fonte de dados dedicada por dispositivo de rede para permitir que você:

    * Monitore o status de cada dispositivo separadamente, para fins de investigação.
    * Explore Shadow IT Discovery por dispositivo, se cada dispositivo for usado por um segmento de usuário diferente.

1. Vá para a guia **Coletores de logs** na parte superior.

    1. Clique em **Adicionar coletor de logs**.
    1. Atribua um **nome** ao coletor de logs.
    1. Insira o **endereço IP do host** do computador que você usará para implantar o Docker. O endereço IP do host pode ser substituído pelo nome do computador, se houver um servidor DNS (ou equivalente) que resolverá o nome do host.
    1. Selecione todas as **fontes de dados** que você deseja conectar ao coletor e clique em **Atualizar** para salvar a configuração.
    ![ubuntu2](media/ubuntu2.png)

1. Mais informações sobre a implantação serão exibidas. **Copie** o comando de execução da caixa de diálogo. Você pode usar o ícone Copiar para área de transferência, ![ícone Copiar para área de transferência](media/copy-icon.png). Você precisará disso mais tarde.

1. **Exporte** a configuração de fonte de dados esperada. Essa configuração descreve como você deve definir a exportação de log em seus dispositivos.

    ![Criar coletor de logs](media/windows7.png)

    > [!NOTE]
    >
    > * Um único coletor de logs pode lidar com várias fontes de dados.
    > * Copie o conteúdo da tela, pois você precisará das informações ao configurar o Coletor de Logs para se comunicar com o Cloud App Security. Se você selecionou Syslog, essa informação incluirá informações sobre qual porta o ouvinte do Syslog está escutando.
    > * Para usuários que enviam dados de log via FTP pela primeira vez, é recomendável alterar a senha para o usuário de FTP. Para obter mais informações, consulte [alterando a senha de FTP](log-collector-ftp.md#changing-the-ftp-password).

### <a name="step-2--on-premises-deployment-of-your-machine"></a>Etapa 2 – implantação local de seu computador

As etapas a seguir descrevem a implantação no Windows. As etapas de implantação para outras plataformas são ligeiramente diferentes.

1. Abra um terminal do PowerShell como administrador em seu computador Windows.

1. Execute o seguinte comando para baixar o arquivo de script do Windows Docker Installer PowerShell: `Invoke-WebRequest https://adaprodconsole.blob.core.windows.net/public-files/LogCollectorInstaller.ps1 -OutFile (Join-Path $Env:Temp LogCollectorInstaller.ps1)`

    Para validar que o instalador é assinado pela Microsoft, consulte [validar assinatura do instalador](#validate-signature)

1. Para habilitar a execução de script do PowerShell, execute `Set-ExecutionPolicy RemoteSigned`

1. Execute: `& (Join-Path $Env:Temp LogCollectorInstaller.ps1)` isso instala o cliente do Docker em seu computador. Enquanto o contêiner do coletor de logs estiver instalado, o computador será reiniciado duas vezes e você precisará fazer logon novamente. **Verifique se o cliente do Docker está definido para usar contêineres do Linux.**

1. Após cada reinicialização, abra um terminal do PowerShell como administrador em seu computador e execute novamente: `& (Join-Path $Env:Temp LogCollectorInstaller.ps1)`

1. Antes da conclusão da instalação, você precisará colar o comando de execução copiado anteriormente.

1. Implante a imagem do coletor no computador de hospedagem importando a configuração do coletor. Importe a configuração copiando o comando de execução gerado no Portal. Se você precisar configurar um proxy, adicione o endereço IP do proxy e o número da porta. Por exemplo, se os detalhes de proxy são 192.168.10.1:8080, o comando de execução atualizado é:

    ```console
    (echo db3a7c73eb7e91a0db53566c50bab7ed3a755607d90bb348c875825a7d1b2fce) | docker run --name MyLogCollector -p 21:21 -p 20000-20099:20000-20099 -e "PUBLICIP='192.168.1.1'" -e "PROXY=192.168.10.1:8080" -e "CONSOLE=mod244533.us.portal.cloudappsecurity.com" -e "COLLECTOR=MyLogCollector" --security-opt apparmor:unconfined --cap-add=SYS_ADMIN --restart unless-stopped -a stdin -i microsoft/caslogcollector starter
    ```

    ![Criar coletor de logs](media/windows7.png)

1. Verifique se o coletor está sendo executado corretamente com o seguinte comando: `docker logs <collector_name>`

Você verá a mensagem: **Concluído com êxito!**

![ubuntu8](media/ubuntu8.png)

### <a name="step-3---on-premises-configuration-of-your-network-appliances"></a>Etapa 3-configuração local de seus dispositivos de rede

Configure seus firewalls de rede e proxies para exportar logs periodicamente para a porta de syslog dedicada do diretório de FTP de acordo com as instruções na caixa de diálogo. Por exemplo:

```console
BlueCoat_HQ - Destination path: \<<machine_name>>\BlueCoat_HQ\
```

### <a name="step-4---verify-the-successful-deployment-in-the-cloud-app-security-portal"></a>Etapa 4-verificar a implantação bem-sucedida no portal de Cloud App Security

Verifique o status do coletor na tabela **Coletor de logs** e verifique se o status é **Conectado**. Se ele for **criado**, será possível que a conexão do coletor de logs e a análise não tenham sido concluídas.

![ubuntu9](media/ubuntu9.png)

Você também pode ir para o **log de governança** e verificar se que os logs estão sendo carregados periodicamente no portal.

Se você tiver problemas durante a implantação, consulte [solução de problemas Cloud Discovery](troubleshooting-cloud-discovery.md).

### Opcional-criar relatórios contínuos personalizados<a name="continuous-reports"></a>

Verifique se os logs estão sendo carregados para Cloud App Security e se os relatórios são gerados. Após a verificação, crie relatórios personalizados. Você pode criar relatórios de descoberta personalizados com base em grupos de usuários Azure Active Directory. Por exemplo, se você quiser ver o uso da nuvem de seu departamento de marketing, importe o grupo de marketing usando o recurso importar grupo de usuários. Em seguida, crie um relatório personalizado para esse grupo. Você também pode personalizar um relatório com base na marca do endereço IP ou intervalos de endereços IP.

1. No portal de Cloud App Security, sob as configurações engrenagem, selecione Cloud Discovery configurações e, em seguida, selecione **relatórios contínuos**.
1. Clique no botão **Criar relatório** e preencha os campos.
1. Em **Filtros**, você pode filtrar os dados de acordo com a fonte de dados, por [grupo de usuários importados](user-groups.md) ou por [marcas e intervalos de endereços IP](ip-tags.md).

    ![Relatório contínuo personalizado](media/custom-continuous-report.png)

### Opcional – validar assinatura do instalador<a name="validate-signature"></a>

Para certificar-se de que o instalador do Docker seja assinado pela Microsoft:

1. Clique com o botão direito do mouse no arquivo e selecione **Propriedades**.
1. Clique em **assinaturas digitais** e verifique se ela diz que **esta assinatura digital está ok**.
1. Verifique se a **Microsoft Corporation** está listada como a única entrada em **nome do assinante**.

    ![Assinatura digital válida](media/digital-signature-successful.png)

Se a assinatura digital não for válida, ela dirá que **esta assinatura digital não é válida**:

![Assinatura digital inválida](media/digital-signature-unsuccessful.png)

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Configuração de FTP do coletor de logs](log-collector-ftp.md)

[!INCLUDE [Open support ticket](includes/support.md)]

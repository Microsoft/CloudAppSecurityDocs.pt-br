---
title: Requisitos de rede – Cloud App Security | Microsoft Docs
description: Este artigo descreve os endereços IP e portas que você precisa abrir para trabalhar com o Cloud App Security.
keywords: ''
author: ShlomoSagir-MS
ms.author: shsagir
manager: ShlomoSagir-MS
ms.date: 7/16/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 4de606f2-a09e-4e48-a578-e223de8b5e69
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 48d13da7ca266c8a2a8054bb810aeba3bd50955a
ms.sourcegitcommit: 0945480ebb18f89b8cc3a3d5ead135ba53b04bfd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/18/2019
ms.locfileid: "68309068"
---
# <a name="network-requirements"></a>Requisitos de rede

*Aplica-se a: Microsoft Cloud App Security*

Este artigo fornece uma lista de portas e endereços IP que você precisa para permitir e permitir que a lista funcione com Microsoft Cloud App Security.

## <a name="view-your-data-center"></a>Exibir seu data center

Alguns dos requisitos abaixo dependem em que data center você está conectado. 

Para ver qual data center você está se conectando, execute as seguintes etapas:

1. No portal do Cloud App Security, clique no **ícone de ponto de interrogação** na barra de menus. Em seguida, selecione **Sobre**. 

    ![clique em Sobre](./media/about-menu.png)

2. Na tela da versão do Cloud App Security, você pode ver a região e o data center.

    ![Exibir seu data center](./media/data-center.png)

## <a name="portal-access"></a>Acesso ao portal

Para acessar o portal de Cloud App Security, adicione a **porta de saída 443** para os seguintes endereços IP e nomes DNS à lista de permissões do firewall:  

    portal.cloudappsecurity.com
    *.portal.cloudappsecurity.com
    cdn.cloudappsecurity.com
    https://adaproddiscovery.azureedge.net 
    *.s-microsoft.com
    *.msecnd.net
    dev.virtualearth.net
    *.cloudappsecurity.com
    flow.microsoft.com
    static2.sharepointonline.com
    dc.services.visualstudio.com
    *.blob.core.windows.net

Além disso, os itens a seguir devem estar na lista de permissões, dependendo do data center usado:
> [!div class="mx-tableFixed"]
> 
> |Data center|Endereços IP|Nome DNS|
> |----|----|----|
> |US1|13.64.26.88<br>13.64.29.32<br>13.80.125.22<br>13.91.91.243<br>40.74.1.235<br>40.74.6.204<br>51.143.58.207<br>52.137.89.147<br>52.183.75.62|\*.us.portal.cloudappsecurity.com|
> |US2|13.80.125.22<br>20.36.222.59<br>20.36.222.60<br>40.74.1.235<br>40.74.6.204<br>51.143.58.207<br>52.137.89.147<br>52.183.75.62<br>52.184.165.82|\*.us2.portal.cloudappsecurity.com|
> |US3|13.80.125.22<br>40.74.1.235<br>40.74.6.204<br>40.90.218.196<br>40.90.218.198<br>51.143.58.207<br>52.137.89.147<br>52.183.75.62|*.us3.portal.cloudappsecurity.com|
> |EU1|13.80.125.22<br>40.119.154.72<br>40.74.1.235<br>40.74.6.204<br>51.143.58.207<br>52.137.89.147<br>52.157.238.58<br>52.174.56.180<br>52.183.75.62|\*.eu.portal.cloudappsecurity.com<|
> |EU2|13.80.125.22<br>40.74.1.235<br>40.74.6.204<br>40.81.156.154<br>40.81.156.156<br>51.143.58.207<br>52.137.89.147<br>52.183.75.62|*.eu2.portal.cloudappsecurity.com|

> [!NOTE]
> Em vez de um caractere curinga (\*), você pode abrir somente a URL específica do locatário, por exemplo, de acordo com a captura de tela acima, você poderá abrir mod244533.us.portal.cloudappsecurity.com

## <a name="siem-agent-connection"></a>Conexão do agente SIEM

Para permitir que Cloud App Security se conectem ao SIEM, adicione a **porta de saída 443** para os seguintes endereços IP à lista de permissões do firewall:  

> [!div class="mx-tableFixed"]
> 
> |Data center|Endereços IP|  
> |----|----|
> |US1|13.64.26.88<br>13.64.29.32<br>13.80.125.22<br>13.91.91.243<br>40.74.1.235<br>40.74.6.204<br>51.143.58.207<br>52.137.89.147<br>52.183.75.62|
> |US2|13.80.125.22<br>20.36.222.59<br>20.36.222.60<br>40.74.1.235<br>40.74.6.204<br>51.143.58.207<br>52.137.89.147<br>52.183.75.62<br>52.184.165.82|
> |US3|13.80.125.22<br>40.74.1.235<br>40.74.6.204<br>40.90.218.196<br>40.90.218.198<br>51.143.58.207<br>52.137.89.147<br>52.183.75.62|
> |EU1|13.80.125.22<br>40.119.154.72<br>40.74.1.235<br>40.74.6.204<br>51.143.58.207<br>52.137.89.147<br>52.157.238.58<br>52.174.56.180<br>52.183.75.62|
> |EU2|13.80.125.22<br>40.74.1.235<br>40.74.6.204<br>40.81.156.154<br>40.81.156.156<br>51.143.58.207<br>52.137.89.147<br>52.183.75.62|

> [!NOTE]
> Se você não especificou um proxy ao configurar o agente Siem Cloud app Security, precisará permitir conexões http://ocsp.msocsp.com/ http e OCSP.DigiCert.com na porta 80. Isso é usado para verificar o status de revogação de certificado ao se conectar ao portal do Cloud App Security.

## <a name="app-connector"></a>Conector de aplicativo

Para alguns aplicativos de terceiros serem acessados pelo Cloud App Security, esses endereços IP podem ser usados. Os endereços IP permitem ao Cloud App Security coletar logs e fornecer acesso ao console do Cloud App Security.

> [!NOTE]
>Você pode ver esses endereços IP nos logs de atividades do fornecedor porque o Cloud App Security executa as ações de governança e as varreduras desses endereços IP.

Para se conectar a aplicativos de terceiros, habilite o Cloud App Security para se conectar nesses endereços IP:

> [!div class="mx-tableFixed"]
> 
> |Data center|Endereços IP||
> |----|----|----|
> |US1|104.209.35.177<br>13.64.196.27<br>13.64.198.19<br>13.64.198.97<br>13.64.199.41<br>13.64.26.88<br>13.64.29.32<br>13.64.30.117<br>13.64.30.118<br>13.64.30.76|13.64.31.116<br>13.86.176.189<br>13.86.176.211<br>13.91.61.249<br>13.91.91.243<br>13.91.98.185<br>13.93.216.68<br>13.93.233.42<br>40.118.211.172<br><br>|
> |US2|104.46.116.211<br>104.46.116.211<br>104.46.121.72<br>104.46.121.72<br>104.46.122.189<br>104.46.122.189<br>20.36.222.59<br>20.36.222.60<br>40.67.152.91|40.67.154.160<br>40.67.155.146<br>40.67.159.55<br>40.84.2.83<br>40.84.4.119<br>40.84.4.93<br>52.184.165.82<br>52.232.224.227<br>52.232.225.84|
> |US3|40.90.218.196<br>40.90.218.197<br>40.90.218.198<br>40.90.218.203<br>40.90.220.190<br>40.90.220.196<br>51.143.120.236<br>51.143.120.242||
> |EU1|13.80.22.71<br>13.95.29.177<br>13.95.30.46<br>40.114.217.8<br>40.114.217.8<br>40.115.24.65<br>40.115.24.65<br>40.115.25.50<br>40.115.25.50|40.119.154.72<br>40.67.219.133<br>51.105.179.157<br>52.157.232.110<br>52.157.233.133<br>52.157.233.92<br>52.157.238.58<br>52.157.239.110<br>52.174.56.180|
> |EU2|40.81.152.171<br>40.81.152.172<br>40.81.156.153<br>40.81.156.154<br>40.81.156.155<br>40.81.156.156<br>51.145.108.227<br>51.145.108.250|

## <a name="third-party-dlp-integration"></a>Integração do DLP de terceiros

Para habilitar o Cloud App Security a enviar dados por meio de seu stunnel para seu servidor ICAP, abra o firewall de rede de perímetro para esses endereços IP com um número da porta de origem dinâmico. 

1. **Endereços de origem** – esses endereços devem ser colocados na lista de permissões conforme listado acima para aplicativos de terceiros de conector de API
2. **Porta TCP de origem** – dinâmica
3. **Endereços de destino** – um ou dois endereços IP do stunnel conectado ao servidor ICAP externo
4. **Porta TCP de destino** – conforme definido em sua rede

> [!NOTE] 
> -  Por padrão, o número da porta stunnel é definido como 11344. Você pode alterá-lo para outra porta, se necessário, mas certifique-se de anotar o novo número da porta.
> - Você pode ver esses endereços IP nos logs de atividades do fornecedor porque o Cloud App Security executa as ações de governança e as varreduras desses endereços IP.

Para se conectar a aplicativos de terceiros e integrar soluções de DLP externas, habilite o Cloud App Security para se conectar nesses endereços IP:

> [!div class="mx-tableFixed"]
> 
> |Data center|Endereços IP||
> |----|----|----|
> |US1|104.209.35.177<br>13.64.196.27<br>13.64.198.19<br>13.64.198.97<br>13.64.199.41<br>13.64.26.88<br>13.64.29.32<br>13.64.30.117<br>13.64.30.118<br>13.64.30.76|13.64.31.116<br>13.86.176.189<br>13.86.176.211<br>13.91.61.249<br>13.91.91.243<br>13.91.98.185<br>13.93.216.68<br>13.93.233.42<br>40.118.211.172<br><br>|
> |US2|104.46.116.211<br>104.46.116.211<br>104.46.121.72<br>104.46.121.72<br>104.46.122.189<br>104.46.122.189<br>20.36.222.59<br>20.36.222.60<br>40.67.152.91|40.67.154.160<br>40.67.155.146<br>40.67.159.55<br>40.84.2.83<br>40.84.4.119<br>40.84.4.93<br>52.184.165.82<br>52.232.224.227<br>52.232.225.84|
> |US3|40.90.218.196<br>40.90.218.197<br>40.90.218.198<br>40.90.218.203<br>40.90.220.190<br>40.90.220.196<br>51.143.120.236<br>51.143.120.242||
> |EU1|13.80.22.71<br>13.95.29.177<br>13.95.30.46<br>40.114.217.8<br>40.114.217.8<br>40.115.24.65<br>40.115.24.65<br>40.115.25.50<br>40.119.154.72|40.67.219.133<br>51.105.179.157<br>52.157.232.110<br>52.157.233.133<br>52.157.233.92<br>52.157.238.58<br>52.157.239.110<br>52.174.56.180<br><br>|
> |EU2|40.81.152.171<br>40.81.152.172<br>40.81.156.153<br>40.81.156.154<br>40.81.156.155<br>40.81.156.156<br>51.145.108.227<br>51.145.108.250||

## <a name="mail-server"></a>Servidor de emails

Para habilitar as notificações a serem enviadas do modelo e das configurações padrão, adicione esses endereços IP à lista de permissões anti-spam. Os endereços IP de email dedicado do Cloud App Security são:

- 65.55.234.192/26
- 207.46.200.0/27
- 65.55.52.224/27
- 94.245.112.0/27
- 111.221.26.0/27
- 207.46.50.192/26

Se você quiser personalizar a identidade do remetente de email, o Microsoft Cloud App Security permitirá essa personalização usando o MailChimp®, um serviço de email de terceiros. Para facilitar o trabalho, no portal do Microsoft Cloud App Security, vá para **Configurações**. Selecione **Configurações de email** e examine os Termos de serviço e a Política de privacidade do MailChimp. Em seguida, dê à Microsoft permissão para usar o MailChimp em seu nome.

Se você não personalizar a identidade do remetente, as notificações de email serão enviadas usando todas as configurações padrão.

Para trabalhar com MailChimp, adicione esse endereço IP à lista de permissões anti-spam para permitir que as notificações sejam enviadas: 198.2.134.139 (mail1.cloudappsecurity.com)

## <a name="log-collector"></a>Coletor de logs

Para habilitar os recursos de Cloud Discovery usando um coletor de logs e detectar TI Sombra na sua organização, abra os seguintes itens:

- Permitir que o coletor de logs receba o tráfego FTP e Syslog de entrada.
- Permitir que o coletor de logs inicie o tráfego de saída para o portal (por exemplo, contoso.cloudappsecurity.com) na porta 443.
- Permita que o coletor de logs inicie o tráfego de saída para o Armazenamento de Blobs do Azure na porta 443:

  | Data center |                        URL                        |
  |-------------|---------------------------------------------------|
  |     US1     | https://adaprodconsole.blob.core.windows.net/     |
  |     US2     | https://prod03use2console1.blob.core.windows.net/ |
  |     US3     | https://prod5usw2console1.blob.core.windows.net/  |
  |     EU1     | https://prod02euwconsole1.blob.core.windows.net/  |
  |     EU2     | https://prod4uksconsole1.blob.core.windows.net/   |

> [!NOTE]
> - Se o firewall exigir uma lista de acesso de endereço IP estático e não for compatível com a lista de permissões baseada em URL, permita que o coletor de logs inicie o tráfego de saída para os [Intervalos de IP do datacenter do Microsoft Azure](https://www.microsoft.com/download/details.aspx?id=41653) na porta 443.
>- Permita que o coletor de logs inicie o tráfego de saída no portal do Cloud App Security.
>- Se você não especificou um proxy ao configurar o coletor de logs, precisará permitir conexões http://ocsp.msocsp.com/ http e OCSP.DigiCert.com na porta 80. Isso é usado para verificar o status de revogação de certificado ao se conectar ao portal do Cloud App Security.

## <a name="next-steps"></a>Próximas etapas

[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/)
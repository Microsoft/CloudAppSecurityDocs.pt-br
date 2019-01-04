---
title: Requisitos de rede – Cloud App Security | Microsoft Docs
description: Este artigo descreve os endereços IP e portas que você precisa abrir para trabalhar com o Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/10/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 4de606f2-a09e-4e48-a578-e223de8b5e69
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: df90f8a2b2a52f9dbaacac3e317b1354bdbe1d8a
ms.sourcegitcommit: b86c3afd1093fbc825fec5ba4103e3a95f65758e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53176596"
---
# <a name="network-requirements"></a>Requisitos de rede

*Aplica-se a: Microsoft Cloud App Security*

Este artigo fornece uma lista de portas e endereços IP que você precisa permitir e adicionar à lista de permissões para trabalhar com o Microsoft Cloud App Security. 

## <a name="view-your-data-center"></a>Exibir seu data center

Alguns dos requisitos abaixo dependem em que data center você está conectado. 

Para ver qual data center você está se conectando, execute as seguintes etapas:

1. No portal do Cloud App Security, clique no **ícone de ponto de interrogação** na barra de menus. Em seguida, selecione **Sobre**. 

    ![clique em Sobre](./media/about-menu.png)

2. Na tela da versão do Cloud App Security, você pode ver a região e o data center.

    ![Exibir seu data center](./media/data-center.png)

## <a name="portal-access"></a>Acesso ao portal

Para acessar o portal do Cloud App Security, adicione a **porta de saída 443** dos seguintes endereços IP e nomes DNS à lista de permissões do firewall:  

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
> |EUA|13.80.125.22<br></br>52.183.75.62<br></br>13.91.91.243|\*.us.portal.cloudappsecurity.com|
> |US2|13.80.125.22<br></br>52.183.75.62<br></br>52.184.165.82|\*.us2.portal.cloudappsecurity.com<br></br>|
> |US3|13.80.125.22<br></br>52.183.75.62<br></br>40.90.218.198<br></br>40.90.218.196|*.us3.portal.cloudappsecurity.com<br></br>|
> |UE|13.80.125.22<br></br>52.183.75.62<br></br>52.174.56.180|\*.eu.portal.cloudappsecurity.com<|
> |EU2|13.80.125.22<br></br>52.183.75.62<br></br>40.81.156.154<br></br>40.81.156.156|*.eu2.portal.cloudappsecurity.com|


> 
> [!NOTE]
> Em vez de um caractere curinga (\*), você pode abrir somente a URL específica do locatário, por exemplo, de acordo com a captura de tela acima, você poderá abrir mod244533.us.portal.cloudappsecurity.com

## <a name="siem-agent-connection"></a>Conexão do agente SIEM

Para habilitar a conexão do Cloud App Security ao seu SIEM, adicione a **porta de saída 443** para os seguintes endereços IP na lista de permissões do seu firewall:  


> [!div class="mx-tableFixed"]
> 
> |Data center|Endereços IP|  
> |----|----|
> |EUA|13.91.91.243|
> |US2|52.184.165.82|
> |US3|40.90.218.198<br>40.90.218.196|
> |UE|52.174.56.180|
> |EU2|40.81.156.154<br>40.81.156.156|

> [!NOTE]
> Se você não especificar um proxy ao configurar o agente SIEM do Cloud App Security, você precisará permitir conexões http para http://ocsp.msocsp.com/ na porta 80. Isso é usado para verificar o status de revogação de certificado ao se conectar ao portal do Cloud App Security.

## <a name="app-connector"></a>Conector de aplicativo

Para alguns aplicativos de terceiros serem acessados pelo Cloud App Security, esses endereços IP podem ser usados. Os endereços IP permitem ao Cloud App Security coletar logs e fornecer acesso ao console do Cloud App Security. 

> [!NOTE]
>Você pode ver esses endereços IP nos logs de atividades do fornecedor porque o Cloud App Security executa as ações de governança e as varreduras desses endereços IP. 

Para se conectar a aplicativos de terceiros, habilite o Cloud App Security para se conectar nesses endereços IP:


> [!div class="mx-tableFixed"]
> 
> |Data center|Endereços IP|  
> |----|----|
> |EUA|13.91.91.243 <br></br> 104.209.35.177 <br></br> 13.91.98.185 <br></br> 40.118.211.172 <br></br> 13.93.216.68 <br></br> 13.91.61.249 <br></br> 13.93.233.42 <br></br> 13.64.196.27 <br></br> 13.64.198.97 <br></br> 13.64.199.41 <br></br> 13.64.198.19|
> |US2|52.184.165.82<br></br> 40.84.4.93 <br></br> 40.84.4.119 <br></br> 40.84.2.83 |
> |US3|40.90.218.197<br>40.90.218.203|
> |UE|52.174.56.180<br></br>13.80.22.71<br></br>13.95.29.177<br></br>13.95.30.46|
> |EU2|40.81.156.155<br>40.81.156.153|


## <a name="third-party-dlp-integration"></a>Integração do DLP de terceiros

Para habilitar o Cloud App Security a enviar dados por meio de seu stunnel para seu servidor ICAP, abra o firewall de DMZ para esses endereços IP com um número da porta de origem dinâmico. 

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
> |Data center|Endereços IP|  
> |----|----|
> |EUA|13.91.91.243 <br></br> 104.209.35.177 <br></br> 13.91.98.185 <br></br> 40.118.211.172 <br></br> 13.93.216.68 <br></br> 13.91.61.249 <br></br> 13.93.233.42 <br></br> 13.64.196.27 <br></br> 13.64.198.97 <br></br> 13.64.199.41 <br></br> 13.64.198.19|
> |US2|52.184.165.82<br></br> 40.84.4.93 <br></br> 40.84.4.119 <br></br> 40.84.2.83 |
> |US3|40.90.218.197<br>40.90.218.203|
> |UE|52.174.56.180<br></br>13.80.22.71<br></br>13.95.29.177<br></br>13.95.30.46|
> |EU2|40.81.156.155<br>40.81.156.153|

## <a name="mail-server"></a>Servidor de emails

Para habilitar o envio de notificações com o modelo e as configurações padrão, adicione esses endereços IP à sua lista de permissões antispam. Os endereços IP de email dedicado do Cloud App Security são: 

- 65.55.234.192/26
- 207.46.200.0/27
- 65.55.52.224/27
- 94.245.112.0/27
- 111.221.26.0/27
- 207.46.50.192/26

Se você quiser personalizar a identidade do remetente de email, o Microsoft Cloud App Security permitirá essa personalização usando o MailChimp®, um serviço de email de terceiros. Para facilitar o trabalho, no portal do Microsoft Cloud App Security, vá para **Configurações**. Selecione **Configurações de email** e examine os Termos de serviço e a Política de privacidade do MailChimp. Em seguida, dê à Microsoft permissão para usar o MailChimp em seu nome.

Se você não personalizar a identidade do remetente, as notificações de email serão enviadas usando todas as configurações padrão.

Para trabalhar com o MailChimp, adicione este endereço IP à lista de permissões antispam para habilitar o envio de notificações: 198.2.134.139 (mail1.cloudappsecurity.com)


## <a name="log-collector"></a>Coletor de logs 

Para habilitar os recursos de Cloud Discovery usando um coletor de logs e detectar TI Sombra na sua organização, abra os seguintes itens:

- Permitir que o coletor de logs receba o tráfego FTP e Syslog de entrada.
- Permitir que o coletor de logs inicie o tráfego de saída para o portal (por exemplo, contoso.cloudappsecurity.com) na porta 443.
- Permita que o coletor de logs inicie o tráfego de saída para o Armazenamento de Blobs do Azure na porta 443:


  | Data center |                        URL                        |
  |-------------|---------------------------------------------------|
  |     EUA      |   https://adaprodconsole.blob.core.windows.net/   |
  |     US2     | https://prod03use2console1.blob.core.windows.net/ |
  |     US3     |https://prod5usw2console1.blob.core.windows.net/   |
  |     UE      | https://prod02euwconsole1.blob.core.windows.net/  |
  |     EU2     |https://prod4uksconsole1.blob.core.windows.net/    |

> [!NOTE]
> - Se o firewall exigir uma lista de acesso de endereço IP estático e não for compatível com a lista de permissões baseada em URL, permita que o coletor de logs inicie o tráfego de saída para os [Intervalos de IP do datacenter do Microsoft Azure](https://www.microsoft.com/download/details.aspx?id=41653) na porta 443.
>- Permita que o coletor de logs inicie o tráfego de saída no portal do Cloud App Security.
>- Se não especificar um proxy ao configurar o coletor de logs, você precisará permitir conexões http para http://ocsp.msocsp.com/ na porta 80. Isso é usado para verificar o status de revogação de certificado ao se conectar ao portal do Cloud App Security.

## <a name="next-steps"></a>Próximas etapas
 
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/)  


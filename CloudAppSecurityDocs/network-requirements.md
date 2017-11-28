---
title: Requisitos de rede do Cloud App Security | Microsoft Docs
description: "Este tópico descreve os endereços IP e portas que você precisa abrir para trabalhar com o Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/11/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 4de606f2-a09e-4e48-a578-e223de8b5e69
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 4b681ef0cd982b79ae096f257f793920607669a2
ms.sourcegitcommit: 4d84f9d15256b05c785a1886338651b86622070c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2017
---
# <a name="network-requirements"></a>Requisitos de rede

Este tópico fornece uma lista de portas e endereços IP que você precisa permitir e adicionar à lista de permissões para trabalhar com o Cloud App Security. 


## <a name="view-your-data-center"></a>Exibir seu data center

Alguns dos requisitos abaixo dependem em que data center você está conectado. 

Para ver a qual data center você está se conectando:

1. No portal do Cloud App Security, clique em **?** na barra de menus e selecione **Sobre**. 

    ![clique em Sobre](./media/about-menu.png)

2. Na tela da versão do Cloud App Security, você pode ver a região e o data center.

    ![Exibir seu data center](./media/data-center.png)

## <a name="portal-access"></a>Acesso ao portal

Para acessar o portal do Cloud App Security, adicione a **porta de saída 443** para os seguintes endereços IP na lista de permissões do seu firewall:  


> [!div class="mx-tableFixed"]
|Data center|Endereços IP|  
|----|----|
|US1|13.80.125.22<br></br>52.183.75.62<br></br>13.91.91.243|
|US2|13.80.125.22<br></br>52.183.75.62<br></br>52.184.165.82|
|EU1|13.80.125.22<br></br>52.183.75.62<br></br>52.174.56.180|

## <a name="siem-agent-connection"></a>Conexão do agente SIEM

Para habilitar a conexão do Cloud App Security ao seu SIEM, adicione a **porta de saída 443** para os seguintes endereços IP na lista de permissões do seu firewall:  


> [!div class="mx-tableFixed"]
|Data center|Endereços IP|  
|----|----|
|US1|13.91.91.243|
|US2|52.184.165.82|
|EU1|52.174.56.180|

## <a name="app-connector-access-and-external-dlp-integration"></a>Acesso ao aplicativo conector e integração de DLP externa

Para se conectar a aplicativos de terceiros e integrar soluções de DLP externas, habilite o Cloud App Security para se conectar a esses endereços IP:


> [!div class="mx-tableFixed"]
|Data center|Endereços IP|  
|----|----|
|US1|13.91.91.243 <br></br> 104.209.35.177 <br></br> 13.91.98.185 <br></br> 40.118.211.172 <br></br> 13.93.216.68 <br></br> 13.91.61.249 <br></br> 13.93.233.42 <br></br> 13.64.196.27 <br></br> 13.64.198.97 <br></br> 13.64.199.41 <br></br> 13.64.198.19|
|US2|52.184.165.82<br></br> 40.84.4.93 <br></br> 40.84.4.119 <br></br> 40.84.2.83 |
|EU1|52.174.56.180<br></br>13.80.22.71<br></br>13.95.29.177<br></br>13.95.30.46|


### <a name="app-connector"></a>Conector de aplicativo
Para alguns aplicativos de terceiros serem acessados pelo Cloud App Security, esses endereços IP podem ser usados para permitir que o Cloud App Security colete logs e forneça acesso para o console do Cloud App Security. 

> [!NOTE]
>Você pode ver esses endereços IP nos logs de atividades do fornecedor porque o Cloud App Security executa as ações de governança e as varreduras desses endereços IP. 
  

### <a name="dlp-integration"></a>Integração do DLP

Para que o Cloud App Security envie dados por meio de seu stunnel para seu servidor ICAP, abra o firewall de DMZ para esses endereços IP com um número da porta de origem dinâmico. 

1.  Endereços de origem: eles devem estar na lista de permissões conforme listado acima para aplicativos de terceiros de conector de API
2.  Porta TCP de origem: dinâmico
3.  Endereços de destino: um ou dois endereços IP do stunnel conectado ao servidor ICAP externo
4.  Porta TCP de destino: conforme definido em sua rede

> [!NOTE] 
> Por padrão, o número da porta stunnel é definido como 11344. Você pode alterá-lo para outra porta, se necessário, mas certifique-se de anotar o novo número da porta.

## <a name="email-server"></a>Servidor de email

O endereço IP dedicado do email do Cloud App Security é: 

198.2.134.139 (mail1.cloudappsecurity.com)

Inclua esse endereço IP à lista de permissões com o serviço antispam a fim de habilitar o envio de notificações.
    
## <a name="log-collector"></a>Coletor de logs 

Para habilitar os recursos de Cloud Discovery usando um coletor de logs e detectar TI sombra na sua organização, é necessário abrir o seguinte:

- Permitir que o coletor de logs receba o tráfego FTP e Syslog de entrada.
- Permitir que o coletor de logs inicie o tráfego de saída para o portal (por exemplo, contoso.cloudappsecurity.com) na porta 443.
- Permita que o coletor de logs inicie o tráfego de saída para o Armazenamento de Blobs do Azure nas portas 80 e 443:
   
    |Data center|URL|
    |----|----|
    |US1|https://adaprodconsole.blob.core.windows.net/|
    |US2|https://prod03use2console1.blob.core.windows.net/|
    |EU1|https://prod02euwconsole1.blob.core.windows.net/|

> [!NOTE]
> Se o seu firewall exigir uma lista de acesso de endereço IP estático e não oferecer suporte à lista de permissões com base na URL, permita que o coletor de logs inicie o tráfego de saída para os Intervalos de IP de datacenter do Microsoft Azure na porta 443.




## <a name="see-also"></a>Veja também  
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  

   
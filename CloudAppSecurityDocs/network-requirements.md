---
title: Requisitos de rede do Cloud App Security | Microsoft Docs
description: "Este tópico descreve os endereços IP e portas que você precisa abrir para trabalhar com o Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 9/27/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 4de606f2-a09e-4e48-a578-e223de8b5e69
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: a43adb2dfbfce0164384bd9fccb87d602e9eb7b7
ms.sourcegitcommit: 8759541301241e03784c5ac87b56986f22bd0561
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/28/2017
---
# <a name="network-requirements"></a>Requisitos de rede

Este tópico fornece uma lista de portas e endereços IP que você precisa permitir e adicionar à lista de permissões para trabalhar com o Cloud App Security. 

Para obter informações sobre como ver a qual data center do Cloud App Security center você está conectado, consulte [Tokens de API](api-tokens.md)



## <a name="portal-access-siem-agent-authentication-gateway-and-log-collector"></a>Acesso ao portal, agente SIEM, gateway de autenticação e coletor de log

Para obter acesso de gateway de autenticação e do portal e para habilitar o Cloud App Security a se conectar ao seu SIEM, bem como para habilitar o coletor de logs do Cloud App Security para executá-lo, é necessário adicionar a **porta de saída 443** ao endereço IP abaixo a lista de permissões do firewall:  


> [!div class="mx-tableFixed"]
|Data center|Endereços IP|  
|----|----|
|US1|13.91.91.243<br></br>52.183.75.62|
|EU1|52.174.56.180<br></br>13.80.125.22|

## <a name="app-connector-access-and-external-dlp-integration"></a>Acesso ao aplicativo conector e integração de DLP externa

Para se conectar a aplicativos de terceiros e integrar soluções de DLP externas, habilite o Cloud App Security para se conectar a esses endereços IP:


> [!div class="mx-tableFixed"]
|Data center|Endereços IP|  
|----|----|
|US1|104.209.35.177<br></br>13.91.98.185<br></br>40.118.211.172<br></br>13.93.216.68<br></br>13.91.61.249<br></br>13.93.233.42<br></br>13.64.196.27<br></br>13.64.198.97<br></br>13.64.199.41<br></br>13.64.198.19|
|EU1|13.80.22.71<br></br>13.95.29.177<br></br>13.95.30.46|


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
    



  
## <a name="see-also"></a>Veja também  
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  

   
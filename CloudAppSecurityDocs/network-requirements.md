---
title: Requisitos de rede do Cloud App Security | Microsoft Docs
description: "Este tópico descreve os endereços IP e portas que você precisa abrir para trabalhar com o Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 8/27/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 4de606f2-a09e-4e48-a578-e223de8b5e69
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: dac230e191c7c2d8159a2f373e6ef939fdd841a4
ms.sourcegitcommit: c3fda43ef6fe0d15f0eb9ea23a6f245bad8c371b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2017
---
# <a name="network-requirements"></a>Requisitos de rede

Este tópico fornece uma lista de portas e endereços IP que você precisa permitir e adicionar à lista de permissões para trabalhar com o Cloud App Security. 


## <a name="portal-access"></a>Acesso ao portal

Para o acesso ao portal, é necessário adicionar os seguintes endereços IP à sua lista de permissões do firewall para fornecer acesso ao portal do Cloud App Security:  
  
104.42.231.28  


## <a name="app-connector-access"></a>Acesso ao conector do aplicativo

Para alguns aplicativos de terceiros serem acessados pelo Cloud App Security, pode ser necessário adicionar os seguintes endereços IP à lista de permissões para permitir que Cloud App Security colete logs e forneça acesso para o console do Cloud App Security:  
  
104.209.35.177  
13.91.98.185 40.118.211.172 13.93.216.68 13.91.61.249 13.93.233.42 13.64.196.27 13.64.198.97 13.64.199.41 13.64.198.19

> [!NOTE]
>Você pode ver esses endereços IP nos logs de atividades do fornecedor porque o Cloud App Security executa as ações de governança e as varreduras desses endereços IP. 
  

## <a name="siem-agent-and-log-collector"></a>Agente SIEM e coletor de logs

Para permitir que o Cloud App Security se conecte ao seu SIEM e que o coletor de logs do Cloud App Security seja executado, é necessário abrir:

- Porta de saída 443 para 104.42.231.28

## <a name="external-dlp-integration"></a>Integração de DLP externa

Para o Cloud App Security enviar dados por meio de seu stunnel para seu servidor ICAP, abra o firewall de DMZ para os endereços IP externos usados pelo Cloud App Security com um número da porta de origem dinâmico. 

1.  Endereços de origem: esses devem ser na lista de permissões conforme listado acima para aplicativos de terceiros de conector de API
2.  Porta TCP de origem: dinâmico
3.  Endereços de destino: um ou dois endereços IP do stunnel conectado ao servidor ICAP externo
4.  Porta TCP de destino: conforme definido em sua rede

> [!NOTE] 
> Por padrão, o número da porta stunnel é definido como 11344. Você pode alterá-lo para outra porta, se necessário, mas certifique-se de anotar o novo número da porta.



  
## <a name="see-also"></a>Veja também  
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  

   
---
title: Conectar aplicativos para obter visibilidade profunda e controle com o Cloud App Security | Microsoft Docs
description: "Este tópico descreve o processo de conexão de aplicativos com conectores de API, para aplicativos na nuvem da sua organização."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 7/3/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 7e718d77-aae7-4a3a-8421-5ba7cee7d67c
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: c8c9b63f4265876fc1de6a24c6576f917f9d2278
ms.sourcegitcommit: a0290ac2a662994f7771975ef6c20d0b47e9edd8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/03/2017
---
Cloud App Security requer acesso da seguinte maneira para se conectar à sua rede. 

## <a name="cloud-app-security-system-ip-addresses"></a>Endereços IP do Cloud App Security System

Os seguintes endereços IP são usados pelo Cloud App Security para conectar-se a ambientes de cliente. Isso é necessário ao se conectar usando [ICAP](icap-stunnel.md) e ao conectar-se os conectores de aplicativos. Para alguns aplicativos, pode ser necessário adicionar os seguintes endereços IP à lista de permissões para permitir que Cloud App Security colete logs e forneça acesso para o console do Cloud App Security. Em alguns aplicativos, esses endereços IP também podem ser usados para identificar as atividades do Cloud App Security, como nos logs de auditoria do serviço. 
  
-   Para os logs:  
  
    104.209.35.177  
  
    13.91.98.185
 
    40.118.211.172

    13.93.216.68

    13.91.61.249

    13.93.233.42

    13.64.196.27

    13.64.198.97

    13.64.199.41

    13.64.198.19
  
  
## <a name="cas-portal-url-and-ip-addresses"></a>Endereços IP e URL do portais do CAS

A URL do Cloud App Security, porta 443 e os endereços IP são usados para acesso de cliente ao portal, conexões de API ao seu conectar a APIs CAS, Coletor de logs e agente SIEM. 
  
     104.42.231.28  

 
  
> [!NOTE]  
>  Para obter atualizações quando URLs e endereços IP forem alterados, assine o RSS conforme explicado em: [URLs e intervalos de endereços IP do Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).  
  

  
## <a name="see-also"></a>Veja também  
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  

   
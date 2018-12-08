---
title: Conectar o Azure ao Cloud App Security para obter visibilidade e controle de uso | Microsoft Docs
description: Este artigo fornece informações sobre como conectar o Azure ao Cloud App Security usando o conector de API.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/13/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 3a677bc7-c8b7-4c6a-aada-82c8b3778352
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 9466a9afa157bad350bb94b63ba633bf0d80bac2
ms.sourcegitcommit: 77850c6777504c2478611cb71a387e7fcc5f2551
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/13/2018
ms.locfileid: "51597160"
---
# <a name="connect-azure-to-microsoft-cloud-app-security"></a>Conectar o Azure ao Microsoft Cloud App Security

*Aplica-se ao: Microsoft Cloud App Security*

Este artigo fornece instruções para conectar o Microsoft Cloud App Security à sua conta existente do Azure usando a API do conector de aplicativos.  
  
## <a name="how-to-connect-azure-to-cloud-app-security"></a>Como conectar o Azure ao Cloud App Security  
  
> [!NOTE]
> - O usuário precisa ser administrador global no Azure AD para conectar o Azure ao Microsoft Cloud App Security. 
> - O Cloud App Security exibe as atividades de **todas** as assinaturas.
>-  Atualmente, o Cloud App Security monitora apenas as atividades ARM. 
 
1.  Na página **Aplicativos conectados**, clique no botão de mais e selecione **Microsoft Azure**.  
  
     ![Conectar o Azure](./media/connect-azure-menu.png) 

2.  No pop-up do Azure, clique em **Conectar o Microsoft Azure**.

      ![Conectar o Azure](./media/connect-azure.png) 
 
> [!NOTE] 
> Após conectar o Azure, o pull dos dados será efetuado. A partir desse momento, você vê os dados.


## <a name="next-steps"></a>Próximas etapas 
[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)   

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
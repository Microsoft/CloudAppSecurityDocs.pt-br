---
title: Perguntas frequentes sobre o Cloud App Security | Microsoft Docs
description: Este artigo fornece as perguntas frequentes e as respostas sobre o Cloud App Security.
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/6/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 081c2cf4-2750-4546-9490-4b65e87ae48c
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 618f5817abc29ee3d46230f0af94e4e819242e6f
ms.sourcegitcommit: b729e881851cdd8dc3f105ddbf6b4b907b8588dd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/06/2017
---
# <a name="frequently-asked-questions"></a>Perguntas frequentes

## <a name="what-kind-of-permissions-do-i-need-to-have-in-order-to-access-cloud-app-security"></a>Que tipo de permissão preciso ter para acessar o Cloud App Security?

Você precisa ser Administrador global, Administrador de conformidade ou Administrador de segurança no Azure Active Directory. Não é suficiente ter essas funções no Centro de Conformidade e Segurança do Office 365.
Para definir um usuário como Administrador global, Administrador de conformidade ou Administrador de segurança no Azure Active Directory, execute o seguinte no Windows PowerShell:

        $cred = Get-Credential
        Connect-MsolService -credential $cred
        Add-MsolRoleMember -RoleName "Compliance Administrator" -RoleMemberEmailAddress "XX@XX.XX"
 OU Add-MsolRoleMember -RoleName "Security Administrator" -RoleMemberEmailAddress “XX@XX.XX”

## <a name="see-also"></a>Veja também  
Para saber como usar e configurar políticas para controlar o uso do aplicativo de nuvem, consulte [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md).   
Para obter suporte técnico, vá para a página de [suporte assistido do Cloud App Security](http://support.microsoft.com/oas/default.aspx?prid=16031).   
Os clientes Premier também podem escolher o Cloud App Security diretamente no [Portal Premier](https://premier.microsoft.com/).  

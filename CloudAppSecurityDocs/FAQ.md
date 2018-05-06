---
title: Perguntas frequentes sobre o Cloud App Security | Microsoft Docs
description: Este artigo fornece as perguntas frequentes e as respostas sobre o Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/22/2018
ms.topic: article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 081c2cf4-2750-4546-9490-4b65e87ae48c
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 3347b7cfba41c2e5dc9f47b74a2b1f6e8d7dab62
ms.sourcegitcommit: 45311f2cafef79483e40d971a4c61c7673834d96
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2018
---
*Aplica-se ao: Microsoft Cloud App Security*


# <a name="frequently-asked-questions"></a>Perguntas frequentes

## <a name="what-kind-of-permissions-do-i-need-to-have-in-order-to-access-cloud-app-security"></a>Que tipo de permissão preciso ter para acessar o Cloud App Security?

Você precisa ser Administrador global, Administrador de conformidade ou Administrador de segurança no Azure Active Directory. Não é suficiente ter essas funções no Centro de Conformidade e Segurança do Office 365.
Para definir um usuário como Administrador global, Administrador de conformidade ou Administrador de segurança no Azure Active Directory, execute o seguinte no Windows PowerShell:

        $cred = Get-Credential
        Connect-MsolService -credential $cred
        Add-MsolRoleMember -RoleName "Compliance Administrator" -RoleMemberEmailAddress "XX@XX.XX"
 OU Add-MsolRoleMember -RoleName "Security Administrator" -RoleMemberEmailAddress “XX@XX.XX”

## <a name="see-also"></a>Consulte também  
Para saber como usar e configurar políticas para controlar o uso do aplicativo de nuvem, consulte [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md).   

Os clientes Premier também podem escolher o Cloud App Security diretamente no [Portal Premier](https://premier.microsoft.com/).  

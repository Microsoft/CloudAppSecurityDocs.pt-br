---
title: Perguntas frequentes sobre o Cloud App Security | Microsoft Docs
description: Este artigo fornece as perguntas frequentes e as respostas sobre o Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/12/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 081c2cf4-2750-4546-9490-4b65e87ae48c
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 071c2aefff1b885f5f63ee6403a6228250cb8686
ms.sourcegitcommit: e424807015f33aa359d9e29e13cc2faac5adcb92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2018
ms.locfileid: "51560978"
---
# <a name="frequently-asked-questions"></a>Perguntas frequentes

*Aplica-se ao: Microsoft Cloud App Security*

Este artigo fornece as perguntas frequentes e as respostas sobre o Cloud App Security.

## <a name="what-kind-of-permissions-do-i-need-to-access-cloud-app-security"></a>Que tipo de permissões preciso ter para acessar o Cloud App Security?

Você precisa ser Administrador global, Administrador de conformidade ou Administrador de segurança no Azure Active Directory. Não é suficiente ter apenas essas funções no Centro de Conformidade e Segurança do Office 365. Use o PowerShell para definir um usuário como Administrador global, Administrador de conformidade ou Administrador de segurança no Azure Active Directory. Execute os seguintes cmdlets abaixo:

```powershell

 $cred = Get-Credential
 Connect-MsolService -credential $cred
 Add-MsolRoleMember -RoleName "Compliance Administrator" -RoleMemberEmailAddress "XX@XX.XX"
```

 OU

```powershell
 Add-MsolRoleMember -RoleName "Security Administrator" -RoleMemberEmailAddress “XX@XX.XX”
```

## <a name="next-steps"></a>Próximas etapas  
Para saber como configurar e usar políticas para controlar o uso de aplicativos na nuvem, confira [Controlar aplicativos na nuvem com políticas](control-cloud-apps-with-policies.md).   

Os clientes Premier também podem escolher o Cloud App Security diretamente no [Portal Premier](https://premier.microsoft.com/).  

---
title: Perguntas frequentes – Cloud App Security | Microsoft Docs
description: Este artigo fornece as perguntas frequentes e as respostas sobre o Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 081c2cf4-2750-4546-9490-4b65e87ae48c
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: f2d2fc6ef5753cbca977e785249ddf61a3664eb5
ms.sourcegitcommit: c342abeec95359ddabdabcc3a081a0f91d52407c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72334442"
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

 ou do

```powershell
 Add-MsolRoleMember -RoleName "Security Administrator" -RoleMemberEmailAddress “XX@XX.XX”
```

## <a name="next-steps"></a>Próximas etapas  
Para saber como configurar e usar políticas para controlar o uso de aplicativos na nuvem, confira [Controlar aplicativos na nuvem com políticas](control-cloud-apps-with-policies.md).   

Os clientes Premier também podem escolher o Cloud App Security diretamente no [Portal Premier](https://premier.microsoft.com/).  

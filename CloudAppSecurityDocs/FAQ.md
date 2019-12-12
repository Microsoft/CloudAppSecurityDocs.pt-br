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
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 043615ccdde609f77f6804ee9040e1df55a321f4
ms.sourcegitcommit: 6eff466c7a6817b14a60d8c3b2c201c7ae4c2e2c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74719859"
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

[!INCLUDE [Open support ticket](includes/support.md)]

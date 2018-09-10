---
title: Políticas de solução de problemas do Cloud App Security | Microsoft Docs
description: Este tópico descreve o processo de criação de políticas de solução de problemas no Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/22/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 828cc94a-248b-44f6-a1ba-c28c0a135f8c
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: ca7d2187ebd83c352cbbcf92efb7a30adf8debcf
ms.sourcegitcommit: 0ac08ca7b3140b79f1d36ff7152476c188fa12b3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44142571"
---
*Aplica-se ao: Microsoft Cloud App Security*


# <a name="troubleshooting-microsoft-cloud-app-security-policies"></a>Políticas de solução de problemas do Microsoft Cloud App Security

|Erro do|Descrição|Resolução|
|----|----|----|
| **A política <policy name> foi automaticamente desabilitada devido a um erro de configuração**|Se este erro ocorrer no Microsoft Cloud App Security, isso significará que você precisará corrigir a configuração da política indicada. Ao criar uma política do Microsoft Cloud App Security, geralmente você faz uso de outros objetos que criou no Cloud App Security, ou no Centro de Segurança e Conformidade, como marcações de IP ou tipos confidenciais personalizados. Se a marcação de IP ou tipo confidencial personalizado usado na política for excluído posteriormente, a política será automaticamente desabilitada e esse erro ocorrerá. Isso também pode indicar um erro de configuração mais geral, como um filtro muito complexo. |Para restaurar a política, edite a política e corrija todo erro de configuração mencionado. Geralmente, isso significa que você precisará remover quaisquer objetos excluídos de filtros de política e salvar a política.|



## <a name="see-also"></a>Consulte Também
[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier](https://premier.microsoft.com/)


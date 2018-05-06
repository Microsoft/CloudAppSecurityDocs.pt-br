---
title: Políticas de solução de problemas do Cloud App Security | Microsoft Docs
description: Este tópico descreve o processo de criação de políticas de solução de problemas no Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/22/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 828cc94a-248b-44f6-a1ba-c28c0a135f8c
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 9bfc880cdaa0bf87abfd2b3b34cdf647a4aa1aaf
ms.sourcegitcommit: 45311f2cafef79483e40d971a4c61c7673834d96
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2018
---
*Aplica-se ao: Microsoft Cloud App Security*


# <a name="troubleshooting-microsoft-cloud-app-security-policies"></a>Políticas de solução de problemas do Microsoft Cloud App Security

|Erro do|Descrição|Resolução|
|----|----|----|
| **A política <policy name> foi automaticamente desabilitada devido a um erro de configuração.**|Se este erro ocorrer no Microsoft Cloud App Security, isso significará que você precisará corrigir a configuração da política nomeada. Ao criar uma política do Microsoft Cloud App Security, geralmente você faz uso de outros objetos que criou no Cloud App Security, como marcações de IP ou filtros de intervalo de IP. Se a marcação ou o intervalo de IP usado na política for excluído posteriormente, a política será automaticamente desabilitada e esse erro ocorrerá. |Para restaurar a política, edite-a, remova quaisquer objetos excluídos de seus filtros e salve a política.|



## <a name="see-also"></a>Consulte Também
[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier](https://premier.microsoft.com/)


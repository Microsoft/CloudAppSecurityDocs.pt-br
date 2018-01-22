---
title: "Políticas de solução de problemas do Cloud App Security | Microsoft Docs"
description: "Este tópico descreve o processo de criação de políticas de solução de problemas no Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/15/2018
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 828cc94a-248b-44f6-a1ba-c28c0a135f8c
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: ccd15579fd18616dccd663947d6513c21e1e1527
ms.sourcegitcommit: 458e936e1ac548eda37e9bf955b439199bbdd018
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2018
---
# <a name="troubleshooting-cloud-app-security-policies"></a>Políticas de solução de problemas do Cloud App Security

|Erro do|Descrição|Resolução|
|----|----|----|
| **A política <policy name> foi automaticamente desabilitada devido a um erro de configuração.**|Se este erro ocorrer no Cloud App Security, isso significa que você precisará corrigir a configuração da política nomeada. Ao criar uma política do Cloud App Security, geralmente você faz uso de outros objetos que criou no Cloud App Security, como marcações de IP ou filtros de intervalo de IP. Se a marcação ou o intervalo de IP usado na política for excluído posteriormente, a política será automaticamente desabilitada e esse erro ocorrerá. |Para restaurar a política, edite-a, remova quaisquer objetos excluídos de seus filtros e salve a política.|



## <a name="see-also"></a>Consulte Também
[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier](https://premier.microsoft.com/)


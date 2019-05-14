---
title: Políticas de solução de problemas do Cloud App Security
description: Este artigo descreve o processo de solução de problemas de criação de política no Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: rkarlin
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 828cc94a-248b-44f6-a1ba-c28c0a135f8c
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: bad9ddf835c4abd1dba339e8d413bd06097a5366
ms.sourcegitcommit: 9f0c562322394a3dfac7f1d84286e673276a28b1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65568843"
---
# <a name="troubleshooting-microsoft-cloud-app-security-policies"></a>Políticas de solução de problemas do Microsoft Cloud App Security

*Aplica-se a: Microsoft Cloud App Security*

Este artigo descreve o processo de solução de problemas de criação de política no Cloud App Security.

## <a name="troubleshooting"></a>Solução de problemas

O gráfico a seguir apresenta a descrição e a resolução de erros que podem aparecer para políticas.

|Erro do|Descrição|Resolução|
|----|----|----|
| **A política <*nome*> foi desabilitada automaticamente devido a um erro de configuração**|Se esse erro ocorrer no Microsoft Cloud App Security, significará que você precisa corrigir a configuração da política indicada. Quando você cria uma política do Microsoft Cloud App Security, geralmente você faz uso de outros objetos criados no Cloud App Security ou no Centro de Conformidade e Segurança, como marcas de IP ou tipos confidenciais personalizados. Se a marca de IP ou o tipo confidencial personalizado usado na política for excluído, a política será desabilitada automaticamente e você receberá esse erro. Essa mensagem também pode indicar um erro de configuração mais geral, como um filtro muito complexo. |Para restaurar a política, edite-a e corrija todos os erros de configuração mencionados. Esse erro geralmente significa que você precisa remover todos os objetos excluídos dos filtros da política e salvar a política.|

## <a name="next-steps"></a>Próximas etapas

[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier](https://premier.microsoft.com/)


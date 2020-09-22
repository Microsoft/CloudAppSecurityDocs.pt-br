---
title: Políticas de solução de problemas do Cloud App Security
description: Este artigo descreve o processo de solução de problemas de criação de política no Cloud App Security.
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
ms.openlocfilehash: ca7eb8ec3a770991ffc3a0bcd8f39f70c2a65a7b
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90877107"
---
# <a name="troubleshooting-microsoft-cloud-app-security-policies"></a>Políticas de solução de problemas do Microsoft Cloud App Security

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Este artigo descreve o processo de solução de problemas de criação de política no Cloud App Security.

## <a name="troubleshooting"></a>Solução de problemas

O gráfico a seguir apresenta a descrição e a resolução de erros que podem aparecer para políticas.

|Erro|Descrição|Resolução|
|----|----|----|
| **A política <*nome*> foi desabilitada automaticamente devido a um erro de configuração**|Se esse erro ocorrer no Microsoft Cloud App Security, significará que você precisa corrigir a configuração da política indicada. Quando você cria uma política do Microsoft Cloud App Security, geralmente você faz uso de outros objetos criados no Cloud App Security ou no Centro de Conformidade e Segurança, como marcas de IP ou tipos confidenciais personalizados. Se a marca de IP ou o tipo confidencial personalizado usado na política for excluído, a política será desabilitada automaticamente e você receberá esse erro. Essa mensagem também pode indicar um erro de configuração mais geral, como um filtro muito complexo. |Para restaurar a política, edite-a e corrija todos os erros de configuração mencionados. Esse erro geralmente significa que você precisa remover todos os objetos excluídos dos filtros da política e salvar a política.|

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]

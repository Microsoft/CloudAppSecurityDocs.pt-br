---
title: API de alertas de Cloud App Security
description: Este artigo fornece informações sobre como usar a API de alertas.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 10/20/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: f1176967bfcf67a458f55fe9421575df329aabe7
ms.sourcegitcommit: 6ae1c05025a49ad3c8e8cecd0c10dc05edcd9bf8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92929073"
---
# <a name="alerts-api"></a>API de alertas

[!INCLUDE [Banner for top of topics](includes/banner.md)]

A API de alertas fornece informações sobre os riscos imediatos identificados por Cloud App Security e exigem atenção. Os alertas podem resultar de padrões de uso suspeitos ou de arquivos que contenham conteúdo que viole a política da empresa.

O seguinte lista as solicitações com suporte:

- [Listar alertas](api-alerts-list.md)
- [Fechar benigno](api-alerts-close-benign.md)
- [Fechar falso positivo](api-alerts-close-false-positive.md)
- [Fechar verdadeiro positivo](api-alerts-close-true-positive.md)
- [Buscar alerta](api-alerts-fetch.md)
- [Marcar alerta como lido](api-alerts-mark-read.md)
- [Marcar alerta como não lido](api-alerts-mark-unread.md)

## <a name="deprecated-requests"></a>Solicitações preteridas

A tabela a seguir lista as solicitações preteridas como obsoletas e as solicitações que as substituem.

| Solicitação obsoleta | Alternativa |
| --- | --- |
| Ignorar em massa | [Fechar falso positivo](api-alerts-close-false-positive.md) |
| Resolver em massa | [Fechar verdadeiro positivo](api-alerts-close-true-positive.md) |
| Ignorar alerta | [Fechar falso positivo](api-alerts-close-false-positive.md) |

> [!NOTE]
> As solicitações preteridas foram mapeadas para as alternativas para evitar interrupções. No entanto, se você estiver usando solicitações obsoletas em seu ambiente, é recomendável atualizá-las para suas alternativas.

## <a name="filters"></a>Filtros

Para obter informações sobre como os filtros funcionam, consulte [filtros](api-introduction.md#filters).

A tabela a seguir descreve os filtros com suporte:

| Filtrar | Tipo | Operadores | Descrição |
| --- | --- | --- | --- |
| entidade. entidade | CP de entidade | EQ, NEQ | Filtrar alertas relacionados a entidades especificadas. Exemplo: `[{ "id": "entity-id", "saas": 11161, "inst": 0 }]` |
| Entity. IP | string | EQ, NEQ | Filtrar alertas relacionados a endereços IP especificados |
| entidade. serviço | inteiro | EQ, NEQ | Filtrar alertas relacionados à appId de serviço especificada, por exemplo: 11770 |
| entidade. instância | inteiro | EQ, NEQ | Filtrar alertas relacionados às instâncias especificadas, por exemplo: 11770, 1059065 |
| entidade. política | string | EQ, NEQ | Filtrar alertas relacionados às políticas especificadas |
| entidade. arquivo | string | EQ, NEQ | Filtrar alertas relacionados ao arquivo especificado |
| alertOpen | booleano | eq | Se definido como "true", retorna somente alertas abertos, se definido como "false", retorna apenas alertas fechados |
| severidade | inteiro | EQ, NEQ | Filtrar por severidade. Os valores possíveis incluem:<br /><br />**0** : baixo<br />**1** : média<br/>**2** : alta |
| resolutionStatus | inteiro | EQ, NEQ | Filtrar por status de resolução de alerta, os valores possíveis incluem:<br /><br />**0** : abrir <br />**1** : ignorado (status herdado)<br />**2** : resolvido (status herdado)<br />**3** : fechado como falso positivo<br />**4** : fechado como benigno<br />**5** : fechado como verdadeiro positivo |
| leitura | booleano | eq | Se definido como "true", retorna somente alertas de leitura, se definido como "false", retorna alertas não lidos |
| date | timestamp | LTE, GTE, Range, lte_ndays, gte_ndays | Filtrar pela hora em que um alerta foi disparado |
| resolutionDate | timestamp | LTE, GTE, Range | Filtrar pelo horário em que um alerta foi resolvido |
| ameaça | inteiro | EQ, NEQ | Filtrar por risco |
| alertType | inteiro | EQ, NEQ | Filtrar por tipo de alerta |
| ID | string | EQ, NEQ | Filtrar por IDs de alerta |
| source | string | eq | A origem do alerta, seja ela interna ou |

[!INCLUDE [Open support ticket](includes/support.md)]

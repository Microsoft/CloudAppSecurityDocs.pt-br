---
title: API de alertas de Cloud App Security
description: Este artigo fornece informações sobre como usar a API de alertas.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 0363d275c764d1e92d8d3f295de82e0c5bd2143a
ms.sourcegitcommit: 286f8d5d940d1bb9a09daa3070ac4fc3768208f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84505435"
---
# <a name="alerts-api"></a>API de alertas

*Aplica-se a: Microsoft Cloud App Security*

A API de alertas fornece informações sobre os riscos imediatos identificados por Cloud App Security e exigem atenção. Os alertas podem resultar de padrões de uso suspeitos ou de arquivos que contenham conteúdo que viole a política da empresa.

O seguinte lista as solicitações com suporte:

- [Lista de alertas](api-alerts-list.md)
- [Ignorar em massa](api-alerts-bulk-dismiss.md)
- [Resolução em massa](api-alerts-bulk-resolve.md)
- [Buscar alerta](api-alerts-fetch.md)
- [Ignorar alerta](api-alerts-dismiss.md)
- [Marcar alerta como lido](api-alerts-mark-read.md)
- [Marcar alerta como não lido](api-alerts-mark-unread.md)

## <a name="filters"></a>Filtros

Para obter informações sobre como os filtros funcionam, consulte [filtros](api-introduction.md#filters).

A tabela a seguir descreve os filtros com suporte:

| Filtrar | Type | Operadores | Descrição |
| --- | --- | --- | --- |
| entidade. entidade | CP de entidade | EQ, NEQ | Filtrar alertas relacionados a entidades especificadas. Exemplo: `[{ "id": "entity-id", "saas": 11161, "inst": 0 }]` |
| Entity. IP | string | EQ, NEQ | Filtrar alertas relacionados a endereços IP especificados |
| entidade. serviço | inteiro | EQ, NEQ | Filtrar alertas relacionados à appId de serviço especificada, por exemplo: 11770 |
| entidade. instância | inteiro | EQ, NEQ | Filtrar alertas relacionados às instâncias especificadas, por exemplo: 11770, 1059065 |
| entidade. política | string | EQ, NEQ | Filtrar alertas relacionados às políticas especificadas |
| entidade. arquivo | string | EQ, NEQ | Filtrar alertas relacionados ao arquivo especificado |
| severidade | inteiro | EQ, NEQ | Filtrar por severidade. Os valores possíveis incluem:<br /><br />**0**: baixo<br />**1**: média<br/>**2**: alta |
| resolutionStatus | inteiro | EQ, NEQ | Filtrar por status de resolução de alerta, os valores possíveis incluem:<br /><br />**0**: abrir<br />**1**: ignorado<br />**2**: resolvido |
| read | booleano | eq | Se definido como "true", retorna somente alertas de leitura, se definido como "false", retorna alertas não lidos |
| date | timestamp | LTE, GTE, Range, lte_ndays, gte_ndays | Filtrar pela hora em que um alerta foi disparado |
| resolutionDate | timestamp | LTE, GTE, Range | Filtrar pelo horário em que um alerta foi resolvido |
| ameaça | inteiro | EQ, NEQ | Filtrar por risco |
| alertType | inteiro | EQ, NEQ | Filtrar por tipo de alerta |
| ID | string | EQ, NEQ | Filtrar por IDs de alerta |
| origem | cadeia de caracteres | eq | A origem do alerta, seja ela interna ou |

[!INCLUDE [Open support ticket](includes/support.md)]

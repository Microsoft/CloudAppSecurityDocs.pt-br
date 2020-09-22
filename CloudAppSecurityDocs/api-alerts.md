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
ms.openlocfilehash: 54aa8efa3ad214ff55f3800ffb95126766e549e4
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90880652"
---
# <a name="alerts-api"></a>API de alertas

[!INCLUDE [Banner for top of topics](includes/banner.md)]

A API de alertas fornece informações sobre os riscos imediatos identificados por Cloud App Security e exigem atenção. Os alertas podem resultar de padrões de uso suspeitos ou de arquivos que contenham conteúdo que viole a política da empresa.

O seguinte lista as solicitações com suporte:

- [Listar alertas](api-alerts-list.md)
- [Ignorar em massa](api-alerts-bulk-dismiss.md)
- [Resolver em massa](api-alerts-bulk-resolve.md)
- [Buscar alerta](api-alerts-fetch.md)
- [Ignorar alerta](api-alerts-dismiss.md)
- [Marcar alerta como lido](api-alerts-mark-read.md)
- [Marcar alerta como não lido](api-alerts-mark-unread.md)

## <a name="filters"></a>Filtros

Para obter informações sobre como os filtros funcionam, consulte [filtros](api-introduction.md#filters).

A tabela a seguir descreve os filtros com suporte:

| Filtrar | Tipo | Operadores | Descrição |
| --- | --- | --- | --- |
| entidade. entidade | CP de entidade | EQ, NEQ | Filtrar alertas relacionados a entidades especificadas. Exemplo: `[{ "id": "entity-id", "saas": 11161, "inst": 0 }]` |
| Entity. IP | string | EQ, NEQ | Filtrar alertas relacionados a endereços IP especificados |
| entidade. serviço | Número inteiro | EQ, NEQ | Filtrar alertas relacionados à appId de serviço especificada, por exemplo: 11770 |
| entidade. instância | Número inteiro | EQ, NEQ | Filtrar alertas relacionados às instâncias especificadas, por exemplo: 11770, 1059065 |
| entidade. política | string | EQ, NEQ | Filtrar alertas relacionados às políticas especificadas |
| entidade. arquivo | string | EQ, NEQ | Filtrar alertas relacionados ao arquivo especificado |
| severidade | Número inteiro | EQ, NEQ | Filtrar por severidade. Os valores possíveis incluem:<br /><br />**0**: baixo<br />**1**: média<br/>**2**: alta |
| resolutionStatus | Número inteiro | EQ, NEQ | Filtrar por status de resolução de alerta, os valores possíveis incluem:<br /><br />**0**: abrir<br />**1**: ignorado<br />**2**: resolvido |
| read | booleano | eq | Se definido como "true", retorna somente alertas de leitura, se definido como "false", retorna alertas não lidos |
| Data | timestamp | LTE, GTE, Range, lte_ndays, gte_ndays | Filtrar pela hora em que um alerta foi disparado |
| resolutionDate | timestamp | LTE, GTE, Range | Filtrar pelo horário em que um alerta foi resolvido |
| ameaça | Número inteiro | EQ, NEQ | Filtrar por risco |
| alertType | Número inteiro | EQ, NEQ | Filtrar por tipo de alerta |
| ID | string | EQ, NEQ | Filtrar por IDs de alerta |
| source | string | eq | A origem do alerta, seja ela interna ou |

[!INCLUDE [Open support ticket](includes/support.md)]

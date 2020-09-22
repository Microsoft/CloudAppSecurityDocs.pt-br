---
title: Listar API de entidades
description: Este artigo descreve a solicitação de lista na API de entidades do Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 389aa799595a0f3f2721f159df4399cea90dcbbd
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90881209"
---
# <a name="list---entities-api"></a>Listar API de entidades

[!INCLUDE [Banner for top of topics](includes/banner.md)]

> [!NOTE]
> Esta solicitação não está disponível para o Office 365 Cloud App Security.

Execute a solicitação GET ou POST para buscar uma lista de entidades que correspondem aos filtros especificados.

## <a name="http-request"></a>Solicitação HTTP

```rest
GET /api/v1/entities/
```

```rest
POST /api/v1/entities/
```

## <a name="request-body-parameters"></a>Parâmetros do corpo da solicitação

| Parâmetro | Descrição |
| --- | --- |
| filtros | Filtrar objetos com todos os filtros de pesquisa para a solicitação, consulte [filtros de entidade](api-entities.md#filters) para obter mais detalhes |
| sortDirection | A direção da classificação. Os valores possíveis são: `asc` e `desc` |
| tipo de classificação | Campos usados para classificar entidades. Os valores possíveis são:<br /><br />**Data**: a data em que a entidade foi criada<br /><br />**severidade**: a severidade da entidade |
| skip | Ignora o número especificado de registros |
| limite | Número máximo de registros retornados pela solicitação |

## <a name="example"></a>Exemplo

### <a name="request"></a>Solicitação

Veja um exemplo da solicitação.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/entities/" -d '{
  "filters": {
    // some filters
  },
  "skip": 5,
  "limit": 10
  ...
}'
```

### <a name="response"></a>Resposta

Retorna uma lista de atividades no formato JSON.

```json
{
  "total": 5 // total number of records
  "hasNext": true // whether there is more data to show or not.
  "data": [
    // returned records
  ]
}
```

[!INCLUDE [Open support ticket](includes/support.md)]

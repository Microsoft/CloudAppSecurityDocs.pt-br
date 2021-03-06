---
title: API de alertas de lista
description: Este artigo descreve a solicitação de lista na API de alertas do Cloud App Security.
ms.date: 03/27/2020
ms.topic: reference
ms.openlocfilehash: 3c3dec04dff5369120decdfc6142d0517eca4e2a
ms.sourcegitcommit: 90df07ce9cd64fd9c46fb6563f0249079204e174
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/04/2021
ms.locfileid: "97859030"
---
# <a name="list---alerts-api"></a>API de alertas de lista

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Execute a solicitação GET ou POST para buscar uma lista de alertas que correspondem aos filtros especificados.

## <a name="http-request"></a>Solicitação HTTP

```rest
GET /api/v1/alerts/
```

```rest
POST /api/v1/alerts/
```

## <a name="request-body-parameters"></a>Parâmetros do corpo da solicitação

| Parâmetro | Descrição |
| --- | --- |
| filtros | Filtrar objetos com todos os filtros de pesquisa para a solicitação, consulte [filtros de alerta](api-alerts.md#filters) para obter mais detalhes |
| sortDirection | A direção da classificação. Os valores possíveis são: `asc` e `desc` |
| tipo de classificação | Campos usados para classificar alertas. Os valores possíveis são:<br />- **Data**: a data em que o alerta foi criado<br />- **severidade**: a severidade do alerta |
| skip | Ignora o número especificado de registros |
| limite | Número máximo de registros retornados pela solicitação |

## <a name="example"></a>Exemplo

### <a name="request"></a>Solicitação

Veja um exemplo da solicitação.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/alerts/" -d '{
  "filters": {
    // some filters
  },
  "skip": 5,
  "limit": 10
  ...
}'
```

### <a name="response"></a>Resposta

Retorna uma lista de alertas no formato JSON.

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

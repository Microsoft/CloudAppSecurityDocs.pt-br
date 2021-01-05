---
title: API de atividades de lista
description: Este artigo descreve a solicitação de lista na API de atividades do Cloud App Security.
ms.date: 03/27/2020
ms.topic: reference
ms.openlocfilehash: 277dfc0a42b258072a35c14d544ef9fbac4cdb7b
ms.sourcegitcommit: 90df07ce9cd64fd9c46fb6563f0249079204e174
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/04/2021
ms.locfileid: "97858996"
---
# <a name="list---activities-api"></a>API de atividades de lista

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Execute a solicitação GET ou POST para buscar uma lista de atividades que correspondem aos filtros especificados.

## <a name="http-request"></a>Solicitação HTTP

```rest
GET /api/v1/activities/
```

```rest
POST /api/v1/activities/
```

## <a name="request-body-parameters"></a>Parâmetros do corpo da solicitação

| Parâmetro | Descrição |
| --- | --- |
| filtros | Filtrar objetos com todos os filtros de pesquisa para a solicitação, consulte [filtros de atividade](api-activities.md#filters) para obter mais detalhes |
| sortDirection | A direção da classificação. Os valores possíveis são: `asc` e `desc` |
| tipo de classificação | Campos usados para classificar atividades. Os valores possíveis são:<br />- **Data**: a data em que a atividade ocorreu<br />- **criado**: o carimbo de data/hora quando a atividade foi salva |
| skip | Ignora o número especificado de registros |
| limite | Número máximo de registros retornados pela solicitação |

## <a name="example"></a>Exemplo

### <a name="request"></a>Solicitação

Veja um exemplo da solicitação.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/activities/" -d '{
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

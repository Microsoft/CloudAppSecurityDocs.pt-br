---
title: Listar API de entidades
description: Este artigo descreve a solicitação de lista na API de entidades do Cloud App Security.
ms.date: 03/27/2020
ms.topic: reference
ms.openlocfilehash: a93fa00db40720d8b8bf31a8494ce949402bca0b
ms.sourcegitcommit: 90df07ce9cd64fd9c46fb6563f0249079204e174
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/04/2021
ms.locfileid: "97858962"
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
| tipo de classificação | Campos usados para classificar entidades. Os valores possíveis são:<br />- **Data**: a data em que a entidade foi criada<br />- **severidade**: a severidade da entidade |
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

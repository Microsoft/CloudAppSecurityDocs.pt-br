---
title: Listar API de enriquecimento de dados
description: Este artigo descreve a solicitação de lista na API de enriquecimento de dados do Cloud App Security.
ms.date: 12/13/2020
ms.topic: reference
ms.openlocfilehash: a817431dc7788900294b8f6fde26beb326a21d87
ms.sourcegitcommit: 90df07ce9cd64fd9c46fb6563f0249079204e174
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/04/2021
ms.locfileid: "97859162"
---
# <a name="list---data-enrichment-api"></a>Listar API de enriquecimento de dados

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Execute a solicitação GET ou POST para buscar uma lista de intervalos de IP que correspondem aos filtros especificados.

## <a name="http-request"></a>Solicitação HTTP

```rest
GET /api/v1/subnet/
```

```rest
POST /api/v1/subnet/
```

## <a name="request-body-parameters"></a>Parâmetros do corpo da solicitação

| Parâmetro | Descrição |
| --- | --- |
| filtros | Filtrar objetos com todos os filtros de pesquisa para a solicitação, consulte [filtros de intervalo de IP](api-data-enrichment.md#filters) para obter mais detalhes |
| sortDirection | A direção da classificação. Os valores possíveis são: `asc` e `desc` |
| tipo de classificação | Campos usados para classificar intervalos de IP. Os valores possíveis são:<br />- **categoria**: a categoria do intervalo de IPS<br />- **marcas**: as marcas do intervalo de IPS<br />- **nome**: o nome do intervalo de IP |
| skip | Ignora o número especificado de registros |
| limite | Número máximo de registros retornados pela solicitação |

## <a name="example"></a>Exemplo

### <a name="request"></a>Solicitação

Veja um exemplo da solicitação.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/subnet/" -d '{
  "filters": {
    // some filters
  },
  "skip": 5,
  "limit": 10
  ...
}'
```

### <a name="response"></a>Resposta

Retorna uma lista de intervalos de IP no formato JSON. Para obter informações sobre os campos de resposta, consulte [Propriedades](api-data-enrichment.md#properties).

```json
{
  "total": 1 // total number of records
  "hasNext": false // whether there is more data to show or not.
  "data": [
    {
      // returned records
      "_id": "5fd767259cd24bb563567d7c",
      "name": "range name",
      "subnets": [
        {
          "mask": 112,
          "address": "0000:0000:0000:0000:0000:ffff:c5c6:0000",
          "originalString": "197.198.192.20/16"
        }
      ],
      "location": {
        "name": "United States",
        "latitude": 39.5035514831543,
        "longitude": -99.01830291748047,
        "countryCode": "US",
        "countryName": "United States"
      },
      "organization": "isp name",
      "tags": [
        {
          "_id": "5ce2aaf42207ad108c76fa3a",
          "id": "000000290000000000000000",
          "target": 1,
          "type": 2,
          "name": "Contoso",
          "nameTemplate": {
            "template": "SAGE_BUILTIN_TAG_CONTOSO_NAME"
          },
          "description": "IP addresses used by Contoso",
          "descriptionTemplate": {
            "template": "SAGE_BUILTIN_TAG_CONTOSO_DESCRIPTION"
          },
          "visibility": 0,
          "status": 0,
          "_tid": 113348336
        }
      ],
      "category": 5,
      "lastModified": 1607952165309.8032,
      "_tid": 113348336
    }
  ]
}
```

[!INCLUDE [Open support ticket](includes/support.md)]

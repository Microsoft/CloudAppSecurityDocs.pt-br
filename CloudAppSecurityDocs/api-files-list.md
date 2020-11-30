---
title: API de arquivos de lista
description: Este artigo descreve a solicitação de lista na API de arquivos do Cloud App Security.
ms.date: 03/27/2020
ms.topic: reference
ms.openlocfilehash: 644bfea227212e5b988eebc7e05aca8694a49f92
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96313994"
---
# <a name="list---files-api"></a>API de arquivos de lista

[!INCLUDE [Banner for top of topics](includes/banner.md)]

> [!NOTE]
>
> - Essa API em breve será preterida. Microsoft Cloud App Security está desenvolvendo uma nova solução para identificar e agir em arquivos que violam as políticas.
> - Esse ponto de extremidade pode atingir o tempo limite ao filtrar e paginar coleções grandes.
> - Esta API não está disponível para o Office 365 Cloud App Security.

Execute a solicitação GET ou POST para buscar uma lista de arquivos que correspondem aos filtros especificados.

## <a name="http-request"></a>Solicitação HTTP

```rest
GET /api/v1/files/
```

```rest
POST /api/v1/files/
```

## <a name="request-body-parameters"></a>Parâmetros do corpo da solicitação

| Parâmetro | Descrição |
| --- | --- |
| filtros | Filtrar objetos com todos os filtros de pesquisa para a solicitação, consulte [filtros de arquivo](api-files.md#filters) para obter mais detalhes |
| skip | Ignora o número especificado de registros |
| limite | Número máximo de registros retornados pela solicitação |

## <a name="example"></a>Exemplo

### <a name="request"></a>Solicitação

Veja um exemplo da solicitação.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/files/" -d '{
  "filters": {
    // some filters
  },
  "skip": 5,
  "limit": 10
  ...
}'
```

### <a name="response"></a>Resposta

Retorna uma lista de arquivos no formato JSON.

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

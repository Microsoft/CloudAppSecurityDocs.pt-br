---
title: API de busca-atividades
description: Este artigo descreve a solicitação de busca na API de atividades do Cloud App Security.
ms.date: 03/27/2020
ms.topic: reference
ms.openlocfilehash: dc26c22748aa2a03e7a59208b691c6a3a92527d6
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96314708"
---
# <a name="fetch---activities-api"></a>API de busca-atividades

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Execute a solicitação GET para buscar a atividade que corresponde à chave primária especificada.

## <a name="http-request"></a>Solicitação HTTP

```rest
GET /api/v1/activities/<pk>/
```

## <a name="request-url-parameters"></a>Parâmetros da URL de solicitação

| Parâmetro | Descrição |
| --- | --- |
| pk | A ID da atividade |

## <a name="example"></a>Exemplo

### <a name="request"></a>Solicitação

Veja um exemplo da solicitação.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/activities/<pk>/"
```

### <a name="response"></a>Resposta

Retorna a atividade especificada no formato JSON.

```json
{
  // activity record
}
```

[!INCLUDE [Open support ticket](includes/support.md)]

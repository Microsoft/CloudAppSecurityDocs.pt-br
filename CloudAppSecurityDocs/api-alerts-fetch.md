---
title: API de busca de alertas
description: Este artigo descreve a solicitação de busca na API de alertas do Cloud App Security.
ms.date: 03/27/2020
ms.topic: reference
ms.openlocfilehash: 8332805803dc05d991ef153b8402afb39b7b0cc1
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96314606"
---
# <a name="fetch---alerts-api"></a>API de busca de alertas

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Execute a solicitação GET para buscar o alerta correspondente à chave primária especificada.

## <a name="http-request"></a>Solicitação HTTP

```rest
GET /api/v1/alerts/<pk>/
```

## <a name="request-url-parameters"></a>Parâmetros da URL de solicitação

| Parâmetro | Descrição |
| --- | --- |
| pk | A ID do alerta |

## <a name="example"></a>Exemplo

### <a name="request"></a>Solicitação

Veja um exemplo da solicitação.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/alerts/<pk>/"
```

### <a name="response"></a>Resposta

Retorna o alerta especificado no formato JSON.

```json
{
  // alert record
}
```

[!INCLUDE [Open support ticket](includes/support.md)]

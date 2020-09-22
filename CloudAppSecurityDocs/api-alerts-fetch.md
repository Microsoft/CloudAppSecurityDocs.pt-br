---
title: API de busca de alertas
description: Este artigo descreve a solicitação de busca na API de alertas do Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 78ef3b8d2982a6f5228344b35f5d67dca9a6aec1
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90879842"
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

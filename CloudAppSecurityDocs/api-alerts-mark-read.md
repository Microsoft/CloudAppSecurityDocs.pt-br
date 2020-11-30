---
title: Marcar como API de alertas de leitura
description: Este artigo descreve a solicitação marcar como leitura na API de alertas do Cloud App Security.
ms.date: 03/27/2020
ms.topic: reference
ms.openlocfilehash: ecf314300e59371fc6cddaeddc0ab4b78efbaaa0
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96314579"
---
# <a name="mark-as-read---alerts-api"></a>Marcar como API de alertas de leitura

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Execute a solicitação POST para marcar o alerta correspondente à chave primária especificada como lido.

## <a name="http-request"></a>Solicitação HTTP

```rest
POST /api/v1/alerts/<pk>/read/
```

## <a name="request-url-parameters"></a>Parâmetros da URL de solicitação

| Parâmetro | Descrição |
| --- | --- |
| pk | A ID do alerta |

## <a name="example"></a>Exemplo

### <a name="request"></a>Solicitação

Veja um exemplo da solicitação.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/alerts/<pk>/read/"
```

[!INCLUDE [Open support ticket](includes/support.md)]

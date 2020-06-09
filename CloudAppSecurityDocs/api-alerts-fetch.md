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
ms.openlocfilehash: aff7a98093101585ce7ed451b1eb983bcc53dfa8
ms.sourcegitcommit: 286f8d5d940d1bb9a09daa3070ac4fc3768208f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84505525"
---
# <a name="fetch---alerts-api"></a>API de busca de alertas

*Aplica-se a: Microsoft Cloud App Security*

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
curl -XPOST -H "Authorization:<your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/alerts/<pk>/"
```

### <a name="response"></a>Resposta

Retorna o alerta especificado no formato JSON.

```json
{
  // alert record
}
```

[!INCLUDE [Open support ticket](includes/support.md)]

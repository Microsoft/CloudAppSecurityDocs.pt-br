---
title: Marcar como API de alertas de leitura
description: Este artigo descreve a solicitação marcar como leitura na API de alertas do Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 1f312bd7929c40efd056adcecd58b9bbd16c6516
ms.sourcegitcommit: 286f8d5d940d1bb9a09daa3070ac4fc3768208f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84505445"
---
# <a name="mark-as-read---alerts-api"></a>Marcar como API de alertas de leitura

*Aplica-se a: Microsoft Cloud App Security*

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
curl -XPOST -H "Authorization:<your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/alerts/<pk>/read/"
```

[!INCLUDE [Open support ticket](includes/support.md)]

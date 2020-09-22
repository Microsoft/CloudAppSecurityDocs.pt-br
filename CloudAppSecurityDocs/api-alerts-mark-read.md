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
ms.openlocfilehash: d3469f45ed36ea2089ef659e9181fef1857454b2
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90880693"
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

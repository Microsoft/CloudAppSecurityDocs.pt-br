---
title: API de descartar alertas
description: Este artigo descreve a solicitação de descarte na API de alertas do Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: efd8ced52fcad8d575242cb702fe6149f3345e20
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90879900"
---
# <a name="dismiss---alerts-api"></a>API de descartar alertas

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Execute a solicitação POST para ignorar o alerta correspondente à chave primária especificada.

## <a name="http-request"></a>Solicitação HTTP

```rest
POST /api/v1/alerts/<pk>/dismiss/
```

## <a name="request-url-parameters"></a>Parâmetros da URL de solicitação

| Parâmetro | Descrição |
| --- | --- |
| pk | A ID do alerta |

## <a name="request-body-parameters"></a>Parâmetros do corpo da solicitação

| Parâmetro | Descrição |
| --- | --- |
| comentário | Um comentário sobre por que o alerta foi descartado |

## <a name="example"></a>Exemplo

### <a name="request"></a>Solicitação

Veja um exemplo da solicitação.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/alerts/<pk>/dismiss/" -d '{
  "comment": "Irrelevant"
}'
```

[!INCLUDE [Open support ticket](includes/support.md)]

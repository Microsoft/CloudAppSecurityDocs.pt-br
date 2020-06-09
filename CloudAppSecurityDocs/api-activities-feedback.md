---
title: Comentários – API de atividades
description: Este artigo descreve a solicitação de comentários na API de atividades do Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: f95aa64c984484d62cea728def5efa729d22b185
ms.sourcegitcommit: 286f8d5d940d1bb9a09daa3070ac4fc3768208f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84505645"
---
# <a name="feedback-on-activity---activities-api"></a>Comentários sobre a API de atividades de atividade

*Aplica-se a: Microsoft Cloud App Security*

Execute a solicitação POST para enviar comentários sobre a atividade que corresponde à chave primária especificada.

## <a name="http-request"></a>Solicitação HTTP

```rest
POST /api/v1/activities/<pk>/feedback
```

## <a name="request-url-parameters"></a>Parâmetros da URL de solicitação

| Parâmetro | Descrição |
| --- | --- |
| pk | A ID da atividade |

## <a name="request-body-parameters"></a>Parâmetros do corpo da solicitação

| Parâmetro | Descrição |
| --- | --- |
| comentários | Os comentários para a atividade |

## <a name="example"></a>Exemplo

### <a name="request"></a>Solicitação

Veja um exemplo da solicitação.

```rest
curl -XPOST -H "Authorization:<your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/activities/<pk>/feedback" -d '{
  "feedbackValue": "0",
  "feedbackText": "Irrelevant",
  "allowContact": false,
  "contactEmail": "some.contact.address"
}'
```

### <a name="response"></a>Resposta

Retorna uma lista de atividades no formato JSON.

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

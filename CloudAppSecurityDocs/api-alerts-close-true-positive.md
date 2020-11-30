---
title: Fechar a verdadeira API de alertas positivos
description: Este artigo descreve o fechamento em massa de um alerta como uma solicitação true positiva na API de alertas do Cloud App Security.
ms.date: 10/20/2020
ms.topic: reference
ms.openlocfilehash: b501f28a098217074c5bbbe912f781ae69d33c23
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96314623"
---
# <a name="close-true-positive---alerts-api"></a>Fechar a verdadeira API de alertas positivos

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Execute a solicitação POST para fechar vários alertas que correspondem aos filtros especificados como verdadeiro positivo (um alerta em uma atividade mal-intencionada confirmada).

## <a name="http-request"></a>Solicitação HTTP

```rest
POST /api/v1/alerts/close_true_positive/
```

## <a name="request-body-parameters"></a>Parâmetros do corpo da solicitação

| Parâmetro | Descrição |
| --- | --- |
| filtros | Filtrar objetos com todos os filtros de pesquisa para a solicitação, consulte [filtros de alerta](api-alerts.md#filters) para obter mais detalhes |
| comentário | Um comentário sobre por que os alertas são ignorados |
| sendFeedback | Um valor booliano que indica que os comentários sobre esse alerta são fornecidos. Valor padrão: false |
| feedbackText | O texto dos comentários |
| allowContact | Um valor booliano que indica que o consentimento para entrar em contato com o usuário é fornecido. Valor padrão: false |
| contactEmail | O endereço de email do usuário |

## <a name="example"></a>Exemplo

### <a name="request"></a>Solicitação

Veja um exemplo da solicitação.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/alerts/close_true_positive" -d '{
  "filters": {
    "id": {
      "eq": [
        "55af7415f8a0a7a29eef2e1f",
        "55af741cf8a0a7a29eef2e20",
        "5f8d70bfc1ffb25b0a541c7d"
      ]
    }
  },
  "comment": "Irrelevant",
  "sendFeedback": true,
  "feedbackText": "Feedback text",
  "allowContact": true,
  "contactEmail": " user@contoso.com"
}'
```

[!INCLUDE [Open support ticket](includes/support.md)]

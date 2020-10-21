---
title: Fechar a API de alertas benignos
description: Este artigo descreve o fechamento em massa de um alerta como uma solicitação benigno na API de alertas do Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 10/20/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: aa28010c10702b917ebbfc3996b52161e0c66a46
ms.sourcegitcommit: ee40375712d2cc4090bd4e9cb58df486ec02aa62
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/21/2020
ms.locfileid: "92327011"
---
# <a name="close-benign---alerts-api"></a>Fechar a API de alertas benignos

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Execute a solicitação POST para fechar vários alertas que correspondem aos filtros especificados como benignos (um alerta em uma atividade suspeita, mas não mal-intencionada, como um teste de penetração ou outra ação suspeita autorizada).

## <a name="http-request"></a>Solicitação HTTP

```rest
POST /api/v1/alerts/close_benign/
```

## <a name="request-body-parameters"></a>Parâmetros do corpo da solicitação

| Parâmetro | Descrição |
| --- | --- |
| filtros | Filtrar objetos com todos os filtros de pesquisa para a solicitação, consulte [filtros de alerta](api-alerts.md#filters) para obter mais detalhes |
| comentário | Um comentário sobre por que os alertas são ignorados |
| reasonid | O motivo para fechar os alertas como benignos. Fornecer um motivo ajuda a melhorar a precisão da detecção ao longo do tempo. Os valores possíveis incluem:<br /><br />**2**: a severidade real é inferior<br />**4**: outros<br />**5**: confirmado com o usuário final<br />**6**: disparado por teste |
| sendFeedback | Um valor booliano que indica que os comentários sobre esse alerta são fornecidos. Valor padrão: false |
| feedbackText | O texto dos comentários |
| allowContact | Um valor booliano que indica que o consentimento para entrar em contato com o usuário é fornecido. Valor padrão: false |
| contactEmail | O endereço de email do usuário |

## <a name="example"></a>Exemplo

### <a name="request"></a>Solicitação

Veja um exemplo da solicitação.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/alerts/close_benign/" -d '{
  "filters": {
    "id": {
      "eq": [
        "55af7415f8a0a7a29eef2e1f",
        "55af741cf8a0a7a29eef2e20"
        "5f8d70bfc1ffb25b0a541c7d"
      ]
    }
  },
  "comment": "Irrelevant",
  "reasonId": 5,
  "sendFeedback": true,
  "feedbackText": "Feedback text",
  "allowContact": true,
  "contactEmail": " user@contoso.com"
}'
```

[!INCLUDE [Open support ticket](includes/support.md)]

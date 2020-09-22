---
title: API de busca-atividades
description: Este artigo descreve a solicitação de busca na API de atividades do Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 96d87db09134be35d5845c6b1755fdb24a26c2c7
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90880105"
---
# <a name="fetch---activities-api"></a>API de busca-atividades

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Execute a solicitação GET para buscar a atividade que corresponde à chave primária especificada.

## <a name="http-request"></a>Solicitação HTTP

```rest
GET /api/v1/activities/<pk>/
```

## <a name="request-url-parameters"></a>Parâmetros da URL de solicitação

| Parâmetro | Descrição |
| --- | --- |
| pk | A ID da atividade |

## <a name="example"></a>Exemplo

### <a name="request"></a>Solicitação

Veja um exemplo da solicitação.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/activities/<pk>/"
```

### <a name="response"></a>Resposta

Retorna a atividade especificada no formato JSON.

```json
{
  // activity record
}
```

[!INCLUDE [Open support ticket](includes/support.md)]

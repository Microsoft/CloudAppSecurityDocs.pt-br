---
title: API de busca-entidades
description: Este artigo descreve a solicitação de busca na API de entidades do Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 0ff0a93866652a0a4cc2e927593a2a56800c64de
ms.sourcegitcommit: cc283f0ecf8124953f1f71181655603de6846d8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87254650"
---
# <a name="fetch---entities-api"></a>API de busca-entidades

*Aplica-se a: Microsoft Cloud App Security*

> [!NOTE]
> Esta solicitação não está disponível para o Office 365 Cloud App Security.

Execute a solicitação GET para buscar a entidade correspondente à chave primária especificada.

## <a name="http-request"></a>Solicitação HTTP

```rest
GET /api/v1/entities/<pk>/
```

## <a name="request-url-parameters"></a>Parâmetros da URL de solicitação

| Parâmetro | Descrição |
| --- | --- |
| pk | Um dicionário com a ID da entidade, o SaaS e detalhes da instância codificados como uma cadeia de caracteres base64. Por exemplo: `{"id":"3fa9f28b-eb0e-463a-ba7b-8089fe9991e2","saas":11161,"inst":0}` codificado como uma cadeia de caracteres base64. |

## <a name="example"></a>Exemplo

### <a name="request"></a>Solicitação

Veja um exemplo da solicitação.

```rest
curl -XPOST -H "Authorization:<your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/entities/<pk>/"
```

### <a name="response"></a>Resposta

Retorna a entidade especificada no formato JSON.

```json
{
  // entity record
}
```

[!INCLUDE [Open support ticket](includes/support.md)]

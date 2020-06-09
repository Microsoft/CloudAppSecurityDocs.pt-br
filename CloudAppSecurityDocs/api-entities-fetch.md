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
ms.openlocfilehash: 536fe23d089d450c3ac1ce5bbfefb08dfb2ad383
ms.sourcegitcommit: 286f8d5d940d1bb9a09daa3070ac4fc3768208f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84505195"
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
| pk | A ID da entidade |

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

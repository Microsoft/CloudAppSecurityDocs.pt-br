---
title: Buscar árvore de entidade-API de entidades
description: Este artigo descreve a solicitação de busca de árvore de entidade na API de entidades do Cloud App Security.
ms.date: 03/27/2020
ms.topic: reference
ms.openlocfilehash: 70e01ffa31ddfe13434c0a1705f2af98b43de6b5
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96314283"
---
# <a name="fetch-entity-tree---entities-api"></a>Buscar árvore de entidade-API de entidades

[!INCLUDE [Banner for top of topics](includes/banner.md)]

> [!NOTE]
> Esta solicitação não está disponível para o Office 365 Cloud App Security.

Execute a solicitação GET para buscar todas as entidades relacionadas à entidade que corresponde à chave primária especificada. Se a entidade for um usuário, o buscará todas as contas associadas ao usuário. Se a entidade for uma conta, o buscará o pai e os irmãos da entidade.

## <a name="http-request"></a>Solicitação HTTP

```rest
GET /api/v1/entities/<pk>/retrieve_tree/
```

## <a name="request-url-parameters"></a>Parâmetros da URL de solicitação

| Parâmetro | Descrição |
| --- | --- |
| pk | A ID da entidade |

## <a name="example"></a>Exemplo

### <a name="request"></a>Solicitação

Veja um exemplo da solicitação.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/entities/<pk>/retrieve_tree/"
```

### <a name="response"></a>Resposta

Retorna a árvore de entidade especificada no formato JSON.

```json
{
  // entity tree record
}
```

[!INCLUDE [Open support ticket](includes/support.md)]

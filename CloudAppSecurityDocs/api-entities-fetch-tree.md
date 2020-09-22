---
title: Buscar árvore de entidade-API de entidades
description: Este artigo descreve a solicitação de busca de árvore de entidade na API de entidades do Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 8d01066d6195b3541045b15094432999dab98cc5
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90879736"
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

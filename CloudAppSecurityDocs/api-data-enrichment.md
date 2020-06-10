---
title: Criar intervalo de endereços IP-API de enriquecimento de dados
description: Este artigo descreve a solicitação criar intervalo de endereços IP na API de enriquecimento de dados do Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 22f19d6d1b03cec31f36f37a0b1bd112927af781
ms.sourcegitcommit: 3172d6bd5e9d7a08f5cd2aa2e36980ef21bf0235
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84563875"
---
# <a name="create-ip-address-range---data-enrichment-api"></a>Criar intervalo de endereços IP-API de enriquecimento de dados

*Aplica-se a: Microsoft Cloud App Security*

Execute a solicitação POST para adicionar um novo intervalo de endereços IP.

## <a name="http-request"></a>Solicitação HTTP

```rest
POST /api/subnet/
```

## <a name="request-body-parameters"></a>Parâmetros do corpo da solicitação

| Parâmetro | Descrição |
| --- | --- |
| category | A ID da categoria do intervalo |
| subredes | Uma matriz de máscaras como cadeias de caracteres (IPv4/IPv6) |
| organização (opcional) | O ISP registrado |
| marcas (opcional) | Uma matriz de marcas (objetos com a propriedade "text" definida com o nome da marca)-novo ou existente |

Atualmente, há suporte para as seguintes categorias:

| Categoria | ID |
| --- | -- |
| Corporativo | 1 |
| Administrativo | 2 |
| Situação | 3 |
| VPN | 4 |
| Provedor de nuvem | 5 |
| Outros | 6 |

## <a name="example"></a>Exemplo

### <a name="request"></a>Solicitação

Veja um exemplo da solicitação.

```rest
curl -XPOST -H "Authorization:<your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/subnet/create_rule/" -d '{
  "name":"range name",
  "category":5,
  "organization":"Microsoft",
  "subnets":[
    "192.168.1.0/24",
    "192.168.2.0/16"
  ],
  "tags":[
    "existing tag"
  ]
}'
```

### <a name="response"></a>Resposta

Retorna a ID do novo intervalo como uma cadeia de caracteres.

[!INCLUDE [Open support ticket](includes/support.md)]

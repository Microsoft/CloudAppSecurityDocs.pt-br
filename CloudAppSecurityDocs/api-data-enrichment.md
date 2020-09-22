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
ms.openlocfilehash: 2da4b992d0c9eab2830793d026c0fd37ccd390be
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90880619"
---
# <a name="create-ip-address-range---data-enrichment-api"></a>Criar intervalo de endereços IP-API de enriquecimento de dados

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Execute a solicitação POST para adicionar um novo intervalo de endereços IP.

## <a name="http-request"></a>Solicitação HTTP

```rest
POST /api/v1/subnet/
```

## <a name="request-body-parameters"></a>Parâmetros do corpo da solicitação

| Parâmetro | Descrição |
| --- | --- |
| category | A ID da categoria do intervalo |
| sub-redes | Uma matriz de máscaras como cadeias de caracteres (IPv4/IPv6) |
| organização (opcional) | O ISP registrado |
| marcas (opcional) | Uma matriz de marcas (objetos com a propriedade "text" definida com o nome da marca)-novo ou existente |

Atualmente, há suporte para as seguintes categorias:

| Categoria | ID |
| --- | -- |
| Corporativo | 1 |
| Administrativa | 2 |
| Situação | 3 |
| VPN | 4 |
| Provedor de nuvem | 5 |
| Outro | 6 |

## <a name="example"></a>Exemplo

### <a name="request"></a>Solicitação

Veja um exemplo da solicitação.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/subnet/create_rule/" -d '{
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

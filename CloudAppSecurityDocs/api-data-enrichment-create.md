---
title: Criar intervalo de endereços IP-API de enriquecimento de dados
description: Este artigo descreve a solicitação criar intervalo de endereços IP na API de enriquecimento de dados do Cloud App Security.
ms.date: 12/13/2020
ms.topic: reference
ms.openlocfilehash: 39cb7fc47146aec690b9418da28a2caa636749d0
ms.sourcegitcommit: 90df07ce9cd64fd9c46fb6563f0249079204e174
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/04/2021
ms.locfileid: "97859160"
---
# <a name="create-ip-address-range---data-enrichment-api"></a>Criar intervalo de endereços IP-API de enriquecimento de dados

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Execute a solicitação POST para adicionar um novo intervalo de endereços IP.

## <a name="http-request"></a>Solicitação HTTP

```rest
POST /api/v1/subnet/create_rule/
```

## <a name="request-body-parameters"></a>Parâmetros do corpo da solicitação

| Parâmetro | Descrição |
| --- | --- |
| name | O nome exclusivo do intervalo |
| category | A ID da categoria do intervalo. Fornecer uma categoria ajuda você a reconhecer facilmente as atividades de endereços IP interessantes. Os valores possíveis incluem:<br /><br />**1**: corporativo<br />**2**: administrativo<br />**3**: arriscado<br />**4**: VPN<br />**5**: provedor de nuvem<br />**6**: outros |
| sub-redes | Uma matriz de máscaras como cadeias de caracteres (IPv4/IPv6) |
| organização (opcional) | O ISP registrado |
| marcas (opcional) | Uma matriz de objetos novos ou existentes, incluindo o nome da marca, a ID, a descrição, o modelo de nome e a ID do locatário |

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

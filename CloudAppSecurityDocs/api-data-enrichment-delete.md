---
title: Excluir intervalo de endereços IP-API de enriquecimento de dados
description: Este artigo descreve a solicitação Excluir intervalo de endereços IP na API de enriquecimento de dados do Cloud App Security.
ms.date: 12/13/2020
ms.topic: reference
ms.openlocfilehash: 0cda04381501283526c77240debd7cfbe4f672fc
ms.sourcegitcommit: 90df07ce9cd64fd9c46fb6563f0249079204e174
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/04/2021
ms.locfileid: "97859165"
---
# <a name="delete-ip-address-range---data-enrichment-api"></a>Excluir intervalo de endereços IP-API de enriquecimento de dados

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Execute a solicitação de exclusão para excluir um intervalo de endereços IP.

## <a name="http-request"></a>Solicitação HTTP

```rest
DELETE /api/v1/subnet/<ip_range_id>/
```

## <a name="example"></a>Exemplo

### <a name="request"></a>Solicitação

Veja um exemplo da solicitação.

```rest
curl -X DELETE -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/subnet/<ip_range_id>/"
```

[!INCLUDE [Open support ticket](includes/support.md)]

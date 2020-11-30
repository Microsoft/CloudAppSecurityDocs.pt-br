---
title: API FETCH-files
description: Este artigo descreve a solicitação de busca na API de arquivos do Cloud App Security.
ms.date: 03/27/2020
ms.topic: reference
ms.openlocfilehash: 7d3faf9630edf3e277b481d5f8bcea87898e67cd
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96314045"
---
# <a name="fetch---files-api"></a>API FETCH-files

[!INCLUDE [Banner for top of topics](includes/banner.md)]

> [!NOTE]
>
> - Essa API em breve será preterida. Microsoft Cloud App Security está desenvolvendo uma nova solução para identificar e agir em arquivos que violam as políticas.
> - Esta API não está disponível para o Office 365 Cloud App Security.

Execute a solicitação GET para buscar o arquivo que corresponde à chave primária especificada.

## <a name="http-request"></a>Solicitação HTTP

```rest
GET /api/v1/files/<pk>/
```

## <a name="request-url-parameters"></a>Parâmetros da URL de solicitação

| Parâmetro | Descrição |
| --- | --- |
| pk | A ID do arquivo |

## <a name="example"></a>Exemplo

### <a name="request"></a>Solicitação

Veja um exemplo da solicitação.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/files/<pk>/"
```

### <a name="response"></a>Resposta

Retorna o arquivo especificado.

[!INCLUDE [Open support ticket](includes/support.md)]

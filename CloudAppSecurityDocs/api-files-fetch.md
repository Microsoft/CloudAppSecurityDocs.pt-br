---
title: API FETCH-files
description: Este artigo descreve a solicitação de busca na API de arquivos do Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 5127f1e09fc5cd34ce0a45fd05ed1714e94cd94a
ms.sourcegitcommit: 288f3011c0ce0e5f2d8cbaa9057a63be044465f7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2020
ms.locfileid: "94375051"
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

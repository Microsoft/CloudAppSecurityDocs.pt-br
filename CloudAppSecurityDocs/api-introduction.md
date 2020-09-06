---
title: API REST do Cloud App Security
description: Este artigo descreve como interagir com Cloud App Security sobre HTTPS.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 31190fd4df5dc9c3bac19794ff1fd78c4982100d
ms.sourcegitcommit: 5ace3437d49c7bbde2266a6f1565a65a379b9c2c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2020
ms.locfileid: "89499485"
---
# <a name="cloud-app-security-rest-api"></a>API REST do Cloud App Security

*Aplica-se a: Microsoft Cloud App Security*

Este artigo descreve como interagir com Cloud App Security sobre HTTPS.

A API do Microsoft Cloud App Security fornece acesso programático ao Cloud App Security por meio de pontos de extremidade API REST. Aplicativos podem usar a API para realizar operações de leitura e atualização nos dados e objetos do Cloud App Security. Por exemplo, a API de segurança do aplicativo de nuvem dá suporte às seguintes operações comuns para um objeto de usuário:

- Carregar arquivos de log para o Cloud Discovery
- Gerar scripts de bloqueio
- Listar atividades e alertas
- Descartar ou resolver alertas

## <a name="api-url-structure"></a>Estrutura de URL da API

Para usar a API de Cloud App Security, você deve primeiro obter a URL de API do seu locatário. A URL da API usa o seguinte formato: `https://<portal_url>/api/<endpoint>` .

Para obter a URL do portal Cloud App Security para seu locatário, execute as seguintes etapas:

1. No portal do Cloud App Security, clique no **ícone de ponto de interrogação** na barra de menus. Em seguida, selecione **Sobre**.

    ![clique em Sobre](media/about-menu.png)

1. Na tela Cloud App Security sobre, você pode ver a URL do Portal.

    ![Exibir seu data center](media/api-url.png)

Depois que você tiver a URL do portal, adicione o `/api` sufixo a ela para obter a URL da API. Por exemplo, se a URL do portal for `https://mytenant.us2.contoso.com` , a URL da API será `https://mytenant.us2.contoso.com/api` .

## <a name="api-tokens"></a>Tokens de API

Cloud App Security requer um token de API no cabeçalho de todas as solicitações de API para o servidor, como o seguinte:

```http
Authorization: Token <your_token_key>
```

Onde `<your_token_key>` é seu token de API pessoal.

Para obter mais informações sobre tokens de API, consulte [Gerenciando tokens de API](api-authentication.md).

### <a name="example"></a>Exemplo

```rest
curl -XGET -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/example-endpoint"
```

## <a name="what-actions-are-supported"></a>Há suporte para quais ações?

A tabela a seguir descreve as ações com suporte:

|Recurso|Verbos HTTP|Rotas de URI|
|---|---|---|
|Descoberta|GET, POST ou PUT|/api/v1/discovery/|
|Enriquecimento de dados|POST|/api/subnet/|
|Atividades|GET ou POST|/api/v1/activities/|
|Alertas|GET ou POST|/api/v1/alerts/|
|Entidades|GET ou POST|/api/v1/entities/|
|Arquivos|GET ou POST|/api/v1/files/|

Em que **Resource** representa um grupo de entidades relacionadas.

## <a name="what-field-types-are-supported"></a>Quais tipos de campo têm suporte?

A tabela a seguir descreve os tipos de campo com suporte:

|Campo|Descrição|
|---|---|
|string|Uma cadeia de caracteres textual|
|booleano|Um valor booliano que representa true/false|
|inteiro|Inteiro com sinal de 32 bits|
|timestamp|Milissegundos desde a época|

## <a name="limits"></a>limites

Você pode optar por limitar suas solicitações fornecendo um parâmetro Limit na solicitação.

Os métodos a seguir têm suporte para fornecer o parâmetro Limit:

- Codificado por URL (com `Content-Type: application/x-www-form-urlencoded` cabeçalho)
- Dados de formulário
- Corpo JSON (com `Content-Type: multipart/form-data` e um cabeçalho de limite apropriado)

> [!NOTE]
>
> - Se nenhum limite for fornecido, um padrão de 100 será definido.
> - As respostas para todas as solicitações feitas com o token de API são limitadas a um máximo de 100 itens.
> - O limite de limitação para todas as solicitações de API é de 30 solicitações por minuto por locatário.

## <a name="filters"></a>Filtros

Quando você tiver um grande número de resultados, achará útil ajustar as solicitações usando filtros. Esta seção descreve a estrutura de e os operadores que podem ser usados com filtros do.

### <a name="structure"></a>Estrutura

Alguns dos nossos pontos de extremidade de API dão suporte a filtros ao executar consultas. Em suas seções relevantes, você encontrará uma referência listando todos os campos filtráveis disponíveis e os operadores com suporte para esse recurso.

A maioria dos filtros dá suporte a vários valores para fornecer a você consultas poderosas. Ao combinar filtros e operadores, usamos e como o operador lógico entre os filtros.

### <a name="example"></a>Exemplo

```rest
curl -XGET -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/example-endpoint" -d '{
  "filters": {
    "some.field": {
      "eq": ["value1", "value2"],
      "isset": true
    },
    "some.field2": {
      "gte": 5
    }
  },
  "skip": 5,
  "limit": 10
}'
```

### <a name="operators"></a>Operadores

> [!NOTE]
> Nem todos os operadores são compatíveis com todos os filtros.

A tabela a seguir descreve os operadores com suporte:

| Operador | Tipo de resposta | Descrição |
| --- | --- | --- |
| contains | lista de cadeias de caracteres | Retorna todos os registros relevantes contendo uma das cadeias de caracteres fornecidas |
| deq | lista de valores | Retorna todos os registros que contêm um valor que não é igual a um dos valores fornecidos |
| descendantof | lista de valores | Retorna todos os registros relevantes correspondentes a valores ou descendentes deles |
| doesnotstartwith | lista de cadeias de caracteres | Retorna todos os registros relevantes que não começam com cada uma das cadeias de caracteres fornecidas |
| endswith | lista de cadeias de caracteres | Retorna todos os registros relevantes que terminam com uma das cadeias de caracteres fornecidas |
| eq | lista de valores | Retorna todos os registros relevantes contendo um dos valores fornecidos |
| gt | valor único | Retorna todos os registros cujo valor é maior que o valor fornecido |
| gte | valor único | Retorna todos os registros cujo valor é maior ou igual ao valor fornecido |
| gte_ndays | número | Retorna todos os registros com data posterior a N dias atrás |
| isnotset | booleano | Quando definido como "true", retorna todos os registros relevantes que não têm um valor no campo especificado |
| isset | booleano | Quando definido como "true", retorna todos os registros relevantes que têm um valor no campo especificado |
| lt | valor único | Retorna todos os registros cujo valor é menor que o valor fornecido |
| LTE | valor único | Retorna todos os registros cujo valor é menor ou igual ao valor fornecido |
| lte_ndays | número | Retorna todos os registros com data anterior a N dias atrás |
| ncontains | lista de cadeias de caracteres | Retorna todos os registros relevantes que não contêm uma das cadeias de caracteres fornecidas |
| ndescendantof | lista de valores | Retorna todos os registros relevantes que não correspondem a valores ou descendentes deles |
| NEQ | lista de valores | Retorna todos os registros relevantes que não contêm todos os valores fornecidos |
| range | lista de objetos que contêm os campos "Start" e "End" | Retorna todos os registros dentro de um dos intervalos fornecidos |
| startswith | lista de cadeias de caracteres | Retorna todos os registros relevantes começando com uma das cadeias de caracteres fornecidas |
| startswithsingle | string | Retorna todos os registros relevantes que começam com a cadeia de caracteres fornecida |
| text | string | Executa uma pesquisa de texto completo de todos os registros |

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Autenticação de API](api-authentication.md)

[!INCLUDE [Open support ticket](includes/support.md)]

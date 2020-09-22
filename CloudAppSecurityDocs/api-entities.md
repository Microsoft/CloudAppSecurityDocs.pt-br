---
title: API de entidades de Cloud App Security
description: Este artigo fornece informações sobre como usar a API de entidades.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 9b6d7c4428b8383a4107a824a6113fcd3362dfa1
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90881095"
---
# <a name="entities-api"></a>API de Entidades

[!INCLUDE [Banner for top of topics](includes/banner.md)]

> [!NOTE]
> Esta API não está disponível para o Office 365 Cloud App Security.

A API de entidades fornece informações básicas sobre os usuários e contas usando os aplicativos de nuvem da sua organização, permitindo que você entenda os padrões de uso do serviço.

O seguinte lista as solicitações com suporte:

- [Listar entidades](api-entities-list.md)
- [Buscar entidade](api-entities-fetch.md)
- [Buscar árvore de entidades](api-entities-fetch-tree.md)

## <a name="filters"></a>Filtros

Para obter informações sobre como os filtros funcionam, consulte [filtros](api-introduction.md#filters).

A tabela a seguir descreve os filtros com suporte:

| Filtrar | Tipo | Operadores | Descrição |
| --- | --- | --- | --- |
| type| string | EQ, NEQ | Filtrar entidades por tipo |
| isAdmin | string | eq | Filtrar entidades que são administradores |
| entidade | CP de entidade | EQ, NEQ | Filtre entidades com entidades específicas PKS. Se um usuário for selecionado, retornará também todas as suas contas. Exemplo: `[{ "id": "entity-id", "saas": 11161, "inst": 0 }]` |
| USERGROUPS |string | EQ, NEQ | Filtrar entidades por suas IDs de grupo associadas |
| app | Número inteiro | EQ, NEQ | Filtre entidades usando serviços com a ID de SaaS especificada, por exemplo: 11770 |
| instance | Número inteiro | EQ, NEQ | Filtre entidades usando serviços com o Appstances especificado (ID de SaaS e ID de instância), por exemplo: 11770, 1059065 |
| IsExternal | booleano | eq | A afiliação da entidade. Os valores possíveis incluem:<br /><br />**true**: externo<br />**false**: interno<br />**NULL**: nenhum valor |
| domínio | string | EQ, NEQ, isset, isnotset | O domínio relacionado da entidade |
| organization | string | EQ, NEQ, isset, isnotset | Filtrar entidades com a unidade organizacional especificada |
| lastSeen | timestamp | LTE, GTE, | entidades de filtro de intervalo que foram vistas pela última vez entre as datas determinadas |
| status | string | EQ, NEQ | Filtrar entidades por status. Os valores possíveis incluem:<br /><br />**0**: N/A<br />**1**: preparado<br />**2**: ativo<br />**3**: suspenso<br />**4**: excluído |
| score | Número inteiro | lt, gt, isset, isnotset | Filtrar entidades por sua pontuação de prioridade de investigação |

[!INCLUDE [Open support ticket](includes/support.md)]

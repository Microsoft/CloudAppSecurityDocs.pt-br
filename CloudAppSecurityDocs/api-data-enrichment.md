---
title: API de enriquecimento de dados Cloud App Security
description: Este artigo fornece informações sobre como usar a API de enriquecimento de dados.
ms.date: 12/13/2020
ms.topic: reference
ms.openlocfilehash: d2050afec68bc29b0f401188b60c3dbb631a4a1b
ms.sourcegitcommit: 0768aa1992819e2651a14a731f79e178fdececc5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/12/2021
ms.locfileid: "98114744"
---
# <a name="data-enrichment-api"></a>API de enriquecimento de dados

[!INCLUDE [Banner for top of topics](includes/banner.md)]

A API de enriquecimento de dados permite que você gerencie intervalos de endereços IP identificáveis, como seus endereços IP físicos do Office. Os intervalos de endereços IP permitem que você marque, categorize e personalize a maneira como os logs e os alertas são exibidos e investigados. Para obter mais informações, consulte [trabalhando com intervalos de IP e marcas](ip-tags.md).

O seguinte lista as solicitações com suporte:

- [Listar intervalos de endereços IP](api-data-enrichment-list.md)
- [Criar intervalo de endereços IP](api-data-enrichment-create.md)
- [Atualizar intervalo de endereços IP](api-data-enrichment-update.md)
- [Excluir intervalo de endereços IP](api-data-enrichment-delete.md)

## <a name="properties"></a>Propriedades

O objeto de resposta define as propriedades a seguir.

| Propriedade | Type | Descrição |
| --- | --- | --- |
| total | INT | Número total de registros |
| hasNext | bool | Indica se há registros adicionais |
| data | list | Lista dos registros existentes |
| _id | string | ID exclusiva do intervalo de IP |
| name | string | O nome exclusivo do intervalo |
| sub-redes | list | Uma matriz de máscaras, endereços IP (IPv4/IPv6) e cadeias de caracteres originais |
| local | string | Um objeto que inclui o nome do local, latitude, longitude, código do país e nome do país |
| organization | string | O ISP registrado |
| marcas| list | Uma matriz de objetos novos ou existentes, incluindo o nome da marca, a ID, a descrição, o modelo de nome e a ID do locatário |
| category | INT | A categoria do intervalo de IP. Fornecer uma categoria ajuda você a reconhecer facilmente as atividades de endereços IP interessantes. Os valores possíveis incluem:<br /><br />**1**: corporativo<br />**2**: administrativo<br />**3**: arriscado<br />**4**: VPN<br />**5**: provedor de nuvem<br />**6**: outros |
| lastModified | long | Carimbo de data/hora da última regra alterada |

## <a name="filters"></a>Filtros

Para obter informações sobre como os filtros funcionam, consulte [filtros](api-introduction.md#filters).

A tabela a seguir descreve os filtros com suporte:

| Filtrar | Type | Operadores | Descrição |
| --- | --- | --- | --- |
| category | inteiro | EQ, NEQ | Filtrar intervalos de IP por categoria. Os valores possíveis incluem:<br /><br />**1**: corporativo<br />**2**: administrativo<br />**3**: arriscado<br />**4**: VPN<br />**5**: provedor de nuvem<br />**6**: outros |
| marcas | string | EQ, NEQ | Filtrar intervalos de IP por IDs de marca |
| builtIn | bool | eq | Filtrar intervalos de IP por tipo. Os valores possíveis incluem: **verdadeiro** (interno) ou **falso** (personalizado) |

[!INCLUDE [Open support ticket](includes/support.md)]

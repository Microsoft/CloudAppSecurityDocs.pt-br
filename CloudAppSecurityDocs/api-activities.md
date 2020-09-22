---
title: API de atividades Cloud App Security
description: Este artigo fornece informações sobre como usar a API de atividades.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 9ba5e83c10406308a1faf6e323fcfb9837da4b12
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90880040"
---
# <a name="activities-api"></a>API de atividades

[!INCLUDE [Banner for top of topics](includes/banner.md)]

A API de atividade fornece visibilidade de todas as ações executadas em seus aplicativos de nuvem. Os dados dessa API podem fornecer informações sobre quem faz logon em qual aplicativo e quando, quais arquivos estão sendo baixados de locais suspeitos e assim por diante.

O seguinte lista as solicitações com suporte:

- [Listar atividades](api-activities-list.md)
- [Buscar atividade](api-activities-fetch.md)
- [Comentários sobre a atividade](api-activities-feedback.md)

## <a name="filters"></a>Filtros

Para obter informações sobre como os filtros funcionam, consulte [filtros](api-introduction.md#filters).

A tabela a seguir descreve os filtros com suporte:

| Filtrar | Tipo | Operadores | Descrição |
| --- | --- | --- | --- |
| serviço | Número inteiro | EQ, NEQ | Filtrar atividades relacionadas à appID de serviço especificada, por exemplo: 11770 |
| instance | Número inteiro | EQ, NEQ | Filtrar atividades de instâncias especificadas |
| User. orgUnit | string | EQ, NEQ, isset, isnotset | Filtrar atividades pela unidade organizacional do usuário em execução |
| Activity. eventType | string | EQ, NEQ | Filtrar atividades por tipo de evento |
| activity.id | string | eq | Localizar uma atividade por ID |
| atividade. representada | booleano | eq | Se definido como "true", retorna apenas eventos representados, se definido como "false", retorna eventos não representados |
| atividade. tipo | booleano | eq | Se definido como "true", retorna somente eventos admin, se definido como "false", retorna eventos regulares |
| Activity. takeaction | string | EQ, NEQ | Filtrar atividades pelas ações executadas nelas. Os valores possíveis incluem:<br /><br />**bloco**: bloqueado<br />**proxy**: Redirecionado para controle de sessão<br />**BypassProxy**: ignorar controle de sessão<br />**criptografar**: criptografado<br />**descriptografar**: descriptografado<br />**verificado**: verificado<br />**encryptionFailed**: falha na criptografia<br />**proteger**: protegido<br />**verificar**: exigir autenticação step-up<br />**NULL**: nenhuma ação |
| dispositivo. tipo | string | EQ, NEQ | Filtrar atividades por tipo de dispositivo. Os valores possíveis incluem:<br /><br />**área de trabalho**: PC<br />**Móvel**: móvel<br />**Tablet**: Tablet<br />**Outro**: outros<br />**NULL**: nenhum valor |
| Device. Tags | string | EQ, NEQ | Filtrar atividades por IDs de marca de dispositivo |
| UserAgent. UserAgent | string | contém, ncontains | Filtrar atividades que fazem ou não contêm as cadeias de caracteres fornecidas no agente do usuário |
| UserAgent. Tags | string | EQ, NEQ | Filtrar atividades que contêm as IDs de marca do agente do usuário especificado |
| localização. país | string | EQ, NEQ, isset, isnotset | Filtrar atividades originadas do código de país/região especificado |
| local. organizações | string | EQ, NEQ, isset, isnotset, contém | Filtrar atividades originadas da organização especificada |
| IP. Address | string | EQ, StartsWith, doesnotstartwith, isset, isnotset, NEQ | Filtrar atividades provenientes do endereço IP fornecido |
| fileseletor | Arquivo  | EQ, NEQ | Filtrar atividades que contêm o arquivo/pasta especificado |
| office365url | string | StartsWith, EQ, EndsWith | Filtrar atividades por URLs do Office 365 |
| fileId | string | eq | Localizar um arquivo por ID |
| IP. categoria | Número inteiro | EQ, NEQ | Filtrar atividades com as categorias de sub-rede especificadas. Os valores possíveis incluem:<br /><br />**1**: corporativo<br />**2**: administrativo<br />**3**: arriscado<br />**4**: VPN<br />**5**: provedor de nuvem<br />**6**: outros |
| IP. Tags | string | EQ, NEQ | Filtrar atividades por IDs de marca IP |
| text | string | EQ, startswithsingle, texto | Filtrar atividades executando uma pesquisa de texto livre |
| Data | timestamp | LTE, GTE, Range, lte_ndays, gte_ndays | Filtrar atividades que ocorreram no intervalo de tempo especificado |
| policy | string | EQ, NEQ, isset, isnotset | Filtrar atividades relacionadas às políticas especificadas |
| source | string | EQ, NEQ | Filtrar todas as atividades por tipo de origem ou ID de fluxo. Exemplo: `[{ "s:stream-id", "t:source-type" }]` possíveis valores de tipo de fonte incluem:<br /><br />**0**: controle de acesso<br />**1**: controle de sessão<br />**2**: conector de aplicativos<br />**3**: análise do conector de aplicativos<br />**5**: descoberta<br />**6**: MDATP |
| atividade. Alertid | string | eq | Filtrar todas as atividades relevantes para uma ID de alerta |
| activityobject | string | EQ, NEQ | Filtrar atividades que contêm a ID especificada |
| rótulos de | string | EQ, NEQ | Filtrar arquivos que contêm as IDs de rótulos de arquivo (marcas) especificadas |
| criado || LTE, GTE, Range, gt, lt, EQ | Filtrar atividades que foram criadas no intervalo de tempo especificado |
| entidade | CP de entidade | EQ, NEQ, isset, isnotset, StartsWith | Filtrar atividades pela entidade que realizou a atividade. Exemplo: `[{ "id": "entity-id", "saas": 11161, "inst": 0 }]` |
| User. username | string | EQ, NEQ, isset, isnotset, StartsWith | Filtrar atividades pelo usuário que realizou a atividade |
| User. Tags | string | EQ, NEQ, isset, isnotset, StartsWith | Filtrar atividades por marcas que pertencem ao usuário em execução. Requer IDs de grupo |
| User. Domain | string | EQ, NEQ, isset, isnotset | Filtrar atividades por meio do domínio de usuário em execução |

[!INCLUDE [Open support ticket](includes/support.md)]

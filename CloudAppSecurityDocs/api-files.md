---
title: API de arquivos Cloud App Security
description: Este artigo fornece informações sobre como usar a API de arquivos.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: f8ad5aa24bb927f545133e0912ec4c6ccff50596
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90880871"
---
# <a name="files-api"></a>API de arquivos

[!INCLUDE [Banner for top of topics](includes/banner.md)]

> [!NOTE]
> Esta API não está disponível para o Office 365 Cloud App Security.

A API de arquivos fornece metadados sobre os arquivos e pastas armazenados em seus aplicativos de nuvem, como data da última modificação, propriedade e muito mais.

O seguinte lista as solicitações com suporte:

- [Listar arquivos](api-files-list.md)
- [Buscar arquivo](api-files-fetch.md)

## <a name="filters"></a>Filtros

Para obter informações sobre como os filtros funcionam, consulte [filtros](api-introduction.md#filters).

A tabela a seguir descreve os filtros com suporte:

| Filtrar | Tipo | Operadores | Descrição |
| --- | --- | --- | --- |
| serviço | Número inteiro | EQ, NEQ | Filtrar arquivos da appID do aplicativo especificado, por exemplo: 11770 |
| instance | Número inteiro | EQ, NEQ | Filtrar arquivos de instâncias especificadas |
| FileType | Número inteiro | EQ, NEQ | Filtrar arquivos com o tipo de arquivo especificado. Os valores possíveis incluem:<br /><br />**0**: outro<br />**1**: documento<br />**2**: planilha<br />**3**: apresentação<br />**4**: texto<br />**5**: imagem<br />**6**: pasta |
| allowDeleted | booleano | eq | Os valores possíveis incluem:<br /><br />**true**: retorna arquivos excluídos<br />**false** ou not set: retorna arquivos não excluídos (incluindo lixo). Isso será substituído pelo operador Trash |
| policy | string | cabinetmatchedrulesequals, NEQ, isset, isnotset | Filtrar atividades relacionadas às políticas especificadas |
| nome do arquivo | string | eq | Filtrar arquivos por nome de arquivo |
| modifiedDate | timestamp | LTE, GTE, Range, lte_ndays, gte_ndays | Filtrar arquivos pela data da última modificação |
| createdDate | timestamp | LTE, GTE, Range | Filtrar arquivos pela data em que foram criados |
| colaboradores. entidade | CP de entidade | EQ, NEQ | Filtrar arquivos compartilhados com entidades especificadas. Exemplo: `[{ "id": "entity-id", "saas": 11161, "inst": 0 }]` |
| colaboradores. domínios | string | EQ, NEQ | Filtrar arquivos compartilhados com domínios especificados |
| colaboradores. grupos | string | EQ, NEQ | Filtrar arquivos compartilhados com grupos especificados |
| colaboradores. withDomain | string | EQ, NEQ, DEQ | Filtrar arquivos compartilhados com domínios especificados |
| proprietário. entidade | CP de entidade | EQ, NEQ | Filtrar arquivos de propriedade de entidades especificadas. Exemplo: `[{ "id": "entity-id", "saas": 11161, "inst": 0 }]` |
| Owner. orgUnit | string | EQ, NEQ | Filtrar arquivos com proprietários de unidades organizacionais especificadas |
| compartilhando | Número inteiro | EQ, NEQ | Filtrar arquivos com os níveis de compartilhamento especificados. Os valores possíveis incluem:<br /><br />**4**: público (Internet)<br />**3**: público<br />**2**: externo<br />**1**: interno<br />**0**: privado |
| fileId | string | EQ, NEQ | Filtrar arquivos por ID de arquivo |
| rótulos de | string | EQ, NEQ, isset, isnotset | Filtrar arquivos que contêm as IDs de rótulos de arquivo (marcas) especificadas |
| fileScanLabels | string | EQ, NEQ, isset, isnotset | Filtrar arquivos que contêm as IDs de avisos (marcas) de inspeção de conteúdo especificado |
| extensão | string | EQ, NEQ | Filtrar arquivos por uma determinada extensão de arquivo |
| Tipo MIME | string | EQ, NEQ | Filtrar arquivos por um tipo MIME específico, deve ser uma única cadeia de caracteres |
| jogado no lixo | booleano | eq | Os valores possíveis incluem:<br /><br />**true**: retorna somente arquivos colatados<br />**false**: retorna arquivos não colatados |
| parentFolder | folder | EQ, NEQ | Filtrar arquivos contidos nas pastas especificadas |
| folder | booleano | eq | Os valores possíveis incluem:<br /><br />**true**: retorna somente pastas<br >**false**: retorna somente arquivos |
| em quarentena | booleano | eq | Os valores possíveis incluem:<br /><br />**true**: retorna somente arquivos em quarentena<br />**false**: retorna somente arquivos não em quarentena |
| snapshotLastModifiedDate | timestamp | LTE, GTE, Range | Filtrar arquivos pela data em que o instantâneo foi modificado pela última vez |

[!INCLUDE [Open support ticket](includes/support.md)]

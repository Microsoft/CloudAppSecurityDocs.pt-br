---
title: Finalizar upload de arquivo-API de Cloud Discovery
description: Este artigo descreve a solicitação de done_upload na API Cloud Discovery do Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: a30fd3f257089d8d3aeda125f63ae2c695d6344c
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90880608"
---
# <a name="finalize-file-upload---cloud-discovery-api"></a>Finalizar upload de arquivo-API de Cloud Discovery

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Depois que o carregamento do conteúdo do arquivo for concluído com êxito, notifique-nos para começar o processamento do arquivo.

## <a name="http-request"></a>Solicitação HTTP

```rest
POST /api/v1/discovery/done_upload/
```

## <a name="request-body-parameters"></a>Parâmetros do corpo da solicitação

| Parâmetro | Descrição |
| --- | --- |
| uploadUrl | A URL que foi retornada na chamada inicial solicitando o carregamento do arquivo. |
| inputStreamName | O nome da fonte de dados da qual os dados são recebidos (representa o dispositivo). |
| uploadAsSnapshot | Carregue os dados como um relatório de instantâneo em vez de carregá-los em um relatório contínuo. Se esse parâmetro for definido, o relatório será criado com o nome especificado em inputStreamName. |

## <a name="example"></a>Exemplo

### <a name="request"></a>Solicitação

Veja um exemplo da solicitação.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/discovery/done_upload/" -d "uploadUrl=<initiate_file_upload_response_url>"
```

[!INCLUDE [Open support ticket](includes/support.md)]

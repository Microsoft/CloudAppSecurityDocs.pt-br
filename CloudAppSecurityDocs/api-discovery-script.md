---
title: Gerar script de bloco-API de Cloud Discovery
description: Este artigo descreve a solicitação de discovery_block_scripts na API Cloud Discovery do Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 542f4a010aa5ca5051dedb5bc3ca8f97913c4a4e
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90879819"
---
# <a name="generate-block-script---cloud-discovery-api"></a>Gerar script de bloco-API de Cloud Discovery

[!INCLUDE [Banner for top of topics](includes/banner.md)]

> [!NOTE]
> Esta solicitação não está disponível para o Office 365 Cloud App Security.

Execute a solicitação GET para obter um script de bloco para seu dispositivo de rede.

## <a name="http-request"></a>Solicitação HTTP

```rest
GET /api/discovery_block_scripts/
```

## <a name="request-url-parameters"></a>Parâmetros da URL de solicitação

| Parâmetro | Descrição |
| --- | --- |
| format | O formato do dispositivo de rede. |

Atualmente, há suporte para os seguintes formatos:

| Dispositivo | Formatar |
| --- | --- |
| BlueCoat ProxySG | 102 |
| Cisco ASA | 104 |
| Fortinet FortiGate | 108 |
| Juniper SRX | 129 |
| Palo Alto | 112 |
| Websense | 135 |
| Zscaler | 120 |

> [!NOTE]
> Se você não conseguir localizar seu dispositivo, gere um script de bloco manualmente usando o Portal.

## <a name="response"></a>Resposta

Essa solicitação retorna o script de bloco como texto.

## <a name="example"></a>Exemplo

### <a name="request"></a>Solicitação

Veja um exemplo da solicitação.

```rest
curl -XGET -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/discovery_block_scripts/?format=102&type=banned"
```

### <a name="response"></a>Resposta

```text
url.domain=application.com deny
url.domain=application.be deny
url.domain=application.co deny
```

[!INCLUDE [Open support ticket](includes/support.md)]

---
title: Iniciar o upload de arquivo-API de Cloud Discovery
description: Este artigo descreve a solicitação de upload_url na API Cloud Discovery do Cloud App Security.
ms.date: 10/21/2020
ms.topic: reference
ms.openlocfilehash: bc46d4c1fcfd88c751e94eb06c0d858ff2b2c4ba
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96314436"
---
# <a name="initiate-file-upload---cloud-discovery-api"></a>Iniciar o upload de arquivo-API de Cloud Discovery

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Execute a solicitação GET para iniciar o processo de carregamento. Essa chamada, a primeira das três, retorna uma URL que será usada posteriormente para executar a solicitação de upload (PUT).

## <a name="http-request"></a>Solicitação HTTP

```rest
GET /api/v1/discovery/upload_url/
```

## <a name="request-url-parameters"></a>Parâmetros da URL de solicitação

| Parâmetro | Descrição |
| --- |--- |
| nome do arquivo | Nome do arquivo que você deseja carregar para Cloud Discovery processamento |
| source | O tipo de Cloud Discovery arquivo de log que está sendo carregado |

Atualmente, há suporte para os seguintes tipos de origem:

- BARRACUDA
- BLUECOAT
- CHECKPOINT
- CHECKPOINT_CEF_SYSLOG
- CHECKPOINT_SMART_VIEW_TRACKER
- CHECKPOINT_XML
- CISCO_ASA
- CISCO_ASA_FIREPOWER
- CISCO_FIREPOWER_V6_SYSLOG
- CISCO_FWSM
- CISCO_IRONPORT_PROXY
- CISCO_IRONPORT_WSA_II
- CISCO_SCAN_SAFE
- CLAVISTER
- CORRATA
- CUSTOM_PARSER
- FORCEPOINT
- FORCEPOINT_LEEF
- FORTIGATE
- GENERIC_CEF
- GENERIC_LEEF
- GENERIC_W3C
- I_FILTER
- IBOSS
- JUNIPER_SRX
- JUNIPER_SRX_SD
- JUNIPER_SRX_WELF
- JUNIPER_SSG
- MACHINE_ZONE_MERAKI
- MCAFEE_SWG
- MICROSOFT_ISA_W3C
- PALO_ALTO
- PALO_ALTO_LEEF
- SONICWALL_SYSLOG
- SOPHOS_CYBEROAM
- SOPHOS_SG
- SOPHOS_XG
- SQUID
- SQUID_NATIVE
- STORMSHIELD
- WEBSENSE_SIEM_CEF
- WEBSENSE_V7_5
- ZSCALER
- ZSCALER_CEF
- ZSCALER_QRADAR

> [!NOTE]
>
> - Ao usar um analisador personalizado, Cloud App Security usará o analisador personalizado anexado à fonte de dados selecionada.
> - Se você não encontrar o formato de arquivo, execute um upload manual usando o Portal.

## <a name="response-parameters"></a>Parâmetros de resposta

| Parâmetro | Descrição |
| --- | --- |
| url | A URL de destino que executará o carregamento de Cloud Discovery. |
| provider | "Azure" ou "AWS", uma indicação se o upload é de destino para o armazenamento do Windows Azure e o armazenamento AWS S3. |

## <a name="example"></a>Exemplo

### <a name="request"></a>Solicitação

Veja um exemplo da solicitação.

```rest
curl -XGET -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/discovery/upload_url/?filename=my_discovery_file.txt&source=LOG_3COM"
```

### <a name="response"></a>Resposta

Aqui está um exemplo da resposta JSON.

```json
{
  "url": "https://<initiate_file_upload_response_url>",
  "provider": "azure"
}
```

[!INCLUDE [Open support ticket](includes/support.md)]

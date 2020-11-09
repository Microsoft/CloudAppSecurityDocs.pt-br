---
title: Implantar Cloud Discovery-Cloud App Security
description: Este artigo descreve o procedimento de configuração para colocar o Cloud Discovery em funcionamento.
author: shsagir
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: how-to
ms.date: 08/09/2020
ms.collection: M365-security-compliance
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 8a5d2d5ee97677482be80a44b33f832cfaee6ddf
ms.sourcegitcommit: 288f3011c0ce0e5f2d8cbaa9057a63be044465f7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2020
ms.locfileid: "94375084"
---
# <a name="set-up-cloud-discovery"></a>Configurar o Cloud Discovery

[!INCLUDE [Banner for top of topics](includes/banner.md)]

O Cloud Discovery analisa seus logs de tráfego com base no catálogo de mais de 16.000 aplicativos de nuvem do Microsoft Cloud App Security. Os aplicativos são classificados e pontuados com base em mais de 80 fatores de risco para fornecer visibilidade contínua sobre o uso da nuvem, sombra de ti e a sombra de risco que ela representa em sua organização.

## <a name="snapshot-and-continuous-risk-assessment-reports"></a>Relatórios contínuo e de instantâneo de avaliação de riscos

Você pode gerar os seguintes tipos de relatórios:

- **Relatórios de instantâneo** – fornecem visibilidade ad hoc em um conjunto de logs de tráfego cujo upload é feito manualmente dos seus firewalls e proxies.

- **Relatórios contínuos** – analisam todos os logs que são encaminhados da sua rede usando o Cloud App Security. Eles oferecem maior visibilidade em todos os dados e identificam automaticamente usos anormais com o mecanismo de detecção de anomalias do Machine Learning ou por meio de políticas personalizadas que você definir. Esses relatórios podem ser criados conectando-se das seguintes maneiras:

  - [**Integração do Microsoft defender para Endpoint: o**](mde-integration.md)Cloud app Security integra-se com o defender for Endpoint nativamente, para simplificar a distribuição de Cloud Discovery, estender os recursos de Cloud Discovery além da rede corporativa e habilitar a investigação baseada em computador.
  - [**Coletor de logs**](discovery-docker.md): os coletores de logs permitem automatizar facilmente o upload de log de sua rede. O coletor de log é executado em sua rede e recebe logs por Syslog ou FTP.
  - **SWG (Secure Web Gateway)** : se você trabalha com Cloud app Security e um dos seguintes SWGs, você pode integrar os produtos para aprimorar sua experiência de Cloud Discovery de segurança. Juntos, Cloud App Security e SWGs fornecem uma implantação direta de Cloud Discovery, bloqueio automático de aplicativos não aprovados e avaliação de riscos diretamente no portal do SWG.
    - [Integração do Zscaler](zscaler-integration.md)
    - [integração do iboss](iboss-integration.md)
    - [Integração do Corrata](corrata-integration.md)
    - [Integração de segurança do Menlo](menlo-integration.md)

- **[API de Cloud Discovery](api-discovery.md)** – use a api de Cloud Discovery do Cloud app Security para automatizar o upload do log de tráfego e obter relatórios automatizados de descoberta de nuvem e avaliação de risco. Você também pode usar a API para [gerar scripts de bloco](api-discovery-script.md) e simplificar os controles de aplicativo diretamente para seu dispositivo de rede.

## <a name="log-process-flow-from-raw-data-to-risk-assessment"></a>Fluxo do processo de log: dos dados brutos a avaliação de riscos

O processo de geração de uma avaliação de riscos consiste nas seguintes etapas. O processo leva de alguns minutos a várias horas, dependendo da quantidade de dados processados.

- **Carregar** – os logs do tráfego da Web da sua rede são carregados no portal.

- **Analisar** – O Cloud App Security analisa e extrai dados de tráfego dos logs de tráfego com um analisador dedicado para cada fonte de dados.

- **Analisar** – os dados de tráfego são examinados em relação ao Catálogo do Cloud App para identificar mais de 16 mil aplicativos de nuvem e avaliar sua pontuação de risco. Usuários ativos e endereços IP também são identificados como parte da análise.

- **Gerar relatório** – Um relatório de avaliação de risco dos dados extraídos dos arquivos de log é gerado.

>[!NOTE]
> Os dados de relatório contínuos são analisados quatro vezes por dia.

## <a name="supported-firewalls-and-proxies"></a>Firewalls e proxies com suporte <a name="supported-firewalls-and-proxies"></a>

- Barracuda – firewall do aplicativo Web (W3C)
- Blue Coat Proxy SG – log de acesso (W3C)
- Ponto de Verificação
- Cisco ASA com FirePOWER
- Firewall Cisco ASA (Para firewalls Cisco ASA, é necessário definir o nível de informações como 6)
- Cisco Cloud Web Security
- Cisco FWSM
- Cisco IronPort WSA
- Cisco Meraki – log de URLs
- Clavister NGFW (Syslog)
- ContentKeeper
- Corrata
- Digital Arts i-FILTER
- Forcepoint
- Fortinet Fortigate
- iboss Secure Cloud Gateway
- Juniper SRX
- Juniper SSG
- McAfee Secure Web Gateway
- Segurança de Menlo (CEF)
- Microsoft Forefront Threat Management Gateway (W3C)
- Firewall da série Palo Alto
- Sonicwall (anteriormente conhecido como Dell)
- Sophos SG
- Sophos XG
- Sophos Cyberoam
- Squid (comum)
- Squid (nativo)
- Stormshield
- Websense – soluções de segurança da Web – relatório de detalhes de investigação (CSV)
- Websense – soluções de segurança da Web – log de atividades de Internet (CEF)
- Zscaler

> [!NOTE]
> O Cloud Discovery oferece suporte a endereços IPv4 e IPv6.

Se o log não tiver suporte ou se você estiver usando um formato de log recentemente liberado de uma das fontes de dados com suporte e o carregamento estiver falhando, selecione **outro** como a **fonte de dados** e especifique o dispositivo e o log que você está tentando carregar. O log será examinado pela equipe de analista de nuvem do Cloud App Security e você será notificado se for adicionado suporte para seu tipo de log. Como alternativa, você pode definir um analisador personalizado que corresponda ao seu formato. Para obter mais informações, consulte [Usar um analisador de log personalizado](custom-log-parser.md).

> [!NOTE]
> A lista de dispositivos com suporte a seguir pode não funcionar com os formatos de log liberados recentemente. Se você estiver usando um formato recentemente liberado e o carregamento estiver falhando, [use um analisador de log personalizado](custom-log-parser.md) e, se necessário, abra um caso de suporte.

Atributos de dados (de acordo com a documentação do fornecedor):

| Fonte de dados | URL do aplicativo de destino | IP do aplicativo de destino | Nome de Usuário | IP de Origem | Tráfego total | Bytes carregados |
|----------------------------------------------|----------------------|----------------------|----------------------|----------------------|----------------------|----------------------|
| Barracuda | **Sim** | **Sim** | **Sim** | **Sim** | Não | Não |
| Blue Coat | **Sim** | Não | **Sim** | **Sim** | **Sim** | **Sim** |
| Ponto de Verificação | Não | **Sim** | Não | **Sim** | Não | Não |
| Cisco ASA (Syslog) | Não | **Sim** | Não | **Sim** | **Sim** | Não |
| Cisco ASA com FirePOWER | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** |
| Cisco Cloud Web Security |**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|
| Cisco FWSM | Não | **Sim** | Não | **Sim** | **Sim** | Não |
| Cisco Ironport WSA | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** |
| Cisco Meraki | **Sim** | **Sim** | Não | **Sim** | Não | Não |
| Clavister NGFW (Syslog) | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** |
| ContentKeeper | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** |
| Corrata | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** |
| SonicWall (anteriormente conhecido como Dell) | **Sim** | **Sim** | Não | **Sim** | **Sim** | **Sim** |
| Digital Arts i-FILTER | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** |
| ForcePoint LEEF |**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|
| Nuvem do ForcePoint Web Security\* |**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|
| FortiGate | Não | **Sim** | Não | **Sim** | **Sim** | **Sim** |
| Fortinet FortiOS |**Sim**|**Sim**|Não|**Sim**|**Sim**|**Sim**|
| iboss |**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|
| Juniper SRX | Não | **Sim** | Não | **Sim** | **Sim** | **Sim** |
| Juniper SSG | Não | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** |
| McAfee SWG | **Sim** | Não | Não | **Sim** | **Sim** | **Sim** |
| Segurança de Menlo (CEF) | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** |
| MS TMG | **Sim** | Não | **Sim** | **Sim** | **Sim** | **Sim** |
| Redes Palo Alto | Não | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** |
| Sophos | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** | Não |
| Squid (comum) | **Sim** | Não | **Sim** | **Sim** | **Sim** | Não |
| Squid (nativo) | **Sim** | Não | **Sim** | **Sim** | Não | Não |
| Stormshield | Não | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** |
| Websense – Relatório de detalhes investigativo (CSV) | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** |
| Websense – log de atividades de Internet (CEF) | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** |
| Zscaler | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** |

\* Não há suporte para as versões 8,5 e posteriores do Forcepoint Web Security Cloud

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Criar instantâneo de relatórios do Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

> [!div class="nextstepaction"]
> [Configurar upload de log automático para relatórios contínuos](discovery-docker.md)

> [!div class="nextstepaction"]
> [Trabalhando com dados do Cloud Discovery](working-with-cloud-discovery-data.md)

---
title: Implantar o Cloud Discovery – Cloud App Security | Microsoft Docs
description: Este artigo descreve o procedimento de configuração para colocar o Cloud Discovery em funcionamento.
author: shsagir
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: conceptual
ms.date: 05/17/2020
ms.collection: M365-security-compliance
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 7e7635cf2fd7400376ec5a57919d2804ab8ab6b1
ms.sourcegitcommit: 211dcc2850a7b1513f93ccc83e8e152bc941f253
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/10/2020
ms.locfileid: "84654412"
---
# <a name="set-up-cloud-discovery"></a>Configurar o Cloud Discovery

*Aplica-se a: Microsoft Cloud App Security*

O Cloud Discovery analisa seus logs de tráfego com base no catálogo de mais de 16.000 aplicativos de nuvem do Microsoft Cloud App Security. Os aplicativos são classificados e pontuados com base em mais de 80 fatores de risco para fornecer visibilidade contínua sobre o uso da nuvem, sombra de ti e a sombra de risco que ela representa em sua organização.

## <a name="snapshot-and-continuous-risk-assessment-reports"></a>Relatórios contínuo e de instantâneo de avaliação de riscos

Há dois tipos de relatórios que você pode gerar:

- **Relatórios de instantâneo** – fornecem visibilidade ad hoc em um conjunto de logs de tráfego cujo upload é feito manualmente dos seus firewalls e proxies.

- **Relatórios contínuos** – analisam todos os logs que são encaminhados da sua rede usando o Cloud App Security. Eles oferecem maior visibilidade em todos os dados e identificam automaticamente usos anormais com o mecanismo de detecção de anomalias do Machine Learning ou por meio de políticas personalizadas que você definir. Esses relatórios podem ser criados conectando-se das seguintes maneiras:

  - [Integração do Microsoft defender ATP: o](wdatp-integration.md)Cloud app Security integra-se com o Microsoft defender com segurança (ATP) nativamente, para simplificar a distribuição de Cloud Discovery, estender os recursos de Cloud Discovery além da rede corporativa e habilitar a investigação baseada em computador.
  - [Coletor de logs](discovery-docker.md): os coletores de logs permitem automatizar facilmente o carregamento de logs da rede. O coletor de log é executado em sua rede e recebe logs por Syslog ou FTP.
  - [Integração do Zscaler](zscaler-integration.md): se trabalha com o Cloud App Security e o Zscaler, você pode integrar os dois produtos para melhorar a experiência de segurança do Cloud Discovery. Juntos, o Cloud App Security e o Zscaler proporcionam uma implantação perfeita do Cloud Discovery, o bloqueio automático de aplicativos não sancionados e a avaliação de riscos diretamente no portal do Zscaler.
  - [integração do iboss](iboss-integration.md): se você trabalha com o Cloud app Security e o iboss, você pode integrar os dois produtos para aprimorar sua experiência de Cloud Discovery de segurança. Juntos, Cloud App Security e iboss fornecem uma implantação direta de Cloud Discovery, bloqueio automático de aplicativos não aprovados e avaliação de riscos diretamente no portal do iboss.
  - [Integração do Corrata](corrata-integration.md): se você trabalha com o Cloud app Security e o Corrata, você pode integrar os dois produtos para aprimorar sua experiência de Cloud Discovery de segurança. Juntos, Cloud App Security e Corrata fornecem uma implantação direta de Cloud Discovery, bloqueio automático de aplicativos não aprovados e avaliação de riscos diretamente no portal do Corrata.

## <a name="log-process-flow-from-raw-data-to-risk-assessment"></a>Fluxo do processo de log: dos dados brutos a avaliação de riscos

O processo de geração de uma avaliação de riscos consiste nas seguintes etapas. O processo leva de alguns minutos a várias horas, dependendo da quantidade de dados processados.

- **Carregar** – os logs do tráfego da Web da sua rede são carregados no portal.

- **Analisar** – O Cloud App Security analisa e extrai dados de tráfego dos logs de tráfego com um analisador dedicado para cada fonte de dados.

- **Analisar** – os dados de tráfego são examinados em relação ao Catálogo do Cloud App para identificar mais de 16 mil aplicativos de nuvem e avaliar sua pontuação de risco. Usuários ativos e endereços IP também são identificados como parte da análise.

- **Gerar relatório** – Um relatório de avaliação de risco dos dados extraídos dos arquivos de log é gerado.

>[!NOTE]
> Dados de relatório contínuos são analisados duas vezes por dia.

## <a name="supported-firewalls-and-proxies"></a>Firewalls e proxies com suporte<a name="supported-firewalls-and-proxies"></a>

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

Se não houver suporte para seu log, selecione **Outro** como a **Fonte de dados** e especifique o dispositivo e o log que você está tentando carregar. O log será examinado pela equipe de analista de nuvem do Cloud App Security e você será notificado se for adicionado suporte para seu tipo de log. Como alternativa, você pode definir um analisador personalizado que corresponda ao seu formato. Para obter mais informações, consulte [Usar um analisador de log personalizado](custom-log-parser.md).

Atributos de dados (de acordo com a documentação do fornecedor):

| Fonte de dados | URL do aplicativo de destino | IP do aplicativo de destino | Nome de Usuário | IP de Origem | Tráfego total | Bytes carregados |
|----------------------------------------------|----------------------|----------------------|----------------------|----------------------|----------------------|----------------------|
| Barracuda | **Sim** | **Sim** | **Sim** | **Sim** | Não | No |
| Blue Coat | **Sim** | Não | **Sim** | **Sim** | **Sim** | **Sim** |
| Ponto de Verificação | Não | **Sim** | Não | **Sim** | Não | No |
| Cisco ASA (Syslog) | Não | **Sim** | Não | **Sim** | **Sim** | Não |
| Cisco ASA com FirePOWER | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** |
| Cisco Cloud Web Security |**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|
| Cisco FWSM | Não | **Sim** | Não | **Sim** | **Sim** | Não |
| Cisco Ironport WSA | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** |
| Cisco Meraki | **Sim** | **Sim** | Não | **Sim** | Não | No |
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
| MS TMG | **Sim** | Não | **Sim** | **Sim** | **Sim** | **Sim** |
| Redes Palo Alto | Não | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** |
| Sophos | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** | Não |
| Squid (comum) | **Sim** | Não | **Sim** | **Sim** | Não | **Sim** |
| Squid (nativo) | **Sim** | Não | **Sim** | **Sim** | Não | **Sim** |
| Stormshield | Não | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** |
| Websense – Relatório de detalhes investigativo (CSV) | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** |
| Websense – log de atividades de Internet (CEF) | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** |
| Zscaler | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** |

\*Não há suporte para as versões 8,5 e posteriores do Forcepoint Web Security Cloud

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Criar instantâneo de relatórios do Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

> [!div class="nextstepaction"]
> [Configurar upload de log automático para relatórios contínuos](discovery-docker.md)

> [!div class="nextstepaction"]
> [Trabalhando com dados do Cloud Discovery](working-with-cloud-discovery-data.md)

---
title: Implantar o Cloud Discovery – Cloud App Security | Microsoft Docs
description: Este artigo descreve o procedimento de configuração para colocar o Cloud Discovery em funcionamento.
author: ShlomoSagir-MS
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: conceptual
ms.date: 8/15/2019
ms.collection: M365-security-compliance
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 296abe6a227d6ab6c72e09cc993d8cf413770cec
ms.sourcegitcommit: 7eecf2f863c410abe0ba6eafd65777973de011cb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/18/2019
ms.locfileid: "69573047"
---
# <a name="set-up-cloud-discovery"></a>Configurar o Cloud Discovery

*Aplica-se a: Microsoft Cloud App Security*

O Cloud Discovery analisa seus logs de tráfego com base no catálogo de mais de 16.000 aplicativos de nuvem do Microsoft Cloud App Security. Os aplicativos são classificados e pontuados com base em mais de 80 fatores de risco para fornecer visibilidade contínua sobre o uso da nuvem, sombra de ti e a sombra de risco que ela representa em sua organização.

## <a name="snapshot-and-continuous-risk-assessment-reports"></a>Relatórios contínuo e de instantâneo de avaliação de riscos

Há dois tipos de relatórios que você pode gerar:

- **Relatórios de instantâneo** – fornecem visibilidade ad hoc em um conjunto de logs de tráfego cujo upload é feito manualmente dos seus firewalls e proxies.

- **Relatórios contínuos** – analisam todos os logs que são encaminhados da sua rede usando o Cloud App Security. Eles oferecem maior visibilidade em todos os dados e identificam automaticamente usos anormais com o mecanismo de detecção de anomalias do Machine Learning ou por meio de políticas personalizadas que você definir. Esses relatórios podem ser criados conectando-se das seguintes maneiras:

     - [Integração do Microsoft defender ATP](wdatp-integration.md): O Cloud App Security integra-se com a ATP (proteção avançada contra ameaças) do Microsoft defender nativamente, para simplificar a distribuição de Cloud Discovery, estender os recursos de Cloud Discovery além da rede corporativa e habilitar a investigação baseada em computador.
     - [Coletor de logs](discovery-docker.md): Os coletores de log permitem que você automatize facilmente o upload de logs da sua rede. O coletor de log é executado em sua rede e recebe logs por Syslog ou FTP.
     - [Integração do Zscaler](zscaler-integration.md): Se você trabalha com o Cloud App Security e o Zscaler, pode integrar os dois produtos para melhorar a experiência de segurança do Cloud Discovery. Juntos, o Cloud App Security e o Zscaler proporcionam uma implantação perfeita do Cloud Discovery, o bloqueio automático de aplicativos não sancionados e a avaliação de riscos diretamente no portal do Zscaler.
     - [integração do iboss](iboss-integration.md): Se você trabalha com o Cloud App Security e o iboss, é possível integrar os dois produtos para melhorar a experiência de segurança do Cloud Discovery. Juntos, Cloud App Security e iboss fornecem uma implantação direta de Cloud Discovery, bloqueio automático de aplicativos não aprovados e avaliação de riscos diretamente no portal do iboss.

## <a name="log-process-flow-from-raw-data-to-risk-assessment"></a>Fluxo do processo de log: Dos dados brutos à avaliação de risco

O processo de geração de uma avaliação de riscos consiste nas seguintes etapas. O processo leva de alguns minutos a várias horas, dependendo da quantidade de dados processados.

- **Carregar** – os logs do tráfego da Web da sua rede são carregados no portal.

- **Analisar** – O Cloud App Security analisa e extrai dados de tráfego dos logs de tráfego com um analisador dedicado para cada fonte de dados.

- **Analisar** – os dados de tráfego são examinados em relação ao Catálogo do Cloud App para identificar mais de 16 mil aplicativos de nuvem e avaliar sua pontuação de risco. Os usuários ativos e os endereços IP também são identificados como parte da análise.

- **Gerar relatório** – Um relatório de avaliação de risco dos dados extraídos dos arquivos de log é gerado.

>[!NOTE]
> Os dados de relatórios contínuos são analisados duas vezes por dia.

## Proxies e firewalls com suporte <a name="supported-firewalls-and-proxies"></a>

- Barracuda - Firewall de aplicativo Web (W3C)
- Blue Coat Proxy SG – Log de acesso (W3C)
- Check Point
- Cisco ASA com FirePOWER
- Firewall Cisco ASA (Para firewalls Cisco ASA, é necessário definir o nível de informações como 6)
- Cisco Cloud Web Security
- Cisco FWSM
- Cisco IronPort WSA
- Cisco Meraki – log de URLs
- Clavister NGFW (Syslog)
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
- Squid (Comum)
- Squid (Nativo)
- Stormshield
- Websense – Soluções de segurança da Web – Relatório detalhado de investigação (CSV)
- Websense – Soluções de segurança da Web – Log de atividades de Internet (CEF)
- Zscaler

> [!NOTE]
> O Cloud Discovery oferece suporte a endereços IPv4 e IPv6.

Se não houver suporte para seu log, selecione **Outro** como a **Fonte de dados** e especifique o dispositivo e o log que você está tentando carregar. O log será examinado pela equipe de analista de nuvem do Cloud App Security e você será notificado se for adicionado suporte para seu tipo de log. Como alternativa, você pode definir um analisador personalizado que corresponda ao seu formato. Para saber mais, confira [Usar analisador de log personalizado](custom-log-parser.md).

Atributos de dados (de acordo com a documentação do fornecedor):

| Fonte de dados | URL do aplicativo de destino | IP do aplicativo de destino | Nome de usuário | IP de Origem | Tráfego total | Bytes carregados |
|----------------------------------------------|----------------------|----------------------|----------------------|----------------------|----------------------|----------------------|
| Barracuda | **Sim** | **Sim** | **Sim** | **Sim** | Não | Não |
| Blue Coat | **Sim** | Não | **Sim** | **Sim** | **Sim** | **Sim** |
| Checkpoint | Não | **Sim** | Não | **Sim** | Não | Não |
| Cisco ASA (Syslog) | Não | **Sim** | Não | **Sim** | **Sim** | Não |
| Cisco ASA com FirePOWER | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** |
| Cisco Cloud Web Security |**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|
| Cisco FWSM | Não | **Sim** | Não | **Sim** | **Sim** | Não |
| Cisco Ironport WSA | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** |
| Cisco Meraki | **Sim** | **Sim** | Não | **Sim** | Não | Não |
| Clavister NGFW (Syslog) | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** |
| SonicWall (anteriormente conhecido como Dell) | **Sim** | **Sim** | Não | **Sim** | **Sim** | **Sim** |
| Digital Arts i-FILTER | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** |
| ForcePoint LEEF |**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|
| Nuvem do ForcePoint Web Security |**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|
| Fortigate | Não | **Sim** | Não | **Sim** | **Sim** | **Sim** |
| Fortinet FortiOS |**Sim**|**Sim**|Não|**Sim**|**Sim**|**Sim**|
| iboss |**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|
| Juniper SRX | Não | **Sim** | Não | **Sim** | **Sim** | **Sim** |
| Juniper SSG | Não | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** |
| McAfee SWG | **Sim** | Não | Não | **Sim** | **Sim** | **Sim** |
| MS TMG | **Sim** | Não | **Sim** | **Sim** | **Sim** | **Sim** |
| Redes de Palo Alto | Não | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** |
| Sophos | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** | Não |
| Squid (Comum) | **Sim** | Não | **Sim** | **Sim** | Não | **Sim** |
| Squid (Nativo) | **Sim** | Não | **Sim** | **Sim** | Não | **Sim** |
| Stormshield | Não | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** |
| Websense – Relatório de detalhes investigativo (CSV) | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** |
| Websense – Log de atividades da Internet (CEF) | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** |
| Zscaler | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** |

## <a name="next-steps"></a>Próximas etapas

[Criar instantâneo de relatórios do Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

[Configurar upload de log automático para relatórios contínuos](configure-automatic-log-upload-for-continuous-reports.md)

[Trabalhando com os dados do Cloud Discovery](working-with-cloud-discovery-data.md)

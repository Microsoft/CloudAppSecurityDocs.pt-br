---
title: Implantar Cloud Discovery-Cloud App Security | Microsoft Docs
description: Este artigo descreve o procedimento de instalação para obter Cloud Discovery funcionando.
author: shsagir
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: conceptual
ms.date: 8/15/2019
ms.collection: M365-security-compliance
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: fe21bbb39b52981d7aeba0839367d2fd54073983
ms.sourcegitcommit: 4f3883a9e85d0aaf2802b10433b221c3f1838d88
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79285680"
---
# <a name="set-up-cloud-discovery"></a>Configurar o Cloud Discovery

*Aplica-se a: Microsoft Cloud App Security*

Cloud Discovery analisa os logs de tráfego no catálogo de aplicativos de nuvem de Microsoft Cloud App Security de mais de 16.000 aplicativos de nuvem. Os aplicativos são classificados e pontuados com base em mais de 80 fatores de risco para fornecer visibilidade contínua sobre o uso da nuvem, sombra de ti e a sombra de risco que ela representa em sua organização.

## <a name="snapshot-and-continuous-risk-assessment-reports"></a>Relatórios de instantâneo e avaliação de risco contínuo

Há dois tipos de relatórios que você pode gerar:

- **Relatórios de instantâneo** – fornece visibilidade ad hoc em um conjunto de logs de tráfego que você carrega manualmente de seus firewalls e proxies.

- **Relatórios contínuos** – Analise todos os logs que são encaminhados da sua rede usando Cloud app Security. Eles fornecem visibilidade aprimorada de todos os dados e identificam automaticamente o uso anormal usando o mecanismo de detecção de anomalias Machine Learning ou usando políticas personalizadas que você definir. Esses relatórios podem ser criados conectando-se das seguintes maneiras:

  - [Integração do Microsoft defender ATP: o](wdatp-integration.md)Cloud app Security integra-se com o Microsoft defender com segurança (ATP) nativamente, para simplificar a distribuição de Cloud Discovery, estender os recursos de Cloud Discovery além da rede corporativa e habilitar a investigação baseada em computador.
  - [Coletor de logs](discovery-docker.md): os coletores de logs permitem automatizar facilmente o upload de log de sua rede. O coletor de log é executado em sua rede e recebe logs por Syslog ou FTP.
  - [Integração do Zscaler](zscaler-integration.md): se você trabalha com o Cloud app Security e o Zscaler, você pode integrar os dois produtos para aprimorar sua experiência de Cloud Discovery de segurança. Juntos, Cloud App Security e Zscaler fornecem uma implantação direta de Cloud Discovery, bloqueio automático de aplicativos não aprovados e avaliação de riscos diretamente no portal do Zscaler.
  - [integração do iboss](iboss-integration.md): se você trabalha com o Cloud app Security e o iboss, você pode integrar os dois produtos para aprimorar sua experiência de Cloud Discovery de segurança. Juntos, Cloud App Security e iboss fornecem uma implantação direta de Cloud Discovery, bloqueio automático de aplicativos não aprovados e avaliação de riscos diretamente no portal do iboss.

## <a name="log-process-flow-from-raw-data-to-risk-assessment"></a>Fluxo do processo de log: de dados brutos a avaliação de risco

O processo de geração de uma avaliação de risco consiste nas etapas a seguir. O processo leva entre alguns minutos e várias horas, dependendo da quantidade de dados processados.

- **Carregar** – os logs de tráfego da Web da sua rede são carregados no Portal.

- **Parse** – Cloud app Security analisa e extrai dados de tráfego dos logs de tráfego com um analisador dedicado para cada fonte de dados.

- **Analisar** – os dados de tráfego são analisados no catálogo de aplicativos de nuvem para identificar mais de 16.000 aplicativos de nuvem e avaliar a pontuação de risco. Os usuários ativos e os endereços IP também são identificados como parte da análise.

- **Gerar relatório** -um relatório de avaliação de risco dos dados extraídos dos arquivos de log é gerado.

>[!NOTE]
> Os dados de relatório contínuos são analisados duas vezes por dia.

## Firewalls e proxies com suporte<a name="supported-firewalls-and-proxies"></a>

- Barracuda-firewall de aplicativo Web (W3C)
- Proxy de revestimento azul de SG – log de acesso (W3C)
- Check Point
- Cisco ASA com potência
- Cisco ASA firewall (para firewalls Cisco ASA, é necessário definir o nível de informações como 6)
- Cisco Cloud Web Security
- Cisco FWSM
- WSA do Cisco IronPort
- Cisco Meraki – log de URLs
- Clavister NGFW (syslog)
- ContentKeeper
- I-FILTER de artes digitais
- Forcepoint
- Fortinet FortiGate
- iboss proteger gateway de nuvem
- Juniper SRX
- Juniper SSG
- Gateway Web seguro da McAfee
- Microsoft Forefront Threat Management Gateway (W3C)
- Firewall da série Palo Alto
- SonicWALL (anteriormente Dell)
- SG do Sophos
- Sophos XG
- Sophos Cyberoam
- Squid (comum)
- Squid (nativo)
- Stormshield
- Websense – soluções de segurança na Web – relatório de detalhes de investigação (CSV)
- Websense – soluções de segurança na Web-log de atividades da Internet (CEF)
- Zscaler

> [!NOTE]
> O Cloud Discovery dá suporte a endereços IPv4 e IPv6.

Se o log não tiver suporte, selecione **outro** como a **fonte de dados** e especifique o dispositivo e o log que você está tentando carregar. Seu log será revisado pelo Cloud App Security equipe de analistas de nuvem e você será notificado se o suporte para o tipo de log for adicionado. Como alternativa, você pode definir um analisador personalizado que corresponda ao seu formato. Para obter mais informações, consulte [usar um analisador de log personalizado](custom-log-parser.md).

Atributos de dados (de acordo com a documentação do fornecedor):

| Fonte de dados | URL do aplicativo de destino | IP do aplicativo de destino | Nome de usuário | IP de origem | Tráfego total | Bytes carregados |
|----------------------------------------------|----------------------|----------------------|----------------------|----------------------|----------------------|----------------------|
| Barracuda | **Sim** | **Sim** | **Sim** | **Sim** | Não | Não |
| Revestimento azul | **Sim** | Não | **Sim** | **Sim** | **Sim** | **Sim** |
| Ponto de verificação | Não | **Sim** | Não | **Sim** | Não | Não |
| Cisco ASA (syslog) | Não | **Sim** | Não | **Sim** | **Sim** | Não |
| Cisco ASA com potência | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** |
| Cisco Cloud Web Security |**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|
| Cisco FWSM | Não | **Sim** | Não | **Sim** | **Sim** | Não |
| WSA do Cisco IronPort | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** |
| Cisco Meraki | **Sim** | **Sim** | Não | **Sim** | Não | Não |
| Clavister NGFW (syslog) | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** |
| ContentKeeper | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** |
| SonicWall (anteriormente Dell) | **Sim** | **Sim** | Não | **Sim** | **Sim** | **Sim** |
| I-FILTER de artes digitais | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** |
| ForcePoint LEEF |**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|
| Nuvem do ForcePoint Web Security |**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|
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
| Websense-relatório detalhado de investigação (CSV) | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** |
| Websense – log de atividades da Internet (CEF) | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** |
| Zscaler | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** | **Sim** |

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Criar instantâneo de relatórios do Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

> [!div class="nextstepaction"]
> [Configurar upload de log automático para relatórios contínuos](configure-automatic-log-upload-for-continuous-reports.md)

> [!div class="nextstepaction"]
> [Trabalhando com os dados do Cloud Discovery](working-with-cloud-discovery-data.md)

---
title: Implantar o Cloud Discovery – Cloud App Security | Microsoft Docs
description: Este artigo descreve o procedimento de configuração para colocar o Cloud Discovery em funcionamento.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: rkarlin
ms.date: 3/18/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: a9b5bd8d-305b-4e93-9a4c-a4683ea09080
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: a8e7c476690b1831b78a59c7c63b061aef0dc78e
ms.sourcegitcommit: 9f0c562322394a3dfac7f1d84286e673276a28b1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65568509"
---
# <a name="set-up-cloud-discovery"></a>Configurar o Cloud Discovery

*Aplica-se a: Microsoft Cloud App Security*

O Cloud Discovery analisa seus logs de tráfego com base no catálogo de mais de 16.000 aplicativos de nuvem do Microsoft Cloud App Security. Os aplicativos são classificados e pontuados com base mais de 70 fatores de risco para fornecer visibilidade contínua do uso de nuvem, TI Sombra e o risco que a TI Sombra representa para sua organização.

## <a name="snapshot-and-continuous-risk-assessment-reports"></a>Relatórios contínuo e de instantâneo de avaliação de riscos 

Há dois tipos de relatórios que você pode gerar: 

- **Relatórios de instantâneo** – fornecem visibilidade ad hoc em um conjunto de logs de tráfego cujo upload é feito manualmente dos seus firewalls e proxies.

- **Relatórios contínuos** – analisam todos os logs que são encaminhados da sua rede usando o Cloud App Security. Eles oferecem maior visibilidade em todos os dados e identificam automaticamente usos anormais com o mecanismo de detecção de anomalias do Machine Learning ou por meio de políticas personalizadas que você definir. Esses relatórios podem ser criados conectando-se das seguintes maneiras:

  - [Integração do Microsoft Defender ATP](wdatp-integration.md): Cloud App Security integra-se com o Microsoft Advanced Threat ATP (proteção Defender) nativamente, para simplificar a distribuição do Cloud Discovery, estender os recursos de Cloud Discovery além da sua rede corporativa e habilitar a máquina com base em investigação.
  - [Coletor de logs](discovery-docker.md): Os coletores de log permitem que você automatize facilmente o upload de logs da sua rede. O coletor de log é executado em sua rede e recebe logs por Syslog ou FTP.
  - [Integração do Zscaler](zscaler-integration.md): Se você trabalha com o Cloud App Security e o Zscaler, pode integrar os dois produtos para melhorar a experiência de segurança do Cloud Discovery. Juntos, o Cloud App Security e o Zscaler proporcionam uma implantação perfeita do Cloud Discovery, o bloqueio automático de aplicativos não sancionados e a avaliação de riscos diretamente no portal do Zscaler.
 - [integração de iboss](iboss-integration.md): Se você trabalha com o Cloud App Security e o iboss, é possível integrar os dois produtos para melhorar a experiência de segurança do Cloud Discovery. Juntos, o Cloud App Security e iboss fornecem uma implantação perfeita do Cloud Discovery, bloqueio de aplicativos não sancionados e avaliação de riscos diretamente no portal do iboss automático.

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
- Firewall Cisco ASA (Para firewalls Cisco ASA, é necessário definir o nível de informações como 6)
- Cisco ASA com FirePOWER
- Cisco IronPort WSA
- Cisco ScanSafe
- Cisco Meraki – log de URLs
- Clavister NGFW (Syslog)
- Digital Arts i-FILTER
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
- Websense – Soluções de segurança da Web – Relatório detalhado de investigação (CSV)
- Websense – Soluções de segurança da Web – Log de atividades de Internet (CEF)
- Zscaler

> [!NOTE]
> O Cloud Discovery oferece suporte a endereços IPv4 e IPv6.

Se não houver suporte para seu log, selecione **Outro** como a **Fonte de dados** e especifique o dispositivo e o log que você está tentando carregar. O log será examinado pela equipe de analista de nuvem do Cloud App Security e você será notificado se for adicionado suporte para seu tipo de log. Como alternativa, você pode definir um analisador personalizado que corresponda ao seu formato. Para saber mais, confira [Usar analisador de log personalizado](custom-log-parser.md).


Atributos de dados (de acordo com a documentação do fornecedor):


|                 Fonte de dados                  |    URL do aplicativo de destino    |    IP do aplicativo de destino     |       Nome de usuário       |      IP de Origem       |    Tráfego total     |    Bytes carregados    |
|----------------------------------------------|----------------------|----------------------|----------------------|----------------------|----------------------|----------------------|
|                  Barracuda                   | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> |          Não          |          Não          |
|                  Blue Coat                   | <strong>Sim</strong> |          Não          | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> |
|                  Checkpoint                  |          Não          | <strong>Sim</strong> |          Não          | <strong>Sim</strong> |          Não          |          Não          |
|              Cisco ASA (Syslog)              |          Não          | <strong>Sim</strong> |          Não          | <strong>Sim</strong> | <strong>Sim</strong> |          Não          |
|           Cisco ASA com FirePOWER           | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> |
|                  Cisco FWSM                  |          Não          | <strong>Sim</strong> |          Não          | <strong>Sim</strong> | <strong>Sim</strong> |          Não          |
|              Cisco Ironport WSA              | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> |
|                 Cisco Meraki                 | <strong>Sim</strong> | <strong>Sim</strong> |          Não          | <strong>Sim</strong> |          Não          |          Não          |
|           Clavister NGFW (Syslog)            | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> |
|                SonicWall (anteriormente conhecido como Dell)                | <strong>Sim</strong> | <strong>Sim</strong> |          Não          | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> |
|            Digital Arts i-FILTER             | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> |
|                  Fortigate                   |          Não          | <strong>Sim</strong> |          Não          | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> |
|                 Juniper SRX                  |          Não          | <strong>Sim</strong> |          Não          | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> |
|                 Juniper SSG                  |          Não          | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> |
|                  McAfee SWG                  | <strong>Sim</strong> |          Não          |          Não          | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> |
|                    MS TMG                    | <strong>Sim</strong> |          Não          | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> |
|              Redes de Palo Alto              |          Não          | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> |
|                    Sophos                    | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> |          Não          |
|                Squid (Comum)                | <strong>Sim</strong> |          Não          | <strong>Sim</strong> | <strong>Sim</strong> |          Não          | <strong>Sim</strong> |
|                Squid (Nativo)                | <strong>Sim</strong> |          Não          | <strong>Sim</strong> | <strong>Sim</strong> |          Não          | <strong>Sim</strong> |
| Websense – Relatório de detalhes investigativo (CSV) | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> |
|    Websense – Log de atividades da Internet (CEF)    | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> |
|                   Zscaler                    | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> |
     


## <a name="next-steps"></a>Próximas etapas

[Criar instantâneo de relatórios do Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

[Configurar upload de log automático para relatórios contínuos](configure-automatic-log-upload-for-continuous-reports.md)

[Trabalhando com os dados do Cloud Discovery](working-with-cloud-discovery-data.md)

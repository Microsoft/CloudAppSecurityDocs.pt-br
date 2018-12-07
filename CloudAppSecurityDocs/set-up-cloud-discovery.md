---
title: Implante o Cloud Discovery com o Cloud App Security | Microsoft Docs
description: Este artigo descreve o procedimento de configuração para colocar o Cloud Discovery em funcionamento.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/30/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: a9b5bd8d-305b-4e93-9a4c-a4683ea09080
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 3918d5595f5f4c18279c02ef896616e436d12636
ms.sourcegitcommit: cae782d508db9d1a7c0c362e9a23e83f74d48b21
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2018
ms.locfileid: "52743617"
---
# <a name="set-up-cloud-discovery"></a>Configurar o Cloud Discovery

*Aplica-se ao: Microsoft Cloud App Security*

O Cloud Discovery analisa seus logs de tráfego com base no catálogo de mais de 16.000 aplicativos de nuvem do Microsoft Cloud App Security. Os aplicativos são classificados e pontuados com base mais de 70 fatores de risco para fornecer visibilidade contínua do uso de nuvem, TI Sombra e o risco que a TI Sombra representa para sua organização.

## <a name="snapshot-and-continuous-risk-assessment-reports"></a>Relatórios contínuo e de instantâneo de avaliação de riscos 

Há dois tipos de relatórios que você pode gerar: 

- **Relatórios de instantâneo** – fornecem visibilidade ad hoc em um conjunto de logs de tráfego cujo upload é feito manualmente dos seus firewalls e proxies.

- **Relatórios contínuos** – analisam todos os logs que são encaminhados da sua rede usando o Cloud App Security. Eles oferecem maior visibilidade em todos os dados e identificam automaticamente usos anormais com o mecanismo de detecção de anomalias do Machine Learning ou por meio de políticas personalizadas que você definir. Esses relatórios podem ser criados conectando-se das seguintes maneiras:

  - [Integração do Windows Defender ATP](wdatp-integration.md): o Microsoft Cloud App Security integra-se ao Windows Defender ATP (Proteção Avançada contra Ameaças) nativamente, para simplificar a distribuição do Cloud Discovery, expandir as funcionalidades do Cloud Discovery para além de sua rede corporativa e habilitar a integração baseada em computador.
  - [Coletor de logs](discovery-docker.md): os coletores de logs permitem automatizar facilmente o carregamento de logs da rede. O coletor de log é executado em sua rede e recebe logs por Syslog ou FTP.
  - [Integração do Zscaler](zscaler-integration.md): se trabalha com o Cloud App Security e o Zscaler, você pode integrar os dois produtos para melhorar a experiência de segurança do Cloud Discovery. Juntos, o Cloud App Security e o Zscaler proporcionam uma implantação perfeita do Cloud Discovery, o bloqueio automático de aplicativos não sancionados e a avaliação de riscos diretamente no portal do Zscaler.

## <a name="log-process-flow-from-raw-data-to-risk-assessment"></a>Fluxo do processo de log: dos dados brutos a avaliação de riscos

O processo de geração de uma avaliação de riscos consiste nas seguintes etapas. O processo leva de alguns minutos a várias horas, dependendo da quantidade de dados processados.  

- **Carregar** – os logs do tráfego da Web da sua rede são carregados no portal.  

- **Analisar** – O Cloud App Security analisa e extrai dados de tráfego dos logs de tráfego com um analisador dedicado para cada fonte de dados.  

- **Analisar** – os dados de tráfego são examinados em relação ao Catálogo do Cloud App para identificar mais de 16 mil aplicativos de nuvem e avaliar sua pontuação de risco. Os usuários ativos e os endereços IP também são identificados como parte da análise.  

- **Gerar relatório** – Um relatório de avaliação de risco dos dados extraídos dos arquivos de log é gerado.


>[!NOTE]
> Os dados de relatórios contínuos são analisados duas vezes por dia.


## <a name="next-steps"></a>Próximas etapas

[Criar instantâneo de relatórios do Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

[Configurar upload de log automático para relatórios contínuos](configure-automatic-log-upload-for-continuous-reports.md)

[Trabalhando com os dados do Cloud Discovery](working-with-cloud-discovery-data.md)
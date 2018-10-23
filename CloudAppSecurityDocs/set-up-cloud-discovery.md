---
title: Implante o Cloud Discovery com o Cloud App Security | Microsoft Docs
description: Este tópico descreve o procedimento de configuração para colocar o Cloud Discovery em funcionamento.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/7/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: a9b5bd8d-305b-4e93-9a4c-a4683ea09080
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: cbc8999419f9c316323227c515fe111310231a9a
ms.sourcegitcommit: 53a1c990ff06674c26563a9ebcb1979818c3c063
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/09/2018
ms.locfileid: "48881795"
---
*Aplica-se ao: Microsoft Cloud App Security*


# <a name="set-up-cloud-discovery"></a>Configurar o Cloud Discovery
O Cloud Discovery analisa os logs de tráfego e os compara com o catálogo de mais de 16 mil aplicativos de nuvem do Microsoft Cloud App Security classificados e pontuados com base em mais de 70 fatores de risco, a fim de fornecer visibilidade contínua do uso da nuvem, TI de sombra e o risco que a TI de sombra representa para sua organização.

## <a name="snapshot-and-continuous-risk-assessment-reports"></a>Relatórios contínuo e de instantâneo de avaliação de riscos 

Há dois tipos de relatórios que você pode gerar: 
- **Relatórios de instantâneo** fornecem visibilidade ad hoc em um conjunto de logs de tráfego que são carregados manualmente dos seus firewalls e proxies.

- **Relatórios contínuos** analisam todos os logs que são encaminhados da sua rede usando o Cloud App Security. Eles oferecem maior visibilidade em todos os dados e identificam automaticamente usos anormais com o mecanismo de detecção de anomalias do Machine Learning ou por meio de políticas personalizadas que você definir. Esses relatórios podem ser criados conectando-se das seguintes maneiras:
  - [Integração do Windows Defender ATP](wdatp-integration.md): o Microsoft Cloud App Security integra-se ao Windows Defender ATP (Proteção Avançada contra Ameaças) nativamente, para simplificar a distribuição do Cloud Discovery, expandir as funcionalidades do Cloud Discovery para além de sua rede corporativa e habilitar a integração baseada em computador.
  - [Coletor de logs]( ):
  - [Integração do Zscaler](zscaler-integration.md): 

## <a name="log-process-flow-from-raw-data-to-risk-assessment"></a>Fluxo do processo de log: dos dados brutos a avaliação de riscos  
O processo de geração de uma avaliação de riscos consiste nas seguintes etapas e leva de alguns minutos a várias horas, dependendo da quantidade de dados processados.  

-   **Carregar** – os logs do tráfego da Web da sua rede são carregados no portal.  

-   **Analisar** – O Cloud App Security analisa e extrai dados de tráfego dos logs de tráfego com um analisador dedicado para cada fonte de dados.  

-   **Analisar** – os dados de tráfego são examinados em relação ao Catálogo do Cloud App para identificar mais de 16 mil aplicativos de nuvem e avaliar sua pontuação de risco. Os usuários ativos e os endereços IP também são identificados como parte da análise.  

-   **Gerar relatório** – Um relatório de avaliação de risco dos dados extraídos dos arquivos de log é gerado.   


>[!NOTE]
>- Os dados de relatórios contínuos são analisados duas vezes por dia.
> 


## <a name="see-also"></a>Consulte também

[Criar instantâneo de relatórios do Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

[Configurar upload de log automático para relatórios contínuos](configure-automatic-log-upload-for-continuous-reports.md)

[Trabalhando com os dados do Cloud Discovery](working-with-cloud-discovery-data.md)
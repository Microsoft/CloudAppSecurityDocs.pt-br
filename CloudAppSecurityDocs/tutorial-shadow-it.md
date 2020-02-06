---
title: Descobrir e gerenciar o Shadow IT | Microsoft Docs
description: Este tutorial descreve o processo para aplicar automaticamente rótulos de classificação da proteção de informações do Azure no Microsoft Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 11/11/2019
ms.topic: tutorial
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: dannyk
ms.suite: ems
ms.openlocfilehash: 4c85117dfd4080946fa5e1a205ec9fc890dea199
ms.sourcegitcommit: f81dd93841d7e5d01a1edaaf464c8656c4e7efda
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76814209"
---
# <a name="tutorial-discover-and-manage-shadow-it-in-your-network"></a>Tutorial: Descobrir e gerenciar o Shadow IT na sua rede

*Aplica-se a: Microsoft Cloud App Security*

Quando perguntam aos administradores de TI quantos aplicativos de nuvem eles acreditam que seus funcionários usam, em média, eles respondem 30 ou 40, quando, na realidade, a média é mais de 1.000 aplicativos distintos sendo usados por funcionários em sua organização. O Shadow IT ajuda você a conhecer e identificar quais aplicativos estão sendo usados e qual é seu nível de risco. Oitenta por cento dos funcionários usam aplicativos não sancionados que ninguém examinou e que podem não estar em conformidade com suas políticas de segurança e conformidade. E como seus funcionários podem acessar seus recursos e aplicativos fora de sua rede corporativa, não é mais suficiente ter regras e políticas em seus firewalls.

Este tutorial fornece instruções sobre como usar o Cloud Discovery para descobrir quais aplicativos estão sendo usados, explorar o risco desses aplicativos, configurar políticas para identificar novos aplicativos arriscados que estão sendo usados e proibir transações desses aplicativos para bloqueá-los nativamente usando seu dispositivo de proxy ou firewall.

> [!div class="checklist"]
>
> * Descobrir e identificar TI sombra
> * Avaliar e analisar
> * Gerenciar seus aplicativos
> * Relatório de descoberta de TI sombra avançado
> * Controlar aplicativos sancionados

## <a name="how-to-discover-and-manage-shadow-it-in-your-network"></a>Como descobrir e gerenciar o Shadow IT na sua rede

Use esse processo para distribuir o Cloud Discovery do Shadow IT em sua organização.

![ciclo de vida do Shadow IT](media/shadow-it-lifecycle.png)

### <a name="phase-1-discover-and-identify-shadow-it"></a>Fase 1: Descobrir e identificar TI sombra

1. **Descubra o Shadow IT**: identifique a postura de segurança de sua organização executando o Cloud Discovery em sua organização para ver o que realmente está acontecendo em sua rede. Para obter mais informações, confira [Configurar o Cloud Discovery](set-up-cloud-discovery.md). Isso pode ser feito usando qualquer um dos seguintes métodos:

    * Coloque o Cloud Discovery em execução rapidamente integrando-o ao [Microsoft Defender ATP](wdatp-integration.md). Essa integração nativa permite que você inicie imediatamente a coleta de dados no tráfego de nuvem em seus dispositivos Windows 10 na rede e fora dela.

    * Para cobertura em todos os dispositivos conectados à sua rede, é importante implantar o [coletor de logs do Cloud App Security](discovery-docker.md) em seus firewalls e outros proxies para coletar dados de seus pontos de extremidade e enviá-los para o Cloud App Security para análise.

    * Integre o Cloud App Security ao seu proxy. O Cloud App Security integra-se nativamente a alguns proxies de terceiros, incluindo o [Zscaler](zscaler-integration.md).

Como as políticas são diferentes entre grupos de usuários, regiões e grupos de negócios, talvez você queira criar um relatório do Shadow IT dedicado para cada uma dessas unidades. Para obter mais informações, confira [Docker on Windows local](discovery-docker-windows.md#continuous-reports).

Agora que o Cloud Discovery está em execução na sua rede, examine os relatórios contínuos que são gerados e o [painel do Cloud Discovery](working-with-cloud-discovery-data.md) para obter uma visão completa de quais aplicativos estão sendo usados em sua organização. É uma boa ideia vê-los por categoria, porque você geralmente descobrirá que aplicativos não sancionados estão sendo usados para fins legítimos relacionados ao trabalho que não foram atendidos por um aplicativo sancionado.

1. **Identifique os níveis de risco de seus aplicativos**: use o catálogo de aplicativos de nuvem do Cloud App Security para aprofundar-se nos riscos envolvidos em cada aplicativo descoberto. O catálogo de risco do Cloud App Security inclui mais de 16 mil aplicativos que são avaliados usando mais de 80 fatores de risco. os fatores de risco começam com informações gerais sobre o aplicativo (em que local é a sede do aplicativo, quem é o editor) e, por meio de controles e medidas de segurança (suporte para criptografia em repouso), fornece um log de auditoria da atividade do usuário. Para saber mais, confira [Como trabalhar com pontuação de risco](risk-score.md).

    * No portal do Cloud App Security, em **Descobrir**, clique em **Aplicativos descobertos**. Filtre a lista de aplicativos descobertos na organização pelos fatores de risco com os quais você está preocupado. Por exemplo, você pode usar os filtros Avançados para localizar todos os aplicativos com uma pontuação de risco inferior a 8.

    * Para fazer drill down no aplicativo a fim de entender mais sobre a conformidade, clique no nome do aplicativo e, em seguida, clique na guia **Informações** para ver detalhes sobre os fatores de risco de segurança do aplicativo.

### <a name="phase-2-evaluate-and-analyze"></a>Fase 2: Avaliar e analisar

1. **Avaliar a conformidade**: verifique se os aplicativos são certificados como em conformidade com os padrões da sua organização, como HIPAA, SOC2 e GDPR.

    * No portal do Cloud App Security, em **Descobrir**, clique em **Aplicativos descobertos**. Filtre a lista de aplicativos descobertos na organização pelos fatores de risco de conformidade com os quais você está preocupado. Por exemplo, use a consulta sugerida para filtrar aplicativos que não estão sem conformidade.

    * Para fazer drill down no aplicativo a fim de entender mais sobre a conformidade, clique no nome do aplicativo e, em seguida, clique na guia **Informações** para ver detalhes sobre os fatores de risco de conformidade do aplicativo.

1. **Analisar o uso**: agora que você sabe se deseja ou não que o aplicativo seja usado na sua organização, você quer investigar como e quem o está usando. Se ele for usado apenas de uma maneira limitada em sua organização, talvez esteja tudo bem. Porém, se o uso estiver aumentando, você deseja ser notificado sobre ele para que possa decidir se deve bloquear o aplicativo.

    * No portal do Cloud App Security, em **Descobrir**, clique em **Aplicativos descobertos** e faça uma busca detalhada clicando no aplicativo específico que você deseja investigar. A guia **Usar** permite que você saiba quantos usuários ativos estão usando o aplicativo e a quantidade de tráfego que ele está gerando. Isso já pode dar uma visão muito boa do que está acontecendo com o aplicativo. Em seguida, se você quiser ver quem, especificamente, está usando o aplicativo, poderá fazer uma busca mais detalhada clicando em **Total de usuários ativos**. Essa etapa importante pode fornecer informações pertinentes. Por exemplo, se você descobrir que todos os usuários de um aplicativo específico são do departamento de marketing, talvez haja uma necessidade comercial para esse aplicativo e, se ele for arriscado, você deverá conversar com os funcionários sobre um alternativa antes de bloqueá-lo.

    * Aprofunde-se ainda mais investigando o uso de aplicativos descobertos. Exiba os subdomínios e recursos para saber mais sobre atividades específicas, acesso a dados e uso de recursos em seus serviços de nuvem. Para obter mais informações, confira [Ver mais sobre aplicativos descobertos](discovered-apps.md#deep-dive-into-discovered-apps) e [Descobrir recursos e aplicativos personalizados](discovered-apps.md#discover-resources-and-custom-apps).

1. Use o catálogo de aplicativos de nuvem e filtre os aplicativos que pertencem à mesma categoria de aplicativo. Além disso, usando os filtros avançados, identifique soluções que estejam em conformidade com os diferentes controles de segurança necessários para manter a conformidade com a política da organização.

### <a name="phase-3-manage-your-apps"></a>Fase 3: Gerenciar seus aplicativos

* **Gerenciar aplicativos de nuvem**: o Cloud App Security ajuda no processo de gerenciamento do uso do aplicativo em sua organização. Depois de identificar os diferentes padrões e comportamentos usados em sua organização, você pode criar marcas de aplicativo personalizadas para classificar cada aplicativo de acordo com o status ou justificativa comercial. Essas tags então podem ser usadas para fins de monitoramento específicos, por exemplo, identificar o alto tráfego que está indo para os aplicativos marcados como aplicativos de armazenamento em nuvem arriscados. As marcas de aplicativo podem ser gerenciadas em **Configurações do Cloud Discovery** > **Marcas de aplicativo**. Essas marcas podem ser usadas posteriormente para filtrar nas páginas do Cloud Discovery e criar políticas usando-as.

* **Monitoramento contínuo**: agora que você investigou minuciosamente os aplicativos, talvez queira definir políticas que os monitorem e forneçam controle quando necessário.

Agora é hora de criar políticas para que você possa ser alertado automaticamente quando acontecer algo com que você esteja preocupado. Por exemplo, talvez você queira criar uma **Política de descoberta de aplicativo** que lhe permita saber quando há um pico nos downloads ou no tráfego de um aplicativo com o qual você esteja preocupado. Para fazer isso, você deve habilitar a **Política de comportamentos anormais em usuários descobertos**, a **Verificação de conformidade de aplicativo de armazenamento em nuvem** e **Novo aplicativo com risco**. Você também deve definir a política para ser notificado por email ou mensagem de texto. Para obter mais informações, confira [referência de modelo de política](policy-template-reference.md), saiba mais sobre as [Políticas do Cloud Discovery](cloud-discovery-policies.md) e configure [Políticas de descoberta de aplicativos](cloud-discovery-policies.md).

Veja a página alertas e use o filtro **Tipo de política** para examinar os alertas de descoberta de aplicativos. Para aplicativos que corresponderam às políticas de descoberta de aplicativo, é recomendado que você faça uma investigação avançada para saber mais sobre a justificativa comercial do uso do aplicativo, por exemplo, você pode entrar em contato com os usuários dele. Em seguida, repita as etapas na Fase 2 para avaliar o risco do aplicativo. Em seguida, determine as próximas etapas para o aplicativo, se você aprova o uso dele no futuro ou deseja bloqueá-lo na próxima vez que um usuário o acessar, caso em que você deve marcá-lo como não sancionado para que ele possa ser bloqueado usando seu firewall, proxy ou gateway Web seguro. Para obter mais informações, confira [Integrar com o Microsoft Defender ATP](wdatp-integration.md#block-access-to-unsanctioned-cloud-apps), [Integrar com o Zscaler](zscaler-integration.md), [Integrar com o iboss](iboss-integration.md) e [Exportar um script de bloqueio para controlar os aplicativos descobertos](governance-discovery.md#export-a-block-script-to-govern-discovered-apps).

### <a name="phase-4-advanced-shadow-it-discovery-reporting"></a>Fase 4: Relatório de descoberta de TI sombra avançado

Além das opções de relatório disponíveis no Cloud App Security, você pode integrar os logs do Cloud Discovery ao Azure Sentinel para investigação e análise adicionais. Depois que os dados estiverem no Azure Sentinel, você poderá exibi-los em painéis, executar consultas usando a linguagem de consulta do Kusto, exportar consultas para o Microsoft Power BI, integrar com outras fontes e criar alertas personalizados. Para saber mais, confira [Integração ao Azure Sentinel](siem-sentinel.md).

### <a name="phase-5-control-sanctioned-apps"></a>Fase 5: Controlar aplicativos sancionados

1. Para habilitar o controle de aplicativo via APIs, [conecte aplicativos por meio da API](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) para monitoramento contínuo.

2. proteger aplicativos usando [Controle de Aplicativos de Acesso Condicional](proxy-intro-aad.md).

A natureza dos aplicativos de nuvem significa que eles são atualizados diariamente e novos aplicativos surgem o tempo todo. Por isso, os funcionários estão continuamente usando novos aplicativos e é importante continuar acompanhando, revisando e atualizando suas políticas, verificando quais aplicativos seus usuários estão usando, bem como seus padrões de uso e comportamento. Você sempre pode acessar o painel do Cloud Discovery e ver quais novos aplicativos estão sendo usados e seguir as instruções neste artigo novamente para garantir que sua organização e seus dados estejam protegidos.

## <a name="see-also"></a>Consulte Também

> [!div class="nextstepaction"]
> [Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]  

---
title: Descobrir e gerenciar a TI sombra | Microsoft Docs
description: Este tutorial descreve o processo para aplicar automaticamente os rótulos de classificação da Proteção de Informações do Azure no Microsoft Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/6/2019
ms.topic: tutorial
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: eac0b192-98d7-4939-9a07-1d4a7f8c39c3
ms.reviewer: dannyk
ms.suite: ems
ms.openlocfilehash: 3e31313739befa39b11853df971dd0c490884e07
ms.sourcegitcommit: 2a25d1af0560243d7f926c87bf56230bdf336ba9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54142277"
---
*Aplica-se a: Microsoft Cloud App Security*


# <a name="tutorial-discover-and-manage-shadow-it-in-your-network"></a>Tutorial: Descobrir e gerenciar a TI sombra na sua rede

Quando é perguntado aos administradores de TI quantos aplicativos de nuvem eles acham que seus funcionários usam, em média eles dizem 30 ou 40, quando na realidade, a média é de mais de mil aplicativos separados usados pelos funcionários da organização. A TI sombra ajuda você a identificar quais aplicativos estão sendo usados e qual é seu nível de risco. 80% dos funcionários usam aplicativos não sancionados que ninguém revisou e podem não estar em conformidade com as políticas de segurança e conformidade da empresa. E como os funcionários são capazes de acessar recursos e aplicativos da empresa de fora da rede corporativa, não é mais suficiente ter políticas e regras nos firewalls. 

Este tutorial fornece instruções de como usar o Cloud Discovery para descobrir quais aplicativos estão sendo usados, explorar o risco desses aplicativos, configurar políticas para identificar novos aplicativos arriscados que estão sendo usados e cancelar a sanção desses aplicativos para bloqueá-los nativamente usando um dispositivo de proxy ou de firewall.

> [!div class="checklist"]
> * Descobrir e identificar a TI sombra
> * Avaliar e analisar
> * Gerenciar seus aplicativos
> * Controlar aplicativos sancionados
 
## <a name="how-to-discover-and-manage-shadow-it-in-your-network"></a>Como descobrir e gerenciar a TI sombra na sua rede

Use esse processo para distribuir o Cloud Discovery de TI sombra na sua organização.

![ciclo de vida da TI sombra](./media/shadow-it-lifecycle.png)

### <a name="phase-1-discover-and-identify-shadow-it"></a>Fase 1: Descobrir e identificar a TI sombra
    
1. **Descobrir a TI sombra**: identifique a situação de segurança da sua organização executando o Cloud Discovery em sua organização para ver o que realmente está acontecendo na rede. Para obter mais informações, confira [Configurar o Cloud Discovery](set-up-cloud-discovery.md). Isso pode ser feito usando um dos seguintes métodos:
  
    - Integre o Cloud App Security com o proxy. O Cloud App Security integra-se nativamente com alguns proxies de terceiros, incluindo o [Zscaler](zscaler-integration.md).
    
    - Coloque o Cloud Discovery em funcionamento rapidamente integrando-o ao [Windows Defender ATP](wdatp-integration.md). Essa integração nativa permite que você comece imediatamente a coletar dados sobre o tráfego de nuvem em seus dispositivos Windows 10 dentro e fora da rede.
   
    - Para obter uma cobertura em todos os dispositivos conectados à rede, é importante implantar o [coletor de logs do Cloud App Security](discovery-docker.md) em seus firewalls e em outros proxies para coletar dados dos pontos de extremidade e enviá-los ao Cloud App Security para análise.


Como as políticas são diferentes entre grupos de usuários, regiões e grupos de negócios, é possível criar um relatório de TI sombra dedicado a cada uma dessas unidades. Para obter mais informações, confira (discovery-docker-windows#continuous-reports).


Agora que o Cloud Discovery está em execução na rede, examine os relatórios contínuos que são gerados e confira o [painel do Cloud Discovery](working-with-cloud-discovery-data.md) para ter uma visão completa de quais aplicativos estão sendo usados na organização. É interessante examiná-los por categoria, porque normalmente você perceberá que os aplicativos não sancionados estão sendo usados para fins relacionados a trabalhos legítimos que não foram atendidos por um aplicativo sancionado. 

2. **Identificar os níveis de risco dos aplicativos**: use o catálogo de aplicativos de nuvem do Cloud App Security para aprofundar-se nos riscos envolvidos em cada aplicativo descoberto. O catálogo de risco do Cloud App Security inclui mais de 16 mil aplicativos que são avaliados com mais de 70 fatores de risco. Os fatores de risco começam com informações gerais sobre o aplicativo (onde é a sede do aplicativo, quem é o editor) e por meio de medidas e controles de segurança (o suporte para criptografia em repouso fornece um log de auditoria da atividade do usuário). Para obter mais informações, confira [Trabalhando com a pontuação de risco](risk-score.md),
    
   - No portal do Cloud App Security, em **Discover**, clique em **Aplicativos descobertos**. Filtre a lista de aplicativos descobertos em uso na organização pelos fatores de risco com os quais você está preocupado. Por exemplo, você pode usar os filtros Avançados para localizar todos os aplicativos com uma pontuação de risco menor que 8. 

   - Você pode fazer drill down no aplicativo para entender mais sobre a conformidade clicando no nome do aplicativo e, em seguida, clicando na guia **Informações** para ver detalhes sobre os fatores de risco de segurança do aplicativo.
    
### <a name="phase-2-evaluate-and-analyze"></a>Fase 2: Avaliar e analisar

1. **Avaliar a conformidade**: verifique se os aplicativos são certificados como em conformidade com os padrões da organização, como HIPAA, SOC2, RGPD.
   - No portal do Cloud App Security, em **Discover**, clique em **Aplicativos descobertos**. Filtre a lista de aplicativos descobertos na organização pelos fatores de risco de conformidade com os quais você está preocupado. Por exemplo, use a consulta sugerida para filtrar os aplicativos fora de conformidade.
   - Você pode fazer drill down no aplicativo para entender mais sobre a conformidade clicando no nome do aplicativo e, em seguida, clicando na guia **Informações** para ver detalhes sobre os fatores de risco de conformidade do aplicativo.

2. **Analisar o uso**: agora que você sabe que deseja ou não que o aplicativo seja usado na organização, investigue como e quem o está usando. Se ele for usado apenas de maneira limitada na organização, talvez não haja problemas, mas, se o uso estiver crescendo, você vai querer ser notificado para que possa decidir se deseja bloquear o aplicativo.
    - No portal do Cloud App Security, em **Descoberta**, clique em **Aplicativos descobertos** e, em seguida, faça drill down clicando no aplicativo específico que deseja investigar. A guia **Uso** permite que você saiba quantos usuários ativos estão usando o aplicativo e a quantidade de tráfego que ele está gerando. Isso já pode oferecer uma visão muito boa do que está acontecendo com o aplicativo. Em seguida, se você quiser ver quem, especificamente, está usando o aplicativo, faça mais drill down clicando em **Total de usuários ativos**. Essa etapa pode fornecer informações pertinentes, por exemplo, se você descobrir que todos os usuários de um aplicativo específico são do departamento de Marketing, poderá haver uma necessidade comercial para esse aplicativo e, se ele for arriscado, você poderá conversar com eles sobre uma alternativa antes de bloqueá-lo.

4. Use o catálogo de aplicativos de nuvem e filtre os aplicativos que pertencem à mesma categoria de aplicativo. Além disso, usando os filtros avançados identifique soluções que estão em conformidade com os diferentes controles de segurança necessários para manter a conformidade com a política da organização.


### <a name="phase-3-manage-your-apps"></a>Fase 3: Gerenciar seus aplicativos
    
- **Gerenciar aplicativos de nuvem**: O Cloud App Security ajuda você com o processo de gerenciar o uso de aplicativos na organização. Depois de identificar os diferentes padrões e comportamentos usados na organização, você pode criar marcas de aplicativo personalizadas para classificar cada aplicativo de acordo com o status ou a justificativa dos negócios.
Essas marcas podem ser usadas para fins de monitoramento específicos, por exemplo, para identificar um tráfego alto direcionado a aplicativos que estejam marcados como aplicativos de armazenamento em nuvem arriscados. As marcas de aplicativo podem ser gerenciadas em **Configurações do Cloud Discovery** > **Marcas de aplicativo**. Mais tarde, essas marcas podem ser usadas para a filtragem nas páginas do Cloud Discovery e a criação de políticas que as usem.
    
Agora é hora de criar políticas para que você possa ser alertado automaticamente quando acontecer algo com que você se preocupe. Por exemplo, é possível criar uma **Política de descoberta de aplicativo** que informe quando há um pico nos downloads ou no tráfego de um aplicativo com o qual você se preocupe. Você pode definir a política para ser notificado por email ou mensagem de texto. Para obter mais informações, confira [referência de modelo de política](policy-template-reference.md) e saiba mais sobre as [políticas do Cloud Discovery](cloud-discovery-policies.md).

- **Monitoramento contínuo**: agora que você investigou os aplicativos cuidadosamente, é possível definir políticas que monitorem os aplicativos e forneçam controle onde for necessário.


Configure [**Políticas de descoberta de aplicativo**](cloud-discovery-policies.md). Por exemplo, você deve habilitar a **Política de comportamento anormal nos usuários descobertos**, a **Verificação de conformidade de aplicativo de armazenamento em nuvem** e a identificação de **Novo aplicativo arriscado**.


Examine essa página de alertas e use o filtro **Tipo de política** para examinar os alertas de descoberta de aplicativo. Para aplicativos que corresponderam às políticas de descoberta de aplicativo, é recomendado que você faça uma investigação avançada para saber mais sobre a justificativa dos negócios para usar o aplicativo, por exemplo, entrar em contato com os usuários dos aplicativos. Em seguida, repita as etapas da Fase 2 para avaliar o risco do aplicativo. Em seguida, determine as próximas etapas do aplicativo, se você quer aprovar o uso futuro ou bloqueá-lo na próxima vez que um usuário o acessar. Neste caso, você deve marcá-lo como não sancionado para que ele possa ser bloqueado usando o firewall, o proxy ou o gateway da Web seguro. 


### <a name="phase-4-control-sanctioned-apps"></a>Fase 4: Controlar aplicativos sancionados

1. Para habilitar o controle do aplicativo por meio de APIs, [conecte os aplicativos por meio da API](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md). (enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) para monitoramento contínuo.

2. Proteja os aplicativos usando o [Controle de Aplicativos de Acesso Condicional](proxy-intro-aad.md).


A natureza dos aplicativos de nuvem significa que eles são atualizados diariamente e novos aplicativos aparecem o tempo todo. Por isso, os funcionários usam novos aplicativos continuamente e é importante acompanhar, examinar e atualizar as políticas da empresa, verificando quais aplicativos os usuários estão usando, bem como seus padrões de uso e comportamento. Você sempre pode acessar o painel do Cloud Discovery, ver quais novos aplicativos estão sendo usados e seguir as instruções neste artigo novamente para garantir que a organização e os dados estejam protegidos.


## <a name="see-also"></a>Consulte Também  
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
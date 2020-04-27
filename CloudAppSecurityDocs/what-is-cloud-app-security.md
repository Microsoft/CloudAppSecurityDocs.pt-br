---
title: O que é o Cloud App Security?
description: Este artigo descreve o Microsoft Cloud App Security e como ele funciona.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 8/15/2019
ms.topic: overview
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: d46756b1-7dd8-4190-9799-3a97688f1266
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 49ecd0d844dd30c4816095686a353c301df4fa49
ms.sourcegitcommit: 0b929f7c8feed7dfb40d5294179fd5c6fc079614
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/21/2020
ms.locfileid: "74720453"
---
# <a name="microsoft-cloud-app-security-overview"></a>Visão geral do Microsoft Cloud App Security

*Aplica-se a: Microsoft Cloud App Security*

> [!NOTE]
> Para obter informações sobre o Office 365 Cloud App Security, consulte [Introdução ao Office 365 Cloud App Security](https://support.office.com/article/Get-started-with-Advanced-Management-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a).

A migração para a nuvem aumenta a flexibilidade tanto para funcionários quanto para a TI. No entanto, ela também apresenta novos desafios e complexidades para manter sua organização segura. Para obter todos os benefícios dos aplicativos e serviços de nuvem, uma equipe de TI precisa encontrar o equilíbrio ideal entre dar suporte ao acesso e manter o controle para proteger dados críticos.

O Microsoft Cloud App Security é um Agente de Segurança de Acesso à Nuvem que oferece suporte a vários modos de implantação, incluindo coleta de log, conectores de API e proxy reverso. Ele fornece visibilidade avançada, controle sobre a viagem de dados e análises sofisticadas para identificar e combater ameaças cibernéticas em todos os seus serviços de nuvem da Microsoft e de terceiros.

O Microsoft Cloud App Security integra-se nativamente às principais soluções da Microsoft e foi desenvolvido com profissionais de segurança em mente. Ele fornece implantação simples, gerenciamento centralizado e recursos de automação inovadores.

Para obter mais informações sobre licenciamento, consulte a [folha de dados licenciamento do Microsoft Cloud App Security](https://aka.ms/mcaslicensing).

## <a name="the-cloud-app-security-framework"></a>A estrutura do Cloud App Security

- **Descubra e controle o uso de Shadow IT**: identifique os aplicativos de nuvem, IaaS e PaaS usados ​​por sua organização. Investigue os padrões de uso, avalie os níveis de risco e a preparação para os negócios de mais de 16.000 aplicativos SaaS em relação a mais de 80 riscos. Comece a gerenciá-los para garantir a segurança e a conformidade.

- **Proteja suas informações confidenciais em qualquer lugar na nuvem**: reconheça, classifique e proteja a exposição de informações confidenciais em repouso. Aproveite as políticas prontas para uso e os processos automatizados para aplicar controles em tempo real em todos os seus aplicativos na nuvem.

- **Proteja contra ameaças cibernéticas e anomalias**: detecte comportamento incomum em aplicativos de nuvem para identificar ransomware, usuários comprometidos ou aplicativos não autorizados, analise o uso de alto risco e faça correções automaticamente para limitar o risco à sua organização.

- **Avalie a conformidade de seus aplicativos na nuvem**: avalie se os seus aplicativos na nuvem atendem aos requisitos de conformidade relevantes, incluindo conformidade regulamentar e padrões do setor. Evite vazamentos de dados para aplicativos não compatíveis e limite o acesso a dados regulamentados.

## <a name="architecture"></a>Arquitetura

O Cloud App Security integra visibilidade à sua nuvem ao:

- Usar o Cloud Discovery para mapear e identificar seu ambiente de nuvem e os aplicativos na nuvem que sua organização está usando.
- Aprovar e desaprovar aplicativos em sua nuvem.
- Usar conectores de aplicativos de fácil implantação que aproveitam as APIs do provedor para visibilidade e governança de aplicativos aos quais você se conecta.
- Usar a proteção de Controle de Aplicativos de Acesso Condicional para obter visibilidade e controle em tempo real do acesso e das atividades em seus aplicativos na nuvem.
- Ajudar você a ter controle contínuo ao configurar as políticas e depois ajustá-las continuamente.

![Diagrama de arquitetura do Cloud App Security](media/proxy-architecture.png)

### <a name="data-retention--compliance"></a>Conformidade e retenção de dados

Para obter mais informações sobre a conformidade e retenção de dados do Microsoft Cloud App Security, consulte [Segurança e privacidade de dados do Microsoft Cloud App Security ](cas-compliance-trust.md).

### <a name="cloud-discovery"></a>Cloud Discovery

O Cloud Discovery usa seus logs de tráfego para descobrir e analisar dinamicamente os aplicativos na nuvem sendo usados pela sua organização. Para criar um relatório de instantâneos do uso da nuvem feito pela sua organização, você pode carregar manualmente os arquivos de log de seus firewalls ou proxies para análise. Para configurar relatórios contínuos, use coletores de logs do Cloud App Security para encaminhar seus logs periodicamente.

Para obter mais informações sobre o Cloud Discovery, consulte [Configurar o Cloud Discovery](set-up-cloud-discovery.md).

### <a name="sanctioning-and-unsanctioning-an-app"></a>Aprovar e desaprovar um aplicativo

Você pode usar o Cloud App Security para aprovar ou desaprovar aplicativos em sua organização usando o *Catálogo de aplicativos na nuvem*. A equipe de analistas da Microsoft tem um catálogo abrangente e em crescimento contínuo com mais de 16.000 aplicativos na nuvem que são classificados e pontuados com base nos padrões do setor. Você pode usar o catálogo de aplicativos em nuvem para classificar o risco de seus aplicativos na nuvem com base em certificações regulatórias, padrões do setor e práticas recomendadas. Depois, personalize as pontuações e os pesos de vários parâmetros conforme as necessidades da sua organização. Com base nessas pontuações, o Cloud App Security permite que você saiba o quão arriscado é um aplicativo. A pontuação se baseia em mais de 80 fatores de risco que podem afetar seu ambiente.

### <a name="app-connectors"></a>Conectores de aplicativos

Os conectores de aplicativos usam APIs de provedores de aplicativos na nuvem para integrar o Cloud App Security Cloud a outros aplicativos na nuvem. Os conectores de aplicativos estendem o controle e a proteção. Eles também fornecem acesso a informações diretamente dos aplicativos na nuvem para a análise do Cloud App Security.

Para conectar um aplicativo e estender a proteção, o administrador de aplicativos autoriza o Cloud App Security a acessar o aplicativo. Em seguida, o Cloud App Security consulta o aplicativo quanto a logs de atividade e examina dados, as contas e o conteúdo na nuvem. O Cloud App Security pode impor políticas, detectar ameaças e fornecer ações de governança para resolver problemas.

O Cloud App Security usa as APIs fornecidas pelo provedor de nuvem. Cada aplicativo tem suas próprias limitações de estrutura e de API. O Cloud App Security trabalha com provedores de aplicativos na otimização do uso de APIs para garantir o melhor desempenho. Considerando as várias limitações que os aplicativos impõem às APIs (como limitação, limites de API e janelas de API com mudança de tempo dinâmica), os mecanismos do Cloud App Security utilizam a capacidade permitida. Algumas operações, como a verificação de todos os arquivos no locatário, requerem um grande número de APIs para que elas fiquem espalhadas por um período mais longo. Espere algumas que algumas políticas sejam executadas por várias horas ou vários dias.

### <a name="conditional-access-app-control-protection"></a>Proteção do Controle de Aplicativos de Acesso Condicional

O Controle de Aplicativos de Acesso Condicional do Microsoft Cloud App Security usa a arquitetura de proxy reverso para fornecer a você as ferramentas necessárias para ter visibilidade e controle em tempo real sobre o acesso e sobre as atividades executadas em seu ambiente na nuvem. Com o Controle de Aplicativos de Acesso Condicional, você pode proteger sua organização para:

- Evitar vazamentos de dados ao bloquear downloads antes que eles ocorram
- Definir regras que forcem os dados armazenados e baixados da nuvem para serem protegidos com criptografia
- Ter visibilidade sobre pontos de extremidade desprotegidos para que você possa monitorar o que está sendo feito em dispositivos não gerenciados
- Controlar o acesso de redes não corporativas ou endereços IP de risco

### <a name="policy-control"></a>Controle de política

Você pode usar políticas para definir o comportamento dos usuários na nuvem. Use políticas para detectar um comportamento de risco, violações ou atividades e pontos de dados suspeitos em seu ambiente na nuvem. Se for preciso, você pode usar políticas para integrar processos de correção para obter uma mitigação de risco completa. Os tipos de políticas se correlacionam aos diferentes tipos de informações que você pode reunir sobre seu ambiente na nuvem e os tipos de ações de correção que podem ser tomados.

## <a name="related-videos"></a>Vídeos relacionados

- [Unindo a comunidade de segurança](https://channel9.msdn.com/Shows/Microsoft-Security/Join-the-Security-Community)

## <a name="next-steps"></a>Próximas etapas

Saiba mais sobre as noções básicas em [Introdução ao Cloud App Security](getting-started-with-cloud-app-security.md).

[!INCLUDE [Open support ticket](includes/support.md)].

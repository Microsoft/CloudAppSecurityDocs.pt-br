---
title: O que é o Cloud App Security?
description: Este artigo descreve o Microsoft Cloud App Security e como ele funciona.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/14/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: d46756b1-7dd8-4190-9799-3a97688f1266
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: a2419702d66602a3a9aa0cef80b13d2c1103c3a2
ms.sourcegitcommit: 475dc75456f4683336e3e4875e3155677e4fb827
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/16/2018
ms.locfileid: "53450572"
---
# <a name="microsoft-cloud-app-security-overview"></a>Visão geral do Microsoft Cloud App Security

*Aplica-se a: Microsoft Cloud App Security*

> [!NOTE]
> Para saber mais sobre o Cloud App Security do Office 365, consulte [Introdução ao Cloud App Security do Office 365](https://support.office.com/article/Get-started-with-Advanced-Management-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a).

A migração para a nuvem aumenta a flexibilidade dos funcionários e reduz os custos de TI. No entanto, ela também apresenta novos desafios e complexidades para manter sua organização segura. Para obter todos os benefícios dos aplicativos de nuvem, uma equipe de TI precisa encontrar o equilíbrio ideal entre dar suporte ao acesso e manter o controle para proteger dados críticos.  

O Cloud App Security é um componente crítico da pilha do Microsoft Cloud Security. É uma solução abrangente que pode ajudar sua organização durante a transição, para que você aproveite ao máximo a promessa dos aplicativos na nuvem, enquanto o mantém no controle com maior visibilidade das atividades. Ela também ajuda a aumentar a proteção de dados críticos em aplicativos de nuvem. Com ferramentas que ajudam a descobrir a TI Invisível, avaliar os riscos, impor políticas, investigar atividades e parar ameaças, sua organização pode migrar para a nuvem com segurança enquanto mantém o controle de dados críticos. 

## <a name="the-cloud-app-security-framework"></a>A estrutura do Cloud App Security  

- **Cloud Discovery**: Descubra o uso completo da nuvem em sua organização, incluindo avaliação de controle e de risco e relatórios de TI sombra.

- **Proteção de dados**: Monitore e controle seus dados na nuvem obtendo visibilidade, impondo políticas DLP, alertas e investigação. 

- **Proteção contra ameaças**: Detecte usos anormais e incidentes de segurança. Use ferramentas avançadas de investigação e análise comportamental para atenuar o risco e definir políticas e alertas para obter o máximo de controle sobre o tráfego na nuvem da rede.

## <a name="architecture"></a>Arquitetura  

O Cloud App Security integra a visibilidade à sua nuvem:  

- Usando o Cloud Discovery para mapear e identificar seu ambiente de nuvem e os aplicativos na nuvem que sua organização está usando.
- Sancionando e cancelando a sanção de aplicativos em sua nuvem.  
- Usando conectores de aplicativos fáceis de implantar que aproveitam as vantagens das APIs do provedor, para visibilidade e governança dos aplicativos ao quais você se conecta.  
- Usando a proteção do Controle de Aplicativos de Acesso Condicional para obter visibilidade em tempo real e controle sobre o acesso e as atividades dos aplicativos na nuvem.
- Ajudando você a ter controle contínuo com a configuração e o posterior ajuste fino constante das políticas.  

![Diagrama de arquitetura do Cloud App Security](./media/proxy-architecture.png)  

### <a name="data-retention--compliance"></a>Conformidade e retenção de dados

Para saber mais sobre conformidade e retenção de dados do Microsoft Cloud App Security, confira [Privacidade e segurança de dados do Microsoft Cloud App Security](cas-compliance-trust.md).

### <a name="cloud-discovery"></a>Cloud Discovery  

O Cloud Discovery usa os logs de tráfego para descobrir e analisar dinamicamente os aplicativos de nuvem que sua organização está utilizando. Para criar um relatório de instantâneo de uso de nuvem da sua organização, você pode carregar manualmente os arquivos de log de seus firewalls ou proxies para análise. Para configurar relatórios contínuos, use coletores de log do Cloud App Security para encaminhar periodicamente os logs.  

Para obter mais informações sobre o Cloud Discovery, consulte [Configurar o Cloud Discovery](set-up-cloud-discovery.md).

### <a name="sanctioning-and-unsanctioning-an-app"></a>Sanção e o cancelamento de sanção de um aplicativo  

Você pode usar o Cloud App Security para sancionar ou cancelar a sanção de aplicativos em sua organização usando nosso *Catálogo de aplicativos de nuvem*. A equipe de analistas da Microsoft tem um catálogo extenso e em constante expansão de mais de 16 mil aplicativos de nuvem que são classificados e pontuados com base nos padrões do setor. Você pode usar o catálogo de aplicativos de nuvem para classificar o risco para seus aplicativos de nuvem com base em certificações regulatórias, padrões da indústria e práticas recomendadas. Depois, personalize as pontuações e os pesos de diversos parâmetros de acordo com as necessidades da sua organização. Com base nessas pontuações, o Cloud App Security informa você sobre os riscos de um aplicativo. A pontuação baseia-se em mais de 70 fatores de risco que podem afetar seu ambiente.  

### <a name="app-connectors"></a>Conectores de aplicativos

Os conectores de aplicativos usam APIs de provedores de aplicativos de nuvem para integrar a nuvem do Cloud App Security com outros aplicativos de nuvem. Conectores de aplicativo estendem o controle e a proteção. Eles também fornecem acesso às informações diretamente de aplicativos de nuvem para análise do Cloud App Security.  

Para conectar um aplicativo e estender a proteção, o administrador do aplicativo autoriza o Cloud App Security a acessar o aplicativo. Em seguida, o Cloud App Security consulta o aplicativo para logs de atividade e verifica dados, contas e conteúdo de nuvem. O Cloud App Security pode impor políticas, detectar ameaças e fornecer ações de governança para resolver problemas.  

O Cloud App Security usa as APIs fornecidas pelo provedor de nuvem. Cada aplicativo tem sua própria estrutura e limitações de API. O Cloud App Security trabalha com os provedores de aplicativo para otimizar o uso das APIs a fim de garantir o melhor desempenho. Considerando as diversas limitações que os aplicativos impõem sobre as APIs (como as limitações, limites de API, janelas de API de mudança de tempo dinâmicas), os mecanismos do Cloud App Security utilizam a capacidade permitida. Algumas operações, como a verificação de todos os arquivos no locatário, exigem uma grande quantidade de APIs e, portanto, são distribuídas por um período mais longo. Espere algumas que algumas políticas sejam executadas por várias horas ou vários dias.  

### <a name="conditional-access-app-control-protection"></a>Proteção do Controle de Aplicativo de Acesso Condicional

O Controle de Aplicativos de Acesso Condicional do Microsoft Cloud App Security usa a arquitetura de proxy reverso para fornecer a você as ferramentas necessárias para proporcionar visibilidade em tempo real e controle sobre o acesso ao seu ambiente de nuvem e sobre as atividades executadas nele. Com o Controle de Aplicativo de Acesso Condicional, é possível proteger a organização:

- Evitar o vazamento de dados bloqueando os downloads antes que eles ocorram
- Definir as regras que forçam os dados armazenados em e baixados da nuvem a serem protegidos com criptografia
- Obter visibilidade para pontos de extremidade desprotegidos para que você possa monitorar o que está sendo feito em dispositivos não gerenciados
- Controlar o acesso por meio de redes não corporativas ou endereços IP arriscados

### <a name="policy-control"></a>Controle de política  

Você pode usar políticas para definir o comportamento dos usuários na nuvem. Use políticas para detectar comportamento arriscado, violações ou pontos de dados suspeitos e atividades em seu ambiente de nuvem. Se necessário, você pode usar políticas para integrar os processos de correção para atingir a mitigação de risco completa. Os tipos de políticas se correlacionam com os diferentes tipos de informações que você pode reunir sobre seu ambiente de nuvem e os tipos de medidas de correção que você pode tomar.  

## <a name="related-videos"></a>Vídeos Relacionados

- [Participar da comunidade de segurança](https://channel9.msdn.com/Shows/Microsoft-Security/Join-the-Security-Community)

## <a name="next-steps"></a>Próximas etapas  

Saiba mais sobre as noções básicas em [Introdução ao Cloud App Security](getting-started-with-cloud-app-security.md).    

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/)   
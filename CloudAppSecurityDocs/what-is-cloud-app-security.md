---
title: "O que é o Cloud App Security | Microsoft Docs"
description: "Este tópico fornece informações sobre o Cloud App Security e como ele funciona."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: d46756b1-7dd8-4190-9799-3a97688f1266
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed4ea71b24767d3602d40894d1cbac7447bcd8a2
ms.openlocfilehash: d2ece0e3a47dc0febbb1314c496045abdc5c8d61


---
# <a name="what-is-cloud-app-security"></a>O que é o Cloud App Security
 
> [!NOTE] 
> Para obter informações sobre o Gerenciamento de Segurança Avançado, os recursos do Cloud App Security no Office 365, consulte a Introdução ao [Gerenciamento de Segurança Avançado](https://support.office.com/article/Get-started-with-Advanced-Management-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a). 
 
Embora mudar para a nuvem tenha aumentado a flexibilidade para os funcionários e reduzido os custos de TI, isso também introduziu novos desafios e complexidade para manter sua organização segura. Para obter todos os benefícios dos aplicativos de nuvem, as equipes de TI devem encontrar o equilíbrio correto de permitir o acesso ao mesmo tempo que mantêm o controle para proteger dados críticos.  
  
O Cloud App Security é um componente crítico da pilha do Microsoft Cloud Security. É uma solução abrangente que ajuda as empresas a aproveitar ao máximo a promessa de aplicativos em nuvem enquanto mantém o controle com visibilidade das atividades aprimorada. Também aumenta a proteção de dados críticos em aplicativos de nuvem. Com ferramentas para ajudar a descobrir a TI Invisível, avaliar os riscos, impor políticas, investigar atividades e parar ameaças, as organizações podem migrar para a nuvem com segurança enquanto mantêm o controle de dados críticos.  
  
## <a name="the-cloud-app-security-framework"></a>A estrutura do Cloud App Security  

|       |   |   |
|-------|---|:---|
|![Descobrir](./media/discovery-icon.png)|Descobrir|Descobrir TI sombra com o Cloud App Security. Obtenha visibilidade descobrindo aplicativos, atividades, usuários, dados e arquivos em seu ambiente de nuvem, bem como outros aplicativos de terceiros que estão conectados à sua nuvem.|
|![Investigar](./media/investigate-icon.png)|Investigar|Investigue seus aplicativos de nuvem usando ferramentas de análise forense de nuvem para se aprofundar em aplicativos arriscados, usuários específicos e arquivos em sua rede, bem como descobrindo padrões nos dados coletados da nuvem e geração de relatórios para monitorar sua nuvem.|
|![Control](./media/protect-icon.png)|Control|Reduza o risco definindo políticas e alertas para obter o máximo controle sobre o tráfego da nuvem na rede. Use o Cloud App Security para migrar seus usuários para alternativas de aplicativo de nuvem seguras e sancionadas.|
|![Proteger](./media/protect-icon.png)|Proteger|Use o Cloud App Security para sancionar/cancelar a sanção de aplicativos, impor DPL (prevenção de perda de dados), controlar permissões e compartilhamento e gerar relatórios e alertas personalizados.|


## <a name="architecture"></a>Arquitetura  

O Cloud App Security permite a integração de visibilidade com sua nuvem das seguintes maneiras:  
  
-   Visibilidade usando o Cloud Discovery para mapear e identificar seu ambiente de nuvem e os aplicativos de nuvem que você tem em uso.  
-   Capacidade de sancionar e cancelar a sanção de aplicativos na sua nuvem.  
-   Visibilidade e governança de aplicativos conectados através dos nossos conectores de aplicativos fáceis de implantar que utilizam as APIs do provedor.  
-   Controle contínuo permitindo que você defina e ajuste continuamente as políticas.  
  
![](./media/architecture.png)  
  
> [!NOTE]  
>  Quando o Cloud App Security executa a inspeção do conteúdo, a privacidade de dados é imposta. Seus dados não são armazenados no banco de dados do Cloud App Security, apenas os metadados dos registros de arquivo e as violações que foram identificadas. Consulte nossa [política de privacidade](http://go.microsoft.com/fwlink/?LinkId=512132) e a [Central de Confiabilidade da Microsoft](https://www.microsoft.com/TrustCenter/Privacy/You-are-in-control-of-your-data) para obter mais informações sobre a retenção de dados.
O Cloud App Security mantém os dados da seguinte maneira:
>- Log de atividades: 180 dias
>- Dados de descoberta: 90 dias
>- Alertas: ilimitado 

Após os dados serem coletados dessas fontes, o Cloud App Security executa uma análise sofisticada neles, alertando você imediatamente quanto a atividades anômalas e fornecendo uma visibilidade profunda. Você pode configurar uma política no Cloud App Security e usá-la para proteger tudo em seu ambiente de nuvem.  
  
###  <a name="how-cloud-discovery-works"></a>Como o Cloud Discovery funciona  

O Cloud Discovery usa os logs de tráfego para descobrir e analisar dinamicamente quais aplicativos de nuvem estão em uso na sua organização.  
  
Você pode criar um relatório de instantâneo do uso de nuvem da sua organização, carregando manualmente os arquivos de log de seus firewalls ou proxies para análise ou pode configurar relatórios contínuos usando os coletores de logs do Cloud App Security para encaminhar os logs periodicamente.  

Para obter mais informações sobre o Cloud Discovery, consulte [Configurar o Cloud Discovery](set-up-cloud-discovery.md).
  
### <a name="how-sanctioning-and-unsanctioning-an-app-works"></a>Como funciona a sanção e o cancelamento de sanção de um aplicativo  

O Cloud App Security permite que você sancione/cancele a sanção de aplicativos em sua organização usando nosso **Catálogo de aplicativos de nuvem**.  
  
A equipe de analistas da Microsoft tem um catálogo extenso e em constante expansão de mais de 13.000 aplicativos de nuvem que são classificados e pontuados com base nos padrões da indústria. O **Catálogo de aplicativos de nuvem** classifica o risco para seus aplicativos de nuvem com base em certificações regulatórias, padrões da indústria e práticas recomendadas. Você pode então personalizar as pontuações e os pesos de diversos parâmetros de acordo com as necessidades da sua organização. Com base nessas pontuações, o Cloud App Security permite que você saiba quão arriscado o aplicativo é de acordo com mais de 50 fatores de risco que podem afetar seu ambiente.  
  
### <a name="how-app-connectors-work"></a>Como funcionam os conectores de aplicativos  
Os conectores de aplicativos utilizam as APIs fornecidas por vários provedores de aplicativos de nuvem para permitir que a nuvem do Cloud App Security se integre a outros aplicativos de nuvem e estenda o controle e a proteção. Isso permite que o Cloud App Security obtenha informações diretamente dos aplicativos de nuvem para análise.  
Para conectar a um aplicativo e estender a proteção, o administrador do aplicativo autoriza o Cloud App Security a acessar o aplicativo e consultá-lo quanto a logs de atividades, dados de verificação e conteúdo de nuvem e contas. O Cloud App Security pode impor políticas, detectar ameaças e fornecer ações de governança para resolver problemas.  
  
O Cloud App Security aproveita as APIs fornecidas pelo provedor de nuvem, cada aplicativo tem sua própria estrutura e limitações de API. O Cloud App Security trabalha com os provedores de aplicativo para otimizar o uso das APIs e para garantir o melhor desempenho. Considerando as diferentes limitações que os aplicativos impõem sobre as APIs (como as limitações, limites de API, janelas de API de mudança de tempo dinâmicas etc.), os mecanismos do Cloud App Security aproveitam a capacidade permitida. Algumas operações, como a verificação de todos os arquivos no locatário, exigem uma grande quantidade de APIs e, portanto, são distribuídas por um período mais longo. Espere algumas que algumas políticas sejam executadas por várias horas ou vários dias.  
  
### <a name="how-policy-control-works"></a>Como o controle de política funciona  

As políticas permitem que você defina a maneira como deseja que os usuários se comportem na nuvem. Elas permitem que você detecte comportamento de risco, violações ou pontos de dados e atividades suspeitos no seu ambiente de nuvem e, se necessário, integre processos de correção para obter a mitigação de risco completa. Existem vários tipos de políticas que se correlacionam com diferentes tipos de informações que você deseja reunir sobre seu ambiente de nuvem e os tipos de ações de correção que deseja executar.  
  
## <a name="see-also"></a>Veja também  

[Introdução ao Cloud App Security](getting-started-with-cloud-app-security.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Oct16_HO4-->



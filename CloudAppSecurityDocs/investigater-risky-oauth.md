---
title: Investigar aplicativos de OAuth arriscados - Cloud App Security | Microsoft Docs
description: Esse artigo fornece informações sobre como investigar os aplicativos de OAuth arriscados no Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: barbkess
ms.date: 3/17/2019
ms.topic: tutorial
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 4118681e-362f-4b10-aa08-39691aa7800a
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 77b33d524e3a88d49c4dd2bcd71bc31c0fa26250
ms.sourcegitcommit: 57bad4dc9b28326c93ee480d308d52ea23c42089
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2019
ms.locfileid: "58163646"
---
# <a name="investigate-risky-oauth-apps"></a>Investigar aplicativos de OAuth arriscados

*Aplica-se a: Microsoft Cloud App Security*

O OAuth é um padrão aberto para autenticação e autorização baseada em token. O OAuth permite que as informações da conta do usuário sejam usadas por serviços de terceiros, sem expor a senha do usuário. O OAuth atua como um intermediário em nome do usuário, fornecendo o serviço com um token de acesso que autoriza o compartilhamento de informações de conta específicas.

Muitos aplicativos de terceiros, que podem ser instalados por usuários corporativos da sua organização, solicitam permissão para acessar dados e informações de usuário e entrar, em nome do usuário, em outros aplicativos de nuvem. Quando os usuários instalam esses aplicativos, eles geralmente clicam em **aceitar** sem examinar atentamente os detalhes na solicitação, incluindo a concessão de permissões para o aplicativo.

Aceitar permissões de aplicativos de terceiros é um risco de segurança potencial para sua organização, portanto, o Microsoft Cloud App Security fornece a capacidade de investigar e monitorar as permissões de aplicativo concedidas pelos usuários. Esse artigo destina-se a ajudar você a investigar os aplicativos de OAuth em sua organização, e se concentrar nos aplicativos com maior probabilidade de levantar suspeitas. 

A nossa abordagem recomendada é investigar os aplicativos utilizando as habilidades e informações fornecidas no portal do Cloud App Security para filtrar aplicações com uma baixa probabilidade de ser arriscado e focar nos aplicativos suspeitos. 

## <a name="how-to-investigate"></a>Como investigar 

1.  De todas as consultas de aplicativos OAuth conectados usando os filtros no portal. Os filtros e as consultas recomendados são: 
    1. O nível de permissão alto e uso da comunidade não é comum. Usar esse filtro ajudaria você a se concentrar no aplicativo com um potencial de alto risco, em que o usuário provavelmente não reconheceu o risco. 
    2. Permissões arriscadas específicas relacionadas a um tipo específico de aplicativos (por exemplo, aplicativos com acesso completo a todas as caixas de correio). Usar esse filtro ajudaria você a investigar em um contexto específico e, com isso, os aplicativos parecem legítimos, mas contêm permissões irrelevantes. Esses aplicativos são mais propensos a serem maliciosos. 
    3. Aplicativos autorizados por usuários externos. Usar esse filtro ajudaria você a encontrar aplicativos que talvez não estivessem alinhados com os padrões de segurança da sua empresa. 
2.  Concentre-se nos seguintes aplicativos, que podem levantar suspeitas: 
    1. Aplicativos com um número baixo de "Autorizado por". Concentrar-se nesses aplicativos pode ajudá-lo a encontrar aplicativos maliciosos que foram autorizados por um usuário comprometido. 
    2. Aplicativos com permissões que não correspondem ao objetivo do aplicativo (por exemplo, um aplicativo de relógio com acesso total a todas as caixas de correio). Concentrar-se nesses aplicativos pode ajudá-lo a encontrar aplicativos que pareçam legítimos, mas que sejam realmente mal-intencionados. 
    3. Aplicativos com nome, editor ou site suspeito. Concentrar-se nesses aplicativos pode ajudar você a encontrar rapidamente aplicativos suspeitos. 
    4. Aplicativos com "Última autorização" antiga. Concentrar-se nesses aplicativos pode ajudar você a encontrar aplicativos que não são mais necessários. 
3. Use o link de atividades relacionadas e exiba na página de log de atividades as que foram realizadas pelo aplicativo. Observe que isso gera automaticamente um filtro para atividades em que o usuário é igual ao nome do aplicativo. No entanto, alguns aplicativos podem executar atividades como um dos usuários. Esses eventos estariam disponíveis no log de atividades, mas poderiam ser filtrados. 
4. Se um aplicativo parecer suspeito, é recomendável verificar o nome e o editor do aplicativo nas diferentes lojas de aplicativos. Concentre-se nos seguintes aplicativos, que podem levantar suspeitas: 
    1. Aplicativo com um número baixo de downloads.
    2. Aplicativo com uma pontuação baixa ou comentários incorretos.
    3. Aplicativo com um publicador ou website suspeito.
    4. Aplicativo com uma data antiga de última atualização, pode indicar que não há mais suporte para o aplicativo. 
    5. Os aplicativos que não atendem às suas permissões podem indicar que esse aplicativo é mal-intencionado. 
5. Se o aplicativo ainda for suspeito, você poderá pesquisar online o editor e a URL do nome do aplicativo. 

## <a name="example"></a>Exemplo 

Escolha a opção "Aplicativos OAuth" no ícone de investigação
 
Use as opções de filtro para filtrar os aplicativos (equivalente à etapa 1)
 

Investigue um aplicativo suspeito usando as informações disponíveis no portal (equivalente à etapa 2)
 

Use o log de atividades (equivalente à etapa 3)
 

Referências https://searchmicroservices.techtarget.com/definition/OAuth https://docs.microsoft.com/cloud-app-security/manage-app-permissions


 
## <a name="next-steps"></a>Próximas etapas
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md) 

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/) 
 

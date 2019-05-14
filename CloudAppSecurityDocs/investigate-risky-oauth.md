---
title: Investigar aplicativos de OAuth arriscados - Cloud App Security | Microsoft Docs
description: Esse artigo fornece informações sobre como investigar os aplicativos de OAuth arriscados no Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: rkarlin
ms.date: 04/08/2019
ms.topic: tutorial
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 4118681e-362f-4b10-aa08-39691aa7800a
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: d2972f43725cdd6e9ea70ce305f41c11a621960b
ms.sourcegitcommit: 9f0c562322394a3dfac7f1d84286e673276a28b1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65568311"
---
# <a name="tutorial-investigate-risky-oauth-apps"></a>Tutorial: Investigar aplicativos de OAuth arriscados

*Aplica-se a: Microsoft Cloud App Security*

O OAuth é um padrão aberto para autenticação e autorização baseada em token. O OAuth permite que as informações da conta do usuário sejam usadas por serviços de terceiros, sem expor a senha do usuário. O OAuth atua como um intermediário em nome do usuário, fornecendo o serviço com um token de acesso que autoriza o compartilhamento de informações de conta específicas. 

Por exemplo, um aplicativo que analisa o calendário do usuário e fornece conselhos sobre produtividade precisa acessar o calendário do usuário. Em vez de fornecer as credenciais do usuário, o OAuth permite que o aplicativo obtenha acesso aos dados somente com base em um token gerado quando o usuário fornece consentimento para uma página, o que pode ser visto na imagem abaixo.

 ![Permissão do aplicativo OAuth](./media/oauth-permission.png) 

Muitos aplicativos de terceiros, que podem ser instalados por usuários corporativos da sua organização, solicitam permissão para acessar dados e informações de usuário e entrar, em nome do usuário, em outros aplicativos de nuvem. Quando os usuários instalam esses aplicativos, eles geralmente clicam em **aceitar** sem examinar atentamente os detalhes na solicitação, incluindo a concessão de permissões para o aplicativo. Aceitar permissões de aplicativo de terceiros é um risco potencial para a segurança da sua organização.

Por exemplo, a seguinte página de consentimento do aplicativo OAuth pode parecer legítima para o usuário médio, no entanto, o "Gerenciador de APIs do Google" não precisa solicitar permissões para o Google em si. Portanto, isso indica que o aplicativo pode ser uma tentativa de phishing sem relação alguma com o Google.

 ![Phishing OAuth](./media/oauth-phishing.png) 

Como administrador de segurança, você precisa de visibilidade e controle sobre os aplicativos em seu ambiente, o que inclui as permissões que eles têm. Você precisa ter a capacidade de evitar o uso de aplicativos que exijam permissões para recursos que você deseja revogar. Portanto, o Microsoft Cloud App Security fornece a capacidade de investigar e monitorar as permissões de aplicativos que seus usuários concederam. Esse artigo destina-se a ajudar você a investigar os aplicativos de OAuth em sua organização, e se concentrar nos aplicativos com maior probabilidade de levantar suspeitas. 

A nossa abordagem recomendada é investigar os aplicativos utilizando as habilidades e informações fornecidas no portal do Cloud App Security para filtrar aplicações com uma baixa probabilidade de ser arriscado e focar nos aplicativos suspeitos. 

## <a name="how-to-detect-risky-oauth-apps"></a>Como detectar aplicativos com risco de OAuth

É possível detectar um aplicativo com risco de OAuth usando: 

- **Alertas**: reagir a um alerta disparado por uma política existente. 
- **Buscar**: procure um aplicativo com risco entre todos os aplicativos disponíveis, sem suspeita concreta do risco. 


### <a name="detect-risky-apps-using-alerts"></a>Detectar aplicativos com risco usando alertas

Você pode definir políticas para enviar automaticamente notificações quando um aplicativo OAuth apresenta determinados critérios. Por exemplo, você pode definir uma política para notificá-lo automaticamente quando for detectado um aplicativo que exija permissões altas e que tenha sido autorizado por mais de 50 usuários. Para obter mais detalhes sobre como criar políticas de OAuth, confira as [Políticas de aplicativo OAuth](app-permission-policy.md).

### <a name="detect-risky-apps-by-hunting"></a>Detectar aplicativos com riscos pela busca

1.  No portal, acesse **Investigar** e, em seguida **Aplicativos OAuth**. Use os filtros e as consultas para analisar o que está acontecendo em seu ambiente:

    - Defina o filtro **Nível de permissão** em gravidade alta e **Uso da comunidade** em não é comum. Usando esse filtro, você pode se concentrar em aplicativos que são potencialmente muito arriscados e que talvez os usuários tenham subestimado o risco.
    - Em **Permissões**, selecione todas as opções que sejam particularmente arriscadas em um contexto específico. Por exemplo, você pode selecionar todos os filtros que fornecem permissão de acesso ao email, como **Acesso completo a todas as caixas de correio** e, em seguida, examinar a lista de aplicativos para se certificar de que todos eles realmente precisam de acesso relacionado à caixa de correio. Isso pode ajudá-lo a investigar em um contexto específico e encontrar aplicativos que parecem legítimos, mas com permissões desnecessárias. É provável que esses aplicativos sejam mais arriscados. 
    
      ![Phishing OAuth](./media/oauth-filters.png) 
 
    - Selecione a consulta salva em **Aplicativos autorizados por usuários externos**. Ao usar esse filtro, você poderá encontrar aplicativos que talvez não estejam alinhados com os padrões de segurança da sua empresa.
2.  Depois de analisar seus aplicativos, você poderá se concentrar nos aplicativos nas consultas que parecem legítimos, mas que na verdade podem oferecer riscos. Use os filtros para encontrá-los:
    - Filtre os aplicativos que estão **Autorizados por um pequeno número de usuários**. Se você se concentrar nesses aplicativos, poderá procurar por aplicativos arriscados que foram autorizados por um usuário comprometido.
    - Os aplicativos com permissões que não correspondem ao objetivo do aplicativo, por exemplo, um aplicativo de relógio com acesso total a todas as caixas de correio.
3. Clique em cada aplicativo para abrir a gaveta de aplicativos e verifique se o aplicativo tem um nome, editor ou site suspeitos.
1. Examine a lista de aplicativos e aplicativos de destino cuja data em **Última autorização** não seja recente. Pode ser que esses aplicativos não sejam mais necessários. 

   ![Gaveta de aplicativo OAuth](./media/oauth-drawer.png) 


## <a name="how-to-investigate"></a>Como investigar

Depois de determinar que um aplicativo é suspeito e que você quer investigá-lo, recomendamos os princípios-chave a seguir para garantir uma investigação eficiente: 

- Quanto mais comum e usado for um aplicativo, tanto pela sua organização ou online, maior a probabilidade de que ele seja seguro.
- Um aplicativo deve exigir apenas as permissões relacionadas à finalidade dele. Se não for o caso, o aplicativo pode ser arriscado. 
- Os aplicativos que exigem mais privilégios ou consentimento do administrador são os mais prováveis de oferecer riscos. 


1. Clique no aplicativo para abrir a gaveta de aplicativo e clique no link em **Atividades relacionadas**. A página do Log de atividades filtrada para as atividades executadas pelo aplicativo será aberta. Lembre-se de que alguns aplicativos realizam atividades que foram registradas como executadas por um usuário. Essas atividades são filtradas automaticamente e excluídas dos resultados no Log de atividades. Para uma investigação adicional usando o log de atividades, confira [Log de atividades](activity-filters.md). 
4. Se um aplicativo parecer suspeito, recomendamos investigar o nome e o editor do aplicativo nas diferentes lojas de aplicativos. Concentre-se nos seguintes aplicativos, que podem levantar suspeitas: 
    - Aplicativos com um número baixo de downloads.
    - Aplicativos com uma classificação ou pontuação baixas ou comentários negativos.
    - Aplicativos com um editor ou website suspeito.
    - Aplicativos cuja última atualização não seja recente. Isso pode indicar um aplicativo que não tem mais suporte. 
    - Aplicativos com permissões irrelevantes. Isso pode indicar que um aplicativo é arriscado. 
5. Se o aplicativo ainda for suspeito, você poderá pesquisar online o editor e a URL do nome do aplicativo. 

## <a name="how-to-remediate"></a>Como corrigir 

Depois de determinar que um aplicativo OAuth é arriscado, o Cloud App Security fornece as seguintes opções de correção: 

- **Correção manual**: Você pode facilmente [vetar e revogar um aplicativo na página de aplicativos do OAuth](manage-app-permissions.md#ban-or-approve-an-app)

- **Correção automática**: Você pode criar uma política que [revogue automaticamente um aplicativo ou um usuário específico de um aplicativo](app-permission-policy.md).


 
## <a name="next-steps"></a>Próximas etapas
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md) 

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/) 
 

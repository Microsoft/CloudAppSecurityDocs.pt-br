---
title: Proteger em tempo real qualquer aplicativo usado em sua organização
description: Este tutorial fornece instruções para usar controles de acesso e de sessão para monitorar e controlar o acesso a aplicativos e seus dados.
author: shsagir
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: tutorial
ms.date: 01/01/2020
ms.collection: M365-security-compliance
ms.openlocfilehash: fec6182d004b934f564291e4ca9f4fe06aa8d723
ms.sourcegitcommit: 0b929f7c8feed7dfb40d5294179fd5c6fc079614
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/21/2020
ms.locfileid: "75667556"
---
# <a name="tutorial-protect-any-apps-in-use-in-your-organization-in-real-time"></a>Tutorial: Proteger em tempo real qualquer aplicativo usado em sua organização

*Aplica-se a: Microsoft Cloud App Security*

Os aplicativos que você aprova para uso dos funcionários geralmente armazenam alguns dos seus dados e segredos corporativos mais confidenciais. No local de trabalho moderno, os usuários acessam esses aplicativos em muitas situações arriscadas. Esses usuários podem ser parceiros da sua organização dos quais você tem pouca visibilidade ou funcionários que usam dispositivos não gerenciados ou provenientes de endereços IP públicos. Devido à ampla gama de riscos nesse cenário, é necessário empregar uma estratégia de confiança zero. Muitas vezes, não é suficiente saber sobre violações e perda de dados nesses aplicativos após o fato; portanto, muitos cenários de ameaça cibernética e de proteção de informações devem ser resolvidos ou impedidos em tempo real.

Este tutorial fornece instruções para usar controles de acesso e de sessão para monitorar e controlar o acesso a aplicativos e seus dados. O gerenciamento adaptável do acesso aos seus dados e a mitigação de ameaças permitem que Cloud App Security proteja seus ativos mais confidenciais. Abordaremos especificamente os seguintes cenários:

> [!div class="checklist"]
>
> * Monitorar as atividades do usuário em busca de anomalias
> * Proteger seus dados em vazamentos
> * Impedir que dados desprotegidos sejam carregados em seus aplicativos

## <a name="how-to-protect-your-organization-from-any-app-in-real-time"></a>Como proteger qualquer aplicativo de sua organização em tempo real

Use este processo para distribuir controles em tempo real em sua organização.

### <a name="phase-1-monitor-user-activities-for-anomalies"></a>Fase 1: Monitorar as atividades do usuário em busca de anomalias

1. **Implantar seus aplicativos**: comece implantando os aplicativos importantes que sua organização usa. A implantação é simplificada por nossa integração nativa com o acesso condicional do Azure AD (Azure Active Directory). Você pode implantar aplicativos usando as seguintes etapas:

    * Para começar, [implante aplicativos em destaque](proxy-intro-aad.md) pelo Cloud App Security para trabalhar imediatamente. Confira uma lista dos aplicativos em destaque em [Aplicativos e clientes com suporte](proxy-intro-aad.md#supported-apps-and-clients).

    * Em seguida, para aplicativos que não estão em destaque no Cloud App Security, use o processo a seguir para [integrar e implantar qualquer aplicativo](proxy-deployment-any-app.md).

    Depois que os aplicativos estiverem implantados, serão monitorados em tempo real, fornecendo informações imediatas sobre atividades e informações relacionadas. Você pode usar essas informações para identificar algum comportamento anormal.

1. **Monitorar e investigar**: no Cloud App Security, use o [Log de atividades](activity-filters.md) para monitorar e caracterizar o uso do aplicativo em seu ambiente e para entender seus riscos. Você pode restringir o escopo das atividades listadas usando [pesquisa, filtros e consultas](activity-filters-queries.md) para identificar rapidamente as atividades arriscadas.

### <a name="phase-2-protect-your-data-when-its-exfiltrated"></a>Fase 2: Proteger seus dados em vazamentos

Uma das principais preocupações de muitas organizações é como evitar o vazamento de dados antes que ocorra. Dois dos maiores riscos são os dispositivos não gerenciados (que podem não estar protegidos com um PIN ou podem conter aplicativos mal-intencionados) e usuários convidados sob os quais o departamento de TI tem pouca visibilidade e controle.

Agora que seus aplicativos estão implantados, você pode configurar facilmente as políticas para atenuar esses dois riscos aproveitando nossas integrações nativas com o Microsoft Intune para gerenciamento de dispositivos, com o Azure AD em grupos de usuários e com a proteção de informações do Azure para garantir a proteção de dados.

* **Mitigar dispositivos não gerenciados**: crie uma [política de sessão para rotular](session-policy-aad.md#create-a-cloud-app-security-session-policy) e proteger arquivos altamente confidenciais destinados somente aos usuários de sua organização.
* **Mitigar usuários convidados**: crie uma [política de sessão para aplicar permissões personalizadas](session-policy-aad.md#protect-download) a qualquer arquivo baixado por usuários convidados. Por exemplo, você pode definir permissões para que os usuários convidados possam acessar apenas um arquivo protegido.

### <a name="phase-3-prevent-unprotected-data-from-being-uploaded-to-your-apps"></a>Fase 3: Impedir que dados desprotegidos sejam carregados em seus aplicativos

Além de impedir o vazamento de dados, geralmente as organizações querem garantir que os dados infiltrados em aplicativos de nuvem também estejam seguros. Um caso de uso comum é quando um usuário tenta carregar arquivos que não estão rotulados corretamente.

Para qualquer um dos aplicativos que você configurou acima, você pode configurar uma política de sessão para impedir o carregamento de arquivos que não estejam rotulados corretamente, da seguinte maneira:

1. Crie uma política de sessão para [bloquear carregamentos de arquivos rotulados incorretamente](session-policy-aad.md#protect-upload).

1. Configure uma política para exibir uma [mensagem de bloqueio com instruções sobre como corrigir o rótulo e tentar novamente](session-policy-aad.md#educate-protect).

Proteger os carregamentos de arquivos dessa maneira garante que os dados salvos na nuvem tenham as permissões de acesso corretas aplicadas. Caso um arquivo seja compartilhado ou perdido, ele só poderá ser acessado por usuários autorizados.

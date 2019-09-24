---
title: Implantar o Controle de Aplicativos de Acesso Condicional do Cloud App Security em aplicativos do Azure AD
description: Este artigo fornece informações sobre como implantar os recursos de proxy reverso do Controle de Aplicativos de Acesso Condicional do Microsoft Cloud App Security para aplicativos do Azure AD.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 9/23/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: a1a8b0e4fa1cb038204849df679581c909d1f678
ms.sourcegitcommit: 37e7568ae5b78fb52bc7bd66261a2d2fbf50c1dd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71185108"
---
# <a name="deploy-conditional-access-app-control-for-featured-apps"></a>Implantar o Controle de Aplicativos de Acesso Condicional para aplicativos em destaque

*Aplica-se a: Microsoft Cloud App Security*

>[!div class="step-by-step"]
[« Anterior: Introdução ao Controle de Aplicativos de Acesso Condicional](proxy-intro-aad.md)<br>
[Próximo: Integração e implantação de Controle de Aplicativos de Acesso Condicional para qualquer aplicativo»](proxy-deployment-any-app.md)

Os controles de sessão no Microsoft Cloud App Security funcionam com os aplicativos em destaque. Para obter uma lista de aplicativos que são apresentados por Cloud App Security para trabalhar prontos para uso, consulte [proteger aplicativos com Microsoft Cloud App Security controle de aplicativos de acesso condicional](proxy-intro-aad.md#featured-apps).

## <a name="prerequisites"></a>Pré-requisitos

Para implantar o Controle de Aplicativos de Acesso Condicional nos aplicativos do Azure AD, você precisa de uma [licença do Azure AD Premium P1](https://docs.microsoft.com/azure/active-directory/license-users-groups) válida, bem como uma licença do Cloud App Security.

## <a name="to-deploy-featured-apps"></a>Para implantar aplicativos em destaque

Siga estas etapas para configurar aplicativos em destaque para serem controlados pelo Microsoft Cloud App Security Controle de Aplicativos de Acesso Condicional.

**Etapa 1: [Vá para o portal do AD do Azure e crie uma política de acesso condicional para os aplicativos e encaminhe a sessão para Cloud App Security](#add-azure-ad)**

**Etapa 2: [Entrar em cada aplicativo usando um escopo de usuário para a política](#sign-in-scoped)**

**Etapa 3: [Verifique se os aplicativos estão configurados para usar controles de acesso e sessão](#portal)**

**Etapa 4: [Testar a implantação](#test)**

## Etapa 1: Crie uma política de teste de acesso condicional do Azure AD <a name="add-azure-ad"></a>

1. Em Azure Active Directory, em **segurança**, clique em **acesso condicional**.

1. Clique em **Nova política** e crie uma política.

1. Na política TESTE, em **Usuários**, atribua um usuário de teste ou um usuário que possa ser usado para um logon e uma verificação iniciais.

1. Na política de TESTE, em **Aplicativo de nuvem**, atribua os aplicativos que você deseja controlar com o Controle de Aplicativo de Acesso Condicional.

1. Em **Sessão**, defina a política para usar uma das políticas internas, **Somente monitorar** ou **Bloquear downloads**. Ou selecione **Usar política personalizada** para definir uma política avançada no portal do Cloud App Security.

1. Adicione **Atribuições de condição** ou **Controles de concessão** aplicáveis (opcional).

   ![Acesso condicional do Azure AD](./media/azure-ad-caac-policy.png)

1. Clique em **habilitar** e **salvar**.

## Etapa 2: Entrar em cada aplicativo usando um escopo de usuário para a política<a name="sign-in-scoped"></a>

> [!NOTE]
> Antes de continuar, certifique-se de primeiro sair das sessões existentes.

Depois de criar a política, entre em cada aplicativo configurado nessa política. Entre usando um usuário configurado na política.

Cloud App Security sincronizará os detalhes da política com seus servidores para cada novo aplicativo no qual você entrar. Isso poderá levar até um minuto.

## Etapa 3: Verifique se os aplicativos estão configurados para usar controles de acesso e sessão<a name="portal"></a>

As instruções acima ajudaram a criar uma política interna do Cloud App Security para aplicativos em destaque diretamente no Azure AD. Nesta etapa, verifique se os controles de acesso e sessão estão configurados para esses aplicativos.

1. No portal de Cloud App Security, clique(./media/settings-icon.png "no ícone configurações")engrenagem ![ícone]configurações e, em seguida, selecione **controle de aplicativos de acesso condicional**.

1. Na tabela de aplicativos Controle de Aplicativos de Acesso Condicional, examine a coluna **controles disponíveis** e verifique se o controle de **acesso** e a **sessão** são exibidos para seus aplicativos.

   > [!NOTE]
   > Se o controle de sessão não aparecer para um aplicativo, ele ainda não estará disponível para esse aplicativo específico. Você pode adicioná-lo imediatamente como um [aplicativo personalizado](proxy-deployment-any-app.md)ou pode abrir uma solicitação para adicioná-lo como um aplicativo em destaque clicando em **solicitar controle de sessão**.
    >
    >![Solicitação de Controle de Aplicativos de Acesso Condicional](media/caac-request.png)

## Etapa 4: Testar a implantação<a name="test"></a>

1. Primeiro saia das sessões existentes. Em seguida, tente entrar em cada aplicativo que foi implantado com êxito. Entre usando um usuário que corresponda à política configurada no Azure AD.

1. No portal do Cloud App Security, em **Investigar**, selecione **Log de atividades** e garanta que as atividades de logon sejam capturadas para cada aplicativo.

1. Você pode filtrar clicando em **Avançado** e, em seguida, usando a filtragem **Origem é igual a Controle de acesso**.

    ![Filtre usando o acesso condicional do Azure AD](./media/sso-logon.png)

1. É recomendável que você entre em aplicativos móveis e da área de trabalho em dispositivos gerenciados e não gerenciados. Isso serve para garantir que as atividades sejam capturadas corretamente no log de atividades.<br>
Para verificar se a atividade é capturada corretamente, clique em um log de logon único na atividade para abrir a gaveta de atividades. Verifique se a **Marca de agente do usuário** reflete corretamente se o dispositivo é um cliente nativo (o que significa um aplicativo móvel ou da área de trabalho) ou um dispositivo gerenciado (em conformidade, ingressado no domínio ou certificado do cliente válido).

> [!NOTE]
> Depois de implantado, você não pode remover um aplicativo da página de Controle de Aplicativos de Acesso Condicional. Desde que você não defina uma política de acesso ou sessão no aplicativo, o Controle de Aplicativos de Acesso Condicional não alterará comportamentos para o aplicativo.

>[!div class="step-by-step"]
[« Anterior: Introdução ao Controle de Aplicativos de Acesso Condicional](proxy-intro-aad.md)<br>[Próximo: Integração e implantação de Controle de Aplicativos de Acesso Condicional para qualquer aplicativo»](proxy-deployment-any-app.md)

## <a name="next-steps"></a>Próximas etapas

[Trabalhando com Cloud App Security Controle de Aplicativos de Acesso Condicional](proxy-intro-aad.md)

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/)

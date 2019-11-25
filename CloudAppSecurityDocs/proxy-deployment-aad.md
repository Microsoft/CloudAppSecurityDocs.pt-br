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
ms.openlocfilehash: 14209e0b394571ee0d71784cb4c50683226a7a2e
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2019
ms.locfileid: "74460631"
---
# <a name="deploy-conditional-access-app-control-for-featured-apps"></a>Implantar o Controle de Aplicativos de Acesso Condicional para aplicativos em destaque

*Aplica-se ao: Microsoft Cloud App Security*

>[!div class="step-by-step"]
[« Anterior: Introdução ao Controle de Aplicativo de Acesso Condicional](proxy-intro-aad.md)<br>
[Next: Onboard and deploy Conditional Access App Control for any app »](proxy-deployment-any-app.md)

Session controls in Microsoft Cloud App Security work with the featured apps. For a list of apps that are featured by Cloud App Security to work out-of-the-box, see [Protect apps with Microsoft Cloud App Security Conditional Access App Control](proxy-intro-aad.md#featured-apps).

## <a name="prerequisites"></a>Pré-requisitos

Para implantar o Controle de Aplicativos de Acesso Condicional nos aplicativos do Azure AD, você precisa de uma [licença do Azure AD Premium P1](https://docs.microsoft.com/azure/active-directory/license-users-groups) válida, bem como uma licença do Cloud App Security.

## <a name="to-deploy-featured-apps"></a>To deploy featured apps

Follow these steps to configure featured apps to be controlled by Microsoft Cloud App Security Conditional Access App Control.

**Step 1: [Go to the Azure AD portal and create a conditional access policy for the apps and route the session to Cloud App Security](#add-azure-ad)**

**Step 2: [Sign in to each app using a user scoped to the policy](#sign-in-scoped)**

**Step 3: [Verify the apps are configured to use access and session controls](#portal)**

**Step 4: [Test the deployment](#test)**

## Step 1: Create an Azure AD conditional access test policy <a name="add-azure-ad"></a>

1. In Azure Active Directory, under **Security**, click **Conditional Access**.

1. Clique em **Nova política** e crie uma política.

1. Na política TESTE, em **Usuários**, atribua um usuário de teste ou um usuário que possa ser usado para um logon e uma verificação iniciais.

1. Na política de TESTE, em **Aplicativo de nuvem**, atribua os aplicativos que você deseja controlar com o Controle de Aplicativo de Acesso Condicional.

1. Em **Sessão**, defina a política para usar uma das políticas internas, **Somente monitorar** ou **Bloquear downloads**. Ou selecione **Usar política personalizada** para definir uma política avançada no portal do Cloud App Security.

1. Adicione **Atribuições de condição** ou **Controles de concessão** aplicáveis (opcional).

   ![Acesso condicional do Azure AD](./media/azure-ad-caac-policy.png)

1. Click **Enable** and **Save**.

## Step 2: Sign in to each app using a user scoped to the policy<a name="sign-in-scoped"></a>

> [!NOTE]
> Before proceeding, make sure to first sign out of existing sessions.

Depois de criar a política, entre em cada aplicativo configurado nessa política. Entre usando um usuário configurado na política.

Cloud App Security will sync your policy details to its servers for each new app you sign in to. Isso poderá levar até um minuto.

## Step 3: Verify the apps are configured to use access and session controls<a name="portal"></a>

As instruções acima ajudaram a criar uma política interna do Cloud App Security para aplicativos em destaque diretamente no Azure AD. In this step, verify that the access and session controls are configured for these apps.

1. In the Cloud App Security portal, click the settings cog ![settings icon](./media/settings-icon.png "ícone de configurações"), and then select **Conditional Access App Control**.

1. In the Conditional Access App Control apps table, look at the **Available controls** column and verify that both **Access control** and **Session control** appear for your apps.

   > [!NOTE]
   > If session control doesn't appear for an app, it's not yet available for that specific app. You can either add it immediately as a [custom app](proxy-deployment-any-app.md), or you can open a request to add it as a featured app by clicking **Request session control**.
    >
    >![Solicitação de Controle de Aplicativos de Acesso Condicional](media/caac-request.png)

## Step 4: Test the deployment<a name="test"></a>

1. Primeiro saia das sessões existentes. Em seguida, tente entrar em cada aplicativo que foi implantado com êxito. Entre usando um usuário que corresponda à política configurada no Azure AD.

1. No portal do Cloud App Security, em **Investigar**, selecione **Log de atividades** e garanta que as atividades de logon sejam capturadas para cada aplicativo.

1. Você pode filtrar clicando em **Avançado** e, em seguida, usando a filtragem **Origem é igual a Controle de acesso**.

    ![Filtre usando o acesso condicional do Azure AD](./media/sso-logon.png)

1. É recomendável que você entre em aplicativos móveis e da área de trabalho em dispositivos gerenciados e não gerenciados. Isso serve para garantir que as atividades sejam capturadas corretamente no log de atividades.<br>
Para verificar se a atividade é capturada corretamente, clique em um log de logon único na atividade para abrir a gaveta de atividades. Verifique se a **Marca de agente do usuário** reflete corretamente se o dispositivo é um cliente nativo (o que significa um aplicativo móvel ou da área de trabalho) ou um dispositivo gerenciado (em conformidade, ingressado no domínio ou certificado do cliente válido).

> [!NOTE]
> Depois de implantado, você não pode remover um aplicativo da página de Controle de Aplicativos de Acesso Condicional. Desde que você não defina uma política de acesso ou sessão no aplicativo, o Controle de Aplicativos de Acesso Condicional não alterará comportamentos para o aplicativo.

>[!div class="step-by-step"]
[« Anterior: Introdução ao Controle de Aplicativo de Acesso Condicional](proxy-intro-aad.md)<br>[Next: Onboard and deploy Conditional Access App Control for any app »](proxy-deployment-any-app.md)

## <a name="next-steps"></a>Próximas etapas

[Working with Cloud App Security Conditional Access App Control](proxy-intro-aad.md)

[!INCLUDE [Open support ticket](includes/support.md)]

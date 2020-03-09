---
title: Implantar Cloud App Security Controle de Aplicativos de Acesso Condicional para aplicativos do Azure AD
description: Este artigo fornece informações sobre como implantar o Microsoft Cloud App Security Controle de Aplicativos de Acesso Condicional recursos de proxy reverso para aplicativos do Azure AD.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 9/23/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 0fc3f43aa76f64d1228a6e45d2fdc743a494a8e3
ms.sourcegitcommit: 3f6ef6b97a0953470135d115323a00cf11441ab7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/08/2020
ms.locfileid: "78927791"
---
# <a name="deploy-conditional-access-app-control-for-featured-apps"></a>Implantar o Controle de Aplicativos de Acesso Condicional para aplicativos em destaque

*Aplica-se a: Microsoft Cloud App Security*

Os controles de sessão no Microsoft Cloud App Security funcionam com os aplicativos em destaque. Para obter uma lista de aplicativos que são apresentados por Cloud App Security para trabalhar prontos para uso, consulte [proteger aplicativos com Microsoft Cloud App Security controle de aplicativos de acesso condicional](proxy-intro-aad.md#featured-apps).

## <a name="prerequisites"></a>Prerequisites

Para implantar Controle de Aplicativos de Acesso Condicional para aplicativos do Azure AD, você precisa de uma [licença válida para Azure ad Premium P1](https://docs.microsoft.com/azure/active-directory/license-users-groups) , bem como uma licença de Cloud app Security.

## <a name="to-deploy-featured-apps"></a>Para implantar aplicativos em destaque

Siga estas etapas para configurar aplicativos em destaque para serem controlados pelo Microsoft Cloud App Security Controle de Aplicativos de Acesso Condicional.

**Etapa 1: [vá para o portal do Azure AD e crie uma política de acesso condicional para os aplicativos e encaminhe a sessão para Cloud app Security](#add-azure-ad)**

**Etapa 2: [entrar em cada aplicativo usando um escopo de usuário para a política](#sign-in-scoped)**

**Etapa 3: [verificar se os aplicativos estão configurados para usar controles de acesso e sessão](#portal)**

**Etapa 4: [testar a implantação](#test)**

## Etapa 1: criar uma política de teste de acesso condicional do Azure AD<a name="add-azure-ad"></a>

1. Em Azure Active Directory, em **segurança**, clique em **acesso condicional**.

1. Clique em **nova política** e crie uma nova política.

1. Na política de teste, em **usuários**, atribua um usuário de teste ou usuário que pode ser usado para um logon inicial e uma verificação.

1. Na política de teste, em **aplicativo de nuvem**, atribua os aplicativos que você deseja controlar com controle de aplicativos de acesso condicional.

1. Em **sessão**, defina a política para usar qualquer uma das políticas internas, **monitorar apenas** ou **bloquear downloads**. Ou selecione **usar política personalizada** para definir uma política avançada no portal de Cloud app Security.

1. Adicione quaisquer **atribuições de condição** ou **controles de concessão** aplicáveis (opcional).

    ![Acesso condicional do Azure AD](media/azure-ad-caac-policy.png)

1. Clique em **habilitar** e **salvar**.

## Etapa 2: entrar em cada aplicativo usando um escopo de usuário para a política<a name="sign-in-scoped"></a>

> [!NOTE]
> Antes de continuar, certifique-se de primeiro sair das sessões existentes.

Depois de criar a política, entre em cada aplicativo configurado nessa política. Certifique-se de entrar usando um usuário configurado na política.

Cloud App Security sincronizará os detalhes da política com seus servidores para cada novo aplicativo no qual você entrar. Isso pode levar até um minuto.

## Etapa 3: verificar se os aplicativos estão configurados para usar controles de acesso e sessão<a name="portal"></a>

As instruções acima ajudaram você a criar uma política de Cloud App Security interna para aplicativos em destaque diretamente no Azure AD. Nesta etapa, verifique se os controles de acesso e sessão estão configurados para esses aplicativos.

1. No portal de Cloud App Security, clique no ícone configurações engrenagem ![configurações](media/settings-icon.png "ícone de configurações")e, em seguida, selecione **controle de aplicativos de acesso condicional**.

1. Na tabela de aplicativos Controle de Aplicativos de Acesso Condicional, examine a coluna **controles disponíveis** e verifique se o controle de **acesso** e a **sessão** são exibidos para seus aplicativos.

    > [!NOTE]
    > Se o controle de sessão não aparecer para um aplicativo, ele ainda não estará disponível para esse aplicativo específico. Você pode adicioná-lo imediatamente como um [aplicativo personalizado](proxy-deployment-any-app.md)ou pode abrir uma solicitação para adicioná-lo como um aplicativo em destaque clicando em **solicitar controle de sessão**.
    >
    >![Solicitação de controle de aplicativo de acesso condicional](media/caac-request.png)

## Etapa 4: testar a implantação<a name="test"></a>

1. Primeiro saia de todas as sessões existentes. Em seguida, tente entrar em cada aplicativo que foi implantado com êxito. Entre usando um usuário que corresponda à política configurada no Azure AD.

1. No portal de Cloud App Security, em **investigar**, selecione **log de atividades**e certifique-se de que as atividades de logon sejam capturadas para cada aplicativo.

1. Você pode filtrar clicando em **avançado**e, em seguida, filtrando usando **código-fonte igual ao controle de acesso**.

    ![Filtrar usando o acesso condicional do Azure AD](media/sso-logon.png)

1. É recomendável que você entre em aplicativos móveis e de área de trabalho de dispositivos gerenciados e não gerenciados. Isso é para garantir que as atividades sejam capturadas corretamente no log de atividades.<br />
Para verificar se a atividade foi capturada corretamente, clique em uma atividade fazer logon único para que ela abra a gaveta de atividade. Verifique se a **marca do agente do usuário** reflete corretamente se o dispositivo é um cliente nativo (ou seja, um aplicativo móvel ou de área de trabalho) ou se o dispositivo é um dispositivo gerenciado (em conformidade, ingressado no domínio ou um certificado de cliente válido).

> [!NOTE]
> Depois de implantado, você não pode remover um aplicativo da página Controle de Aplicativos de Acesso Condicional. Desde que você não defina uma sessão ou política de acesso no aplicativo, a Controle de Aplicativos de Acesso Condicional não alterará nenhum comportamento para o aplicativo.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [«ANTERIOR: introdução ao Controle de Aplicativos de Acesso Condicional](proxy-intro-aad.md)

> [!div class="nextstepaction"]
> [Em seguida: integrar e implantar Controle de Aplicativos de Acesso Condicional para qualquer aplicativo»](proxy-deployment-any-app.md)

[!INCLUDE [Open support ticket](includes/support.md)]

---
title: Conectar o GitHub Enterprise Cloud a Cloud App Security
description: Este artigo fornece informações sobre como conectar seu aplicativo de nuvem empresarial do GitHub a Cloud App Security usando o conector de API para visibilidade e controle sobre o uso.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 11/10/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ROBOTS: NOINDEX
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 774fd931210f5e3303b94e5903a724811583e61e
ms.sourcegitcommit: 98f1b892294beb74157cb3452aa5d489e78bbef4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94424513"
---
# <a name="connect-github-enterprise-cloud-to-microsoft-cloud-app-security"></a>Conectar o GitHub Enterprise Cloud a Microsoft Cloud App Security

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Este artigo fornece instruções para conectar Microsoft Cloud App Security à sua organização de nuvem empresarial do GitHub existente usando as APIs do conector de aplicativo. Essa conexão fornece visibilidade e controle sobre o uso de nuvem empresarial do GitHub de sua organização. Para obter mais informações sobre como Cloud App Security protege o GitHub Enterprise Cloud, consulte [proteger o GitHub Enterprise](protect-github.md).

## <a name="prerequisites"></a>Pré-requisitos

- Sua organização deve ter uma licença do GitHub Enterprise Cloud.
- A conta do GitHub usada para se conectar ao Cloud App Security deve ter permissões de *proprietário* para sua organização.
- Para verificar os proprietários da sua organização, navegue até a página da sua organização, selecione **pessoas** e, em seguida, filtre por *proprietário*.

## <a name="how-to-connect-github-enterprise-cloud-to-cloud-app-security"></a>Como conectar o GitHub Enterprise Cloud ao Cloud App Security

### <a name="verify-your-github-domains"></a>Verifique seus domínios do GitHub

A verificação de seus domínios é opcional. No entanto, é altamente recomendável que você verifique seus domínios para que Cloud App Security possa corresponder os emails de domínio dos membros da sua organização do GitHub ao usuário correspondente Azure Active Directory.

Essas etapas podem ser concluídas independentemente das etapas [Configurar a nuvem empresarial do GitHub](#configure-github-enterprise-cloud) e podem ser ignoradas se você já tiver verificado seus domínios.

1. Atualize sua organização para os [termos de serviço corporativos](https://help.github.com/en/github/setting-up-and-managing-organizations-and-teams/upgrading-to-the-corporate-terms-of-service).
1. Verifique [os domínios da sua organização](https://help.github.com/en/github/setting-up-and-managing-organizations-and-teams/verifying-your-organizations-domain).

    > [!NOTE]
    > Certifique-se de verificar cada um dos domínios gerenciados listados em seu portal de Cloud App Security. Para exibir seus domínios gerenciados, em Cloud app Security, navegue até **configurações**  >  **organização detalhes**  >  **domínios gerenciados**.

### <a name="configure-github-enterprise-cloud"></a>Configurar a nuvem empresarial do GitHub

1. **Localizar o nome de logon da sua organização**  
No GitHub, navegue até a página da sua organização e, na URL, anote o nome de logon da sua organização, você precisará dela mais tarde.

    > [!NOTE]
    > A página terá uma URL como `https://github.com/<your-organization>` . Por exemplo, se a página da sua organização for `https://github.com/sample-organization` , o nome de logon da organização será de *exemplo-organização*.

    ![Captura de tela mostrando como obter o nome de logon da organização](media/connect-github-org-login-name.png)

1. **Crie um aplicativo OAuth para Cloud App Security para conectar sua organização do GitHub.**  
Repita essa etapa para cada organização conectada adicional.

    1. Navegue até **configurações**  >  **configurações do desenvolvedor** , selecione **aplicativos OAuth** e, em seguida, clique em **registrar um aplicativo**. Como alternativa, se você tiver aplicativos OAuth existentes, clique em **novo aplicativo OAuth**.

        ![Captura de tela mostrando a criação de um aplicativo OAuth](media/connect-github-create-oauth-app.png)

    1. Preencha os detalhes **registrar um novo aplicativo OAuth** e, em seguida, clique em **registrar aplicativo**.
        - Na caixa **nome do aplicativo** , insira um nome para o aplicativo.
        - Na caixa **URL da Home Page** , insira a URL para a página inicial do aplicativo.
        - Na caixa **URL de retorno de chamada de autorização** , insira o seguinte valor: `https://portal.cloudappsecurity.com/api/oauth/connect` .

            > [!NOTE]
            > Para clientes de GCC do governo dos EUA, insira o seguinte valor: `https://portal.cloudappsecurity.us/api/oauth/connect`

        ![Captura de tela mostrando o registro de um aplicativo OAuth](media/connect-github-register-oauth-app.png)

    > [!NOTE]
    >
    > - Por padrão, o acesso ao aplicativo OAuth é restrito para organizações. Para habilitar o acesso, navegue até **configurações**  >  **acesso** de terceiros, clique em **remover restrições** e, em seguida, clique em **Sim, remover restrições de aplicativo**.
    > - Os aplicativos pertencentes a uma organização têm acesso aos aplicativos da organização. Para obter mais informações, consulte [sobre as restrições de acesso do aplicativo OAuth](https://help.github.com/en/github/setting-up-and-managing-organizations-and-teams/about-oauth-app-access-restrictions).

1. Navegue até **configurações**  >  **aplicativos OAuth** , selecione o aplicativo OAuth que você acabou de criar e anote sua **ID do cliente** e o **segredo do cliente**.

    ![Captura de tela mostrando detalhes de um aplicativo OAuth](media/connect-github-oauth-app-details.png)

### <a name="configure-cloud-app-security"></a>Configurar o Microsoft Cloud App Security

1. No portal do Cloud App Security, clique em **Investigar** e em **Aplicativos conectados**.

1. Na página **conectores de aplicativos** , clique no botão de adição seguido pelo **GitHub**.

1. No pop-up, preencha a ID do **cliente** , o **segredo do cliente** e o **nome de logon da organização** anotado anteriormente e clique em **conectar no GitHub**.

    ![Captura de tela mostrando a API do GitHub de conexão](media/connect-github-connect-app.png)

    A página de entrada do GitHub é aberta. Se necessário, insira suas credenciais de administrador do GitHub para permitir que Cloud App Security acesso à instância de nuvem empresarial do GitHub da sua equipe.

1. Autorize o aplicativo a fornecer Cloud App Security para acessar sua organização do GitHub.

    > [!NOTE]
    > Cloud App Security requer os seguintes escopos OAuth:
    >
    > - **admin: org** -necessário para sincronizar o log de auditoria da sua organização
    > - **leitura: usuário** e **usuário: email** -necessário para sincronizar os membros da sua organização
    > - **repositório: status** -necessário para sincronizar eventos relacionados ao repositório no log de auditoria para obter mais informações sobre escopos OAuth, consulte [noções básicas sobre escopos para aplicativos OAuth](https://developer.github.com/apps/building-oauth-apps/understanding-scopes-for-oauth-apps/).

    ![Captura de tela mostrando autorizar o GitHub OAuth](media/connect-github-authorize-app.png)

1. De volta ao console do Cloud App Security, você deve receber uma mensagem informando que o GitHub foi conectado com êxito.

1. Certifique-se de que a conexão foi bem-sucedida clicando em **Testar API**.

    O teste pode levar alguns minutos. Depois de receber uma notificação de êxito, clique em **Fechar**.

Depois de conectar o GitHub Enterprise Cloud, você receberá eventos por 7 dias antes da conexão.

Se você tiver problemas para conectar o aplicativo, consulte [Solucionando problemas de conectores de aplicativos](troubleshooting-api-connectors-using-error-messages.md).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]

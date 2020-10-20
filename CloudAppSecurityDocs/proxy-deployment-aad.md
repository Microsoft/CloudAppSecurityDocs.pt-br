---
title: Implantar o Controle de Aplicativos de Acesso Condicional do Cloud App Security em aplicativos do Azure AD
description: Este artigo fornece informações sobre como implantar os recursos de proxy reverso do Controle de Aplicativos de Acesso Condicional do Microsoft Cloud App Security para aplicativos do Azure AD.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/31/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 0df2a20c1c8c8bb1aef440cf3eb8bf16634e6ce0
ms.sourcegitcommit: 812cb1e24ec18de2c4818970f3042ac06acea14c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92212010"
---
# <a name="deploy-conditional-access-app-control-for-featured-apps"></a>Implantar o Controle de Aplicativos de Acesso Condicional para aplicativos em destaque

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Os controles de sessão no Microsoft Cloud App Security funcionam com os aplicativos em destaque. Para obter uma lista de aplicativos que são apresentados por Cloud App Security para trabalhar prontos para uso, consulte [proteger aplicativos com Cloud App Security controle de aplicativos de acesso condicional](proxy-intro-aad.md#featured-apps).

## <a name="prerequisites"></a>Pré-requisitos

- Sua organização deve ter as seguintes licenças para usar Controle de Aplicativos de Acesso Condicional:

  - [Azure Active Directory (Azure AD) Premium P1](/azure/active-directory/license-users-groups) ou superior, ou a licença exigida pela sua solução IDP (provedor de identidade)
  - Microsoft Cloud App Security

- Os aplicativos devem ser configurados com logon único
- Os aplicativos devem usar um dos seguintes protocolos de autenticação:

    |IdP|Protocolos|
    |---|---|
    |Azure AD|SAML 2.0 ou OpenID Connect|
    |Outros|SAML 2.0|

## <a name="to-deploy-featured-apps"></a>Para implantar aplicativos em destaque

Siga estas etapas para configurar aplicativos em destaque para serem controlados pelo Microsoft Cloud App Security Controle de Aplicativos de Acesso Condicional.

**Etapa 1: [configurar seu IDP para trabalhar com Cloud app Security](#conf-idp)**

**Etapa 2: [entrar em cada aplicativo usando um escopo de usuário para a política](#sign-in-scoped)**

**Etapa 3: [verificar se os aplicativos estão configurados para usar controles de acesso e sessão](#portal)**

**Etapa 4: [testar a implantação](#test)**

## <a name="step-1--configure-your-idp-to-work-with-cloud-app-security"></a>Etapa 1: configurar seu IdP para trabalhar com Cloud App Security<a name="conf-idp"></a><a name="add-azure-ad"></a>

### <a name="configure-integration-with-azure-ad"></a>Configurar a integração com o Azure AD

Use as etapas a seguir para criar uma política de acesso condicional do Azure AD que roteia sessões de aplicativo para Cloud App Security. Para outras soluções IdP, consulte [Configurar a integração com outras soluções IDP](#configure-integration-with-other-idp-solutions).

1. No Azure AD, navegue até **segurança**  >  **acesso condicional**.

1. No painel **acesso condicional** , na barra de ferramentas na parte superior, clique em **nova política**.

1. No **novo** painel, na caixa de texto **nome** , insira o nome da política.

1. Em **atribuições**, clique em **usuários e grupos**, atribua os usuários que estarão integrados (logon inicial e verificação) no aplicativo e clique em **concluído**.

1. Em **atribuições**, clique em **aplicativos de nuvem**, atribua os aplicativos que você deseja controlar com controle de aplicativos de acesso condicional e, em seguida, clique em **concluído**.

1. Em **controles de acesso**, clique em **sessão**, selecione **usar controle de aplicativos de acesso condicional** e escolha uma política interna (**monitorar somente** ou **bloquear downloads**) ou **use a política personalizada** para definir uma política avançada no Cloud app Security e clique em **selecionar**.

    ![Acesso condicional do Azure AD](media/azure-ad-caac-policy.png)

1. Opcionalmente, adicione condições e conceda controles conforme necessário.

1. Defina **habilitar política** como **ativado** e, em seguida, clique em **criar**.

### <a name="configure-integration-with-other-idp-solutions"></a>Configurar a integração com outras soluções IdP

Use as etapas a seguir para rotear sessões de aplicativo de outras soluções IdP para Cloud App Security. Para o Azure AD, consulte [Configurar a integração com o Azure ad](#configure-integration-with-azure-ad). Para obter exemplos de como configurar soluções IdP, consulte [configurando seu IDP](proxy-idp-examples.md).

1. Em Cloud app Security, navegue para **investigar**  >  **aplicativos conectados**  >  **controle de aplicativos de acesso condicional aplicativos**.

1. Clique no sinal de adição e, no pop-up, selecione o aplicativo que você deseja implantar e clique em **Iniciar assistente**.
1. Na página **informações do aplicativo** , preencha o formulário usando as informações da página de configuração de logon único do seu aplicativo e clique em **Avançar**.
    - Se o IdP fornecer um arquivo de metadados de logon único para o aplicativo selecionado, selecione **carregar arquivo de metadados do aplicativo** e carregue o arquivo de metadados.
    - Ou selecione **preencher dados manualmente** e forneça as seguintes informações:
        - **URL do serviço de consumidor de asserção**
        - Se seu aplicativo fornecer um certificado SAML, selecione **usar <app_name> certificado SAML** e carregue o arquivo de certificado.

    ![Captura de tela mostrando a página de informações do aplicativo](media/proxy-deploy-add-idp-app-info.png)

1. Na página **provedor de identidade** , use as etapas fornecidas para configurar um novo aplicativo no portal do IDP e clique em **Avançar**.
    1. Vá para o portal do IdP e crie um novo aplicativo SAML personalizado.
    1. Copie a configuração de logon único do `<app_name>` aplicativo existente para o novo aplicativo personalizado.
    1. Atribua usuários ao novo aplicativo personalizado.
    1. Copie a configuração de logon único dos aplicativos inf'rmation, você precisará dela na próxima etapa.

    ![Captura de tela mostrando a página coletar informações do provedor de identidade](media/proxy-deploy-add-idp-get-conf.png)

    > [!NOTE]
    > Essas etapas podem diferir ligeiramente, dependendo do seu provedor de identidade. Esta etapa é recomendada pelos seguintes motivos:
    >
    > - Alguns provedores de identidade não permitem que você altere os atributos SAML ou as propriedades de URL de um aplicativo da Galeria
    > - Configurar um aplicativo personalizado permite que você teste esse aplicativo com controles de acesso e sessão sem alterar o comportamento existente para sua organização.

1. Na próxima página, preencha o formulário usando as informações da página de configuração de logon único do seu aplicativo e clique em **Avançar**.
    - Se o IdP fornecer um arquivo de metadados de logon único para o aplicativo selecionado, selecione **carregar arquivo de metadados do aplicativo** e carregue o arquivo de metadados.
    - Ou selecione **preencher dados manualmente** e forneça as seguintes informações:
        - **URL do serviço de consumidor de asserção**
        - Se seu aplicativo fornecer um certificado SAML, selecione **usar <app_name> certificado SAML** e carregue o arquivo de certificado.

    ![Captura de tela mostrando a página inserir informações do provedor de identidade](media/proxy-deploy-add-idp-enter-conf.png)

1. Na página seguinte, copie as informações a seguir e clique em **Avançar**. Você precisará das informações na próxima etapa.

    - URL de logon único
    - Atributos e valores

    ![Captura de tela mostrando a página coletar informações do SAML dos provedores de identidade](media/proxy-deploy-add-idp-ext-conf.png)

1. No portal do IdP, faça o seguinte:
    > [!NOTE]
    > As configurações normalmente são encontradas na página de configurações do aplicativo personalizado do portal IdP

    1. No campo URL de logon único, insira a URL de logon único anotada anteriormente.
        > [!NOTE]
        > Alguns provedores podem se referir à URL de logon único como a *URL de resposta*.
    1. Adicione os atributos e os valores anotados anteriormente nas propriedades do aplicativo.
        > [!NOTE]
        >
        > - Alguns provedores podem se referir a eles como *atributos de usuário* ou *declarações*.
        > - Ao criar um novo aplicativo SAML, o provedor de identidade Okta limita os atributos a 1024 caracteres. Para atenuar essa limitação, primeiro crie o aplicativo sem os atributos relevantes. Depois de criar o aplicativo, edite-o e, em seguida, adicione os atributos relevantes.
    1. Verifique se o identificador de nome está no formato de endereço de email.
    1. Salve suas configurações.
1. Na página **alterações do aplicativo** , faça o seguinte e clique em **Avançar**. Você precisará das informações na próxima etapa.

    - Copiar a URL de logon único
    - Baixar o Cloud App Security certificado SAML

    ![Captura de tela mostrando a página reunir Cloud App Security informações de SAML](media/proxy-deploy-add-idp-app-changes.png)

1. No portal do aplicativo, nas configurações de logon único, faça o seguinte:
    1. Aconselhável Crie um backup de suas configurações atuais.
    1. No campo URL de logon único, insira a URL de logon único anotada anteriormente.
    1. Carregue o Cloud App Security certificado SAML anotado anteriormente.
    > [!NOTE]
    > Depois de salvar as configurações, todas as solicitações de logon associadas a esse aplicativo serão roteadas por meio de Controle de Aplicativos de Acesso Condicional.

## <a name="step-2-sign-in-to-each-app-using-a-user-scoped-to-the-policy"></a>Etapa 2: entrar em cada aplicativo usando um escopo de usuário para a política<a name="sign-in-scoped"></a>

> [!NOTE]
> Antes de continuar, certifique-se de primeiro sair das sessões existentes.

Depois de criar a política, entre em cada aplicativo configurado nessa política. Entre usando um usuário configurado na política.

Cloud App Security sincronizará os detalhes da política com seus servidores para cada novo aplicativo no qual você entrar. Isso poderá levar até um minuto.

## <a name="step-3-verify-the-apps-are-configured-to-use-access-and-session-controls"></a>Etapa 3: verificar se os aplicativos estão configurados para usar controles de acesso e sessão<a name="portal"></a>

As instruções acima ajudaram a criar uma política interna do Cloud App Security para aplicativos em destaque diretamente no Azure AD. Nesta etapa, verifique se os controles de acesso e sessão estão configurados para esses aplicativos.

1. No portal de Cloud App Security, clique no ícone configurações engrenagem ![configurações](media/settings-icon.png "Ícone de configurações")e, em seguida, selecione **controle de aplicativos de acesso condicional**.

1. Na tabela Controle de Aplicativos de Acesso Condicional aplicativos, examine a coluna **controles disponíveis** e verifique se o controle de **acesso** ou o **acesso condicional do Azure ad**e o **controle de sessão** são exibidos para seus aplicativos.

    > [!NOTE]
    > Se o controle de sessão não aparecer para um aplicativo, ele ainda não estará disponível para esse aplicativo específico. Você pode adicioná-lo imediatamente como um [aplicativo personalizado](proxy-deployment-any-app.md)ou pode abrir uma solicitação para adicioná-lo como um aplicativo em destaque clicando em **solicitar controle de sessão**.
    >
    >![Solicitação de Controle de Aplicativos de Acesso Condicional](media/caac-request.png)

## <a name="step-4-test-the-deployment"></a>Etapa 4: testar a implantação<a name="test"></a>

1. Primeiro saia das sessões existentes. Em seguida, tente entrar em cada aplicativo que foi implantado com êxito. Entre usando um usuário que corresponda à política configurada no Azure AD ou para um aplicativo SAML configurado com seu provedor de identidade.

1. No portal do Cloud App Security, em **Investigar**, selecione **Log de atividades** e garanta que as atividades de logon sejam capturadas para cada aplicativo.

1. Você pode filtrar clicando em **Avançado** e, em seguida, usando a filtragem **Origem é igual a Controle de acesso**.

    ![Filtre usando o acesso condicional do Azure AD](media/sso-logon.png)

1. É recomendável que você entre em aplicativos móveis e da área de trabalho em dispositivos gerenciados e não gerenciados. Isso serve para garantir que as atividades sejam capturadas corretamente no log de atividades.  
Para verificar se a atividade foi capturada corretamente, clique em uma atividade de logon único para que ela abra a gaveta de atividade. Verifique se a **Marca de agente do usuário** reflete corretamente se o dispositivo é um cliente nativo (o que significa um aplicativo móvel ou da área de trabalho) ou um dispositivo gerenciado (em conformidade, ingressado no domínio ou certificado do cliente válido).

> [!NOTE]
> Depois de implantado, você não pode remover um aplicativo da página de Controle de Aplicativos de Acesso Condicional. Desde que você não defina uma política de acesso ou sessão no aplicativo, o Controle de Aplicativos de Acesso Condicional não alterará comportamentos para o aplicativo.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [«ANTERIOR: introdução ao Controle de Aplicativos de Acesso Condicional](proxy-intro-aad.md)

> [!div class="nextstepaction"]
> [Em seguida: integrar e implantar Controle de Aplicativos de Acesso Condicional para qualquer aplicativo»](proxy-deployment-any-app.md)

> [!div class="nextstepaction"]
> [Solução de problemas de controles de acesso e de sessão](troubleshooting-proxy.md)

[!INCLUDE [Open support ticket](includes/support.md)]
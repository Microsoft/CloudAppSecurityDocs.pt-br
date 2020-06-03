---
title: Implantar Cloud App Security Controle de Aplicativos de Acesso Condicional para qualquer aplicativo
description: Este artigo fornece informações sobre como implantar o Microsoft Cloud App Security Controle de Aplicativos de Acesso Condicional recursos de proxy reverso para qualquer aplicativo.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/31/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.suite: ems
ms.openlocfilehash: ddbcbbe72c83f926b8307904a9d5e2bb2731dcba
ms.sourcegitcommit: 5822fcdb1433a6a26195692b05aed160bc339656
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84275788"
---
# <a name="onboard-and-deploy-conditional-access-app-control-for-any-app"></a>Integração e implantação de Controle de Aplicativos de Acesso Condicional para qualquer aplicativo

*Aplica-se a: Microsoft Cloud App Security*

Os controles de sessão no Microsoft Cloud App Security podem ser configurados para trabalhar com qualquer aplicativo Web. Este artigo descreve como integrar e implantar aplicativos de linha de negócios personalizados, aplicativos SaaS sem recursos e aplicativos locais hospedados por meio do proxy de aplicativo Azure Active Directory (Azure AD) com controles de sessão.

Para obter uma lista de aplicativos que são apresentados por Cloud App Security para trabalhar prontos para uso, consulte [proteger aplicativos com Cloud App Security controle de aplicativos de acesso condicional](proxy-intro-aad.md#featured-apps).

## <a name="prerequisites"></a>Pré-requisitos

- Sua organização deve ter as seguintes licenças para usar Controle de Aplicativos de Acesso Condicional:

  - [Azure Active Directory (Azure AD) Premium P1](https://docs.microsoft.com/azure/active-directory/license-users-groups) ou superior, ou a licença exigida pela sua solução IDP (provedor de identidade)
  - Microsoft Cloud App Security

- Os aplicativos devem ser configurados com logon único
- Os aplicativos devem usar um dos seguintes protocolos de autenticação:

    |IdP|Protocolos|
    |---|---|
    |Azure AD|SAML 2.0 ou OpenID Connect|
    |Outros|SAML 2.0|

## <a name="to-deploy-any-app"></a>Para implantar qualquer aplicativo

Siga estas etapas para configurar qualquer aplicativo a ser controlado pelo Cloud App Security Controle de Aplicativos de Acesso Condicional.

**Etapa 1: [configurar seu IDP para trabalhar com Cloud app Security](#conf-idp)**

**Etapa 2: [configurar os usuários que implantarão o aplicativo](#conf-users)**

**Etapa 3: [Configurar o aplicativo que você está implantando](#conf-app)**

**Etapa 4: [verificar se o aplicativo está funcionando corretamente](#verify-app)**

**Etapa 5: [habilitar o aplicativo para uso em sua organização](#enable-app)**

**Etapa 6: [atualizar a política do Azure ad](#update-azure-ad)**

> [!NOTE]
> Para implantar Controle de Aplicativos de Acesso Condicional para aplicativos do Azure AD, você precisa de uma [licença válida para Azure Active Directory Premium P1 ou superior](https://docs.microsoft.com/azure/active-directory/license-users-groups) , bem como uma licença de Cloud app Security.

## <a name="step-1--configure-your-idp-to-work-with-cloud-app-security"></a>Etapa 1: configurar seu IdP para trabalhar com Cloud App Security<a name="conf-idp"></a><a name="conf-azure-ad"></a>

### <a name="configure-integration-with-azure-ad"></a>Configurar a integração com o Azure AD

Use as etapas a seguir para criar uma política de acesso condicional do Azure AD que roteia sessões de aplicativo para Cloud App Security. Para outras soluções IdP, consulte [Configurar a integração com outras soluções IDP](#configure-integration-with-other-idp-solutions).

1. No Azure AD, navegue até **segurança**  >  **acesso condicional**.

1. No painel **acesso condicional** , na barra de ferramentas na parte superior, clique em **nova política**.

1. No **novo** painel, na caixa de texto **nome** , insira o nome da política.

1. Em **atribuições**, clique em **usuários e grupos**, atribua os usuários que estarão integrados (logon inicial e verificação) no aplicativo e clique em **concluído**.

1. Em **atribuições**, clique em **aplicativos de nuvem**, atribua os aplicativos que você deseja controlar com controle de aplicativos de acesso condicional e, em seguida, clique em **concluído**.

1. Em **controles de acesso**, clique em **sessão**, selecione **usar controle de aplicativos de acesso condicional** e escolha as políticas internas (**monitorar somente** ou **bloquear downloads**) ou **use a política personalizada** para definir uma política avançada no Cloud app Security e clique em **selecionar**.

    ![Acesso condicional do Azure AD](media/azure-ad-caac-policy.png)

1. Opcionalmente, adicione condições e conceda controles conforme necessário.

1. Defina **habilitar política** como **ativado** e, em seguida, clique em **criar**.

### <a name="configure-integration-with-other-idp-solutions"></a>Configurar a integração com outras soluções IdP

Use as etapas a seguir para rotear sessões de aplicativo de outras soluções IdP para Cloud App Security. Para o Azure AD, consulte [Configurar a integração com o Azure ad](#configure-integration-with-azure-ad).

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
    1. Copie as informações de configuração de logon único dos aplicativos, você precisará dela na próxima etapa.

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

## <a name="step-2-configure-the-users-that-will-deploy-the-app"></a>Etapa 2: configurar os usuários que implantarão o aplicativo<a name="conf-users"></a>

1. No Cloud App Security, na barra de menus, clique no ícone configurações engrenagem ![configurações](media/settings-icon.png "ícone de configurações") e selecione **configurações**.

1. Em **controle de aplicativos de acesso condicional**, selecione **integração do aplicativo/manutenção**.

1. Insira o nome principal do usuário ou o email para os usuários que estarão integrando o aplicativo e clique em **salvar**.

    ![Captura de tela de configurações para integração de aplicativos e manutenção.](media/app-onboarding-settings.png)

## <a name="step-3-configure-the-app-that-you-are-deploying"></a>Etapa 3: configurar o aplicativo que você está implantando<a name="conf-app"></a>

Vá para o aplicativo que você está implantando. A página que você vê depende se o aplicativo é reconhecido. Realize um dos seguintes procedimentos:

| Status do aplicativo | Descrição | Etapas |
| --- | --- | --- |
| Não reconhecido | Você verá uma página aplicativo não reconhecido solicitando que você configure seu aplicativo. | 1. [adicione o aplicativo ao controle de aplicativos de acesso condicional](#add-app).<br /> 2. [adicione os domínios para o aplicativo](#add-domains)e, em seguida, retorne ao aplicativo e atualize a página.<br /> 3. [Instale os certificados para o aplicativo](#install-certs). |
| Reconhecido | Você verá uma página de integração solicitando que você continue o processo de configuração do aplicativo. | - [Instale os certificados para o aplicativo](#install-certs). <br /><br /> **Observação:** Verifique se o aplicativo está configurado com todos os domínios necessários para que o aplicativo funcione corretamente. Para configurar domínios adicionais, vá para [adicionar os domínios do aplicativo](#add-domains)e, em seguida, retorne à página do aplicativo. |

### <a name="to-add-a-new-app"></a>Para adicionar um novo aplicativo<a name="add-app"></a>

1. Na barra de menus, clique no ícone configurações engrenagem ![configurações](media/settings-icon.png "ícone de configurações")e selecione **controle de aplicativos de acesso condicional**.

1. Clique em **Exibir novos aplicativos**.

    ![Controle de Aplicativos de Acesso Condicional, exibir novos aplicativos](media/caac-view-apps.png)

1. Na tela que é aberta, você pode ver uma lista de novos aplicativos. Para cada aplicativo que você estiver integrando, clique no **+** sinal e, em seguida, clique em **Adicionar**.

    > [!NOTE]
    > Se um aplicativo não for exibido no catálogo de aplicativos do Cloud App Security, ele será exibido na caixa de diálogo nos aplicativos não identificados juntamente com a URL de logon. Ao clicar no sinal + desses aplicativos, você pode integrar o aplicativo como um aplicativo personalizado.

    ![Controle de Aplicativos de Acesso Condicional, aplicativos do Azure AD descobertos](media/caac-discovered-aad-apps.png)

### <a name="to-add-domains-for-an-app"></a>Para adicionar domínios a um aplicativo<a name="add-domains"></a>

A Associação dos domínios corretos a um aplicativo permite que Cloud App Security imponha políticas e atividades de auditoria.

Por exemplo, se você tiver configurado uma política que bloqueia o download de arquivos para um domínio associado, os downloads de arquivo do aplicativo desse domínio serão bloqueados. No entanto, os downloads de arquivo pelo aplicativo de domínios não associados ao aplicativo não serão bloqueados e a ação não será auditada no log de atividades.
> [!NOTE]
> Cloud App Security ainda adiciona um sufixo aos domínios não associados ao aplicativo para garantir uma experiência de usuário tranqüila.

1. De dentro do aplicativo, na barra de ferramentas Cloud App Security admin, clique em **domínios descobertos**.
    > [!NOTE]
    > A barra de ferramentas de administração só é visível para os usuários com permissões para aplicativos integrados ou de manutenção.
1. No painel domínios descobertos, anote os nomes de domínio ou exporte a lista como um arquivo. csv.
    > [!NOTE]
    > O painel exibe uma lista de domínios descobertos que não estão associados no aplicativo. Os nomes de domínio são totalmente qualificados.
1. Vá para Cloud App Security, na barra de menus, clique no ícone configurações engrenagem ![configurações](media/settings-icon.png "ícone de configurações") e selecione **controle de aplicativos de acesso condicional**.
1. Na lista de aplicativos, na linha na qual o aplicativo que você está implantando aparece, escolha os três pontos no final da linha e, em **detalhes do aplicativo**, escolha **Editar**.
    > [!TIP]
    > Para exibir a lista de domínios configurados no aplicativo, clique em **Exibir domínios de aplicativo**.
1. Em **domínios definidos pelo usuário**, insira todos os domínios que você deseja associar a esse aplicativo e, em seguida, clique em **salvar**.
    > [!NOTE]
    > Você pode usar o caractere curinga * como um espaço reservado para qualquer caractere. Ao adicionar domínios, decida se deseja adicionar domínios específicos ( `sub1.contoso.com` , `sub2.contoso.com` ) ou vários domínios ( `*.contoso.com` ).

### <a name="to-install-root-certificates"></a>Para instalar certificados raiz<a name="install-certs"></a>

1. Repita as etapas a seguir para instalar a **autoridade de certificação atual** e os próximos certificados raiz autoassinados **da CA** .
    1. Selecione o certificado.
    1. Clique em **abrir**e, quando solicitado, clique em **abrir** novamente.
    1. Clique em **Instalar certificado**.
    1. Escolha o **usuário atual** ou o **computador local**.
    1. Selecione **Coloque todos os certificados no repositório a seguir** e clique em **procurar**.
    1. Selecione **autoridades de certificação raiz confiáveis** e clique em **OK**.
    1. Clique em **Concluir**.

    > [!NOTE]
    > Para que os certificados sejam reconhecidos, depois de instalar o certificado, você deve reiniciar o navegador e ir para a mesma página.<!-- You'll see a check-mark by the certificates links confirmation they are installed.-->

1. Clique em **Continuar**.

## <a name="step-4-verify-that-the-app-is-working-correctly"></a>Etapa 4: verificar se o aplicativo está funcionando corretamente<a name="verify-app"></a>

1. Verifique se o fluxo de entrada funciona corretamente.
    <!--
    > [!NOTE]
    > Some apps issue a nonce hash during authentication that may break the sign-in process. If this happens, see the Troubleshooting Guide to resolve the issue.-->
1. Quando você estiver no aplicativo, execute as seguintes verificações:
    1. Visite todas as páginas dentro do aplicativo que fazem parte do processo de trabalho de um usuário e verifique se as páginas são renderizadas corretamente.
    1. Verifique se o comportamento e a funcionalidade do aplicativo não são afetados negativamente executando ações comuns, como baixar e carregar arquivos.
    1. Examine a lista de domínios associados ao aplicativo. Para obter mais informações, consulte [adicionar os domínios para o aplicativo](#add-domains).

## <a name="step-5-enable-the-app-for-use-in-your-organization"></a>Etapa 5: habilitar o aplicativo para uso em sua organização<a name="enable-app"></a>

Quando estiver pronto para habilitar o aplicativo para uso no ambiente de produção de sua organização, execute as etapas a seguir.

1. Em Cloud App Security, clique no ícone configurações engrenagem ![configurações](media/settings-icon.png "ícone de configurações")e, em seguida, selecione **controle de aplicativos de acesso condicional**.
1. Na lista de aplicativos, na linha na qual o aplicativo que você está implantando aparece, escolha os três pontos no final da linha e escolha **Editar aplicativo**.
1. Selecione **usar com controle de aplicativos de acesso condicional** e, em seguida, clique em **salvar**.

## <a name="step-6-update-the-azure-ad-policy-azure-ad-only"></a>Etapa 6: atualizar a política do Azure AD (somente Azure AD)<a name="update-azure-ad"></a>

1. No Azure AD, em **segurança**, clique em **acesso condicional**.
1. Atualize a política criada anteriormente para incluir os usuários, grupos e controles relevantes necessários.
1. Em uso da **sessão**  >  **controle de aplicativos de acesso condicional**, se você selecionou **usar política personalizada**, vá para Cloud app Security e crie uma política de sessão correspondente. Para mais informações, confira [Políticas da sessão](session-policy-aad.md).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [«ANTERIOR: implantar Controle de Aplicativos de Acesso Condicional para aplicativos em destaque](proxy-deployment-aad.md)

> [!div class="nextstepaction"]
> [Em seguida: como criar uma política de sessão»](session-policy-aad.md)

## <a name="see-also"></a>Confira também

> [!div class="nextstepaction"]
> [Introdução ao Controle de Aplicativos de Acesso Condicional](proxy-intro-aad.md)

[!INCLUDE [Open support ticket](includes/support.md)]

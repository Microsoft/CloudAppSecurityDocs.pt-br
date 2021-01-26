---
title: Implantar Cloud App Security Controle de Aplicativos de Acesso Condicional para qualquer aplicativo Web usando PingOne
description: Este artigo fornece informações sobre como implantar o Controle de Aplicativos de Acesso Condicional de Microsoft Cloud App Security para qualquer aplicativo Web usando o provedor de identidade PingOne.
ms.date: 09/29/2020
ms.topic: how-to
ms.openlocfilehash: df0ab81e2dcb6140f939caff436d18868daad496
ms.sourcegitcommit: f56a2060b99ab087b8637606a1fb66e5577aded8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98795003"
---
# <a name="onboard-and-deploy-conditional-access-app-control-for-any-web-app-using-pingone-as-the-identity-provider-idp"></a>Integração e implantação de Controle de Aplicativos de Acesso Condicional para qualquer aplicativo Web usando PingOne como o IdP (provedor de identidade)

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Você pode configurar controles de sessão no Microsoft Cloud App Security para trabalhar com qualquer aplicativo Web e qualquer IdP de terceiros. Este artigo descreve como rotear sessões de aplicativo de PingOne para Cloud App Security para controles de sessão em tempo real.

Para este artigo, usaremos o aplicativo Salesforce como um exemplo de um aplicativo Web que está sendo configurado para usar Cloud App Security controles de sessão.

## <a name="prerequisites"></a>Pré-requisitos

- Sua organização deve ter as seguintes licenças para usar Controle de Aplicativos de Acesso Condicional:

  - Uma licença do PingOne relevante (necessária para logon único)
  - Microsoft Cloud App Security

- Uma configuração de logon único do PingOne existente para o aplicativo usando o protocolo de autenticação SAML 2,0

## <a name="to-configure-session-controls-for-your-app-using-pingone-as-the-idp"></a>Para configurar controles de sessão para seu aplicativo usando PingOne como o IdP

Use as etapas a seguir para rotear suas sessões de aplicativo Web de PingOne para Cloud App Security. Para obter as etapas de configuração do Azure AD, consulte [Configurar a integração com o Azure ad](proxy-deployment-any-app.md#configure-integration-with-azure-ad).

> [!NOTE]
> Você pode configurar as informações de logon único do SAML do aplicativo fornecidas pelo PingOne usando um dos seguintes métodos:
>
> - **Opção 1**: carregar o arquivo de metadados SAML do aplicativo.
> - **Opção 2**: fornecer manualmente os dados SAML do aplicativo.
>
> Nas etapas a seguir, usaremos a opção 2.

**Etapa 1: [obter as configurações de logon único do SAML do seu aplicativo](#idp1-get-your-app-saml-sso-info)**

**Etapa 2: [configurar Cloud app Security com as informações de SAML do seu aplicativo](#idp1-conf-cas-with-your-app-saml-info)**

**Etapa 3: [criar um aplicativo personalizado no PingOne](#idp1-create-custom-app-pingone)**

**Etapa 4: [configurar Cloud app Security com as informações do aplicativo PingOne](#idp1-conf-cas-with-pingone-app-info)**

**Etapa 5: [concluir o aplicativo personalizado no PingOne](#idp1-complete-custom-app-in-pingone)**

**Etapa 6: [obter as alterações do aplicativo no Cloud app Security](#idp1-get-app-changes-in-cas)**

**Etapa 7: [concluir as alterações do aplicativo](#idp1-complete-app-changes)**

**Etapa 8: [concluir a configuração no Cloud app Security](#idp1-complete-conf-in-cas)**

<a name="idp1-get-your-app-saml-sso-info"></a>

## <a name="step-1-get-your-apps-saml-single-sign-on-settings"></a>Etapa 1: obter as configurações de logon único do SAML do seu aplicativo

1. No Salesforce, navegue até configurações de **configuração**  >    >  **identidade** de  >  **Sign-On único configurações**.

1. Em **configurações de Sign-On único**, clique no nome da sua configuração existente do SAML 2,0.

    ![Selecione as configurações de SSO do Salesforce](media/proxy-idp-pingone/idp-pingone-sf-select-sso-settings.png)

1. Na página de **configuração de Sign-On única do SAML** , anote a URL de **logon** do Salesforce. Você precisará dessas informações posteriormente.

    > [!NOTE]
    > Se seu aplicativo fornecer um certificado SAML, baixe o arquivo de certificado.

    ![Selecione a URL de logon SSO do Salesforce](media/proxy-idp-pingone/idp-pingone-sf-copy-saml-sso-login-url.png)

<a name="idp1-conf-cas-with-your-app-saml-info"></a>

## <a name="step-2-configure-cloud-app-security-with-your-apps-saml-information"></a>Etapa 2: configurar Cloud App Security com as informações de SAML do seu aplicativo

1. Em Cloud app Security, navegue para **investigar**  >  **aplicativos conectados**  >  **controle de aplicativos de acesso condicional aplicativos**.

1. Clique no sinal de adição ( **+** ) e, no pop-up, selecione o aplicativo que você deseja implantar e clique em **Iniciar assistente**.
1. Na página **informações do aplicativo** , selecione **preencher dados manualmente**, na URL do **serviço do consumidor de asserção** , insira a URL de **logon** do Salesforce que você anotou anteriormente e clique em **Avançar**.

    > [!NOTE]
    > Se seu aplicativo fornecer um certificado SAML, selecione **usar <app_name> certificado SAML** e carregue o arquivo de certificado.

    ![Preencher manualmente as informações de SAML do Salesforce](media/proxy-idp-pingone/idp-pingone-cas-sf-app-info.png)

<a name="idp1-create-custom-app-pingone"></a>

## <a name="step-3-create-a-custom-app-in-pingone"></a>Etapa 3: criar um aplicativo personalizado no PingOne

Antes de prosseguir, use as etapas a seguir para obter informações de seu aplicativo Salesforce existente.

1. Em PingOne, edite seu aplicativo Salesforce existente.

1. Na página **mapeamento de atributo SSO** , anote o atributo e o valor SAML_SUBJECT e, em seguida, baixe o **certificado de autenticação** e os arquivos de **metadados SAML** .

    ![Observe os atributos existentes do aplicativo Salesforce](media/proxy-idp-pingone/idp-pingone-sf-app-copy-saml-sso-attributes.png)

1. Abra o arquivo de metadados SAML e anote o **local PingOne SingleSignOnService**. Você precisará dessas informações posteriormente.

    ![Observação de localização do serviço SSO do aplicativo Salesforce existente](media/proxy-idp-pingone/idp-pingone-sf-app-copy-saml-sso-service-location.png)

1. Na página **acesso ao grupo** , anote os grupos atribuídos.

    ![Observe os grupos atribuídos do aplicativo Salesforce existente](media/proxy-idp-pingone/idp-pingone-sf-app-copy-saml-sso-user-groups.png)

Em seguida, use as instruções da página **Adicionar um aplicativo SAML com seu provedor de identidade** para configurar um aplicativo personalizado no portal do IDP.

![Adicionar aplicativo SAML com seu provedor de identidade](media/proxy-deploy-add-idp-get-conf.png)

> [!NOTE]
> Configurar um aplicativo personalizado permite testar o aplicativo existente com controles de acesso e sessão sem alterar o comportamento atual da sua organização.

1. Crie um **novo aplicativo SAML**.

    ![No PingOne, crie um novo aplicativo personalizado do Salesforce](media/proxy-idp-pingone/idp-pingone-sf-custom-app-new.png)

1. Na página **detalhes do aplicativo** , preencha o formulário e clique em **continuar para a próxima etapa**.

    > [!TIP]
    > Use um nome de aplicativo que lhe ajudará a diferenciar entre o aplicativo personalizado e o aplicativo Salesforce existente.

    ![Preencha os detalhes do aplicativo personalizado](media/proxy-idp-pingone/idp-pingone-sf-custom-app-details.png)

1. Na página **configuração de aplicativo** , faça o seguinte e clique em **continuar na próxima etapa**.
    - No campo **URL de serviço entrar único** , insira a **URL de logon** do Salesforce que você anotou anteriormente.
    - No campo **ID da entidade** , insira uma ID exclusiva começando com *https://*. Certifique-se de que isso seja diferente da configuração existente do aplicativo Salesforce PingOne.
    - Anote a **ID da entidade**. Você precisará dessas informações posteriormente.

    ![Configurar aplicativo personalizado com detalhes de SAML do Salesforce](media/proxy-idp-pingone/idp-pingone-sf-custom-app-set-saml-sso-properties.png)

1. Na página **mapeamento de atributo SSO** , adicione o atributo de **SAML_SUBJECT** do aplicativo Salesforce existente e o valor que você anotou anteriormente e clique em **continuar para a próxima etapa**.

    ![Adicionar atributos ao aplicativo Salesforce personalizado](media/proxy-idp-pingone/idp-pingone-sf-custom-app-set-saml-sso-attributes.png)

1. Na página **acesso ao grupo** , adicione os grupos existentes do aplicativo Salesforce que você anotou anteriormente e conclua a configuração.

    ![Atribuir grupos ao aplicativo Salesforce personalizado](media/proxy-idp-pingone/idp-pingone-sf-custom-app-set-saml-sso-user-groups.png)

<a name="idp1-conf-cas-with-pingone-app-info"></a>

## <a name="step-4-configure-cloud-app-security-with-the-pingone-apps-information"></a>Etapa 4: configurar Cloud App Security com as informações do aplicativo PingOne

1. De volta à página **provedor de identidade** Cloud app Security, clique em **Avançar** para continuar.

1. Na página seguinte, selecione **preencher dados manualmente**, faça o seguinte e clique em **Avançar**.
    - Para a **URL do serviço do consumidor de asserção**, insira a **URL de logon** do Salesforce que você anotou anteriormente.
    - Selecione **carregar certificado SAML do provedor de identidade** e carregue o arquivo de certificado que você baixou anteriormente.

    ![Adicionar URL do serviço SSO e certificado SAML](media/proxy-idp-pingone/idp-pingone-cas-sf-app-idp-info.png)

1. Na próxima página, anote as informações a seguir e clique em **Avançar**. Você precisará das informações mais tarde.

    - URL de logon único do Cloud App Security
    - Cloud App Security atributos e valores

    ![Em Cloud App Security, observe a URL de SSO e os atributos](media/proxy-idp-pingone/idp-pingone-cas-get-sf-app-external-config.png)

<a name="idp1-complete-custom-app-in-pingone"></a>

## <a name="step-5-complete-the-custom-app-in-pingone"></a>Etapa 5: concluir o aplicativo personalizado no PingOne

1. Em PingOne, localize e edite o aplicativo Salesforce personalizado.

    ![Localizar e editar o aplicativo Salesforce personalizado](media/proxy-idp-pingone/idp-pingone-sf-custom-app-edit.png)

1. No campo **serviço de consumidor de asserção (ACS)** , substitua a URL pela URL de logon único do Cloud app Security que você anotou anteriormente e clique em **Avançar**.

    ![Substituir o ACS no aplicativo personalizado do Salesforce](media/proxy-idp-pingone/idp-pingone-sf-custom-app-replace-saml-sso-properties.png)

1. Adicione os atributos de Cloud App Security e os valores que você anotou anteriormente às propriedades do aplicativo.

    ![Adicionar atributos de Cloud App Security ao aplicativo personalizado do Salesforce](media/proxy-idp-pingone/idp-pingone-sf-custom-app-replace-saml-sso-attributes.png)

1. Salve suas configurações.

<a name="idp1-get-app-changes-in-cas"></a>

## <a name="step-6-get-the-app-changes-in-cloud-app-security"></a>Etapa 6: obter as alterações do aplicativo no Cloud App Security

De volta à página **alterações do aplicativo** Cloud app Security, faça o seguinte, mas **não clique em concluir**. Você precisará das informações mais tarde.

- Copiar a URL de logon único do SAML Cloud App Security
- Baixar o Cloud App Security certificado SAML

![Anote a URL de SSO do SAML Cloud App Security e baixe o certificado](media/proxy-idp-pingone/idp-pingone-cas-sf-app-changes.png)

<a name="idp1-complete-app-changes"></a>

## <a name="step-7-complete-the-app-changes"></a>Etapa 7: concluir as alterações do aplicativo

No Salesforce, navegue até configurações de **configuração**  >    >  **identidade**  >  **Sign-On configurações únicas** e faça o seguinte:

1. Recomendado: Crie um backup de suas configurações atuais.
1. Substitua o valor do campo **URL de logon do provedor de identidade** pela URL de logon único do SAML Cloud app Security que você anotou anteriormente.
1. Carregue o Cloud App Security certificado SAML baixado anteriormente.
1. Substitua o valor do campo **ID da entidade** pela ID da entidade do aplicativo personalizado PingOne que você anotou anteriormente.
1. Clique em **Save** (Salvar).

    > [!NOTE]
    > O Cloud App Security certificado SAML é válido por um ano. Depois de expirar, será necessário gerar um novo certificado.

    ![Atualizar o aplicativo Salesforce personalizado com detalhes Cloud App Security SAML](media/proxy-idp-pingone/idp-pingone-sf-custom-app-changes.png)

<a name="idp1-complete-conf-in-cas"></a>

## <a name="step-8-complete-the-configuration-in-cloud-app-security"></a>Etapa 8: concluir a configuração no Cloud App Security

- De volta à página **alterações do aplicativo** Cloud app Security, clique em **concluir**. Depois de concluir o assistente, todas as solicitações de logon associadas a esse aplicativo serão roteadas por meio de Controle de Aplicativos de Acesso Condicional.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [«ANTERIOR: implantar Controle de Aplicativos de Acesso Condicional para qualquer aplicativo](proxy-deployment-any-app.md)

## <a name="see-also"></a>Confira também

> [!div class="nextstepaction"]
> [Introdução ao Controle de Aplicativos de Acesso Condicional](proxy-intro-aad.md)

> [!div class="nextstepaction"]
> [Solução de problemas de controles de acesso e de sessão](troubleshooting-proxy.md)

[!INCLUDE [Open support ticket](includes/support.md)]

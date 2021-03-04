---
title: Implantar Cloud App Security Controle de Aplicativos de Acesso Condicional para qualquer aplicativo Web usando Okta
description: Este artigo fornece informações sobre como implantar o Microsoft Cloud App Security Controle de Aplicativos de Acesso Condicional para qualquer aplicativo Web usando o Okta como o provedor de identidade.
ms.date: 02/18/2021
ms.topic: how-to
ms.openlocfilehash: 8d431689e69c88c31f30fd5d58d718e929eb9a2f
ms.sourcegitcommit: 859594eee0b0bdfab86930f91c994ce609f8debe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2021
ms.locfileid: "101873372"
---
# <a name="onboard-and-deploy-conditional-access-app-control-for-any-web-app-using-okta-as-the-identity-provider-idp"></a>Integração e implantação de Controle de Aplicativos de Acesso Condicional para qualquer aplicativo Web usando Okta como o IdP (provedor de identidade)

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Você pode configurar controles de sessão no Microsoft Cloud App Security para trabalhar com qualquer aplicativo Web e qualquer IdP de terceiros. Este artigo descreve como rotear sessões de aplicativo de Okta para Cloud App Security para controles de sessão em tempo real.

Para este artigo, usaremos o aplicativo Salesforce como um exemplo de um aplicativo Web que está sendo configurado para usar Cloud App Security controles de sessão.

## <a name="prerequisites"></a>Pré-requisitos

- Sua organização deve ter as seguintes licenças para usar Controle de Aplicativos de Acesso Condicional:

  - Um locatário Okta pré-configurado.
  - Microsoft Cloud App Security

- Uma configuração de logon único do Okta existente para o aplicativo usando o protocolo de autenticação SAML 2,0

## <a name="to-configure-session-controls-for-your-app-using-okta-as-the-idp"></a>Para configurar controles de sessão para seu aplicativo usando Okta como o IdP

Use as etapas a seguir para rotear suas sessões de aplicativo Web de Okta para Cloud App Security. Para obter as etapas de configuração do Azure AD, consulte [Configurar a integração com o Azure ad](proxy-deployment-any-app.md#configure-integration-with-azure-ad).

> [!NOTE]
> Você pode configurar as informações de logon único do SAML do aplicativo fornecidas pelo Okta usando um dos seguintes métodos:
>
> - **Opção 1**: carregar o arquivo de metadados SAML do aplicativo.
> - **Opção 2**: fornecer manualmente os dados SAML do aplicativo.
>
> Nas etapas a seguir, usaremos a opção 2.

**Etapa 1: [obter as configurações de logon único do SAML do seu aplicativo](#idp1-get-your-app-saml-sso-info)**

**Etapa 2: [configurar Cloud app Security com as informações de SAML do seu aplicativo](#idp1-conf-cas-with-your-app-saml-info)**

**Etapa 3: [criar um novo aplicativo personalizado do Okta e o aplicativo de configuração Sign-On única](#idp1-create-custom-app-okta)**

**Etapa 4: [configurar Cloud app Security com as informações do aplicativo Okta](#idp1-conf-cas-with-okta-app-info)**

**Etapa 5: [concluir a configuração do aplicativo personalizado Okta](#idp1-complete-custom-app-in-okta)**

**Etapa 6: [obter as alterações do aplicativo no Cloud app Security](#idp1-get-app-changes-in-cas)**

**Etapa 7: [concluir as alterações do aplicativo](#idp1-complete-app-changes)**

**Etapa 8: [concluir a configuração no Cloud app Security](#idp1-complete-conf-in-cas)**

<a name="idp1-get-your-app-saml-sso-info"></a>

## <a name="step-1-get-your-apps-saml-single-sign-on-settings"></a>Etapa 1: obter as configurações de logon único do SAML do seu aplicativo

1. No Salesforce, navegue até configurações de **configuração**  >    >  **identidade** de  >  **Sign-On único configurações**.

1. Em **configurações de Sign-On único**, clique no nome da configuração existente do Okta.

    ![Selecione as configurações de SSO do Salesforce](media/proxy-idp-okta/idp-okta-sf-select-sso-settings.png)

1. Na página de **configuração de Sign-On única do SAML** , anote a URL de **logon** do Salesforce. Você precisará disso mais tarde ao configurar Cloud App Security.

    > [!NOTE]
    > Se seu aplicativo fornecer um certificado SAML, baixe o arquivo de certificado.

    ![Selecione a URL de logon SSO do Salesforce](media/proxy-idp-okta/idp-okta-sf-copy-saml-sso-login-url.png)

<a name="idp1-conf-cas-with-your-app-saml-info"></a>

## <a name="step-2-configure-cloud-app-security-with-your-apps-saml-information"></a>Etapa 2: configurar Cloud App Security com as informações de SAML do seu aplicativo

1. Em Cloud app Security, navegue para **investigar**  >  **aplicativos conectados**  >  **controle de aplicativos de acesso condicional aplicativos**.

1. Clique no sinal de adição e, no pop-up, selecione o aplicativo que você deseja implantar e clique em **Iniciar assistente**.
1. Na página **informações do aplicativo** , selecione **preencher dados manualmente**, na URL do **serviço do consumidor de asserção** , insira a URL de **logon** do Salesforce que você anotou anteriormente e clique em **Avançar**.

    > [!NOTE]
    > Se seu aplicativo fornecer um certificado SAML, selecione **usar <app_name> certificado SAML** e carregue o arquivo de certificado.

    ![Preencher manualmente as informações de SAML do Salesforce](media/proxy-idp-okta/idp-okta-cas-sf-app-info.png)

<a name="idp1-create-custom-app-okta"></a>

## <a name="step-3-create-a-new-okta-custom-application-and-app-single-sign-on-configuration"></a>Etapa 3: criar um novo aplicativo personalizado do Okta e o aplicativo de configuração Sign-On única

> [!NOTE]
> Para limitar o tempo de inatividade do usuário final e preservar sua configuração válida conhecida, é recomendável criar um novo **aplicativo personalizado** e uma **única configuração de Sign-On**. Quando isso não for possível, ignore as etapas relevantes. Por exemplo, se o aplicativo que você está configurando não oferecer suporte à criação de várias **configurações de Sign-On único**, ignore a etapa criar novo logon único.

1. No console de **Administração do Okta** , em **aplicativos**, exiba as propriedades de sua configuração existente para seu aplicativo e anote as configurações.

1. Clique em **Adicionar aplicativo** e, em seguida, clique em **criar novo aplicativo**. Além do valor do **URI da audiência (ID da entidade do SP)** que deve ser um nome exclusivo, configure o novo aplicativo usando as configurações que você anotou anteriormente. Você precisará desse aplicativo mais tarde ao configurar Cloud App Security.
1. Navegue até **aplicativos**, exiba a configuração existente do Okta e, na guia **entrar** , selecione **exibir instruções de instalação**.

    ![Observação de localização do serviço SSO do aplicativo Salesforce existente](media/proxy-idp-okta/idp-okta-sf-view-setup-instructions.png)

1. Anote a **URL de Sign-On única do provedor de identidade** e baixe o certificado de autenticação do provedor de identidade (X. 509). Você precisará dessas informações posteriormente.

1. De volta ao Salesforce, na página de configurações de logon único do Okta existente, anote todas as configurações.
1. Crie uma nova configuração de logon único do SAML. Além do valor da **ID da entidade** que deve corresponder ao URI de público do aplicativo personalizado **(ID da entidade do SP)**, configure o logon único usando as configurações que você anotou anteriormente. Você precisará disso mais tarde ao configurar Cloud App Security.
1. Depois de salvar o novo aplicativo, navegue até a página **atribuições** e atribua as **pessoas** ou **grupos** que exigem acesso ao aplicativo.

<a name="idp1-conf-cas-with-okta-app-info"></a>ׂ

## <a name="step-4-configure-cloud-app-security-with-the-okta-apps-information"></a>Etapa 4: configurar Cloud App Security com as informações do aplicativo Okta

1. De volta à página **provedor de identidade** Cloud app Security, clique em **Avançar** para continuar.

1. Na página seguinte, selecione **preencher dados manualmente**, faça o seguinte e clique em **Avançar**.
    - Para a **URL do serviço de logon único**, insira a **URL de logon** do Salesforce que você anotou anteriormente.
    - Selecione **carregar certificado SAML do provedor de identidade** e carregue o arquivo de certificado que você baixou anteriormente.

    ![Adicionar URL do serviço SSO e certificado SAML](media/proxy-idp-okta/idp-okta-cas-sf-app-idp-info.png)

1. Na próxima página, anote as informações a seguir e clique em **Avançar**. Você precisará das informações mais tarde.

    - URL de logon único do Cloud App Security
    - Cloud App Security atributos e valores

    > [!NOTE]
    > Se você vir uma opção para carregar o **Cloud app Security certificado SAML para o provedor de identidade**, clique em clique para baixar o arquivo de certificado. Você precisará dessas informações posteriormente.

    ![Em Cloud App Security, observe a URL de SSO e os atributos](media/proxy-idp-okta/idp-okta-cas-get-sf-app-external-config.png)

<a name="idp1-complete-custom-app-in-okta"></a>

## <a name="step-5-complete-the-configuration-of-the-okta-custom-application"></a>Etapa 5: concluir a configuração do aplicativo personalizado Okta

1. De volta ao console de **Administração do Okta** , em **aplicativos**, selecione o aplicativo personalizado que você criou anteriormente e, em configurações **gerais**  >  de **SAML**, clique em **Editar**.

    ![Localizar e editar configurações de SAML](media/proxy-idp-okta/idp-okta-sf-saml-settings-edit.png)

1. No campo **URL de logon único** , substitua a URL pela URL de logon único do Cloud app Security que você anotou anteriormente e, em seguida, salve as configurações.

1. Em **diretório**, selecione **Editor de perfil**, selecione o aplicativo personalizado que você criou anteriormente e, em seguida, clique em **perfil**. Adicione atributos usando as informações a seguir.

    | Nome de exibição | Nome da variável | Tipo de dados | Tipo de atributo |
    | --- | --- | --- | --- |
    | McasSigningCert | McasSigningCert | string | Personalizado |
    | McasAppId | McasAppId | string | Personalizado |

    ![Adicionar atributos de perfil](media/proxy-idp-okta/idp-okta-sf-add-profile-attributes-edit.png)

1. De volta à página **Editor de perfil** , selecione o aplicativo personalizado que você criou anteriormente, clique em **mapeamentos** e, em seguida, selecione **Okta usuário para {custom_app_name}**. Mapeie os atributos **McasSigningCert** e **McasAppId** para os valores de atributo Cloud app Security que você anotou anteriormente.

    > [!NOTE]
    >
    > - Certifique-se de colocar os valores entre aspas duplas (")
    > - Okta limita os atributos a 1024 caracteres. Para atenuar essa limitação, adicione os atributos usando o **Editor de perfil** , conforme descrito.

    ![Mapear atributos de perfil](media/proxy-idp-okta/idp-okta-sf-map-profile-attributes-edit.png)

1. Salve suas configurações.

<a name="idp1-get-app-changes-in-cas"></a>

## <a name="step-6-get-the-app-changes-in-cloud-app-security"></a>Etapa 6: obter as alterações do aplicativo no Cloud App Security

De volta à página **alterações do aplicativo** Cloud app Security, faça o seguinte, mas **não clique em concluir**. Você precisará das informações mais tarde.

- Copiar a URL de logon único do SAML Cloud App Security
- Baixar o Cloud App Security certificado SAML

![Anote a URL de SSO do SAML Cloud App Security e baixe o certificado](media/proxy-idp-okta/idp-okta-cas-sf-app-changes.png)

<a name="idp1-complete-app-changes"></a>

## <a name="step-7-complete-the-app-changes"></a>Etapa 7: concluir as alterações do aplicativo

No Salesforce, navegue até configurações de **configuração**  >    >  **identidade**  >  **Sign-On configurações únicas** e faça o seguinte:

1. Aconselhável Crie um backup de suas configurações atuais.
1. Substitua o valor do campo **URL de logon do provedor de identidade** pela URL de logon único do SAML Cloud app Security que você anotou anteriormente.
1. Carregue o Cloud App Security certificado SAML baixado anteriormente.
1. Clique em **Save** (Salvar).

    > [!NOTE]
    >
    > - Depois de salvar as configurações, todas as solicitações de logon associadas a esse aplicativo serão roteadas por meio de Controle de Aplicativos de Acesso Condicional.
    > - O Cloud App Security certificado SAML é válido por um ano. Depois de expirar, será necessário gerar um novo certificado.

    ![Atualizar configurações de SSO](media/proxy-idp-okta/idp-okta-sf-update-sso-settings.png)

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

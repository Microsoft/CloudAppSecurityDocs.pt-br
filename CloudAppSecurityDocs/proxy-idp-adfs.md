---
title: Implantar Cloud App Security Controle de Aplicativos de Acesso Condicional para qualquer aplicativo Web usando AD FS
description: Este artigo fornece informações sobre como implantar o Controle de Aplicativos de Acesso Condicional de Microsoft Cloud App Security para qualquer aplicativo Web usando AD FS como o provedor de identidade.
ms.date: 01/26/2021
ms.topic: how-to
ms.openlocfilehash: 74a454332125162dbec74f076d150ffe1b9d9b45
ms.sourcegitcommit: f56a2060b99ab087b8637606a1fb66e5577aded8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98795002"
---
# <a name="onboard-and-deploy-conditional-access-app-control-for-any-web-app-using-active-directory-federation-services-ad-fs-as-the-identity-provider-idp"></a>Integração e implantação de Controle de Aplicativos de Acesso Condicional para qualquer aplicativo Web usando Serviços de Federação do Active Directory (AD FS) (AD FS) como o IdP (provedor de identidade)

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Você pode configurar controles de sessão no Microsoft Cloud App Security para trabalhar com qualquer aplicativo Web e qualquer IdP de terceiros. Este artigo descreve como rotear sessões de aplicativo de AD FS para Cloud App Security para controles de sessão em tempo real.

Para este artigo, usaremos o aplicativo Salesforce como um exemplo de um aplicativo Web que está sendo configurado para usar Cloud App Security controles de sessão.

## <a name="prerequisites"></a>Pré-requisitos

- Sua organização deve ter as seguintes licenças para usar Controle de Aplicativos de Acesso Condicional:

  - Um ambiente de AD FS pré-configurado
  - Microsoft Cloud App Security

- Uma configuração de logon único AD FS existente para o aplicativo usando o protocolo de autenticação SAML 2,0

## <a name="to-configure-session-controls-for-your-app-using-ad-fs-as-the-idp"></a>Para configurar controles de sessão para seu aplicativo usando AD FS como o IdP

Use as etapas a seguir para rotear suas sessões de aplicativo Web de AD FS para Cloud App Security. Para obter as etapas de configuração do Azure AD, consulte [Configurar a integração com o Azure ad](proxy-deployment-any-app.md#configure-integration-with-azure-ad).

> [!NOTE]
> Você pode configurar as informações de logon único do SAML do aplicativo fornecidas por AD FS usando um dos seguintes métodos:
>
> - **Opção 1**: carregar o arquivo de metadados SAML do aplicativo.
> - **Opção 2**: fornecer manualmente os dados SAML do aplicativo.
>
> Nas etapas a seguir, usaremos a opção 2.

**Etapa 1: [obter as configurações de logon único do SAML do seu aplicativo](#idp1-get-your-app-saml-sso-info)**

**Etapa 2: [configurar Cloud app Security com as informações de SAML do seu aplicativo](#idp1-conf-cas-with-your-app-saml-info)**

**Etapa 3: [criar uma nova AD FS confiança de terceira parte confiável e configuração de Sign-On de aplicativo único](#idp1-create-custom-app-adfs)**

**Etapa 4: [configurar Cloud app Security com as informações do aplicativo AD FS](#idp1-conf-cas-with-adfs-app-info)**

**Etapa 5: [concluir a configuração do AD FS a terceira parte confiável](#idp1-complete-custom-app-in-adfs)**

**Etapa 6: [obter as alterações do aplicativo no Cloud app Security](#idp1-get-app-changes-in-cas)**

**Etapa 7: [concluir as alterações do aplicativo](#idp1-complete-app-changes)**

**Etapa 8: [concluir a configuração no Cloud app Security](#idp1-complete-conf-in-cas)**

<a name="idp1-get-your-app-saml-sso-info"></a>

## <a name="step-1-get-your-apps-saml-single-sign-on-settings"></a>Etapa 1: obter as configurações de logon único do SAML do seu aplicativo

1. No Salesforce, navegue até configurações de **configuração**  >    >  **identidade** de  >  **Sign-On único configurações**.

1. Em **configurações de Sign-On único**, clique no nome da configuração de AD FS existente.

    ![Selecione as configurações de SSO do Salesforce](media/proxy-idp-adfs/idp-adfs-sf-select-sso-settings.png)

1. Na página de **configuração de Sign-On única do SAML** , anote a URL de **logon** do Salesforce. Você precisará disso mais tarde ao configurar Cloud App Security.

    > [!NOTE]
    > Se seu aplicativo fornecer um certificado SAML, baixe o arquivo de certificado.

    ![Selecione a URL de logon SSO do Salesforce](media/proxy-idp-adfs/idp-adfs-sf-copy-saml-sso-login-url.png)

<a name="idp1-conf-cas-with-your-app-saml-info"></a>

## <a name="step-2-configure-cloud-app-security-with-your-apps-saml-information"></a>Etapa 2: configurar Cloud App Security com as informações de SAML do seu aplicativo

1. Em Cloud app Security, navegue para **investigar**  >  **aplicativos conectados**  >  **controle de aplicativos de acesso condicional aplicativos**.

1. Clique no sinal de adição e, no pop-up, selecione o aplicativo que você deseja implantar e clique em **Iniciar assistente**.
1. Na página **informações do aplicativo** , selecione **preencher dados manualmente**, na URL do **serviço do consumidor de asserção** , insira a URL de **logon** do Salesforce que você anotou anteriormente e clique em **Avançar**.

    > [!NOTE]
    > Se seu aplicativo fornecer um certificado SAML, selecione **usar <app_name> certificado SAML** e carregue o arquivo de certificado.

    ![Preencher manualmente as informações de SAML do Salesforce](media/proxy-idp-adfs/idp-adfs-cas-sf-app-info.png)

<a name="idp1-create-custom-app-adfs"></a>

## <a name="step-3-create-a-new-ad-fs-relying-party-trust-and-app-single-sign-on-configuration"></a>Etapa 3: criar uma nova AD FS confiança de terceira parte confiável e configuração de Sign-On de aplicativo único

> [!NOTE]
> Para limitar o tempo de inatividade do usuário final e preservar sua configuração válida conhecida, é recomendável criar uma nova relação de confiança de terceira **parte confiável** e **configuração de Sign-On única**. Quando isso não for possível, ignore as etapas relevantes. Por exemplo, se o aplicativo que você está configurando não oferecer suporte à criação de várias **configurações de Sign-On único**, ignore a etapa criar novo logon único.

1. No console de **Gerenciamento do AD FS** , em relações de confiança de terceira parte **confiável**, exiba as propriedades da relação de confiança de terceira parte confiável existente para seu aplicativo e anote as configurações.

1. Em **ações**, clique em **Adicionar confiança de terceira parte confiável**. Além do valor do **identificador** que deve ser um nome exclusivo, configure a nova relação de confiança usando as configurações que você anotou anteriormente. Você precisará dessa relação de confiança mais tarde ao configurar Cloud App Security.
1. Abra o arquivo de metadados de Federação e anote o local do AD FS **SingleSignOnService**. Você precisará dessas informações posteriormente.

    > [!NOTE]
    > Você pode usar o ponto de extremidade a seguir para acessar o arquivo de metadados de Federação: `https://<Your_Domain>/federationmetadata/2007-06/federationmetadata.xml`

    ![Observação de localização do serviço SSO do aplicativo Salesforce existente](media/proxy-idp-adfs/idp-adfs-sf-app-copy-saml-sso-service-location.png)

1. Baixe o certificado de autenticação do provedor de identidade. Você precisará dessas informações posteriormente.
    1. Em **Serviços**  >  **certificados**, clique com o botão direito do mouse no certificado de assinatura AD FS e selecione **Exibir certificado**.

        ![Exibir Propriedades do certificado de autenticação IdP](media/proxy-idp-adfs/idp-adfs-view-signing-cert-props.png)

    1. Na guia detalhes do certificado, clique em **copiar para arquivo** e siga as etapas no **Assistente para exportação de certificados** para exportar seu certificado como um *X. 509 codificado em base-64 (. CER)* arquivo.

        ![Salvar arquivo de certificado de autenticação IdP](media/proxy-idp-adfs/idp-adfs-save-signing-cert-file.png)

1. De volta ao Salesforce, na página de configurações de logon único do AD FS existente, anote todas as configurações.
1. Crie uma nova configuração de logon único do SAML. Além do valor da **ID de entidade** que deve corresponder ao **identificador** de confiança de terceira parte confiável, configure o logon único usando as configurações que você anotou anteriormente. Você precisará disso mais tarde ao configurar Cloud App Security.

<a name="idp1-conf-cas-with-adfs-app-info"></a>

## <a name="step-4-configure-cloud-app-security-with-the-ad-fs-apps-information"></a>Etapa 4: configurar Cloud App Security com as informações do aplicativo AD FS

1. De volta à página **provedor de identidade** Cloud app Security, clique em **Avançar** para continuar.

1. Na página seguinte, selecione **preencher dados manualmente**, faça o seguinte e clique em **Avançar**.
    - Para a **URL do serviço de logon único**, insira a **URL de logon** do Salesforce que você anotou anteriormente.
    - Selecione **carregar certificado SAML do provedor de identidade** e carregue o arquivo de certificado que você baixou anteriormente.

    ![Adicionar URL do serviço SSO e certificado SAML](media/proxy-idp-adfs/idp-adfs-cas-sf-app-idp-info.png)

1. Na próxima página, anote as informações a seguir e clique em **Avançar**. Você precisará das informações mais tarde.

    - URL de logon único do Cloud App Security
    - Cloud App Security atributos e valores

    > [!NOTE]
    > Se você vir uma opção para carregar o **Cloud app Security certificado SAML para o provedor de identidade**, clique no link para baixar o arquivo de certificado. Você precisará dessas informações posteriormente.

    ![Em Cloud App Security, observe a URL de SSO e os atributos](media/proxy-idp-adfs/idp-adfs-cas-get-sf-app-external-config.png)

<a name="idp1-complete-custom-app-in-adfs"></a>

## <a name="step-5-complete-the-configuration-of-the-ad-fs-relying-party-trust"></a>Etapa 5: concluir a configuração do AD FS a terceira parte confiável

1. De volta ao console de **Gerenciamento do AD FS** , clique com o botão direito do mouse na terceira parte confiável que você criou anteriormente e selecione **Editar política de emissão de declaração**.

    ![Localizar e editar a emissão de declaração de confiança dependente](media/proxy-idp-adfs/idp-adfs-sf-relying-trust-edit.png)

1. Na caixa de diálogo **Editar política de emissão de declaração** , em **regras de transformação de emissão**, use as informações fornecidas na tabela a seguir para concluir as etapas para criar regras personalizadas.

    | Nome da regra de declaração | Regra personalizada |
    | --- | --- |
    | McasSigningCert | `=> issue(type="McasSigningCert", value="<value>");` onde `<value>` é o valor de **McasSigningCert** do assistente de Cloud app Security que você anotou anteriormente |
    | McasAppId | `=> issue(type="McasAppId", value="<value>");` é o valor de **McasAppId** do assistente de Cloud app Security que você anotou anteriormente |

    1. Clique em **Adicionar regra**, em **modelo de regra de declaração** , selecione **enviar declarações usando uma regra personalizada** e clique em **Avançar**.
    1. Na página **Configurar regra** , insira o respectivo **nome da regra de declaração** e a **regra personalizada** fornecida.

    > [!NOTE]
    > Essas regras são além de quaisquer regras de declaração ou atributos exigidos pelo aplicativo que você está configurando.

1. De volta à página de confiança de terceira parte **confiável** , clique com o botão direito do mouse na terceira parte confiável que você criou anteriormente e selecione **Propriedades**.
1. Na guia **pontos** de extremidade, selecione **terminal de consumidor de Asserção SAML**, clique em **Editar** e substitua a **URL confiável** pela URL de logon único do Cloud app Security que você anotou anteriormente e, em seguida, clique em **OK**.

    ![Atualizar URL confiável das propriedades do ponto de extremidade de confiança dependente](media/proxy-idp-adfs/idp-adfs-sf-relying-trust-endpoint-properties.png)

1. Se você baixou um **Cloud app Security certificado SAML para o provedor de identidade**, na guia **assinatura** , clique em **Adicionar** e carregue o arquivo de certificado e, em seguida, clique em **OK**.

    ![Atualizar propriedades de assinatura de confiança dependente certificado SAML](media/proxy-idp-adfs/idp-adfs-sf-relying-trust-signature-properties.png)

1. Salve suas configurações.

<a name="idp1-get-app-changes-in-cas"></a>

## <a name="step-6-get-the-app-changes-in-cloud-app-security"></a>Etapa 6: obter as alterações do aplicativo no Cloud App Security

De volta à página **alterações do aplicativo** Cloud app Security, faça o seguinte, mas **não clique em concluir**. Você precisará das informações mais tarde.

- Copiar a URL de logon único do SAML Cloud App Security
- Baixar o Cloud App Security certificado SAML

![Anote a URL de SSO do SAML Cloud App Security e baixe o certificado](media/proxy-idp-adfs/idp-adfs-cas-sf-app-changes.png)

<a name="idp1-complete-app-changes"></a>

## <a name="step-7-complete-the-app-changes"></a>Etapa 7: concluir as alterações do aplicativo

No Salesforce, navegue até configurações de **configuração**  >    >  **identidade**  >  **Sign-On configurações únicas** e faça o seguinte:

1. Recomendado: Crie um backup de suas configurações atuais.
1. Substitua o valor do campo **URL de logon do provedor de identidade** pela URL de logon único do SAML Cloud app Security que você anotou anteriormente.
1. Carregue o Cloud App Security certificado SAML baixado anteriormente.
1. Clique em **Save** (Salvar).

    > [!NOTE]
    > O Cloud App Security certificado SAML é válido por um ano. Depois de expirar, será necessário gerar um novo certificado.

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

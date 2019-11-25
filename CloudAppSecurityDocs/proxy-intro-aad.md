---
title: Proteger aplicativos com o Controle de Aplicativos de Acesso Condicional do Microsoft Cloud App Security
description: Este artigo fornece informações sobre como funciona o proxy reverso do Controle de Aplicativos de Acesso Condicional do Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 9/23/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: d4b800afa927b8a9151837cfbff76478c98bf71f
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2019
ms.locfileid: "74460544"
---
# <a name="protect-apps-with-microsoft-cloud-app-security-conditional-access-app-control"></a>Proteger aplicativos com o Controle de Aplicativo de Acesso Condicional do Microsoft Cloud App Security

*Aplica-se ao: Microsoft Cloud App Security*

>[!div class="step-by-step"]
[PRÓXIMO: Implantar o Controle de Aplicativo de Acesso Condicional »](proxy-deployment-aad.md)

No espaço de trabalho de hoje, muitas vezes não é suficiente saber o que está acontecendo em seu ambiente de nuvem após o fato. Você deseja interromper violações e vazamentos em tempo real antes que os funcionários intencional ou inadvertidamente coloquem seus dados e sua organização em risco. É importante permitir que os usuários em sua organização aproveitem ao máximo os serviços e as ferramentas disponíveis a eles em aplicativos de nuvem e que eles tragam os próprios dispositivos para o trabalho. Ao mesmo tempo, são necessárias ferramentas para ajudar a proteger sua organização contra vazamentos de dados e roubo de dados, em tempo real. Juntamente com o Azure Active Directory, o Microsoft Cloud App Security oferece esses recursos em uma experiência holística e integrada com o Controle de Aplicativo de Acesso Condicional.

> [!NOTE]
> To use Cloud App Security Conditional Access App Control, you need an [Azure Active Directory P1 license](https://azure.microsoft.com/pricing/details/active-directory/), and an active Microsoft Cloud App Security subscription or Office 365 E5 license. For a list of featured apps included with Office 365 E5, see [Office 365 featured apps](#O365-apps).

Office 365 E5 license. For a list of apps included with supported Office 365 E5, see Office 365 featured apps

## <a name="how-it-works"></a>Como funciona

Controle de Aplicativos de Acesso Condicional usa uma arquitetura de proxy reverso e é exclusivamente integrado ao acesso condicional do Azure AD. O acesso condicional do Azure AD permite que você aplique controles de acesso nos aplicativos da sua organização com base em determinadas condições. As condições definem a *quem* (usuário ou grupo de usuários), a *quais* (quais aplicativos de nuvem) e *onde* (quais locais e redes) uma política de acesso condicional é aplicada. Depois de determinar as condições, é possível encaminhar os usuários ao Microsoft Cloud App Security para proteger dados com o Controle de Aplicativos de Acesso Condicional, aplicando controles de acesso e de sessão.

O Controle de Aplicativo de Acesso Condicional permite o monitoramento e controle em tempo real do acesso e das sessões do aplicativo com base nas políticas de acesso e de sessão. As políticas de acesso e de sessão são utilizadas dentro do portal do Cloud App Security para refinar ainda mais os filtros e definir as ações a serem executadas em relação a um usuário. Com as políticas de acesso e de sessão, é possível:

- **Prevent data exfiltration**: You can block the download, cut, copy, and print of sensitive documents on, for example, unmanaged devices.

- **Protect on download**: Instead of blocking the download of sensitive documents, you can require documents to be labeled and protected with Azure Information Protection. This action ensures the document is protected and user access is restricted in a potentially risky session.

- **Prevent upload of unlabeled files**: Before a sensitive file is uploaded, distributed, and used by others, it’s important to make sure that the file has the right label and protection. You can ensure that unlabeled files with sensitive content are blocked from being uploaded until the user classifies the content.

- **Monitor user sessions for compliance**: Risky users are monitored when they sign into apps and their actions are logged from within the session. É possível investigar e analisar o comportamento do usuário para compreender onde e sob quais condições as políticas de sessão deverão ser aplicadas no futuro.

- **Block access**: You can granularly block access for specific apps and users depending on several risk factors. For example, you can block them if they are using client certificates as a form of device management.

- **Block custom activities**: Some applications have unique scenarios that carry risk, for example, sending messages with sensitive content in applications like Microsoft Teams or Slack. In these kinds of scenarios, you can scan messages for sensitive content and block them in real time.

### <a name="how-session-control-works"></a>Como funciona o controle de sessão

A criação de uma política de sessão com Controle de Aplicativo de Acesso Condicional permite que você controle as sessões do usuário, redirecionando-o por meio de um proxy reverso, em vez de diretamente para o aplicativo. From then on, user requests and responses go through Cloud App Security rather than directly to the app.

When a session is protected by proxy, all the relevant URLs and cookies are replaced by Cloud App Security. Por exemplo, se o aplicativo retornar uma página com links cujos domínios terminam com myapp.com, o link será substituído por domínios que terminam com algo como: myapp.com.us.cas.ms

This method doesn't require you to install anything on the device making it ideal when monitoring or controlling sessions from unmanaged devices or partner users.

> [!NOTE]
> O Cloud App Security aproveita os data centers do Azure em todo o mundo para fornecer desempenho otimizado por meio de geolocalização. Isso significa que uma sessão de usuário pode ser hospedada fora de uma região específica, dependendo dos padrões de tráfego e da localização. No entanto, para proteger sua privacidade, nenhum dado de sessão é armazenado nesses data centers.

## <a name="managed-device-identification"></a>Identificação do dispositivo gerenciado

O Controle de Aplicativo de Acesso Condicional permite que você crie políticas que levam em conta se um dispositivo é gerenciado ou não. Para identificar se um dispositivo é gerenciado ou não, o recurso usa:

- Dispositivos em conformidade
- Dispositivos ingressados em domínio
- Implantação de certificados do cliente

To configure a policy to leverage device management via client certificates:

1. Vá até a engrenagem de configurações e selecione **Identificação de dispositivo**.
1. Carregue um ou mais certificados raiz ou intermediários.
1. After the certificate is uploaded, you can create [access policies](access-policy-aad.md) and [session policies](session-policy-aad.md) based on **Device tag** and **Valid client certificate**.

    ![ID do dispositivo do Controle de Aplicativos de Acesso Condicional](./media/caac-device-id.png)

> [!NOTE]
> Um certificado será solicitado de um usuário apenas se a sessão corresponder a uma política que use o filtro de certificado do cliente válido.

### <a name="compliant-and-domain-joined-devices"></a>Dispositivos em conformidade e ingressados em domínio

O acesso condicional do Azure AD permite que informações do dispositivo em conformidade e ingressado em domínio sejam passadas diretamente para o Microsoft Cloud App Security. Nele, uma política de acesso ou de sessão que usa o estado do dispositivo como filtro pode ser desenvolvida. Para obter mais informações, consulte a [Introdução ao gerenciamento de dispositivos no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/device-management-introduction).

> [!NOTE]
> Some browsers may require additional configuration such as installing an extension. For more information, see [Conditional Access browser support](https://go.microsoft.com/fwlink/?linkid=2102732).

### <a name="client-certificate-authenticated-devices"></a>Dispositivos autenticados por certificado do cliente

O mecanismo de identificação de dispositivos pode solicitar autenticação de dispositivos relevantes usando certificados do cliente. Você pode usar certificados existentes do cliente já implantados em sua organização ou distribuir novos certificados do cliente para dispositivos gerenciados. Você usa a presença desses certificados para definir políticas de acesso e de sessão.

SSL client certificates are verified via a trust chain. You can upload an X.509 root or intermediate certificate authority (CA) formatted in the PEM certificate format. These certificates must contain the public key of the CA, which is then used to sign the client certificates presented during a session.

Once the certificate is uploaded and a relevant policy is configured, when an applicable session traverses Conditional Access App Control, the Cloud App Security endpoint requests the browser to present the SSL client certificates. The browser serves the SSL client certificates that are installed with a private key. This combination of certificate and private key is done by using the PKCS #12 file format, typically .p12 or .pfx.

When a client certificate check is performed, Cloud App Security checks for the following conditions:

1. The selected client certificate is valid and is under the correct root or intermediate CA.
1. The certificate is not revoked (if CRL is enabled).

> [!NOTE]
> Most major browsers support performing a client certificate check. However, mobile and desktop apps often leverage built-in browsers that may not support this check and therefore affect authentication for these apps.

Saiba mais sobre como implantar certificados do cliente em [Implantar Controle de Aplicativo de Acesso Condicional para aplicativos do Azure AD](proxy-deployment-aad.md).

## <a name="supported-apps-and-clients"></a>Clientes e aplicativos compatíveis

Conditional Access App Control currently supports SAML and Open ID Connect apps configured with single sign-on, along with web apps hosted on-premises configured with the [Azure AD App Proxy](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy).
> [!NOTE]
> O Controle de Aplicativos de Acesso Condicional também é compatível com aplicativos configurados com outros provedores de identidade além do Azure AD. Para obter mais informações sobre esse cenário, envie um email para mcaspreview@microsoft.com.

**O controle de sessão está disponível para todos os navegadores, nas principais plataformas e em todos os sistemas operacionais**. We recommend using Internet Explorer 11, Microsoft Edge (latest), Google Chrome (latest), Mozilla Firefox (latest), or Apple Safari (latest). Access to mobile and desktop apps can also be blocked or allowed.

> [!NOTE]
> Using the **Client app** filter in access policies can cause the resulting user session to be proxied by Cloud App Security.
>
> In access policies, when using the **Client app** filter it defaults to **Mobile and desktop**. This can cause the resulting user session to be proxied by Cloud App Security. To void this behavior, set the value to **Browser**.
>
> By default, evaluating whether an app is mobile or desktop can cause the resulting user session to be proxied by Cloud App Security. To avoid this behavior, set the Client App filter in your Access policies to be equal to **Browser**.

> [!NOTE]
> O Cloud App Security usa protocolos TLS 1.2+ para fornecer a melhor criptografia do setor. Aplicativos cliente nativos e navegadores que não são compatíveis com TLS 1.2+ não estarão acessíveis quando configurados com controle de sessão. No entanto, aplicativos SaaS que usam TLS 1.1 ou inferior aparecerão no navegador como usando TLS 1.2+ quando configurados com o Cloud App Security.

<a name="featured-apps"></a>By natively integrating with Azure AD, any app that is configured with SAML or Open ID Connect you can onboard any app yourself. In addition, the following apps are featured by Cloud App Security and are already onboarded and ready to use in any tenant:

- AWS
- Azure DevOps (Visual Studio Team Services)
- Portal do Azure (versão prévia)
- Caixa
- Concur
- CornerStone on Demand
- DocuSign
- Dropbox
- Dynamics 365 CRM (preview)
- Egnyte
- Exchange Online
- G Suite
- GitHub
- HighQ
- JIRA/Confluence
- OneDrive for Business
- LinkedIn Learning
- Power BI
- Salesforce
- ServiceNow
- SharePoint online
- Slack
- Tableau
- Microsoft Teams (versão prévia)
- Workday
- Workiva
- Workplace by Facebook
- Yammer (versão prévia)

### <a name="a-ido365-apps-office-365-featured-apps"></a><a id="O365-apps" />Office 365 featured apps

The following is a list of featured apps that are supported in Office 365 Cloud App Security:

- Exchange Online
- OneDrive for Business
- Power BI
- SharePoint online
- Microsoft Teams (versão prévia)
- Yammer (versão prévia)

If you're interested in a specific app being featured, [send us details about the app](mailto:casfeedback@microsoft.com). Envie o caso de uso em que você está interessado para integrá-lo.

> [!div class="step-by-step"]
> [PRÓXIMO: Implantar o Controle de Aplicativo de Acesso Condicional »](proxy-deployment-aad.md)

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Implantar o controle de aplicativo de acesso condicional para aplicativos do Azure AD](proxy-deployment-aad.md)

[!INCLUDE [Open support ticket](includes/support.md)]

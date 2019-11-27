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
> Para usar Cloud App Security Controle de Aplicativos de Acesso Condicional, você precisa de uma [licença Azure Active Directory P1](https://azure.microsoft.com/pricing/details/active-directory/)e uma assinatura do Active Microsoft Cloud app Security ou licença do Office 365 e5. Para obter uma lista de aplicativos em destaque incluídos no Office 365 e5, consulte [aplicativos em destaque do office 365](#O365-apps).

Licença do Office 365 e5. Para obter uma lista de aplicativos incluídos com o Office 365 E5 com suporte, consulte aplicativos em destaque do Office 365

## <a name="how-it-works"></a>Como funciona

Controle de Aplicativos de Acesso Condicional usa uma arquitetura de proxy reverso e é exclusivamente integrado ao acesso condicional do Azure AD. O acesso condicional do Azure AD permite que você aplique controles de acesso nos aplicativos da sua organização com base em determinadas condições. As condições definem a *quem* (usuário ou grupo de usuários), a *quais* (quais aplicativos de nuvem) e *onde* (quais locais e redes) uma política de acesso condicional é aplicada. Depois de determinar as condições, é possível encaminhar os usuários ao Microsoft Cloud App Security para proteger dados com o Controle de Aplicativos de Acesso Condicional, aplicando controles de acesso e de sessão.

O Controle de Aplicativo de Acesso Condicional permite o monitoramento e controle em tempo real do acesso e das sessões do aplicativo com base nas políticas de acesso e de sessão. As políticas de acesso e de sessão são utilizadas dentro do portal do Cloud App Security para refinar ainda mais os filtros e definir as ações a serem executadas em relação a um usuário. Com as políticas de acesso e de sessão, é possível:

- **Impedir vazamento de dados**: você pode bloquear o download, recortar, copiar e imprimir documentos confidenciais em, por exemplo, dispositivos não gerenciados.

- **Proteger no download**: em vez de bloquear o download de documentos confidenciais, você pode exigir que os documentos sejam rotulados e protegidos com a proteção de informações do Azure. Essa ação garante que o documento esteja protegido e o acesso do usuário seja restrito em uma sessão potencialmente arriscada.

- **Impedir o carregamento de arquivos sem rótulo**: antes de um arquivo confidencial ser carregado, distribuído e usado por outros, é importante certificar-se de que o arquivo tem o rótulo e a proteção corretos. Você pode garantir que arquivos sem rótulo com conteúdo confidencial sejam impedidos de serem carregados até que o usuário classificar o conteúdo.

- **Monitorar sessões de usuário para fins de conformidade**: os usuários arriscados são monitorados quando entram em aplicativos e suas ações são registradas de dentro da sessão. É possível investigar e analisar o comportamento do usuário para compreender onde e sob quais condições as políticas de sessão deverão ser aplicadas no futuro.

- **Bloquear o acesso**: você pode bloquear o acesso de maneira granular para aplicativos e usuários específicos, dependendo de vários fatores de risco. Por exemplo, você pode bloqueá-los se eles estiverem usando certificados de cliente como uma forma de gerenciamento de dispositivo.

- **Bloquear atividades personalizadas**: alguns aplicativos têm cenários exclusivos que trazem risco, por exemplo, enviar mensagens com conteúdo confidencial em aplicativos como equipes da Microsoft ou margem de atraso. Nesses tipos de cenários, você pode verificar mensagens quanto ao conteúdo confidencial e bloqueá-los em tempo real.

### <a name="how-session-control-works"></a>Como funciona o controle de sessão

A criação de uma política de sessão com Controle de Aplicativo de Acesso Condicional permite que você controle as sessões do usuário, redirecionando-o por meio de um proxy reverso, em vez de diretamente para o aplicativo. A partir de então, as solicitações e respostas do usuário passam por Cloud App Security em vez de diretamente para o aplicativo.

Quando uma sessão é protegida por proxy, todas as URLs e cookies relevantes são substituídos por Cloud App Security. Por exemplo, se o aplicativo retornar uma página com links cujos domínios terminam com myapp.com, o link será substituído por domínios que terminam com algo como: myapp.com.us.cas.ms

Esse método não exige que você instale nada no dispositivo, tornando-o ideal ao monitorar ou controlar sessões de dispositivos não gerenciados ou de usuários de parceiros.

> [!NOTE]
> O Cloud App Security aproveita os data centers do Azure em todo o mundo para fornecer desempenho otimizado por meio de geolocalização. Isso significa que uma sessão de usuário pode ser hospedada fora de uma região específica, dependendo dos padrões de tráfego e da localização. No entanto, para proteger sua privacidade, nenhum dado de sessão é armazenado nesses data centers.

## <a name="managed-device-identification"></a>Identificação do dispositivo gerenciado

O Controle de Aplicativo de Acesso Condicional permite que você crie políticas que levam em conta se um dispositivo é gerenciado ou não. Para identificar se um dispositivo é gerenciado ou não, o recurso usa:

- Dispositivos em conformidade
- Dispositivos ingressados em domínio
- Implantação de certificados do cliente

Para configurar uma política para aproveitar o gerenciamento de dispositivos por meio de certificados de cliente:

1. Vá até a engrenagem de configurações e selecione **Identificação de dispositivo**.
1. Carregue um ou mais certificados raiz ou intermediários.
1. Depois que o certificado for carregado, você poderá criar [políticas de acesso](access-policy-aad.md) e políticas de [sessão](session-policy-aad.md) com base na **marca do dispositivo** e no **certificado de cliente válido**.

    ![ID do dispositivo do Controle de Aplicativos de Acesso Condicional](./media/caac-device-id.png)

> [!NOTE]
> Um certificado será solicitado de um usuário apenas se a sessão corresponder a uma política que use o filtro de certificado do cliente válido.

### <a name="compliant-and-domain-joined-devices"></a>Dispositivos em conformidade e ingressados em domínio

O acesso condicional do Azure AD permite que informações do dispositivo em conformidade e ingressado em domínio sejam passadas diretamente para o Microsoft Cloud App Security. Nele, uma política de acesso ou de sessão que usa o estado do dispositivo como filtro pode ser desenvolvida. Para obter mais informações, consulte a [Introdução ao gerenciamento de dispositivos no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/device-management-introduction).

> [!NOTE]
> Alguns navegadores podem exigir configuração adicional, como a instalação de uma extensão. Para obter mais informações, consulte [suporte ao navegador de acesso condicional](https://go.microsoft.com/fwlink/?linkid=2102732).

### <a name="client-certificate-authenticated-devices"></a>Dispositivos autenticados por certificado do cliente

O mecanismo de identificação de dispositivos pode solicitar autenticação de dispositivos relevantes usando certificados do cliente. Você pode usar certificados existentes do cliente já implantados em sua organização ou distribuir novos certificados do cliente para dispositivos gerenciados. Você usa a presença desses certificados para definir políticas de acesso e de sessão.

Os certificados de cliente SSL são verificados por meio de uma cadeia de confiança. Você pode carregar uma raiz do X. 509 ou AC (autoridade de certificação) intermediária formatada no formato de certificado PEM. Esses certificados devem conter a chave pública da autoridade de certificação, que é usada para assinar os certificados de cliente apresentados durante uma sessão.

Depois que o certificado é carregado e uma política relevante é configurada, quando uma sessão aplicável atravessa Controle de Aplicativos de Acesso Condicional, o ponto de extremidade de Cloud App Security solicita que o navegador apresente os certificados de cliente SSL. O navegador serve os certificados de cliente SSL que são instalados com uma chave privada. Essa combinação de certificado e chave privada é feita usando o formato de arquivo PKCS #12, normalmente. p12 ou. pfx.

Quando uma verificação de certificado de cliente é executada, o Cloud App Security verifica as seguintes condições:

1. O certificado de cliente selecionado é válido e está na autoridade de certificação raiz ou intermediária correta.
1. O certificado não é revogado (se a CRL estiver habilitada).

> [!NOTE]
> A maioria dos principais navegadores dá suporte à execução de uma verificação de certificado de cliente. No entanto, os aplicativos móveis e de desktop geralmente aproveitam os navegadores internos que podem não dar suporte a essa verificação e, portanto, afetam a autenticação para esses aplicativos.

Saiba mais sobre como implantar certificados do cliente em [Implantar Controle de Aplicativo de Acesso Condicional para aplicativos do Azure AD](proxy-deployment-aad.md).

## <a name="supported-apps-and-clients"></a>Clientes e aplicativos compatíveis

O Controle de Aplicativos de Acesso Condicional atualmente dá suporte a aplicativos SAML e Open ID Connect configurados com logon único, juntamente com aplicativos Web hospedados localmente configurados com o [proxy de aplicativo Azure ad](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy).
> [!NOTE]
> O Controle de Aplicativos de Acesso Condicional também é compatível com aplicativos configurados com outros provedores de identidade além do Azure AD. Para obter mais informações sobre esse cenário, envie um email para mcaspreview@microsoft.com.

**O controle de sessão está disponível para todos os navegadores, nas principais plataformas e em todos os sistemas operacionais**. É recomendável usar o Internet Explorer 11, o Microsoft Edge (mais recente), o Google Chrome (mais recente), o Mozilla Firefox (mais recente) ou o Apple Safari (mais recente). O acesso a aplicativos móveis e de área de trabalho também pode ser bloqueado ou permitido.

> [!NOTE]
> Usar o filtro de **aplicativo cliente** nas políticas de acesso pode fazer com que a sessão de usuário resultante seja modificada por Cloud app Security.
>
> Em políticas de acesso, ao usar o filtro de **aplicativo cliente** , ele assume como padrão a **mobilidade e a área de trabalho**. Isso pode fazer com que a sessão de usuário resultante seja modificada por um Cloud App Security. Para anular esse comportamento, defina o valor como **navegador**.
>
> Por padrão, avaliar se um aplicativo é móvel ou a área de trabalho pode fazer com que a sessão de usuário resultante seja modificada por Cloud App Security. Para evitar esse comportamento, defina o filtro de aplicativo cliente em suas políticas de acesso como sendo igual ao **navegador**.

> [!NOTE]
> O Cloud App Security usa protocolos TLS 1.2+ para fornecer a melhor criptografia do setor. Aplicativos cliente nativos e navegadores que não são compatíveis com TLS 1.2+ não estarão acessíveis quando configurados com controle de sessão. No entanto, aplicativos SaaS que usam TLS 1.1 ou inferior aparecerão no navegador como usando TLS 1.2+ quando configurados com o Cloud App Security.

<a name="featured-apps"></a>Ao integrar nativamente com o Azure AD, qualquer aplicativo configurado com SAML ou Open ID Connect você pode integrar qualquer aplicativo por conta própria. Além disso, os aplicativos a seguir são apresentados por Cloud App Security e já estão integrados e prontos para uso em qualquer locatário:

- AWS
- Azure DevOps (Visual Studio Team Services)
- Portal do Azure (versão prévia)
- Caixa
- Concur
- CornerStone on Demand
- DocuSign
- Dropbox
- Dynamics 365 CRM (versão prévia)
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
- SharePonot Onlnoe
- Slack
- Tableau
- Microsoft Teams (versão prévia)
- Workday
- Workiva
- Workplace by Facebook
- Yammer (versão prévia)

### <a name="a-ido365-apps-office-365-featured-apps"></a><a id="O365-apps" />aplicativos em destaque do Office 365

Veja a seguir uma lista de aplicativos em destaque com suporte no Office 365 Cloud App Security:

- Exchange Online
- OneDrive for Business
- Power BI
- SharePonot Onlnoe
- Microsoft Teams (versão prévia)
- Yammer (versão prévia)

Se você estiver interessado em um aplicativo específico em destaque, [envie-nos detalhes sobre o aplicativo](mailto:casfeedback@microsoft.com). Envie o caso de uso em que você está interessado para integrá-lo.

> [!div class="step-by-step"]
> [PRÓXIMO: Implantar o Controle de Aplicativo de Acesso Condicional »](proxy-deployment-aad.md)

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Implantar o controle de aplicativo de acesso condicional para aplicativos do Azure AD](proxy-deployment-aad.md)

[!INCLUDE [Open support ticket](includes/support.md)]

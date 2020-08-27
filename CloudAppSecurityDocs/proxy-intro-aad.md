---
title: Proteger aplicativos com o Controle de Aplicativos de Acesso Condicional do Microsoft Cloud App Security
description: Este artigo fornece informações sobre como funciona o proxy reverso do Controle de Aplicativos de Acesso Condicional do Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 07/09/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: a1d6abfc92a1678f954c4a332dc4c7e5e82536b8
ms.sourcegitcommit: 870ca47381a36b4bc04e1ccb9b2a522944431fed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88963957"
---
# <a name="protect-apps-with-microsoft-cloud-app-security-conditional-access-app-control"></a>Proteger aplicativos com o Controle de Aplicativo de Acesso Condicional do Microsoft Cloud App Security

*Aplica-se a: Microsoft Cloud App Security*

No local de trabalho atual, geralmente não é suficiente saber o que está acontecendo em seu ambiente de nuvem após o fato. Você deseja interromper violações e vazamentos em tempo real antes que os funcionários intencional ou inadvertidamente coloquem seus dados e sua organização em risco. É importante permitir que os usuários em sua organização disponibilizem o máximo dos serviços e ferramentas disponíveis para eles em aplicativos de nuvem e permitem que eles tragam seus próprios dispositivos para funcionarem. Ao mesmo tempo, são necessárias ferramentas para ajudar a proteger sua organização contra vazamentos de dados e roubo de dados, em tempo real. O Microsoft Cloud App Security integra-se com qualquer provedor de identidade (IdP) para fornecer esses recursos com controles de acesso e sessão. Se você estiver usando o Azure Active Directory (Azure AD) como seu IdP, esses controles serão integrados e simplificados para uma implantação mais simples e mais personalizada criada na ferramenta de [acesso condicional](/azure/active-directory/conditional-access/overview)do Azure AD.

> [!NOTE]
>
> - Para usar Cloud App Security Controle de Aplicativos de Acesso Condicional, você precisa de uma [licença Azure Active Directory P1](https://azure.microsoft.com/pricing/details/active-directory/)ou a licença exigida por sua solução IDP, bem como uma licença de Cloud app Security.

## <a name="how-it-works"></a>Como ele funciona

Controle de Aplicativos de Acesso Condicional usa uma arquitetura de proxy reverso e se integra ao IdP. Ao integrar com o acesso condicional do Azure AD, você pode configurar aplicativos para trabalhar com Controle de Aplicativos de Acesso Condicional com apenas alguns cliques, permitindo que você imponha de forma fácil e seletiva os controles de acesso e de sessão nos aplicativos da sua organização com base em qualquer condição no acesso condicional. As condições definem *quem* (usuário ou grupo de usuários) e *o que* (quais aplicativos de nuvem) e *onde* (quais locais e redes) uma política de acesso condicional é aplicada. Depois de determinar as condições, você pode encaminhar os usuários para Cloud App Security em que você pode proteger dados com Controle de Aplicativos de Acesso Condicional aplicando controles de acesso e sessão.

O Controle de Aplicativo de Acesso Condicional permite o monitoramento e controle em tempo real do acesso e das sessões do aplicativo com base nas políticas de acesso e de sessão. As políticas de acesso e de sessão são utilizadas dentro do portal do Cloud App Security para refinar ainda mais os filtros e definir as ações a serem executadas em relação a um usuário. Com as políticas de acesso e de sessão, é possível:

- **Impedir vazamento de dados**: você pode bloquear o download, recortar, copiar e imprimir documentos confidenciais em, por exemplo, dispositivos não gerenciados.

- **Proteger no download**: em vez de bloquear o download de documentos confidenciais, você pode exigir que os documentos sejam rotulados e protegidos com a proteção de informações do Azure. Essa ação garante que o documento esteja protegido e o acesso do usuário seja restrito em uma sessão potencialmente arriscada.

- **Impedir o carregamento de arquivos sem rótulo**: antes de um arquivo confidencial ser carregado, distribuído e usado por outros, é importante certificar-se de que o arquivo tem o rótulo e a proteção corretos. Você pode garantir que arquivos sem rótulo com conteúdo confidencial sejam impedidos de serem carregados até que o usuário classificar o conteúdo.

- **Bloquear possíveis malwares**: você pode proteger seu ambiente contra malware bloqueando o upload de arquivos potencialmente mal-intencionados. Qualquer arquivo carregado ou baixado pode ser verificado em relação à inteligência contra ameaças da Microsoft e bloqueado instantaneamente.

- **Monitorar sessões de usuário para fins de conformidade**: os usuários arriscados são monitorados quando entram em aplicativos e suas ações são registradas de dentro da sessão. É possível investigar e analisar o comportamento do usuário para compreender onde e sob quais condições as políticas de sessão deverão ser aplicadas no futuro.

- **Bloquear o acesso**: você pode bloquear o acesso de maneira granular para aplicativos e usuários específicos, dependendo de vários fatores de risco. Por exemplo, você pode bloqueá-los se eles estiverem usando certificados de cliente como uma forma de gerenciamento de dispositivo.

- **Bloquear atividades personalizadas**: alguns aplicativos têm cenários exclusivos que trazem risco, por exemplo, enviar mensagens com conteúdo confidencial em aplicativos como equipes da Microsoft ou margem de atraso. Nesses tipos de cenários, você pode verificar mensagens quanto ao conteúdo confidencial e bloqueá-los em tempo real.

### <a name="how-session-control-works"></a>Como funciona o controle de sessão

A criação de uma política de sessão com Controle de Aplicativo de Acesso Condicional permite que você controle as sessões do usuário, redirecionando-o por meio de um proxy reverso, em vez de diretamente para o aplicativo. A partir de então, as solicitações e respostas do usuário passam por Cloud App Security em vez de diretamente para o aplicativo.

Quando uma sessão é protegida por proxy, todas as URLs e cookies relevantes são substituídos por Cloud App Security. Por exemplo, se o aplicativo retornar uma página com links cujos domínios terminem com `myapp.com` , o domínio do link será sufixado com algo como `*.mcas.ms` , da seguinte maneira:

|URL do aplicativo|URL substituída|
|---|---|
|`myapp.com`|`myapp.com.mcas.ms`|

Esse método não exige que você instale nada no dispositivo, tornando-o ideal ao monitorar ou controlar sessões de dispositivos não gerenciados ou de usuários de parceiros.

> [!NOTE]
>
> - Nossa tecnologia usa a melhor heurística patenteada de classe para identificar e controlar atividades executadas pelo usuário no aplicativo de destino. Nossa heurística foi projetada para otimizar e balancear a segurança com usabilidade. Em alguns cenários raros, quando as atividades de bloqueio no lado do servidor renderizam o aplicativo inutilizável, protegemos essas atividades somente no lado do cliente, o que as torna potencialmente suscetíveis à exploração por pessoas mal-intencionadas.
> - O Cloud App Security aproveita os data centers do Azure em todo o mundo para fornecer desempenho otimizado por meio de geolocalização. Isso significa que a sessão de um usuário pode ser hospedada fora de uma região específica, dependendo dos padrões de tráfego e da localização. No entanto, para proteger sua privacidade, nenhum dado de sessão é armazenado nesses data centers.
> - Nossos servidores proxy não armazenam dados em repouso. Ao armazenar o conteúdo em cache, seguimos os requisitos dispostos no [RFC 7234 (cache http)](https://tools.ietf.org/html/rfc7234) e apenas o conteúdo público do cache.

## <a name="managed-device-identification"></a>Identificação do dispositivo gerenciado

O Controle de Aplicativos de Acesso Condicional permite que você crie políticas que levam em conta se um dispositivo é gerenciado ou não. Para identificar o estado de um dispositivo, você pode configurar políticas de acesso e sessão para verificar:

- Microsoft Intune dispositivos em conformidade [disponível somente com o Azure AD]
- Dispositivos adicionados ao Azure Active Directory híbrido [disponível somente com o Azure AD]
- Presença de certificados doe cliente em uma cadeia confiável

### <a name="intune-compliant-and-hybrid-azure-ad-joined-devices"></a>Dispositivos ingressados no Azure AD híbrido e em conformidade com o Intune

O acesso condicional do Azure AD permite que as informações do dispositivo associado ao Azure AD híbrido e em conformidade com o Intune sejam passadas diretamente para Cloud App Security. Nele, uma política de acesso ou de sessão que usa o estado do dispositivo como filtro pode ser desenvolvida. Para obter mais informações, consulte a [introdução ao gerenciamento de dispositivos no Azure Active Directory](/azure/active-directory/device-management-introduction).

> [!NOTE]
> Alguns navegadores podem exigir configuração adicional, como a instalação de uma extensão. Para obter mais informações, consulte [suporte ao navegador de acesso condicional](https://go.microsoft.com/fwlink/?linkid=2102732).

### <a name="client-certificate-authenticated-devices"></a>Dispositivos autenticados por certificado do cliente

O mecanismo de identificação de dispositivos pode solicitar autenticação de dispositivos relevantes usando certificados do cliente. Você pode usar certificados existentes do cliente já implantados em sua organização ou distribuir novos certificados do cliente para dispositivos gerenciados. Verifique se o certificado do cliente está instalado no repositório do usuário e não no repositório do computador. Você usa a presença desses certificados para definir políticas de acesso e de sessão.

Os certificados de cliente SSL são verificados por meio de uma cadeia de confiança. Você pode carregar uma raiz do X. 509 ou AC (autoridade de certificação) intermediária formatada no formato de certificado PEM. Esses certificados devem conter a chave pública da autoridade de certificação, que é usada para assinar os certificados de cliente apresentados durante uma sessão.

Depois que o certificado é carregado e uma política relevante é configurada, quando uma sessão aplicável atravessa Controle de Aplicativos de Acesso Condicional, o ponto de extremidade de Cloud App Security solicita que o navegador apresente os certificados de cliente SSL. O navegador serve os certificados de cliente SSL que são instalados com uma chave privada. Essa combinação de certificado e chave privada é feita usando o formato de arquivo PKCS #12, normalmente. p12 ou. pfx.

Quando uma verificação de certificado de cliente é executada, o Cloud App Security verifica as seguintes condições:

1. O certificado de cliente selecionado é válido e está na autoridade de certificação raiz ou intermediária correta.
1. O certificado não é revogado (se a CRL estiver habilitada).

> [!NOTE]
>
> A maioria dos principais navegadores dá suporte à execução de uma verificação de certificado de cliente. No entanto, os aplicativos móveis e de desktop geralmente aproveitam os navegadores internos que podem não dar suporte a essa verificação e, portanto, afetam a autenticação para esses aplicativos.

Para configurar uma política para aproveitar o gerenciamento de dispositivos por meio de certificados de cliente:

1. No Cloud App Security, na barra de menus, clique no ícone configurações engrenagem ![configurações](media/settings-icon.png "Ícone de configurações") e selecione **configurações**.

1. Selecione a guia **identificação do dispositivo** .
1. Carregue quantos certificados raiz ou intermediários forem necessários.

    > [!TIP]
    > Para testar como isso funciona, você pode usar nosso CA raiz de exemplo e certificado de cliente, da seguinte maneira:
    >
    > 1. Baixe o [certificado de cliente](https://github.com/microsoft/Microsoft-Cloud-App-Security/blob/master/Doc%20Assets/Proxy/Samples/SampleClientCert.pfx)e a [AC raiz](https://github.com/microsoft/Microsoft-Cloud-App-Security/blob/master/Doc%20Assets/Proxy/Samples/SampleRootCA.crt.pem) de exemplo.
    > 1. Carregue a AC raiz para Cloud App Security.
    > 1. Instale o certificado do cliente (password = Microsoft) nos dispositivos relevantes.

Depois que os certificados forem carregados, você poderá criar políticas de acesso e sessão com base na **marca do dispositivo** e no **certificado de cliente válido**.

## <a name="supported-apps-and-clients"></a>Clientes e aplicativos compatíveis

Controles de sessão e de acesso podem ser aplicados a qualquer logon único interativo, usando o protocolo de autenticação SAML 2,0 ou, se você estiver usando o Azure AD, o protocolo de autenticação Open ID Connect também. Além disso, se seus aplicativos estiverem configurados com o Azure AD, você também poderá aplicar esses controles a aplicativos hospedados localmente configurados com o [proxy de aplicativo Azure ad](/azure/active-directory/manage-apps/application-proxy). Além disso, os controles de acesso podem ser aplicados a aplicativos cliente móveis e de desktop nativos.

Cloud App Security identifica aplicativos usando as informações disponíveis em seu catálogo de aplicativos de nuvem. Algumas organizações e usuários personalizam aplicativos adicionando plug-ins. No entanto, para que os controles de sessão funcionem corretamente com esses plug-ins, os domínios personalizados associados devem ser adicionados ao respectivo aplicativo no catálogo.

> [!NOTE]
> O aplicativo Authenticator, entre outros fluxos de entrada do aplicativo cliente nativo, usa um fluxo de entrada não interativo e não pode ser usado com controles de acesso.

### <a name="access-controls"></a>Controles de acesso

Muitas organizações que optam por usar controles de sessão para aplicativos de nuvem para controlar as atividades na sessão, também aplicam controles de acesso para bloquear o mesmo conjunto de aplicativos de cliente móvel e de desktop nativos, fornecendo, assim, segurança abrangente para os aplicativos.

Você pode bloquear o acesso a aplicativos cliente móveis nativos e de desktop com políticas de acesso, definindo o filtro de **aplicativo cliente** como **móvel e área de trabalho**. Alguns aplicativos cliente nativos podem ser reconhecidos individualmente, enquanto outros que fazem parte de um pacote de aplicativos só podem ser identificados como seu aplicativo de nível superior. Por exemplo, aplicativos como o SharePoint Online só podem ser reconhecidos pela criação de uma política de acesso aplicada aos aplicativos do Office 365.

> [!NOTE]
> A menos que o filtro de **aplicativo cliente** seja definido especificamente como **móvel e área de trabalho**, a política de acesso resultante só se aplicará a sessões do navegador. O motivo para isso é evitar a proxy inadvertidamente de sessões de usuário, o que pode ser um subproduto do uso desse filtro. Embora a maioria dos principais navegadores dê suporte à execução de uma verificação de certificado de cliente, alguns aplicativos móveis e de área de trabalho usam navegadores internos que podem não dar suporte a essa verificação. Portanto, o uso desse filtro pode afetar a autenticação para esses aplicativos.

### <a name="session-controls"></a>Controles de sessão

Embora os controles de sessão sejam criados para funcionar com qualquer navegador em qualquer plataforma principal em qualquer sistema operacional, damos suporte ao [Microsoft Edge](https://www.microsoft.com/edge) (mais recente), ao Google Chrome (mais recente), ao Mozilla Firefox (mais recente) ou ao Apple Safari (mais recente). O acesso a aplicativos móveis e de área de trabalho também pode ser bloqueado ou permitido.

> [!NOTE]
>
> - O Cloud app Security aproveita os protocolos do protocolo TLS 1.2 + para fornecer a melhor criptografia de classe. Aplicativos cliente nativos e navegadores que não dão suporte a TLS 1.2 +, não estarão acessíveis quando configurados com controle de sessão. No entanto, aplicativos SaaS que usam TLS 1.1 ou inferior aparecerão no navegador como usando TLS 1.2+ quando configurados com o Cloud App Security.
> - Para aplicar controles de sessão ao portal.office.com, você deve integrar Microsoft Office centro de administração 365. Para obter mais informações sobre aplicativos de integração, consulte [integração e implantação controle de aplicativos de acesso condicional para qualquer aplicativo](proxy-deployment-any-app.md).

<a name="featured-apps"></a>Qualquer aplicativo Web configurado usando os [protocolos de autenticação mencionados anteriormente](#supported-apps-and-clients) pode ser integrado para trabalhar com controles de acesso e de sessão. Além disso, os aplicativos a seguir são apresentados por Cloud App Security e já estão integrados e prontos para uso em qualquer locatário:

- AWS
- Azure DevOps (Visual Studio Team Services)
- Portal do Azure (versão prévia)
- Box
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
- SharePoint online
- Margem de atraso
- Tableau
- Microsoft Teams (versão prévia)
- Workday
- Workiva
- Workplace by Facebook
- Yammer (versão prévia)

### <a name="office-365-featured-apps"></a><a name="O365-apps"></a>Aplicativos em destaque do Office 365

Veja a seguir uma lista de aplicativos em destaque com suporte no Office 365 Cloud App Security. Para usar esses aplicativos com Cloud App Security, você deve ter uma licença do Office 365 e5.

- Exchange Online
- OneDrive for Business
- Power BI
- SharePoint online
- Microsoft Teams (versão prévia)
- Yammer (versão prévia)

Se você estiver interessado em um aplicativo específico em destaque, [envie-nos detalhes sobre o aplicativo](mailto:casfeedback@microsoft.com). Lembre-se de enviar o caso de uso no qual você está interessado para fazer a integração.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Implantar o Controle de Aplicativo de Acesso Condicional para aplicativos em destaque](proxy-deployment-aad.md)

> [!div class="nextstepaction"]
> [Implantar Controle de Aplicativos de Acesso Condicional para qualquer aplicativo](proxy-deployment-any-app.md)

> [!div class="nextstepaction"]
> [Solução de problemas de controles de acesso e de sessão](troubleshooting-proxy.md)

[!INCLUDE [Open support ticket](includes/support.md)]
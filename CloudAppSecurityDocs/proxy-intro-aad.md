---
title: Proteger aplicativos com o Controle de Aplicativos de Acesso Condicional do Microsoft Cloud App Security
description: Este artigo fornece informações sobre como funciona o proxy reverso do Controle de Aplicativos de Acesso Condicional do Cloud App Security.
keywords: ''
author: ShlomoSagir-MS
ms.author: shsagir
manager: ShlomoSagir-MS
ms.date: 7/2/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 35a43120-bf67-4cf9-9b48-ebe157dbbd18
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: fca34e1bb6a9f83928ef3a4eaf388090468ce06a
ms.sourcegitcommit: ee00e0033bf45a5f795bfd3e1d71fa1f70f97acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67511353"
---
# <a name="protect-apps-with-microsoft-cloud-app-security-conditional-access-app-control"></a>Proteger aplicativos com o Controle de Aplicativo de Acesso Condicional do Microsoft Cloud App Security

*Aplica-se a: Microsoft Cloud App Security*

>[!div class="step-by-step"]
[PRÓXIMO: Implantar o Controle de Aplicativos de Acesso Condicional »](proxy-deployment-aad.md)

No espaço de trabalho de hoje, muitas vezes não é suficiente saber o que está acontecendo em seu ambiente de nuvem após o fato. Você deseja interromper violações e vazamentos em tempo real antes que os funcionários intencional ou inadvertidamente coloquem seus dados e sua organização em risco. É importante permitir que os usuários em sua organização aproveitem ao máximo os serviços e as ferramentas disponíveis a eles em aplicativos de nuvem e que eles tragam os próprios dispositivos para o trabalho. Ao mesmo tempo, são necessárias ferramentas para ajudar a proteger sua organização contra vazamentos de dados e roubo de dados, em tempo real. Juntamente com o Azure Active Directory, o Microsoft Cloud App Security oferece esses recursos em uma experiência holística e integrada com o Controle de Aplicativo de Acesso Condicional.

> [!NOTE]
> Para usar o Controle de Aplicativos de Acesso Condicional do Cloud App Security, é necessária uma [licença P1 do Azure Active Directory](https://azure.microsoft.com/pricing/details/active-directory/) e uma assinatura ativa do Microsoft Cloud App Security.
>

## <a name="how-it-works"></a>Como funciona

Controle de Aplicativos de Acesso Condicional usa uma arquitetura de proxy reverso e é exclusivamente integrado ao acesso condicional do Azure AD. O acesso condicional do Azure AD permite que você aplique controles de acesso nos aplicativos da sua organização com base em determinadas condições. As condições definem a *quem* (usuário ou grupo de usuários), a *quais* (quais aplicativos de nuvem) e *onde* (quais locais e redes) uma política de acesso condicional é aplicada. Depois de determinar as condições, é possível encaminhar os usuários ao Microsoft Cloud App Security para proteger dados com o Controle de Aplicativos de Acesso Condicional, aplicando controles de acesso e de sessão.

O Controle de Aplicativo de Acesso Condicional permite o monitoramento e controle em tempo real do acesso e das sessões do aplicativo com base nas políticas de acesso e de sessão. As políticas de acesso e de sessão são utilizadas dentro do portal do Cloud App Security para refinar ainda mais os filtros e definir as ações a serem executadas em relação a um usuário. Com as políticas de acesso e de sessão, é possível:

- **Impedir o vazamento de dados**: Você pode bloquear o download, recortar, copiar e de impressão de documentos confidenciais em, por exemplo, os dispositivos não gerenciados.

- **Proteger download**: Em vez de bloquear o download de documentos confidenciais, você pode exigir documentos a ser rotulado e protegidos com a proteção de informações do Azure. Esta ação garante que o documento está protegido e o acesso do usuário é restrito em uma sessão potencialmente perigosa.

- **Impedir o carregamento de arquivos sem rótulo**: Antes de um arquivo confidencial é carregado, distribuído e usado por outras pessoas, é importante certificar-se de que o arquivo tem o rótulo à direita e a proteção. Você pode garantir que arquivos não rotulados com conteúdo confidencial estão bloqueados do que está sendo carregado até que o usuário classifica o conteúdo.

- **Monitorar sessões de usuário quanto à conformidade**: Os usuários de risco são monitorados quando entram nos aplicativos e suas ações são registradas na sessão. É possível investigar e analisar o comportamento do usuário para compreender onde e sob quais condições as políticas de sessão deverão ser aplicadas no futuro.

- **Bloquear o acesso**: Granularmente, você pode bloquear o acesso para usuários, dependendo de vários fatores de risco e aplicativos específicos. Por exemplo, você pode bloqueá-los se eles estão usando certificados de cliente como uma forma de gerenciamento de dispositivo.

- **Bloquear atividades personalizadas**: Alguns aplicativos têm cenários exclusivos que carregam o risco, por exemplo, enviar mensagens com conteúdo confidencial em aplicativos como o Microsoft Teams ou Slack. Esses tipos de cenários, você pode verificar mensagens para conteúdo confidencial e bloqueá-los em tempo real.

### <a name="how-session-control-works"></a>Como o controle de sessão funciona

A criação de uma política de sessão com Controle de Aplicativo de Acesso Condicional permite que você controle as sessões do usuário, redirecionando-o por meio de um proxy reverso, em vez de diretamente para o aplicativo. Daí em seguida diante, as solicitações do usuário e as respostas passam pelo Cloud App Security em vez de diretamente para o aplicativo.

Quando uma sessão é protegida pelo proxy, todas as URLs relevantes e os cookies são substituídos pelo Cloud App Security. Por exemplo, se o aplicativo retornar uma página com links cujos domínios terminam com myapp.com, o link será substituído por domínios que terminam com algo como: myapp.com.us.cas.ms

Esse método não exige que você instalar nada no dispositivo, tornando-o ideal ao monitorar ou controlar sessões de dispositivos não gerenciados ou os usuários do parceiro.

## <a name="managed-device-identification"></a>Identificação do dispositivo gerenciado

O Controle de Aplicativo de Acesso Condicional permite que você crie políticas que levam em conta se um dispositivo é gerenciado ou não. Para identificar se um dispositivo é gerenciado ou não, o recurso usa:

- Dispositivos em conformidade
- Dispositivos ingressados em domínio
- Implantação de certificados do cliente
 
### <a name="compliant-and-domain-joined-devices"></a>Dispositivos em conformidade e ingressados em domínio

O acesso condicional do Azure AD permite que informações do dispositivo em conformidade e ingressado em domínio sejam passadas diretamente para o Microsoft Cloud App Security. Nele, uma política de acesso ou de sessão que usa o estado do dispositivo como filtro pode ser desenvolvida.
Para obter mais informações, consulte a [Introdução ao gerenciamento de dispositivos no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/device-management-introduction). 

### <a name="client-certificate-authenticated-devices"></a>Dispositivos autenticados por certificado do cliente

O mecanismo de identificação de dispositivos pode solicitar autenticação de dispositivos relevantes usando certificados do cliente. Você pode usar certificados existentes do cliente já implantados em sua organização ou distribuir novos certificados do cliente para dispositivos gerenciados. Você usa a presença desses certificados para definir políticas de acesso e de sessão.

Certificados de cliente SSL são verificados por meio de uma cadeia de confiança. Você pode carregar uma raiz de x. 509 ou formatado no formato PEM de certificado de autoridade de certificação intermediária (CA). Esses certificados devem conter a chave pública da autoridade de certificação, que é usada para assinar os certificados de cliente apresentados durante uma sessão.

Depois que o certificado é carregado e uma política correspondente for configurada, quando uma sessão aplicável atravessa o controle de aplicativo de acesso condicional, o ponto de extremidade do Cloud App Security solicita o navegador para apresentar certificados de cliente SSL. O navegador serve o cliente SSL certificados que são instalados com uma chave privada. Essa combinação de certificado e chave privada é feita usando o PKCS n º 12 formato de arquivo, normalmente. p12 ou. pfx.

Quando é realizada uma verificação de certificado do cliente, o Cloud App Security verifica as condições a seguir:

1. O certificado do cliente selecionado é válido e está sob a AC intermediária ou raiz correta.
1. O certificado é revogado não (se a CRL é habilitada).

Saiba mais sobre como implantar certificados do cliente em [Implantar Controle de Aplicativo de Acesso Condicional para aplicativos do Azure AD](proxy-deployment-aad.md).

## <a name="supported-apps-and-clients"></a>Clientes e aplicativos compatíveis

O Controle de Aplicativos de Acesso Condicional atualmente dá suporte a aplicativos SAML e Open ID Connect configurados com logon único, juntamente com aplicativos Web hospedados localmente e configurados com o [Proxy de Aplicativo do Azure AD](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy).
> [!NOTE]
> O Controle de Aplicativos de Acesso Condicional também é compatível com aplicativos configurados com outros provedores de identidade além do Azure AD. Para obter mais informações sobre esse cenário, envie um email para mcaspreview@microsoft.com.

**O controle de sessão está disponível para todos os navegadores, nas principais plataformas e em todos os sistemas operacionais**. É recomendável usar o Internet Explorer 11, Microsoft Edge (mais recente), Google Chrome (mais recente), Mozilla Firefox (mais recente) ou Apple Safari (mais recente). Aplicativos móveis e aplicativos da área de trabalho também podem ser bloqueados ou permitidos. Com a integração nativa com o Azure AD, qualquer aplicativo que está configurado com SAML ou Open ID Connect pode ser integrado de autoatendimento. Além disso, os seguintes aplicativos em destaque do Cloud App Security e já estão integrados e prontos para uso em qualquer locatário:

- AWS
- Azure DevOps (Visual Studio Team Services)
- Portal do Azure (versão prévia)
- Caixa
- Concur
- CornerStone on Demand
- DocuSign
- Dropbox
- Dynamics 365 CRM (visualização)
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

Se você estiver interessado em um aplicativo específico que está sendo em destaque [envie-nos detalhes sobre o aplicativo](mailto:casfeedback@microsoft.com). Envie o caso de uso em que você está interessado para integrá-lo.

>[!div class="step-by-step"]
[PRÓXIMO: Implantar o Controle de Aplicativos de Acesso Condicional »](proxy-deployment-aad.md)

## <a name="next-steps"></a>Próximas etapas
[Implantar o controle de aplicativo de acesso condicional para aplicativos do Azure AD](proxy-deployment-aad.md)

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/)
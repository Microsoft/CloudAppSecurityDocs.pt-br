---
title: Proteger aplicativos com o Controle de Aplicativos de Acesso Condicional do Microsoft Cloud App Security
description: Este artigo fornece informações sobre como funciona o proxy reverso do Controle de Aplicativos de Acesso Condicional do Cloud App Security.
keywords: ''
author: ShlomoSagir-MS
ms.author: ShlomoSagir-MS
manager: ShlomoSagir-MS
ms.date: 06/04/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 35a43120-bf67-4cf9-9b48-ebe157dbbd18
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 0e1a48c5c139839b7999d8a36713adb22e37d957
ms.sourcegitcommit: a77d2ed241e6d9d99d296f99f073d31fec88b709
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66687553"
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

- **Bloquear download**: Bloqueie o download de documentos confidenciais. Por exemplo, em dispositivos não gerenciados.

- **Proteger download**: Em vez de bloquear o download de documentos confidenciais, exija que os documentos sejam protegidos por meio de criptografia no momento do download. Essa criptografia garante que o documento esteja protegido e que o acesso do usuário seja autenticado se os dados são baixados para um dispositivo não confiável. 

- **Monitorar sessões de usuário de baixa confiança**: Os usuários de risco são monitorados quando entram nos aplicativos e suas ações são registradas na sessão. É possível investigar e analisar o comportamento do usuário para compreender onde e sob quais condições as políticas de sessão deverão ser aplicadas no futuro. 

- **Bloquear o acesso**: Bloqueie o acesso por completo a aplicativos específicos de usuários provenientes de dispositivos não gerenciados ou de redes não corporativas.

- **Criar modo somente leitura**: Monitorando e bloqueando atividades personalizadas no aplicativo, você pode criar um modo somente leitura de aplicativos específicos para usuários específicos.  

- **Restringir sessões de usuário de redes não corporativas**: Os usuários que acessam um aplicativo protegido em uma localização que não faz parte da rede corporativa têm acesso restrito. O download de materiais confidenciais é bloqueado ou protegido.

### <a name="how-session-control-works"></a>Como funciona o controle de sessão

A criação de uma política de sessão com Controle de Aplicativo de Acesso Condicional permite que você controle as sessões do usuário, redirecionando-o por meio de um proxy reverso, em vez de diretamente para o aplicativo. Daí em diante, as solicitações do usuário e as respostas passam pelo Microsoft Cloud App Security em vez de diretamente para o aplicativo.

Para manter o usuário dentro da sessão, todas as URLs relevantes, os scripts Java e os cookies dentro da sessão do aplicativo são substituídos por URLs do Microsoft Cloud App Security. Por exemplo, se o aplicativo retornar uma página com links cujos domínios terminam com myapp.com, o link será substituído por domínios que terminam com algo como: myapp.com.us.cas.ms 

Este método não requer que você instale nada em seu dispositivo. Esse método é ideal ao monitorar sessões de dispositivos não gerenciados. 

Após o direcionamento de uma sessão pelo Microsoft Cloud App Security, é possível executar as seguintes ações:

1. Inspecionar as atividades de usuário do tráfego
2. Exibir as atividades identificadas no log de Atividades do Microsoft Cloud App Security
3. Salvar os logs de tráfego e analisá-los
4. Permitir que o administrador exporte os logs de tráfego
5. Aplicar políticas na sessão

## <a name="managed-device-identification"></a>Identificação do dispositivo gerenciado

O Controle de Aplicativo de Acesso Condicional permite que você crie políticas que levam em conta se um dispositivo é gerenciado ou não. Para identificar se um dispositivo é gerenciado ou não, o recurso usa:

- Dispositivos em conformidade
- Dispositivos ingressados em domínio
- Implantação de certificados do cliente
 
### <a name="compliant-and-domain-joined-devices"></a>Dispositivos em conformidade e ingressados em domínio

O acesso condicional do Azure AD permite que informações do dispositivo em conformidade e ingressado em domínio sejam passadas diretamente para o Microsoft Cloud App Security. Nele, uma política de acesso ou de sessão que usa o estado do dispositivo como filtro pode ser desenvolvida.
Para obter mais informações, consulte a [Introdução ao gerenciamento de dispositivos no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/device-management-introduction). 

### <a name="client-certificate-authenticated-devices"></a>Dispositivos autenticados por certificado do cliente

O mecanismo de identificação de dispositivos pode solicitar autenticação de dispositivos relevantes usando certificados do cliente. Você pode usar certificados existentes do cliente já implantados em sua organização ou distribuir novos certificados do cliente para dispositivos gerenciados. Você usa a presença desses certificados para definir políticas de acesso e de sessão. Saiba mais sobre como implantar certificados do cliente em [Implantar Controle de Aplicativo de Acesso Condicional para aplicativos do Azure AD](proxy-deployment-aad.md).
 
## <a name="supported-apps-and-clients"></a>Clientes e aplicativos compatíveis

O Controle de Aplicativos de Acesso Condicional atualmente dá suporte a aplicativos SAML e Open ID Connect configurados com logon único, juntamente com aplicativos Web hospedados localmente e configurados com o [Proxy de Aplicativo do Azure AD](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy).
> [!NOTE]
> O Controle de Aplicativos de Acesso Condicional também é compatível com aplicativos configurados com outros provedores de identidade além do Azure AD. Para obter mais informações sobre esse cenário, envie um email para mcaspreview@microsoft.com.

**O controle de sessão está disponível para todos os navegadores, nas principais plataformas e em todos os sistemas operacionais**. Aplicativos móveis e aplicativos da área de trabalho também podem ser bloqueados ou permitidos. Com a integração nativa do Azure AD, há suporte para todos os aplicativos SAML ou Open ID Connect configurados com logon único no Azure AD, incluindo os seguintes aplicativos em destaque:

- AWS
- Azure DevOps (Visual Studio Team Services) (versão prévia)
- Portal do Azure (versão prévia)
- Caixa
- Concur
- CornerStone on Demand
- DocuSign
- Dropbox
- Dynamics 365 CRM (visualização)
- Egnyte
- Exchange Online (versão prévia)
- G Suite
- GitHub
- HighQ
- JIRA/Confluence
- OneDrive for Business (versão prévia)
- LinkedIn Learning
- Power BI (versão prévia)
- Salesforce
- ServiceNow
- SharePoint Online (versão prévia)
- Slack
- Tableau
- Microsoft Teams (versão prévia)
- Workday
- Workiva
- Workplace by Facebook
- Yammer (versão prévia)




Aplicativos adicionais estão sendo continuamente integrados ao controle de sessão. Se você estiver interessado em um aplicativo específico não mencionado aqui, [envie-nos detalhes sobre o aplicativo](mailto:casfeedback@microsoft.com). Envie o caso de uso em que você está interessado para integrá-lo.



>[!div class="step-by-step"]
[PRÓXIMO: Implantar o Controle de Aplicativos de Acesso Condicional »](proxy-deployment-aad.md)


## <a name="next-steps"></a>Próximas etapas
[Implantar o controle de aplicativo de acesso condicional para aplicativos do Azure AD](proxy-deployment-aad.md)   

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/)  
  



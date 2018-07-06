---
title: Proteger com o Controle de Aplicativo de Acesso Condicional do Microsoft Cloud App Security | Microsoft Docs
description: Este tópico fornece informações sobre como funciona o proxy reverso do Controle de Aplicativo de Acesso Condicional do Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 6/18/2018
ms.topic: article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 35a43120-bf67-4cf9-9b48-ebe157dbbd18
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 8b3aea5db6a56efc94ed165f540519a5e7de22f3
ms.sourcegitcommit: 49a06f2169af74304eef0288e31783c06ccd3b74
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/24/2018
ms.locfileid: "36747027"
---
*Aplica-se ao: Microsoft Cloud App Security*


# <a name="protect-apps-with-microsoft-cloud-app-security-conditional-access-app-control"></a>Proteger aplicativos com o Controle de Aplicativo de Acesso Condicional do Microsoft Cloud App Security

>[!div class="step-by-step"]
[PRÓXIMO: Implantar o Controle de Aplicativo de Acesso Condicional »](proxy-deployment-aad.md)


Na área de trabalho de hoje em dia, geralmente não é suficiente saber o que está acontecendo em seu ambiente de nuvem após o fato, você deseja ser capaz de parar as violações e os vazamentos em tempo real, antes que os funcionários intencional ou inadvertidamente coloquem seus dados e sua organização em risco. É importante permitir que os usuários em sua organização aproveitem ao máximo os serviços e as ferramentas disponíveis a eles em aplicativos de nuvem e que eles tragam os próprios dispositivos para o trabalho. Ao mesmo tempo, são necessárias ferramentas para ajudar a proteger sua organização contra vazamentos de dados e roubo de dados, em tempo real. Juntamente com o Azure Active Directory, o Microsoft Cloud App Security oferece esses recursos em uma experiência holística e integrada com o Controle de Aplicativo de Acesso Condicional.

## <a name="how-it-works"></a>Como funciona

Controle de Aplicativo de Acesso Condicional usa uma arquitetura de proxy reverso e é exclusivamente integrado ao acesso condicional do Azure AD. O acesso condicional do Azure AD permite que você aplique controles de acesso nos aplicativos da sua organização com base em determinadas condições. As condições definem a *quem* (por exemplo, um usuário ou um grupo de usuários), a *quais* (quais aplicativos de nuvem) e *onde* (quais locais e redes) uma política de acesso condicional é aplicada. Depois de determinar as condições, é possível encaminhar os usuários ao Microsoft Cloud App Security para proteger dados com o Controle de Aplicativo de Acesso Condicional, aplicando controles de acesso e de sessão.

O Controle de Aplicativo de Acesso Condicional permite o monitoramento e controle em tempo real do acesso e das sessões do aplicativo com base nas políticas de acesso e de sessão. As políticas de acesso e de sessão são utilizadas dentro do portal do Cloud App Security para refinar ainda mais os filtros e definir as ações a serem executadas em relação a um usuário. Com as políticas de acesso e de sessão, é possível:

-   **Bloquear downloads**: é possível bloquear o download de documentos confidenciais. Por exemplo, em dispositivos não gerenciados.

-   **Proteger downloads**: em vez de bloquear o download de documentos confidenciais, é possível exigir que os documentos sejam protegidos por meio de criptografia no download. Isso garante que o documento esteja protegido e que o acesso do usuário seja autenticado se os dados são baixados para um dispositivo não confiável. 

-   **Monitorar sessões de usuário de baixa confiança**: usuários de risco são monitorados quando eles entram em aplicativos e suas ações são registradas dentro da sessão. É possível investigar e analisar o comportamento do usuário para compreender onde e sob quais condições as políticas de sessão deverão ser aplicadas no futuro. 

- **Bloquear o acesso**: bloqueie o acesso por completo a aplicativos específicos de usuários provenientes de dispositivos não gerenciados ou de redes não corporativas.

- **Criar modo somente leitura**: ao monitorar e bloquear atividades personalizadas no aplicativo, você pode criar um modo somente leitura para aplicativos específicos para usuários específicos.  

- **Restringir sessões de usuário de redes não corporativas**: os usuários que acessarem um aplicativo protegido de um local que não faz parte da sua rede corporativa terão acesso restrito, e o download de materiais confidenciais estará bloqueado ou protegido.

### <a name="how-session-control-works"></a>Como funciona o controle de sessão

A criação de uma política de sessão com Controle de Aplicativo de Acesso Condicional permite que você controle as sessões do usuário, redirecionando-o por meio de um proxy reverso, em vez de diretamente para o aplicativo. Daí em diante, as solicitações do usuário e as respostas passam pelo Microsoft Cloud App Security em vez de diretamente para o aplicativo.

Para manter o usuário dentro da sessão, todas as URLs relevantes, os scripts Java e os cookies dentro da sessão do aplicativo são substituídos por URLs do Microsoft Cloud App Security. Por exemplo: se o aplicativo retornar uma página com links cujos domínios terminam com myapp.com, o link é substituído por domínios que terminam com algo como: myapp.com.us.cas.ms 

Este método não requer que você instale nada em seu dispositivo. Ele é ideal ao monitorar sessões de dispositivos não gerenciados. 

Após o direcionamento de uma sessão pelo Microsoft Cloud App Security, é possível executar as seguintes ações:
1. Inspecionar as atividades de usuário do tráfego
2. Exibir as atividades identificadas no log de Atividades do Microsoft Cloud App Security
3. Salvar os logs de tráfego e analisá-los
4. Permitir que o administrador exporte os logs de tráfego
5. Aplicar políticas na sessão

## <a name="managed-device-identification"></a>Identificação do dispositivo gerenciado

O Controle de Aplicativo de Acesso Condicional permite que você crie políticas que levam em conta se um dispositivo é gerenciado ou não. Para identificar se um dispositivo é gerenciado ou não, o recurso usa:

-   Dispositivos em conformidade 
-   Dispositivos ingressados em domínio 
-   Implantação de certificados do cliente
 
 
### <a name="compliant-and-domain-joined-devices"></a>Dispositivos em conformidade e ingressados em domínio
O acesso condicional do Azure AD permite que informações do dispositivo em conformidade e ingressado em domínio sejam passadas diretamente para o Microsoft Cloud App Security. Nele, uma política de acesso ou de sessão que usa o estado do dispositivo como filtro pode ser desenvolvida.
Para obter mais informações, consulte a [Introdução ao gerenciamento de dispositivos no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/device-management-introduction). 

### <a name="client-certificate-authenticated-devices"></a>Dispositivos autenticados por certificado do cliente

O mecanismo de identificação de dispositivos pode solicitar autenticação de dispositivos relevantes usando certificados do cliente. Isso permite que você use certificados do cliente existentes já implantados em sua organização ou distribua novos certificados do cliente a dispositivos gerenciados e, em seguida, use a presença desses certificados para definir políticas de acesso e de sessão. Saiba mais sobre como implantar certificados do cliente em [Implantar Controle de Aplicativo de Acesso Condicional para aplicativos do Azure AD](proxy-deployment-aad.md).
 
## <a name="supported-apps-and-clients"></a>Clientes e aplicativos compatíveis

No momento, o Controle de Aplicativo de Acesso Condicional é compatível com aplicativos configurados com logon único SAML no Azure AD. 

> [!NOTE]
> - O Controle de Aplicativos de Acesso Condicional também é compatível com aplicativos configurados com outros provedores de identidade além do Azure AD. Para obter mais informações sobre esse cenário, envie um email para mcaspreview@microsoft.com.
> - Os aplicativos do Office 365 não estão configurados com SAML, portanto, não são compatíveis no momento.

O controle de sessão está disponível para qualquer navegador nas principais plataformas (aplicativos móveis e aplicativos da área de trabalho podem também ser bloqueados ou permitidos). Com a integração nativa do Microsoft Azure AD, há suporte para todos os aplicativos configurados com logon único do SAML no Azure AD, incluindo os seguintes aplicativos em destaque:

-   Salesforce

-   Caixa

-   G Suite

-   Workday

-   Slack

-   Workplace by Facebook

-   ServiceNow

-   JIRA/Confluence

-   AWS

-   Workiva

-   CornerStone on Demand

-   DocuSign

-   HighQ 

-   Concur

-   Tableau

Aplicativos adicionais estão sendo continuamente integrados ao controle de sessão. Se você estiver interessado em um aplicativo específico que não foi mencionado aqui, [envie os detalhes do aplicativo para nós](mailto:casfeedback@microsoft.com) e o caso de uso de seu interesse para que ele seja integrado.



>[!div class="step-by-step"]
[PRÓXIMO: Implantar o Controle de Aplicativo de Acesso Condicional »](proxy-deployment-aad.md)


## <a name="see-also"></a>Consulte Também  
[Implantar o controle de aplicativo de acesso condicional para aplicativos do Azure AD](proxy-deployment-aad.md)   

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  



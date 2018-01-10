---
title: Proteger-se com o proxy do Microsoft Cloud App Security | Microsoft Docs
description: "Este tópico fornece informações sobre como funciona o proxy do Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/20/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 35a43120-bf67-4cf9-9b48-ebe157dbbd18
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: d180fce8789fa20bea7135ce3fba437db996dcce
ms.sourcegitcommit: 3d943dbb0e0850af0dc390a78d8feca2f3fde61b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/20/2017
---
# <a name="protect-apps-with-microsoft-cloud-app-security-proxy"></a>Proteja aplicativos com o proxy do Microsoft Cloud App Security

> [!NOTE]
> Este é um recurso de versão prévia.


Na área de trabalho de hoje em dia, geralmente não é suficiente saber o que está acontecendo em seu ambiente de nuvem após o fato, você deseja ser capaz de parar as violações e os vazamentos em tempo real, antes que os funcionários intencional ou inadvertidamente coloquem seus dados e sua organização em risco. É importante permitir que os usuários em sua organização aproveitem ao máximo os serviços e as ferramentas disponíveis a eles em aplicativos de nuvem e que eles tragam os próprios dispositivos para o trabalho. Ao mesmo tempo, são necessárias ferramentas para ajudar a proteger sua organização contra vazamentos de dados e roubo de dados, em tempo real. Juntamente com o Azure Active Directory, o proxy do Cloud App Security oferece esses recursos em uma experiência holística e integrada.

## <a name="how-it-works"></a>Como funciona

O proxy do Cloud App Security integra-se ao acesso condicional do Azure AD. O acesso condicional do Azure AD permite que você aplique controles de acesso nos aplicativos da sua organização com base em determinadas condições. As condições definem a *quem* (por exemplo, um usuário ou um grupo de usuários), a *quais* (quais aplicativos de nuvem) e *onde* (quais locais e redes) uma política de acesso condicional é aplicada. Depois de determinar as condições, encaminhe os usuários para o proxy do Cloud App Security, no qual você poderá aplicar os controles de acesso e sessão.

Depois que um usuário for encaminhado para o proxy do Cloud App Security, seu acesso e suas sessões do aplicativo poderão ser monitoradas e controladas em tempo real com base nas políticas de acesso e de sessão. As políticas de acesso e de sessão são utilizadas dentro do portal do Cloud App Security para refinar ainda mais os filtros e definir as ações a serem executadas em relação a um usuário. Com as políticas de acesso e de sessão, é possível:

-   **Bloquear downloads**: é possível bloquear o download de documentos confidenciais. Por exemplo, em dispositivos não gerenciados.

-   **Proteger downloads**: em vez de bloquear o download de documentos confidenciais, é possível exigir que os documentos sejam protegidos por meio de criptografia no download. Isso garante que o documento esteja protegido e que o acesso do usuário seja autenticado se os dados são baixados para um dispositivo não confiável. 

-   **Restringir sessões de usuário de redes não corporativas**: os usuários que acessarem um aplicativo protegido de um local que não faz parte da sua rede corporativa terão acesso restrito, e o download de materiais confidenciais estará bloqueado ou protegido.

-   **Monitorar sessões de usuário de baixa confiança**: usuários de risco são monitorados quando eles entram em aplicativos e suas ações são registradas dentro da sessão. É possível investigar e analisar o comportamento do usuário para compreender onde e sob quais condições as políticas de sessão deverão ser aplicadas no futuro. 

- **Bloquear o acesso**: bloqueie o acesso por completo a aplicativos específicos de usuários provenientes de dispositivos não gerenciados ou de redes não corporativas.


### <a name="how-session-control-works"></a>Como funciona o controle de sessão

O controle de sessão do proxy é criado com base no acesso condicional. Depois de controlar o acesso a um aplicativo, é possível redirecionar as sessões de usuário para o controle de sessão do proxy em vez de diretamente para o aplicativo. Daí em diante, as solicitações do usuário e as respostas passam pelo proxy em vez de diretamente para o aplicativo.

Para manter o usuário dentro da sessão, o proxy substitui todas as URLs, os scripts Java e os cookies relevantes dentro da sessão do aplicativo por URLs do proxy. Por exemplo: se o aplicativo retornar uma página com links cujos domínios terminam com myapp.com, o proxy substituirá os links por domínios que terminam com algo como: myapp.com.us.cas.ms 

Este método não requer que você instale nada em seu dispositivo. Ele é ideal ao monitorar sessões de dispositivos não gerenciados. 

Depois que uma sessão for direcionada por meio do proxy, o proxy poderá realizar o seguinte:
1. Inspecionar as atividades de usuário do tráfego
3. Exibir as atividades identificadas no portal de proxy do Cloud App Security
2. Salvar os logs de tráfego e analisá-los
3. Permitir que o administrador exporte os logs de tráfego
4. Aplicar políticas na sessão

## <a name="managed-device-identification"></a>Identificação do dispositivo gerenciado

O proxy permite que você crie políticas que levam em conta se um dispositivo é gerenciado ou não. Para identificar se um dispositivo é gerenciado ou não, o proxy usa:

-   Dispositivos em conformidade 
-   Dispositivos ingressados em domínio 
-   Implantação de certificados do cliente
 
 
### <a name="compliant-and-domain-joined-devices"></a>Dispositivos em conformidade e ingressados em domínio
O acesso condicional do Azure AD permite que informações do dispositivo em conformidade e ingressado em domínio sejam passadas diretamente para o proxy do Cloud App Security. Nele, uma política de acesso ou de sessão que usa o estado do dispositivo como filtro pode ser desenvolvida.
Para obter mais informações, consulte a [Introdução ao gerenciamento de dispositivos no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/device-management-introduction). 

### <a name="client-certificate-authenticated-devices"></a>Dispositivos autenticados por certificado do cliente

O mecanismo de identificação de dispositivos do proxy pode solicitar autenticação de dispositivos relevantes usando certificados do cliente. Isso permite que você use certificados do cliente existentes já implantados em sua organização ou distribua novos certificados do cliente a dispositivos gerenciados e, em seguida, use a presença desses certificados para definir políticas de acesso e de sessão. Para obter informações sobre como implantar certificados do cliente, consulte [Deploy proxy for Azure AD apps](proxy-deployment-aad.md) (Implantar proxy para aplicativos do Azure AD).
 
## <a name="supported-apps-and-clients"></a>Clientes e aplicativos compatíveis

No momento, o proxy é compatível com aplicativos configurados com logon único SAML no Azure AD. 

> [!NOTE]
> - O proxy também é compatível com aplicativos configurados com provedores de identidade diferentes do Azure AD na Versão Prévia Privada. Para obter mais informações sobre a Versão Prévia Privada, envie um email para mcaspreview@microsoft.com.
> - Os aplicativos do Office 365 não estão configurados com SAML, portanto, não são compatíveis no momento.

Além disso, o controle de sessão não está automaticamente disponível para todos os aplicativos. A equipe do Cloud App Security testou muitos aplicativos populares com controle de sessão. Outros aplicativos podem exigir que um processo de integração seja realizado com o cliente.
Em termos de clientes, o controle de sessão está disponível para qualquer navegador em qualquer plataforma principal. No entanto, aplicativos móveis e aplicativos da área de trabalho não são compatíveis com o controle de sessão. 



## <a name="see-also"></a>Consulte Também  
[Implantar o proxy do Cloud App Security](proxy-deployment-aad.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  



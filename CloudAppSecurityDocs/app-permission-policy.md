---
title: Criar políticas para controlar aplicativos OAuth no Cloud App Security
description: Este artigo fornece instruções para criar e trabalhar com políticas de permissão de aplicativo no Microsoft Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 11/27/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 9d007c4760ace7a4337e4738406016576fa04171
ms.sourcegitcommit: 445a7c208455e6ce2c4e13b028c811f4c3486290
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78342668"
---
# <a name="oauth-app-policies"></a>Políticas de aplicativo OAuth

*Aplica-se a: Microsoft Cloud App Security*

Além da [investigação existente de aplicativos OAuth](manage-app-permissions.md) conectados ao seu ambiente, você pode definir políticas de permissão para para que você obtenha notificações automatizadas quando um aplicativo OAuth atender a determinados critérios. Por exemplo, você poderá receber um alerta automaticamente quando houver aplicativos que exijam um nível de permissão elevado e que tenham sido autorizados por mais de 50 usuários.

As políticas de aplicativo OAuth permitem que você investigue quais permissões cada aplicativo solicitou e quais usuários os autorizou para o Office 365, G Suite e Salesforce. Você também pode marcar essas permissões como aprovadas ou banidas. Marcá-las como banidas revogará permissões para cada aplicativo para cada usuário que o autorizou.

## <a name="create-a-new-oauth-app-policy"></a>Criar uma nova política de aplicativo OAuth

Há duas maneiras de criar uma nova política de aplicativo OAuth. A primeira maneira está em **investigar** e a segunda está sob **controle**.

Para criar uma nova política de aplicativo OAuth:

1. Em **investigar** , selecione **aplicativo OAuth**.

1. Filtre os aplicativos de acordo com suas necessidades, por exemplo, você pode exibir todos os aplicativos que solicitam **permissão** para **Modificar calendários em sua caixa de correio**.
1. Clique no botão **Nova política da pesquisa**.
    ![nova política da pesquisa](media/app-permissions-filter.png)
1. Você pode usar o filtro **usar a Comunidade** para obter informações sobre se permitir a permissão para esse aplicativo é comum, incomum ou raro. Esse filtro pode ser útil se você tiver um aplicativo raro e solicitar permissão que tenha um nível de severidade alto ou solicitar permissão de muitos usuários.
1. Você pode definir a política com base nas associações de grupo dos usuários que autorizam os aplicativos. Por exemplo, um administrador pode decidir por configurar uma política que revoga aplicativos incomuns se eles solicitarem permissões altas, somente se o usuário que autorizou as permissões for membro do grupo de administradores.

Como alternativa, você também pode criar a política clicando em **controle** seguido por **políticas**. Em seguida, clique em **criar política** seguido pela **política de aplicativo OAuth**.

   ![nova política de aplicativo OAuth](media/app-permissions-policy.png)

## <a name="oauth-app-anomaly-detection-policies"></a>Políticas de detecção de anomalias do aplicativo OAuth

Além das políticas de aplicativo OAuth que você pode criar, há as seguintes políticas de detecção de anomalias prontas para uso que fazem o perfil de metadados de aplicativos OAuth para identificar aqueles que são potencialmente mal-intencionados:

| Nome da política | Descrição da política |
| --- | --- |
| Nome do aplicativo OAuth enganoso | Verifica os aplicativos OAuth conectados ao seu ambiente e dispara um alerta quando um aplicativo com um nome enganoso é detectado. Nomes enganosos, como cartas estrangeiras que se assemelham a letras latinas, podem indicar uma tentativa de disfarçar um aplicativo mal-intencionado como um aplicativo conhecido e confiável. |
| Nome do editor enganoso para um aplicativo OAuth | Verifica os aplicativos OAuth conectados ao seu ambiente e dispara um alerta quando um aplicativo com um nome de editor enganoso é detectado. Nomes de Publicadores enganosos, como cartas estrangeiras semelhantes a letras latinas, podem indicar uma tentativa de disfarçar um aplicativo mal-intencionado como um aplicativo proveniente de um Publicador conhecido e confiável. |
| Consentimento de aplicativo OAuth mal-intencionado | Verifica os aplicativos OAuth conectados ao seu ambiente e dispara um alerta quando um aplicativo potencialmente mal-intencionado é autorizado. Aplicativos OAuth mal-intencionados podem ser usados como parte de uma campanha de phishing em uma tentativa de comprometer os usuários. Essa detecção aproveita a especialização da Microsoft em pesquisa de segurança e inteligência contra ameaças para identificar aplicativos mal-intencionados. |

<!--| Suspicious OAuth app name | Scans OAuth apps connected to your environment and triggers an alert when an app with a suspicious name is detected. Suspicious names, such as names of known apps published by unknown publishers, could indicate an attempt to disguise a malicious app as a known and trusted app. |
| Non-secure redirect URL is used by an OAuth app | Scans OAuth apps connected to your environment and triggers an alert when an app uses a non-secure redirect URL (for example, does not use the HTTPS protocol), which exposes sensitive data to interception. |-->

> [!NOTE]
> As políticas de detecção de anomalias só estão disponíveis para aplicativos OAuth que são autorizados em seu Azure Active Directory.

## <a name="next-steps"></a>{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}

> [!div class="nextstepaction"]
> [Políticas de proteção de dados](data-protection-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]

---
title: Criar políticas para controlar aplicativos OAuth no Cloud App Security
description: Este artigo oferece instruções para criar e trabalhar com políticas de permissão de aplicativo no Microsoft Cloud App Security.
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
ms.openlocfilehash: e5853882b7f95a492f4d8647af154f855d4f1d19
ms.sourcegitcommit: 7c93b6f93d2699d466b172590710ed01697bbdad
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74720287"
---
# <a name="oauth-app-policies"></a>Políticas de aplicativo OAuth

*Aplica-se ao: Microsoft Cloud App Security*

Além da [investigação existente dos aplicativos OAuth](manage-app-permissions.md) conectados ao seu ambiente, você pode definir políticas de permissão para obter notificações automatizadas quando um aplicativo OAuth atender a determinados critérios. Por exemplo, você poderá ser alertado automaticamente quando houver aplicativos que requerem um alto nível de permissão e foram autorizados por mais de 50 usuários.

As políticas de aplicativo OAuth permitem que você investigue quais permissões cada aplicativo solicitou e quais usuários as autorizaram para Office 365, G Suite e Salesforce. Você também poderá marcar essas permissões como aprovadas ou banidas. Marcá-las como banidas revogará as permissões de cada aplicativo de cada usuário que as autorizou.

## <a name="create-a-new-oauth-app-policy"></a>Criar uma nova política de aplicativo OAuth

Há duas maneiras de criar uma nova política de aplicativo OAuth. A primeira maneira é em **Investigar** e a segunda é em **Controle**.

Para criar uma nova política de aplicativo OAuth:

1. Em **Investigar**, selecione **Aplicativo OAuth**.

1. Filtre os aplicativos de acordo com suas necessidades, por exemplo, é possível exibir todos os aplicativos que solicitaram **Permissões** para **Modificar calendários em sua caixa de correio**.
1. Clique no botão **Nova política da pesquisa**.
    ![nova política da pesquisa](media/app-permissions-filter.png)
1. É possível usar o filtro **Uso da comunidade** para receber informações se a permissão a esse aplicativo é comum, incomum ou rara. Esse filtro poderá ser útil se um aplicativo do caso raro solicitar permissões com um alto nível de gravidade ou solicitar permissão de muitos usuários.
1. Você pode definir a política de acordo com as associações a grupo dos usuários que autorizaram os aplicativos. Por exemplo, um administrador poderá decidir definir uma política que revogue aplicativos incomuns se eles solicitarem permissões altas apenas se o usuário que autorizou as permissões for membro do grupo de administradores.

Como alternativa, também é possível criar a política clicando em **Controle** e, em seguida, em **Políticas**. Em seguida, clique em **Criar política** seguido por **Política de aplicativo OAuth**.

   ![nova política de aplicativo OAuth](media/app-permissions-policy.png)

## <a name="oauth-app-anomaly-detection-policies"></a>Políticas de detecção de anomalias do aplicativo OAuth

Além das políticas de aplicativo OAuth que você pode criar, há as seguintes políticas de detecção de anomalias prontas para uso que fazem o perfil de metadados de aplicativos OAuth para identificar aqueles que são potencialmente mal-intencionados:

| Nome da política | Descrição da política |
| --- | --- |
| Nome do aplicativo OAuth enganoso | Verifica os aplicativos OAuth conectados ao seu ambiente e dispara um alerta quando um aplicativo com um nome enganoso é detectado. Nomes enganosos, como cartas estrangeiras que se assemelham a letras latinas, podem indicar uma tentativa de disfarçar um aplicativo mal-intencionado como um aplicativo conhecido e confiável. |
| Nome do editor enganoso para um aplicativo OAuth | Verifica os aplicativos OAuth conectados ao seu ambiente e dispara um alerta quando um aplicativo com um nome de editor enganoso é detectado. Nomes de Publicadores enganosos, como cartas estrangeiras semelhantes a letras latinas, podem indicar uma tentativa de disfarçar um aplicativo mal-intencionado como um aplicativo proveniente de um Publicador conhecido e confiável. |

<!--| Suspicious OAuth app name | Scans OAuth apps connected to your environment and triggers an alert when an app with a suspicious name is detected. Suspicious names, such as names of known apps published by unknown publishers, could indicate an attempt to disguise a malicious app as a known and trusted app. |
| Non-secure redirect URL is used by an OAuth app | Scans OAuth apps connected to your environment and triggers an alert when an app uses a non-secure redirect URL (for example, does not use the HTTPS protocol), which exposes sensitive data to interception. |-->

> [!NOTE]
> As políticas de detecção de anomalias só estão disponíveis para aplicativos OAuth que são autorizados em seu Azure Active Directory.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Políticas de proteção de dados](data-protection-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]

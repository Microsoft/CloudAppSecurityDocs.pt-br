---
title: Criar políticas para controlar aplicativos OAuth no Cloud App Security
description: Este artigo oferece instruções para criar e trabalhar com políticas de permissão de aplicativo no Microsoft Cloud App Security.
ms.date: 11/27/2019
ms.topic: how-to
ms.openlocfilehash: c97fbd615432b2c1579f406bc57427b261124848
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96313824"
---
# <a name="oauth-app-policies"></a>Políticas de aplicativo OAuth

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Além da [investigação existente dos aplicativos OAuth](manage-app-permissions.md) conectados ao seu ambiente, você pode definir políticas de permissão para obter notificações automatizadas quando um aplicativo OAuth atender a determinados critérios. Por exemplo, você poderá receber um alerta automaticamente quando houver aplicativos que exijam um nível de permissão elevado e que tenham sido autorizados por mais de 50 usuários.

As políticas de aplicativo OAuth permitem que você investigue quais permissões cada aplicativo solicitou e quais usuários as autorizaram para Office 365, G Suite e Salesforce. Você também poderá marcar essas permissões como aprovadas ou banidas. Marcá-las como banidas revogará as permissões de cada aplicativo de cada usuário que as autorizou.

## <a name="create-a-new-oauth-app-policy"></a>Criar uma nova política de aplicativo OAuth

Há duas maneiras de criar uma nova política de aplicativo OAuth. A primeira maneira é em **Investigar** e a segunda é em **Controle**.

Para criar uma nova política de aplicativo OAuth:

1. Em **Investigar**, selecione **Aplicativo OAuth**.

1. Filtre os aplicativos de acordo com suas necessidades, por exemplo, é possível exibir todos os aplicativos que solicitaram **Permissões** para **Modificar calendários em sua caixa de correio**.
1. Clique no botão **Nova política da pesquisa**.
    ![nova política da pesquisa](media/app-permissions-filter.png)
1. É possível usar o filtro **Uso da comunidade** para receber informações se a permissão a esse aplicativo é comum, incomum ou rara. Esse filtro poderá ser útil se um aplicativo do caso raro solicitar permissões com um alto nível de gravidade ou solicitar permissão de muitos usuários.
1. Você pode definir a política de acordo com as associações a grupo dos usuários que autorizaram os aplicativos. Por exemplo, um administrador pode decidir por configurar uma política que revoga aplicativos incomuns se eles solicitarem permissões altas, somente se o usuário que autorizou as permissões for membro do grupo de administradores.

Como alternativa, também é possível criar a política clicando em **Controle** e, em seguida, em **Políticas**. Em seguida, clique em **Criar política** seguido por **Política de aplicativo OAuth**.

   ![nova política de aplicativo OAuth](media/app-permissions-policy.png)

## <a name="oauth-app-anomaly-detection-policies"></a>Políticas de detecção de anomalias do aplicativo OAuth

Além das políticas de aplicativo OAuth que você pode criar, há as seguintes políticas de detecção de anomalias prontas para uso que fazem o perfil de metadados de aplicativos OAuth para identificar aqueles que são potencialmente mal-intencionados:

| Nome de política | Descrição da política |
| --- | --- |
| Nome do aplicativo OAuth enganoso | Verifica os aplicativos OAuth conectados ao seu ambiente e dispara um alerta quando um aplicativo com um nome enganoso é detectado. Nomes enganosos, como cartas estrangeiras que se assemelham a letras latinas, podem indicar uma tentativa de disfarçar um aplicativo mal-intencionado como um aplicativo conhecido e confiável. |
| Nome do editor enganoso para um aplicativo OAuth | Verifica os aplicativos OAuth conectados ao seu ambiente e dispara um alerta quando um aplicativo com um nome de editor enganoso é detectado. Nomes de Publicadores enganosos, como cartas estrangeiras semelhantes a letras latinas, podem indicar uma tentativa de disfarçar um aplicativo mal-intencionado como um aplicativo proveniente de um Publicador conhecido e confiável. |
| Consentimento de aplicativo OAuth mal-intencionado | Verifica os aplicativos OAuth conectados ao seu ambiente e dispara um alerta quando um aplicativo potencialmente mal-intencionado é autorizado. Aplicativos OAuth mal-intencionados podem ser usados como parte de uma campanha de phishing em uma tentativa de comprometer os usuários. Essa detecção aproveita a especialização da Microsoft em pesquisa de segurança e inteligência contra ameaças para identificar aplicativos mal-intencionados. |
| Atividades suspeitas de download do arquivo de aplicativo OAuth | Consulte [políticas de detecção de anomalias](anomaly-detection-policy.md#suspicious-oauth-app-file-download-activities) |

<!--
| OAuth apps authorized by external users | Scans OAuth apps connected to your environment and triggers an alert when an app was authorized by an external user. |
| OAuth apps with high permissions and rare community use – Google | Scans OAuth apps connected to your environment and triggers an alert for apps with high permissions and rare community use in Google. |
| OAuth apps with high permissions and rare community use – Office | Scans OAuth apps connected to your environment and triggers an alert for apps with high permissions and rare community use in Office. |
| OAuth apps with rare community use - Salesforce | Scans OAuth apps connected to your environment and triggers an alert for apps with rare community use in Salesforce. |
-->

> [!NOTE]
> As políticas de detecção de anomalias só estão disponíveis para aplicativos OAuth que são autorizados em seu Azure Active Directory.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Políticas de proteção de dados](data-protection-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]

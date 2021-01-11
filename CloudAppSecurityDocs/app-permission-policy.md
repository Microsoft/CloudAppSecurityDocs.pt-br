---
title: Criar políticas para controlar aplicativos OAuth no Cloud App Security
description: Este artigo oferece instruções para criar e trabalhar com políticas de permissão de aplicativo no Microsoft Cloud App Security.
ms.date: 01/11/2021
ms.topic: how-to
ms.openlocfilehash: 3fe565607f59834cf1b4a6931b087b597c3f5c8d
ms.sourcegitcommit: 04d8731dce2a3b3b2d10bbfa27e5dc80b0a3e0f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2021
ms.locfileid: "98062695"
---
# <a name="oauth-app-policies"></a>Políticas de aplicativo OAuth

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Além da [investigação existente dos aplicativos OAuth](manage-app-permissions.md) conectados ao seu ambiente, você pode definir políticas de permissão para obter notificações automatizadas quando um aplicativo OAuth atender a determinados critérios. Por exemplo, você poderá receber um alerta automaticamente quando houver aplicativos que exijam um nível de permissão elevado e que tenham sido autorizados por mais de 50 usuários.

As políticas de aplicativo OAuth permitem investigar quais permissões cada aplicativo solicitou e quais usuários os autorizam para o Office 365, o Google Workspace e o Salesforce. Você também poderá marcar essas permissões como aprovadas ou banidas. Marcá-las como banidas revogará as permissões de cada aplicativo de cada usuário que as autorizou.

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
>
> - As políticas de detecção de anomalias só estão disponíveis para aplicativos OAuth que são autorizados em seu Azure Active Directory.
> - A severidade das políticas de detecção de anomalias do aplicativo OAuth não pode ser modificada.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Políticas de proteção de dados](data-protection-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]

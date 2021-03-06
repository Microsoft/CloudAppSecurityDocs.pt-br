---
title: Definir preferências de administrador
description: Este artigo fornece instruções para configurar as preferências do administrador em Cloud App Security.
ms.date: 04/19/2020
ms.topic: how-to
ms.openlocfilehash: 18b5940ad4365a31b7e344860c0f791e306d8890
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96314776"
---
# <a name="admin-user-settings"></a>Configurações do usuário administrador

[!INCLUDE [Banner for top of topics](includes/banner.md)]

O Microsoft Cloud App Security permite personalizar suas configurações de usuário administrador. As configurações de notificação permitem que os administradores especifiquem se eles desejam receber notificações por email ou texto para alertas.

## <a name="customize-your-admin-settings"></a><a name="Adminsettings"></a>Personalizar suas configurações de administrador

Para configurar suas preferências como um administrador do Microsoft Cloud App Security, clique em seu nome na barra de menus do portal e selecione **Configurações de usuário** para definir as seguintes configurações:

1. Clique em **idioma**. Aqui você pode escolher o idioma a ser usado no portal de Cloud App Security.

    ![configurações personalizadas do usuário](media/custom-language-settings.png)

2. Clique em **Notificações** e defina as preferências de notificação de email e texto para os emails recebidos do sistema. Você pode definir a gravidade que determina para quais alertas e violações você deseja receber emails. A gravidade é definida por política. Quando as violações forem disparadas, você receberá uma notificação por email dependendo da configuração daqui e da configuração de Gravidade na política que foi violada. Os emails são enviados para o alias associado à conta de usuário do administrador usada para entrar no Cloud App Security. Insira um número de telefone para permitir que o Cloud App Security envie mensagens de texto quando alertas e notificações forem enviados e defina o nível de gravidade para o qual você deseja receber notificações por mensagem de texto.

    > [!NOTE]
    >
    > - O número máximo de alertas enviados por meio de mensagem de texto é 10 por número de telefone por dia. O dia é calculado de acordo com o fuso horário UTC.
    > - As notificações não são enviadas para eventos Azure Active Directory IPC.

    ![configurações de notificação](media/notification-settings.png)

3. Quando terminar, clique em **Salvar**.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Configurar Cloud Discovery](set-up-cloud-discovery.md)

[!INCLUDE [Open support ticket](includes/support.md)]

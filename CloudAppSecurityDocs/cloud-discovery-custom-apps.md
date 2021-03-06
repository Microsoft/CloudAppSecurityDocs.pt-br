---
title: Adicionar aplicativos personalizados ao Cloud Discovery no Cloud App Security
description: Este tópico fornece informações sobre como adicionar aplicativos personalizados ao Cloud Discovery no Cloud App Security a fim de monitorar a TI Sombra.
ms.date: 12/10/2018
ms.topic: how-to
ms.openlocfilehash: c757d320b242a8cccdde312835ec9e35299f6bdf
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96313246"
---
# <a name="add-custom-apps-to-cloud-discovery"></a>Adicionar aplicativos personalizados ao Cloud Discovery

[!INCLUDE [Banner for top of topics](includes/banner.md)]

O Cloud Discovery analisa os logs de tráfego no catálogo de aplicativos de nuvem do Microsoft Cloud App Security. Há mais de 16 mil aplicativos de nuvem no catálogo de aplicativos de nuvem. O catálogo contém apenas aplicativos de nuvem disponíveis publicamente, para os quais o Cloud App Security fornece visibilidade e informações sobre o risco.

Para ganhar visibilidade dos aplicativos de nuvem excluídos do catálogo de aplicativos de nuvem, o Cloud App Security permite que você descubra o uso de aplicativos de nuvem personalizados (aplicativos de LOB) que foram desenvolvidos ou atribuídos especificamente para sua organização.

Ao adicionar um novo aplicativo de nuvem personalizado, o Cloud App Security é capaz de corresponder mensagens de log de tráfego de proxy e de firewall carregadas no aplicativo e, em seguida, fornecer visibilidade do uso desse aplicativo na organização nas páginas do Cloud Discovery. Por exemplo, quantos usuários usam o aplicativo, quantos endereços IP de origem exclusivos usam o aplicativo e a quantidade de tráfego transmitido para dentro e para fora do aplicativo.

## <a name="add-a-new-custom-cloud-app"></a>Adicionar um novo aplicativo de nuvem personalizado

1. No portal do Cloud App Security, clique em **Descobrir** e em **Painel do Cloud Discovery**.

    ![menu do painel do cloud discovery](media/cloud-discovery-dashboard-menu.png)

2. No canto superior direito, clique nos três pontos e, em seguida, selecione **Adicionar novo aplicativo personalizado**.

    ![menu adicionar aplicativo personalizado](media/add-custom-app-menu.png)

3. Preencha os campos para definir o novo registro de aplicativo que será listado no catálogo de aplicativos de nuvem e no Cloud Discovery após a descoberta nos logs de firewall.

    ![aplicativo personalizado](media/add-custom-app.png)

4. Em **Domínios**, preencha os domínios exclusivos que são usados ao acessar o aplicativo personalizado. Esses domínios são usados para corresponder às mensagens do log de tráfego para esse aplicativo. Se a fonte de dados que você está usando não tiver informações de URL do aplicativo, certifique-se de preencher os campos de endereço **IPv4** e **IPv6** .
5. Adicione a **Plataforma de hospedagem** e a **ID da Assinatura do Azure**. Opcionalmente, especifique a **Unidade de negócios** do aplicativo.
6. Atribua uma **Pontuação** de risco e adicione **Anotações do Aplicativo** para ajudá-lo a acompanhar as alterações deste registro.
7. Clique em **Criar**.

Depois que o aplicativo for criado, ele estará disponível para você no catálogo de aplicativos de nuvem.

A qualquer momento, você pode clicar nas reticências no final da linha para editar ou excluir um aplicativo personalizado.

>[!NOTE]
> Aplicativos personalizados são marcados automaticamente com a marca **Aplicativo personalizado** depois de adicioná-los. A marca desse aplicativo não pode ser removida.
Para exibir todos os seus aplicativos personalizados, defina o filtro de **marca do aplicativo** como igual a ' aplicativo personalizado '.
<!-- - By default, custom apps have a risk score of 10, but you can use the **Override app score** action to change it at any time.-->

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Políticas de atividade de usuário](user-activity-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]

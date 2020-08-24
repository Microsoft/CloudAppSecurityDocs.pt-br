---
title: Privacidade da atividade
description: Este artigo fornece informações sobre como configurar o monitoramento de atividades para estar em conformidade com a política de privacidade do usuário.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 05/27/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 0fbb487695c395fe7fddbd6bc84855d74e060497
ms.sourcegitcommit: 29a8e66c665f51d831516924ae4d9d8047b39276
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88779977"
---
# <a name="activity-privacy"></a>Privacidade da atividade

*Aplica-se a: Microsoft Cloud App Security*

O Microsoft Cloud App Security fornece às empresas a capacidade de determinar de maneira granular quais usuários eles desejam monitorar com base na associação de grupo. A privacidade da atividade adiciona a capacidade de seguir os regulamentos de conformidade da sua organização sem comprometer a privacidade do usuário. Isso é feito permitindo que você monitore os usuários enquanto mantém sua privacidade ocultando suas atividades no log de atividades. Somente administradores autorizados têm a opção de exibir essas atividades privadas, com cada instância sendo auditada no log de governança.

## <a name="configure-activity-privacy-user-groups"></a>Configurar grupos de usuários de privacidade da atividade

Você pode ter usuários em Cloud App Security que deseja monitorar, mas, devido a regulamentos de conformidade, você precisa limitar as pessoas que podem fazer isso. A privacidade da atividade permite que você defina um grupo de usuários para o qual as atividades ficarão ocultas por padrão.

Para configurar os grupos de privacidade do usuário, você deve primeiro [importar grupos de usuários](user-groups.md) para Cloud app Security. Por padrão, você verá os seguintes grupos:

- Grupo de usuários de **aplicativo** – um grupo integrado que lhe permite ver as atividades executadas pelos aplicativos do Office 365 e do Azure AD.

- Grupo de **usuários externos** – todos os usuários que não são membros de qualquer um dos domínios gerenciados que você configurou para sua organização.

1. Na barra de menus, clique nas configurações engrenagem e selecione **implantação e privacidade com escopo**.

    ![Ícone de configurações](media/settings-icon.png)

1. Para definir grupos específicos a serem monitorados pelo Cloud App Security, na guia **privacidade da atividade** , clique no ícone de adição.
    ![icon](media/plus-icon.png)

1. Na caixa de diálogo **Adicionar grupos** de usuários, em **Selecionar grupos de usuários**, selecione todos os grupos que você deseja tornar particulares em Cloud app Security e clique em **Adicionar**.

    ![Captura de tela mostrando a caixa de diálogo Adicionar grupos de usuários](media/activity-privacy-add-user-groups.png)

    > [!NOTE]
    > Depois que um grupo de usuários é adicionado, todas as atividades executadas por usuários do grupo serão feitas de forma privada a partir desse fim. As atividades existentes não são afetadas.

## <a name="assign-admins-permission-to-view-private-activities"></a>Atribuir permissão de administradores para exibir atividades privadas

1. Na barra de menus, clique nas configurações engrenagem e selecione **gerenciar acesso de administrador**.

    ![Ícone de configurações](media/settings-icon.png)

1. Para conceder permissão a administradores específicos para exibir atividades privadas, na guia **permissões de privacidade da atividade** , clique no ícone de adição.
    ![icon](media/plus-icon.png)

1. Na caixa de diálogo **adicionar permissão de administrador** , insira o UPN ou o endereço de email do administrador e clique em **adicionar permissão**.

    ![Captura de tela mostrando a caixa de diálogo Adicionar permissão de administrador](media/activity-privacy-add-admin-permission.png)

    > [!NOTE]
    > Somente administradores podem receber permissão para exibir atividades privadas.

## <a name="viewing-private-activities"></a>Exibindo atividades privadas

Depois que um administrador tiver recebido a permissão apropriada para exibir atividades privadas, ele terá a opção de escolher ver essas atividades no log de atividades.

### <a name="to-view-private-activities"></a>Para exibir atividades privadas

1. Na página **log de atividades** , à direita da tabela atividade, clique no ícone configurações e selecione **Mostrar atividades privadas**.

    ![Captura de tela mostrando o ícone de configurações do log de atividades](media/activity-privacy-view-settings-icon.png)

1. Na caixa de diálogo **Mostrar atividades privadas** , clique em **OK** para confirmar que você entendeu que a ação está sendo auditada. Depois de confirmadas, as atividades privadas são mostradas no log de atividades e a ação é registrada no log de governança.

[!INCLUDE [Open support ticket](includes/support.md)]

---
title: Importar grupos de usuários de aplicativos conectados no Cloud App Security
description: Este artigo fornece instruções sobre como importar os grupos de usuários de aplicativos conectados para o Cloud App Security.
ms.date: 11/17/2019
ms.topic: how-to
ms.openlocfilehash: d441e28280df81e8f34a73e28e56797b2826f867
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96315715"
---
# <a name="importing-user-groups-from-connected-apps"></a>Importar grupos de usuários de aplicativos conectados

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Quando você conecta aplicativos usando conectores de API, o Microsoft Cloud App Security permite que você importe grupos de usuários, por exemplo do Office 365 e do Azure Active Directory. Há dois tipos de grupos de usuários:

- Grupos automáticos  
Grupos automáticos são criados por padrão pelo Microsoft Cloud App Security. Por exemplo, há um grupo de usuários automático chamado **Externo** que combina todos os usuários de todos os aplicativos que são externos à sua organização e que têm acesso a arquivos ou que estavam em atividades do usuário em seu locatário. Os seguintes grupos automáticos existem no Cloud App Security:

  - Externo
  - Administrador do Dropbox
  - Administrador do Office 365
  - Administrador do G Suite
  - Administrador do Box
  - Todos os perfis personalizados e padrão do Salesforce, por exemplo o Administrador de Sistema do Salesforce. Consulte a lista completa [aqui](https://help.salesforce.com/articleView?id=standard_profiles.htm&language=en&type=0).

- Grupos importados  
Você pode importar qualquer grupo de seus aplicativos conectados. Por exemplo, você pode importar grupos de usuários do Office 365 (Active Directory) e outros aplicativos conectados. Esses grupos permitem que você procure ameaças em sua organização, não observando a organização inteira nem um usuário específico, mas observando um grupo específico.

  Os cenários típicos que usam grupos de usuários importados incluem:

  - Investigar os documentos que a equipe de RH visualizou
  - Verificar se há algo incomum acontecendo no grupo de executivos
  - Descobrir se alguém do grupo de administradores realizou uma atividade fora dos EUA.

## <a name="how-to-import-user-groups"></a>Como importar grupos de usuários

1. Na barra de menus, clique no ícone configurações ícones ![configurações](media/settings-icon.png "Ícone de configurações") e selecione **grupos de usuários**.
1. Clique em **Importar grupo de usuários**.

    ![Importar grupos de usuários](media/user-groups-add.png)

1. Selecione o aplicativo do qual deseja importar o grupo de usuários. A lista de aplicativos dependerá de qual Conector de Aplicativo você implantou.
1. Selecione o grupo a ser importado. A lista de grupos disponíveis será uma lista de todos os grupos de usuário existente no próprio aplicativo. Caso deseje adicionar um novo grupo, você precisará fazê-lo diretamente no próprio aplicativo. Em seguida, quando o grupo for exibido na lista aqui, selecione-o.
1. Dependendo do tamanho do grupo, a importação pode demorar até uma hora. Você pode selecionar a opção para ser notificado por email quando o processo de importação for concluído.
1. Clique em **Importar**. Depois de importar um grupo, o Cloud App Security sincroniza automaticamente os membros do grupo, assim como faz o Active Directory Connect.
1. Depois que a importação for concluída, na página **Grupos de usuários**, você pode clicar em um grupo específico para exibir uma lista de todos os membros do grupo. Clique em qualquer membro do grupo para fazer uma busca detalhada em uma conta específica. Você pode exibir quais aplicativos foram usados e um resumo da conta, incluindo grafos do usuário e suas atividades.

A importação de grupos permite que você selecione os grupos como filtros ao investigar no **Log de atividades** e ao criar políticas.

> [!NOTE]
>
> - O número máximo de grupos de usuários importados é 500.
> - Pode haver um pequeno atraso até que os grupos de usuários importados estejam disponíveis em filtros.
> - Somente as atividades executadas após a importação de um grupo de usuários serão marcadas como tendo sido executada por um membro do grupo de usuários.
> - Após a sincronização inicial, os grupos são atualizados a cada hora.

Para obter mais informações sobre como usar os filtros de grupo de usuários, consulte [Atividades](activity-filters.md).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Configurar Cloud Discovery](set-up-cloud-discovery.md)

[!INCLUDE [Open support ticket](includes/support.md)]

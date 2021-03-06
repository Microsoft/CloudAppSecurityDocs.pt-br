---
title: Visibilidade em contas de aplicativo de nuvem
description: Este artigo fornece informações sobre como examinar as contas de seus aplicativos conectados.
ms.date: 05/20/2020
ms.topic: how-to
ms.openlocfilehash: d832891699a9840117935d815c04714ea1ec2f20
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96311257"
---
# <a name="accounts"></a>Contas

[!INCLUDE [Banner for top of topics](includes/banner.md)]

O Microsoft Cloud App Security proporciona visibilidade das contas de seus aplicativos conectados. Depois que você conectar o Cloud App Security a um aplicativo usando o conector de aplicativos, o Cloud App Security lerá as informações da conta associadas aos aplicativos conectados. A página Contas permite que você investigue essas contas, as permissões, os grupos dos quais são membros, os aliases delas e os aplicativos que elas estão usando. Além disso, quando o Cloud App Security detecta uma nova conta que não foi vista anteriormente em um dos aplicativos conectados, como nas atividades ou no compartilhamento de arquivos, a conta é adicionada à lista de contas deste aplicativo. Isso permite que você tenha visibilidade sobre a atividade de usuários externos interagindo com seus aplicativos em nuvem.

Os administradores podem pesquisar os metadados de um usuário específico ou as atividades do usuário. A página **usuários e contas** fornece detalhes abrangentes sobre as entidades extraídas dos aplicativos de nuvem conectados. Também fornece o histórico de atividades e os alertas de segurança relacionados ao usuário.

[!INCLUDE [Handle personal data](../includes/gdpr-intro-sentence.md)]

A página **usuários e contas** pode ser [filtrada](#users-and-accounts-filters) para permitir que você encontre contas específicas e aprofunde-se em diferentes tipos de contas, por exemplo, você pode filtrar por todas as contas externas que não foram acessadas desde o último ano.

A página **Usuários e contas** permite que você investigue facilmente suas contas, incluindo com relação aos seguintes problemas:

* Verifique se quaisquer contas estiveram inativas em um serviço específico por um longo período (talvez você deva revogar a licença desse usuário para esse serviço)

* Você pode filtrar a lista de usuários com permissões de administrador
* Você pode pesquisar usuários que não fazem mais parte da sua organização, mas que ainda podem ter contas ativas
* Você pode tomar [ações de governança](#governance-actions) nas contas, como suspender um aplicativo ou ir para a página de configurações de conta.
* Você pode ver quais contas estão incluídas em cada grupo de usuários  
* Você pode ver quais aplicativos são acessados por cada conta e quais aplicativos são excluídos para contas específicas

    ![tela de contas](media/accounts-page.png)

## <a name="users-and-accounts-filters"></a>Filtros de usuários e contas

Veja a seguir uma lista de filtros de contas que podem ser aplicados. A maioria dos filtros dá suporte a vários valores, bem como NOT, para fornecer uma ferramenta poderosa para a criação de políticas.  
  
<!--- **Account name**: The account name is the primary alias of the user, but other identifiers from other Microsoft accounts (Office 365 and Azure Active Directory) such as proxy addresses, aliases, SID are supported and consolidated beneath the primary alias. -->

* **Afiliação**: a afiliação pode ser **interna** ou **externa**. Para definir quais usuários e contas são internos, em **configurações**, certifique-se de definir o **intervalo de endereços IP** da sua organização interna. Se a conta tiver permissões de administrador, o ícone na tabela Contas aparecerá com a adição da gravata vermelha. ![ícone de administrador de contas](media/accounts-admin-icon.png)

* **Aplicativo**: você pode filtrar para qualquer aplicativo conectado de API que esteja sendo usado por contas em sua organização.
* **Domínio**: permite que você filtre para usuários em domínios específicos.
* **Grupos**: permite que você filtre para membros de grupos de usuários no Cloud App Security – grupos de usuários internos e grupos de usuários importados.
* **Instância**: permite que você filtre para membros de uma instância de aplicativo específico.
* **Visto pela última vez em**: o filtro **Visto pela última vez em** permite localizar as contas que estão inativas e cujos usuários não executaram nenhuma atividade há algum tempo.
* **Organização**: permite que você filtre os membros de grupos organizacionais específicos definidos em seus aplicativos conectados.
* **Mostrar apenas administradores**: filtros para contas e usuários que são administradores.
* **Status**: filtre com base no status da conta de usuário de N/D, em estágios, ativo, suspenso ou excluído. Um status de não disponível (N/A) é normal e pode aparecer, por exemplo, para contas anônimas.
* **Tipo**: permite que você filtre para o usuário ou o tipo de conta.
* **Nome de usuário**: permite que você filtre para usuários específicos.

## <a name="governance-actions"></a>Ações de governança

Na página **usuários e conta** , você pode tomar ações de governança, como suspender um aplicativo ou ir para a página Configurações de conta. Para obter uma lista completa de ações de governança, confira o [log de governança](governance-actions.md).

Por exemplo, se você identificar um usuário comprometido, poderá aplicar a ação **confirmar comprometimento do usuário** para definir o nível de risco do usuário como alto, fazendo com que as ações de política relevantes definidas em Azure Active Directory sejam impostas. A ação pode ser aplicada manualmente ou usando [políticas relevantes que dão suporte a ações de governança](governance-actions.md).

### <a name="to-manually-apply-a-user-or-account-governance-action"></a>Para aplicar manualmente uma ação de governança de usuário ou conta

Você pode aplicar manualmente a ação **confirmar o usuário comprometido** usando um dos seguintes métodos:

* Na página **usuários e conta** , na linha em que o usuário ou conta relevante aparece, escolha os três pontos no final da linha e, em seguida, escolha **confirmar usuário comprometido**.

* Na **página usuário**, selecione **ações do usuário** e, em seguida, escolha **confirmar usuário comprometido**.

* **Nome de usuário**: permite que você filtre para usuários específicos.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]

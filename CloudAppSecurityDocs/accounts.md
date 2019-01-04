---
title: Visibilidade das contas de aplicativos na nuvem – Cloud App Security | Microsoft Docs
description: Este artigo fornece informações sobre como examinar as contas de seus aplicativos conectados.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/10/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 7811f23b-6100-427f-93b1-44f5f81f6c76
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 7b04724605eba07b2adbd952f634bd92496d772e
ms.sourcegitcommit: b86c3afd1093fbc825fec5ba4103e3a95f65758e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53175661"
---
# <a name="accounts"></a>Contas

*Aplica-se a: Microsoft Cloud App Security*

O Microsoft Cloud App Security proporciona visibilidade das contas de seus aplicativos conectados. Depois que você conectar o Cloud App Security a um aplicativo usando o conector de aplicativos, o Cloud App Security lerá as informações da conta associadas aos aplicativos conectados. A página Contas permite que você investigue essas contas, as permissões, os grupos dos quais são membros, os aliases delas e os aplicativos que elas estão usando. Além disso, quando o Cloud App Security detecta uma nova conta que não foi vista anteriormente em um dos aplicativos conectados, como nas atividades ou no compartilhamento de arquivos, a conta é adicionada à lista de contas deste aplicativo. Isso permite que você tenha visibilidade sobre a atividade de usuários externos interagindo com seus aplicativos em nuvem.

Os administradores podem pesquisar metadados de um usuário específico ou a atividade do usuário. A página **Usuários e contas** fornece detalhes abrangentes sobre a entidade, extraídos de aplicativos de nuvem conectados. Ela também fornece o histórico de atividades e alertas de segurança do usuário.

[!INCLUDE [Handle personal data](../includes/gdpr-intro-sentence.md)]


A página **Usuários e contas** pode ser filtrada para que você possa localizar contas específicas e se aprofundar em diferentes tipos de contas, por exemplo, você pode filtrar todas as contas Externas que não tenham sido acessadas desde o ano passado. 

A página **Usuários e contas** permite que você investigue facilmente suas contas, incluindo com relação aos seguintes problemas:  

-   Verifique se quaisquer contas estiveram inativas em um serviço específico por um longo período (talvez você deva revogar a licença desse usuário para esse serviço)  
-   Você pode filtrar a lista de usuários com permissões de administrador  

-   Você pode pesquisar usuários que não fazem mais parte da sua organização, mas que ainda podem ter contas ativas  

-   Você pode realizar ações de governança nas contas, como suspender um aplicativo ou acessar a página de configurações da conta de controle. Para obter uma lista completa de ações de governança, confira o [log de governança](governance-actions.md).
    
-   Você pode ver quais contas estão incluídas em cada grupo de usuários  

-   Você pode ver quais aplicativos são acessados por cada conta e quais aplicativos são excluídos para contas específicas
    

![tela de contas](./media/accounts-page.png)

## <a name="users-and-accounts-filters"></a>Filtros de usuários e contas
Veja a seguir uma lista de filtros de contas que podem ser aplicados. A maioria dos filtros dá suporte a vários valores, bem como NOT, para fornecer uma ferramenta poderosa para a criação de políticas.  
  
<!--- **Account name**: The account name is the primary alias of the user, but other identifiers from other Microsoft accounts (Office 365 and Azure Active Directory) such as proxy addresses, aliases, SID are supported and consolidated beneath the primary alias. -->

- **Afiliação**: A afiliação pode ser **Interna** ou **Externa**. Para definir quais usuários e contas são internos, em **configurações**, certifique-se de definir o **intervalo de endereços IP** da sua organização interna. Se a conta tiver permissões de administrador, o ícone na tabela Contas aparecerá com a adição da gravata vermelha. ![ícone de administrador de contas](./media/accounts-admin-icon.png)

- **Aplicativo**: Você pode filtrar qualquer aplicativo conectado de API que esteja sendo usado por contas em sua organização.

- **Domínio**: Permite a filtragem de usuários em domínios específicos.

- **Grupos**: Permite a filtragem dos membros de grupos de usuários no Cloud App Security – grupos de usuários internos e grupos de usuários importados.

- **Instância**: Permite a filtragem dos membros de uma instância de aplicativo específica. 

- **Visto pela última vez em**: O filtro **Visto pela última vez em** permite localizar as contas que estão inativas e cujos usuários não executaram nenhuma atividade há algum tempo.

- **Organização**: Permite a filtragem dos membros de grupos organizacionais específicos definidos em seus aplicativos conectados.

- **Mostrar somente Administradores**: Filtre contas e usuários que são administradores.

- **Status**: Filtre com base no status da conta de usuário de N/D, de teste, ativa, suspensa ou excluída.

- **Tipo**: Permite a filtragem do usuário ou do tipo de conta.

- **Nome de usuário**: Permite a filtragem de usuários específicos. 


## <a name="next-steps"></a>Próximas etapas  
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   

[Os clientes Premier também podem criar um problema diretamente no portal Premier.](https://premier.microsoft.com/)  
  
  
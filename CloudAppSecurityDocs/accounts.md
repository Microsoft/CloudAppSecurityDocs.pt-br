---
title: Visibilidade das contas do dos aplicativos na nuvem | Microsoft Docs
description: "Este tópico pro."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/25/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 7811f23b-6100-427f-93b1-44f5f81f6c76
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: cc25a661cf7bd18be19e9e6fd82a4d39cf132c66
ms.sourcegitcommit: 50fac1cec86dfb8170ba9c63a8f58a4bf24e3c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2017
---
# <a name="accounts"></a>Contas
O Cloud App Security proporciona visibilidade das contas de seus aplicativos conectados. Depois que você conectar o Cloud App Security a um aplicativo usando o conector de aplicativos, o Cloud App Security lerá as informações da conta associadas aos aplicativos conectados. A página Contas permite que você investigue essas contas, as permissões, os grupos dos quais são membros, os aliases delas e os aplicativos que elas estão usando. Além disso, quando o Cloud App Security detecta uma nova conta que não foi vista anteriormente em um dos aplicativos conectados, por exemplo, nas atividades ou no compartilhamento de arquivos, a conta é adicionada à lista de contas deste aplicativo. Isso permite que você tenha visibilidade sobre a atividade de usuários externos interagindo com seus aplicativos em nuvem.


A página **Contas** pode ser filtrada para que você possa localizar contas específicas e se aprofundar em diferentes tipos de contas, por exemplo, você pode filtrar todas as contas Externas que não tenham sido acessadas desde o ano passado. 

A página **Contas** permite que você investigue facilmente suas contas quanto a problemas, incluindo o seguinte:  

-   Verifique se quaisquer contas estiveram inativas em um serviço específico por um longo período (talvez você deva revogar a licença desse usuário para esse serviço)  
-   Você pode filtrar a lista de usuários com permissões de administrador  

-   Você pode pesquisar usuários que não fazem mais parte da sua organização, mas que ainda podem ter contas ativas  

-   Você pode realizar ações de governança nas contas, como suspender um aplicativo ou acessar a página de configurações da conta de controle. Para obter uma lista completa de ações de governança, consulte o [log de controle](governance-actions.md).
    
-   Você pode ver quais contas estão incluídas em cada grupo de usuários  

-   Você pode ver quais aplicativos são acessados por cada conta e quais aplicativos são excluídos para contas específicas
    

![tela de contas](./media/accounts-page.png)

## <a name="account-filters"></a>Filtros de conta
Abaixo está uma lista de filtros de contas que podem ser aplicados. A maioria dos filtros dá suporte a vários valores, bem como NOT, para fornecer uma ferramenta muito poderosa para a criação de políticas.  
  
- **Nome da conta**: o nome da conta é o alias primário do usuário, mas outros identificadores de outras contas da Microsoft (Office 365 e Azure Active Directory), tais como endereços de proxy, aliases e SID, têm suporte e são consolidados sob o alias primário.

- **Afiliação**: a afiliação será **interna** ou **externa**. Para definir quais usuários e contas são internos, em **configurações**, certifique-se de definir o **intervalo de endereços IP** da sua organização interna. Se a conta tiver permissões de administrador, o ícone na tabela Contas aparecerá com a adição da gravata vermelha ![ícone de administrador de contas](./media/accounts-admin-icon.png).

- **Aplicativo**: você pode filtrar para qualquer aplicativo conectado de API que esteja sendo usado por contas em sua organização.

- **Domínio**: permite que você filtre para usuários em domínios específicos.

- **Visto pela última vez em**: o filtro **Visto pela última vez em** permite localizar as contas que estão inativas e cujos usuários não executaram nenhuma atividade há algum tempo.

- **Departamento/Organização**: permite que você filtre os membros de grupos organizacionais específicos definidos em seus aplicativos conectados.

- **Grupo de usuários**: permite que você filtre para membros de grupos de usuários no Cloud App Security – grupos de usuários internos e grupos de usuários importados.


## <a name="see-also"></a>Veja também  
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
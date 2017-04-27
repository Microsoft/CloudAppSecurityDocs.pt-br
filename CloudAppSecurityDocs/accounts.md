---
title: Visibilidade das contas do dos aplicativos na nuvem | Microsoft Docs
description: "Este tópico pro."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/23/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 7811f23b-6100-427f-93b1-44f5f81f6c76
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 5d5ccc55fe0d9c3fea93446daebfcbd5bbed8c8d
ms.sourcegitcommit: fd3b6c04cec30f7c9300cc02d29d562d17bf43ea
translationtype: HT
---
# <a name="accounts"></a>Contas
O Cloud App Security proporciona visibilidade de todas as contas de seus aplicativos conectados. Depois que você conectar o Cloud App Security a um aplicativo usando o conector de aplicativos, o Cloud App Security examina todas as contas associadas aos aplicativos. A página Contas permite investigar essas contas, os grupos dos quais são membros, os aliases delas e os aplicativos que elas estão usando. 


O log **Contas** pode ser filtrado para que você possa localizar contas específicas e se aprofundar em diferentes tipos de contas, por exemplo, você pode filtrar para todas as contas Externas que não tenham sido acessadas desde o ano passado. É possível criar políticas com base nas contas e, em seguida, definir sobre o que você deseja ser alertado e agir. 

A página **Contas** permite que você investigue facilmente suas contas quanto a problemas, incluindo o seguinte:  

-   Verifique se quaisquer contas estiveram inativas em um serviço específico por um longo período (talvez você deva revogar a licença desse usuário para esse serviço)  
-   Você pode filtrar a lista de usuários com permissões de administrador  

-   Você pode exibir as contas que estão ativas mas pertencem a usuários que não fazem mais parte da organização  

-   Você pode revogar a permissão do usuário para um aplicativo específico (dependendo do aplicativo) ou exigir que um usuário específico execute a autenticação multifator
    
-   Você pode ver quais contas estão incluídas em cada grupo de usuários  

-   Você pode ver quais aplicativos são acessados por cada conta e quais aplicativos são excluídos para contas específicas
    
-   Você também pode detalhar a conta do usuário e selecionar ações de governança relevantes, como **Suspender um usuário** ou **Remover colaborações do usuário**. Se o usuário foi importado do Azure Active Directory, você também pode clicar nas **Configurações da conta do Azure AD** para ter acesso fácil a recursos de gerenciamento de usuários Advanced, como gerenciamento de grupo, autenticação multifator, detalhes sobre as entradas do usuário e a possibilidade de bloquear a entrada.

![tela de contas](./media/accounts-page.png)

## <a name="account-filters"></a>Filtros de conta
Abaixo está uma lista de filtros de contas que podem ser aplicados. A maioria dos filtros dá suporte a vários valores, bem como NOT, para fornecer uma ferramenta muito poderosa para a criação de políticas.  
  
- **Nome da conta**: o nome da conta é o alias primário do usuário, mas outros identificadores de outras contas da Microsoft (Office 365 e Azure Active Directory), tais como endereços de proxy, aliases e SID, têm suporte e são consolidados sob o alias primário.

- **Afiliação**: a afiliação será **interna** ou **externa**. Para definir quais usuários e contas são internos, em **configurações**, certifique-se de definir o **intervalo de endereços IP** da sua organização interna. Se a conta tiver permissões de administrador, o ícone na tabela Contas aparecerá com a adição da gravata vermelha ![ícone de administrador de contas](./media/accounts-admin-icon.png).

- **Aplicativo**: você pode filtrar para qualquer aplicativo conectado de API que esteja sendo usado por contas em sua organização.

- **Domínio**: permite que você filtre para usuários em domínios específicos.

- **Visto pela última vez em**: o filtro **Visto pela última vez em** permite localizar as contas que estão inativas e cujos usuários não executaram nenhuma atividade há algum tempo.

- **Departamento/Organização**: permite que você filtre para membros de grupos organizacionais do Office 365 ou do Azure Active Directory.

- **Grupo de usuários**: permite que você filtre para membros de grupos de usuários no Cloud App Security – grupos de usuários internos e grupos de usuários importados.


## <a name="see-also"></a>Veja também  
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
---
title: "Importar grupos de usuários de aplicativos conectados | Microsoft Docs"
description: "Este tópico fornece instruções de importação de seus grupos de usuários para Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/4/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 87b831ef-5977-4df8-bed3-3ee54a8adbb5
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 451d88f6403e62ed5cf68d5a932e5029f270df7a
ms.sourcegitcommit: 34cd68651b5a1be9bc460d7175bc2711efa103b2
ms.translationtype: HT
ms.contentlocale: pt-BR
---
# <a name="import-user-groups"></a>Importar grupos de usuários

Quando você conecta aplicativos usando conectores de API, o Cloud App Security permite que você importe grupos de usuários, por exemplo do Office 365 e do Azure Active Directory.
Há dois tipos de grupos de usuários: 
- Grupos automáticos </br>Grupos automáticos são criados por padrão pelo Cloud App Security. Por exemplo, há um grupo de usuários automático chamado **Externo**, que combina todos os usuários de todos os aplicativos que são externos à sua organização e tem acesso aos arquivos ou estavam em atividades do usuário em seu locatário.
 Os seguintes grupos automáticos existem no Cloud App Security:
  - Externa
  - Administrador do Dropbox
  - Administrador do Office 365
  - Administrador do G Suite
  - Administrador do Box
  - Todos os perfis personalizados e padrão do Salesforce, por exemplo o Administrador de Sistema do Salesforce. Consulte a lista completa [aqui](https://help.salesforce.com/articleView?id=standard_profiles.htm&language=en&type=0).

- Grupos importados</br>Você pode importar qualquer grupo de seus aplicativos conectados. Por exemplo, você pode importar grupos de usuários do Office 365 (Active Directory) e outros aplicativos conectados. Isso permite que você procure ameaças na organização ao observar um grupo específico e não ao observar a organização inteira ou um usuário específico. 

Os cenários típicos que aproveitam os grupos de usuários importados incluem: você pode investigar os documentos que as pessoas de RH observam, verificar se há algo incomum acontecendo no grupo de executivos ou se alguém do grupo administradores realizou uma atividade fora dos EUA. Para importar grupos de usuários:

1. Na barra de menus, clique no ícone de configurações ![ícone de configurações](./media/settings-icon.png "ícone de configurações") e selecione **Grupos de usuários**.
2. Clique em **Importar grupo de usuários**.

  ![Importar grupos de usuários](./media/user-groups-add.png)

3. Selecione o aplicativo do qual deseja importar o grupo de usuários. A lista de aplicativos dependerá de qual Conector de Aplicativo você implantou.
4. Selecione o grupo a ser importado. A lista de grupos disponíveis será uma lista de todos os grupos de usuário existente no próprio aplicativo. Se quiser adicionar um novo grupo, você precisará fazê-lo diretamente no próprio aplicativo e quando ele for exibido, selecione-o.
4. Dependendo do tamanho do grupo, a importação pode demorar até uma hora. Você pode selecionar a opção para ser notificado por email quando o processo de importação for concluído.
5. Clique em **Importar**. Depois de importar um grupo, o Cloud App Security sincroniza automaticamente os membros do grupo, assim como faz o Active Directory Connect.
7. Depois que a importação for concluída, na página **Grupos de usuários**, você pode clicar em um grupo específico para exibir uma lista de todos os membros do grupo. Você também pode clicar em qualquer membro do grupo mais se aprofundar nos detalhes de uma conta específica e exibir quais aplicativos são usados, além de um resumo da conta, incluindo gráficos do usuário e suas atividades.

A importação de grupos permite que você selecione os grupos como filtros ao investigar no **Log de atividades** e ao criar políticas. 

> [!NOTE]
> Somente as atividades executadas após a importação de um grupo de usuários serão marcadas como tendo sido executada por um membro do grupo de usuários.

Para obter mais informações sobre como usar os filtros de grupo de usuários, consulte [Atividades](activity-filters.md).


    
## <a name="see-also"></a>Consulte Também  
[Configurar o Cloud Discovery](set-up-cloud-discovery.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
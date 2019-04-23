---
title: Gerenciar o acesso de administrador ao portal do Cloud App Security
description: Este artigo fornece instruções para definir o acesso ao portal do Cloud App Security para seus administradores.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: barbkess
ms.date: 04/04/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: b718edad-350c-4d90-b045-92529d701dc5
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: ad619e9d8d1503fc91b4e52b0b11bfaf22b8124e
ms.sourcegitcommit: b0ae3a969a85a1ae0332a30efd058e415d9efb5c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59904304"
---
# <a name="manage-admin-access"></a>Gerenciar acesso de administrador

*Aplica-se a: Microsoft Cloud App Security*

O Microsoft Cloud App Security é compatível com o controle de acesso baseado em função. Este artigo fornece instruções para definir o acesso ao portal do Cloud App Security para seus administradores. Para obter mais informações sobre como atribuir funções de administrador, confira os artigos [Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles) e [Office 365](https://docs.microsoft.com/office365/admin/add-users/assign-admin-roles).

## <a name="office-365-and-azure-ad-roles-with-access-to-cloud-app-security"></a>Funções do Office 365 e do Azure AD com acesso ao Cloud App Security

Por padrão, as seguintes funções de administrador do Office 365 e do [Azure Active Directory (Azure AD)](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles) têm acesso ao Microsoft Cloud App Security:

- **Administrador global e administrador de segurança:** Os administradores com **Acesso completo** têm permissões completas no Cloud App Security. Eles podem adicionar administradores, adicionar políticas e configurações, fazer upload de logs e executar ações de governança.

- **Administrador de conformidade:** Tem permissões somente leitura e pode gerenciar alertas. Pode criar e modificar políticas de arquivo, permitir ações de governança de arquivo e exibir todos os relatórios internos em Gerenciamento de dados. 

- **Leitor de segurança:** Tem permissões somente leitura e pode gerenciar alertas. O Leitor de segurança não tem permissão para executar as seguintes ações:

  - Criar políticas e editar as existentes 
  - Executar ações de controle 
  - Carregar logs de descoberta
  - Proibir ou aprovar aplicativos de terceiros
  - Acessar e exibir a página de configurações de intervalo de endereço IP
  - Acessar e exibir páginas de configurações 
  - Acessar e exibir as configurações de Descoberta 
  - Acessar e exibir a página de Conectores de aplicativo
  - Acessar e exibir o Log de controle 
  - Acessar e exibir a página Gerenciar relatórios de instantâneo 

- **Administrador de aplicativo/instância:** Tem permissões em todos os dados no Microsoft Cloud App Security relacionados exclusivamente ao aplicativo ou à instância específica de um aplicativo selecionado. Por exemplo, você concede uma permissão de administrador de usuários à sua instância europeia do Box. O administrador verá apenas os dados relacionados à instância europeia do Box, sejam arquivos, atividades, políticas ou alertas:

  - Página de atividades – somente atividades sobre o aplicativo específico
  - Alertas – somente alertas relacionados ao aplicativo específico
  - Políticas – pode exibir todas as políticas e editar ou criar somente as políticas relacionadas exclusivamente ao aplicativo/à instância
  - Página de contas – somente contas para a instância/o aplicativo específico
  - Permissões de aplicativo – somente permissões para a instância/o aplicativo específico
  - Página de arquivos – somente arquivos de instância/aplicativo específico
  - Controle de Aplicativo de Acesso Condicional: sem permissões
  - Atividade do descoberta Cloud Discovery: sem permissões
  - Extensões de segurança – permissões somente para o token de API com permissões de usuário
  - Ações de governança – somente para a instância/o aplicativo específico 

- **Administrador de grupo de usuários:** Tem permissões em todos os dados no Microsoft Cloud App Security relacionados exclusivamente ao grupo específico selecionado aqui. Por exemplo, se você conceder a permissão de administrador de usuários ao grupo "Alemanha – todos os usuários", o administrador poderá exibir e modificar as informações no Microsoft Cloud App Security somente para esse grupo de usuários:

  - Página de atividades – somente atividades relacionadas aos usuários do grupo
  - Alertas – somente alertas relacionados aos usuários do grupo
  - Políticas – pode exibir todas as políticas e editar ou criar somente as políticas relacionadas exclusivamente aos usuários do grupo
  - Página de contas – somente contas dos usuários específicos do grupo
  - Permissões de aplicativo: nenhuma permissão
  - Página de arquivos: nenhuma permissão
  - Controle de Aplicativo de Acesso Condicional: sem permissões
  - Atividade do descoberta Cloud Discovery: sem permissões
  - Extensões de segurança – permissões somente para o token de API com usuários do grupo
  - Ações de governança – somente para os usuários específicos do grupo

- **Administrador global de descoberta de nuvem:**  Tem permissão para exibir e editar todos os dados e configurações do Cloud Discovery. O administrador de Descoberta Global tem acesso da seguinte maneira:

  - Configurações – 
     -  Configurações do sistema – somente exibição
     - Configurações do Cloud Discovery – exibir e editar tudo (permissões de anonimização dependem se ele recebeu autorização durante a atribuição de função)
  - Atividade do Cloud Discovery – todas as permissões
  - Alertas – somente alertas relacionados a dados do Cloud Discovery
  - Políticas – pode exibir todas as políticas e editar ou criar somente as políticas do Cloud Discovery
  - Página de atividades – nenhuma permissão
  - Página de contas – nenhuma permissão
  - Permissões de aplicativo: nenhuma permissão
  - Página de arquivos: nenhuma permissão
  - Controle de Aplicativo de Acesso Condicional: sem permissões
  - Extensões de segurança – nenhuma permissão
  - Ações de governança – apenas ações relacionadas ao Cloud Discovery

- **Administrador de relatório de descoberta de nuvem:** Tem permissão para exibir todos os dados no Microsoft Cloud App Security que selecionou lida exclusivamente com os relatórios específicos do Cloud Discovery. Por exemplo, você pode conceder a alguém permissão de administrador para o relatório contínuo do Microsoft Defender ATP. O administrador de descoberta verá apenas os dados de descoberta de nuvem que relaciona a essa fonte de dados e o catálogo de aplicativos.
Este administrador não terá acesso para o **atividades** ou **arquivos** páginas e acesso limitado a políticas.

- **Leitor global:** Tem acesso somente leitura completa a todos os aspectos do Microsoft Cloud App Security. Não é possível alterar as configurações ou tomar qualquer ação.
 
## <a name="override-admin-permissions"></a>Substituir permissões de administrador

Se você quiser substituir a permissão do administrador no Azure Active Directory ou no Office 365, faça isso manualmente adicionando o usuário ao Cloud App Security e atribuindo permissões de usuário.
Por exemplo, caso deseje atribuir a Sara, um Leitor de segurança no Azure Active Directory, o **Acesso completo** no Cloud App Security, adicione-a manualmente ao Cloud App Security e atribua a ela o **Acesso completo** para substituir sua função e conceder a ela as permissões necessárias no Cloud App Security. 

## <a name="add-additional-admins"></a>Adicionar administradores adicionais

Adicione também outros administradores ao Cloud App Security sem adicionar usuários a funções administrativas do Azure Active Directory. Para adicionar outros administradores, realize as seguintes etapas:

   >[!IMPORTANT]
   > Somente Administradores globais ou Administradores de segurança podem conceder acesso a outros usuários ao Cloud App Security.


1. Clique na engrenagem de configurações ![ícone de configurações](./media/settings-icon.png "ícone de configurações") e, em seguida, em **Gerenciar acesso de administrador**. 

2. Clique no sinal de adição para adicionar os administradores que devem ter acesso ao Cloud App Security. Você pode digitar um endereço de email interno ou externo para permitir que administradores internos da organização ou MSSPs (Provedores de Serviço de Segurança Gerenciada) externos administrem seus alertas de segurança.
  
   ![adicionar administradores](./media/add-admin.png)

3. Em seguida, clique na lista suspensa para definir o tipo de função do administrador, **Administrador global**, **Leitor de segurança**, **Administrador de conformidade** ou **Administrador de aplicativo/instância**. Se você selecionar **Administrador de aplicativo/instância**, selecione o aplicativo e a instância aos quais o administrador terá permissões.

     >[!NOTE]
      >Qualquer administrador, cujo acesso é limitado, que tentar acessar uma página restrita ou executar uma ação restrita receberá um erro indicando que ele não tem permissão para acessar a página ou executar a ação.

4. Clique em **Adicionar administrador**.  

## <a name="invite-external-admins"></a>Convidar administradores externos

O Microsoft Cloud App Security permite convidar MSSPs (Provedores de Serviço de Segurança Gerenciada) externos para serem administradores do portal do Microsoft Cloud App Security. Agora, os usuários externos podem ser configurados como administradores e atribuídos a uma das funções disponíveis no Microsoft Cloud App Security. Além disso, para permitir que os MSSPs forneçam serviços em vários locatários de cliente, os Administradores que têm direitos de acesso a mais de um locatário agora podem alternar locatários com facilidade no portal. 

Para alternar locatários, depois de receber permissões para vários locatários, clique no ícone de usuário. Você verá uma lista dos locatários para os quais você tem permissões. Selecione o locatário que deseja gerenciar.

![escolher locatário](./media/choose-tenant.png "escolher locatário")

## <a name="next-steps"></a>Próximas etapas  
[Configurar o Cloud Discovery](set-up-cloud-discovery.md)   
  
  
  

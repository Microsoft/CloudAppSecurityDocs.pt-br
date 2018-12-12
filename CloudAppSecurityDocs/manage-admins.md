---
title: Gerenciar acesso de administrador ao portal do Cloud App Security | Microsoft Docs
description: Este artigo fornece instruções para definir o acesso ao portal do Cloud App Security para seus administradores.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/9/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: b718edad-350c-4d90-b045-92529d701dc5
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 23fe11600fc802e0c4f4d8024b78fa2713cc4a63
ms.sourcegitcommit: c497253a7ab63973bb806607e5f15dece91640be
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53123951"
---
# <a name="manage-admin-access"></a>Gerenciar acesso de administrador

*Aplica-se ao: Microsoft Cloud App Security*

O Microsoft Cloud App Security é compatível com o Controle de acesso baseado em função. Por padrão, algumas [funções de administrador do Office 365](https://docs.microsoft.com/office365/admin/add-users/about-admin-roles) e [funções de administrador do Azure AD (Azure Active Directory)](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles) têm acesso ao Microsoft Cloud App Security. Este artigo fornece instruções para definir o acesso ao portal do Cloud App Security para seus administradores. Para obter mais informações sobre como atribuir funções de administrador, confira os artigos [Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles) e [Office 365](https://docs.microsoft.com/office365/admin/add-users/assign-admin-roles).

## <a name="office-365-and-azure-ad-roles-with-access-to-cloud-app-security"></a>Funções do Office 365 e do Azure AD com acesso ao Cloud App Security

Por padrão, as seguintes funções de administrador do Office 365 e o Azure AD têm acesso ao Microsoft Cloud App Security:

- **Administrador global e Administrador de segurança:** os administradores com **Acesso completo** têm permissões completas no Cloud App Security. Eles podem adicionar administradores, adicionar políticas e configurações, fazer upload de logs e executar ações de governança.

- **Administrador de conformidade:** tem permissões somente leitura e pode gerenciar alertas. Pode criar e modificar políticas de arquivo, permitir ações de governança de arquivo e exibir todos os relatórios internos em Gerenciamento de dados. 

- **Leitor de segurança:** tem permissões somente leitura e pode gerenciar alertas. O Leitor de segurança não tem permissão para executar as seguintes ações:

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

- **Administrador de aplicativo/instância:** tem permissões a todos os dados no Microsoft Cloud App Security relacionados exclusivamente ao aplicativo ou à instância específica de um aplicativo selecionado. Por exemplo, você concede uma permissão de administrador de usuários à sua instância europeia do Box. O administrador verá apenas os dados relacionados à instância europeia do Box, sejam arquivos, atividades, políticas ou alertas, da seguinte maneira:

  - Página de atividades – somente atividades sobre o aplicativo específico
  - Alertas – somente alertas relacionados ao aplicativo específico
  - Políticas – pode exibir todas as políticas e editar ou criar somente as políticas relacionadas exclusivamente ao aplicativo/à instância
  - Conta – somente contas para a instância/o aplicativo específico
  - Permissões de aplicativo – somente permissões para a instância/o aplicativo específico
  - Página de arquivos – somente arquivos de instância/aplicativo específico
  - Controle de Aplicativo de Acesso Condicional: sem permissões
  - Atividade do descoberta Cloud Discovery: sem permissões
  - Extensões de segurança – permissões somente para o token de API com permissões de usuário
  - Ações de governança – somente para a instância/o aplicativo específico 

- **Administrador de grupos:** tem permissões a todos os dados no Microsoft Cloud App Security relacionados exclusivamente ao grupo específico selecionado aqui. Por exemplo, se você conceder a permissão de administrador de usuários ao grupo "Alemanha – todos os usuários", o administrador poderá exibir e modificar as informações no Microsoft Cloud App Security somente para esse grupo de usuários, da seguinte maneira:

  - Página de atividades – somente atividades relacionadas aos usuários do grupo
  - Alertas – somente alertas relacionados aos usuários do grupo
  - Políticas – pode exibir todas as políticas e editar ou criar somente as políticas relacionadas exclusivamente aos usuários do grupo
  - Conta – somente contas dos usuários específicos do grupo
  - Permissões de aplicativo: nenhuma permissão
  - Página de arquivos: nenhuma permissão
  - Controle de Aplicativo de Acesso Condicional: sem permissões
  - Atividade do descoberta Cloud Discovery: sem permissões
  - Extensões de segurança – permissões somente para o token de API com usuários do grupo
  - Ações de governança – somente para os usuários específicos do grupo


## <a name="override-admin-permissions"></a>Substituir permissões de administrador

Se você quiser substituir a permissão do administrador no Azure Active Directory ou no Office 365, faça isso manualmente adicionando o usuário ao Cloud App Security e atribuindo permissões de usuário.
Por exemplo, caso deseje atribuir a Sara, um Leitor de segurança no Azure Active Directory, o **Acesso completo** no Cloud App Security, adicione-a manualmente ao Cloud App Security e atribua a ela o **Acesso completo** para substituir sua função e conceder a ela as permissões necessárias no Cloud App Security. 

## <a name="add-additional-admins"></a>Adicionar administradores adicionais

Adicione também outros administradores ao Cloud App Security sem adicionar usuários a funções administrativas do Azure Active Directory. Para adicionar outros administradores, siga as seguintes etapas:

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

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  

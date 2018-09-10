---
title: Gerenciar acesso de administrador ao portal do Cloud App Security | Microsoft Docs
description: Este tópico fornece instruções para configurar o acesso ao portal do Cloud App Security para seus administradores.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 6/24/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: b718edad-350c-4d90-b045-92529d701dc5
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 623c2c5e89da95f550c35f346a27dede245195b1
ms.sourcegitcommit: 0ac08ca7b3140b79f1d36ff7152476c188fa12b3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44144390"
---
*Aplica-se ao: Microsoft Cloud App Security*


# <a name="manage-admin-access"></a>Gerenciar acesso de administrador

O Microsoft Cloud App Security é compatível com o Controle de acesso baseado em função. Por padrão, as seguintes funções de administrador do Office 365 e o Azure AD têm acesso ao Microsoft Cloud App Security:

- Administrador global e Administrador de segurança: administradores com **Acesso completo** têm permissão total no Cloud App Security para adicionar administradores, adicionar políticas e configurações, carregar logs e executar ações de controle.

- Administrador de conformidade: tem permissões somente leitura e pode gerenciar alertas. Pode criar e modificar políticas de arquivo, permitir ações de governança de arquivo e exibir todos os relatórios internos em Gerenciamento de dados. 

- Leitor de segurança: tem permissões somente leitura e pode gerenciar alertas. O Leitor de segurança não tem permissão para executar o seguinte:

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

- Administrador de aplicativo/instância: tem permissões para todos os dados no Microsoft Cloud App Security relacionados exclusivamente ao aplicativo ou instância específica de um aplicativo selecionado aqui. Por exemplo, se você conceder uma permissão de administrador de usuário à sua instância do Box European, o administrador poderá ver somente os dados relacionados a essa instância do aplicativo, como arquivos, atividades, políticas ou alertas, da seguinte maneira:

  - Página de atividades: somente atividades relacionadas ao aplicativo específico
  - Alertas: somente alertas relacionados ao aplicativo específico
  - Políticas: podem exibir todas as políticas e editar ou criar somente as políticas que lidam exclusivamente com o aplicativo/instância
  - Conta: somente contas para o aplicativo/instância específico
  - Permissões de aplicativo: somente as permissões para o aplicativo/instância específico
  - Página de arquivos: somente arquivos de aplicativo/instância específico
  - Controle de Aplicativo de Acesso Condicional: sem permissões
  - Atividade do descoberta Cloud Discovery: sem permissões
  - Extensões de segurança: permissões apenas para o token de API com permissões de usuário
  - Ações de governança: apenas para o aplicativo/instância específico 

- Administrador de grupo: tem permissões para todos os dados no Microsoft Cloud App Security, relacionados exclusivamente ao grupo específico selecionado aqui. Por exemplo, se você conceder permissão de administrador ao usuário para o grupo "Alemanha – Todos os usuários", o administrador será capaz de exibir e modificar as informações no Microsoft Cloud App Security somente para esse grupo de usuários, da seguinte maneira:

  - Página de atividades: somente atividades relacionadas aos usuários do grupo
  - Alertas: somente alertas relacionados aos usuários do grupo
  - Políticas: podem exibir todas as políticas e editar ou criar somente as políticas que lidam exclusivamente com os usuários do grupo
  - Conta: somente contas de usuários específicos do grupo
  - Permissões de aplicativo: nenhuma permissão
  - Página de arquivos: nenhuma permissão
  - Controle de Aplicativo de Acesso Condicional: sem permissões
  - Atividade do descoberta Cloud Discovery: sem permissões
  - Extensões de segurança: permissões somente para o token de API com usuários do grupo
  - Ações de governança: somente para usuários específicos do grupo



Para obter mais informações, consulte [Atribuindo funções de administrador no Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-assign-admin-roles).

Você também pode adicionar administradores adicionais ao Cloud App Security, sem adicionar usuários a funções administrativas do Azure Active Directory, executando as seguintes etapas:

1. Clique na engrenagem de configurações ![ícone de configurações](./media/settings-icon.png "ícone de configurações") e, em seguida, em **Gerenciar administradores**. 

2. Clique no sinal de adição para adicionar os administradores que devem ter acesso ao Cloud App Security. Você pode digitar um endereço de email interno ou externo para permitir que administradores internos da organização ou MSSPs (Provedores de Serviço de Segurança Gerenciada) externos administrem seus alertas de segurança.
  
  ![adicionar administradores](./media/add-admin.png)
    
3. Em seguida, clique na lista suspensa para definir o tipo de função do administrador, **Administrador global**, **Leitor de segurança**, **Administrador de conformidade** ou **Administrador de aplicativo/instância**. Se você selecionar **Administrador de aplicativo/instância**, selecione o aplicativo e a instância aos quais o administrador terá permissões.

     >[!NOTE]
      >Qualquer administrador com acesso limitado que tentar acessar uma página restrita ou executar uma ação restrita receberá um erro indicando que não tem permissão para acessar a página ou executar a ação.
4. Clique em **Adicionar administrador**.  

   >[!NOTE]
    >Somente Administradores globais ou Administradores de segurança podem conceder acesso a outros usuários ao Cloud App Security.


## <a name="override-admin-permissions"></a>Substituir permissões de administrador

Se você quiser substituir a permissão do administrador no Azure Active Directory ou no Office 365, faça isso manualmente adicionando o usuário ao Cloud App Security e atribuindo permissões de usuário.
Por exemplo, se você quiser atribuir à Stephanie, uma Leitora de segurança no Azure Active Directory, o **Acesso completo** no Cloud App Security, adicione-a manualmente ao Cloud App Security e atribua a ela o **Acesso completo** a fim de substituir sua função e permitir a ela as permissões desejadas no Cloud App Security. 

## <a name="add-additional-admins"></a>Adicionar administradores adicionais

Para adicionar outros administradores ao Cloud App Security:
1. Clique na engrenagem de configurações ![ícone de configurações](./media/settings-icon.png "ícone de configurações") e, em seguida, em **Gerenciar acesso de administrador**. 

2. Adicione os administradores que devem ter acesso ao Cloud App Security. Selecione o nível de acesso e clique em **Fechar**.

  
## <a name="invite-external-admins"></a>Convidar administradores externos

O Microsoft Cloud App Security permite convidar MSSPs (Provedores de Serviço de Segurança Gerenciada) externos para serem administradores do portal do Microsoft Cloud App Security. Agora, os usuários externos podem ser configurados como administradores e atribuídos a uma das funções disponíveis atualmente no Microsoft Cloud App Security. Além disso, para permitir que os MSSPs forneçam serviços entre vários locatários de clientes, os administradores que têm direitos de acesso a mais de um locatário agora podem mudar de locatário facilmente no portal. 

Para mudar de locatário, depois de receber permissões para vários locatários, clique no ícone de usuário ![ícone de usuário](./media/user-icon.png "ícone de usuário"). Será exibida uma lista dos locatários para os quais você tem permissões. Selecione o locatário que deseja gerenciar.

![escolher locatário](./media/choose-tenant.png "escolher locatário")

## <a name="see-also"></a>Consulte Também  
[Configurar o Cloud Discovery](set-up-cloud-discovery.md)   

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
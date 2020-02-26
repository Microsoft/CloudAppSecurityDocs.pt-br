---
title: Gerenciar o acesso de administrador ao portal de Cloud App Security
description: Este artigo fornece instruções para configurar o acesso ao portal de Cloud App Security para seus administradores.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 02/25/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: f36b3e09abdc8f10a1e3fa5b59b32101f13f1065
ms.sourcegitcommit: c5d288898630c949bab6538f59ae196ff9bbb909
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77599753"
---
# <a name="manage-admin-access"></a>Gerenciar o acesso de administrador

*Aplica-se a: Microsoft Cloud App Security*

O Microsoft Cloud App Security dá suporte ao controle de acesso baseado em função. Este artigo fornece instruções para configurar o acesso ao portal de Cloud App Security para seus administradores. Para obter mais informações sobre como atribuir funções de administrador, consulte os artigos para [Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles) e [Office 365](https://docs.microsoft.com/office365/admin/add-users/assign-admin-roles).

## <a name="office-365-and-azure-ad-roles-with-access-to-cloud-app-security"></a>Funções do Office 365 e do Azure AD com acesso ao Cloud App Security

Por padrão, as seguintes funções de administrador do Office 365 e [do Azure Active Directory (Azure AD)](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles) têm acesso ao Cloud app Security:

- Administrador **global e administrador de segurança:** Os administradores com **acesso completo** têm permissões totais no Cloud app Security. Eles podem adicionar administradores, adicionar políticas e configurações, carregar logs e executar ações de governança.

- **Administrador de conformidade:** Tem permissões somente leitura e pode gerenciar alertas. Pode criar e modificar políticas de arquivo, permitir ações de governança de arquivo e exibir todos os relatórios internos em Gerenciamento de Dados.

- **Administrador de dados de conformidade:** Tem permissões somente leitura, pode criar e modificar políticas de arquivo, permitir ações de governança de arquivo e exibir todos os relatórios de descoberta.

- **Operador de segurança:** Tem permissões somente leitura e pode gerenciar alertas.

- **Leitor de segurança:** Tem permissões somente leitura e pode gerenciar alertas. O leitor de segurança é restrito de executar as seguintes ações:

  - Criar políticas e editar as existentes
  - Executar ações de controle
  - Carregar logs de descoberta
  - Proibindo ou aprovando aplicativos de terceiros
  - Acessar e exibir a página de configurações de intervalo de endereço IP
  - Acessar e exibir páginas de configurações
  - Acessando e exibindo as configurações de descoberta
  - Acessando e exibindo a página de conectores de aplicativos
  - Acessar e exibir o Log de controle
  - Acessar e exibir a página Gerenciar relatórios de instantâneo
  - Acessando e editando o agente SIEM

- **Leitor global:** Tem acesso completo somente leitura a todos os aspectos de Microsoft Cloud App Security. Não é possível alterar nenhuma configuração ou executar ações.

Além disso, as seguintes Cloud App Security funções de administrador específicas podem ser configuradas no portal de Cloud App Security:

- **Administrador de aplicativo/instância:** Tem permissões completas ou somente leitura para todos os dados em Microsoft Cloud App Security que lidam exclusivamente com o aplicativo ou instância específica de um aplicativo selecionado. Por exemplo, você concede uma permissão de administrador de usuário à sua instância Europeia do box. O administrador verá apenas os dados relacionados à instância européia do box, seja arquivos, atividades, políticas ou alertas:

  - Atividades somente de página de atividades sobre o aplicativo específico
  - Alertas somente alertas relacionados ao aplicativo específico
  - Políticas – pode exibir todas as políticas e se as permissões completas atribuídas podem editar ou criar somente políticas que lidam exclusivamente com o aplicativo/instância
  - Contas somente página de contas para o aplicativo/instância específico
  - Permissões de aplicativo-somente permissões para o aplicativo/instância específico
  - Arquivos somente página arquivos do aplicativo/instância específico
  - Controle de Aplicativos de Acesso Condicional-sem permissões
  - Cloud Discovery atividade-sem permissões
  - Extensões de segurança-permissões somente para o token de API com permissões de usuário
  - Ações de governança-somente para o aplicativo/instância específico

- **Administrador do grupo de usuários:** Tem permissões completas ou somente leitura para todos os dados em Microsoft Cloud App Security que lidam exclusivamente com o grupo específico selecionado aqui. Por exemplo, se você conceder a um usuário permissão de administrador para o grupo "Alemanha-todos os usuários", o administrador poderá exibir e modificar informações em Microsoft Cloud App Security somente para esse grupo de usuários:

  - Atividades somente página de atividades sobre os usuários no grupo
  - Alertas somente alertas relacionados aos usuários no grupo
  - Políticas – pode exibir todas as políticas e se as permissões completas atribuídas podem editar ou criar somente as políticas que lidam exclusivamente com os usuários no grupo
  - Contas de contas somente de página para usuários específicos no grupo
  - Permissões de aplicativo – sem permissões
  - Página arquivos – sem permissões
  - Controle de Aplicativos de Acesso Condicional-sem permissões
  - Cloud Discovery atividade-sem permissões
  - Extensões de segurança-permissões somente para o token de API com usuários no grupo
  - Ações de governança-somente para usuários específicos no grupo

- **Cloud Discovery administrador global:**  Tem permissão para exibir e editar todos os Cloud Discovery configurações e dados. O administrador de descoberta global tem acesso da seguinte maneira:

  - Configurações
    - Configurações do sistema – somente exibição
    - Configurações de Cloud Discovery-exibir e editar tudo (as permissões de anonimato dependem de terem sido permitidas durante a atribuição de função)
  - Atividade de Cloud Discovery-permissões totais
  - Alertas somente alertas relacionados a dados de Cloud Discovery
  - Políticas – pode exibir todas as políticas e pode editar ou criar apenas Cloud Discovery políticas
  - Página de atividades-sem permissões
  - Página contas-sem permissões
  - Permissões de aplicativo – sem permissões
  - Página arquivos – sem permissões
  - Controle de Aplicativos de Acesso Condicional-sem permissões
  - Extensões de segurança-sem permissões
  - Ações de governança-somente Cloud Discovery ações relacionadas

- **Administrador do relatório de Cloud Discovery:** Tem permissões para exibir todos os dados em Microsoft Cloud App Security que lidam exclusivamente com os relatórios de Cloud Discovery específicos selecionados. Por exemplo, você pode conceder a alguém permissão de administrador para o relatório contínuo do Microsoft defender ATP. O administrador de descoberta verá apenas os dados Cloud Discovery relacionados a essa fonte de dados e ao catálogo de aplicativos.
Esse administrador não terá acesso às páginas de **atividades** ou **arquivos** e acesso limitado às políticas.

## <a name="override-admin-permissions"></a>Substituir permissões de administrador

Se você quiser substituir a permissão de um administrador do Azure Active Directory ou do Office 365, poderá fazer isso adicionando manualmente o usuário ao Cloud App Security e atribuindo as permissões de usuário.
Por exemplo, se você quiser atribuir Stephanie, que é um leitor de segurança no Azure Active Directory ter **acesso completo** no Cloud app Security, você pode adicioná-lo manualmente ao Cloud app Security e atribuir a ele **acesso completo** para substituir sua função e permitir que ela tenha as permissões necessárias no Cloud app Security.

## <a name="add-additional-admins"></a>Adicionar administradores adicionais

Você pode adicionar outros administradores a Cloud App Security sem adicionar usuários a Azure Active Directory funções administrativas. Para adicionar outros administradores, execute as seguintes etapas:

> [!IMPORTANT]
> Somente administradores globais ou administradores de segurança podem conceder acesso a outros usuários para Cloud App Security.

1. Clique no ícone configurações ![configurações](media/settings-icon.png "ícone de configurações") de engrenagem e **gerenciar acesso de administrador**.

2. Clique no sinal de adição para adicionar os administradores que devem ter acesso ao Cloud App Security. Você pode digitar um endereço de email interno ou externo para habilitar os administradores de dentro da sua organização ou MSSPs (provedores de serviços de segurança gerenciados) externos para administrar seus alertas de segurança.

    ![adicionar administradores](media/add-admin.png)

3. Em seguida, clique na lista suspensa para definir o tipo de função que o administrador tem, **administrador global**, **leitor de segurança**, administrador de **conformidade**ou **administrador de aplicativo/instância**. Se você selecionar **administrador de aplicativo/instância**, selecione o aplicativo e a instância para o qual o administrador tem permissões.

    >[!NOTE]
    >Qualquer administrador, cujo acesso é limitado, que tenta acessar uma página restrita ou executar uma ação restrita receberá um erro informando que eles não têm permissão para acessar a página ou executar a ação.

4. Clique em **Adicionar Administrador**.

## <a name="admin-activity-auditing"></a>Auditoria de atividade do administrador

Cloud App Security permite exportar um log de todas as atividades de administrador, incluindo a auditoria de um administrador investigando um usuário específico ou exibindo alertas específicos.

Para exportar um log, execute as seguintes etapas:

1. Na página **gerenciar acesso de administradores** , selecione **Exportar atividades de administrador**.

1. Especifique o intervalo de tempo necessário.

1. Clique em **Exportar**.

## <a name="invite-external-admins"></a>Convidar administradores externos

Cloud App Security permite que você convide provedores de serviço de segurança gerenciados externos (MSSPs) como administradores do seu portal de Cloud App Security. Os usuários externos agora podem ser configurados como administradores e atribuídos a qualquer uma das funções disponíveis no Cloud App Security. Além disso, para permitir que o MSSPs forneça serviços em vários locatários de clientes, os administradores que têm direitos de acesso a mais de um locatário agora podem facilmente alternar locatários no Portal.

Para alternar entre locatários, depois de ter permissões para vários locatários, clique no ícone de usuário. Você verá uma lista dos locatários para os quais você tem permissões. Selecione o locatário que você deseja gerenciar.

![escolher locatário](media/choose-tenant.png "escolher locatário")

## <a name="next-steps"></a>{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}  

> [!div class="nextstepaction"]
> [Configurar Cloud Discovery](set-up-cloud-discovery.md)

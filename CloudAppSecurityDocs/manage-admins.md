---
title: Gerenciar o acesso de administrador ao portal do Cloud App Security
description: Este artigo fornece instruções para definir o acesso ao portal do Cloud App Security para seus administradores.
ms.date: 11/25/2020
ms.topic: how-to
ms.openlocfilehash: ef72326fd8c02b40230074c9029a091b8d0cc24a
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96314997"
---
# <a name="manage-admin-access"></a>Gerenciar acesso de administrador

[!INCLUDE [Banner for top of topics](includes/banner.md)]

O Microsoft Cloud App Security dá suporte ao controle de acesso baseado em função. Este artigo fornece instruções para definir o acesso ao portal do Cloud App Security para seus administradores. Para obter mais informações sobre como atribuir funções de administrador, consulte os artigos para [Azure Active Directory](/azure/active-directory/active-directory-assign-admin-roles) e [Office 365](/office365/admin/add-users/assign-admin-roles).

## <a name="office-365-and-azure-ad-roles-with-access-to-cloud-app-security"></a>Funções do Office 365 e do Azure AD com acesso ao Cloud App Security

Por padrão, as seguintes funções de administrador do Office 365 e [do Azure Active Directory (Azure AD)](/azure/active-directory/users-groups-roles/directory-assign-admin-roles) têm acesso ao Cloud app Security:

- **Administrador global e Administrador de segurança:** os administradores com **Acesso completo** têm permissões completas no Cloud App Security. Eles podem adicionar administradores, adicionar políticas e configurações, fazer upload de logs e executar ações de governança.

- **Administrador de conformidade:** Tem permissões somente leitura e pode gerenciar alertas. Não é possível acessar as recomendações de segurança para plataformas de nuvem. Pode criar e modificar políticas de arquivo, permitir ações de governança de arquivo e exibir todos os relatórios internos em Gerenciamento de dados.

- **Administrador de dados de conformidade:** Tem permissões somente leitura, pode criar e modificar políticas de arquivo, permitir ações de governança de arquivo e exibir todos os relatórios de descoberta. Não é possível acessar as recomendações de segurança para plataformas de nuvem.

- **Operador de segurança:** Tem permissões somente leitura e pode gerenciar alertas.

- **Leitor de segurança:** Tem permissões somente leitura e pode gerenciar alertas. O Leitor de segurança não tem permissão para executar as seguintes ações:

  - Criar políticas e editar as existentes
  - Executar ações de controle
  - Carregar logs de descoberta
  - Proibir ou aprovar aplicativos de terceiros
  - Acessar e exibir a página de configurações de intervalo de endereço IP
  - Acessando e exibindo as páginas de configurações do sistema
  - Acessar e exibir as configurações de Descoberta
  - Acessar e exibir a página de Conectores de aplicativo
  - Acessar e exibir o Log de controle
  - Acessar e exibir a página Gerenciar relatórios de instantâneo
  - Acessando e editando o agente SIEM

- **Leitor global:** Tem acesso completo somente leitura a todos os aspectos de Cloud App Security. Não é possível alterar nenhuma configuração ou executar ações.

> [!NOTE]
> As funções do Office 365 e do Azure AD não estão listadas na página **gerenciar acesso de administrador** .

## <a name="built-in-cloud-app-security-admin-roles"></a>Funções internas de administrador de Cloud App Security

As seguintes Cloud App Security funções de administrador específicas podem ser configuradas no portal de Cloud App Security:

- **Administrador de aplicativo/instância:** Tem permissões completas ou somente leitura para todos os dados em Cloud App Security que lidam exclusivamente com o aplicativo ou instância específica de um aplicativo selecionado. Por exemplo, você concede uma permissão de administrador de usuários à sua instância europeia do Box. O administrador verá apenas os dados relacionados à instância europeia do Box, sejam arquivos, atividades, políticas ou alertas:

  - Página de atividades – somente atividades sobre o aplicativo específico
  - Alertas – somente alertas relacionados ao aplicativo específico
  - Políticas – pode exibir todas as políticas e se as permissões completas atribuídas podem editar ou criar somente políticas que lidam exclusivamente com o aplicativo/instância
  - Página de contas – somente contas para a instância/o aplicativo específico
  - Permissões de aplicativo – somente permissões para a instância/o aplicativo específico
  - Página de arquivos – somente arquivos de instância/aplicativo específico
  - Controle de Aplicativo de Acesso Condicional: sem permissões
  - Atividade do descoberta Cloud Discovery: sem permissões
  - Extensões de segurança-permissões somente para o token de API com permissões de usuário
  - Ações de governança – somente para a instância/o aplicativo específico
  - Recomendações de segurança para plataformas de nuvem-sem permissões

- **Administrador do grupo de usuários:** Tem permissões completas ou somente leitura para todos os dados em Cloud App Security que lidam exclusivamente com os grupos específicos atribuídos a eles. Por exemplo, se você atribuir permissões de administrador de usuário ao grupo "Alemanha-todos os usuários", o administrador poderá exibir e editar informações em Cloud App Security somente para esse grupo de usuários. O administrador do grupo de usuários tem o seguinte acesso:

  - Página de atividades – somente atividades relacionadas aos usuários do grupo
  - Alertas – somente alertas relacionados aos usuários do grupo
  - Políticas – pode exibir todas as políticas e se as permissões completas atribuídas podem editar ou criar somente as políticas que lidam exclusivamente com os usuários no grupo
  - Página de contas – somente contas dos usuários específicos do grupo
  - Permissões de aplicativo: nenhuma permissão
  - Página de arquivos: nenhuma permissão
  - Controle de Aplicativo de Acesso Condicional: sem permissões
  - Atividade do descoberta Cloud Discovery: sem permissões
  - Extensões de segurança-permissões somente para o token de API com usuários no grupo
  - Ações de governança – somente para os usuários específicos do grupo
  - Recomendações de segurança para plataformas de nuvem-sem permissões

    > [!NOTE]
    >
    > - Para atribuir grupos a administradores de grupo de usuários, você deve primeiro [importar grupos de usuários](user-groups.md) de aplicativos conectados.
    > - Você só pode atribuir permissões de administradores de grupo de usuários a grupos do Azure AD importados.

- **Cloud Discovery administrador global:** Tem permissão para exibir e editar todos os Cloud Discovery configurações e dados. O administrador de descoberta global tem o seguinte acesso:

  - Configurações
    - Configurações do sistema – somente exibição
    - Configurações do Cloud Discovery – exibir e editar tudo (permissões de anonimização dependem se ele recebeu autorização durante a atribuição de função)
  - Atividade do Cloud Discovery – todas as permissões
  - Alertas – somente alertas relacionados a dados do Cloud Discovery
  - Políticas – pode exibir todas as políticas e editar ou criar somente as políticas do Cloud Discovery
  - Página de atividades – nenhuma permissão
  - Página de contas – nenhuma permissão
  - Permissões de aplicativo: nenhuma permissão
  - Página de arquivos: nenhuma permissão
  - Controle de Aplicativo de Acesso Condicional: sem permissões
  - Extensões de segurança-criando e excluindo seus próprios tokens de API
  - Ações de governança – apenas ações relacionadas ao Cloud Discovery
  - Recomendações de segurança para plataformas de nuvem-sem permissões

- **Administrador do relatório de Cloud Discovery:** Tem permissões para exibir todos os dados em Cloud App Security que lidam exclusivamente com os relatórios de Cloud Discovery específicos selecionados. Por exemplo, você pode conceder a alguém permissão de administrador para o relatório contínuo do Microsoft defender ATP. O administrador de descoberta verá apenas os dados Cloud Discovery relacionados a essa fonte de dados e ao catálogo de aplicativos. Esse administrador não terá acesso às páginas **atividades**, **arquivos** ou recomendações de **segurança** e acesso limitado às políticas.

> [!NOTE]
> As funções internas de administrador Cloud App Security fornecem permissões de acesso para Cloud App Security.

## <a name="override-admin-permissions"></a>Substituir permissões de administrador

Se você quiser substituir a permissão do administrador no Azure Active Directory ou no Office 365, faça isso manualmente adicionando o usuário ao Cloud App Security e atribuindo permissões de usuário. Por exemplo, caso deseje atribuir a Sara, um Leitor de segurança no Azure Active Directory, o **Acesso completo** no Cloud App Security, adicione-a manualmente ao Cloud App Security e atribua a ela o **Acesso completo** para substituir sua função e conceder a ela as permissões necessárias no Cloud App Security.

## <a name="add-additional-admins"></a>Adicionar administradores adicionais

Adicione também outros administradores ao Cloud App Security sem adicionar usuários a funções administrativas do Azure Active Directory. Para adicionar outros administradores, realize as seguintes etapas:

> [!IMPORTANT]
> Somente Administradores globais ou Administradores de segurança podem conceder acesso a outros usuários ao Cloud App Security.

1. Clique no ícone configurações ![configurações](media/settings-icon.png "Ícone de configurações") de engrenagem e **gerenciar acesso de administrador**.

2. Clique no sinal de adição para adicionar os administradores que devem ter acesso ao Cloud App Security. Você pode digitar um endereço de email interno ou externo para permitir que administradores internos da organização ou MSSPs (Provedores de Serviço de Segurança Gerenciada) externos administrem seus alertas de segurança.

    ![adicionar administradores](media/add-admin.png)

3. Em seguida, clique na lista suspensa para definir o tipo de função que o administrador tem **, administrador global**, **leitor de segurança**, administrador de **conformidade**, **administrador de aplicativo/instância**, **administrador de grupo de usuários**, **administrador global de Cloud Discovery** ou **Cloud Discovery administrador de relatório**. Se você selecionar **administrador de aplicativo/instância**, selecione o aplicativo e a instância para o qual o administrador tem permissões.

    >[!NOTE]
    > Qualquer administrador, cujo acesso é limitado, que tentar acessar uma página restrita ou executar uma ação restrita receberá um erro indicando que ele não tem permissão para acessar a página ou executar a ação.

4. Clique em **Adicionar administrador**.

## <a name="admin-activity-auditing"></a>Auditoria de atividade do administrador

Cloud App Security permite exportar um log de atividades de entrada de administrador e uma auditoria de exibições de um usuário específico ou alertas executados como parte de uma investigação.

Para exportar um log, execute as seguintes etapas:

1. Na página **gerenciar acesso de administradores** , selecione **Exportar atividades de administrador**.

1. Especifique o intervalo de tempo necessário.

1. Clique em **Exportar**.

## <a name="invite-external-admins"></a>Convidar administradores externos

Cloud App Security permite que você convide provedores de serviço de segurança gerenciados externos (MSSPs) como administradores do seu portal de Cloud App Security. Os usuários externos agora podem ser configurados como administradores e atribuídos a qualquer uma das funções disponíveis no Cloud App Security. Para adicionar usuários externos, verifique se Cloud App Security está habilitado no locatário de origem e, em seguida, forneça um endereço de email externo nas etapas em [adicionar administradores adicionais](#add-additional-admins).

Além disso, para permitir que os MSSPs forneçam serviços em vários locatários de cliente, os Administradores que têm direitos de acesso a mais de um locatário agora podem alternar locatários com facilidade no portal. Para alternar locatários, depois de receber permissões para vários locatários, clique no ícone de usuário. Você verá uma lista dos locatários para os quais você tem permissões. Selecione o locatário que deseja gerenciar.

![escolher locatário](media/choose-tenant.png "escolher locatário")

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Configurar Cloud Discovery](set-up-cloud-discovery.md)

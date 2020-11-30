---
title: Definir escopo da implantação do Microsoft Cloud App Security
description: Este artigo fornece informações sobre como definir o escopo de sua implantação do Cloud App Security, incluir e excluir usuários ou grupos específicos.
ms.date: 8/25/2019
ms.topic: how-to
ms.openlocfilehash: 94aec27172d83c2884ea91c944ecd80898ae0381
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96315558"
---
# <a name="scoped-deployment"></a>Implantação com escopo <a name="scoped-deployment"></a> 

[!INCLUDE [Banner for top of topics](includes/banner.md)]

O Microsoft Cloud App Security permite definir o escopo da implantação. Escopo permite que você selecione alguns grupos de usuários a serem monitorados para aplicativos ou excluídos do monitoramento.

## <a name="include-or-exclude-user-groups"></a>Incluir ou excluir grupos de usuários

Não convém usar o Microsoft Cloud App Security para todos os usuários em sua organização. O escopo é especialmente útil quando você deseja limitar a implantação devido a restrições de licença. Talvez você também precise limitar devido a regulamentos de conformidade que exigem que você não monitore os usuários de determinados países/regiões. Por exemplo, use a implantação no escopo para monitorar somente os funcionários baseado nos EUA. Como alternativa, você pode evitar mostrar todas as atividades para os usuários baseados na Alemanha.

- Para definir o escopo de sua implantação, primeiro [importe grupos de usuários](user-groups.md) no Microsoft Cloud App Security. Por padrão, você verá os seguintes grupos:

  - Grupo de usuários de **aplicativo** – um grupo integrado que lhe permite ver as atividades executadas pelos aplicativos do Office 365 e do Azure AD.

  - Grupo de **usuários externos** – todos os usuários que não são membros de qualquer um dos domínios gerenciados que você configurou para sua organização.

- A definição de uma regra de inclusão excluirá automaticamente todos os grupos que não estejam dentro do grupo incluído. Por exemplo, se você definir uma regra para incluir todos os membros dos grupos de escritórios dos EUA, os grupos que não forem desse grupo não serão monitorados.

- Grupos de usuários excluídos substituem os grupos de usuários incluídos. Isso significa que se você incluir o grupo de usuários "Funcionários do Reino Unido", mas excluir "Marketing", os membros de marketing do Reino Unido não serão monitorados, mesmo se forem membros do grupo **Funcionários do Reino Unido**.

1. Na barra de menus, clique na engrenagem de configurações e selecione **Implantação com escopo**.

    ![Ícone de configurações](media/settings-icon.png "Ícone de configurações")

2. Para definir o escopo de sua implantação a fim de incluir ou excluir grupos específicos, primeiro [importe grupos de usuários](user-groups.md) no Microsoft Cloud App Security.

3. Para definir grupos específicos para monitoramento do Microsoft Cloud App Security, na guia **Incluir**, clique no ícone de sinal de adição.
    ![icon](media/plus-icon.png)

4. Na caixa de diálogo **Criar nova regra de inclusão**, realize as seguintes etapas:

    1. Em **Digitar nome da regra**, dê um nome descritivo para a regra.
    2. Em **Selecionar grupos de usuários**, selecione todos os grupos que você quer monitorar com o Cloud App Security.
    3. Selecione se você quer aplicar esta regra a todos os aplicativos conectados ou apenas a **aplicativos específicos**. Se você selecionar **aplicativos específicos**, a regra afetará apenas o monitoramento dos aplicativos que você selecionar. Por exemplo, se você selecionar **Usuários da equipe da interface do usuário** e **Caixa**, o Cloud App Security monitorará apenas a atividade Caixa para usuários no grupo de usuários da equipe da interface do usuário e para todos os outros aplicativos, o Cloud App Security monitorará todas as atividades de todos os usuários.

        ![regra de inclusão](media/include-rule.png)

5. Para definir grupos específicos a serem excluídos do monitoramento, na guia **excluir** , clique no ícone de adição.

   ![ícone](media/plus-icon.png)

6. Na caixa de diálogo **Criar nova regra de Exclusão**, defina os seguintes parâmetros:

    1. Em **Digitar nome da regra**, dê um nome descritivo para a regra.
    Em **Selecionar grupos de usuários**, selecione todos os grupos que você não quer que o Cloud App Security monitore.
    2. Selecione se você quer aplicar esta regra a todos os aplicativos conectados ou apenas a **aplicativos específicos**. Se você selecionar **Aplicativos específicos**, o Cloud App Security deixará de monitorar o grupo selecionado apenas para os aplicativos selecionados. Isso significa que, se você selecionar os **usuários** e **Active Directory** da equipe de interface de usuário do grupo, Cloud app Security monitorará toda a atividade do usuário, exceto as atividades de Active Directory que são executadas por usuários da equipe da interface do usuário.

       ![regra de exclusão](media/exclude-rule.png)

## <a name="example-results-for-include-and-exclude-rules"></a>Resultados de exemplo para incluir e excluir regras

As regras de inclusão e exclusão criadas por você funcionam juntas para definir o escopo do monitoramento geral executado pelo Microsoft Cloud App Security do escopo. Aqui está um exemplo de regras de inclusão e exclusão que você pode criar, e o resultado final do que o Microsoft Cloud App Security monitora após a execução dessas regras.

Se você criar as seguintes regras:

- Excluir o grupo de usuários "Alemanha todos os usuários"
- Incluir no grupo de usuários "Vendas globais"somente as atividades do Office 365
- Incluir no grupo de usuário "Gerentes de vendas" somente atividades do Power BI
- O Salesforce está conectado ao Microsoft Cloud App Security e não há regras definidas para ele

As seguintes atividades de usuário são monitoradas:

|Usuário|Associação de grupo|Atividades monitoradas|
|----|----|----|
|Manuela|Alemanha todos os usuários<br />Vendas globais<br />Gerentes de vendas|Nenhum|
|Davi|Vendas globais|Office 365 e todos os subaplicativos, exceto o Power BI|
|Barros|Vendas globais<br />Gerentes de vendas|Office 365 e todos os subaplicativos|
|Diogo|Gerentes de vendas|Apenas Power BI|

> [!NOTE]
> Outros aplicativos não serão afetados pelo escopo do grupo nestas regras.
> No exemplo, para o Salesforce, todas as atividades são monitoradas em todos os grupos de usuários.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Configurar Cloud Discovery](set-up-cloud-discovery.md)

[!INCLUDE [Open support ticket](includes/support.md)]  

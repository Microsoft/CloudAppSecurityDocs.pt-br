---
title: Definir escopo de sua implantação do Microsoft Cloud App Security | Microsoft Docs
description: Este artigo fornece informações sobre como definir o escopo de sua implantação do Cloud App Security, incluir e excluir usuários ou grupos específicos.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/30/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: fe2ce27b-1020-45e9-ad72-fad93d197169
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: d7148854286218172fdbeb7c9e651a49cb721980
ms.sourcegitcommit: af8fad9709171b200699ca1ed513e2831826ed7e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34568655"
---
*Aplica-se ao: Microsoft Cloud App Security*


# Implantação com escopo <a name="scoped-deployment"></a> 

O Microsoft Cloud App Security permite que você defina o escopo de sua implantação para que apenas determinados grupos de usuários sejam monitorados, ou para que grupos de usuários específicos sejam excluídos do monitoramento.

Não convém usar o Microsoft Cloud App Security para todos os usuários em sua organização. Ele é especialmente útil quando você quer limitar sua implantação devido a restrições de licença, ou devido a normas de conformidade que podem exigir o não monitoramento de usuários de alguns países. Com a implantação com escopo, você pode, por exemplo, monitorar apenas os funcionários com base nos EUA ou, como alternativa, evitar mostrar as atividades para os usuários alemães. 

- Para definir o escopo de sua implantação, primeiro [importe grupos de usuários](user-groups.md) no Microsoft Cloud App Security. Por padrão, você verá o grupo de usuários **Aplicativo**, que é um grupo interno que permite a você ver atividades executadas pelo Office 365 e por aplicativos do Azure AD, e o grupo **Usuários externos**, que consolida todos os usuários que não estão dentro dos [intervalos de endereços IP](ip-tags.md) definidos para a sua organização.
- A definição de uma regra de inclusão excluirá automaticamente todos os grupos que não estejam dentro do grupo incluído. Por exemplo, se você definir uma regra para incluir todos os membros dos grupos de escritórios dos EUA, qualquer grupo que não fizer parte desse grupo não será monitorado.
- Grupos de usuários excluídos substituem os grupos de usuários incluídos. Isso significa que se você incluir o grupo de usuários "Funcionários do Reino Unido", mas excluir "Marketing", os membros de marketing do Reino Unido não serão monitorados, mesmo se forem membros do grupo **Funcionários do Reino Unido**.

1. Na barra de menus, clique na engrenagem de configurações ![ícone de configurações](./media/settings-icon.png "ícone de configurações") e selecione **Implantação com escopo**.  

2. Para definir o escopo de sua implantação a fim de incluir ou excluir grupos específicos, primeiro [importe grupos de usuários](user-groups.md) no Microsoft Cloud App Security. 

3. Para definir grupos específicos para monitoramento do Microsoft Cloud App Security, na guia **Incluir**, clique no ![ícone de sinal de adição](./media/plus-icon.png). <br>Na caixa de diálogo **Criar nova regra de inclusão**, faça o seguinte:

    1. Em **Digitar nome da regra**, dê um nome descritivo para a regra.
    2. Em **Selecionar grupos de usuários**, selecione todos os grupos que você quer monitorar com o Cloud App Security.
    3. Selecione se você quer aplicar esta regra a todos os aplicativos conectados ou apenas a **aplicativos específicos**. Se você selecionar **aplicativos específicos**, a regra afetará apenas o monitoramento dos aplicativos que você selecionar. Isso significa que, se você selecionar o grupo **Usuários do Reino Unido** e **Caixa**, o Cloud App Security monitorará apenas a atividade Caixa dos usuários no Reino Unido e, para todos os outros aplicativos, o Cloud App Security monitorará todas as atividades de todos os usuários.
     
     ![regra de inclusão](./media/include-rule.png)

4. Para definir a exclusão de grupos específicos do monitoramento, na guia **Excluir**, clique no ![ícone](./media/plus-icon.png) do sinal de adição. <br>Na caixa de diálogo **Criar nova regra de inclusão**, defina os parâmetros a seguir:

    1. Em **Digitar nome da regra**, dê um nome descritivo para a regra.
    Em **Selecionar grupos de usuários**, selecione todos os grupos que você quer excluir do monitoramento do Cloud App Security.
    2. Selecione se você quer aplicar esta regra a todos os aplicativos conectados ou apenas a **aplicativos específicos**. Se você selecionar **Aplicativos específicos**, o Cloud App Security deixará de monitorar o grupo selecionado apenas para os aplicativos selecionados. Isso significa que, se você selecionar o grupo **Usuários da Alemanha** e o **Active Directory**, o Cloud App Security monitorará todas as atividades de usuário, exceto atividades do Active Directory realizadas pelos usuários na Alemanha.
    
    ![regra de exclusão](./media/exclude-rule.png)

As regras de inclusão e exclusão criadas por você funcionam juntas para definir o escopo do monitoramento geral executado pelo Microsoft Cloud App Security do escopo.

Aqui está um exemplo de regras de inclusão e exclusão que você pode criar, e o resultado final do que o Microsoft Cloud App Security monitora após a execução dessas regras.

Se você criar as seguintes regras:

- Excluir o grupo de usuários "Alemanha todos os usuários"
- Incluir no grupo de usuários "Vendas globais"somente as atividades do Office 365
- Incluir no grupo de usuário "Gerentes de vendas" somente atividades do Power BI
- O Salesforce está conectado ao Microsoft Cloud App Security e não há regras definidas para ele

As seguintes atividades de usuário são monitoradas:

|User|Associação de grupo|Atividades monitoradas|
|----|----|----|
|Manuela|Alemanha todos os usuários<br>Vendas globais<br>Gerentes de vendas|Não|
|Davi|Vendas globais|Office 365 e todos os subaplicativos, exceto o Power BI|
|Barros|Vendas globais<br>Gerentes de vendas|Office 365 e todos os subaplicativos|
|Diogo|Gerentes de vendas|Apenas Power BI|

> [!NOTE] 
> Outros aplicativos não serão afetados pelo escopo do grupo nestas regras.
> No exemplo, para o Salesforce, todas as atividades são monitoradas em todos os grupos de usuários.

  
    
## <a name="see-also"></a>Consulte Também  
[Configurar o Cloud Discovery](set-up-cloud-discovery.md)   

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
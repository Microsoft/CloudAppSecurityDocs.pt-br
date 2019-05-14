---
title: Definir escopo da implantação do Microsoft Cloud App Security
description: Este artigo fornece informações sobre como definir o escopo de sua implantação do Cloud App Security, incluir e excluir usuários ou grupos específicos.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: rkarlin
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: fe2ce27b-1020-45e9-ad72-fad93d197169
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: c1bd96bd60cd1170b9283ff19e35369193872c36
ms.sourcegitcommit: 9f0c562322394a3dfac7f1d84286e673276a28b1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65568884"
---
# Implantação com escopo <a name="scoped-deployment"></a> 

*Aplica-se a: Microsoft Cloud App Security*

O Microsoft Cloud App Security permite definir o escopo da implantação. Escopo permite que você selecione alguns grupos de usuários a serem monitorados para aplicativos ou excluídos do monitoramento.

## <a name="include-or-exclude-user-groups"></a>Incluir ou excluir grupos de usuários

Não convém usar o Microsoft Cloud App Security para todos os usuários em sua organização. O escopo é especialmente útil quando você deseja limitar a implantação devido a restrições de licença. Talvez você também precise limitar devido a regulamentos de conformidade que exigem que você não monitore usuário de certos países. Por exemplo, use a implantação no escopo para monitorar somente os funcionários baseado nos EUA. Como alternativa, você pode evitar mostrar todas as atividades para os usuários baseados na Alemanha.

- Para definir o escopo de sua implantação, primeiro [importe grupos de usuários](user-groups.md) no Microsoft Cloud App Security. Por padrão, você verá os seguintes grupos:
    - Grupo de usuários de **aplicativo** – um grupo integrado que lhe permite ver as atividades executadas pelos aplicativos do Office 365 e do Azure AD.
    - Grupo de **usuários externos** – todos os usuários que não estão dentro dos [Intervalos de endereços IP](ip-tags.md) definidos para a sua organização.
- A definição de uma regra de inclusão excluirá automaticamente todos os grupos que não estejam dentro do grupo incluído. Por exemplo, se você definir uma regra para incluir todos os membros dos grupos de escritórios dos EUA, os grupos que não forem desse grupo não serão monitorados.
- Grupos de usuários excluídos substituem os grupos de usuários incluídos. Isso significa que se você incluir o grupo de usuários "Funcionários do Reino Unido", mas excluir "Marketing", os membros de marketing do Reino Unido não serão monitorados, mesmo se forem membros do grupo **Funcionários do Reino Unido**.

1. Na barra de menus, clique na engrenagem de configurações e selecione **Implantação com escopo**.  

    ![ícone de configurações](./media/settings-icon.png "settings icon")

2. Para definir o escopo de sua implantação a fim de incluir ou excluir grupos específicos, primeiro [importe grupos de usuários](user-groups.md) no Microsoft Cloud App Security. 

3. Para definir grupos específicos para monitoramento do Microsoft Cloud App Security, na guia **Incluir**, clique no ícone de sinal de adição. 
    ![ícone](./media/plus-icon.png)

4. Na caixa de diálogo **Criar nova regra de inclusão**, realize as seguintes etapas:

    1. Em **Digitar nome da regra**, dê um nome descritivo para a regra.
    2. Em **Selecionar grupos de usuários**, selecione todos os grupos que você quer monitorar com o Cloud App Security.
    3. Selecione se você quer aplicar esta regra a todos os aplicativos conectados ou apenas a **aplicativos específicos**. Se você selecionar **aplicativos específicos**, a regra afetará apenas o monitoramento dos aplicativos que você selecionar. Por exemplo, se você selecionar **Usuários da equipe da interface do usuário** e **Caixa**, o Cloud App Security monitorará apenas a atividade Caixa para usuários no grupo de usuários da equipe da interface do usuário e para todos os outros aplicativos, o Cloud App Security monitorará todas as atividades de todos os usuários.
     
        ![regra de inclusão](./media/include-rule.png)

5. Para definir a exclusão de grupos específicos do monitoramento, na guia **Excluir**, clique no ícone do sinal de adição. 
    
   ![ícone](./media/plus-icon.png)

6. Na caixa de diálogo **Criar nova regra de Exclusão**, defina os seguintes parâmetros:

    1. Em **Digitar nome da regra**, dê um nome descritivo para a regra.
    Em **Selecionar grupos de usuários**, selecione todos os grupos que você não quer que o Cloud App Security monitore.
    2. Selecione se você quer aplicar esta regra a todos os aplicativos conectados ou apenas a **aplicativos específicos**. Se você selecionar **Aplicativos específicos**, o Cloud App Security deixará de monitorar o grupo selecionado apenas para os aplicativos selecionados. Isso significa que, se você selecionar o grupo **Usuários da equipe da interface do usuário** e o **Active Directory**, o Cloud App Security monitorará todas as atividades do usuário, exceto atividades do Active Directory realizadas por usuário equipe da equipe de interface do usuário.
    
       ![regra de exclusão](./media/exclude-rule.png)

## <a name="example-results-for-include-and-exclude-rules"></a>Resultados de exemplo para incluir e excluir regras

As regras de inclusão e exclusão criadas por você funcionam juntas para definir o escopo do monitoramento geral executado pelo Microsoft Cloud App Security do escopo. Aqui está um exemplo de regras de inclusão e exclusão que você pode criar, e o resultado final do que o Microsoft Cloud App Security monitora após a execução dessas regras.

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

## <a name="next-steps"></a>Próximas etapas  
[Configurar o Cloud Discovery](set-up-cloud-discovery.md)   

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  

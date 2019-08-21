---
title: Automatizar os alertas para proteger os pontos de extremidade | Microsoft Docs
description: Este tutorial descreve o processo para configurar alertas do Microsoft Cloud App Security a fim de usar o Microsoft Flow para executar ações do Microsoft Defender.
author: ShlomoSagir-MS
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: tutorial
ms.date: 8/15/2019
ms.openlocfilehash: bfec590f92172773bf263dbb5b84832329c63488
ms.sourcegitcommit: 12dfc4c0b8d72aad8cfae9c70f0014ca312b9e4e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69037420"
---
# <a name="tutorial-automate-alerts-to-protect-endpoints"></a>Tutorial: Automatizar alertas para proteger os pontos de extremidade

Por conta própria, o Cloud App Security fornece opções predefinidas de governança, como suspender o usuário ou tornar o arquivo privado durante a definição de políticas. Ao criar um guia estratégico no Microsoft Flow usando o conector do Cloud App Security, você pode criar fluxos de trabalho para habilitar ações personalizadas no ponto de extremidade para suas políticas usando a ATP (Proteção Avançada contra Ameaças) do Microsoft Defender. Depois que o guia estratégico é criado no Flow, basta associá-lo a uma política no Cloud App Security para enviar alertas ao Flow. O Microsoft Flow oferece vários conectores e condições para criar um fluxo de trabalho personalizado para sua organização.

O [conector do Cloud App Security](https://docs.microsoft.com/connectors/cloudappsecurity/) no Flow é compatível com gatilhos e ações automatizados. O Flow é disparado automaticamente quando o Cloud App Security gera um alerta. As ações incluem a alteração do status de alerta no Cloud App Security.

Neste tutorial, você aprenderá a automatizar alertas para:

> [!div class="checklist"]
> * Executar um exame antivírus usando o Microsoft Defender ATP
> * Isolar um computador usando o Microsoft Defender ATP

Para os fins deste tutorial, o procedimento descreve como automatizar alertas para executar um exame antivírus usando o Microsoft Defender ATP. Para automatizar alertas a fim de isolar um computador, use as mesmas etapas trocando o fluxo de antivírus pelo fluxo de isolamento.

> [!NOTE]
> Esses fluxos são relevantes apenas para políticas que contêm atividades de usuário. Por exemplo, você não pode usar esses fluxos com políticas de descoberta ou de OAuth.

Se você não tiver um plano do Flow, [inscreva-se para uma conta de avaliação gratuita](https://flow.microsoft.com/pricing).

## <a name="prerequisites"></a>Pré-requisitos

* Você precisa ter um [plano válido do Microsoft Flow](https://flow.microsoft.com/pricing)
* O ambiente do Flow deve ser sincronizado com o Azure AD, monitorado pelo Defender ATP e ingressado no domínio

## <a name="run-an-antivirus-scan-using-microsoft-defender-atp"></a>Executar um exame antivírus usando o Microsoft Defender ATP

As etapas a seguir orientam você para a criação de um fluxo que executa um exame antivírus e para a adição desse fluxo em uma política que detecta comportamentos suspeitos. Quando um alerta de comportamento suspeito é gerado para um usuário, ele dispara o fluxo que executa um exame antivírus no computador usado pelo usuário suspeito de estar comprometido.

### <a name="step-1-create-a-flow-to-run-an-antivirus-scan"></a>Etapa 1: Criar um fluxo para executar um exame antivírus

> [!NOTE]
> Se você tiver criado anteriormente um fluxo usando um conector do Defender ATP, o Flow reutilizará automaticamente o conector e você poderá ignorar a etapa **Entrar**.

1. Vá para o [portal do Microsoft Flow](https://flow.microsoft.com/) e selecione Modelos.
    ![Captura de tela da página principal do Flow, mostrando a seleção de modelos.](media/tutorial-flow-templates.png)
1. Pesquise "Cloud App Security" e selecione **Executar exame antivírus usando o Windows Defender em um alerta do Cloud App Security**.
    ![Captura de tela da página de modelos do Flow mostrando os resultados da pesquisa.](media/tutorial-flow-templates-search.png)
1. Clique em **Entrar** e insira as credenciais de administrador que deseja usar com o conector do Microsoft Defender ATP.
    ![Captura de tela da página de modelos do Flow mostrando o processo de entrada.](media/tutorial-flow-templates-signin.png)

> [!TIP]
> Mantenha esta página aberta, você precisará dela mais tarde.

### <a name="step-2-create-a-cloud-app-security-connector"></a>Etapa 2: Criar um conector do Cloud App Security

> [!NOTE]
> Se você tiver criado anteriormente um fluxo usando um conector do Cloud App Security, o Flow reutilizará automaticamente o token e você poderá ignorar esta etapa.

1. Na barra de menus do Cloud App Security, clique na engrenagem de configurações ![ícone de configurações](./media/settings-icon.png "settings icon") e selecione **Extensões de segurança**.
1. Na página de **Extensões de segurança**, clique no botão de adição para gerar um novo token de API.
1. Na janela pop-up **Gerar novo token**, insira o nome do token (por exemplo, "Flow-Token") e, em seguida, clique em **Gerar**.
    ![Captura de tela da janela de token mostrando a entrada de nome e o botão gerar.](media/tutorial-flow-token-generate.png)
1. Depois que o token for gerado, clique no ícone de cópia à direita do token gerado e, em seguida, clique em **Fechar**. Você precisará do token mais tarde.
    ![Captura de tela da janela do token mostrando o token e o processo de cópia.](media/tutorial-flow-token-copy.png)

### <a name="step-3-configure-the-flow"></a>Etapa 3: Configurar o fluxo

> [!NOTE]
> Se você tiver criado anteriormente um fluxo usando um conector do Azure AD, o Flow reutilizará automaticamente o token e você poderá ignorar esta etapa.

1. De volta ao portal do Microsoft Flow, clique em **Criar**.
    ![Captura de tela da página de modelos do Flow mostrando o processo de criação.](media/tutorial-flow-templates-create.png)
1. Na janela pop-up do **Cloud App Security**, insira o nome da conexão (por exemplo, "Token do Cloud App Security"), cole o token de API copiado e, em seguida, clique em **Criar**.
    ![Captura de tela da janela do Cloud App Security mostrando as entradas do nome e da chave e o botão criar.](media/tutorial-flow-token-generate.png)
1. Na lista de aplicativos, na linha em que aparece **HTTP com o Azure AD**, selecione os três pontos ao final da linha e, em seguida, clique em **Adicionar nova conexão**.
1. Na janela pop-up **HTTP com o Azure AD**, para ambos os campos **URL de recurso de base** e **URI de recurso do Azure AD**, insira `https://graph.microsoft.com` e, em seguida, clique em **Entrar** e insira as credenciais de administrador que deseja usar com o conector HTTP com o Azure AD.
    ![Captura de tela da janela HTTP com o Azure AD mostrando os campos de recurso e o botão Entrar.](media/tutorial-flow-templates-azure.png)
1. Clique em **Continue**.
    ![Captura de tela da janela de modelos do Flow mostrando as ações concluídas e o botão continuar.](media/tutorial-flow-templates-continue.png)
1. Depois que todos os conectores tiverem sido conectados com sucesso, na página do fluxo, em **Aplicar a cada computador**, opcionalmente modifique o comentário e o tipo de exame e, em seguida, clique em **Salvar**.
    ![Captura de tela da página de fluxo mostrando a seção de configuração do exame.](media/tutorial-flow-templates-scan.png)

### <a name="step-4-apply-the-flow-to-a-policy"></a>Etapa 4: Aplicar o fluxo a uma política

1. No Cloud App Security, edite a política em que deseja adicionar o fluxo de antivírus e, em **alertas**, selecione **Enviar alertas para o Flow** e, em seguida, selecione **Executar exame antivírus usando o Windows Defender em um alerta do Cloud App Security**.
    ![Captura de tela da página de política mostrando a seção de configurações de alertas.](media/tutorial-flow-templates-alerts.png)

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
[Integrar ao Flow para automação de alertas personalizada](flow-integration.md)

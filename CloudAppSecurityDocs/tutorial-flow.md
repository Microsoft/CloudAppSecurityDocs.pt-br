---
title: Estender a governança para correção de ponto de extremidade | Microsoft Docs
description: Este tutorial descreve o processo para configurar alertas de política do Microsoft Cloud App Security a fim de disparar os fluxos de trabalho do Microsoft Power Automate para executar ações de correção da Proteção Avançada contra Ameaças do Microsoft Defender.
author: shsagir
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: tutorial
ms.date: 04/27/2020
ms.openlocfilehash: 689b40482c4064add4edc4a05d2dbcd768ccf53c
ms.sourcegitcommit: 4e2b905c8770d411df68372c29154d30b2cf195e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/21/2020
ms.locfileid: "85123301"
---
# <a name="tutorial-extend-governance-to-endpoint-remediation"></a>Tutorial: Estender a governança para correção de ponto de extremidade

O Cloud App Security fornece opções de governança predefinidas para políticas, como suspender um usuário ou tornar um arquivo privado. Usando a integração nativa com o Microsoft Power Automate, é possível usar um grande ecossistema de conectores SaaS (software como serviço) para criar fluxos de trabalho para automatizar processos, incluindo correção.

Por exemplo, ao detectar uma possível ameaça de malware, é possível usar fluxos de trabalho para iniciar as ações de correção da ATP (Proteção Avançada contra Ameaças) do Microsoft defender, como a execução de uma verificação antivírus ou o isolamento de um ponto de extremidade.

Neste tutorial, você aprenderá a configurar uma ação de governança de política para usar um fluxo de trabalho para executar uma verificação antivírus em um ponto de extremidade em que um usuário mostra sinais de comportamento suspeito.

> [!div class="checklist"]
>
> * 1: [Gerar um token de API do Cloud App Security](#generate-token)
> * 2: [Criar um fluxo para executar um exame antivírus](#create-flow)
> * 3: [Configurar o fluxo](#configure-flow)
> * 4: [Configurar uma política para executar o fluxo](#configure-policy)

> [!NOTE]
> Esses fluxos de trabalho são relevantes apenas para políticas que contêm atividades de usuário. Por exemplo, não é possível usar esses fluxos de trabalho com políticas de descoberta ou de OAuth.

Se você não tiver um plano do Power Automate, [inscreva-se para uma conta de avaliação gratuita](https://flow.microsoft.com/pricing).

## <a name="prerequisites"></a>Pré-requisitos

* Você precisa ter um plano válido do [Microsoft Power Automate](https://flow.microsoft.com/pricing)
* Você precisa ter um plano válido do Microsoft Defender ATP
* O ambiente do Power Automate precisa ser sincronizado com o Azure AD, monitorado pelo Defender ATP e ingressado no domínio

## <a name="phase-1-generate-a-cloud-app-security-api-token"></a>Fase 1: Gerar um token de API do Cloud App Security<a name="generate-token"></a>

> [!NOTE]
> Se você tiver criado anteriormente um fluxo de trabalho usando um conector do Cloud App Security, o Power Automate reutilizará automaticamente o token e você poderá ignorar esta etapa.

1. Na barra de menus do Cloud App Security, clique na engrenagem de configurações ![ícone de configurações](media/settings-icon.png "Ícone de configurações") e selecione **Extensões de segurança**.

1. Na página **Extensões de segurança**, clique no botão de adição para gerar um novo token de API.
1. Na janela pop-up **Gerar novo token**, insira o nome do token (por exemplo, "Flow-Token") e, em seguida, clique em **Gerar**.

    ![Captura de tela da janela de token mostrando a entrada de nome e o botão Gerar.](media/tutorial-flow-token-generate.png)
1. Depois que o token for gerado, clique no ícone de cópia à direita do token gerado e, em seguida, clique em **Fechar**. Você precisará do token mais tarde.

    ![Captura de tela da janela do token mostrando o token e o processo de cópia.](media/tutorial-flow-token-copy.png)

## <a name="phase-2-create-a-flow-to-run-an-antivirus-scan"></a>Fase 2: Criar um fluxo para executar um exame antivírus<a name="create-flow"></a>

> [!NOTE]
> Se você tiver criado anteriormente um fluxo usando um conector do Defender ATP, o Power Automate reutilizará automaticamente o conector e você poderá ignorar a etapa **Entrar**.

1. Vá para o [portal do Power Automate](https://flow.microsoft.com/) e selecione **Modelos**.

    ![Captura de tela da página principal do Power Automate mostrando a seleção de modelos.](media/tutorial-flow-templates.png)

1. Pesquise "Cloud App Security" e selecione **Executar exame antivírus usando o Windows Defender em um alerta do Cloud App Security**.

    ![Captura de tela da página de modelos do Power Automate mostrando os resultados da pesquisa.](media/tutorial-flow-templates-search.png)

1. Na lista de aplicativos, na linha na qual o **conector do Microsoft Defender ATP** aparece, clique em **Entrar**.

    ![Captura de tela da página de modelos do Power Automate mostrando o processo de conexão.](media/tutorial-flow-templates-signin.png)

## <a name="phase-3-configure-the-flow"></a>Fase 3: Configurar o fluxo<a name="configure-flow"></a>

> [!NOTE]
> Se você tiver criado anteriormente um fluxo usando um conector do Azure AD, o Power Automate reutilizará automaticamente o token e você poderá ignorar esta etapa.

1. Na lista de aplicativos, na linha na qual o **Cloud App Security** aparece, clique em **Criar**.

    ![Captura de tela da página de modelos do Power Automate mostrando o botão Criar do Cloud App Security.](media/tutorial-flow-templates-create.png)

1. Na janela pop-up do **Cloud App Security**, insira o nome da conexão (por exemplo, "Token do Cloud App Security"), cole o token de API copiado e, em seguida, clique em **Criar**.

    ![Captura de tela da janela do Cloud App Security mostrando as entradas do nome e da chave e o botão Criar.](media/tutorial-flow-templates-create-window.png)

1. Na lista de aplicativos, na linha na qual **HTTP com o Azure AD** aparece, clique em **Entrar**.

1. Na janela pop-up **HTTP com o Azure AD**, para ambos os campos **URL de recurso de base** e **URI de recurso do Azure AD**, insira `https://graph.microsoft.com` e, em seguida, clique em **Entrar** e insira as credenciais de administrador que deseja usar com o conector HTTP com o Azure AD.

    ![Captura de tela da janela HTTP com o Azure AD mostrando os campos de recursos e o botão Entrar.](media/tutorial-flow-templates-azure.png)

1. Clique em **Continue**.

    ![Captura de tela da janela de modelos do Power Automate mostrando as ações concluídas e o botão Continuar.](media/tutorial-flow-templates-continue.png)

1. Depois que todos os conectores tiverem sido conectados com sucesso, na página do fluxo, em **Aplicar a cada computador**, opcionalmente modifique o comentário e o tipo de exame e, em seguida, clique em **Salvar**.

    ![Captura de tela da página de fluxo mostrando a seção de configuração do exame.](media/tutorial-flow-templates-scan.png)

## <a name="phase-4-configure-a-policy-to-run-the-flow"></a>Fase 4: Configurar uma política para executar o fluxo<a name="configure-policy"></a>

1. No Cloud App Security, clique em **Controle** e em **Políticas**.

1. Na lista de políticas, na linha em que a política relevante é exibida, escolha os três pontos no final da linha e escolha **Editar política**.

1. Em **Alertas**, selecione **Enviar alertas para o Flow** e, em seguida, selecione **Executar verificação antivírus usando o Windows Defender em um alerta do Cloud App Security**.

    ![Captura de tela da página de política mostrando a seção de configurações de alertas.](media/tutorial-flow-templates-alerts.png)

Agora, cada alerta gerado para essa política iniciará o fluxo para executar a verificação antivírus.

É possível usar as etapas neste tutorial para criar uma ampla gama de ações baseadas em fluxo de trabalho para estender os recursos de correção do Cloud App Security, incluindo outras ações do Defender ATP. Para ver uma lista de fluxos de trabalho predefinidos do Cloud App Security, no Power Automate, [pesquise "Cloud App Security"](https://go.microsoft.com/fwlink/?linkid=2102574).

## <a name="see-also"></a>Consulte Também

> [!div class="nextstepaction"]
> [Integrar-se ao Power Automate para automação de alertas personalizada](flow-integration.md)

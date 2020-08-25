---
title: Integre a automatização de energia da Microsoft com o Microsoft Cloud App Security para obter automação de alerta personalizada
description: Este artigo fornece informações sobre como obter a automação de alertas personalizada integrando a automatização de energia da Microsoft com o Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 04/27/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 991d71778e08aa7c5200a5f719d5df6867653367
ms.sourcegitcommit: 29a8e66c665f51d831516924ae4d9d8047b39276
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88781490"
---
# <a name="integrate-with-microsoft-power-automate-for-custom-alert-automation"></a>Integre-se ao Microsoft Power Automate para automação de alerta personalizada

*Aplica-se a: Microsoft Cloud App Security*

O Cloud App Security integra-se com a [automatização de energia da Microsoft](https://docs.microsoft.com/flow/getting-started) para fornecer automação de alerta personalizada e guias estratégicos de orquestração. Usando o [ecossistema de conectores](https://docs.microsoft.com/connectors/) disponíveis na automatização de energia, você pode automatizar o disparo de guias estratégicos quando Cloud app Security gera alertas. Por exemplo, crie automaticamente um problema nos sistemas de tíquete usando o [conector do ServiceNow](https://docs.microsoft.com/connectors/service-now/) ou envie um email de aprovação para executar uma ação de governança personalizada quando um alerta é disparado no Cloud App Security.

## <a name="prerequisites"></a>Pré-requisitos

- Você precisa ter um plano válido do [Microsoft Power Automate](https://flow.microsoft.com/pricing)

## <a name="how-it-works"></a>Como ele funciona

Por conta própria, Cloud App Security fornece opções de governança predefinidas, como suspender um usuário ou tornar um arquivo privado ao definir políticas. Ao criar um guia estratégico na automação de energia usando o conector de Cloud App Security, você pode criar fluxos de trabalho para habilitar opções de governança personalizadas para suas políticas. Depois que o guia estratégico é criado na automatização de energia, basta associá-lo a uma política no Cloud App Security para enviar alertas para a automatização de energia. A automatização de energia da Microsoft oferece vários conectores e condições para criar um fluxo de trabalho personalizado para sua organização.

O [conector de Cloud app Security](https://docs.microsoft.com/connectors/cloudappsecurity/) no Power Automate dá suporte a gatilhos e ações automatizadas. A automatização de energia é disparada automaticamente quando Cloud App Security gera um alerta. As ações incluem a alteração do status de alerta no Cloud App Security.

## <a name="how-to-create-playbooks-with-power-automate"></a>Como criar guias estratégicos com o Power Automate

1. [Criar um token de API](api-tokens.md) no Cloud App Security.

2. Navegue até o [portal de automatização de energia](https://flow.microsoft.com), selecione **meus fluxos**, selecione **novo**e, na lista suspensa, selecione **automatizado de em branco**.

    ![Automatizar a criação de novo fluxo](media/flow-create-new.png)

3. Forneça um nome para o fluxo e, em **escolha o gatilho do fluxo**, digite **Cloud app Security** e selecione **quando um alerta é gerado**.

    ![Automatizar a energia quando um alerta é gerado](media/flow-when-alert.png)

4. Em **Configurações de autenticação**, cole o token de API da etapa 1.

5. Defina o fluxo de trabalho que deverá ser disparado quando uma política no Cloud App Security gerar um alerta. Você pode adicionar uma ação, uma condição lógica, condições de mudança entre maiúsculas e minúsculas ou loops e salvar o guia estratégico.

    ![Fluxo de trabalho de automação de energia](media/flow-workflow.png)

6. No portal de Cloud App Security, vá para **políticas** e, na linha da política cujos alertas você deseja encaminhar para a automatização de energia, clique nos três pontos e selecione **configurações**.
7. Em **alertas**, selecione **enviar alertas para poder automatizar** e escolha o nome do guia estratégico no menu suspenso.

    ![Habilitar a automatização de energia no portal Cloud App Security](media/flow-mcas-config.png)

8. Cloud App Security guias estratégicos que você criou ou com acesso concedido podem ser vistos na tela extensões de **segurança** .

    ![exibir guias estratégicos no Cloud App Security](media/flow-extensions.png)

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]

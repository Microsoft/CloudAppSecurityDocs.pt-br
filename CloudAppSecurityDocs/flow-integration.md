---
title: Integrar o Flow ao Cloud App Security para obter automação de alerta personalizada
description: Este artigo fornece informações de como obter a automação de alerta personalizada integrando o Flow ao Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 6/18/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 76115cb85be2f20f6d57f2e016d1a7d4548d05d1
ms.sourcegitcommit: 6eff466c7a6817b14a60d8c3b2c201c7ae4c2e2c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74719995"
---
# <a name="integrate-with-flow-for-custom-alert-automation"></a>Integrar com o Flow para automação de alerta personalizada

*Aplica-se ao: Microsoft Cloud App Security*

O Cloud App Security integra-se ao [Microsoft Flow](https://docs.microsoft.com/flow/getting-started) para fornecer guias estratégicos de automação e orquestração de alerta personalizadas. Usando o [ecossistema de conectores](https://docs.microsoft.com/connectors/) disponível no Microsoft Flow, você pode automatizar o disparo de guias estratégicos quando o Cloud App Security gera alertas. Por exemplo, crie automaticamente um problema nos sistemas de tíquete usando o [conector do ServiceNow](https://docs.microsoft.com/connectors/service-now/) ou envie um email de aprovação para executar uma ação de governança personalizada quando um alerta é disparado no Cloud App Security.

## <a name="prerequisites"></a>Pré-requisitos

- Você precisa ter um [plano válido do Microsoft Flow](https://flow.microsoft.com/pricing)

## <a name="how-it-works"></a>Como funciona

Por conta própria, o Cloud App Security fornece opções predefinidas de governança, como suspender o usuário ou tornar o arquivo privado durante a definição de políticas. Ao criar um guia estratégico no Microsoft Flow usando o conector do Cloud App Security, você pode criar fluxos de trabalho para habilitar as opções de governança personalizadas para suas políticas. Depois que o guia estratégico é criado no Flow, basta associá-lo a uma política no Cloud App Security para enviar alertas ao Flow. O Microsoft Flow oferece vários conectores e condições para criar um fluxo de trabalho personalizado para sua organização.

O [conector do Cloud App Security](https://docs.microsoft.com/connectors/cloudappsecurity/) no Flow é compatível com gatilhos e ações automatizados. O Flow é disparado automaticamente quando o Cloud App Security gera um alerta. As ações incluem a alteração do status de alerta no Cloud App Security.

## <a name="how-to-create-playbooks-with-microsoft-flow"></a>Como criar guias estratégicos com o Microsoft Flow

1. [Criar um token de API](api-tokens.md) no Cloud App Security.

2. Navegue até o [portal do Microsoft Flow](https://flow.microsoft.com) e escolha [**Criar um novo fluxo do zero**](https://docs.microsoft.com/flow/get-started-logic-flow).

3. Em gatilhos e conectores de pesquisa, digite **Cloud App Security** e selecione **Quando um alerta é gerado**.

    ![Flow – Quando um alerta é gerado](media/flow-when-alert.png)

4. Em **Configurações de autenticação**, cole o token de API da etapa 1.

5. Defina o fluxo de trabalho que deverá ser disparado quando uma política no Cloud App Security gerar um alerta. Você pode adicionar uma ação, uma condição lógica, condições de mudança entre maiúsculas e minúsculas ou loops e salvar o guia estratégico.

    ![Fluxo de trabalho do Flow](media/flow-workflow.png)

6. No portal do Cloud App Security, acesse **Políticas** e na linha da política cujos alertas você deseja encaminhar ao Flow, clique nos três pontos e selecione **Configurações**.
7. Em **Alertas**, selecione **Enviar alertas ao Flow** e escolha o nome do guia estratégico no menu suspenso.

    ![Habilitar o Flow no portal do Cloud App Security](media/flow-mcas-config.png)

8. Os guias estratégicos do Cloud App Security que você criou ou para os quais recebeu acesso podem ser vistos na tela **Extensões de segurança**.

    ![exibir guias estratégicos no Cloud App Security](media/flow-extensions.png)

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]

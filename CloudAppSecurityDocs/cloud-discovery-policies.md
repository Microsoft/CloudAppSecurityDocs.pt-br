---
title: Criar políticas em aplicativos Cloud Discovery-Cloud App Security | Microsoft Docs
description: Este artigo fornece informações sobre como trabalhar com políticas de Cloud Discovery.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: d3b5b62664abc9e82ad726e60c5105ef29ae0b16
ms.sourcegitcommit: 4f3883a9e85d0aaf2802b10433b221c3f1838d88
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79285480"
---
# <a name="cloud-discovery-policies"></a>Políticas do Cloud Discovery

*Aplica-se a: Microsoft Cloud App Security*

Você pode criar políticas de descoberta de aplicativo para alertá-lo quando novos aplicativos forem detectados. Cloud App Security também pesquisa todos os logs em seu Cloud Discovery para obter anomalias.

## <a name="creating-an-app-discovery-policy"></a>Criando uma política de descoberta de aplicativo

As políticas de descoberta permitem que você defina alertas que o notificam quando novos aplicativos são detectados em sua organização.

1. No console do, clique em **controle** seguido por **políticas**.

2. Clique em **criar política** e selecione **política de descoberta de aplicativo**.

    ![menu de política do App Discovery](media/app-discovery-policy-menu.png "menu de política do App Discovery")

3. Dê um nome e uma descrição à sua política. Se desejar, você pode baseá-lo em um modelo. Para obter mais informações sobre modelos de política, consulte [controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md).

4. Defina a **severidade** da política.

5. Para definir quais aplicativos descobertos disparam essa política, adicione filtros.

6. Você pode definir um limite para o quão confidencial a política deve ser. Habilitar **disparar uma correspondência de política se todos os itens a seguir ocorrerem no mesmo dia**. Você pode definir critérios que o aplicativo deve exceder diariamente para corresponder à política. Selecione um dos seguintes critérios:
    - Tráfego diário
    - Dados baixados
    - Número de endereços IP
    - Número de transações
    - Quantidade de usuários
    - Dados carregados

7. Defina um **limite de alerta diário** em **alertas**. Selecione se o alerta é enviado como um email, uma mensagem de texto ou ambos. Em seguida, forneça números de telefone e endereços de email conforme necessário.
    - Clicar em **salvar configurações de alerta como o padrão para sua organização** permite que as políticas futuras usem a configuração.
    - Se você tiver uma configuração padrão, poderá selecionar **usar as configurações padrão da sua organização**.

8. Selecione ações de **governança** a serem aplicadas quando um aplicativo corresponder a essa política. Ele pode marcar políticas como **aprovados**, não **aprovados**ou como uma marca personalizada.

9. Clique em **Criar**.

Por exemplo, se você estiver interessado em descobrir aplicativos de hospedagem arriscados encontrados em seu ambiente de nuvem, defina sua política da seguinte maneira:

Defina os filtros de política para descobrir quaisquer serviços encontrados na categoria **serviços de hospedagem** e que tenham uma pontuação de risco de 1, indicando que eles são altamente arriscados.

 Defina os limites que devem disparar um alerta para um determinado aplicativo descoberto na parte inferior. Por exemplo, alertar apenas se mais de 100 usuários no ambiente usavam o aplicativo e se eles baixaram uma determinada quantidade de dados do serviço.
Além disso, você pode definir o limite de alertas diários que deseja receber.

![exemplo de política de descoberta de aplicativo](media/app-discovery-policy-example.png "exemplo de política de descoberta de aplicativo")

## <a name="cloud-discovery-anomaly-detection"></a>Detecção de anomalias Cloud Discovery

Cloud App Security pesquisa todos os logs em seu Cloud Discovery para obter anomalias. Por exemplo, quando um usuário, que nunca usou o Dropbox antes, carrega de repente 600 GB para ele ou quando há muito mais transações do que o normal em um aplicativo específico. A política de detecção de anomalias é habilitada por padrão. Não é necessário configurar uma nova política para que ela funcione. No entanto, você pode ajustar quais tipos de anomalias você deseja que sejam alertados na política padrão.

1. No console do, clique em **controle** seguido por **políticas**.

2. Clique em **criar política** e selecione **Cloud Discovery política de detecção de anomalias**.

    ![menu da política de detecção de anomalias da descoberta de nuvem](media/cloud-discovery-anomaly-detection-policy-menu.png "menu da política de detecção de anomalias da descoberta de nuvem")

3. Dê um nome e uma descrição à sua política. Se desejar, você pode baseá-lo em um modelo, para obter mais informações sobre modelos de política, consulte [controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md).

4. Para definir quais aplicativos descobertos disparam essa política, clique em **adicionar filtros**.

    Os filtros são escolhidos nas listas suspensas. Para adicionar filtros, clique no botão de adição. Para remover um filtro, clique no ' X '.

5. Em **aplicar para** escolher se essa política aplicará **todos os relatórios contínuos** ou **relatórios contínuos específicos**. Selecione se a política se aplica a **usuários**, **endereços IP**ou ambos.

6. Selecione as datas em que a atividade anômala ocorreu para disparar o alerta em **gerar alertas somente para atividades suspeitas que ocorrem após a data.**

7. Defina um **limite de alerta diário** em **alertas**. Selecione se o alerta é enviado como um email, uma mensagem de texto ou ambos. Em seguida, forneça números de telefone e endereços de email conforme necessário.
    - Clicar em **salvar configurações de alerta como o padrão para sua organização** permite que as políticas futuras usem a configuração.
    - Se você tiver uma configuração padrão, poderá selecionar **usar as configurações padrão da sua organização**.

8. Clique em **Criar**.

![nova política de anomalias de descoberta](media/new-discovery-anomaly-policy.png "nova política de anomalias de descoberta")

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Políticas de atividade do usuário](user-activity-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]

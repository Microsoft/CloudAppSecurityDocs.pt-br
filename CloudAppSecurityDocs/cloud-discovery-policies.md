---
title: Criar políticas em aplicativos do Cloud Discovery – Cloud App Security | Microsoft Docs
description: Este artigo fornece informações sobre como trabalhar com políticas do Cloud Discovery.
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
ms.sourcegitcommit: 6eff466c7a6817b14a60d8c3b2c201c7ae4c2e2c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74720110"
---
# <a name="cloud-discovery-policies"></a>Políticas de Cloud Discovery

*Aplica-se ao: Microsoft Cloud App Security*

Você pode criar políticas de descoberta de aplicativo para alertá-lo quando novos aplicativos são detectados. O Cloud App Security também pesquisa anomalias em todos os logs do Cloud Discovery.

## <a name="creating-an-app-discovery-policy"></a>Criando uma política de descoberta de aplicativos

As políticas de descoberta permitem que você defina alertas que notificam quando novos aplicativos são detectados na sua organização.

1. No console, clique em **Controlar** seguido por **Políticas**.

2. Clique em **Criar política** e selecione a política **Descoberta de aplicativos**.

    ![menu de política do App Discovery](media/app-discovery-policy-menu.png "menu de política de descoberta de aplicativo")

3. Forneça um nome e uma descrição à sua política. Caso deseje, você poderá baseá-los em um modelo. Para obter mais informações sobre modelos de política, confira [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md).

4. Defina a **Gravidade** da política.

5. Para definir quais aplicativos descobertos disparam essa política, adicione filtros.

6. Você pode definir um limite para o nível de sensibilidade que a política deve ter. Habilite **Disparar uma correspondência de política se todas as situações a seguir ocorrerem no mesmo dia**. Você pode definir os critérios que o aplicativo precisa exceder diariamente para corresponder à política. Selecione um dos seguintes critérios:
    - Tráfego diário
    - Dados baixados
    - Número de endereços IP
    - Número de transações
    - Número de usuários
    - Dados carregados

7. Defina um **Limite de alerta diário** em **Alertas**. Selecione se o alerta será enviado como um email e/ou como uma mensagem de texto. Em seguida, forneça números de telefone e endereços de email, conforme o necessário.
    - Clicar em **Salvar configurações de alerta como o padrão da organização** permite que políticas futuras usem a configuração.
    - Se houver uma configuração padrão, você poderá selecionar **Usar as configurações padrão da organização**.

8. Selecione ações de **Governança** a serem aplicadas quando um aplicativo corresponder a essa política. Elas podem marcar as políticas como **Sancionadas**, **Não Sancionadas** ou com uma marca personalizada.

9. Clique em **Criar**.

Por exemplo, se você estiver interessado em descobrir aplicativos de hospedagem arriscados encontrados em seu ambiente de nuvem, defina sua política da seguinte maneira:

Defina os filtros de política para descobrir todos os serviços encontrados na categoria **serviços de hospedagem** que têm uma pontuação de risco igual a 1, indicando que eles são altamente arriscados.

 Defina os limites que devem disparar um alerta para um determinado aplicativo descoberto na parte inferior. Por exemplo, alertar apenas se mais de 100 usuários no ambiente usaram o aplicativo e se eles baixaram uma determinada quantidade de dados do serviço.
Além disso, você pode definir o limite de alertas diários que deseja receber.

![exemplo de política de descoberta de aplicativo](media/app-discovery-policy-example.png "exemplo de política de descoberta de aplicativo")

## <a name="cloud-discovery-anomaly-detection"></a>Detecção de anomalias do Cloud Discovery

O Cloud App Security pesquisa todos os logs em seu Cloud Discovery quanto a anomalias. Por exemplo, quando um usuário, que nunca usou o Dropbox antes, de repente carrega 600 GB nele ou quando há muito mais transações que o normal em um aplicativo específico. A política de detecção de anomalias é habilitada por padrão. Não é necessário configurar uma nova política para que ela funcione. No entanto, você pode ajustar sobre quais tipos de anomalias deseja ser alertado na política padrão.

1. No console, clique em **Controlar** seguido por **Políticas**.

2. Clique em **Criar política** e selecione **Política de detecção de anomalias de Cloud Discovery**.

    ![menu da política de detecção de anomalias da descoberta de nuvem](media/cloud-discovery-anomaly-detection-policy-menu.png "menu de política de detecção de anomalias do Cloud Discovery")

3. Forneça um nome e uma descrição à sua política. Caso deseje, você poderá baseá-los em um modelo, para obter mais informações sobre modelos de política, confira [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md).

4. Para definir quais aplicativos descobertos disparam essa política, clique em **Adicionar filtros**.

    Os filtros são escolhidos em listas suspensas. Para adicionar filtros, clique no botão de adição. Para remover um filtro, clique em 'X'.

5. Em **Aplicar a** escolha se essa política aplica a **Todos os relatórios contínuos** ou **Relatórios contínuos específicos**. Se a política se aplica a **Usuários** e/ou a **Endereços IP**.

6. Selecione as datas durante as quais a atividade anômala ocorreu para disparar o alerta em **Gerar alertas apenas para atividades suspeitas que ocorrerem após a data.**

7. Defina um **Limite de alerta diário** em **Alertas**. Selecione se o alerta será enviado como um email e/ou como uma mensagem de texto. Em seguida, forneça números de telefone e endereços de email, conforme o necessário.
    - Clicar em **Salvar configurações de alerta como o padrão da organização** permite que políticas futuras usem a configuração.
    - Se houver uma configuração padrão, você poderá selecionar **Usar as configurações padrão da organização**.

8. Clique em **Criar**.

![nova política de anomalias de descoberta](media/new-discovery-anomaly-policy.png "nova política de descoberta de anomalias")

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Políticas de atividade de usuário](user-activity-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]

---
title: Criar política de detecção de anomalias do Cloud Discovery no Cloud App Security
description: Estes tópico fornece informações sobre como trabalhar com as políticas de detecção de anomalias do Cloud Discovery.
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
ms.openlocfilehash: c8fc0a705a88d65922368356721d4c9b61b98cb6
ms.sourcegitcommit: 7c93b6f93d2699d466b172590710ed01697bbdad
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74719799"
---
# <a name="cloud-discovery-anomaly-detection-policy"></a>Política de detecção de anomalias do Cloud Discovery

*Aplica-se ao: Microsoft Cloud App Security*

Este artigo fornece detalhes de referência sobre as políticas. São listadas explicações sobre cada tipo de política e os campos que podem ser configurados para cada política.

## <a name="cloud-discovery-anomaly-detection-policy-reference"></a>Referência de política de detecção de anomalias do Cloud Discovery

Uma política de detecção de anomalias do Cloud Discovery permite instalar e configurar o monitoramento contínuo de aumentos incomuns no uso do aplicativo de nuvem. Aumentos de dados baixados, dados carregados, transações e usuários são considerados para cada aplicativo na nuvem. Cada aumento é comparado com o padrão de uso normal do aplicativo conforme aprendido com base no uso anterior. Os aumentos mais extremos disparam alertas de segurança.

Para cada política, é possível definir filtros que permitem monitorar seletivamente o uso do aplicativo. Os filtros incluem um filtro de aplicativo, exibições de dados selecionadas e uma data de início selecionada. Você também pode definir a sensibilidade, a qual permite definir quantos alertas a política deve disparar.

Para cada política, defina os seguintes parâmetros:

1. Decida se deseja basear a política em um modelo. Um modelo de política relevante é o modelo **Comportamento anormal de usuários descobertos**. Ele alerta quando comportamentos anormais são detectados em usuários e aplicativos descobertos, como grandes quantidades de dados carregados em comparação com outros usuários e transações grandes de usuário em comparação com o histórico do usuário. Selecione também o modelo **Comportamento anormal de endereços IP descobertos**. Esse modelo alerta quando comportamentos anormais são detectados em endereços IP e aplicativos descobertos, como grandes quantidades de dados carregados em comparação com outros endereços IP e transações grandes de aplicativo em comparação com o histórico do endereço IP.

2. Forneça o **Nome da política** e **Descrição**.

3. Crie um filtro para os aplicativos que você deseja monitorar clicando em **Adicionar filtro**.
   Você pode selecionar um aplicativo específico, uma **Categoria** de aplicativo ou filtrar por **Nome**, **Domínio e **Fator de risco** e clicar em **Salvar**.

4. Em **Aplicar a**, defina como deseja que o uso seja filtrado. O uso sendo monitorado pode ser filtrado de duas maneiras diferentes:

    - **Relatórios contínuos** – selecione se deseja monitorar **Todos os relatórios contínuos** (padrão) ou escolha **Relatórios contínuos específicos** a serem monitorados.

        - Ao selecionar **Todos os relatórios contínuos**, todo aumento no uso será comparado ao padrão de uso normal com base em todas as exibições de dados.
        - Ao selecionar **Relatórios contínuos específicos**, cada aumento no uso é comparado com o padrão de uso normal. O padrão é obtido na mesma exibição de dados na qual o aumento foi observado.

    - **Usuários e endereços IP** – todo uso de aplicativo na nuvem é associado a um usuário, um endereço IP ou ambos.

        - A seleção de **Usuários** ignora a associação do uso do aplicativo a endereços IP.

        - A seleção de **Endereços IP** ignora a associação do uso do aplicativo a usuários.

        - Selecionar **Usuários e endereços IP** (padrão) considera as duas associações, mas poderá produzir alertas duplicados quando houver uma forte correspondência entre usuários e endereços IP.

    - **Disparar alertas apenas para atividades suspeitas que ocorrerem após a data** – qualquer aumento no uso do aplicativo antes da data selecionada é ignorado. No entanto, a atividade anterior à data selecionada é obtida para estabelecer o padrão de uso normal.

5. Em **Alertas**, você pode definir a sensibilidade do alerta. Há várias maneiras de controlar o número de alertas disparados pela política:

    - O controle deslizante **Selecionar a sensibilidade da detecção de anomalias** – dispare alertas para as principais X atividades anômalas por 1.000 usuários por semana. Os alertas são disparados para as atividades com o maior risco.

    - **Limite diário de alertas** – restrinja o número de alertas gerados em um único dia. Você pode selecionar se deseja **Enviar alerta como email**, **Enviar alerta como mensagem de texto ou ambos**. As mensagens enviadas por mensagem de texto são limitadas a dez por dia, para o fuso horário UTC, o que significa que o limite de dez mensagens é reiniciado à meia-noite no fuso horário UTC.

    - Selecione também a opção **Usar as configurações padrão de sua organização**. Essa opção preenche as configurações padrão de **Limite diário de alertas**, email e mensagem de texto de sua organização. Para definir o padrão, preencha as definições de **Configuração de alerta** e clique em **Salvar essas configurações de alerta como o padrão para a sua organização**.

6. Clique em **Criar**.

7. Como em todas as políticas, é possível **Editar**, **Desabilitar** e **Habilitar** a política clicando nos três pontos ao final da linha na página **Políticas**. Por padrão, quando você cria uma política, ela é habilitada.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]

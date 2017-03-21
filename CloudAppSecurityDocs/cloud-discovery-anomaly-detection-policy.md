---
title: "Criar uma política de descoberta de anomalias do Cloud Discovery no Cloud App Security | Microsoft Docs"
description: "Estes tópico fornece informações sobre como trabalhar com as políticas de detecção de anomalias do Cloud Discovery."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/23/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: eaf73af0-7610-4903-b656-8d90b1d2b18c
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 5c5d77a83d3eba40250ece02cfce4aa8f80d345d
ms.sourcegitcommit: 355226ee21981563066d637e7db0bff0d53c2da6
translationtype: HT
---
# <a name="cloud-discovery-anomaly-detection-policy"></a>Política de detecção de anomalias do Cloud Discovery
Este artigo fornece detalhes de referência sobre as políticas, fornecendo explicações sobre cada tipo de política e os campos que podem ser configurados para cada política.  
  
## <a name="cloud-discovery-anomaly-detection-policy-reference"></a>Referência de política de detecção de anomalias do Cloud Discovery  
Uma política de detecção de anomalias do Cloud Discovery permite instalar e configurar o monitoramento contínuo de aumentos incomuns no uso do aplicativo de nuvem. Para cada aplicativo de nuvem, são considerados aumentos de dados baixados, dados carregados, número de transações e número de usuários. Cada aumento é comparado com o padrão de uso normal do aplicativo conforme aprendido com base no uso anterior. Os aumentos mais extremos disparam alertas de segurança.  
  
Para cada política, é possível definir filtros que permitem monitorar de maneira seletiva o uso do aplicativo, com base em um filtro de aplicativo, nas exibições de dados selecionadas e em uma data de início selecionada. Você também pode definir a sensibilidade, a qual permite definir quantos alertas a política deve disparar.  

Para cada política, defina o seguinte:

1. Decida se deseja basear a política em um modelo. Os modelos de política relevantes são o modelo **Comportamento anômalo em usuários descobertos**, o qual alerta ao detectar comportamentos anômalos em usuários e em aplicativos descobertos, como: grandes quantidades de dados carregados em comparação com outros usuários, transações grandes do usuário em comparação com o histórico do usuário. Você também pode selecionar o modelo **Comportamento anômalo de endereços IP descobertos**, o qual alerta ao detectar comportamentos anômalos em endereços IP e aplicativos descobertos, como: grandes quantidades de dados carregados em comparação com outros endereços IP, transações grandes de aplicativo em comparação com o histórico do endereço IP. 
 
2. Forneça o **Nome da política** e **Descrição**.  

3. Crie um filtro para os aplicativos que você deseja monitorar clicando em **Adicionar filtro**. Você pode selecionar um aplicativo específico, uma **Categoria** de aplicativo ou filtrar por **Nome**, **Domínio** e **Fator de risco** e clicar em **Salvar**.

4. Em **Aplicar a**, defina como deseja que o uso seja filtrado. O uso sendo monitorado pode ser filtrado de duas maneiras diferentes:  
  
    -   Relatórios contínuos – selecione se deseja monitorar **Todos os relatórios contínuos** (padrão) ou escolha monitorar **Relatórios contínuos específicos**.  
  
        -   Ao selecionar **Todos os relatórios contínuos**, todo aumento no uso será comparado ao padrão de uso normal com base em todas as exibições de dados.  
  
        -   Ao selecionar **Relatórios contínuos específicos**, todo aumento no uso será comparado ao padrão de uso normal com base na mesma exibição de dados em que o aumento foi observado.  
  
    -   **Usuários e endereços IP** – todo uso de aplicativo na nuvem é associado ao usuário e/ou ao endereço IP.  
  
        -   Selecionar **Usuários** ignorará a associação do uso do aplicativo com endereços IP, se houver algum.  
  
        -   Selecionar **Endereços IP** ignorará a associação do uso do aplicativo com usuários, se houver algum.  
  
        -   Selecionar **Usuários e endereços IP** (padrão) considerará as duas associações, mas poderá produzir alertas duplicados quando houver uma forte correspondência entre usuários e endereços IP.
    -   Disparar alertas apenas para atividades suspeitas que ocorrerem após a data – será ignorado qualquer aumento no uso do aplicativo antes da data selecionada. No entanto, a atividade de antes da data selecionada será obtida com a finalidade de estabelecer o padrão de uso normal.  
  
5. Em **Alertas**, você pode definir a sensibilidade do alerta. Há várias maneiras de controlar o número de alertas disparados pela política:  
  
    -   O controle deslizante **Selecionar a sensibilidade da detecção de anomalias** – dispare alertas para as principais X atividades anômalas por 1.000 usuários por semana. Os alertas serão disparados para as atividades com o maior risco.  
  
    -   **Limite diário de alertas** – restrinja o número de alertas gerados em um único dia. Você pode selecionar se deseja **Enviar alerta como email**, **Enviar alerta como mensagem de texto ou ambos**. As mensagens enviadas por mensagem de texto serão limitadas a dez por dia, para o fuso horário UTC, o que significa que o limite de dez mensagens é reiniciado à meia-noite no fuso horário UTC.

    - Você também pode selecionar a opção **Usar as configurações padrão da sua organização**, a qual preenche as configurações de **Limite de alerta diário**, de email e de mensagem de texto nas configurações padrão da sua organização. Para definir o padrão, preencha as definições de **Configuração de alerta** e clique em **Salvar essas configurações de alerta como o padrão para a sua organização**.

6. Clique em **Criar**.

7. Como em todas as políticas, é possível **Editar**, **Desabilitar** e **Habilitar** a política clicando nos três pontos ao final da linha na página **Políticas**. Por padrão, ao criar uma política, ela estará habilitada.

## <a name="see-also"></a>Consulte Também  
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
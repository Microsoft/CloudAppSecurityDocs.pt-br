---
title: "Política de detecção de anomalias do Cloud Discovery | Microsoft Docs"
description: "Estes tópico fornece informações sobre como trabalhar com as políticas de detecção de anomalias do Cloud Discovery."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: eaf73af0-7610-4903-b656-8d90b1d2b18c
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 400741713d40422a3b1c7680663a572d18e9c692
ms.openlocfilehash: 132b4d296b26dd187418734b40d08ecb243692da


---

# <a name="cloud-discovery-anomaly-detection-policy"></a>Política de detecção de anomalias do Cloud Discovery
Este artigo fornece detalhes de referência sobre as políticas, fornecendo explicações sobre cada tipo de política e os campos que podem ser configurados para cada política.  
  
## <a name="cloud-discovery-anomaly-detection-policy-reference"></a>Referência de política de detecção de anomalias do Cloud Discovery  
Uma política de detecção de anomalias do Cloud Discovery permite instalar e configurar o monitoramento contínuo de aumentos incomuns no uso do aplicativo de nuvem. Para cada aplicativo de nuvem, são considerados aumentos de dados baixados, dados carregados, número de transações e número de usuários. Cada aumento é comparado com o padrão de uso normal do aplicativo conforme aprendido com base no uso anterior. Os aumentos mais extremos disparam alertas de segurança.  
  
Cada política é composta pelas seguintes partes:  
  
-   Filtros – permitem monitorar seletivamente o uso do aplicativo, com base em um filtro de aplicativo, exibição de dados selecionada e uma data de início selecionada.  
  
-   Sensibilidade – permite definir quantos alertas a política deve disparar.  
  
### <a name="activity-filters"></a>Filtros de atividade  
Para obter uma lista dos filtros de atividade, confira [Atividades](activity-filters.md).  
  
### <a name="apply-to"></a>Aplicar a  
O uso sendo monitorado pode ser filtrado de duas maneiras diferentes:  
  
-   Exibições de dados – Selecione se deseja monitorar todas as exibições de dados (padrão) ou escolha exibições de dados específicas a serem monitoradas.  
  
    -   Ao selecionar **Todas as exibições de dados**, cada aumento do uso é comparado ao padrão de uso normal conforme aprendido com base em todas as exibições de dados.  
  
    -   Ao selecionar exibições de dados específicas, cada aumento do uso é comparado ao padrão de uso normal conforme aprendido com base na mesma exibição de dados em que o aumento foi observado.  
  
-   Usuários e endereços IP – cada uso de aplicativo de nuvem é associado ao usuário, ao endereço IP ou ambos.  
  
    -   Selecionar **Usuários** ignorará a associação do uso do aplicativo com endereços IP, se houver algum.  
  
    -   Selecionar **Endereços IP** ignorará a associação do uso do aplicativo com usuários, se houver algum.  
  
    -   Selecionar **Usuários e endereços IP** considerará as duas associações, mas pode produzir alertas duplicados quando houver uma forte correspondência entre usuários e endereços IP.  
  
Gerar alertas apenas para atividades suspeitas que ocorrerem após a data: qualquer aumento no uso do aplicativo antes da data selecionada será ignorado. No entanto, a atividade de antes da data selecionada será obtida com a finalidade de estabelecer o padrão de uso normal.  
  
### <a name="sensitivity"></a>Sensibilidade  
Há duas maneiras de controlar o número de alertas disparados pela política:  
  
-   Controle deslizante de sensibilidade – escolha quantos alertas disparar por 1.000 usuários por semana. Os alertas serão disparados das atividades com o maior risco.  
  
-   Limite diário de alertas – restringir o número de alertas gerados em um único dia.  
  
## <a name="see-also"></a>Veja também  
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Nov16_HO5-->



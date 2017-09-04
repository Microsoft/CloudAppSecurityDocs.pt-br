---
title: Conectar o Azure ao Cloud App Security para obter visibilidade e controle de uso | Microsoft Docs
description: "Este tópico fornece informações sobre como conectar o Azure ao Cloud App Security usando o conector de API."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 9/3/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 3a677bc7-c8b7-4c6a-aada-82c8b3778352
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 7e2b6d0f02d49eaa4354f5344d0555fc3f503fb8
ms.sourcegitcommit: 5688d3916a54deada225f7a83c34a7c501953960
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2017
---
# <a name="connect-azure-to-microsoft-cloud-app-security"></a>Conectar o Azure ao Microsoft Cloud App Security

Esta seção fornece instruções para conectar o Cloud App Security à sua conta do Azure existente usando a API do conector de aplicativos.  
  
## <a name="setting-up-azure-for-connection-to-cloud-app-security"></a>Configuração do Azure para conexão com o Cloud App Security

O Cloud App Security se conecta ao Azure por meio dos Hubs de Eventos. Esta seção fornece instruções para transmitir todos os seus Logs de Atividades a um único Hub de Eventos em sua assinatura. 

### <a name="step-1-stream-your-azure-activity-logs-to-event-hubs"></a>Etapa 1: transmitir seus logs de atividade do Azure para Hubs de Eventos

1.  Transmita o Log de Atividades do Azure da sua assinatura do Azure a um Hub de Eventos. Siga o guia oficial na documentação do Azure: https://docs.microsoft.com/en-us/azure/monitoring-and-diagnostics/monitoring-stream-activity-logs-event-hubs

 > [!NOTE]
 > Se você tiver mais de uma assinatura do Azure, repita isso para cada assinatura, mas use um único Hub de Eventos que será compartilhado entre suas assinaturas.

 Depois de concluir as instruções, será criado um novo Hub de Eventos no namespace que você escolher.
 
 > [!NOTE]
 > Se você receber um erro depois de tentar exportar os Logs de Atividade, vá para a folha **Provedores de recursos** no Azure e certifique-se de que ‘microsoft.insights’ está registrado.

### <a name="step-2-get-a-connection-string-to-your-event-hub"></a>Etapa 2: obter uma cadeia de conexão para seu Hub de Eventos

1.  Vá para a folha **Hubs de Eventos – Versão Prévia**.
  
   ![Folha Hubs de Eventos](media/azure-event-hubs.png "Hubs de Eventos do Azure")

2.  Selecione o Namespace do seu Hub de Eventos.
  
    ![Namespace do Hub de Eventos](media/azure-namespace.png "Namespace do Azure")

3.  No menu, em **Entidades**, clique em **Hubs de Eventos**. 
  
    ![Entidades de Hubs de Eventos](media/azure-event-hubs-entities.png "Entidades do Hub de Eventos do Azure")

4.  Selecione o novo Hub de Eventos criado pelo Azure Monitor. Ele é chamado de **insights-operational-logs**.
  > [!NOTE]
  > Poderá levar alguns minutos até que o Hub de Eventos seja criado.

   ![Logs operacionais de insights](media/azure-insight-operational-logs.png "Logs operacionais de insights do Azure")
  
  
5. Crie uma nova política de acesso que conceda permissão ao Cloud App Security para ler do Hub de Eventos clicando em **Políticas de acesso compartilhado** e, em seguida, clique em **Adicionar**.
  
    ![Políticas de acesso compartilhado](media/azure-shared-access-policies.png "Política de acesso compartilhado do Azure")

6.  Insira um nome para a nova política e certifique-se de incluir pelo menos a **Declaração de escuta**. Quando terminar, clique em **Criar**.
  
    ![Nova política do Azure](media/azure-new-policy.png "Criar nova política do Azure")

7.  Em **Configurações** e em **Políticas de acesso compartilhado**, clique na política de acesso que você acabou de criar.   
  
    ![Selecionar política do Azure](media/azure-select-policy.png "Selecionar política do Azure")

8. Na janela Política, copie uma das cadeias de conexão clicando no botão ao lado de **Cadeia de conexão – Chave primária** ou **Cadeia de conexão – Chave secundária**.

### <a name="step-3-add-azure-to-cloud-app-security"></a>Etapa 3: adicionar o Azure ao Cloud App Security
 
1.  No portal do Cloud App Security, clique em **Investigar** e em **Aplicativos conectados**.  
  
3.  Na página **Conectores de aplicativos**, clique no botão de sinal de mais e selecione **Microsoft Azure**.  
  
     ![conectar o Azure ao Cloud App Security](media/azure-connect-app.png "conectar o Azure")  
  
4.  No campo **Cadeia de conexão**, cole a cadeia de conexão que você copiou na etapa anterior.  
  
5.  No **Grupo de consumidores**, digite:   `$Default`
    
   >[!NOTE] 
   > Se você criou um grupo de consumidores diferente para ser usado, use o nome **Grupo de consumidores**.
  
6.  Clique em **Conectar**.
     Isso enviará uma mensagem de texto para a conexão e poderá levar alguns minutos. Depois de receber uma notificação de êxito, clique em **Fechar**.  


> [!NOTE]
> Esse recurso está em visualização pública.


## <a name="see-also"></a>Veja também  
[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
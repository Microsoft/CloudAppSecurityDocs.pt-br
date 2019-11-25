---
title: Solução de problemas de integração do SIEM – Cloud App Security | Microsoft Docs
description: Este artigo apresenta uma lista de possíveis problemas ao conectar o SIEM ao Cloud App Security e fornece resoluções para cada um.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 08/30/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: de64d9ca-eaed-4243-bcf7-adca5aff18c8
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: a5ab44813959db6ad7b1f437ba88b47223ce5e41
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2019
ms.locfileid: "74459966"
---
# <a name="troubleshooting-the-siem-agent"></a>Solucionando problemas do agente SIEM

*Aplica-se ao: Microsoft Cloud App Security*

Este artigo apresenta uma lista de possíveis problemas ao conectar o SIEM ao Cloud App Security e fornece as possíveis resoluções.

## <a name="recover-missing-activity-events-in-mcas-siem-agent"></a>Recover missing activity events in MCAS SIEM Agent 

If you received a system alert regarding an issue with activity delivery through the SIEM agent, follow the steps below to recover the activity events in the timeframe of the issue. These steps will guide you through setting up a new Recovery SIEM agent that will run in parallel and resend the activity events to your SIEM.

>[!NOTE]
>The recovery process will resend all activity events in the timeframe described in the system alert. If your SIEM already contains activity events from this timeframe, you will experience duplicated events after this recovery. 

### <a name="step-1--configure-a-new-siem-agent-in-parallel-to-your-existing-agent"></a>Step 1 – Configure a new SIEM Agent in parallel to your existing agent 
1. In the Cloud App Security portal, go to Security Extensions page.  
2. In the SIEM Agents tab, click on [add a new SIEM agent](siem.md), and use the wizard to configure the connection details to your SIEM. 

    >[!NOTE]
    >This agent should run in parallel to the existing one, so network configuration might not be identical. 

1. In the wizard, configure the Data Types to include **only Activities** and apply the same activity filter that was used in your original SIEM agent (if it exists). 
2. Turn on **Recovery mode** by checking the Recovery mode checkbox. This action will automatically configure the SIEM Agent to send only the missing activities due to the issue and stop sending activities once all activities are fully recovered.
3. Salve as configurações.
4. Run the new agent using the generated token.


### <a name="step-2--validate-the-successful-data-delivery-to-your-siem"></a>Step 2 – Validate the successful data delivery to your SIEM 
1. Connect to your SIEM and validate that new data is received from the new SIEM Agent that you configured. 
2. The agent will only send activities from the timeframe of the issue, which you were alerted on. 

### <a name="step-3--remove-the-recovery-siem-agent"></a>Step 3 – Remove the Recovery SIEM agent 
1. The recovery SIEM agent will automatically stop sending data and be disabled once it reaches the end date.
2. Validate in your SIEM that no new data is sent by the recovery SIEM agent. 
3. Stop the execution of the agent on your machine. 
4. In the portal, go to SIEM Agent page, and remove the Recovery SIEM Agent. 
5. Make sure your original SIEM Agent is still running properly. 

## <a name="general-troubleshooting"></a>General troubleshooting

Verifique se o status do agente SIEM no portal do Microsoft Cloud App Security não está como **Erro de conexão** ou **Desconectado** e se não há nenhuma notificação do agente. O status será mostrado como **Erro de conexão** se a conexão estiver inativa por mais de duas horas. O status será alterado para **Desconectado** se a conexão estiver inativa por mais de 12 horas.

Caso veja algum dos seguintes erros no prompt de comando ao executar o agente, use as seguintes etapas para corrigir o problema:

|Erro do|Description|Resolução|
|----|----|----|
|Erro geral durante a inicialização|Erro inesperado durante a inicialização do agente.|Contate o suporte.|
|Muitos erros críticos|Muitos erros críticos durante a conexão ao console. Desligue-o.|Contate o suporte.|
|Token inválido|O token fornecido não é válido.|Verifique se você copiou o token correto. Você pode usar o processo acima para regenerar o token.|
|Endereço de proxy inválido|O endereço de proxy fornecido não é válido.|Verifique se você inseriu o proxy e a porta corretos.|


Depois de criar o agente, verifique a página do agente SIEM no portal do Cloud App Security. Se aparecer uma das seguintes **Notificações do agente**, use as seguintes etapas para corrigir o problema:

|Erro do|Description|Resolução|
|----|----|----|
|**Erro interno**|Algo desconhecido deu errado com o agente SIEM.|Contate o suporte.|
|**Erro de envio do servidor de dados**|Você poderá receber esse erro se estiver trabalhando com um servidor Syslog em TCP. O agente SIEM não pode se conectar ao servidor Syslog.  Se esse erro ocorrer, o agente parará de efetuar pull de novas atividades até que seja corrigido. Siga as etapas de correção até que o erro pare de aparecer.|1. Make sure you properly defined your Syslog server: In the Cloud App Security UI, edit your SIEM agent as described above. Verifique se você escreveu o nome do servidor corretamente e definiu a porta certa. </br>2. Check connectivity to your Syslog server: Make sure your firewall isn't blocking communication.| 
|**Erro de conexão do servidor de dados**| Você poderá receber esse erro se estiver trabalhando com um servidor Syslog em TCP. O agente SIEM não pode se conectar ao servidor Syslog.  Se esse erro ocorrer, o agente parará de efetuar pull de novas atividades até que seja corrigido. Siga as etapas de correção até que o erro pare de aparecer.|1. Make sure you properly defined your Syslog server: In the Cloud App Security UI, edit your SIEM agent as described above. Verifique se você escreveu o nome do servidor corretamente e definiu a porta certa. </br>2. Check connectivity to your Syslog server: Make sure your firewall isn't blocking communication.|
|**Erro do agente SIEM**|O agente SIEM está desconectado há mais de X horas|Verifique se você não alterou a configuração do SIEM no portal do Cloud App Security. Caso contrário, esse erro poderá indicar problemas de conectividade entre o Cloud App Security e o computador no qual você está executando o agente SIEM.|
|**Erro de notificação do agente SIEM**|A notificação do agente SIEM encaminha erros que foram recebidos de um agente SIEM.|Esse erro indica que você recebeu erros sobre a conexão entre o agente SIEM e o servidor SIEM. Verifique se não há um firewall bloqueando o servidor SIEM ou o computador no qual você está executando o agente SIEM. Além disso, verifique se o endereço IP do servidor SIEM não foi alterado.|


## <a name="next-steps"></a>Próximas etapas
  
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   

[!INCLUDE [Open support ticket](includes/support.md)]  
  

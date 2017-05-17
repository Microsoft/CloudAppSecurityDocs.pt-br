---
title: "Solução de problemas de integração do SIEM ao Cloud App Security | Microsoft Docs"
description: "Este tópico fornece uma lista de possíveis problemas ao conectar o SIEM ao Cloud App Security e fornece soluções para cada um."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/9/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: de64d9ca-eaed-4243-bcf7-adca5aff18c8
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: d7b71a3db122db3b7ed6ae28348bb74946b57427
ms.sourcegitcommit: ea8207f412f31127beafd18a0bd028052fbadf90
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/09/2017
---
# <a name="troubleshooting-the-siem-agent"></a>Solucionando problemas do agente SIEM

Verifique se o status do agente SIEM no portal do Cloud App Security não está como **Erro de Conexão** ou **Desconectado** e se não há nenhuma notificação do agente. Ele será exibido como **Erro de Conexão** se a conexão estiver inativa por mais de duas horas e como **Desconectado**, se a conexão estiver inativa por mais de 12 horas.

Caso veja algum dos seguintes erros no prompt de comando ao executar o agente, use as seguintes etapas para corrigir o problema:

|Erro do|Descrição|Resolução|
|----|----|----|
|Erro geral durante a inicialização|Erro inesperado durante a inicialização do agente.|Contate o suporte.|
|Muitos erros críticos|Muitos erros críticos durante a conexão ao console. Desligue-o.|Contate o suporte.|
|Token inválido|O token fornecido não é válido.|Verifique se você copiou o token correto. Você pode usar o processo acima para regenerar o token.|
|Endereço de proxy inválido|O endereço de proxy fornecido não é válido.|Verifique se você inseriu o proxy e a porta corretos.|


Depois de criar o agente, se você vir uma das seguintes **Notificações do agente** no portal do Cloud App Security na página do agente SIEM, use as seguintes etapas para corrigir o problema:

|Erro do|Descrição|Resolução|
|----|----|----|
|**Erro interno**|Algo desconhecido deu errado com o agente SIEM.|Contate o suporte.|
|**Erro de envio do servidor de dados**|Você poderá receber esse erro se estiver trabalhando com um servidor Syslog sobre TCP. O agente SIEM não pode se conectar ao servidor Syslog.  Se você receber esse erro, o agente parará de efetuar pull de novas atividades até a correção do problema, portanto não se esqueça de seguir as etapas de correção até o erro desaparecer.|1. Verifique se você definiu corretamente o servidor Syslog: na interface do usuário do Cloud App Security, edite o agente SIEM conforme descrito acima e verifique se você escreveu o nome do servidor corretamente e definiu a porta correta. </br>2. Verifique a conectividade com o servidor Syslog: verifique se o firewall não está bloqueando a comunicação.| 
|**Erro de conexão do servidor de dados**| Você poderá receber esse erro se estiver trabalhando com um servidor Syslog sobre TCP. O agente SIEM não pode se conectar ao servidor Syslog.  Se você receber esse erro, o agente parará de efetuar pull de novas atividades até a correção do problema, portanto não se esqueça de seguir as etapas de correção até o erro desaparecer.|1. Verifique se você definiu corretamente o servidor Syslog: na interface do usuário do Cloud App Security, edite o agente SIEM conforme descrito acima e verifique se você escreveu o nome do servidor corretamente e definiu a porta correta. </br>2. Verifique a conectividade com o servidor Syslog: verifique se o firewall não está bloqueando a comunicação.|
|**Erro do agente SIEM**|O agente SIEM está desconectado há mais de X horas|Verifique se você não alterou a configuração do SIEM no portal do Cloud App Security. Caso contrário, isso pode indicar problemas de conectividade entre o Cloud App Security e o computador no qual você está executando o agente SIEM.|
|**Erro de notificação do agente SIEM**|A notificação do agente SIEM encaminha erros que foram recebidos de um agente SIEM.|Isso indica que você recebeu erros relacionados à conexão entre o agente SIEM e o servidor SIEM. Verifique se não há um firewall bloqueando o servidor SIEM ou o computador no qual o agente SIEM está sendo executado. Além disso, verifique se o endereço IP do servidor SIEM não foi alterado.|



## <a name="see-also"></a>Veja também  
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
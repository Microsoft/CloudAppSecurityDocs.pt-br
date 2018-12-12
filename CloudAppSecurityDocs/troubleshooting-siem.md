---
title: Solução de problemas de integração do SIEM ao Cloud App Security | Microsoft Docs
description: Este artigo apresenta uma lista de possíveis problemas ao conectar o SIEM ao Cloud App Security e fornece resoluções para cada um.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/9/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: de64d9ca-eaed-4243-bcf7-adca5aff18c8
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 9711115763babc9807d4761f62bde675b435a68d
ms.sourcegitcommit: c497253a7ab63973bb806607e5f15dece91640be
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53124053"
---
# <a name="troubleshooting-the-siem-agent"></a>Solucionando problemas do agente SIEM

*Aplica-se ao: Microsoft Cloud App Security*

Este artigo apresenta uma lista de possíveis problemas ao conectar o SIEM ao Cloud App Security e fornece as possíveis resoluções.

## <a name="troubleshooting"></a>Solução de problemas

Verifique se o status do agente SIEM no portal do Microsoft Cloud App Security não está como **Erro de conexão** ou **Desconectado** e se não há nenhuma notificação do agente. O status será mostrado como **Erro de conexão** se a conexão estiver inativa por mais de duas horas. O status será alterado para **Desconectado** se a conexão estiver inativa por mais de 12 horas.

Caso veja algum dos seguintes erros no prompt de comando ao executar o agente, use as seguintes etapas para corrigir o problema:

|Erro do|Descrição|Resolução|
|----|----|----|
|Erro geral durante a inicialização|Erro inesperado durante a inicialização do agente.|Contate o suporte.|
|Muitos erros críticos|Muitos erros críticos durante a conexão ao console. Desligue-o.|Contate o suporte.|
|Token inválido|O token fornecido não é válido.|Verifique se você copiou o token correto. Você pode usar o processo acima para regenerar o token.|
|Endereço de proxy inválido|O endereço de proxy fornecido não é válido.|Verifique se você inseriu o proxy e a porta corretos.|


Depois de criar o agente, verifique a página do agente SIEM no portal do Cloud App Security. Se aparecer uma das seguintes **Notificações do agente**, use as seguintes etapas para corrigir o problema:

|Erro do|Descrição|Resolução|
|----|----|----|
|**Erro interno**|Algo desconhecido deu errado com o agente SIEM.|Contate o suporte.|
|**Erro de envio do servidor de dados**|Você poderá receber esse erro se estiver trabalhando com um servidor Syslog em TCP. O agente SIEM não pode se conectar ao servidor Syslog.  Se esse erro ocorrer, o agente parará de efetuar pull de novas atividades até que seja corrigido. Siga as etapas de correção até que o erro pare de aparecer.|1. Verifique se você definiu corretamente o servidor Syslog: na interface do usuário do Cloud App Security, edite o agente SIEM conforme descrito acima. Verifique se você escreveu o nome do servidor corretamente e definiu a porta certa. </br>2. Verifique a conectividade com o servidor Syslog: verifique se o firewall não está bloqueando a comunicação.| 
|**Erro de conexão do servidor de dados**| Você poderá receber esse erro se estiver trabalhando com um servidor Syslog em TCP. O agente SIEM não pode se conectar ao servidor Syslog.  Se esse erro ocorrer, o agente parará de efetuar pull de novas atividades até que seja corrigido. Siga as etapas de correção até que o erro pare de aparecer.|1. Verifique se você definiu corretamente o servidor Syslog: na interface do usuário do Cloud App Security, edite o agente SIEM conforme descrito acima. Verifique se você escreveu o nome do servidor corretamente e definiu a porta certa. </br>2. Verifique a conectividade com o servidor Syslog: verifique se o firewall não está bloqueando a comunicação.|
|**Erro do agente SIEM**|O agente SIEM está desconectado há mais de X horas|Verifique se você não alterou a configuração do SIEM no portal do Cloud App Security. Caso contrário, esse erro poderá indicar problemas de conectividade entre o Cloud App Security e o computador no qual você está executando o agente SIEM.|
|**Erro de notificação do agente SIEM**|A notificação do agente SIEM encaminha erros que foram recebidos de um agente SIEM.|Esse erro indica que você recebeu erros sobre a conexão entre o agente SIEM e o servidor SIEM. Verifique se não há um firewall bloqueando o servidor SIEM ou o computador no qual você está executando o agente SIEM. Além disso, verifique se o endereço IP do servidor SIEM não foi alterado.|


## <a name="next-steps"></a>Próximas etapas
  
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/)  
  

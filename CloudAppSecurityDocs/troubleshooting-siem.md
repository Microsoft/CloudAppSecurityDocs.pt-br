---
title: Solução de problemas de integração do SIEM-Cloud App Security
description: Este artigo apresenta uma lista de possíveis problemas ao conectar o SIEM ao Cloud App Security e fornece resoluções para cada um.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 06/29/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: cc27146979efcf090ef4f4596ec1c4a5840892ed
ms.sourcegitcommit: b15034dd50142afd8e95de22a9232f711b1eae6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85624742"
---
# <a name="troubleshooting-the-siem-agent"></a>Solucionando problemas do agente SIEM

*Aplica-se a: Microsoft Cloud App Security*

Este artigo apresenta uma lista de possíveis problemas ao conectar o SIEM ao Cloud App Security e fornece as possíveis resoluções.

## <a name="recover-missing-activity-events-in-mcas-siem-agent"></a>Recuperar eventos de atividade ausentes no agente SIEM MCAS

Se você recebeu um alerta do sistema sobre um problema com a entrega de atividade por meio do agente SIEM, siga as etapas abaixo para recuperar os eventos de atividade no período de tempo do problema. Essas etapas o orientarão na configuração de um novo agente SIEM de recuperação que será executado em paralelo e reenviará os eventos de atividade para o SIEM.

> [!NOTE]
> O processo de recuperação reenviará todos os eventos de atividade no período de tempo descrito no alerta do sistema. Se o SIEM já contiver eventos de atividade desse período, você experimentará eventos duplicados após essa recuperação.

### <a name="step-1--configure-a-new-siem-agent-in-parallel-to-your-existing-agent"></a>Etapa 1 – configurar um novo agente SIEM em paralelo ao agente existente

1. No portal de Cloud App Security, acesse a página de extensões de segurança.
1. Na guia agentes SIEM, clique em [Adicionar um novo agente Siem](siem.md)e use o assistente para configurar os detalhes de conexão para o Siem.

    >[!NOTE]
    >Esse agente deve ser executado em paralelo ao existente, portanto, a configuração de rede pode não ser idêntica.

1. No assistente, configure os tipos de dados para incluir **apenas as atividades** e aplicar o mesmo filtro de atividade que foi usado em seu agente Siem original (se existir).
1. Salve as configurações.
1. Execute o novo agente usando o token gerado.

### <a name="step-2--validate-the-successful-data-delivery-to-your-siem"></a>Etapa 2 – validar a entrega de dados bem-sucedida para o SIEM

1. Conecte-se ao seu SIEM e valide se os novos dados são recebidos do novo agente SIEM que você configurou.
1. O agente enviará apenas atividades do período de tempo do problema, no qual você foi alertado.

### <a name="step-3--remove-the-recovery-siem-agent"></a>Etapa 3 – remover o agente SIEM de recuperação

1. O agente SIEM de recuperação interromperá automaticamente o envio de dados e será desabilitado quando atingir a data de término.
1. Valide em seu SIEM que nenhum dado novo é enviado pelo agente SIEM de recuperação.
1. Pare a execução do agente em seu computador.
1. No portal, acesse a página do agente SIEM e remova o agente SIEM de recuperação.
1. Verifique se o agente SIEM original ainda está sendo executado corretamente.

## <a name="general-troubleshooting"></a>Solução de problemas gerais

Verifique se o status do agente SIEM no portal do Microsoft Cloud App Security não está como **Erro de conexão** ou **Desconectado** e se não há nenhuma notificação do agente. O status será mostrado como **Erro de conexão** se a conexão estiver inativa por mais de duas horas. O status será alterado para **Desconectado** se a conexão estiver inativa por mais de 12 horas.

Caso veja algum dos seguintes erros no prompt de comando ao executar o agente, use as seguintes etapas para corrigir o problema:

|Erro|Descrição|Resolução|
|----|----|----|
|Erro geral durante a inicialização|Erro inesperado durante a inicialização do agente.|Entre em contato com o suporte.|
|Muitos erros críticos|Muitos erros críticos durante a conexão ao console. Desligue-o.|Entre em contato com o suporte.|
|Token inválido|O token fornecido não é válido.|Verifique se você copiou o token correto. Você pode usar o processo acima para regenerar o token.|
|Endereço de proxy inválido|O endereço de proxy fornecido não é válido.|Verifique se você inseriu o proxy e a porta corretos.|

Depois de criar o agente, verifique a página do agente SIEM no portal do Cloud App Security. Se aparecer uma das seguintes **Notificações do agente**, use as seguintes etapas para corrigir o problema:

|Erro|Descrição|Resolução|
|----|----|----|
|**Erro interno**|Algo desconhecido deu errado com o agente SIEM.|Entre em contato com o suporte.|
|**Erro de envio do servidor de dados**|Você poderá receber esse erro se estiver trabalhando com um servidor Syslog em TCP. O agente SIEM não pode se conectar ao servidor Syslog.  Se você receber esse erro, o agente deixará de receber novas atividades até que ele seja corrigido. Siga as etapas de correção até que o erro pare de aparecer.|1. Verifique se você definiu corretamente seu servidor syslog: na interface do usuário do Cloud App Security, edite seu agente SIEM, conforme descrito acima. Verifique se você escreveu o nome do servidor corretamente e definiu a porta certa. </br>2. Verifique a conectividade com o servidor syslog: Verifique se o firewall não está bloqueando a comunicação.|
|**Erro de conexão do servidor de dados**| Você poderá receber esse erro se estiver trabalhando com um servidor Syslog em TCP. O agente SIEM não pode se conectar ao servidor Syslog.  Se você receber esse erro, o agente deixará de receber novas atividades até que ele seja corrigido. Siga as etapas de correção até que o erro pare de aparecer.|1. Verifique se você definiu corretamente seu servidor syslog: na interface do usuário do Cloud App Security, edite seu agente SIEM, conforme descrito acima. Verifique se você escreveu o nome do servidor corretamente e definiu a porta certa. </br>2. Verifique a conectividade com o servidor syslog: Verifique se o firewall não está bloqueando a comunicação.|
|**Erro do agente SIEM**|O agente SIEM está desconectado há mais de X horas|Verifique se você não alterou a configuração do SIEM no portal do Cloud App Security. Caso contrário, esse erro poderá indicar problemas de conectividade entre o Cloud App Security e o computador no qual você está executando o agente SIEM.|
|**Erro de notificação do agente SIEM**|A notificação do agente SIEM encaminha erros que foram recebidos de um agente SIEM.|Esse erro indica que você recebeu erros sobre a conexão entre o agente SIEM e o servidor SIEM. Verifique se não há um firewall bloqueando o servidor SIEM ou o computador no qual você está executando o agente SIEM. Além disso, verifique se o endereço IP do servidor SIEM não foi alterado.|

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]

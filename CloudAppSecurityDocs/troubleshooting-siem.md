---
title: Solução de problemas de integração de SIEM
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
ms.openlocfilehash: ae2f83f04557342122b733600daba11c3fbe7d58
ms.sourcegitcommit: a0a8e25bda77fb21f280a0e504896be85b89ed6f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96034068"
---
# <a name="troubleshooting-the-siem-agent"></a>Solucionando problemas do agente SIEM

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Este artigo apresenta uma lista de possíveis problemas ao conectar o SIEM ao Cloud App Security e fornece as possíveis resoluções.

## <a name="recover-missing-activity-events-in-cloud-app-security-siem-agent"></a>Recuperar eventos de atividade ausentes no agente Cloud App Security SIEM

Antes de prosseguir, verifique se sua [licença de Cloud app Security](https://aka.ms/mcaslicensing) dá suporte à integração Siem que você está tentando configurar.

Se você recebeu um alerta do sistema sobre um problema com a entrega de atividade por meio do agente SIEM, siga as etapas abaixo para recuperar os eventos de atividade no período de tempo do problema. Essas etapas o orientarão na configuração de um novo agente SIEM de recuperação que será executado em paralelo e reenviará os eventos de atividade para o SIEM.

> [!NOTE]
> O processo de recuperação reenviará todos os eventos de atividade no período de tempo descrito no alerta do sistema. Se o SIEM já contiver eventos de atividade desse período, você experimentará eventos duplicados após essa recuperação.

### <a name="step-1--configure-a-new-siem-agent-in-parallel-to-your-existing-agent"></a>Etapa 1 – configurar um novo agente SIEM em paralelo ao agente existente

1. No portal de Cloud App Security, acesse a página de extensões de segurança.
1. Na guia agentes SIEM, clique em [Adicionar um novo agente Siem](siem.md)e use o assistente para configurar os detalhes de conexão para o Siem. Por exemplo, você pode criar um novo agente SIEM com a seguinte configuração:
    - **Protocolo**: TCP
    - **Host remoto**: qualquer dispositivo em que você possa escutar uma porta. Por exemplo, uma solução simples seria usar o mesmo dispositivo que o agente e definir o endereço IP do host remoto como 127.0.0.1
    - **Porta**: qualquer porta que você possa escutar no dispositivo de host remoto

    > [!NOTE]
    > Esse agente deve ser executado em paralelo ao existente, portanto, a configuração de rede pode não ser idêntica.

1. No assistente, configure os tipos de dados para incluir **apenas as atividades** e aplicar o mesmo filtro de atividade que foi usado em seu agente Siem original (se existir).
1. Salve as configurações.
1. Execute o novo agente usando o token gerado.

### <a name="step-2--validate-the-successful-data-delivery-to-your-siem"></a>Etapa 2 – validar a entrega de dados bem-sucedida para o SIEM

Use as etapas a seguir para validar sua configuração:

1. Conecte-se ao seu SIEM e verifique se os novos dados foram recebidos do novo agente SIEM que você configurou.

> [!NOTE]
> O agente só enviará atividades no período de tempo do problema em que você foi alertado.

1. Se os dados não forem recebidos pelo seu SIEM, no novo dispositivo do agente SIEM, tente escutar a porta que você configurou para encaminhar atividades para ver se os dados estão sendo enviados do agente para o SIEM. Por exemplo, execute `netcat -l <port>` onde `<port>` é o número da porta configurada anteriormente.

> [!NOTE]
> Se você estiver usando `ncat` o, certifique-se de especificar o sinalizador IPv4 `-4` .

1. Se os dados estiverem sendo enviados pelo agente, mas não forem recebidos por seu SIEM, verifique o log do agente SIEM. Se você puder ver mensagens de "conexão recusada", verifique se o agente SIEM está configurado para usar o TLS 1,2 ou mais recente.

### <a name="step-3--remove-the-recovery-siem-agent"></a>Etapa 3 – remover o agente SIEM de recuperação

1. O agente SIEM de recuperação interromperá automaticamente o envio de dados e será desabilitado quando atingir a data de término.
1. Valide em seu SIEM que nenhum dado novo é enviado pelo agente SIEM de recuperação.
1. Pare a execução do agente em seu dispositivo.
1. No portal, vá para a página do agente SIEM e remova o agente SIEM de recuperação.
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

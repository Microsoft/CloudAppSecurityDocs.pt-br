---
title: Solucionando problemas Cloud Discovery erros-Cloud App Security | Microsoft Docs
description: Este artigo fornece uma lista de Cloud Discovery erros frequentes e recomendações de resolução para cada um.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 04/19/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: ea537c11bfb94f8f33f467ca04b5d797a3821635
ms.sourcegitcommit: 94f36e81067f05f841bec25bc31dd8983fde18f9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80675488"
---
# <a name="troubleshooting-cloud-discovery"></a>Solução de problemas do Cloud Discovery

*Aplica-se a: Microsoft Cloud App Security*

Este artigo fornece uma lista de erros de Cloud Discovery e recomendações de resolução para cada um.

## <a name="microsoft-defender-atp-integration"></a>Integração do Microsoft defender ATP

Se você integrou o Microsoft defender ATP com o Cloud App Security e não vê os resultados da integração.

|Problema|Resolução|
|----|----|
|O **ponto de extremidade do Win10** relatórios de usuários não aparecem na lista|Verifique se os computadores aos quais você está se conectando são o Windows 10 versão 1809 ou posterior e se você aguardou as duas horas necessárias para que os dados sejam acessíveis.|
|Os relatórios de descoberta estão vazios|Se o dispositivo de ponto de extremidade estiver protegido por um proxy de encaminhamento, você poderá enviar logs do proxy de encaminhamento usando um coletor de logs|

## <a name="log-parsing-errors"></a>Erros de análise de log

Você pode acompanhar o processamento de logs de Cloud Discovery usando o log de governança. Este artigo fornece ações de resolução a serem executadas para cada erro que pode ser exibido lá.

### <a name="governance-log-errors"></a>Erros de log de governança

|Error|Descrição|Resolução|
|----|----|----|
|Tipo de arquivo sem suporte|O arquivo carregado não é um arquivo de log válido (por exemplo, um arquivo de imagem).|Carregue um arquivo de **texto**, * * zip ou **gzip** que foi exportado diretamente do seu firewall ou proxy.|
|O formato de log não corresponde|O formato de log que você carregou não correspondeu ao formato de log esperado para esta fonte de dados.|1. Verifique se o log não está corrompido. <br /> 2. Compare e corresponda ao seu log com o formato de exemplo mostrado na página carregar.|
|As transações têm mais de 90 dias de idade|Todas as transações têm mais de 90 dias de idade e estão sendo ignoradas.|Exporte um novo log com eventos recentes e recarregue-o.|
|Não há transações para aplicativos de nuvem catalogados|Nenhuma transação para nenhum aplicativo de nuvem reconhecido foi encontrada no log.|Verifique se o log contém informações de tráfego de saída.|
|Tipo de log sem suporte|Quando você seleciona **fonte de dados = outros (sem suporte)** , o log não é analisado. Em vez disso, ele é enviado para revisão para a equipe técnica de Cloud App Security.|A equipe técnica de Cloud App Security cria um analisador dedicado por cada fonte de dados. As fontes de dados mais populares [já têm suporte](set-up-cloud-discovery.md). Cada carregamento de uma fonte de dados sem suporte é revisado e adicionado ao pipeline para novos analisadores de fonte de dados. As novas notificações do analisador são publicadas como parte das [notas de versão](release-notes.md)do Cloud app Security.|

## <a name="log-collector-errors"></a>Erros do coletor de log

|Problema|Resolução|
|----|----|
|Não foi possível conectar-se ao coletor de logs por FTP| 1. Verifique se você está usando credenciais de FTP e não credenciais de SSH. <br />2. Verifique se o cliente FTP que você está usando não está definido como SFTP.  |
|Falha ao atualizar a configuração do coletor | 1. Verifique se você inseriu o token de acesso mais recente. <br />2. Verifique no firewall se o coletor de logs tem permissão para iniciar o tráfego de saída na porta 443.|
|Os logs enviados ao coletor não aparecem no portal | 1. Verifique se há tarefas de análise com falha no log de governança.  <br />  &nbsp;&nbsp;&nbsp;&nbsp;se estiver, solucione o erro com a tabela de erros de análise de log acima.<br /> 2. caso contrário, verifique as fontes de dados e a configuração do coletor de logs no Portal. <br /> &nbsp;&nbsp;&nbsp;&nbsp;um. Na página fonte de dados, verifique se a fonte de dados que você está usando está configurada com precisão. <br />&nbsp;&nbsp;&nbsp;&nbsp;b. Na página coletores de logs, verifique se a fonte de dados está vinculada ao coletor de logs correto. <br /> 3. Verifique a configuração local do computador do coletor de logs local.  <br />&nbsp;&nbsp;&nbsp;&nbsp;um. Faça logon no coletor de logs por SSH e execute o utilitário collector_config.<br/>&nbsp;&nbsp;&nbsp;&nbsp;b. Confirme se o firewall ou o proxy está enviando logs para o coletor de logs usando o protocolo que você definiu (syslog/TCP, syslog/UDP ou FTP) e que ele está enviando para a porta e o diretório corretos.<br /> &nbsp;&nbsp;&nbsp;&nbsp;c. Execute o netstat no computador e verifique se ele recebe conexões de entrada do seu firewall ou proxy <br /> 4. Verifique se o coletor de logs tem permissão para iniciar o tráfego de saída na porta 443. |
|Status do coletor de log: criado | A implantação do coletor de logs não foi concluída. Conclua as etapas de implantação local de acordo com o guia de implantação.|
|Status do coletor de log: desconectado | Nenhum dado recebido nas últimas 24 horas de qualquer uma das fontes de dados vinculadas. |
|Falha ao extrair a imagem do coletor mais recente| Se você receber esse erro durante a implantação do Docker, pode ser que você não tenha memória suficiente no computador host. Para verificar isso, execute este comando no host: `docker pull microsoft/caslogcollector`. Se ele retornar esse erro: `failed to register layer: Error processing tar file(exist status 1): write /opt/jdk/jdk1.8.0_152/src.zip: no space left on device` contate o administrador do computador host para fornecer mais espaço.|

## <a name="discovery-dashboard-errors"></a>Erros do painel de descoberta

|Problema|Resolução|
|----|----|
|Os dados de descoberta foram carregados e analisados com êxito, mas o painel de Cloud Discovery parece vazio|O painel pode ser filtrado em dados que os logs não têm, portanto, não há dados a serem mostrados. Tente alterar os filtros no painel de Cloud Discovery para mostrar diferentes tipos de dados para ver os resultados.|

## <a name="next-steps"></a>{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}

> [!div class="nextstepaction"]
> [Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]

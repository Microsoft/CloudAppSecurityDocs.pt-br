---
title: Solucionando problemas de erros de Cloud Discovery
description: Este artigo apresenta uma lista de erros frequentes do Cloud Discovery e as recomendações de resolução para cada um.
ms.date: 04/19/2019
ms.topic: conceptual
ms.openlocfilehash: c8c34f6d08fa0ba360988a11dd5501546c8ec318
ms.sourcegitcommit: 7fc4d916a43d188b1aa4e3cee2e8bd1de230d135
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98206493"
---
# <a name="troubleshooting-cloud-discovery"></a>Solução de problemas do Cloud Discovery

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Este artigo apresenta uma lista de erros do Cloud Discovery e as recomendações de resolução para cada um.

## <a name="microsoft-defender-for-endpoint-integration"></a>Integração do Microsoft Defender para Ponto de Extremidade

Se você integrou o Microsoft defender for Endpoint ao Cloud App Security e não vê os resultados da integração.

|Problema|Resolução|
|----|----|
|O **ponto de extremidade do Win10** relatórios de usuários não aparecem na lista|Verifique se os dispositivos aos quais você está se conectando são o Windows 10 versão 1809 ou posterior e se você aguardou as duas horas necessárias para que os dados sejam acessíveis.|
|Os relatórios de descoberta estão vazios|Se o dispositivo de ponto de extremidade estiver protegido por um proxy de encaminhamento, você poderá enviar logs do proxy de encaminhamento usando um coletor de logs|

## <a name="log-parsing-errors"></a>Erros de análise de log

Você pode controlar o processamento dos registros do Cloud Discovery usando o log de governança. Este artigo fornece as ações de resolução a serem executadas para cada erro que pode ser exibido.

### <a name="governance-log-errors"></a>Erros de log de governança

|Erro|Descrição|Resolução|
|----|----|----|
|Tipo de arquivo sem suporte|O arquivo carregado não é um arquivo de log válido (por exemplo, um arquivo de imagem).|Carregue um arquivo de **texto**, * * zip ou **gzip** que foi exportado diretamente do seu firewall ou proxy.|
|O formato de log não corresponde|O formato de log carregado não corresponde ao esperado para esta fonte de dados.|1. Verifique se o log não está corrompido. <br /> 2. Compare e corresponda ao seu log com o formato de exemplo mostrado na página carregar.|
|As transações têm mais de 90 dias|Todas as transações têm mais de 90 dias e estão sendo ignoradas.|Exporte um novo log com eventos recentes e recarregue-o.|
|Nenhuma transação para aplicativos de nuvem catalogados|Não foi encontrada no log nenhuma transação com aplicativos de nuvem reconhecidos.|Verifique se o log contém informações sobre o tráfego de saída.|
|Tipo de log sem suporte|Quando você seleciona **Fonte de dados = outra (sem suporte)**, o log não é analisado. Nesse caso, ele é enviado à equipe técnica do Cloud App Security para ser analisado.|A equipe técnica do Cloud App Security cria um analisador dedicado por cada fonte de dados. As fontes de dados mais populares [já têm suporte](set-up-cloud-discovery.md). Cada upload de uma fonte de dados sem suporte é revisado e adicionado ao pipeline de analisadores de novas fontes de dados. Novas notificações de analisador são publicadas como parte das [notas de versão](release-notes.md) do Cloud App Security.|

## <a name="log-collector-errors"></a>Erros do coletor de logs

|Problema|Resolução|
|----|----|
|Não foi possível conectar ao coletor de logs por FTP| 1. Verifique se você está usando credenciais de FTP e não credenciais de SSH. <br />2. Verifique se o cliente FTP que você está usando não está definido como SFTP.  |
|Falha ao atualizar a configuração do coletor | 1. Verifique se você inseriu o token de acesso mais recente. <br />2. Verifique no firewall se o coletor de logs tem permissão para iniciar o tráfego de saída na porta 443.|
|Logs enviados ao coletor não aparecem no portal | 1. Verifique se há tarefas de análise com falha no log de governança.  <br />  &nbsp;&nbsp;&nbsp;&nbsp;Se houver, corrija o erro com a tabela de erros de Análise de Log acima.<br /> 2. caso contrário, verifique as fontes de dados e a configuração do coletor de logs no Portal. <br /> &nbsp;&nbsp;&nbsp;&nbsp;a. Na página fonte de dados, verifique se o nome da fonte de dados é **NSS** e se está configurado corretamente. <br />&nbsp;&nbsp;&nbsp;&nbsp;b. Na página Coletores de Logs, verifique se que a fonte de dados está vinculada ao coletor de logs correto. <br /> 3. Verifique a configuração local do computador do coletor de logs local.  <br />&nbsp;&nbsp;&nbsp;&nbsp;a. Faça logon no coletor de logs via SSH e execute o utilitário collector_config.<br/>&nbsp;&nbsp;&nbsp;&nbsp;b. Confirme se seu firewall ou proxy está enviando logs para o coletor de logs usando o protocolo definido (Syslog/TCP, Syslog/UDP ou FTP) e se ele está enviando para a porta e diretório corretos.<br /> &nbsp;&nbsp;&nbsp;&nbsp;c. Execute netstat no computador e verifique se ele recebe conexões de entrada de seu proxy ou firewall <br /> 4. Verifique se o coletor de logs tem permissão para iniciar o tráfego de saída na porta 443. |
|Status do coletor de logs: criado | A implantação do coletor de logs não foi concluída. Conclua as etapas de implantação locais de acordo com a guia de implantação.|
|Status do coletor de logs: desconectado | Não há dados recebidos nas últimas 24 horas de qualquer uma das fontes de dados vinculados. |
|Falha ao extrair a imagem do coletor mais recente| Se você receber esse erro durante a implantação do Docker, pode ser que você não tenha memória suficiente no host. Para verificar isso, execute este comando no host: `docker pull mcr.microsoft.com/mcas/logcollector` . Se ele retornar este erro: `failed to register layer: Error processing tar file(exist status 1): write /opt/jdk/jdk1.8.0_152/src.zip: no space left on device` contate o administrador da máquina host para fornecer mais espaço.|

## <a name="discovery-dashboard-errors"></a>Erros do painel de descoberta

|Problema|Resolução|
|----|----|
|Dados de descoberta foram carregados e analisados com êxito, mas o painel do Cloud Discovery parece vazio|O painel pode estar filtrado por dados que os logs não têm e, portanto, não há dados a serem exibidos. Tente alterar os filtros no painel do Cloud Discovery para mostrar os diferentes tipos de dados para ver os resultados.|

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]

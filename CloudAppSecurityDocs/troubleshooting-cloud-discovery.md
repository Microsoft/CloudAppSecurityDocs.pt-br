---
title: Solução de problemas de erros do Cloud Discovery – Cloud App Security | Microsoft Docs
description: Este artigo apresenta uma lista de erros frequentes do Cloud Discovery e as recomendações de resolução para cada um.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/10/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 76dfaebb-d477-4bdb-b3d7-04cc3fe6431d
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 17890e4b54b4ed6447b274dc7e266011f8be236d
ms.sourcegitcommit: b86c3afd1093fbc825fec5ba4103e3a95f65758e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53176919"
---
# <a name="troubleshooting-cloud-discovery"></a>Solucionando problemas de Cloud Discovery

*Aplica-se a: Microsoft Cloud App Security*

Este artigo apresenta uma lista de erros do Cloud Discovery e as recomendações de resolução para cada um.

## <a name="log-parsing-errors"></a>Erros de análise de log

Você pode controlar o processamento dos registros do Cloud Discovery usando o log de governança. Este artigo fornece as ações de resolução a serem executadas para cada erro que pode ser exibido.

### <a name="governance-log-errors"></a>Erros de log de governança

|Erro do|Descrição|Resolução|
|----|----|----|
|Tipo de arquivo sem suporte|O arquivo carregado não é um arquivo de log válido (por exemplo, um arquivo de imagem).|Carregue um arquivo de **texto**, **zip ou **gzip** que foi exportado diretamente do seu firewall ou proxy.|
|O formato de log não corresponde|O formato de log carregado não corresponde ao esperado para esta fonte de dados.|1. Verifique se o log não está corrompido. <br /> 2. Compare e corresponda o log com o formato de exemplo mostrado na página de upload.|
|As transações têm mais de 90 dias|Todas as transações têm mais de 90 dias e estão sendo ignoradas.|Exporte um novo log com eventos recentes e recarregue-o.|
|Nenhuma transação para aplicativos de nuvem catalogados|Não foi encontrada no log nenhuma transação com aplicativos de nuvem reconhecidos.|Verifique se o log contém informações sobre o tráfego de saída.|
|Tipo de log sem suporte|Quando você seleciona **Fonte de dados = outra (sem suporte)**, o log não é analisado. Nesse caso, ele é enviado à equipe técnica do Cloud App Security para ser analisado.|A equipe técnica do Cloud App Security cria um analisador dedicado por cada fonte de dados. As fontes de dados mais populares [já têm suporte](set-up-cloud-discovery.md). Cada upload de uma fonte de dados sem suporte é revisado e adicionado ao pipeline de analisadores de novas fontes de dados. Novas notificações de analisador são publicadas como parte das [notas de versão](release-notes.md) do Cloud App Security.|

## <a name="log-collector-errors"></a>Erros do coletor de logs

|PROBLEMA | RESOLUÇÃO |
|--------|--|
|Não foi possível conectar ao coletor de logs por FTP| 1. Verifique se você estiver usando credenciais FTP e não SSH. <br />2. Verifique se o cliente FTP que você está usando não está definido para SFTP.  |
|Falha ao atualizar a configuração do coletor | 1. Verifique se você inseriu o token de acesso mais recente. <br />2. Verifique no seu firewall se o coletor de logs tem permissão para iniciar o tráfego de saída na porta 443.|
|Logs enviados ao coletor não aparecem no portal | 1.  Verifique se há tarefas de análise com falha no Log de governança.  <br />  &nbsp;&nbsp;&nbsp;&nbsp;Se houver, corrija o erro com a tabela de erros de Análise de Log acima.<br /> 2. Caso contrário, verifique as fontes de dados e a configuração do Coletor de Logs no portal. <br /> &nbsp;&nbsp;&nbsp;&nbsp;a. Na página Fonte de dados, verifique se a fonte de dados que você está usando está devidamente configurada. <br />&nbsp;&nbsp;&nbsp;&nbsp;b. Na página Coletores de Logs, verifique se que a fonte de dados está vinculada ao coletor de logs correto. <br /> 3. Verifique a configuração local do computador local do coletor de logs.  <br />&nbsp;&nbsp;&nbsp;&nbsp;a. Faça logon no coletor de logs via SSH e execute o utilitário collector_config.<br/>&nbsp;&nbsp;&nbsp;&nbsp;b. Confirme se seu firewall ou proxy está enviando logs para o coletor de logs usando o protocolo definido (Syslog/TCP, Syslog/UDP ou FTP) e se ele está enviando para a porta e diretório corretos.<br /> &nbsp;&nbsp;&nbsp;&nbsp;c. Execute netstat no computador e verifique se ele recebe conexões de entrada de seu proxy ou firewall <br /> 4.   Verifique se o coletor de logs tem permissão para iniciar o tráfego de saída na porta 443. |
|Status do coletor de logs: Criado | A implantação do coletor de logs não foi concluída. Conclua as etapas de implantação locais de acordo com a guia de implantação.|
|Status do coletor de logs: Disconnected | Não há dados recebidos nas últimas 24 horas de qualquer uma das fontes de dados vinculados. |


## <a name="discovery-dashboard-errors"></a>Erros do painel de descoberta

|Problema|Resolução|
|----|----|
|Dados de descoberta foram carregados e analisados com êxito, mas o painel do Cloud Discovery parece vazio|O painel pode estar filtrado por dados que os logs não têm e, portanto, não há dados a serem exibidos. Tente alterar os filtros no painel do Cloud Discovery para mostrar os diferentes tipos de dados para ver os resultados.|

## <a name="next-steps"></a>Próximas etapas
  
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/)  


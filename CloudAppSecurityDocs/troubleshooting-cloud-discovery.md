---
title: "Solução de problemas de Cloud Discovery | Microsoft Docs"
description: "Este tópico fornece uma lista de erros frequentes do Cloud Discovery e recomendações de resolução para cada um."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 76dfaebb-d477-4bdb-b3d7-04cc3fe6431d
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed4ea71b24767d3602d40894d1cbac7447bcd8a2
ms.openlocfilehash: 2d0b2cebdfa15cccc5888660da498446d620b64f


---

# <a name="troubleshooting-cloud-discovery"></a>Solucionando problemas de Cloud Discovery
## <a name="log-parsing-errors"></a>Erros de análise de log

Você pode controlar o processamento dos registros do Cloud Discovery usando o log de governança. Este guia fornece as ações de resolução a serem executada para cada erro que pode ser exibido.

### <a name="governance-log-errors"></a>Erros de log de governança
|ERRO|DESCRIÇÃO|RESOLUÇÃO|
|----|----|----|
|Tipo de arquivo sem suporte|O arquivo carregado não é um arquivo de log válido (por exemplo, um arquivo de imagem).|Carregue um arquivo de **texto**, **zip** ou **gzip** que foi exportado diretamente do seu firewall ou proxy.|
|Erro interno|Foi detectada uma falha de recurso interno|Clique em **Tetar novamente** para executar a tarefa novamente.|
|O formato de log não corresponde|O formato de log que você carregou não coincide com o esperado para esta fonte de dados.|1. Verifique se o log não está corrompido. <br /> 2. Compare e corresponda o log com o formato de exemplo mostrado na página de upload.|
|As transações têm mais de 90 dias|Todas as transações têm mais de 90 dias e, portanto, estão sendo ignorados.|Exporte um novo log com os eventos recentes e faça upload dele novamente.|
|Nenhuma transação para aplicativos de nuvem catalogados|Nenhuma transação para quaisquer aplicativos de nuvem reconhecidos foi encontrada no log.|Verifique se o log contém informações sobre o tráfego de saída.|
|Tipo de log sem suporte|Quando você seleciona **Fonte de dados = Outro (sem suporte)**, o log não é analisado. Em vez disso, ele é enviado para análise para a equipe técnica do Cloud App Security.|A equipe técnica do Cloud App Security cria um analisador dedicado por cada fonte de dados. As fontes de dados mais populares [já têm suporte](set-up-cloud-discovery.md). Cada upload de uma fonte de dados sem suporte é revisado e adicionado ao pipeline de analisadores de novas fontes de dados. Novas notificações de analisador são publicadas como parte das notas de versão do Cloud App Security.|
## <a name="log-collector-errors"></a>Erros do coletor de logs

|PROBLEMA|RESOLUÇÃO|
|----|----|
|Não foi possível conectar ao coletor de logs por FTP|1. Verifique se você estiver usando credenciais FTP e não SSH. <br />2. Verifique se o cliente FTP que você está usando não está definido para SFTP.|
|Falha ao atualizar a configuração do coletor|1. Verifique se você inseriu o token de acesso mais recente. <br />2. Verifique no seu firewall se o coletor de logs tem permissão para iniciar o tráfego de saída na porta 443.|
|Logs enviados ao coletor não aparecem no portal|1.  Verifique se há tarefas de análise com falha no Log de governança.  <br />  &nbsp;&nbsp;&nbsp;&nbsp;Se houver, corrija o erro com a tabela de erros de Análise de Log acima.<br /> 2. Caso contrário, verifique as fontes de dados e a configuração do Coletor de Logs no portal. <br /> &nbsp;&nbsp;&nbsp;&nbsp;a. Na página Fonte de dados, verifique se a fonte de dados que você está usando está devidamente configurada. <br />&nbsp;&nbsp;&nbsp;&nbsp;b. Na página Coletores de Logs, verifique se que a fonte de dados está vinculada ao coletor de logs correto. <br /> 3. Verifique a configuração local do computador local do coletor de logs.  <br />&nbsp;&nbsp;&nbsp;&nbsp;a. Faça logon no coletor de logs via SSH e execute o utilitário collector_config.<br/>&nbsp;&nbsp;&nbsp;&nbsp;b. Confirme se seu firewall ou proxy está enviando logs para o coletor de logs usando o protocolo definido (Syslog/TCP, Syslog/UDP ou FTP) e se ele está enviando para a porta e diretório corretos.<br /> &nbsp;&nbsp;&nbsp;&nbsp;c. Execute netstat no computador e verifique se ele recebe conexões de entrada de seu proxy ou firewall <br /> 4.   Verifique se o coletor de logs tem permissão para iniciar o tráfego de saída na porta 443.|

## <a name="see-also"></a>Veja também  
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Nov16_HO5-->



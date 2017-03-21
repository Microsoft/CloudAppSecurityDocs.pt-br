---
title: "Solução de problemas de erros de inspeção de conteúdo no Cloud App Security | Microsoft Docs"
description: "Este tópico fornece uma lista de status de inspeção de conteúdo e seus significados."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/23/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 359eb77f-e719-4c50-9b62-6ef64149a5a5
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 02451f0bc49cc5b3365673806562708943de7cfd
ms.sourcegitcommit: 355226ee21981563066d637e7db0bff0d53c2da6
translationtype: HT
---
# <a name="troubleshooting-content-inspection"></a>Solução de problemas de inspeção de conteúdo
|Status da inspeção de conteúdo|Descrição|
|----|----|
|Concluído|A inspeção de conteúdo foi concluída com êxito.|
|Não Aplicável|A inspeção de conteúdo não era aplicável para este arquivo. Isso pode ser porque nenhuma política requer a inspeção de conteúdo desse arquivo ou porque não há suporte para o tipo de arquivo.|
|Pending (Pendente)|O arquivo está na fila de inspeção de conteúdo no momento.|
|Falha: Erro no download|O Cloud App Security não pôde baixar o arquivo para inspeção.|
|Falha: O arquivo está criptografado|Não foi possível descriptografar o arquivo.|
|Falha: O arquivo está corrompido|O arquivo está corrompido de alguma forma e não pode ser inspecionado.|
|Falha: Erro interno|Ocorreu um erro indeterminado ao tentar verificar o arquivo.|
|Falha: Erro do DLP externo|Algo em seu DLP externo deu errado, causando uma falha ao inspecionar o conteúdo no Cloud App Security.|
|Falha: tamanho do arquivo excedido|O limite do arquivo varia dependendo do tamanho do arquivo e do número de caracteres.|
|Falha: Acesso ao arquivo negado|O arquivo externo à sua nuvem e não pôde ser acessado pelo Cloud App Security.|
|Falha: O arquivo foi excluído|O arquivo não existe na sua nuvem e não pode ser inspecionado.|
|Falha: tipo de arquivo sem suporte|O Cloud App Security não pode executar a inspeção de conteúdo nesse tipo de arquivo. Isso pode ter ocorrido porque não há suporte para o tipo de arquivo ou porque o arquivo não é realmente do formato do tipo de arquivo esperado.|

> [!NOTE]
> Se você encontrar um traço no status de verificação, isso indicará que o arquivo não está na fila para ser verificado. Consulte [Políticas de arquivos](data-protection-policies.md) para obter informações sobre a configuração de políticas de inspeção de conteúdo.

## <a name="see-also"></a>Veja também  
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
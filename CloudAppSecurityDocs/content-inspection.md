---
title: "Inspeção de Conteúdo | Microsoft Docs"
description: "seu artigo descreve o processo que o Cloud App Security segue ao executar a inspeção de conteúdo DLP nos dados na nuvem."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 2401adbc-0011-4938-9e3a-a4c719a2f619
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed4ea71b24767d3602d40894d1cbac7447bcd8a2
ms.openlocfilehash: ea1854d6bf32e01afe6183409b68ded32ee37dd1


---

# <a name="content-inspection"></a>Inspeção de Conteúdo
Este artigo descreve o processo que o Cloud App Security segue ao executar a inspeção de conteúdo DLP nos dados na nuvem. 


A inspeção de conteúdo do Cloud App Security funciona da seguinte maneira:
1. O Cloud App Security executa uma verificação contínua de todos os arquivos relevantes em todas as unidades. 
2. O Cloud App Security executa uma verificação NRT (Quase em Tempo Real) de unidades e eventos que são detectados como novos ou alterados. 

Tanto os arquivos na verificação contínua quanto aqueles na verificação NRT são adicionados à fila para inspeção. A ordem dos arquivos na fila de verificação é definida por atividade nos arquivos e na verificação das suas unidades. Os arquivos são verificados somente se os metadados do arquivo mostrarem que se trata de um tipo MIME com suporte. Se essa verificação for para arquivos que são relevantes para a verificação de dados (documentos, imagens, apresentações, planilhas, arquivos de texto e zip/arquivo morto).  

Depois que um arquivo é verificado, ocorre o seguinte:

1. O Cloud App Security aplica a todas as suas políticas personalizadas relacionadas aos metadados e não ao próprio conteúdo. Por exemplo, uma política que avisa quando os arquivos excedem 20 MB ou quando arquivos docx são salvos no OneDrive. 

2. Se houver uma política que exija a inspeção de conteúdo e o arquivo se qualifica para tal, o conteúdo será enfileirado para inspeção. O comprimento da fila depende do tamanho do locatário e o número de arquivos que exigem a verificação. 

3. Neste ponto, você pode exibir o status de inspeção do conteúdo acessando **Investigar** > **Arquivos** e clicando em um arquivo. Na gaveta de arquivos que se abre com os detalhes do arquivo, o **status de Inspeção de Conteúdo** exibirá um dos seguintes: 

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

## <a name="see-also"></a>Veja também  
[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  


<!--HONumber=Oct16_HO4-->



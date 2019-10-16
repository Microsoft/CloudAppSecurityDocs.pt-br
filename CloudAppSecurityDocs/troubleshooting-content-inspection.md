---
title: Solução de problemas de erros de inspeção de conteúdo – Cloud App Security | Microsoft Docs
description: Este artigo fornece uma lista de status de inspeção de conteúdo e seus significados.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 359eb77f-e719-4c50-9b62-6ef64149a5a5
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 6d2ffb878cc48c619a7e5026b2f51dd7407c038b
ms.sourcegitcommit: c342abeec95359ddabdabcc3a081a0f91d52407c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72336156"
---
# <a name="troubleshooting-content-inspection"></a>Solução de problemas de inspeção de conteúdo

*Aplica-se ao: Microsoft Cloud App Security*

Este artigo fornece uma lista de status de inspeção de conteúdo e seus significados.

## <a name="content-inspection-status"></a>Status da inspeção de conteúdo

A tabela lista cada status de inspeção de conteúdo e sua descrição.

|Status da inspeção de conteúdo|Description|
|----|----|
|Concluído|A inspeção de conteúdo foi concluída com êxito.|
|Não Aplicável|A inspeção de conteúdo não era aplicável a este arquivo. Esse status pode aparecer porque nenhuma política requer a inspeção de conteúdo desse arquivo ou porque não há suporte para esse tipo de arquivo.|
|Pending (Pendente)|O arquivo está na fila de inspeção de conteúdo no momento.|
|Falha: Erro no download|O Microsoft Cloud App Security não pôde baixar o arquivo para inspeção.|
|Falha: O arquivo está criptografado|O arquivo não pôde ser descriptografado.|
|Falha: O arquivo está corrompido|O arquivo está corrompido de alguma forma e não pôde ser inspecionado.|
|Falha: Erro interno|Ocorreu um erro indeterminado ao tentar verificar o arquivo.|
|Falha: Erro do DLP externo|Algo em seu DLP externo deu errado, causando uma falha ao inspecionar o conteúdo no Cloud App Security.|
|Falha: tamanho do arquivo excedido|O limite do arquivo varia dependendo do tamanho do arquivo e do número de caracteres.|
|Falha: Acesso ao arquivo negado|O arquivo é externo à sua nuvem e não pôde ser acessado pelo Cloud App Security.|
|Falha: O arquivo foi excluído|O arquivo não existe mais na sua nuvem e não pôde ser inspecionado.|
|Falha: tipo de arquivo sem suporte|O Cloud App Security não pode executar a inspeção de conteúdo nesse tipo de arquivo. Esse status pode aparecer porque não há suporte para o tipo de arquivo ou porque o arquivo não está no formato do tipo de arquivo esperado.|

> [!NOTE]
> Se você encontrar um traço no status de verificação, isso indicará que o arquivo não está na fila para ser verificado. Consulte [Políticas de arquivos](data-protection-policies.md) para obter informações sobre a configuração de políticas de inspeção de conteúdo.

## <a name="see-also"></a>Confira Também  
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/)  

## <a name="next-steps"></a>Próximas etapas
 
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)


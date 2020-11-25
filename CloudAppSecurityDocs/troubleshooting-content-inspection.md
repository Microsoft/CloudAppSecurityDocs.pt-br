---
title: Solucionando problemas de erros de inspeção de conteúdo
description: Este artigo fornece uma lista de status de inspeção de conteúdo e seus significados.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 05/25/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 50c240d70492b9db22e584a1fdc2c438e982bb01
ms.sourcegitcommit: a0a8e25bda77fb21f280a0e504896be85b89ed6f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96034085"
---
# <a name="troubleshooting-content-inspection"></a>Solução de problemas de inspeção de conteúdo

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Este artigo fornece uma lista de status de inspeção de conteúdo e seus significados.

## <a name="content-inspection-status"></a>Status da inspeção de conteúdo

A tabela lista cada status de inspeção de conteúdo e sua descrição.

|Status da inspeção de conteúdo|Descrição|
|---|---|
|Concluído|A inspeção de conteúdo foi concluída com êxito.|
|Não aplicável|A inspeção de conteúdo não era aplicável a este arquivo. Esse status pode aparecer porque nenhuma política requer a inspeção de conteúdo desse arquivo ou porque não há suporte para esse tipo de arquivo.|
|Pendente|O arquivo está na fila de inspeção de conteúdo no momento.|
|Falha: Erro no download|O Microsoft Cloud App Security não pôde baixar o arquivo para inspeção.|
|Falha: O arquivo está criptografado|O arquivo não pôde ser descriptografado.|
|Falha: O arquivo está corrompido|O arquivo está corrompido de alguma forma e não pôde ser inspecionado.|
|Falha: Erro interno|Ocorreu um erro indeterminado ao tentar verificar o arquivo.|
|Falha: Erro do DLP externo|Algo em seu DLP externo deu errado, causando uma falha ao inspecionar o conteúdo no Cloud App Security.|
|Falha: tamanho do arquivo excedido|O arquivo excedeu o tamanho de arquivo máximo de 50 MB.|
|Falha: o arquivo é muito longo e foi parcialmente verificado|O arquivo excedeu o máximo de 1 milhão caracteres. Para a parte do conteúdo que foi examinado, as correspondências de política relevantes foram aplicadas.|
|Falha: Acesso ao arquivo negado|O arquivo é externo à sua nuvem e não pôde ser acessado pelo Cloud App Security.|
|Falha: O arquivo foi excluído|O arquivo não existe mais na sua nuvem e não pôde ser inspecionado.|
|Falha: tipo de arquivo sem suporte|O Cloud App Security não pode executar a inspeção de conteúdo nesse tipo de arquivo. Esse status pode aparecer porque não há suporte para o tipo de arquivo ou porque o arquivo não está no formato do tipo de arquivo esperado.|

> [!NOTE]
> Se você encontrar um traço no status de verificação, isso indicará que o arquivo não está na fila para ser verificado. Consulte [Políticas de arquivos](data-protection-policies.md) para obter informações sobre a configuração de políticas de inspeção de conteúdo.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]

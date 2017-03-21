---
title: "Como o Cloud App Security executa inspeção de conteúdo | Microsoft Docs"
description: "seu artigo descreve o processo que o Cloud App Security segue ao executar a inspeção de conteúdo DLP nos dados na nuvem."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/23/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 2401adbc-0011-4938-9e3a-a4c719a2f619
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: a1ff57c60d8b35711330e8e4879fe1a48a7dee77
ms.sourcegitcommit: 355226ee21981563066d637e7db0bff0d53c2da6
translationtype: HT
---
# <a name="content-inspection"></a>Inspeção de conteúdo
Este artigo descreve o processo que o Cloud App Security segue ao executar a inspeção de conteúdo DLP nos dados na nuvem. 


A inspeção de conteúdo do Cloud App Security funciona da seguinte maneira:
1. Primeiro, o Cloud App Security executa uma verificação NRT (Quase em Tempo Real) de unidades e eventos detectados como novos ou alterados.
2. Depois de concluir isso, o Cloud App Security executa uma verificação contínua de todos os arquivos relevantes em todas as unidades.  

Tanto os arquivos na verificação NRT quanto aqueles na verificação contínua são adicionados à fila para inspeção. A ordem dos arquivos na fila de verificação é definida por atividade nos arquivos e na verificação das suas unidades. Os arquivos são verificados somente se os metadados do arquivo mostrarem que se trata de um tipo MIME com suporte. Se essa verificação for para arquivos que são relevantes para a verificação de dados (documentos, imagens, apresentações, planilhas, arquivos de texto e zip/arquivo morto).  

Depois que um arquivo é verificado, ocorre o seguinte:

1. O Cloud App Security aplica a todas as suas políticas personalizadas relacionadas aos metadados e não ao próprio conteúdo. Por exemplo, uma política que avisa quando os arquivos excedem 20 MB ou quando arquivos docx são salvos no OneDrive. 

2. Se houver uma política que exija a inspeção de conteúdo e o arquivo se qualifica para tal, o conteúdo será enfileirado para inspeção. O comprimento da fila depende do tamanho do locatário e o número de arquivos que exigem a verificação. 

3. Neste ponto, você pode exibir o status de inspeção do conteúdo acessando **Investigar** > **Arquivos** e clicando em um arquivo. Na gaveta de arquivos que é aberta com os detalhes do arquivo, o **Status de inspeção de conteúdo** exibirá **Concluído**, **Pendente**, **Não aplicável** (se não houver suporte para o tipo de arquivo) ou uma mensagem de falha. Para obter informações sobre mensagens de falha de verificação de conteúdo, consulte [Solução de problemas de inspeção de conteúdo](troubleshooting-content-inspection.md).

> [!NOTE]
> Se você encontrar um traço no status de verificação, isso indicará que o arquivo não está na fila para ser verificado. Consulte [Políticas de arquivos](data-protection-policies.md) para obter informações sobre a configuração de políticas de inspeção de conteúdo.

As políticas internas de verificação de inspeção de conteúdo podem pesquisar o seguinte:

- Endereços de email 
- Números de cartão de crédito 
  - Todas as empresas de cartão de crédito (Visa, MasterCard, American Express, Diners Club, Discover, JCB, Dankort, UnionPay) 
  - Delimitadores: espaço, ponto ou traço
  - Essa verificação também inclui a validação de Luhn
- Códigos SWIFT
- Números de passaporte internacional
- Números de carteira de motorista
- Datas
- Números de trânsito de roteamento de banco da ABA (American Bankers Association)
- Códigos de identificação do banco
- Números de declaração de plano de saúde HICN da HIPAA (Health Insurance Portability Accountability Act)
- Números de identificador de provedor NPI nacional da HIPAA
- Nome completo e data de nascimento de PHI
- Números de carteira de motorista ou ID da Califórnia
- Números de carteira de motorista
- Endereço residencial
- Cartões de passaporte
- Números do seguro social



## <a name="see-also"></a>Veja também  
[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
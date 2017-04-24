---
title: "Como o Cloud App Security executa inspeção de conteúdo | Microsoft Docs"
description: "seu artigo descreve o processo que o Cloud App Security segue ao executar a inspeção de conteúdo DLP nos dados na nuvem."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/23/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 2401adbc-0011-4938-9e3a-a4c719a2f619
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 1083a743f2602bab6e55e96e1e7f7dd4c0b77bce
ms.sourcegitcommit: fd3b6c04cec30f7c9300cc02d29d562d17bf43ea
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
  -    Todas as empresas de cartão de crédito (Visa, MasterCard, American Express, Diners Club, Discover, JCB, Dankort, UnionPay) 
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

## <a name="supported-languages"></a>Idiomas com suporte

O mecanismo de inspeção de conteúdo do Cloud App Security:
-    Oferece suporte a todos os caracteres Unicode
-    Abrange mais de 1.000 tipos de arquivo
-    Oferece suporte a vários idiomas, especialmente arquivos que usam os conjuntos de caracteres Unicode. Defina suas políticas para considerar esses idiomas; por exemplo se você estiver procurando palavras-chave, deve defini-las para os idiomas que você pretende usar.
-    Comparar tipos de arquivo baseados em texto que usam codificação diferente de Unicode, por exemplo chinês GB2312, com palavras-chave em chinês Unicode não funcionará conforme o esperado.
-    Para tipos de arquivo que se baseiam em bibliotecas de terceiros, corresponder cadeias de caracteres e palavras pode não funcionar conforme o esperado em todos os momentos. Isso é mais comum em arquivos (como tipos de arquivo binários) em que a inspeção de conteúdo se baseia em bibliotecas de terceiros que retornam cadeias de caracteres Java para conjuntos de idiomas e caracteres.



## <a name="see-also"></a>Veja também  
[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
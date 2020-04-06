---
title: Como Cloud App Security executa a inspeção de conteúdo
description: Este artigo descreve o processo Cloud App Security segue ao executar inspeção de conteúdo DLP nos dados em sua nuvem.
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
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 543631f5ffaa6716d8686e86e1386b55c081158b
ms.sourcegitcommit: 288c279a0d2dd62a8ad8d7425c3e9e98857bf5f4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/05/2020
ms.locfileid: "80666471"
---
# <a name="built-in-content-inspection"></a>Inspeção de conteúdo interna

*Aplica-se a: Microsoft Cloud App Security*

Este artigo descreve o processo Microsoft Cloud App Security segue ao executar a inspeção de conteúdo de DLP interno nos dados em sua nuvem.

Cloud App Security inspeção de conteúdo funciona da seguinte maneira:

1. Primeiro, Cloud App Security executa uma verificação quase em tempo real (NRT) de unidades e eventos que são detectados para serem novos ou alterados.
2. Depois que a verificação for concluída, Cloud App Security executará uma verificação contínua de todos os arquivos relevantes em todas as unidades.

Os arquivos na verificação de NRT e a verificação contínua são adicionados à fila para inspeção. A ordem dos arquivos na fila de verificação é definida por atividade nos arquivos e na verificação de suas unidades. Os arquivos serão verificados somente se os metadados do arquivo mostrarem que é um tipo MIME com suporte. Essa verificação é para arquivos que são relevantes para verificação de dados (documentos, imagens, apresentações, planilhas, texto e arquivos zip/mortos).

Depois que um arquivo é examinado, ocorrem as seguintes ações:

1. Cloud App Security aplica todas as suas políticas personalizadas relacionadas aos metadados e não ao próprio conteúdo. Por exemplo, uma política que alerta quando os arquivos são mais de 20 MB ou uma política que o alerta quando arquivos docx são salvos no OneDrive.

2. Se houver uma política que exija inspeção de conteúdo e o arquivo for qualificado para inspeção de conteúdo, o conteúdo será enfileirado para inspeção. O comprimento da fila depende do tamanho do locatário e do número de arquivos que exigem verificação.

3. Neste ponto, você pode exibir o status da inspeção de conteúdo indo para **investigar** > **arquivos** e clicando em um arquivo. Na gaveta do arquivo que é aberta com os detalhes do arquivo, o **status de inspeção do conteúdo** será exibido como **concluído**, **pendente**, **não aplicável** (se o tipo de arquivo não tiver suporte) ou uma mensagem de falha. Para obter informações sobre mensagens de falha de verificação de conteúdo, consulte [Solucionando problemas de inspeção de conteúdo](troubleshooting-content-inspection.md).

> [!NOTE]
> Se você vir um traço no status da verificação, isso significa que o arquivo não está enfileirado para ser verificado. Consulte [políticas de arquivo](data-protection-policies.md) para obter informações sobre como definir políticas de inspeção de conteúdo.

As políticas de exame de inspeção de conteúdo interno podem pesquisar os seguintes itens:

- Endereços de email
- Números de cartão de crédito
  - Todas as empresas de cartão de crédito (Visa, MasterCard, American Express, clientes Club, Discover, JCB, Dankort, UnionPay)
  - Delimitadores-espaço, ponto ou traço
  - Essa verificação também inclui a validação de Luhn
- Códigos SWIFT
- Números do passaporte internacional
- Números de licença dos drivers
- Datas
- Números de trânsito de roteamento de ABA bancário
- Códigos de identificador bancários
- Números de declaração de seguro de saúde HICN da HIPAA
- Números de identificador de provedor do HIPAA NPI National
- PHI de nome completo e datas de nascimento
- Números de licença da ID ou dos drivers da Califórnia
- Números de licença dos drivers
- Endereços residenciais
- Cartões do Passport
- Números de seguro social

## <a name="supported-languages"></a>Idiomas com suporte

O mecanismo de inspeção de conteúdo Cloud App Security:

- Dá suporte a todos os caracteres Unicode
- Cobre mais de 100 tipos de arquivo
- Há suporte para vários idiomas, especialmente arquivos que usam conjuntos de caracteres Unicode. Certifique-se de definir suas políticas para considerar esses idiomas. Por exemplo, se você estiver procurando palavras-chave, deverá colocar as palavras-chave nos idiomas que pretende usar.
- Em tipos de arquivo baseados em texto que usam codificação não-Unicode, por exemplo, chinês GB2312, a comparação com palavras-chave do chinês Unicode não funcionará conforme o esperado.
- Para tipos de arquivo que dependem de bibliotecas de terceiros, cadeias de caracteres e palavras correspondentes nem sempre podem funcionar conforme o esperado. Isso é mais comum em arquivos (como tipos de arquivo binários) em que a inspeção de conteúdo depende de bibliotecas de terceiros que retornam cadeias de caracteres Java para conjuntos de idiomas e de caractere.

## <a name="next-steps"></a>{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}

> [!div class="nextstepaction"]
> [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]

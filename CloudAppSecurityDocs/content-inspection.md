---
title: Como Cloud App Security executa a inspeção de conteúdo
description: Este artigo descreve o processo Cloud App Security segue ao executar inspeção de conteúdo DLP nos dados em sua nuvem.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 1/6/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 82d157bbe887f70194cbb55708635759e48433b1
ms.sourcegitcommit: 288c279a0d2dd62a8ad8d7425c3e9e98857bf5f4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/05/2020
ms.locfileid: "80666448"
---
# <a name="content-inspection"></a>Inspeção de conteúdo

*Aplica-se a: Microsoft Cloud App Security*

Se você habilitar a inspeção de conteúdo, poderá optar por usar expressões predefinidas ou pesquisar outras expressões personalizadas.

Você pode especificar uma expressão regular para excluir um arquivo dos resultados. Essa opção será altamente útil se você tiver um padrão de palavra-chave de classificação interna que você deseja excluir da política.

Você pode decidir definir o número mínimo de violações de conteúdo que deseja corresponder antes que o arquivo seja considerado uma violação. Por exemplo, você pode escolher 10 se deseja ser alertado em arquivos com pelo menos 10 números de cartão de crédito encontrados em seu conteúdo.

Quando o conteúdo é correspondido em relação à expressão selecionada, o texto de violação é substituído por caracteres "X". Por padrão, as violações são mascaradas e mostradas em seu contexto exibindo 100 caracteres antes e depois da violação. Os números no contexto da expressão são substituídos por caracteres "#" e nunca são armazenados dentro de Cloud App Security. Você pode selecionar a opção para **remover a máscara dos últimos quatro caracteres de uma violação** para remover a máscara dos últimos quatro caracteres da violação em si. É necessário definir quais tipos de dados são pesquisados pela expressão regular: conteúdo, metadados e/ou nome do arquivo. Por padrão, ele pesquisa o conteúdo e os metadados.

## <a name="content-inspection-for-protected-files"></a>Inspeção de conteúdo para arquivos protegidos

Cloud App Security permite que os administradores concedam Cloud App Security permissão para descriptografar arquivos criptografados e verificar o conteúdo em busca de violações.

Para fornecer ao Cloud app Security as permissões necessárias:

1. Vá para **configurações** e, em seguida, **proteção de informações do Azure**.
2. Habilitar **inspecionar arquivos protegidos.**
3. Siga o prompt para permitir as permissões necessárias no Azure Active Directory.
4. Você pode definir as configurações por política de arquivo para determinar quais políticas verificará arquivos protegidos.

## <a name="next-steps"></a>{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}

> [!div class="nextstepaction"]
> [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]

---
title: Como o Cloud App Security executa a inspeção de conteúdo
description: Este artigo descreve o processo que o Cloud App Security segue ao executar a inspeção de conteúdo DLP nos dados na nuvem.
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
ms.openlocfilehash: 83969121e83bfa2efae352fc66de00766c23e5d9
ms.sourcegitcommit: 7c93b6f93d2699d466b172590710ed01697bbdad
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74720237"
---
# <a name="content-inspection"></a>Inspeção de conteúdo

*Aplica-se ao: Microsoft Cloud App Security*

Ao habilitar a inspeção de conteúdo, você poderá escolher se deseja usar expressões predefinidas ou pesquisar outras expressões personalizadas.

É possível especificar uma expressão regular para excluir um arquivo dos resultados. Essa opção será muito útil se você tiver um padrão de palavra-chave de classificação interno que deseja excluir da política.

Você pode definir o número mínimo de violações de conteúdo que deseja corresponder antes de o arquivo ser considerado uma violação. Por exemplo, você poderá escolher 10 se quiser ser alertado sobre arquivos com pelo menos 10 números de cartão de crédito encontrados em seu conteúdo.

Quando o conteúdo é comparado com a expressão selecionada, o texto de violação é substituído por caracteres "X". Por padrão, as violações são mascaradas e mostradas em seu contexto, exibindo 100 caracteres antes e após a violação. Os números no contexto da expressão são substituídos por caracteres "#" e nunca são armazenados no Cloud App Security. Você pode selecionar a opção para **Remover a máscara dos últimos quatro caracteres de uma violação** para remover a máscara dos últimos quatro caracteres da própria violação. É necessário definir quais tipos de dados a expressão regular pesquisa: conteúdo, metadados e/ou nome do arquivo. Por padrão, ela pesquisa o conteúdo e os metadados.

## <a name="content-inspection-for-protected-files"></a>Inspeção de conteúdo para arquivos protegidos

O Cloud App Security permite que os administradores concedam permissão ao Cloud App Security para descriptografar arquivos criptografados e examinar o conteúdo quanto a violações.

Para dar as permissões necessárias ao Cloud App Security:

1. Acesse **Configurações** e, em seguida a **Proteção de Informações do Azure**.
2. Habilite **Inspecionar arquivos protegidos.**
3. Siga os prompts para permitir as permissões necessárias no Azure Active Directory.
4. Você pode definir as configurações de acordo com a política de arquivo para determinar quais políticas examinarão os arquivos protegidos.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]

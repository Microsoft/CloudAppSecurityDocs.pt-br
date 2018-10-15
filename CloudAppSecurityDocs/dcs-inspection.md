---
title: Como o Cloud App Security executa a inspeção de conteúdo usando o Serviço de Classificação de Dados da Microsoft | Microsoft Docs
description: Este artigo descreve o processo que o Microsoft Cloud App Security segue ao executar a inspeção de conteúdo DLP usando o Serviço de Classificação de Dados da Microsoft.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 9/21/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: bf25d1e6-e5dc-449f-b50e-1cd4a21b6d3d
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 46f948064bfea4aa921fd5b269f6576ec0f75d97
ms.sourcegitcommit: da651fb36d26d0dfe796b988e86205f41f7dc5de
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2018
ms.locfileid: "48251464"
---
*Aplica-se ao: Microsoft Cloud App Security*



# <a name="microsoft-data-classification-services-integration"></a>Integração dos Serviços de Classificação de Dados da Microsoft

O Microsoft Cloud App Security permite que você utilize de forma nativa o Serviço de Classificação de Dados da Microsoft, para classificar os arquivos em seus aplicativos de nuvem. O Serviço de Classificação de Dados da Microsoft fornece uma experiência unificada de proteção de informações no Office 365, na Proteção de Informações do Azure e no Microsoft Cloud App Security, e permite que você amplie seus esforços de classificação de dados para aplicativos de nuvem de terceiros protegidos pelo Microsoft Cloud App Security, aproveitando as decisões que você já tomou em um número ainda maior de aplicativos.

>[!NOTE]
> Atualmente, este recurso está disponível somente nos EUA e na Europa (exceto na França).

Nenhuma configuração adicional é necessária ao criar uma política de prevenção de perda de dados para seus arquivos no Microsoft Cloud App Security. Você automaticamente terá a opção de definir o **Método de inspeção** para usar o **Serviço de Classificação de Dados da Microsoft**.

![Configuração do serviço de classificação de dados](./media/dcs-enable.png)

Para habilitar a inspeção de conteúdo com os Serviços de Classificação de Dados:

1. Na página [Política de arquivo](data-protection-policies.md), em **Método de inspeção** selecione **Serviço de Classificação de Dados**.
2. Selecione se a política deve ser aplicada quando **qualquer** ou **todos** os critérios são atendidos.
3. Escolha o tipo de inspeção de conteúdo selecionando os tipos de informações confidenciais.
 ![Configuração do serviço de classificação de dados](./media/dcs-sensitive-information-type.png)

5. Você pode usar os [tipos de informações confidenciais padrão](https://support.office.com/article/what-the-sensitive-information-types-look-for-fd505979-76be-4d9f-b459-abef3fc9e86b), bem como os [tipos de informações confidenciais personalizados](https://support.office.com/article/create-a-custom-sensitive-information-type-82c382a5-b6db-44fd-995d-b333b3c7fc30) (que suportam padrões complexos com Regex, palavras-chave e dicionário grande) que você criou no Office 365 e os reutilizar para definir o que acontece com os arquivos protegidos pelo Microsoft Cloud App Security.

6. Como opção, você pode retirar a máscara dos últimos quatro caracteres de uma correspondência. Por padrão, as correspondências são mascaradas e mostradas em seu contexto, e incluem os 40 caracteres antes e após a correspondência. Se você ativar essa caixa de seleção, ela removerá a máscara dos últimos quatro caracteres da correspondência em si.

7. Você também pode definir alertas e ações de governança para a política. Para obter mais informações, confira [Políticas de arquivo](data-protection-policies.md) e [Ações de governança](governance-actions.md).

Definir essas políticas no Microsoft Cloud App Security permite que você amplie facilmente a força dos recursos de DLP do Office 365 para todos os seus outros aplicativos de nuvem sancionados e proteja os dados armazenados neles com o conjunto de ferramentas completo fornecido pelo Microsoft Cloud App Security, como a capacidade de [aplicar automaticamente os rótulos de classificação da Proteção de Informações do Azure](azip-integration.md) e a capacidade de controlar as permissões de compartilhamento.



## <a name="see-also"></a>Consulte Também  
[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)   

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
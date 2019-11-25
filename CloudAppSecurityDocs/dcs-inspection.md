---
title: Inspeção de conteúdo do Cloud App Security usando o Serviço de Classificação de Dados da Microsoft
description: Este artigo descreve o processo que o Microsoft Cloud App Security segue ao executar a inspeção de conteúdo DLP usando o Serviço de Classificação de Dados da Microsoft.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 7/30/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: bf25d1e6-e5dc-449f-b50e-1cd4a21b6d3d
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: c4e00f152fcb09f2133805157b85b2a930ad3aca
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2019
ms.locfileid: "74461331"
---
# <a name="microsoft-data-classification-services-integration"></a>Integração dos Serviços de Classificação de Dados da Microsoft

*Aplica-se ao: Microsoft Cloud App Security*

O Microsoft Cloud App Security permite que você use nativamente o Serviço de Classificação de Dados da Microsoft para classificar os arquivos em seus aplicativos na nuvem. O Serviço de Classificação de Dados da Microsoft fornece uma experiência de proteção de informações unificada no Office 365, na Proteção de Informações do Azure e no Microsoft Cloud App Security. O serviço de classificação permite que você estenda seus esforços de classificação de dados para os aplicativos de nuvem de terceiros protegidos pelo Microsoft Cloud App Security usando as decisões que você já tomou em um número ainda maior de aplicativos.

>[!NOTE]
> This feature is currently available in the US, Europe (except France), Australia, India, Canada, Japan, and APAC.

## <a name="enable-content-inspection-with-data-classification-services"></a>Habilitar inspeção de conteúdo com os Serviços de Classificação de Dados

Você tem a opção de definir o **Método de inspeção** para usar o **Serviço de Classificação de Dados da Microsoft** sem precisar fazer nenhuma configuração adicional. Essa opção é útil ao criar uma política de prevenção de vazamento de dados para seus arquivos no Microsoft Cloud App Security.

1. Na página [política de arquivo](data-protection-policies.md), em **Método de inspeção**, selecione **Serviço de Classificação de Dados**. You can also set the **Inspection method** in the [session policy](session-policy-aad.md) page with **Control file download (with DLP)** selected.
     ![Configuração do serviço de classificação de dados](./media/dcs-enable.png)
2. Selecione se a política deve ser aplicada quando **qualquer** ou **todos** os critérios são atendidos.
3. **Escolha o tipo de inspeção** selecionando os **Tipos de informações confidenciais**.
 ![Configuração do serviço de classificação de dados](./media/dcs-sensitive-information-type.png)

4. Você pode usar os [tipos de informações confidenciais padrão](https://support.office.com/article/what-the-sensitive-information-types-look-for-fd505979-76be-4d9f-b459-abef3fc9e86b) para definir o que acontece com arquivos protegidos pelo Microsoft Cloud App Security. Você também pode reutilizar qualquer um dos seus [tipos de informações confidenciais personalizadas do Office 365](https://support.office.com/article/create-a-custom-sensitive-information-type-82c382a5-b6db-44fd-995d-b333b3c7fc30).
    > [!NOTE]
    > You can configure your policy to use advanced classification types such as Fingerprints and Exact Data Match.

5. Como opção, você pode retirar a máscara dos últimos quatro caracteres de uma correspondência. Por padrão, as correspondências são mascaradas e mostradas em seu contexto, e incluem os 40 caracteres antes e após a correspondência. Se você ativar essa caixa de seleção, ela removerá a máscara dos últimos quatro caracteres da correspondência em si.

6. Leveraging file policies, you can also set alerts and governance actions for the policy. Para obter mais informações, confira [Políticas de arquivo](data-protection-policies.md) e [Ações de governança](governance-actions.md). Leveraging session policies, you can also monitor and control actions in real-time when a file matches a DCS type. For more information, see [session policy](session-policy-aad.md).

Definir essas políticas permite que você amplie facilmente a força dos recursos de DLP do Office 365 para todos os seus outros aplicativos de nuvem sancionados e proteja os dados armazenados neles com o conjunto de ferramentas completo fornecido pelo Microsoft Cloud App Security, como a capacidade de [aplicar automaticamente os rótulos de classificação da Proteção de Informações do Azure](azip-integration.md) e a capacidade de controlar as permissões de compartilhamento.

## <a name="next-steps"></a>Próximas etapas

[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
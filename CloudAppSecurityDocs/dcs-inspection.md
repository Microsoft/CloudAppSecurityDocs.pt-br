---
title: Inspeção de conteúdo do Cloud App Security usando o Serviço de Classificação de Dados da Microsoft
description: Este artigo descreve o processo que o Microsoft Cloud App Security segue ao executar a inspeção de conteúdo DLP usando o Serviço de Classificação de Dados da Microsoft.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 06/24/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 9d9032b0084a1c25290f8e067279f9ef7e66f8a6
ms.sourcegitcommit: c174a7ada5c6a14f0fea9870672898c54e5e3b52
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89150070"
---
# <a name="microsoft-data-classification-services-integration"></a>Integração dos Serviços de Classificação de Dados da Microsoft

*Aplica-se a: Microsoft Cloud App Security*

O Microsoft Cloud App Security permite que você use nativamente o Serviço de Classificação de Dados da Microsoft para classificar os arquivos em seus aplicativos na nuvem. O serviço de classificação de dados da Microsoft fornece uma experiência unificada de proteção de informações em Microsoft 365, proteção de informações do Azure e Microsoft Cloud App Security. O serviço de classificação permite que você estenda seus esforços de classificação de dados para os aplicativos de nuvem de terceiros protegidos pelo Microsoft Cloud App Security usando as decisões que você já tomou em um número ainda maior de aplicativos.

>[!NOTE]
> Esse recurso está disponível no momento nos EUA, Europa, Austrália, Índia, Canadá, Japão e na Austrália.

## <a name="enable-content-inspection-with-data-classification-services"></a>Habilitar inspeção de conteúdo com os Serviços de Classificação de Dados

Você tem a opção de definir o **Método de inspeção** para usar o **Serviço de Classificação de Dados da Microsoft** sem precisar fazer nenhuma configuração adicional. Essa opção é útil ao criar uma política de prevenção de vazamento de dados para seus arquivos no Microsoft Cloud App Security.

1. Na página [política de arquivo](data-protection-policies.md), em **Método de inspeção**, selecione **Serviço de Classificação de Dados**. Você também pode definir o **método de inspeção** na página [política de sessão](session-policy-aad.md) com o **download do arquivo de controle (com inspeção)** selecionado.

    ![Configuração do serviço de classificação de dados](media/dcs-enable.png)
2. Selecione se a política deve ser aplicada quando **qualquer** ou **todos** os critérios são atendidos.
3. **Escolha o tipo de inspeção** selecionando os **Tipos de informações confidenciais**.

    ![Escolher o tipo de inspeção do serviço de classificação de dados](media/dcs-sensitive-information-type.png)

4. Você pode usar os [tipos de informações confidenciais padrão](https://support.office.com/article/what-the-sensitive-information-types-look-for-fd505979-76be-4d9f-b459-abef3fc9e86b) para definir o que acontece com arquivos protegidos pelo Microsoft Cloud App Security. Você também pode reutilizar qualquer um dos seus [tipos de informações confidenciais personalizadas do Office 365](https://support.office.com/article/create-a-custom-sensitive-information-type-82c382a5-b6db-44fd-995d-b333b3c7fc30).
    > [!NOTE]
    > Você pode configurar sua política para usar tipos de classificação avançados, como [impressões digitais](/microsoft-365/compliance/document-fingerprinting?view=o365-worldwide), [correspondência exata de dados](/microsoft-365/compliance/create-custom-sensitive-information-types-with-exact-data-match-based-classification)e [classificadores treináveis](/microsoft-365/compliance/classifier-getting-started-with).

5. Como opção, você pode retirar a máscara dos últimos quatro caracteres de uma correspondência. Por padrão, as correspondências são mascaradas e mostradas em seu contexto, e incluem os 40 caracteres antes e após a correspondência. Se você ativar essa caixa de seleção, ela removerá a máscara dos últimos quatro caracteres da correspondência em si.

6. Aproveitando as políticas de arquivo, você também pode definir alertas e ações de governança para a política. Para obter mais informações, confira [Políticas de arquivo](data-protection-policies.md) e [Ações de governança](governance-actions.md). Aproveitando as políticas de sessão, você também pode monitorar e controlar ações em tempo real quando um arquivo corresponde a um tipo de DCS. Para obter mais informações, consulte [política de sessão](session-policy-aad.md).

Definir essas políticas permite que você estenda facilmente a força do Microsoft 365 recursos de DLP para todos os seus aplicativos de nuvem aprovados e proteja os dados armazenados neles com o conjunto de ferramentas completo fornecido a você por Microsoft Cloud App Security – como a capacidade de [aplicar automaticamente rótulos de classificação da proteção de informações do Azure](azip-integration.md) e a capacidade de controlar permissões de compartilhamento.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]

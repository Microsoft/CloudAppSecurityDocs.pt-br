---
title: Inspeção de conteúdo do Cloud App Security usando o Serviço de Classificação de Dados da Microsoft
description: Este artigo descreve o processo que o Microsoft Cloud App Security segue ao executar a inspeção de conteúdo DLP usando o Serviço de Classificação de Dados da Microsoft.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 04/16/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 353cff79b3e76c3f63380194ea055a92f13c0ce8
ms.sourcegitcommit: 826d2ec022647bce6c3135c115a41ee894ff8ecd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/16/2020
ms.locfileid: "84800768"
---
# <a name="microsoft-data-classification-services-integration"></a>Integração dos Serviços de Classificação de Dados da Microsoft

*Aplica-se a: Microsoft Cloud App Security*

O Microsoft Cloud App Security permite que você use nativamente o Serviço de Classificação de Dados da Microsoft para classificar os arquivos em seus aplicativos na nuvem. O Serviço de Classificação de Dados da Microsoft fornece uma experiência de proteção de informações unificada no Office 365, na Proteção de Informações do Azure e no Microsoft Cloud App Security. O serviço de classificação permite que você estenda seus esforços de classificação de dados para os aplicativos de nuvem de terceiros protegidos pelo Microsoft Cloud App Security usando as decisões que você já tomou em um número ainda maior de aplicativos.

>[!NOTE]
> Esse recurso está disponível no momento nos EUA, Europa, Austrália, Índia, Canadá, Japão e na Austrália.

## <a name="enable-content-inspection-with-data-classification-services"></a>Habilitar inspeção de conteúdo com os Serviços de Classificação de Dados

Você tem a opção de definir o **Método de inspeção** para usar o **Serviço de Classificação de Dados da Microsoft** sem precisar fazer nenhuma configuração adicional. Essa opção é útil ao criar uma política de prevenção de vazamento de dados para seus arquivos no Microsoft Cloud App Security.

1. Na página [política de arquivo](data-protection-policies.md), em **Método de inspeção**, selecione **Serviço de Classificação de Dados**. Você também pode definir o **método de inspeção** na página [política de sessão](session-policy-aad.md) com o **download do arquivo de controle (com inspeção)** selecionado.

    ![Configuração do serviço de classificação de dados](media/dcs-enable.png)
2. Selecione se a política deve ser aplicada quando **qualquer** ou **todos** os critérios são atendidos.
3. **Escolha o tipo de inspeção** selecionando os **Tipos de informações confidenciais**.

    ![Configuração do serviço de classificação de dados](media/dcs-sensitive-information-type.png)

4. Você pode usar os [tipos de informações confidenciais padrão](https://support.office.com/article/what-the-sensitive-information-types-look-for-fd505979-76be-4d9f-b459-abef3fc9e86b) para definir o que acontece com arquivos protegidos pelo Microsoft Cloud App Security. Você também pode reutilizar qualquer um dos seus [tipos de informações confidenciais personalizadas do Office 365](https://support.office.com/article/create-a-custom-sensitive-information-type-82c382a5-b6db-44fd-995d-b333b3c7fc30).
    > [!NOTE]
    > Você pode configurar sua política para usar tipos de classificação avançados, como as impressões digitais e a correspondência exata de dados.

5. Como opção, você pode retirar a máscara dos últimos quatro caracteres de uma correspondência. Por padrão, as correspondências são mascaradas e mostradas em seu contexto, e incluem os 40 caracteres antes e após a correspondência. Se você ativar essa caixa de seleção, ela removerá a máscara dos últimos quatro caracteres da correspondência em si.

6. Aproveitando as políticas de arquivo, você também pode definir alertas e ações de governança para a política. Para obter mais informações, confira [Políticas de arquivo](data-protection-policies.md) e [Ações de governança](governance-actions.md). Aproveitando as políticas de sessão, você também pode monitorar e controlar ações em tempo real quando um arquivo corresponde a um tipo de DCS. Para obter mais informações, consulte [política de sessão](session-policy-aad.md).

Definir essas políticas permite que você amplie facilmente a força dos recursos de DLP do Office 365 para todos os seus outros aplicativos de nuvem sancionados e proteja os dados armazenados neles com o conjunto de ferramentas completo fornecido pelo Microsoft Cloud App Security, como a capacidade de [aplicar automaticamente os rótulos de classificação da Proteção de Informações do Azure](azip-integration.md) e a capacidade de controlar as permissões de compartilhamento.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]

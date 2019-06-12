---
title: Inspeção de conteúdo do Cloud App Security usando o Serviço de Classificação de Dados da Microsoft
description: Este artigo descreve o processo que o Microsoft Cloud App Security segue ao executar a inspeção de conteúdo DLP usando o Serviço de Classificação de Dados da Microsoft.
keywords: ''
author: ShlomoSagir-MS
ms.author: ShlomoSagir-MS
manager: ShlomoSagir-MS
ms.date: 06/10/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: bf25d1e6-e5dc-449f-b50e-1cd4a21b6d3d
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 0424af7b50aea3bfe77ae0cb2fe1e7d66f6f1fde
ms.sourcegitcommit: a5b9089b381bcf8bb48031a5a9141e4e20955aaf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66830323"
---
# <a name="microsoft-data-classification-services-integration"></a>Integração dos Serviços de Classificação de Dados da Microsoft

*Aplica-se a: Microsoft Cloud App Security*

O Microsoft Cloud App Security permite que você use nativamente o Serviço de Classificação de Dados da Microsoft para classificar os arquivos em seus aplicativos na nuvem. O Serviço de Classificação de Dados da Microsoft fornece uma experiência de proteção de informações unificada no Office 365, na Proteção de Informações do Azure e no Microsoft Cloud App Security. O serviço de classificação permite que você estenda seus esforços de classificação de dados para os aplicativos de nuvem de terceiros protegidos pelo Microsoft Cloud App Security usando as decisões que você já tomou em um número ainda maior de aplicativos.

>[!NOTE]
> Esse recurso está atualmente disponível nos EUA, na Europa (exceto a França) e na Ásia-Pacífico.


## <a name="enable-content-inspection-with-data-classification-services"></a>Habilitar inspeção de conteúdo com os Serviços de Classificação de Dados

Você tem a opção de definir o **Método de inspeção** para usar o **Serviço de Classificação de Dados da Microsoft** sem precisar fazer nenhuma configuração adicional. Essa opção é útil ao criar uma política de prevenção de vazamento de dados para seus arquivos no Microsoft Cloud App Security.


1. Na página [política de arquivo](data-protection-policies.md), em **Método de inspeção**, selecione **Serviço de Classificação de Dados**. Você também pode definir a **método de inspeção** na [política de sessão](session-policy-aad.md) página com **download do arquivo de controle (com DLP)** selecionado.
     ![Configuração do serviço de classificação de dados](./media/dcs-enable.png)
2. Selecione se a política deve ser aplicada quando **qualquer** ou **todos** os critérios são atendidos.
3. **Escolha o tipo de inspeção** selecionando os **Tipos de informações confidenciais**.
 ![Configuração do serviço de classificação de dados](./media/dcs-sensitive-information-type.png)

4. Você pode usar os [tipos de informações confidenciais padrão](https://support.office.com/article/what-the-sensitive-information-types-look-for-fd505979-76be-4d9f-b459-abef3fc9e86b) para definir o que acontece com arquivos protegidos pelo Microsoft Cloud App Security. Você também pode reutilizar qualquer um dos seus [tipos de informações confidenciais personalizadas do Office 365](https://support.office.com/article/create-a-custom-sensitive-information-type-82c382a5-b6db-44fd-995d-b333b3c7fc30).

5. Como opção, você pode retirar a máscara dos últimos quatro caracteres de uma correspondência. Por padrão, as correspondências são mascaradas e mostradas em seu contexto, e incluem os 40 caracteres antes e após a correspondência. Se você ativar essa caixa de seleção, ela removerá a máscara dos últimos quatro caracteres da correspondência em si.

6. Utilizando políticas de arquivo, você também pode definir alertas e ações de governança da política. Para obter mais informações, confira [Políticas de arquivo](data-protection-policies.md) e [Ações de governança](governance-actions.md). Aproveitar as políticas de sessão, você também pode monitorar e controlar ações em tempo real quando um arquivo corresponde a um tipo de controladores de domínio. Para obter mais informações, consulte [política de sessão](session-policy-aad.md).

Definir essas políticas permite que você amplie facilmente a força dos recursos de DLP do Office 365 para todos os seus outros aplicativos de nuvem sancionados e proteja os dados armazenados neles com o conjunto de ferramentas completo fornecido pelo Microsoft Cloud App Security, como a capacidade de [aplicar automaticamente os rótulos de classificação da Proteção de Informações do Azure](azip-integration.md) e a capacidade de controlar as permissões de compartilhamento.



## <a name="next-steps"></a>Próximas etapas  
[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)   

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/)  
  

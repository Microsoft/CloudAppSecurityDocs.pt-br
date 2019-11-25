---
title: Integrate Azure Advanced Threat Protection with Cloud App Security
description: This article provides information about how to leverage Azure Advanced Threat Protection insights in Cloud App Security for hybrid risk detection.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 11/20/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 5636c6a0aa51d17847560a122248e625137840cb
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2019
ms.locfileid: "74460936"
---
# <a name="azure-advanced-threat-protection-integration"></a>Azure Advanced Threat Protection integration

*Aplica-se ao: Microsoft Cloud App Security*

Microsoft Cloud App Security integrates with Azure Advanced Threat Protection (Azure ATP) to provide user entity behavioral analytics (UEBA) across a hybrid environment - both cloud app and on-premises, for more information, see [Tutorial: Investigate risky users](tutorial-ueba.md) For more information about the machine learning and behavioral analytics provided by Azure ATP, see [What is Azure ATP?](https://docs.microsoft.com/azure-advanced-threat-protection/what-is-atp).

## <a name="prerequisites"></a>Pré-requisitos

Para fazer uma investigação completa em um ambiente híbrido, é necessário:

- Uma licença válida do ATP do Azure vinculada à instância do Azure Active Directory
- You must be a global admin to enable integration between Azure ATP and Microsoft Cloud App Security
- If do not have Azure ATP, try it now

>[!NOTE]
>If you don't have a subscription for Microsoft Cloud App Security, you will still be able to use the Cloud App Security portal to get Azure ATP insights.

## <a name="enable-azure-advanced-threat-protection"></a>Enable Azure Advanced Threat Protection

To enable Cloud App Security integration with Azure ATP:

1. In Cloud App Security, under the settings cog, select **Settings**.

   ![Settings menu](media/azip-system-settings.png)

1. Under **Threat Protection**, select **Azure ATP**.

    ![enable azure advanced threat protection](media/aatp-integration.png)

1. Select **Connect Azure ATP data including alerts and activities with Cloud App Security** and then click **Save**.

> [!NOTE]
> It may take up to 12 hours until the integration takes effect.

After enabling Azure Advanced Threat Protection integration, you'll be able to see on-premises activities for all the users in your organization. You will also get advanced insights on your users that combine alerts and suspicious activities across your cloud and on-premises environments.

## <a name="disable-azure-advanced-threat-protection"></a>Disable Azure Advanced Threat Protection

To disable Cloud App Security integration with Azure ATP:

1. In Cloud App Security, under the settings cog, select **Settings**.

1. Under **Threat Protection**, select **Azure ATP**.

1. Clear **Connect Azure ATP data including alerts and activities with Cloud App Security** and then click **Save**.

> [!NOTE]
> Existing azure ATP data is kept in accordance with Cloud App Security retention policies but the Identity Security Posture assessments are removed.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]

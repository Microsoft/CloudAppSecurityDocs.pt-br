---
title: Integre a proteção avançada contra ameaças do Azure com o Cloud App Security
description: Este artigo fornece informações sobre como aproveitar as ideias de proteção avançada contra ameaças do Azure no Cloud App Security para detecção de riscos híbridos.
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
# <a name="azure-advanced-threat-protection-integration"></a>Integração da proteção avançada contra ameaças do Azure

*Aplica-se ao: Microsoft Cloud App Security*

O Microsoft Cloud App Security integra-se com o Azure ATP (proteção avançada contra ameaças do Azure) para fornecer UEBA (análise comportamental de entidade de usuário) em um ambiente híbrido-ambos os aplicativos de nuvem e locais, para obter mais informações, consulte [tutorial: investigar usuários arriscados](tutorial-ueba.md) para obter mais informações sobre o aprendizado de máquina e análise comportamental fornecidos pelo Azure ATP, consulte [o que é o Azure ATP?](https://docs.microsoft.com/azure-advanced-threat-protection/what-is-atp).

## <a name="prerequisites"></a>Pré-requisitos

Para fazer uma investigação completa em um ambiente híbrido, é necessário:

- Uma licença válida do ATP do Azure vinculada à instância do Azure Active Directory
- Você deve ser um administrador global para habilitar a integração entre o Azure ATP e o Microsoft Cloud App Security
- Se não tiver o Azure ATP, experimente-o agora

>[!NOTE]
>Se você não tiver uma assinatura para Microsoft Cloud App Security, ainda poderá usar o portal de Cloud App Security para obter informações do Azure ATP.

## <a name="enable-azure-advanced-threat-protection"></a>Habilitar a proteção avançada contra ameaças do Azure

Para habilitar a integração de Cloud App Security com o Azure ATP:

1. Em Cloud App Security, na engrenagem configurações, selecione **configurações**.

   ![Menu configurações](media/azip-system-settings.png)

1. Em **proteção contra ameaças**, selecione **Azure ATP**.

    ![habilitar a proteção avançada contra ameaças do Azure](media/aatp-integration.png)

1. Selecione **conectar dados do Azure ATP, incluindo alertas e atividades com Cloud app Security** e, em seguida, clique em **salvar**.

> [!NOTE]
> Pode levar até 12 horas até que a integração entre em vigor.

Depois de habilitar a integração da proteção avançada contra ameaças do Azure, você poderá ver as atividades locais para todos os usuários em sua organização. Você também obterá informações avançadas sobre seus usuários que combinam alertas e atividades suspeitas em seus ambientes de nuvem e locais.

## <a name="disable-azure-advanced-threat-protection"></a>Desabilitar a proteção avançada contra ameaças do Azure

Para desabilitar a integração de Cloud App Security com o Azure ATP:

1. Em Cloud App Security, na engrenagem configurações, selecione **configurações**.

1. Em **proteção contra ameaças**, selecione **Azure ATP**.

1. Desmarque **conectar dados do Azure ATP, incluindo alertas e atividades com Cloud app Security** e, em seguida, clique em **salvar**.

> [!NOTE]
> Os dados existentes do Azure ATP são mantidos de acordo com as políticas de retenção de Cloud App Security, mas as avaliações de postura de segurança de identidade são removidas.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]

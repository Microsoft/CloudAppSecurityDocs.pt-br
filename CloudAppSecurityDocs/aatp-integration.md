---
title: Integre a proteção avançada contra ameaças do Azure com o Cloud App Security
description: Este artigo fornece informações sobre como aproveitar as ideias de proteção avançada contra ameaças do Azure no Cloud App Security para detecção de riscos híbridos.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/19/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: c38ccba7b6d9729ebdd80f005d9630270726d209
ms.sourcegitcommit: d493fc811a68387398615ff6288a300bb1f0fce7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75310405"
---
# <a name="azure-advanced-threat-protection-integration"></a>Integração da proteção avançada contra ameaças do Azure

*Aplica-se a: Microsoft Cloud app Security* o Git Microsoft Cloud app Security integra-se com o Azure ATP (proteção avançada contra ameaças do Azure) para fornecer Ueba (análise comportamental de entidade de usuário) em um ambiente híbrido – tanto no aplicativo de nuvem quanto no local, para obter mais informações, consulte [tutorial: investigar usuários arriscados](tutorial-ueba.md). Para obter mais informações sobre o aprendizado de máquina e análise comportamental fornecidos pelo Azure ATP, consulte [o que é o Azure ATP?](https://docs.microsoft.com/azure-advanced-threat-protection/what-is-atp)

## <a name="prerequisites"></a>Pré-requisitos

Para fazer uma investigação completa em um ambiente híbrido, é necessário:

- Uma licença válida do ATP do Azure vinculada à instância do Azure Active Directory
- Você deve ser um administrador global Azure Active Directory para habilitar a integração entre o Azure ATP e o Cloud App Security

> [!NOTE]
>
> - Se você não tiver uma assinatura para Microsoft Cloud App Security, ainda poderá usar Cloud App Security para obter insights do Azure ATP.
> - Os administradores do Azure ATP podem exigir novas permissões para acessar Cloud App Security. Para saber como atribuir permissões a Cloud App Security, consulte [gerenciar o acesso de administrador](manage-admins.md).

## <a name="enable-azure-atp"></a>Habilitar o Azure ATP

Para habilitar a integração de Cloud App Security com o Azure ATP:

1. Em Cloud App Security, na engrenagem configurações, selecione **configurações**.

    ![Menu configurações](media/azip-system-settings.png)

1. Em **proteção contra ameaças**, selecione **Azure ATP**.

    ![habilitar a proteção avançada contra ameaças do Azure](media/aatp-integration.png)

1. Selecione **conectar dados do Azure ATP, incluindo alertas e atividades com Cloud app Security** e, em seguida, clique em **salvar**.

> [!NOTE]
> Pode levar até 12 horas até que a integração entre em vigor.

Depois de habilitar a integração do Azure ATP, você poderá ver as atividades locais para todos os usuários em sua organização. Você também obterá informações avançadas sobre seus usuários que combinam alertas e atividades suspeitas em seus ambientes de nuvem e locais. Além disso, as políticas do Azure ATP aparecerão na página políticas de Cloud App Security. Para obter uma lista de políticas do Azure ATP, consulte [alertas de segurança](https://docs.microsoft.com/azure-advanced-threat-protection/suspicious-activity-guide).

## <a name="disable-azure-atp"></a>Desabilitar o Azure ATP

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

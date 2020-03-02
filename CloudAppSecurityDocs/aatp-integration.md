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
ms.openlocfilehash: 0605d54b8af24b2b060e96788349e2cfe45abaac
ms.sourcegitcommit: 661228206512c6c8dcb30fdce59b2c038cf2fe69
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/01/2020
ms.locfileid: "78204261"
---
# <a name="azure-advanced-threat-protection-integration"></a>Integração da proteção avançada contra ameaças do Azure

*Aplica-se a: Microsoft Cloud app Security* o Git Microsoft Cloud app Security integra-se com o Azure ATP (proteção avançada contra ameaças do Azure) para fornecer Ueba (análise comportamental de entidade de usuário) em um ambiente híbrido – tanto no aplicativo de nuvem quanto no local, para obter mais informações, consulte [tutorial: investigar usuários arriscados](tutorial-ueba.md). Para obter mais informações sobre o aprendizado de máquina e análise comportamental fornecidos pelo Azure ATP, consulte [o que é o Azure ATP?](https://docs.microsoft.com/azure-advanced-threat-protection/what-is-atp)

## <a name="prerequisites"></a>Prerequisites

Para fazer uma investigação completa em um ambiente híbrido, é necessário:

- Uma licença válida do ATP do Azure vinculada à instância do Azure Active Directory
- Você deve ser um administrador global Azure Active Directory para habilitar a integração entre o Azure ATP e o Cloud App Security

> [!NOTE]
>
> - Se você não tiver uma assinatura para Microsoft Cloud App Security, ainda poderá usar Cloud App Security para obter insights do Azure ATP.
> - Os administradores do ATP do Azure podem exigir novas permissões para acessar o Cloud App Security. Para saber como atribuir permissões ao Cloud App Security, confira [Gerenciar o acesso de administrador](manage-admins.md).

## <a name="enable-azure-atp"></a>Habilitar o Azure ATP

Para habilitar a integração de Cloud App Security com o Azure ATP:

1. Em Cloud App Security, na engrenagem configurações, selecione **configurações**.

    ![Menu configurações](media/azip-system-settings.png)

1. Em **proteção contra ameaças**, selecione **Azure ATP**.

    ![habilitar a proteção avançada contra ameaças do Azure](media/aatp-integration.png)

1. Selecione **habilitar a integração de dados do Azure ATP** e clique em **salvar**.

> [!NOTE]
> Pode levar até 12 horas até que a integração entre em vigor.

Depois de habilitar a integração do Azure ATP, você poderá ver as atividades locais para todos os usuários em sua organização. Você também obterá informações avançadas sobre seus usuários que combinam alertas e atividades suspeitas em seus ambientes de nuvem e locais. Além disso, as políticas do Azure ATP aparecerão na página políticas de Cloud App Security. Para obter uma lista de políticas do Azure ATP, consulte [alertas de segurança](https://docs.microsoft.com/azure-advanced-threat-protection/suspicious-activity-guide).

Você também deve usar os links de **configuração do Azure ATP** para definir as configurações do Azure ATP que são relevantes para Cloud app Security. Use as informações a seguir para saber mais sobre essas configurações:

- [Configurar sensores do Azure ATP](/azure-advanced-threat-protection/install-atp-step5)
- [Configurar contas de serviço de diretório](/azure-advanced-threat-protection/install-atp-step2)
- [Configurar a contabilização RADIUS para VPN](/azure-advanced-threat-protection/install-atp-step6-vpn)
- [Acessar o centro de integridade do Azure ATP](/azure-advanced-threat-protection/atp-health-center)

## <a name="disable-azure-atp"></a>Desabilitar o Azure ATP

Para desabilitar a integração de Cloud App Security com o Azure ATP:

1. Em Cloud App Security, na engrenagem configurações, selecione **configurações**.

1. Em **proteção contra ameaças**, selecione **Azure ATP**.

1. Desmarque **conectar dados do Azure ATP, incluindo alertas e atividades com Cloud app Security** e, em seguida, clique em **salvar**.

> [!NOTE]
> Quando a integração está desabilitada, os dados existentes do Azure ATP são mantidos de acordo com as políticas de retenção Cloud App Security, mas a seção de avaliações de segurança de identidade é removida.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]

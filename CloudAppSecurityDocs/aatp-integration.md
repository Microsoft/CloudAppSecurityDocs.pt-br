---
title: Integre a proteção avançada contra ameaças do Azure com o Cloud App Security
description: Este artigo fornece informações sobre como aproveitar as ideias de proteção avançada contra ameaças do Azure no Cloud App Security para detecção de riscos híbridos.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/24/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 5ed5d8c23a231d058b79c0d945a954a8afb6533d
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90880275"
---
# <a name="azure-advanced-threat-protection-integration"></a>Integração da proteção avançada contra ameaças do Azure

[!INCLUDE [Banner for top of topics](includes/banner.md)]

O Microsoft Cloud App Security integra-se com o Azure ATP (proteção avançada contra ameaças do Azure) para fornecer UEBA (análise comportamental de entidade de usuário) em um ambiente híbrido – tanto no aplicativo de nuvem quanto no local, para obter mais informações, consulte [tutorial: investigar usuários arriscados](tutorial-ueba.md). Para obter mais informações sobre o aprendizado de máquina e análise comportamental fornecidos pelo Azure ATP, consulte [o que é o Azure ATP?](/azure-advanced-threat-protection/what-is-atp)

## <a name="prerequisites"></a>Pré-requisitos

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

    ![Menu Configurações](media/azip-system-settings.png)

1. Em **proteção contra ameaças**, selecione **Azure ATP**.

    ![habilitar a proteção avançada contra ameaças do Azure](media/aatp-integration.png)

1. Selecione **habilitar a integração de dados do Azure ATP** e clique em **salvar**.

> [!NOTE]
> Pode levar até 12 horas até que a integração entre em vigor.

Depois de habilitar a integração do Azure ATP, você poderá ver as atividades locais para todos os usuários em sua organização. Você também obterá informações avançadas sobre seus usuários que combinam alertas e atividades suspeitas em seus ambientes de nuvem e locais. Além disso, as políticas do Azure ATP aparecerão na página políticas de Cloud App Security. Para obter uma lista de políticas do Azure ATP, consulte [alertas de segurança](/azure-advanced-threat-protection/suspicious-activity-guide).

Você também deve usar os links de **configuração do Azure ATP** para definir as configurações do Azure ATP que são relevantes para Cloud app Security. Use as informações a seguir para saber mais sobre essas configurações:

- [Configurar sensores do Azure ATP](/azure-advanced-threat-protection/install-atp-step5)
- [Configurar contas de serviço de diretório](/azure-advanced-threat-protection/install-atp-step2)
- [Configurar a contabilização RADIUS para VPN](/azure-advanced-threat-protection/install-atp-step6-vpn)
- [Acessar o centro de integridade do Azure ATP](/azure-advanced-threat-protection/atp-health-center)

## <a name="disable-azure-atp"></a>Desabilitar o Azure ATP

Para desabilitar a integração de Cloud App Security com o Azure ATP:

1. Em Cloud App Security, na engrenagem configurações, selecione **configurações**.

1. Em **proteção contra ameaças**, selecione **Azure ATP**.

1. Desmarque **habilitar a integração de dados do Azure ATP** e clique em **salvar**.

> [!NOTE]
> Quando a integração está desabilitada, os dados existentes do Azure ATP são mantidos de acordo com as políticas de retenção Cloud App Security, mas a seção de avaliações de segurança de identidade é removida.

## <a name="known-issues"></a>Problemas conhecidos

### <a name="missing-siem-alert-updates"></a>Atualizações de alerta do SIEM ausentes

Esse problema afeta os alertas que são disparados mais de uma vez. A primeira instância do alerta é enviada para o SIEM, mas os gatilhos subsequentes do mesmo alerta não são enviados.

#### <a name="resolution"></a>Resolução

Não há solução conhecida.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
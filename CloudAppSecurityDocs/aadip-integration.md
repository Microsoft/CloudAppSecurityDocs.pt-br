---
title: Integrar Azure Active Directory Identity Protection com Cloud App Security
description: Este artigo fornece informações sobre como aproveitar os alertas de proteção de identidade no Cloud App Security para detecção de riscos híbridos.
ms.date: 12/27/2020
ms.topic: how-to
ms.openlocfilehash: f71e73dfd3ca8be7d6ed5e03847ac6e11e290818
ms.sourcegitcommit: 4900168878f42e9fa79873df4b7c2d81991b5b27
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/04/2021
ms.locfileid: "97857947"
---
# <a name="azure-active-directory-identity-protection-integration"></a>Integração do Azure Active Directory Identity Protection

[!INCLUDE [Banner for top of topics](includes/banner.md)]

O Microsoft Cloud App Security integra-se com o Azure Active Directory Identity Protection (proteção de identidade) para fornecer UEBA (análise comportamental de entidade de usuário) em um ambiente híbrido. Para obter mais informações sobre o aprendizado de máquina e análise comportamental fornecidos pela proteção de identidade, consulte [o que é a proteção de identidade?](/azure/active-directory/identity-protection/overview-identity-protection).

## <a name="prerequisites"></a>Pré-requisitos

- Uma conta de administrador Cloud App Security para habilitar a integração entre o Identity Protection e o Cloud App Security.

## <a name="enable-identity-protection"></a>Habilitar o Identity Protection

> [!NOTE]
> O recurso de proteção de identidade é habilitado por padrão. No entanto, se o recurso foi desabilitado, você pode usar estas etapas para habilitá-lo.

Para habilitar a integração de Cloud App Security com a proteção de identidade:

1. Em Cloud App Security, na engrenagem configurações, selecione **configurações**.

    ![Menu Configurações](media/azip-system-settings.png)

1. Em **proteção contra ameaças**, selecione **Azure ad Identity Protection**.

    ![habilitar a proteção avançada contra ameaças do Azure](media/aadip-integration.png)

1. Selecione **habilitar Azure ad Identity Protection integração de alertas** e clique em **salvar**.

Depois de habilitar a integração de proteção de identidade, você poderá ver alertas para todos os usuários em sua organização.

## <a name="disable-identity-protection"></a>Desabilitar a proteção de identidade

Para desabilitar a integração de Cloud App Security com a proteção de identidade:

1. Em Cloud App Security, na engrenagem configurações, selecione **configurações**.

1. Em **proteção contra ameaças**, selecione **Azure ad Identity Protection**.

1. Desmarque **habilitar Azure ad Identity Protection integração de alertas** e clique em **salvar**.

> [!NOTE]
>
> - Quando a integração está desabilitada, os alertas existentes de proteção de identidade são mantidos de acordo com as políticas de retenção de Cloud App Security.
> - Como Cloud App Security consome apenas logons interativos do Azure AD, alguns alertas podem não mostrar atividades relacionadas. Você pode investigar essas atividades no portal do Azure AD.

## <a name="configure-identity-protection-policies"></a>Configurar políticas de proteção de identidade

As políticas de proteção de identidade podem ser ajustadas para a necessidade da sua organização usando o controle deslizante de severidade. O controle deslizante sensibilidade permite controlar quais alertas são ingeridos. Dessa forma, você pode adaptar a detecção de acordo com suas necessidades de cobertura e seus destinos (SNR).

As seguintes políticas estão disponíveis:

|Política|Descrição|Estado padrão|Gravidade padrão|
|---|---|---|---|
|Credenciais vazadas|Mostra alertas de credenciais vazadas, as credenciais válidas do usuário foram vazadas|habilitado|Todos os alertas de recebimento baixo|
|Entrada arriscada|Agrega várias detecções de entrada arriscadas, entradas que não foram executadas pelo usuário|habilitado|Alto-receber alertas de alta severidade|

> [!NOTE]
> Cloud App Security não envia notificações por email para alertas de proteção de identidade. No entanto, você pode configurar notificações por email para eles no portal de proteção de identidade.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]

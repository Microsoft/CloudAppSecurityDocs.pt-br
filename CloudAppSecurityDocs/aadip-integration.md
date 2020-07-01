---
title: Integrar Azure Active Directory Identity Protection com Cloud App Security
description: Este artigo fornece informações sobre como aproveitar os alertas de proteção de identidade no Cloud App Security para detecção de riscos híbridos.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 06/28/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 5af7efa448e7d93902e9d8845dd97479b7c53df7
ms.sourcegitcommit: b15034dd50142afd8e95de22a9232f711b1eae6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85624385"
---
# <a name="azure-active-directory-identity-protection-integration"></a>Integração do Azure Active Directory Identity Protection

*Aplica-se a: Microsoft Cloud App Security*

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
> Quando a integração está desabilitada, os alertas existentes de proteção de identidade são mantidos de acordo com as políticas de retenção de Cloud App Security.

## <a name="configure-identity-protection-policies"></a>Configurar políticas de proteção de identidade

As políticas de proteção de identidade podem ser ajustadas para a necessidade da sua organização usando o controle deslizante de severidade. O controle deslizante sensibilidade permite controlar quais alertas são ingeridos. Dessa forma, você pode adaptar a detecção de acordo com suas necessidades de cobertura e seus destinos (SNR).

As seguintes políticas estão disponíveis:

|Política|Descrição|Estado padrão|Gravidade padrão|
|---|---|---|---|
|Credenciais vazadas|Mostra alertas de credenciais vazadas, as credenciais válidas do usuário foram vazadas|habilitado|Todos os alertas de recebimento baixo|
|Entrada arriscada|Agrega várias detecções de entrada arriscadas, entradas que não foram executadas pelo usuário|habilitado|Alto-receber alertas de alta severidade|

## <a name="remediating-risky-users"></a>Corrigindo usuários arriscados

As políticas de proteção de identidade podem ser usadas para corrigir automaticamente os usuários arriscados definindo o nível de risco do usuário como alto. Quando um usuário é definido como alto, o algoritmo avançado de análise de risco do usuário leva em consideração o novo status do usuário, bem como o status de *Gerenciamento do dispositivo do computador* . Isso faz com que as ações de política relevantes definidas no Azure AD sejam impostas, como redefinir a senha do usuário, exigir autenticação MFA ou forçar o usuário a usar um dispositivo gerenciado. Para obter mais informações, consulte [como o AD do Azure usa meus comentários de risco](https://docs.microsoft.com/azure/active-directory/identity-protection/howto-identity-protection-risk-feedback#how-does-azure-ad-use-my-risk-feedback) e [ações de governança](accounts.md#governance-actions).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]

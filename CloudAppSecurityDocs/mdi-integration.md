---
title: Integre o Microsoft defender para identidade com o Cloud App Security
description: Este artigo fornece informações sobre como aproveitar o Microsoft defender para informações de identidade no Cloud App Security para detecção de riscos híbridos.
ms.date: 11/08/2020
ms.topic: how-to
ms.openlocfilehash: 260effd5750af75e8ca5bc58d566c6cbb95b1cd3
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96315099"
---
# <a name="microsoft-defender-for-identity-integration"></a>Integração do Microsoft Defender para Identidade

[!INCLUDE [Banner for top of topics](includes/banner.md)]

O Microsoft Cloud App Security integra-se com o Microsoft defender for Identity para fornecer UEBA (análise comportamental de entidade de usuário) em um ambiente híbrido – tanto no aplicativo de nuvem quanto no local, para obter mais informações, consulte [tutorial: investigar usuários arriscados](tutorial-ueba.md). Para obter mais informações sobre o aprendizado de máquina e análise comportamental fornecidos pelo defender for Identity, consulte [o que é o defender for Identity?](/defender-for-identity/what-is)

## <a name="prerequisites"></a>Pré-requisitos

Para fazer uma investigação completa em um ambiente híbrido, é necessário:

- Uma licença válida para o Microsoft defender para identidade conectada à sua instância do Active Directory
- Você deve ser um administrador global Azure Active Directory para habilitar a integração entre o defender para identidade e Cloud App Security

> [!NOTE]
>
> - Se você não tiver uma assinatura para Microsoft Cloud App Security, ainda poderá usar Cloud App Security para obter o defender para obter informações de identidade.
> - Os administradores do defender for Identity podem exigir novas permissões para acessar Cloud App Security. Para saber como atribuir permissões ao Cloud App Security, confira [Gerenciar o acesso de administrador](manage-admins.md).

## <a name="enable-defender-for-identity"></a>Habilitar defender para identidade

Para habilitar a integração de Cloud App Security com o defender para identidade:

1. Em Cloud App Security, na engrenagem configurações, selecione **configurações**.

    ![Menu Configurações](media/azip-system-settings.png)

1. Em **proteção contra ameaças**, selecione **Microsoft defender para identidade**.

    ![habilitar a proteção avançada contra ameaças do Azure](media/mdi-integration.png)

1. Selecione **habilitar Microsoft defender para integração de dados de identidade** e clique em **salvar**.

> [!NOTE]
> Pode levar até 12 horas até que a integração entre em vigor.

Depois de habilitar o defender para integração de identidade, você poderá ver as atividades locais para todos os usuários em sua organização. Você também obterá informações avançadas sobre seus usuários que combinam alertas e atividades suspeitas em seus ambientes de nuvem e locais. Além disso, as políticas do defender para identidade aparecerão na página políticas de Cloud App Security. Para obter uma lista de políticas do defender for Identity, consulte [alertas de segurança](/defender-for-identity/suspicious-activity-guide). Para editar essas políticas, consulte [excluindo entidades de detecções](/defender-for-identity/excluding-entities-from-detections).

Você também deve usar os links de **configuração do defender for Identity** para configurar o defender para configurações de identidade que são relevantes para Cloud app Security. Use as informações a seguir para saber mais sobre essas configurações:

- [Configurar o Microsoft defender para sensores de identidade](/defender-for-identity/install-step5)
- [Configurar contas de serviço de diretório](/defender-for-identity/install-step2)
- [Configurar a contabilização RADIUS para VPN](/defender-for-identity/install-step6-vpn)
- [Acessar o Microsoft defender para o centro de integridade de identidade](/defender-for-identity/health-center)

## <a name="disable-defender-for-identity"></a>Desabilitar defender para identidade

Para desabilitar a integração de Cloud App Security com o defender para identidade:

1. Em Cloud App Security, na engrenagem configurações, selecione **configurações**.

1. Em **proteção contra ameaças**, selecione **Microsoft defender para identidade**.

1. Desmarque **habilitar Microsoft defender para integração de dados de identidade** e clique em **salvar**.

> [!NOTE]
> Quando a integração é desabilitada, os dados existentes do defender for Identity são mantidos de acordo com Cloud App Security políticas de retenção, mas a seção de avaliações de segurança de identidade é removida.

## <a name="known-issues"></a>Problemas conhecidos

### <a name="missing-siem-alert-updates"></a>Atualizações de alerta do SIEM ausentes

Esse problema afeta os alertas que são disparados mais de uma vez. A primeira instância do alerta é enviada para o SIEM, mas os gatilhos subsequentes do mesmo alerta não são enviados.

#### <a name="resolution"></a>Resolução

Não há solução conhecida.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
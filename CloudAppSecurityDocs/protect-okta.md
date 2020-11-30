---
title: Como Cloud App Security ajuda a proteger seu ambiente Okta
description: Este artigo fornece informações sobre os benefícios de conectar seu aplicativo Okta para Cloud App Security usando o conector de API para visibilidade e controle sobre o uso.
ms.date: 12/04/2019
ms.topic: article
ms.openlocfilehash: aac67b4c39f95ffea36ac20a4cd0c10abb0054c3
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96315201"
---
# <a name="how-cloud-app-security-helps-protect-your-okta-environment"></a>Como Cloud App Security ajuda a proteger seu ambiente Okta

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Como uma solução de gerenciamento de acesso e identidade, o Okta mantém as chaves para as organizações que a maioria dos serviços críticos para os negócios. O Okta gerencia os processos de autenticação e autorização para seus usuários e clientes. Qualquer abuso de Okta por um ator mal-intencionado ou qualquer erro humano pode expor seus ativos e serviços mais críticos a ataques potenciais.

A conexão do Okta ao Cloud App Security oferece informações aprimoradas sobre suas atividades de administração do Okta, usuários gerenciados e entrars do cliente e fornece detecção de ameaças para comportamento anormal.

## <a name="main-threats"></a>Principais ameaças

- Contas comprometidas e ameaças internas

## <a name="how-cloud-app-security-helps-to-protect-your-environment"></a>Como Cloud App Security ajuda a proteger seu ambiente

- [Detecte ameaças à nuvem, contas comprometidas e pessoas mal-intencionadas](best-practices.md#detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware)
- [Usar a trilha de auditoria das atividades para investigações forenses](best-practices.md#use-the-audit-trail-of-activities-for-forensic-investigations)

## <a name="control-okta-with-built-in-policies-and-policy-templates"></a>Controlar o Okta com políticas internas e modelos de política

Você pode usar os seguintes modelos de política interna para detectar e notificá-lo sobre possíveis ameaças:

| Type | Nome |
| ---- | ---- |
| Política de detecção de anomalias interna | [Atividade de endereços IP anônimos](anomaly-detection-policy.md#activity-from-anonymous-ip-addresses)<br />[Atividade de país não frequente](anomaly-detection-policy.md#activity-from-infrequent-country)<br />[Atividade de endereços IP suspeitos](anomaly-detection-policy.md#activity-from-suspicious-ip-addresses)<br />[Viagem impossível](anomaly-detection-policy.md#impossible-travel)<br />[Várias tentativas de logon com falha](anomaly-detection-policy.md#multiple-failed-login-attempts)<br />[Detecção de ransomware](anomaly-detection-policy.md#ransomware-activity)<br />[Atividade administrativas incomuns](anomaly-detection-policy.md#unusual-activities-by-user) |
| Modelo de política de atividade | Logon de um endereço IP com risco |

Para obter mais informações sobre como criar políticas, consulte [criar uma política](control-cloud-apps-with-policies.md#create-a-policy).

## <a name="automate-governance-controls"></a>Automatizar controles de governança

No momento, não existem controles de governança disponíveis para Okta. Se você estiver interessado em ter ações de governança para esse conector, poderá [enviar os comentários da equipe de Cloud app Security](support-and-ts.md#feedback) com detalhes das ações desejadas.

Para obter mais informações sobre como corrigir ameaças de aplicativos, consulte [governando aplicativos conectados](governance-actions.md).

## <a name="protect-okta-in-real-time"></a>Proteger Okta em tempo real

Examine nossas práticas recomendadas para [proteger e colaborar com usuários externos](best-practices.md#secure-collaboration-with-external-users-by-enforcing-real-time-session-controls) e [bloquear e proteger o download de dados confidenciais para dispositivos não gerenciados ou arriscados](best-practices.md#block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Como conectar o Okta ao Microsoft Cloud App Security](connect-okta-to-microsoft-cloud-app-security.md)

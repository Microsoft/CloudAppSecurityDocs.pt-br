---
title: Como Cloud App Security ajuda a proteger seu ambiente workday
description: Este artigo fornece informações sobre os benefícios de conectar seu aplicativo do WORKDAY para Cloud App Security usando o conector de API para visibilidade e controle sobre o uso.
author: shsagir
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: article
ms.date: 12/04/2019
ms.collection: M365-security-compliance
ms.openlocfilehash: 9ee405188d0f338bfe43ca9a08730baa6054a844
ms.sourcegitcommit: 582779b75be41e57fb1d773d1cf01f6b8598521e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78274638"
---
# <a name="how-cloud-app-security-helps-protect-your-workday-environment"></a>Como Cloud App Security ajuda a proteger seu ambiente workday

*Aplica-se a: Microsoft Cloud App Security*

Como uma solução HCM principal, o workday mantém algumas das informações mais confidenciais em sua organização, como dados pessoais de funcionários, contratos, detalhes de fornecedores e muito mais. Impedir a exposição desses dados exige monitoramento contínuo para impedir que quaisquer atores maliciosos ou pessoas sem reconhecimento de segurança invasão as informações confidenciais.

Conectar o workday ao Cloud App Security oferece informações aprimoradas sobre as atividades dos usuários e fornece detecção de ameaças para comportamento anormal.

## <a name="main-threats"></a>Principais ameaças

- Contas comprometidas e ameaças internas
- Vazamento de dados
- Reconhecimento de segurança insuficiente
- BYOD (Traga seu próprio dispositivo) não gerenciado

## <a name="how-cloud-app-security-helps-to-protect-your-environment"></a>Como Cloud App Security ajuda a proteger seu ambiente

- [Detecte ameaças à nuvem, contas comprometidas e pessoas mal-intencionadas](best-practices.md#detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware)
- [Use a trilha de auditoria das atividades para investigações forenses](best-practices.md#use-the-audit-trail-of-activities-for-forensic-investigations)

## <a name="control-workday-with-built-in-policies-and-policy-templates"></a>Controlar o workday com políticas internas e modelos de política

Você pode usar os seguintes modelos de política interna para detectar e notificá-lo sobre possíveis ameaças:

| Digite | Name |
| ---- | ---- |
| Política de detecção de anomalias interna | [Atividade de endereços IP anônimos](anomaly-detection-policy.md#activity-from-anonymous-ip-addresses)<br />[Atividade de um país infrequente](anomaly-detection-policy.md#activity-from-infrequent-country)<br />[Atividade de endereços IP suspeitos](anomaly-detection-policy.md#activity-from-suspicious-ip-addresses)<br />[Viagem impossível](anomaly-detection-policy.md#impossible-travel) |
| Modelo de política de atividade | Logon de um endereço IP arriscado |

Para obter mais informações sobre como criar políticas, consulte [criar uma política](control-cloud-apps-with-policies.md#create-a-policy).

## <a name="automate-governance-controls"></a>Automatizar controles de governança

No momento, não existem controles de governança disponíveis para o workday. Se você estiver interessado em ter ações de governança para esse conector, poderá [enviar os comentários da equipe de Cloud app Security](support-and-ts.md#feedback) com detalhes das ações desejadas.

Para obter mais informações sobre como corrigir ameaças de aplicativos, consulte [governando aplicativos conectados](governance-actions.md).

## <a name="protect-workday-in-real-time"></a>Proteger o workday em tempo real

Examine nossas práticas recomendadas para [proteger e colaborar com usuários externos](best-practices.md#secure-collaboration-with-external-users-by-enforcing-real-time-session-controls) e [bloquear e proteger o download de dados confidenciais para dispositivos não gerenciados ou arriscados](best-practices.md#block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Como conectar o workday ao Microsoft Cloud App Security](connect-workday-to-microsoft-cloud-app-security.md)

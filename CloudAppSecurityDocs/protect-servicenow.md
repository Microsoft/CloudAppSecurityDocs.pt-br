---
title: Como Cloud App Security ajuda a proteger seu ambiente do ServiceNow
description: Este artigo fornece informações sobre os benefícios de conectar seu aplicativo ServiceNow para Cloud App Security usando o conector de API para visibilidade e controle sobre o uso.
author: shsagir
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: article
ms.date: 12/04/2019
ms.collection: M365-security-compliance
ms.openlocfilehash: 7a8838ed08b6ffdc3949234204a957f2a28a0eeb
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90880424"
---
# <a name="how-cloud-app-security-helps-protect-your-servicenow-environment"></a>Como Cloud App Security ajuda a proteger seu ambiente do ServiceNow

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Como um provedor de nuvem principal do CRM, o ServiceNow incorpora grandes quantidades de informações confidenciais sobre clientes, processos internos, incidentes e relatórios dentro de sua organização. Sendo um aplicativo essencial para os negócios, o ServiceNow é acessado e usado por pessoas dentro da sua organização e por outras pessoas fora dele (como parceiros e prestadores de trabalho) para várias finalidades. Em muitos casos, uma grande proporção de seus usuários acessando o ServiceNow tem baixo reconhecimento de segurança e pode colocar suas informações confidenciais em risco ao compartilhá-lo involuntariamente. Em outras instâncias, os atores mal-intencionados podem obter acesso aos seus ativos mais confidenciais relacionados ao cliente.

Conectar o ServiceNow ao Cloud App Security oferece informações aprimoradas sobre as atividades dos usuários, fornece detecção de ameaças usando detecções de anomalias baseadas em aprendizado de máquina e detecções de proteção de informações, como identificar quando informações confidenciais do cliente são carregadas na nuvem do ServiceNow.

## <a name="main-threats"></a>Principais ameaças

- Contas comprometidas e ameaças internas
- Vazamento de dados
- Reconhecimento de segurança insuficiente
- Ransomware
- BYOD (Traga seu próprio dispositivo) não gerenciado

## <a name="how-cloud-app-security-helps-to-protect-your-environment"></a>Como Cloud App Security ajuda a proteger seu ambiente

- [Detecte ameaças à nuvem, contas comprometidas e pessoas mal-intencionadas](best-practices.md#detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware)
- [Descobrir, classificar, rotular e proteger dados regulamentados e confidenciais armazenados na nuvem](best-practices.md#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)
- [Impor políticas de conformidade e DLP (proteção contra perda de dados) para dados armazenados na nuvem](best-practices.md#enforce-dlp-and-compliance-policies-for-data-stored-in-the-cloud)
- [Limitar a exposição de dados compartilhados e impor políticas de colaboração](best-practices.md#limit-exposure-of-shared-data-and-enforce-collaboration-policies)
- [Usar a trilha de auditoria das atividades para investigações forenses](best-practices.md#use-the-audit-trail-of-activities-for-forensic-investigations)

## <a name="control-servicenow-with-built-in-policies-and-policy-templates"></a>Controle o ServiceNow com políticas internas e modelos de política

Você pode usar os seguintes modelos de política interna para detectar e notificá-lo sobre possíveis ameaças:

| Tipo | Nome |
| ---- | ---- |
| Política de detecção de anomalias interna | [Atividade de endereços IP anônimos](anomaly-detection-policy.md#activity-from-anonymous-ip-addresses)<br />[Atividade de país não frequente](anomaly-detection-policy.md#activity-from-infrequent-country)<br />[Atividade de endereços IP suspeitos](anomaly-detection-policy.md#activity-from-suspicious-ip-addresses)<br />[Viagem impossível](anomaly-detection-policy.md#impossible-travel)<br />[Atividade executada pelo usuário encerrado](anomaly-detection-policy.md#activity-performed-by-terminated-user) (requer o AAD como IDP)<br />[Várias tentativas de logon com falha](anomaly-detection-policy.md#multiple-failed-login-attempts)<br />[Detecção de ransomware](anomaly-detection-policy.md#ransomware-activity)<br />[Atividades incomuns de download de vários arquivos](anomaly-detection-policy.md#unusual-activities-by-user) |
| Modelo de política de atividade | Logon de um endereço IP com risco<br />Download em massa por um único usuário<br />Atividade de ransomware potencial |
| Modelo de política de arquivo | Detectar um arquivo compartilhado com um domínio não autorizado<br />Detectar um arquivo compartilhado com endereços de email pessoais<br />Detectar arquivos com PII/PCI/PHI |

Para obter mais informações sobre como criar políticas, consulte [criar uma política](control-cloud-apps-with-policies.md#create-a-policy).

## <a name="automate-governance-controls"></a>Automatizar controles de governança

Além de monitorar possíveis ameaças, você pode aplicar e automatizar as seguintes ações de governança do ServiceNow para corrigir ameaças detectadas:

| Tipo | Ação |
| ---- | ---- |
| Governança de usuário | -Notificar o usuário sobre o alerta (por meio do Azure AD)<br />-Exigir que o usuário entre novamente (por meio do Azure AD)<br />– Suspender usuário (por meio do Azure AD) |

Para obter mais informações sobre como corrigir ameaças de aplicativos, consulte [governando aplicativos conectados](governance-actions.md).

## <a name="protect-servicenow-in-real-time"></a>Proteger o ServiceNow em tempo real

Examine nossas práticas recomendadas para [proteger e colaborar com usuários externos](best-practices.md#secure-collaboration-with-external-users-by-enforcing-real-time-session-controls) e [bloquear e proteger o download de dados confidenciais para dispositivos não gerenciados ou arriscados](best-practices.md#block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Como conectar o ServiceNow ao Microsoft Cloud App Security](connect-servicenow-to-microsoft-cloud-app-security.md)

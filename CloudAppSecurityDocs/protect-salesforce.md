---
title: Como Cloud App Security ajuda a proteger seu ambiente do Salesforce
description: Este artigo fornece informações sobre os benefícios de conectar seu aplicativo Salesforce para Cloud App Security usando o conector de API para visibilidade e controle sobre o uso.
author: shsagir
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: article
ms.date: 12/04/2019
ms.collection: M365-security-compliance
ms.openlocfilehash: 3f3aef39e134e34c46bc97a559bc3c19d4434f84
ms.sourcegitcommit: 6e266262b9b54e991acb8230a04e865628820557
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77495696"
---
# <a name="how-cloud-app-security-helps-protect-your-salesforce-environment"></a>Como Cloud App Security ajuda a proteger seu ambiente do Salesforce

*Aplica-se a: Microsoft Cloud App Security*

Como um grande provedor de nuvem do CRM, o Salesforce incorpora grandes quantidades de informações confidenciais sobre clientes, guias de preços e principais negócios de sua organização. Sendo um aplicativo essencial para os negócios, o Salesforce é acessado e usado por pessoas dentro da sua organização e por outras pessoas fora dele (como parceiros e prestadores de trabalho) para várias finalidades. Em muitos casos, uma grande proporção de seus usuários acessando o Salesforce tem baixa conscientização da segurança e pode colocar suas informações confidenciais em risco ao compartilhá-lo involuntariamente. Em outras instâncias, os atores mal-intencionados podem obter acesso aos seus ativos mais confidenciais relacionados ao cliente.

Conectar o Salesforce ao Cloud App Security oferece informações aprimoradas sobre as atividades dos usuários, fornece detecção de ameaças usando detecções de anomalias baseadas em Machine Learning e detecções de proteção de informações (como a detecção de informações externas) compartilhamento), habilita controles de atualização automatizados e detecta ameaças de aplicativos de terceiros habilitados em sua organização.

## <a name="main-threats"></a>Principais ameaças

- Contas comprometidas e ameaças internas
- Vazamento de dados
- Privilégios elevados
- Reconhecimento de segurança insuficiente
- Aplicativos de terceiros mal-intencionados e Complementos do Google
- Ransomware
- BYOD (Traga seu próprio dispositivo) não gerenciado

## <a name="how-cloud-app-security-helps-to-protect-your-environment"></a>Como Cloud App Security ajuda a proteger seu ambiente

- [Detecte ameaças à nuvem, contas comprometidas e pessoas mal-intencionadas](best-practices.md#detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware)
- [Descobrir, classificar, rotular e proteger dados regulamentados e confidenciais armazenados na nuvem](best-practices.md#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)
- [Descobrir e gerenciar aplicativos OAuth que têm acesso ao seu ambiente](manage-app-permissions.md)
- [Impor políticas de conformidade e DLP para dados armazenados na nuvem](best-practices.md#enforce-dlp-and-compliance-policies-for-data-stored-in-the-cloud)
- [Limitar a exposição de dados compartilhados e impor políticas de colaboração](best-practices.md#limit-exposure-of-shared-data-and-enforce-collaboration-policies)
- [Use a trilha de auditoria das atividades para investigações forenses](best-practices.md#use-the-audit-trail-of-activities-for-forensic-investigations)

## <a name="control-salesforce-with-built-in-policies-and-policy-templates"></a>Controle o Salesforce com políticas internas e modelos de política

Você pode usar os seguintes modelos de política interna para detectar e notificá-lo sobre possíveis ameaças:

| Tipo | {1&gt;Nome&lt;1} |
| ---- | ---- |
| Política de detecção de anomalias interna | [Atividade de endereços IP anônimos](anomaly-detection-policy.md#activity-from-anonymous-ip-addresses)<br />[Atividade de um país infrequente](anomaly-detection-policy.md#activity-from-infrequent-country)<br />[Atividade de endereços IP suspeitos](anomaly-detection-policy.md#activity-from-suspicious-ip-addresses)<br />[Viagem impossível](anomaly-detection-policy.md#impossible-travel)<br />[Atividade executada pelo usuário encerrado](anomaly-detection-policy.md#activity-performed-by-terminated-user) (requer o AAD como IDP)<br />[Várias tentativas de logon com falha](anomaly-detection-policy.md#multiple-failed-login-attempts)<br />[Detecção de ransomware](anomaly-detection-policy.md#ransomware-activity)<br />[Atividades administrativas incomuns](anomaly-detection-policy.md#unusual-activities-by-user)<br />[Atividades de exclusão de arquivo incomum](anomaly-detection-policy.md#unusual-activities-by-user)<br />[Atividades de compartilhamento de arquivos incomum](anomaly-detection-policy.md#unusual-activities-by-user)<br />[Atividades representadas incomuns](anomaly-detection-policy.md#unusual-activities-by-user)<br />[Atividades de download de vários arquivos incomuns](anomaly-detection-policy.md#unusual-activities-by-user) |
| Modelo de política de atividade | Logon de um endereço IP arriscado<br />Download em massa por um único usuário<br />Atividade de ransomware potencial |
| Modelo de política de arquivo | Detectar um arquivo compartilhado com um domínio não autorizado<br />Detectar um arquivo compartilhado com endereços de email pessoais<br />Detectar arquivos com PII/PCI/PHI |

Para obter mais informações sobre como criar políticas, consulte [criar uma política](control-cloud-apps-with-policies.md#create-a-policy).

## <a name="automate-governance-controls"></a>Automatizar controles de governança

Além de monitorar possíveis ameaças, você pode aplicar e automatizar as seguintes ações de governança do Salesforce para corrigir ameaças detectadas:

| Tipo | Ação |
| ---- | ---- |
| Governança de usuário | -Notificar usuários de alertas pendentes<br />-Enviar resumo de violação de DLP para proprietários de arquivo<br />-Suspender usuário<br />-Notificar o usuário sobre o alerta (por meio do Azure AD)<br />-Exigir que o usuário entre novamente (por meio do Azure AD)<br />– Suspender usuário (por meio do Azure AD) |
| Governança de aplicativo OAuth | -Revogar aplicativo OAuth para usuários |

Para obter mais informações sobre como corrigir ameaças de aplicativos, consulte [governando aplicativos conectados](governance-actions.md).

## <a name="protect-salesforce-in-real-time"></a>Proteger o Salesforce em tempo real

Examine nossas práticas recomendadas para [proteger e colaborar com usuários externos](best-practices.md#secure-collaboration-with-external-users-by-enforcing-real-time-session-controls) e [bloquear e proteger o download de dados confidenciais para dispositivos não gerenciados ou arriscados](best-practices.md#block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices).

## <a name="next-steps"></a>{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}

> [!div class="nextstepaction"]
> [Como conectar o Salesforce ao Microsoft Cloud App Security](connect-salesforce-to-microsoft-cloud-app-security.md)

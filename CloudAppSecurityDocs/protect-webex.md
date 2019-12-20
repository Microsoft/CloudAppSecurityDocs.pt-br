---
title: Como Cloud App Security ajuda a proteger seu ambiente Cisco WebEx
description: Este artigo fornece informações sobre os benefícios de conectar seu aplicativo Cisco WebEx para Cloud App Security usando o conector de API para visibilidade e controle sobre o uso.
author: shsagir
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: article
ms.date: 12/04/2019
ms.collection: M365-security-compliance
ms.openlocfilehash: 5ee11b6c97bc8aa5b0ec35394ac6f1f40bd3873a
ms.sourcegitcommit: db5ec79d219dd6674939c872ace7cd2ca80860a4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75190206"
---
# <a name="how-cloud-app-security-helps-protect-your-cisco-webex-environment"></a>Como Cloud App Security ajuda a proteger seu ambiente Cisco WebEx

*Aplica-se ao: Microsoft Cloud App Security*

Como uma plataforma de comunicação e colaboração, o Cisco WebEx permite a comunicação simplificada e a colaboração em toda a sua organização. Usar o Cisco WebEx para a troca de dados e ativos pode expor suas informações organizacionais confidenciais para usuários externos, por exemplo, em salas de bate-papo em que eles também podem participar de uma conversa com seus funcionários.

Conectar o Cisco WebEx ao Cloud App Security oferece informações aprimoradas sobre as atividades dos usuários, fornece detecções de proteção de informações e permite controles de governança automatizados.

## <a name="main-threats"></a>Principais ameaças

- Contas comprometidas e ameaças internas
- Vazamento de dados
- Reconhecimento de segurança insuficiente
- Ransomware
- BYOD (Traga seu próprio dispositivo) não gerenciado

## <a name="how-cloud-app-security-helps-to-protect-your-environment"></a>Como Cloud App Security ajuda a proteger seu ambiente

- [Impor políticas de conformidade e DLP para dados armazenados na nuvem](best-practices.md#enforce-dlp-and-compliance-policies-for-data-stored-in-the-cloud)
- [Limitar a exposição de dados compartilhados e impor políticas de colaboração](best-practices.md#limit-exposure-of-shared-data-and-enforce-collaboration-policies)
- [Use a trilha de auditoria das atividades para investigações forenses](best-practices.md#use-the-audit-trail-of-activities-for-forensic-investigations)

## <a name="control-cisco-webex-with-built-in-policies-and-policy-templates"></a>Controlar o Cisco WebEx com políticas internas e modelos de política

Você pode usar os seguintes modelos de política interna para detectar e notificá-lo sobre possíveis ameaças:

| Tipo | Nome |
| ---- | ---- |
| Política de detecção de anomalias interna | [Atividade executada pelo usuário encerrado](anomaly-detection-policy.md#activity-performed-by-terminated-user) (requer o AAD como IDP)<br />[Várias tentativas de logon com falha](anomaly-detection-policy.md#multiple-failed-login-attempts)<br />[Detecção de ransomware](anomaly-detection-policy.md#ransomware-activity)<br />[Atividades de exclusão de arquivo incomum](anomaly-detection-policy.md#unusual-activities-by-user)<br />[Atividades de compartilhamento de arquivos incomum](anomaly-detection-policy.md#unusual-activities-by-user)<br />[Atividades de download de vários arquivos incomuns](anomaly-detection-policy.md#unusual-activities-by-user) |
| Modelo de política de arquivo | Detectar um arquivo compartilhado com um domínio não autorizado<br />Detectar um arquivo compartilhado com endereços de email pessoais<br />Detectar arquivos com PII/PCI/PHI |
| Modelo de política de atividade | Download em massa por um único usuário<br />Atividade de ransomware potencial |

Para obter mais informações sobre como criar políticas, consulte [criar uma política](control-cloud-apps-with-policies.md#create-a-policy).

## <a name="automate-governance-controls"></a>Automatizar controles de governança

Além de monitorar possíveis ameaças, você pode aplicar e automatizar as seguintes ações de governança do Cisco WebEx para corrigir ameaças detectadas:

| Tipo | Ação |
| ---- | ---- |
| Governança de usuário | -Notificar o usuário sobre o alerta (por meio do Azure AD)<br />-Exigir que o usuário entre novamente (por meio do Azure AD)<br />– Suspender usuário (por meio do Azure AD) |
| Governança de dados | -Arquivo de lixo |

Para obter mais informações sobre como corrigir ameaças de aplicativos, consulte [governando aplicativos conectados](governance-actions.md).

## <a name="protect-cisco-webex-in-real-time"></a>Proteger o Cisco WebEx em tempo real

Examine nossas práticas recomendadas para [proteger e colaborar com usuários externos](best-practices.md#secure-collaboration-with-external-users-by-enforcing-real-time-session-controls) e [bloquear e proteger o download de dados confidenciais para dispositivos não gerenciados ou arriscados](best-practices.md#block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Como conectar o Cisco WebEx ao Microsoft Cloud App Security](connect-webex-to-microsoft-cloud-app-security.md)

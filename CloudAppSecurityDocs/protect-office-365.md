---
title: Como Cloud App Security ajuda a proteger seu ambiente do Office 365
description: Este artigo fornece informações sobre os benefícios de conectar seu aplicativo do Office 365 para Cloud App Security usando o conector de API para visibilidade e controle sobre o uso.
author: shsagir
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: article
ms.date: 12/04/2019
ms.collection: M365-security-compliance
ms.openlocfilehash: eaf8218f45da787e361fe4e1627bb2cdfc4afeb1
ms.sourcegitcommit: 27c45aa35c11c4ce54edbe10a9d22cf6b452fbe6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78304791"
---
# <a name="how-cloud-app-security-helps-protect-your-office-365-environment"></a>Como Cloud App Security ajuda a proteger seu ambiente do Office 365

*Aplica-se a: Microsoft Cloud App Security*

Como um pacote de produtividade importante que fornece armazenamento de arquivos em nuvem, colaboração, BI e ferramentas de CRM, o Office 365 permite que os usuários compartilhem seus documentos em sua organização e parceiros de maneira simplificada e eficiente. Usar o Office 365 pode expor seus dados confidenciais não apenas internamente, mas também para colaboradores externos, ou ainda pior disponibilizá-los publicamente por meio de um link compartilhado. Esses incidentes podem ocorrer devido a um ator mal-intencionado ou por um funcionário inconsciente. O Office 365 também fornece um grande sistema de eco de aplicativos de terceiros para ajudar a aumentar a produtividade. O uso desses aplicativos pode expor sua organização ao risco de aplicativos mal-intencionados ou uso de aplicativos com permissões excessivas.

Conectar o Office 365 ao Cloud App Security oferece informações aprimoradas sobre as atividades dos usuários, fornece detecção de ameaças usando detecções de anomalias baseadas em Machine Learning, detecções de proteção de informações (como a detecção de compartilhamento de informações externas ), permite controles de atualização automatizados e detecta ameaças de aplicativos de terceiros habilitados em sua organização.

O uso do conector do Office 365 fornece proteção para os seguintes produtos:

- CRM do Dynamics 365
- Exchange
- Office 365
- OneDrive
- Automatizar energia
- Power BI
- SharePoint
- Skype for Business
- Equipes
- Yammer

> [!NOTE]
> O Cloud App Security se integra diretamente aos [logs de auditoria do Office 365](https://docs.microsoft.com/microsoft-365/compliance/detailed-properties-in-the-office-365-audit-log?view=o365-worldwide) e recebe todos os eventos auditados de **todos os serviços com suporte**, como PowerApps, Forms, Sway e Stream.

## <a name="main-threats"></a>Principais ameaças

- Contas comprometidas e ameaças internas
- Vazamento de dados
- Reconhecimento de segurança insuficiente
- Aplicativos mal-intencionados de terceiros
- Malware
- Phishing
- Ransomware
- BYOD (Traga seu próprio dispositivo) não gerenciado

## <a name="how-cloud-app-security-helps-to-protect-your-environment"></a>Como Cloud App Security ajuda a proteger seu ambiente

- [Detecte ameaças à nuvem, contas comprometidas e pessoas mal-intencionadas](best-practices.md#detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware)
- [Descobrir, classificar, rotular e proteger dados regulamentados e confidenciais armazenados na nuvem](best-practices.md#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)
- [Descobrir e gerenciar aplicativos OAuth que têm acesso ao seu ambiente](manage-app-permissions.md)
- [Impor políticas de conformidade e DLP para dados armazenados na nuvem](best-practices.md#enforce-dlp-and-compliance-policies-for-data-stored-in-the-cloud)
- [Limitar a exposição de dados compartilhados e impor políticas de colaboração](best-practices.md#limit-exposure-of-shared-data-and-enforce-collaboration-policies)
- [Use a trilha de auditoria das atividades para investigações forenses](best-practices.md#use-the-audit-trail-of-activities-for-forensic-investigations)

## <a name="control-office-365-with-built-in-policies-and-policy-templates"></a>Controlar o Office 365 com políticas internas e modelos de política

Você pode usar os seguintes modelos de política interna para detectar e notificá-lo sobre possíveis ameaças:

| Digite | Name |
| ---- | ---- |
| Política de detecção de anomalias interna | [Atividade de endereços IP anônimos](anomaly-detection-policy.md#activity-from-anonymous-ip-addresses)<br />[Atividade de um país infrequente](anomaly-detection-policy.md#activity-from-infrequent-country)<br />[Atividade de endereços IP suspeitos](anomaly-detection-policy.md#activity-from-suspicious-ip-addresses)<br />[Viagem impossível](anomaly-detection-policy.md#impossible-travel)<br />[Atividade executada pelo usuário encerrado](anomaly-detection-policy.md#activity-performed-by-terminated-user) (requer o AAD como IDP)<br />[Detecção de malware](anomaly-detection-policy.md#malware-detection)<br />[Várias tentativas de logon com falha](anomaly-detection-policy.md#multiple-failed-login-attempts)<br />[Detecção de ransomware](anomaly-detection-policy.md#ransomware-activity)<br />[Atividade de exclusão de email suspeito (versão prévia)](anomaly-detection-policy.md#suspicious-email-deletion-activity-preview)<br />[Caixa de entrada suspeita encaminhando](anomaly-detection-policy.md#suspicious-inbox-forwarding)[atividades incomuns de exclusão de arquivo](anomaly-detection-policy.md#unusual-activities-by-user)<br />[Atividades de compartilhamento de arquivos incomum](anomaly-detection-policy.md#unusual-activities-by-user)<br />[Atividades de download de vários arquivos incomuns](anomaly-detection-policy.md#unusual-activities-by-user) |
| Modelo de política de atividade | Logon de um endereço IP arriscado<br />Download em massa por um único usuário<br />Atividade de ransomware potencial |
| Modelo de política de arquivo | Detectar um arquivo compartilhado com um domínio não autorizado<br />Detectar um arquivo compartilhado com endereços de email pessoais<br />Detectar arquivos com PII/PCI/PHI |
| Política de detecção de anomalias do aplicativo OAuth | [Nome do aplicativo OAuth enganoso](app-permission-policy.md#oauth-app-anomaly-detection-policies)<br />[Nome do editor enganoso para um aplicativo OAuth](app-permission-policy.md#oauth-app-anomaly-detection-policies)<br />[Consentimento de aplicativo OAuth mal-intencionado](app-permission-policy.md#oauth-app-anomaly-detection-policies) |

Para obter mais informações sobre como criar políticas, consulte [criar uma política](control-cloud-apps-with-policies.md#create-a-policy).

## <a name="automate-governance-controls"></a>Automatizar controles de governança

Além de monitorar possíveis ameaças, você pode aplicar e automatizar as seguintes ações de governança do Office 365 para corrigir ameaças detectadas:

| Digite | Ação |
| ---- | ---- |
| Governança de dados | **For**<br /> -Herdar permissões de pasta pai<br /> -Tornar o arquivo/pasta particular<br /> -Colocar arquivo/pasta na quarentena do administrador<br /> -Colocar arquivo/pasta na quarentena do usuário<br /> -Lixeira/arquivo/pasta<br /> -Remover um colaborador específico<br /> -Remover colaboradores externos no arquivo/pasta<br /> -Aplicar rótulo de classificação da proteção de informações do Azure<br /> -Remover rótulo de classificação da proteção de informações do Azure<br /> **Services**<br /> -Herdar permissões de pasta pai<br /> -Tornar o arquivo/pasta particular<br /> -Colocar arquivo/pasta na quarentena do administrador<br /> -Colocar arquivo/pasta na quarentena do usuário<br /> -Colocar arquivo/pasta em quarentena do usuário e adicionar permissões de proprietário<br /> -Lixeira/arquivo/pasta<br /> -Remover colaboradores externos no arquivo/pasta<br /> -Remover um colaborador específico<br /> -Aplicar rótulo de classificação da proteção de informações do Azure<br /> -Remover rótulo de classificação da proteção de informações do Azure |
| Governança de usuário | -Notificar o usuário sobre o alerta (por meio do Azure AD)<br /> -Exigir que o usuário entre novamente (por meio do Azure AD)<br /> – Suspender usuário (por meio do Azure AD) |
| Governança de aplicativo OAuth | -Revogar permissão de aplicativo OAuth |

Para obter mais informações sobre como corrigir ameaças de aplicativos, consulte [governando aplicativos conectados](governance-actions.md).

## <a name="protect-office-365-in-real-time"></a>Proteja o Office 365 em tempo real

Examine nossas práticas recomendadas para [proteger e colaborar com usuários externos](best-practices.md#secure-collaboration-with-external-users-by-enforcing-real-time-session-controls) e [bloquear e proteger o download de dados confidenciais para dispositivos não gerenciados ou arriscados](best-practices.md#block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Como conectar o Office 365 ao Microsoft Cloud App Security](connect-office-365-to-microsoft-cloud-app-security.md)

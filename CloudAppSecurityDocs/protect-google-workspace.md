---
title: Como Cloud App Security ajuda a proteger seu ambiente do Google Workspace
description: Este artigo fornece informações sobre os benefícios de conectar seu aplicativo Google Workspace ao Cloud App Security usando o conector de API para visibilidade e controle sobre o uso.
ms.date: 12/04/2019
ms.topic: article
ms.openlocfilehash: d8dbdb2ede59c75a8556b5ba1059bd3005c80481
ms.sourcegitcommit: 72ddcd0f9a83251d588009abf506676612c50267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/13/2020
ms.locfileid: "97370374"
---
# <a name="how-cloud-app-security-helps-protect-your-google-workspace-environment"></a>Como Cloud App Security ajuda a proteger seu ambiente do Google Workspace

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Como uma ferramenta de armazenamento e colaboração de arquivos em nuvem, o Google Workspace permite que seus usuários compartilhem seus documentos em sua organização e parceiros de maneira simplificada e eficiente. Usar o Google Workspace pode expor seus dados confidenciais não apenas internamente, mas também para colaboradores externos, ou até mesmo pior disponibilizá-los publicamente por meio de um link compartilhado. Esses incidentes podem ser causados por atores mal-intencionados ou por funcionários sem reconhecimento. O Google Workspace também fornece um grande sistema de eco de aplicativo de terceiros para ajudar a aumentar a produtividade. O uso desses aplicativos pode expor sua organização ao risco de aplicativos mal-intencionados ou uso de aplicativos com permissões excessivas.

Conectar o Google Workspace ao Cloud App Security oferece informações aprimoradas sobre as atividades dos usuários, fornece detecção de ameaças usando as detecções de anomalias baseadas no aprendizado de máquina, detecções da proteção de informações (como a detecção de compartilhamento de informações externas), habilita controles de atualização automatizados e detecta ameaças de aplicativos de terceiros habilitados em sua organização.

## <a name="main-threats"></a>Principais ameaças

- Contas comprometidas e ameaças internas
- Vazamento de dados
- Reconhecimento de segurança insuficiente
- Aplicativos de terceiros mal-intencionados e Complementos do Google
- Malware
- Ransomware
- BYOD (Traga seu próprio dispositivo) não gerenciado

## <a name="how-cloud-app-security-helps-to-protect-your-environment"></a>Como Cloud App Security ajuda a proteger seu ambiente

- [Detecte ameaças à nuvem, contas comprometidas e pessoas mal-intencionadas](best-practices.md#detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware)
- [Descobrir, classificar, rotular e proteger dados regulamentados e confidenciais armazenados na nuvem](best-practices.md#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)
- [Descobrir e gerenciar aplicativos OAuth que têm acesso ao seu ambiente](manage-app-permissions.md)
- [Impor políticas de conformidade e DLP (proteção contra perda de dados) para dados armazenados na nuvem](best-practices.md#enforce-dlp-and-compliance-policies-for-data-stored-in-the-cloud)
- [Limitar a exposição de dados compartilhados e impor políticas de colaboração](best-practices.md#limit-exposure-of-shared-data-and-enforce-collaboration-policies)
- [Usar a trilha de auditoria das atividades para investigações forenses](best-practices.md#use-the-audit-trail-of-activities-for-forensic-investigations)

## <a name="control-google-workspace-with-built-in-policies-and-policy-templates"></a>Controlar o Google Workspace com políticas internas e modelos de política

Você pode usar os seguintes modelos de política interna para detectar e notificá-lo sobre possíveis ameaças:

| Tipo | Nome |
| ---- | ---- |
| Política de detecção de anomalias interna | [Atividade de endereços IP anônimos](anomaly-detection-policy.md#activity-from-anonymous-ip-addresses)<br />[Atividade de país não frequente](anomaly-detection-policy.md#activity-from-infrequent-country)<br />[Atividade de endereços IP suspeitos](anomaly-detection-policy.md#activity-from-suspicious-ip-addresses)<br />[Viagem impossível](anomaly-detection-policy.md#impossible-travel)<br />[Atividade executada pelo usuário encerrado](anomaly-detection-policy.md#activity-performed-by-terminated-user) (requer o AAD como IDP)<br />[Detecção de malware](anomaly-detection-policy.md#malware-detection)<br />[Várias tentativas de logon com falha](anomaly-detection-policy.md#multiple-failed-login-attempts)<br />[Detecção de ransomware](anomaly-detection-policy.md#ransomware-activity)<br />[Atividade administrativas incomuns](anomaly-detection-policy.md#unusual-activities-by-user)<br />[Atividades incomuns de exclusão de arquivos](anomaly-detection-policy.md#unusual-activities-by-user)<br />[Atividades incomuns de compartilhamento de arquivos](anomaly-detection-policy.md#unusual-activities-by-user)<br />[Atividades incomuns de download de vários arquivos](anomaly-detection-policy.md#unusual-activities-by-user) |
| Modelo de política de atividade | Logon de um endereço IP com risco<br />Download em massa por um único usuário<br />Atividade de ransomware potencial |
| Modelo de política de arquivo | Detectar um arquivo compartilhado com um domínio não autorizado<br />Detectar um arquivo compartilhado com endereços de email pessoais<br />Detectar arquivos com PII/PCI/PHI |

Para obter mais informações sobre como criar políticas, consulte [criar uma política](control-cloud-apps-with-policies.md#create-a-policy).

## <a name="automate-governance-controls"></a>Automatizar controles de governança

Além de monitorar possíveis ameaças, você pode aplicar e automatizar as seguintes ações de governança do Google Workspace para corrigir ameaças detectadas:

| Tipo | Ação |
| ---- | ---- |
| Governança de dados | -Aplicar rótulo de classificação da proteção de informações do Azure<br />-Conceder permissão de leitura ao domínio<br />-Criar um arquivo/pasta no Google Drive privado<br />-Reduzir o acesso público ao arquivo/pasta<br />-Remover um colaborador de um arquivo<br />-Remover rótulo de classificação da proteção de informações do Azure<br />-Remover colaboradores externos no arquivo/pasta<br />-Remover a capacidade de compartilhamento do editor de arquivo<br />-Remover acesso público ao arquivo/pasta<br />-Exigir que o usuário redefina a senha para o Google<br />-Enviar resumo de violação de DLP para proprietários de arquivo<br />-Enviar violação de DLP para o último editor de arquivo<br />-Transferir Propriedade do arquivo<br />-Arquivo de lixo |
| Governança de usuário | -Suspender usuário<br />-Notificar o usuário sobre o alerta (por meio do Azure AD)<br />-Exigir que o usuário entre novamente (por meio do Azure AD)<br />– Suspender usuário (por meio do Azure AD) |
| Governança de aplicativo OAuth | -Revogar permissão de aplicativo OAuth |

Para obter mais informações sobre como corrigir ameaças de aplicativos, consulte [governando aplicativos conectados](governance-actions.md).

## <a name="protect-google-workspace-in-real-time"></a>Proteger o Google Workspace em tempo real

Examine nossas práticas recomendadas para [proteger e colaborar com usuários externos](best-practices.md#secure-collaboration-with-external-users-by-enforcing-real-time-session-controls) e [bloquear e proteger o download de dados confidenciais para dispositivos não gerenciados ou arriscados](best-practices.md#block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Como conectar o Google Workspace ao Microsoft Cloud App Security](connect-google-workspace-to-microsoft-cloud-app-security.md)

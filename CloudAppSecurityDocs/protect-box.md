---
title: Como Cloud App Security ajuda a proteger o ambiente do box
description: Este artigo fornece informações sobre os benefícios de conectar seu aplicativo de caixa para Cloud App Security usando o conector de API para visibilidade e controle sobre o uso.
ms.date: 12/04/2019
ms.topic: article
ms.openlocfilehash: 6ab53ae59f13e59029ee6745922e28c89afa3566
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96315286"
---
# <a name="how-cloud-app-security-helps-protect-your-box-environment"></a>Como Cloud App Security ajuda a proteger o ambiente do box

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Como uma ferramenta de armazenamento e colaboração de arquivos em nuvem, o box permite que os usuários compartilhem seus documentos em sua organização e parceiros de maneira simplificada e eficiente. O uso do box pode expor seus dados confidenciais não apenas internamente, mas também para colaboradores externos, ou até mesmo pior disponibilizá-los publicamente por meio de um link compartilhado. Esses incidentes podem ser causados por atores mal-intencionados ou por funcionários sem reconhecimento.

A caixa de conexão com o Cloud App Security oferece informações aprimoradas sobre as atividades dos usuários, fornecer detecção de ameaças usando detecções de anomalias baseadas no aprendizado de máquina, detecções de proteção de informações como detectar o compartilhamento de informações externas e habilitar controles de correção automatizados.

## <a name="main-threats"></a>Principais ameaças

- Contas comprometidas e ameaças internas
- Vazamento de dados
- Reconhecimento de segurança insuficiente
- Malware
- Ransomware
- BYOD (Traga seu próprio dispositivo) não gerenciado

## <a name="how-cloud-app-security-helps-to-protect-your-environment"></a>Como Cloud App Security ajuda a proteger seu ambiente

- [Detecte ameaças à nuvem, contas comprometidas e pessoas mal-intencionadas](best-practices.md#detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware)
- [Descobrir, classificar, rotular e proteger dados regulamentados e confidenciais armazenados na nuvem](best-practices.md#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)
- [Impor políticas de conformidade e DLP (proteção contra perda de dados) para dados armazenados na nuvem](best-practices.md#enforce-dlp-and-compliance-policies-for-data-stored-in-the-cloud)
- [Limitar a exposição de dados compartilhados e impor políticas de colaboração](best-practices.md#limit-exposure-of-shared-data-and-enforce-collaboration-policies)
- [Usar a trilha de auditoria das atividades para investigações forenses](best-practices.md#use-the-audit-trail-of-activities-for-forensic-investigations)

## <a name="control-box-with-built-in-policies-and-policy-templates"></a>Caixa de controle com políticas internas e modelos de política

Você pode usar os seguintes modelos de política interna para detectar e notificá-lo sobre possíveis ameaças:

| Type | Nome |
| ---- | ---- |
| Política de detecção de anomalias interna | [Atividade de endereços IP anônimos](anomaly-detection-policy.md#activity-from-anonymous-ip-addresses)<br />[Atividade de país não frequente](anomaly-detection-policy.md#activity-from-infrequent-country)<br />[Atividade de endereços IP suspeitos](anomaly-detection-policy.md#activity-from-suspicious-ip-addresses)<br />[Viagem impossível](anomaly-detection-policy.md#impossible-travel)<br />[Atividade executada pelo usuário encerrado](anomaly-detection-policy.md#activity-performed-by-terminated-user) (requer o AAD como IDP)<br />[Detecção de malware](anomaly-detection-policy.md#malware-detection)<br />[Várias tentativas de logon com falha](anomaly-detection-policy.md#multiple-failed-login-attempts)<br />[Detecção de ransomware](anomaly-detection-policy.md#ransomware-activity)<br />[Atividade administrativas incomuns](anomaly-detection-policy.md#unusual-activities-by-user)<br />[Atividades incomuns de exclusão de arquivos](anomaly-detection-policy.md#unusual-activities-by-user)<br />[Atividades incomuns de compartilhamento de arquivos](anomaly-detection-policy.md#unusual-activities-by-user)<br />[Atividades incomuns de download de vários arquivos](anomaly-detection-policy.md#unusual-activities-by-user) |
| Modelo de política de atividade | Logon de um endereço IP com risco<br />Download em massa por um único usuário<br />Atividade de ransomware potencial |
| Modelo de política de arquivo | Detectar um arquivo compartilhado com um domínio não autorizado<br />Detectar um arquivo compartilhado com endereços de email pessoais<br />Detectar arquivos com PII/PCI/PHI |

Para obter mais informações sobre como criar políticas, consulte [criar uma política](control-cloud-apps-with-policies.md#create-a-policy).

## <a name="automate-governance-controls"></a>Automatizar controles de governança

Além de monitorar possíveis ameaças, você pode aplicar e automatizar as seguintes ações de governança para corrigir ameaças detectadas:

| Type | Ação |
| ---- | ---- |
| Governança de dados | -Aplicar rótulo de classificação da proteção de informações do Azure<br />-Alterar o nível de acesso do link compartilhado<br />-Colocar arquivo na quarentena do administrador<br />-Colocar arquivo na quarentena do usuário<br />-Remover um colaborador de um arquivo<br />-Remover rótulo de classificação da proteção de informações do Azure<br />-Remover links compartilhados diretos<br />-Remover colaboradores externos<br />-Enviar resumo de violação de DLP para proprietários de arquivo<br />-Enviar resumo de violação para o último editor de arquivo<br />-Definir a data de validade para um link compartilhado<br /> -Arquivo de lixo |
| Governança de usuário | -Suspender usuário<br />-Notificar o usuário sobre o alerta (por meio do Azure AD)<br />-Exigir que o usuário entre novamente (por meio do Azure AD)<br />– Suspender usuário (por meio do Azure AD) |

Para obter mais informações sobre como corrigir ameaças de aplicativos, consulte [governando aplicativos conectados](governance-actions.md).

## <a name="protect-box-in-real-time"></a>Proteger a caixa em tempo real

Examine nossas práticas recomendadas para [proteger e colaborar com usuários externos](best-practices.md#secure-collaboration-with-external-users-by-enforcing-real-time-session-controls) e [bloquear e proteger o download de dados confidenciais para dispositivos não gerenciados ou arriscados](best-practices.md#block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Como conectar a caixa ao Microsoft Cloud App Security](connect-box-to-microsoft-cloud-app-security.md)

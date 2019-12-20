---
title: Como Cloud App Security ajuda a proteger seu ambiente de Amazon Web Services
description: Este artigo fornece informações sobre os benefícios de conectar seu aplicativo AWS para Cloud App Security usando o conector de API para visibilidade e controle sobre o uso.
author: shsagir
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: article
ms.date: 12/04/2019
ms.collection: M365-security-compliance
ms.openlocfilehash: 151e698fe196946c41e945857b69a1e41135d433
ms.sourcegitcommit: db5ec79d219dd6674939c872ace7cd2ca80860a4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75190006"
---
# <a name="how-cloud-app-security-helps-protect-your-amazon-web-services-aws-environment"></a>Como Cloud App Security ajuda a proteger seu ambiente de Amazon Web Services (AWS)

*Aplica-se ao: Microsoft Cloud App Security*

Amazon Web Services é um provedor de IaaS que permite que sua organização hospede e gerencie suas cargas de trabalho inteiras na nuvem. Junto com os benefícios de aproveitar a infraestrutura na nuvem, os ativos mais críticos de sua organização podem ser expostos a ameaças. Os ativos expostos incluem instâncias de armazenamento com informações potencialmente confidenciais, recursos de computação que operam alguns dos seus aplicativos, portas e redes virtuais privadas mais importantes que permitem o acesso à sua organização.

Conectar o AWS ao Cloud App Security ajuda a proteger seus ativos e detectar possíveis ameaças monitorando atividades administrativas e de entrada, notificando sobre possíveis ataques de força bruta, uso mal-intencionado de uma conta de usuário com privilégios, exclusões incomuns de VMs, e os buckets de armazenamento expostos publicamente.

## <a name="main-threats"></a>Principais ameaças

- Abuso de recursos de nuvem
- Contas comprometidas e ameaças internas
- Vazamento de dados
- Insuficiência de configuração de recurso e controle de acesso insuficiente

## <a name="how-cloud-app-security-helps-to-protect-your-environment"></a>Como Cloud App Security ajuda a proteger seu ambiente

- [Detecte ameaças à nuvem, contas comprometidas e pessoas mal-intencionadas](best-practices.md#detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware)
- [Limitar a exposição de dados compartilhados e impor políticas de colaboração](best-practices.md#limit-exposure-of-shared-data-and-enforce-collaboration-policies)
- [Mantenha-se atualizado com a recomendação de configuração de segurança mais recente](security-config-aws.md)
- [Use a trilha de auditoria das atividades para investigações forenses](best-practices.md#use-the-audit-trail-of-activities-for-forensic-investigations)

## <a name="control-aws-with-built-in-policies-and-policy-templates"></a>Controlar o AWS com políticas internas e modelos de política

Você pode usar os seguintes modelos de política interna para detectar e notificá-lo sobre possíveis ameaças:

| Tipo | Nome |
| ---- | ---- |
| Modelo de política de atividade | Falhas de conexão do console de administração<br />Alterações de configuração do CloudTrail<br />Alterações de configuração da instância EC2<br />Alterações de política IAM<br />Logon de um endereço IP com risco<br />Alterações de ACL (lista de controle de acesso) de rede<br />Alterações do gateway de rede<br />Alterações de configuração S3<br />Alterações na configuração do grupo de segurança<br />Alterações na rede virtual privada |
| Política de detecção de anomalias interna | [Atividade de endereços IP anônimos](anomaly-detection-policy.md#activity-from-anonymous-ip-addresses)<br />[Atividade de país não frequente](anomaly-detection-policy.md#activity-from-infrequent-country)<br />[Atividade de endereços IP suspeitos](anomaly-detection-policy.md#activity-from-suspicious-ip-addresses)<br />[Viagem impossível](anomaly-detection-policy.md#impossible-travel)<br />[Atividade executada pelo usuário encerrado](anomaly-detection-policy.md#activity-performed-by-terminated-user) (requer o AAD como IDP)<br />[Várias tentativas de logon com falha](anomaly-detection-policy.md#multiple-failed-login-attempts)<br />[Atividades administrativas incomuns](anomaly-detection-policy.md#unusual-activities-by-user)<br />[Várias atividades de exclusão de armazenamento incomum](anomaly-detection-policy.md#unusual-activities-by-user) (visualização)<br />[Várias atividades de exclusão de VM](anomaly-detection-policy.md#multiple-delete-vm-activities)<br />[Várias atividades de criação de VM incomuns](anomaly-detection-policy.md#unusual-activities-by-user) (versão prévia) |
| Modelo de política de arquivo | O Bucket S3 pode ser acessado publicamente |

Para obter mais informações sobre como criar políticas, consulte [criar uma política](control-cloud-apps-with-policies.md#create-a-policy).

## <a name="automate-governance-controls"></a>Automatizar controles de governança

Além de monitorar possíveis ameaças, você pode aplicar e automatizar as seguintes ações de governança AWS para corrigir ameaças detectadas:

| Tipo | Ação |
| ---- | ---- |
| Governança de usuário | -Notificar o usuário sobre o alerta (por meio do Azure AD)<br />-Exigir que o usuário entre novamente (por meio do Azure AD)<br />– Suspender usuário (por meio do Azure AD) |
| Governança de dados | -Tornar um Bucket S3 privado<br />-Remover um colaborador de um Bucket S3 |

Para obter mais informações sobre como corrigir ameaças de aplicativos, consulte [governando aplicativos conectados](governance-actions.md).

## <a name="protect-aws-in-real-time"></a>Proteger AWS em tempo real

Examine nossas práticas recomendadas para [bloquear e proteger o download de dados confidenciais para dispositivos não gerenciados ou arriscados](best-practices.md#block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Como conectar o AWS ao Microsoft Cloud App Security](connect-aws-to-microsoft-cloud-app-security.md)

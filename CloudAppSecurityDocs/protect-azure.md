---
title: Como Cloud App Security ajuda a proteger seu ambiente do Azure
description: Este artigo fornece informações sobre os benefícios de conectar seu aplicativo do Azure para Cloud App Security usando o conector de API para visibilidade e controle sobre o uso.
author: shsagir
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: article
ms.date: 09/15/2020
ms.collection: M365-security-compliance
ms.openlocfilehash: 44e15814bf3a7017d44eb7fb3465245b8ad8e43b
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90877536"
---
# <a name="how-cloud-app-security-helps-protect-your-azure-environment"></a>Como Cloud App Security ajuda a proteger seu ambiente do Azure

[!INCLUDE [Banner for top of topics](includes/banner.md)]

O Azure é um provedor de IaaS que permite que sua organização hospede e gerencie suas cargas de trabalho inteiras na nuvem. Junto com os benefícios de aproveitar a infraestrutura na nuvem, os ativos mais críticos de sua organização podem ser expostos a ameaças. Os ativos expostos incluem instâncias de armazenamento com informações potencialmente confidenciais, recursos de computação que operam alguns dos seus aplicativos, portas e redes virtuais privadas mais importantes que permitem o acesso à sua organização.

Conectar o Azure ao Cloud App Security ajuda a proteger seus ativos e detectar possíveis ameaças monitorando atividades administrativas e de entrada, notificando sobre possíveis ataques de força bruta, uso mal-intencionado de uma conta de usuário com privilégios e exclusões incomuns de VMs.

## <a name="main-threats"></a>Principais ameaças

- Abuso de recursos de nuvem
- Contas comprometidas e ameaças internas
- Vazamento de dados
- Insuficiência de configuração de recurso e controle de acesso insuficiente

## <a name="how-cloud-app-security-helps-to-protect-your-environment"></a>Como Cloud App Security ajuda a proteger seu ambiente

- [Detecte ameaças à nuvem, contas comprometidas e pessoas mal-intencionadas](best-practices.md#detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware)
- [Limitar a exposição de dados compartilhados e impor políticas de colaboração](best-practices.md#limit-exposure-of-shared-data-and-enforce-collaboration-policies)
- [Usar a trilha de auditoria das atividades para investigações forenses](best-practices.md#use-the-audit-trail-of-activities-for-forensic-investigations)
- [Examinar as recomendações de configuração de segurança](security-config-azure.md)

## <a name="control-azure-with-built-in-policies-and-policy-templates"></a>Controlar o Azure com políticas internas e modelos de política

Você pode usar os seguintes modelos de política interna para detectar e notificá-lo sobre possíveis ameaças:

| Tipo | Nome |
| ---- | ---- |
| Política de detecção de anomalias interna | [Atividade de endereços IP anônimos](anomaly-detection-policy.md#activity-from-anonymous-ip-addresses)<br />[Atividade de país não frequente](anomaly-detection-policy.md#activity-from-infrequent-country)<br />[Atividade de endereços IP suspeitos](anomaly-detection-policy.md#activity-from-suspicious-ip-addresses)<br />[Atividade executada pelo usuário encerrado](anomaly-detection-policy.md#activity-performed-by-terminated-user) (requer o AAD como IDP)<br />[Várias tentativas de logon com falha](anomaly-detection-policy.md#multiple-failed-login-attempts)<br />[Atividade administrativas incomuns](anomaly-detection-policy.md#unusual-activities-by-user)<br />[Várias atividades de exclusão de armazenamento incomum](anomaly-detection-policy.md#unusual-activities-by-user) (visualização)<br />[Várias atividades de exclusão de VM](anomaly-detection-policy.md#multiple-delete-vm-activities)<br />[Várias atividades de criação de VM incomuns](anomaly-detection-policy.md#unusual-activities-by-user) (versão prévia) |

Para obter mais informações sobre como criar políticas, consulte [criar uma política](control-cloud-apps-with-policies.md#create-a-policy).

## <a name="security-recommendations"></a>Recomendações de Segurança

Cloud App Security fornece uma exibição no nível de locatário da sua plataforma Azure, listando as recomendações de segurança de todas as assinaturas do Azure no locatário. Você pode usar as recomendações de segurança integradas do Azure para mais de 100 recursos do Azure no [benchmark de segurança do Azure](/azure/security/benchmarks/introduction), bem como [recomendações personalizadas](/azure/security-center/custom-security-policies). As recomendações integradas incluem os seguintes tipos de recursos: máquinas virtuais, identidade e acesso, dados e armazenamento, computação e aplicativos, redes, contêineres e serviços de aplicativos.

Você deve examinar continuamente as recomendações de segurança para avaliar e avaliar o status atual da postura de segurança da sua plataforma e identificar lacunas de configuração importantes. Em seguida, você deve criar um plano para atenuar os problemas em sua plataforma Azure.

Para obter mais informações, consulte o [Guia de recomendações do Azure](/azure/security-center/recommendations-reference) e as [recomendações de segurança do Azure](security-config-azure.md).

## <a name="automate-governance-controls"></a>Automatizar controles de governança

Além de monitorar possíveis ameaças, você pode aplicar e automatizar as seguintes ações de governança do Azure para corrigir ameaças detectadas:

| Tipo | Ação |
| ---- | ---- |
| Governança de usuário | -Notificar o usuário sobre o alerta (por meio do Azure AD)<br />-Exigir que o usuário entre novamente (por meio do Azure AD)<br />– Suspender usuário (por meio do Azure AD) |

Para obter mais informações sobre como corrigir ameaças de aplicativos, consulte [governando aplicativos conectados](governance-actions.md).

## <a name="protect-azure-in-real-time"></a>Proteger o Azure em tempo real

Examine nossas práticas recomendadas para [proteger e colaborar com usuários externos](best-practices.md#secure-collaboration-with-external-users-by-enforcing-real-time-session-controls) e [bloquear e proteger o download de dados confidenciais para dispositivos não gerenciados ou arriscados](best-practices.md#block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Como conectar o Azure ao Microsoft Cloud App Security](connect-azure-to-microsoft-cloud-app-security.md)

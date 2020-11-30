---
title: Como Cloud App Security ajuda a proteger seu ambiente de Google Cloud Platform
description: Este artigo fornece informações sobre os benefícios de conectar seu aplicativo Google Cloud Platform para Cloud App Security usando o conector de API para visibilidade e controle sobre o uso.
ms.date: 09/15/2020
ms.topic: article
ms.openlocfilehash: 461d6c0c883c84892a049de7193dd5f28e1a0a99
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96315252"
---
# <a name="how-cloud-app-security-helps-protect-your-google-cloud-platform-gcp-environment"></a>Como Cloud App Security ajuda a proteger seu ambiente de Google Cloud Platform (GCP)

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Google Cloud Platform é um provedor de IaaS que permite que sua organização hospede e gerencie suas cargas de trabalho inteiras na nuvem. Junto com os benefícios de aproveitar a infraestrutura na nuvem, os ativos mais críticos de sua organização podem ser expostos a ameaças. Os ativos expostos incluem instâncias de armazenamento com informações potencialmente confidenciais, recursos de computação que operam alguns dos seus aplicativos, portas e redes virtuais privadas mais importantes que permitem o acesso à sua organização.

Conectar o GCP ao Cloud App Security ajuda a proteger seus ativos e detectar possíveis ameaças monitorando atividades administrativas e de entrada, notificando sobre possíveis ataques de força bruta, uso mal-intencionado de uma conta de usuário com privilégios e exclusões incomuns de VMs.

## <a name="main-threats"></a>Principais ameaças

- Abuso de recursos de nuvem
- Contas comprometidas e ameaças internas
- Vazamento de dados
- Insuficiência de configuração de recurso e controle de acesso insuficiente

## <a name="how-cloud-app-security-helps-to-protect-your-environment"></a>Como Cloud App Security ajuda a proteger seu ambiente

- [Detecte ameaças à nuvem, contas comprometidas e pessoas mal-intencionadas](best-practices.md#detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware)
- [Usar a trilha de auditoria das atividades para investigações forenses](best-practices.md#use-the-audit-trail-of-activities-for-forensic-investigations)
- [Examinar as recomendações de configuração de segurança](security-config-gcp.md)

## <a name="control-gcp-with-built-in-policies-and-policy-templates"></a>Controlar o GCP com políticas internas e modelos de política

Você pode usar os seguintes modelos de política interna para detectar e notificá-lo sobre possíveis ameaças:

| Type | Nome |
| ---- | ---- |
| Política de detecção de anomalias interna | [Atividade de endereços IP anônimos](anomaly-detection-policy.md#activity-from-anonymous-ip-addresses)<br />[Atividade de país não frequente](anomaly-detection-policy.md#activity-from-infrequent-country)<br />[Atividade de endereços IP suspeitos](anomaly-detection-policy.md#activity-from-suspicious-ip-addresses)<br />[Viagem impossível](anomaly-detection-policy.md#impossible-travel)<br />[Atividade executada pelo usuário encerrado](anomaly-detection-policy.md#activity-performed-by-terminated-user) (requer o AAD como IDP)<br />[Várias tentativas de logon com falha](anomaly-detection-policy.md#multiple-failed-login-attempts)<br />[Atividade administrativas incomuns](anomaly-detection-policy.md#unusual-activities-by-user)<br />[Várias atividades de exclusão de VM](anomaly-detection-policy.md#multiple-delete-vm-activities)<br />[Várias atividades de criação de VM incomuns](anomaly-detection-policy.md#unusual-activities-by-user) (versão prévia) |
| Modelo de política de atividade | Alterações nos recursos do mecanismo de computação<br />Alterações na configuração do StackDriver<br />Alterações nos recursos de armazenamento<br />Alterações na rede virtual privada<br />Logon de um endereço IP com risco |

Para obter mais informações sobre como criar políticas, consulte [criar uma política](control-cloud-apps-with-policies.md#create-a-policy).

## <a name="automate-governance-controls"></a>Automatizar controles de governança

Além de monitorar possíveis ameaças, você pode aplicar e automatizar as seguintes ações de governança GCP para corrigir ameaças detectadas:

| Type | Ação |
| ---- | ---- |
| Governança de usuário | -Exigir que o usuário redefina a senha para o Google (requer a conexão conectada G do Suite vinculado)<br />-Suspender usuário (requer instância do Suite G vinculada conectada)<br />-Notificar o usuário sobre o alerta (por meio do Azure AD)<br />-Exigir que o usuário entre novamente (por meio do Azure AD)<br />– Suspender usuário (por meio do Azure AD) |

Para obter mais informações sobre como corrigir ameaças de aplicativos, consulte [governando aplicativos conectados](governance-actions.md).

## <a name="security-recommendations"></a>Recomendações de Segurança

Cloud App Security fornece uma visão geral da conformidade da configuração da plataforma GCP para todos os seus projetos do GCP com base no benchmark do CIS (Center for Internet Security) para GCP.

Você deve examinar continuamente as recomendações de segurança para avaliar e avaliar o status atual da postura de segurança da sua plataforma e identificar lacunas de configuração importantes. Em seguida, você deve criar um plano para atenuar os problemas em sua plataforma GCP.

Para obter mais informações, [GCP Security Recommendations](security-config-gcp.md).

## <a name="protect-gcp-in-real-time"></a>Proteger GCP em tempo real

Examine nossas práticas recomendadas para [proteger e colaborar com usuários externos](best-practices.md#secure-collaboration-with-external-users-by-enforcing-real-time-session-controls) e [bloquear e proteger o download de dados confidenciais para dispositivos não gerenciados ou arriscados](best-practices.md#block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Como conectar o GCP ao Microsoft Cloud App Security](connect-google-gcp-to-microsoft-cloud-app-security.md)

---
title: Gerenciar a segurança da plataforma de nuvem usada pela sua organização
description: Este tutorial descreve como usar o Microsoft Cloud App Security para proteger suas plataformas de nuvem do Azure, da AWS e da GCP.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 09/17/2020
ms.topic: tutorial
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.suite: ems
ms.openlocfilehash: 069ed5a6182c88bef89c792793c9bab2e0700f56
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90881016"
---
# <a name="tutorial-manage-cloud-platform-security"></a>Tutorial: Gerenciar segurança da plataforma de nuvem

[!INCLUDE [Banner for top of topics](includes/banner.md)]

O trabalho remoto geralmente leva ao uso extensivo de aplicativos de nuvem e plataformas de nuvem para tarefas de negócios comuns e revela a necessidade de proteger os ambientes de nuvem e a adoção de produtos de segurança de nuvem. De acordo com o [modelo de responsabilidade compartilhada](/azure/security/fundamentals/shared-responsibility), uma organização é responsável por gerenciar e proteger a própria plataforma de nuvem: IAM (Gerenciamento de Identidades e Acesso), VM (Máquinas Virtuais) e os recursos de computação delas, dados e armazenamento, recursos de rede e muito mais.

![Proteger seu ambiente multinuvem](media/tutorial-cloud-platform-security.png)

## <a name="how-does-security-posture-management-help"></a>Como o gerenciamento da postura de segurança ajuda?

É crítico ter as ferramentas de segurança apropriadas em vigor para proteger os recursos que talvez não tenham sido adequadamente protegidos. As organizações precisam obter visibilidade sobre a postura dos recursos de nuvem delas, ter funcionalidades de descoberta para conhecer o uso real de cada plataforma, poder monitorar atividades suspeitas, avaliar e examinar configurações e status de conformidade e estarem habilitadas para implantar mecanismos de proteção em tempo real.

O GPSN (Gerenciamento da Postura de Segurança na Nuvem) também se estende para além da postura de segurança de IaaS e PaaS a fim de abranger as configurações de SaaS também. Por exemplo, o repositório GitHub com um nível de acesso público ou aplicativos OAuth que têm acesso aos meus aplicativos SaaS como Office 365, G Suite ou Sales Force. O GPSN de SaaS é um domínio novo e crescente de GPSN, que é uma expansão nativa do produto Cloud App Security.

## <a name="protecting-multiple-clouds-from-a-single-management-portal"></a>Proteger várias nuvens em um único portal de gerenciamento

Muitas organizações usam várias plataformas de nuvem para diferentes finalidades e diferentes escalas e status de implantação. A moderna complexidade delas requer a capacidade de acompanhar o ambiente multinuvem regularmente.  O status de implantação de alguns serviços pode ser alterado ao longo do tempo e não necessariamente com notificação total das alterações feitas nas equipes de segurança. Reunindo esses sinais em um portal, a experiência de administração é simplificada para um gerenciamento de tempo e recursos ainda mais eficiente, tanto para as pessoas que realizam o monitoramento quanto as que usam recursos de nuvem.

A postura de segurança organizacional abrange todas as plataformas de nuvem em uma organização e essa nova funcionalidade foi criada para ser usada por arquitetos de segurança, administradores de segurança central ou analistas de conformidade. Com base nesse recurso, os administradores podem examinar as assinaturas com recursos que não estão em conformidade e promover a correção de cada uma delas pelo proprietário do recurso.

Este tutorial fornece instruções para usar o Microsoft Cloud App Security para proteger suas plataformas de nuvem do Azure, da AWS e da GCP.

> [!div class="checklist"]
>
> * Descobrir recursos, o uso e a TI sombra multinuvem
> * Monitorar atividades e alertas para detectar comportamentos suspeitos entre cargas de trabalho
> * Avaliar e corrigir configurações incorretas e o status de conformidade da plataforma de nuvem
> * Automatizar a proteção e a imposição de políticas para recursos de nuvem em tempo real

## <a name="how-to-secure-your-multi-cloud-environment"></a>Como proteger seu ambiente multinuvem

Para evitar configurações incorretas críticas da plataforma de nuvem, é importante que as organizações tenham visibilidade no nível dos locatários multinuvem sobre os respectivos status de configuração de nuvem e possam aprimorar a postura de segurança delas com base nas recomendações de conformidade e em parâmetros de comparação de segurança. Use o processo a seguir para proteger o ambiente multinuvem da sua organização.

### <a name="phase-1-discover-multi-cloud-resources-usage-and-shadow-it"></a>Fase 1: Descobrir recursos, o uso e a TI sombra multinuvem

**Identificar a postura de segurança**: comece identificando a postura de segurança na nuvem da sua organização executando o Cloud Discovery para ver o que está acontecendo em sua rede e avaliar o uso real dos recursos em suas plataformas de nuvem. Você pode fazer isso [configurando o Cloud Discovery](set-up-cloud-discovery.md) para monitorar e analisar o tráfego de rede no Cloud App Security. A análise de logs de tráfego da Web com o Shadow IT Discovery do Cloud App Security fornece visibilidade aprimorada sobre o uso de recursos de nuvem pelo seu Shadow IT, identificando atividades anormais com o uso do mecanismo de detecção de anomalias do Machine Learning ou de políticas personalizadas que você define:

* **Descobrir**: descubra o uso nas plataformas de nuvem de hospedagem de recursos de sua organização. Por exemplo, avalie o volume real de dados que foram baixados de seus recursos de armazenamento e identifique o uso de recursos suspeitos que possa indicar tentativas de exfiltração dos dados. Da mesma forma, identifique atividades de upload suspeitas que possam indicar uma tentativa de comprometer seu ambiente injetando código mal-intencionado em um destino.
* **Investigue**: use a página **Recursos descobertos** para exibir o acesso a dados entre recursos, incluindo contas de armazenamento, infraestrutura e aplicativos personalizados hospedados no Azure, na AWS e na GCP. Faça perguntas, como: havia um número suspeito de transações para acessar um recurso específico?

    ![Exibir os recursos descobertos](media/tutorial-cloud-platform-security-view-discovered-resources.png)

    Para investigar ainda mais, você pode fazer drill down em cada recurso para ver os tipos de transações que ocorreram, quem o acessou e, em seguida, fazer drill down para investigar ainda mais os usuários.

    ![Investigar recursos descobertos](media/tutorial-cloud-platform-security-investigate-discovered-resources.png)

### <a name="phase-2-monitor-activities-and-alerts-to-detect-suspicious-behavior-across-workloads"></a>Fase 2: Monitorar atividades e alertas para detectar comportamentos suspeitos entre cargas de trabalho

Acompanhe atividades suspeitas que possam indicar uma violação, como uma alteração de função IAM (Gerenciamento de Identidades e Acesso) ou alteração de configuração do CloudTrail. Por exemplo, use nosso **modelo de política** de [buckets AWS S3 publicamente acessíveis](policy-template-reference.md) predefinido para acompanhar as alterações de configuração do bucket S3.

O monitoramento de logs de auditoria para alterações suspeitas é um ótimo lugar para aplicar ferramentas de detecção de anomalias, gerando alertas sobre possíveis violações por meio da identificação de várias tentativas de logon com falha ou várias atividades de VM excluídas em combinação com um cenário de viagem impossível.

![Exibir alertas](media/tutorial-cloud-platform-security-view-alerts.png)

Use o que você aprender com os alertas para ajustar as detecções de atividade do usuário a fim de identificar comprometimentos verdadeiros e reduzir o excesso de alertas resultantes do manuseio de grandes volumes de detecções de falsos positivos. Considere ajustar os seguintes parâmetros de política:

* Configure [intervalos de endereços IP](tutorial-suspicious-activity.md#phase-1-configure-ip-address-ranges)
* Ajuste [políticas de detecção de anomalias](tutorial-suspicious-activity.md#phase-2-tune-anomaly-detection-policies), como atividades administrativas incomuns, atividades de download de vários arquivos incomuns, atividade de ransomware e atividades de entrada com falha em plataformas de nuvem
* Ajuste as [políticas de detecção de anomalias de descoberta de nuvem](tutorial-suspicious-activity.md#phase-3-tune-cloud-discovery-anomaly-detection-policies) adequando o monitoramento de uso e a sensibilidade dos alertas
* Ajuste [políticas de atividade e políticas de detecção baseadas em regras](tutorial-suspicious-activity.md#phase-4-tune-rule-based-detection-activity-policies), incluindo buckets AWS S3 publicamente acessíveis
* Configure [alertas](tutorial-suspicious-activity.md#phase-5-configure-alerts)
* [Investigar e corrigir](tutorial-suspicious-activity.md#phase-6-investigate-and-remediate)

### <a name="phase-3-assess-and-remediate-cloud-platform-misconfigurations-and-compliance-status"></a>Fase 3: Avaliar e corrigir configurações incorretas e o status de conformidade da plataforma de nuvem

Avalie o status de sua conformidade de segurança por locatário, em todas as plataformas de nuvem pública, incluindo assinaturas do Azure, contas da AWS e projetos GCP. As avaliações permitem que você comunique lacunas de configuração e detalhes de recomendação para proprietários de recursos e promova a correção.

Cada plataforma de nuvem fornece uma lista de recursos configurados incorretamente com base nas melhores práticas de conformidade regulatória.

Os arquitetos de nuvem ou analistas de conformidade podem avaliar as lacunas de configuração de cada ambiente de nuvem e promover a correção por proprietários de recursos. Por exemplo, as recomendações podem ser avaliadas por:

* Assinatura para diferenciar entre ambientes de produção e não produção
* Gravidade para identificar recomendações de alta severidade que geralmente têm diferentes SLA e processos relativos a recomendações de baixa severidade

Para recomendações de configuração de segurança do Azure, oferecemos recomendações do locatário inteiro do Azure e todas as assinaturas dele com base nas melhores práticas da Central de Segurança do Azure. Selecionar uma recomendação direciona você à página de recomendações na Central de Segurança do Azure, em que você pode ver mais detalhes sobre ela e usá-la para promover a correção pelo proprietário da assinatura. Algumas recomendações têm opções de **Correção Rápida** para corrigir o problema. Para obter mais informações sobre as recomendações de segurança do Azure, confira [Configuração de segurança para o Azure](security-config-azure.md).

![Exibir recomendações do Azure](media/tutorial-cloud-platform-security-view-azure-recommendations.png)

Para recomendações de configuração de segurança da AWS, você pode selecionar uma recomendação para fazer drill down dos recursos afetados. Por exemplo, a recomendação 2.9 da AWS CIS "Verifique se o log de fluxo VPC está habilitado em todos os VPC" revela recursos que não têm o log de VPC habilitado. Os detalhes incluem os nomes do VPC, a conta na qual o recurso está hospedado e a região. Você pode selecionar o link da AWS para exibir a localização relevante e alterar as configurações relacionadas na AWS para cumprir a recomendação. Para obter mais informações sobre a Configuração de Segurança para a AWS, confira [Configuração de segurança para a AWS](security-config-aws.md).

![Exibir recomendações da AWS](media/tutorial-cloud-platform-security-view-aws-recommendations.png)

Para recomendações de configuração de segurança da GCP, a seleção em uma recomendação revela informações detalhadas da recomendação e as etapas de correção para ajudar você a entender melhor e a avaliar o impacto e o esforço da correção do problema. Em seguida, você pode selecionar o link do Centro de Comando de Segurança da GCP para corrigir a localização na plataforma. Para obter mais informações sobre as recomendações da GCP, confira [Configuração de segurança para a GCP](security-config-gcp.md).

![Exibir recomendações da GCP](media/tutorial-cloud-platform-security-view-gcp-recommendations.png)

### <a name="phase-4-automate-protection-and-policy-enforcement-for-cloud-resources-in-real-time"></a>Fase 4: Automatizar a proteção e a imposição de políticas para recursos de nuvem em tempo real

Proteja os recursos da sua organização contra vazamentos e roubo de dados em tempo real aplicando políticas de controle de acesso e de sessão. Para obter mais informações, confira [Proteger aplicativos em tempo real](tutorial-proxy.md).

* Impeça a exfiltração dos dados [bloqueando downloads](session-policy-aad.md#block-download) para dispositivos não gerenciados ou arriscados. Proteja o download em uma sessão arriscada.
* Impeça o [upload de arquivos mal-intencionados](session-policy-aad.md#block-malware-on-upload) para suas plataformas de nuvem e bloqueie o acesso a usuários específicos com base em muitos fatores de risco.

![Especificar a ação de correção de política](media/tutorial-cloud-platform-security-remediation.png)

## <a name="see-also"></a>Consulte Também

> [!div class="nextstepaction"]
> [Proteja seu ambiente do Azure](protect-azure.md)

> [!div class="nextstepaction"]
> [Proteja seu ambiente da AWS](protect-aws.md)

> [!div class="nextstepaction"]
> [Proteja seu ambiente da GCP](protect-gcp.md)

[!INCLUDE [Open support ticket](includes/support.md)]

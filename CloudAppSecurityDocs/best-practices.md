---
title: Melhores práticas para proteger sua organização
description: Este artigo fornece um conjunto de melhores práticas para proteger sua organização.
ms.date: 10/24/2019
ms.topic: quickstart
ms.openlocfilehash: b0639bb79c9aed35086c3e8dea084f1e1c823628
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96313637"
---
# <a name="cloud-app-security-best-practices"></a>práticas recomendadas do Cloud App Security

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Este artigo fornece melhores práticas para proteger sua organização usando o Microsoft Cloud App Security. Elas surgiram de nossa experiência com o Cloud App Security e das experiências de clientes como você.

As melhores práticas abordadas neste artigo incluem:

> [!div class="checklist"]
>
> * [Descobrir e avaliar aplicativos de nuvem](#discover-and-assess-cloud-apps)
> * [Aplicar políticas de governança de nuvem](#apply-cloud-governance-policies)
> * [Limitar a exposição de dados compartilhados e impor políticas de colaboração](#limit-exposure-of-shared-data-and-enforce-collaboration-policies)
> * [Descobrir, classificar, rotular e proteger dados regulamentados e confidenciais armazenados na nuvem](#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)
> * [Impor políticas de conformidade e DLP (proteção contra perda de dados) para dados armazenados na nuvem](#enforce-dlp-and-compliance-policies-for-data-stored-in-the-cloud)
> * [Bloquear e proteger o download de dados confidenciais para dispositivos não gerenciados ou arriscados](#block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices)
> * [Proteger a colaboração com usuários externos ao impor controles de sessão em tempo real](#secure-collaboration-with-external-users-by-enforcing-real-time-session-controls)
> * [Detectar ameaças à nuvem, contas comprometidas, pessoas mal-intencionadas e ransomware](#detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware)
> * [Usar a trilha de auditoria das atividades para investigações forenses](#use-the-audit-trail-of-activities-for-forensic-investigations)
> * [Proteger serviços de IaaS (infraestrutura como serviço) e aplicativos personalizados](#secure-iaas-services-and-custom-apps)

## <a name="discover-and-assess-cloud-apps"></a>Descobrir e avaliar aplicativos de nuvem

A integração do Cloud App Security com o Microsoft Defender para Ponto de Extremidade proporciona a você a capacidade de usar o Cloud Discovery fora da rede corporativa ou de gateways da Web seguros. Com as informações combinadas de usuário e dispositivo, é possível identificar usuários ou dispositivos suspeitos, ver quais aplicativos eles estão usando e investigar ainda mais no portal do Defender para Ponto de Extremidade.

**Melhor prática**: Habilitar Shadow IT Discovery usando o Defender para Ponto de Extremidade  
**Detalhe**: o Cloud Discovery analisa os logs de tráfego coletados pelo Defender para Ponto de Extremidade e avalia os aplicativos identificados no catálogo de aplicativos na nuvem para fornecer informações de conformidade e segurança. Ao configurar o Cloud Discovery, você obterá visibilidade do uso da nuvem, da TI Sombra e do monitoramento contínuo dos aplicativos não sancionados utilizados por seus usuários.  
**Para saber mais**:

* [Integração do Defender para Ponto de Extremidade com o Cloud App Security](mde-integration.md)
* [Configurar Cloud Discovery](set-up-cloud-discovery.md)
* [Descobrir e gerenciar a TI sombra na sua rede](tutorial-shadow-it.md)

---

**Melhor prática**: configurar políticas de Descoberta de Aplicativos para identificar proativamente aplicativos suspeitos, fora de conformidade e em alta  
**Detalhes**: as políticas de Descoberta de aplicativos facilitam o controle dos aplicativos significativos descobertos em sua organização para ajudar você a gerenciá-los com eficiência. Crie políticas para receber alertas ao detectar novos aplicativos identificados como suspeitos, fora de conformidade, em alta ou de grande volume.  
**Para saber mais**:

* [Políticas do Cloud Discovery](cloud-discovery-policies.md)
* [Política de detecção de anomalias do Cloud Discovery](cloud-discovery-anomaly-detection-policy.md)
* [Obter análise comportamental e detecção de anomalias instantaneamente](anomaly-detection-policy.md)

---

**Melhor prática**: gerenciar aplicativos OAuth autorizados por seus usuários  
**Detalhe**: vários usuários concedem casualmente permissões OAuth para que aplicativos de terceiros acessem suas informações de conta e, com isso, também fornecem inadvertidamente acesso a seus dados em outros aplicativos de nuvem. Normalmente, a TI não tem visibilidade desses aplicativos, dificultando a avaliação do risco de segurança de um aplicativo em relação ao benefício de produtividade que ele oferece.

O Cloud App Security fornece a capacidade de investigar e monitorar as permissões de aplicativos que seus usuários concederam. Você pode usar essas informações para identificar um aplicativo potencialmente suspeito e, se determinar que ele é suspeito, será possível proibir o acesso a ele.  
**Para saber mais**:

* [Gerenciar aplicativos OAuth](manage-app-permissions.md)
* [Políticas de aplicativo OAuth](app-permission-policy.md)

---
---
---
---

## <a name="apply-cloud-governance-policies"></a>Aplicar políticas de governança de nuvem

**Melhor prática**: marcar aplicativos e exportar scripts de bloco  
**Detalhe**: depois de examinar a lista de aplicativos descobertos em sua organização, você pode proteger seu ambiente contra o uso indesejado do aplicativo. É possível aplicar a marca **Sancionado** a aplicativos aprovados por sua organização e a marca **Não sancionado** a aplicativos reprovados. Você pode monitorar aplicativos não sancionados usando filtros de descoberta ou exportar um script para bloquear aplicativos não sancionados usando seus dispositivos de segurança locais. O uso de marcas e scripts de exportação permite organizar seus aplicativos e proteger seu ambiente para permitir o acesso apenas aos aplicativos seguros.  
**Para saber mais**:

* [Controlar aplicativos descobertos](governance-discovery.md)

---
---
---
---

## <a name="limit-exposure-of-shared-data-and-enforce-collaboration-policies"></a>Limitar a exposição de dados compartilhados e impor políticas de colaboração

**Melhor prática**: Conectar o Office 365  
**Detalhe**: conectar o Office 365 ao Cloud App Security proporciona visibilidade imediata quanto às atividades dos usuários e aos arquivos que eles acessam, além de fornecer ações de governança para o Office 365, SharePoint, OneDrive, Teams, Power BI, Exchange e Dynamics.  
**Para saber mais**:

* [Conectar aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)
* [Conectar o Office 365 ao Microsoft Cloud App Security](connect-office-365-to-microsoft-cloud-app-security.md)

---

**Melhor prática**: conectar aplicativos de terceiros  
**Detalhe**: a conexão de aplicativos de terceiros ao Cloud App Security disponibiliza insights aprimorados sobre as atividades dos usuários, detecção de ameaças e recursos de governança. Há suporte para as seguintes APIs de aplicativos de terceiros: [AWS (Amazon Web Services)](connect-aws-to-microsoft-cloud-app-security.md), [Box](connect-box-to-microsoft-cloud-app-security.md), [Dropbox](connect-dropbox-to-microsoft-cloud-app-security.md), [G Suite](connect-google-apps-to-microsoft-cloud-app-security.md), [Okta](connect-okta-to-microsoft-cloud-app-security.md), [Salesforce](connect-salesforce-to-microsoft-cloud-app-security.md), [ServiceNow](connect-servicenow-to-microsoft-cloud-app-security.md), [WebEx](connect-webex-to-microsoft-cloud-app-security.md) e [Workday](connect-workday-to-microsoft-cloud-app-security.md).  
**Para saber mais**:

* [Conectar aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)

---

**Melhor prática**: examinar a exposição dos dados da organização  
**Detalhe**: use os relatórios de exposição de arquivos para obter visibilidade de como os usuários estão compartilhando arquivos com aplicativos de nuvem. Os seguintes relatórios estão disponíveis e podem ser exportados para análise adicional em ferramentas como o Microsoft Power BI:

* **Visão geral do compartilhamento de dados**: lista os arquivos por permissões de acesso armazenadas em cada um de seus aplicativos de nuvem
* **Compartilhamento de saída por domínio**: lista os domínios com os quais os arquivos corporativos são compartilhados por seus funcionários
* **Proprietários de arquivos compartilhados**: lista os usuários que estão compartilhando arquivos corporativos com o mundo externo  
**Para saber mais**:

* [Gerar relatórios de gerenciamento de dados](built-in-reports.md)

---

**Melhor prática**: criar políticas para remover o compartilhamento com contas pessoais  
**Detalhe**: conectar o Office 365 ao Cloud App Security proporciona visibilidade imediata quanto às atividades dos usuários e aos arquivos que eles acessam, além de fornecer ações de governança para o Office 365, SharePoint, OneDrive, Teams, Power BI, Exchange e Dynamics.  
**Para saber mais**:

* [Controlando aplicativos conectados](governance-actions.md)

---
---
---
---

## <a name="discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud"></a>Descobrir, classificar, rotular e proteger dados regulamentados e confidenciais armazenados na nuvem

**Melhor prática**: integração à Proteção de Informações do Azure  
**Detalhe**: a integração com a proteção de informações do Azure proporciona a capacidade de aplicar automaticamente rótulos de classificação e, como opção, adicionar a proteção de criptografia. Depois que a integração for ativada, você poderá aplicar rótulos como uma ação de governança, exibir arquivos por classificação, investigar arquivos por nível de classificação e criar políticas granulares para garantir que os arquivos classificados sejam manuseados corretamente. Se você não ativar a integração, não poderá se beneficiar da capacidade de examinar, rotular e criptografar automaticamente os arquivos na nuvem.  
**Para saber mais**:

* [Integração à Proteção de Informações do Azure](azip-integration.md)
* [Tutorial: Aplicar automaticamente os rótulos de classificação da Proteção de Informações do Azure](use-case-information-protection.md)

---

**Melhor prática**: criar políticas de exposição de dados  
**Detalhe**: use políticas de arquivo para detectar o compartilhamento de informações e verificar se há informações confidenciais em seus aplicativos de nuvem. Crie as seguintes políticas de arquivo para receber alertas quando forem detectadas exposições de dados:

* Arquivos compartilhados externamente contendo dados confidenciais
* Arquivos compartilhados externamente e rotulados como **Confidenciais**
* Arquivos compartilhados com domínios não autorizados
* Proteger arquivos confidenciais em aplicativos SaaS

**Para saber mais**:

* [Inspeção de conteúdo](content-inspection.md)
* [Políticas de arquivos](data-protection-policies.md)
* [Políticas de proteção de informações](policies-information-protection.md)

---

**Melhor prática**: examinar relatórios na página **Arquivos**  
**Detalhe**: depois que você conecta vários aplicativos SaaS usando conectores, o Cloud App Security examina os arquivos armazenados por esses aplicativos. Além disso, toda vez que um arquivo é modificado, ele é examinado novamente. Você pode usar a página **Arquivos** para reconhecer e investigar os tipos de dados armazenados em seus aplicativos de nuvem. Para ajudar na investigação, você pode filtrar por domínios, grupos, usuários, data de criação, extensão, nome e tipo de arquivo, ID de arquivo, rótulo de classificação e muito mais. O uso desses filtros coloca você no controle de como investigar os arquivos para garantir que nenhum dos seus dados esteja em risco. Depois de entender melhor como seus dados são usados, você pode criar políticas para examinar se há conteúdo confidencial nesses arquivos.  
**Para saber mais**:

* [Conectar aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)
* [Filtros de arquivos](file-filters.md)
* [Inspeção de conteúdo](content-inspection.md)

---
---
---
---

## <a name="enforce-dlp-and-compliance-policies-for-data-stored-in-the-cloud"></a>Impor políticas de conformidade e DLP (proteção contra perda de dados) para dados armazenados na nuvem

**Melhor prática**: proteger dados confidenciais do compartilhamento com usuários externos  
**Detalhe**: crie uma política de arquivo que detecte quando um usuário tenta compartilhar um arquivo com o rótulo de classificação **Confidencial** com alguém externo à sua organização e configure a ação de governança para remover usuários externos. Essa política garante que seus dados confidenciais não saiam da sua organização e que os usuários externos não possam acessá-los.  
**Para saber mais**:

* [Controlando aplicativos conectados](governance-actions.md)

---
---
---
---

## <a name="block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices"></a>Bloquear e proteger o download de dados confidenciais para dispositivos não gerenciados ou arriscados

**Melhor prática**: gerenciar e controlar o acesso a dispositivos de alto risco  
**Detalhe**: use Controle de Aplicativos de Acesso Condicional para definir controles em seus aplicativos SaaS. Você pode criar políticas de sessão para monitorar suas sessões de alto risco e de baixa confiança. Da mesma forma, é possível criar políticas de sessão para bloquear e proteger downloads feitos por usuários que estejam tentando acessar dados confidenciais em dispositivos suspeitos ou não gerenciados. Se você não criar políticas de sessão para monitorar sessões de alto risco, perderá a capacidade de bloquear e proteger os downloads no cliente Web, bem como a capacidade de monitorar a sessão de baixa confiança tanto na Microsoft quanto em aplicativos de terceiros.  
**Para saber mais**:

* [Proteger aplicativos com o Controle de Aplicativo de Acesso Condicional do Microsoft Cloud App Security](proxy-intro-aad.md)
* [Políticas de sessão](session-policy-aad.md)

---
---
---
---

## <a name="secure-collaboration-with-external-users-by-enforcing-real-time-session-controls"></a>Proteger a colaboração com usuários externos ao impor controles de sessão em tempo real

**Melhor prática**: monitorar sessões com usuários externos usando o Controle de Aplicativos de Acesso Condicional  
**Detalhe**: para proteger a colaboração em seu ambiente, você pode criar uma política de sessão para monitorar sessões entre seus usuários internos e externos. Isso não apenas proporciona a capacidade de monitorar a sessão entre os usuários (e notificá-los de que suas atividades de sessão estão sendo monitoradas), como também permite que você limite atividades específicas. Ao criar políticas de sessão para monitorar atividades, você pode escolher os aplicativos e usuários que deseja monitorar.  
**Para saber mais**:

* [Proteger aplicativos com o Controle de Aplicativo de Acesso Condicional do Microsoft Cloud App Security](proxy-intro-aad.md)
* [Políticas de sessão](session-policy-aad.md)

---
---
---
---

## <a name="detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware"></a>Detectar ameaças à nuvem, contas comprometidas, pessoas mal-intencionadas e ransomware

**Melhor prática**: ajustar políticas de anomalias, definir intervalos de IP, enviar comentários para alertas  
**Detalhe**: as políticas de detecção de anomalias fornecem UEBA (análise comportamental de usuários e entidades) e ML (aprendizado de máquina) prontos para uso a fim de que você possa executar imediatamente a detecção avançada de ameaças em seu ambiente de nuvem.

As políticas de detecção de anomalias são acionadas quando há atividades incomuns executadas pelos usuários em seu ambiente. O Cloud App Security monitora continuamente as atividades dos usuários e usa UEBA e ML para aprender e reconhecer o comportamento *normal* deles. Você pode ajustar as configurações de política para atender aos requisitos de sua organização, por exemplo, é possível definir a sensibilidade da política ou o escopo de uma política para um grupo específico.

* **Ajustar e definir o escopo das Políticas de Detecção de Anomalias**: por exemplo, para reduzir o número de falsos positivos no alerta de viagem impossível, você pode definir o controle deslizante de sensibilidade da política como baixo. Se a sua organização tiver usuários que são viajantes corporativos frequentes, você poderá adicioná-los a um grupo e selecionar esse grupo no escopo da política.

* **Definir Intervalos de IP**: o Cloud App Security pode identificar endereços IP conhecidos depois que os intervalos de endereços IP são definidos. Com os intervalos de endereços IP configurados, você pode marcar, categorizar e personalizar a maneira como os logs e alertas são exibidos e investigados. Adicionar intervalos de endereços IP ajuda a reduzir as detecções de falsos positivos e a aumentar a precisão dos alertas. Se optar por não adicionar os endereços IP, você poderá ter um maior número de possíveis falsos positivos e alertas a serem investigados.

* **Enviar Comentários para alertas**

    Ao descartar ou resolver alertas, lembre-se de enviar comentários com o motivo pelo qual você ignorou o alerta ou como ele foi resolvido. Essas informações auxiliam o Cloud App Security a melhorar nossos alertas e a reduzir os falsos positivos.

**Para saber mais**:

* [Obter análise comportamental e detecção de anomalias instantaneamente](anomaly-detection-policy.md)
* [Trabalhar com intervalos de IP e marcas](ip-tags.md)
* [Monitorar alertas no Cloud App Security](monitor-alerts.md)

---

**Melhor prática**: detectar atividade de locais ou países inesperados  
**Detalhe**: crie uma política de atividade para notificar você quando os usuários se conectarem de locais ou países/regiões inesperados. Essas notificações podem enviar alertas sobre sessões possivelmente comprometidas em seu ambiente para que você possa detectar e corrigir ameaças antes que elas ocorram.  
**Para saber mais**:

* [Políticas de proteção contra ameaças](policies-threat-protection.md)

---

**Melhor prática**: criar políticas de aplicativo OAuth  
**Detalhe**: crie uma política de aplicativo OAuth para notificar você quando um aplicativo OAuth atender a determinados critérios. Por exemplo, você pode optar por ser notificado quando um aplicativo específico que requer um nível de permissão alto for acessado por mais de 100 usuários.  
**Para saber mais**:

* [Políticas de aplicativo OAuth](app-permission-policy.md)

---
---
---
---

## <a name="use-the-audit-trail-of-activities-for-forensic-investigations"></a>Usar a trilha de auditoria das atividades para investigações forenses

**Melhor prática**: usar a trilha de auditoria das atividades ao investigar alertas  
**Detalhe**: os alertas são disparados quando as atividades de usuário, administrador ou entrada não estão em conformidade com suas políticas. É importante investigar alertas para reconhecer se há uma possível ameaça em seu ambiente.

Você pode investigar um alerta selecionando-o na página **Alertas** e examinando a trilha de auditoria das atividades relacionadas a ele. A trilha de auditoria proporciona visibilidade das atividades do mesmo tipo, usuário, endereço IP e local, a fim de fornecer a história geral de um alerta. Se um alerta exigir mais investigação, crie um plano para resolver esses alertas em sua organização.

Ao ignorar alertas, é importante investigar e entender por que eles não têm importância ou se são falsos positivos. Caso haja um alto volume dessas atividades, pode ser conveniente analisar e ajustar a política que dispara o alerta.  
**Para saber mais**:

* [Atividades](activity-filters.md)

---
---
---
---

## <a name="secure-iaas-services-and-custom-apps"></a>Proteger serviços de IaaS (infraestrutura como serviço) e aplicativos personalizados

**Melhor prática**: conectar o Azure, AWS e GCP  
**Detalhe**: conectar cada uma dessas plataformas de nuvem ao Cloud App Security ajuda a melhorar os recursos de detecções de ameaças. Ao monitorar as atividades administrativas e de entrada desses serviços, você pode detectar e ser notificado sobre possíveis ataques de força bruta, uso mal-intencionado de uma conta de usuário com privilégios e outras ameaças em seu ambiente. Por exemplo, você pode identificar riscos como exclusões incomuns de VMs ou até mesmo atividades de representação nesses aplicativos.  
**Para saber mais**:

* [Conectar o Azure ao Microsoft Cloud App Security](connect-azure-to-microsoft-cloud-app-security.md)
* [Conectar o AWS ao Microsoft Cloud App Security](connect-aws-to-microsoft-cloud-app-security.md)
* [Conectar o GCP ao Microsoft Cloud App Security (versão prévia)](connect-google-gcp-to-microsoft-cloud-app-security.md)

---

**Melhor prática**: examinar as avaliações de configuração de segurança do Azure, AWS e GCP  
**Detalhe**: a integração com a Central de Segurança do Azure fornece uma avaliação da configuração de segurança do seu ambiente no Azure. Essa avaliação disponibiliza recomendações para controles de segurança e configurações ausentes. A revisão dessas recomendações ajuda a identificar anomalias e possíveis vulnerabilidades no ambiente e a navegar diretamente para o local relevante no portal de segurança do Azure a fim de resolvê-las.

O AWS e o GCP proporcionam a capacidade de obter visibilidade das recomendações de configurações de segurança sobre como melhorar a segurança na nuvem.

Use essas recomendações para monitorar o status de conformidade e a postura de segurança de toda a sua organização, incluindo assinaturas do Azure, contas do AWS e projetos do GCP.  
**Para saber mais**:

* [Configuração de segurança para o Azure](security-config.md)
* [Configuração de segurança para o AWS](security-config-aws.md)
* [Configuração de segurança para o GCP](security-config-gcp.md)

---

**Melhor prática**: integrar aplicativos personalizados  
**Detalhe**: para obter visibilidade adicional das atividades de seus aplicativos de linha de negócios, você pode integrar aplicativos personalizados ao Cloud App Security. Depois que os aplicativos personalizados forem configurados, você verá informações sobre como usá-los, os endereços IP em que são usados e a quantidade de tráfego que entra e sai do aplicativo.

Além disso, você poderá integrar um aplicativo personalizado no Controle de Aplicativos de Acesso Condicional para monitorar as sessões de baixa confiança.  
**Para saber mais**:

* [Adicionar aplicativos personalizados ao Cloud Discovery](cloud-discovery-custom-apps.md)
* [Integrar e implantar o Controle de Aplicativos de Acesso Condicional em qualquer aplicativo](proxy-deployment-any-app.md)

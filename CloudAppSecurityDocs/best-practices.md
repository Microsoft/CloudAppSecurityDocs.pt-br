---
title: Práticas recomendadas para proteger sua organização-Cloud App Security
description: Este artigo fornece um conjunto de práticas recomendadas para proteger sua organização.
author: shsagir
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: best-practice
ms.date: 10/24/2019
ms.collection: M365-security-compliance
ms.openlocfilehash: e90a340c206c0bfb1c01542dd184664d1fe87dfe
ms.sourcegitcommit: 6eff466c7a6817b14a60d8c3b2c201c7ae4c2e2c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74143463"
---
# <a name="cloud-app-security-best-practices"></a>Práticas recomendadas de Cloud App Security

*Aplica-se ao: Microsoft Cloud App Security*

Este artigo fornece as práticas recomendadas para proteger sua organização usando Microsoft Cloud App Security. Essas práticas recomendadas são de nossa experiência com Cloud App Security e as experiências de clientes como você.

As práticas recomendadas abordadas neste artigo incluem:

> [!div class="checklist"]
> * [Descubra e avalie aplicativos de nuvem](#discover-and-assess-cloud-apps)
> * [Aplicar políticas de governança de nuvem](#apply-cloud-governance-policies)
> * [Limitar a exposição de dados compartilhados e impor políticas de colaboração](#limit-exposure-of-shared-data-and-enforce-collaboration-policies)
> * [Descobrir, classificar, rotular e proteger dados regulamentados e confidenciais armazenados na nuvem](#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)
> * [Impor políticas de conformidade e DLP para dados armazenados na nuvem](#enforce-dlp-and-compliance-policies-for-data-stored-in-the-cloud)
> * [Bloquear e proteger o download de dados confidenciais para dispositivos não gerenciados ou arriscados](#block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices)
> * [Colaboração segura com usuários externos impondo controles de sessão em tempo real](#secure-collaboration-with-external-users-by-enforcing-real-time-session-controls)
> * [Detecte ameaças à nuvem, contas comprometidas, pessoas mal-intencionadas e ransomware](#detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware)
> * [Use a trilha de auditoria das atividades para investigações forenses](#use-the-audit-trail-of-activities-for-forensic-investigations)
> * [Proteger serviços de IaaS e aplicativos personalizados](#secure-iaas-services-and-custom-apps)

## <a name="discover-and-assess-cloud-apps"></a>Descobrir e avaliar aplicativos de nuvem

A integração do Cloud App Security à proteção avançada contra ameaças do Microsoft defender (Microsoft defender ATP) oferece a capacidade de usar Cloud Discovery além da rede corporativa ou de gateways Web seguros. Com as informações de usuário e computador combinadas, você pode identificar usuários ou máquinas arriscados, ver quais aplicativos eles estão usando e investigar ainda mais no portal do Microsoft defender ATP.

**Prática recomendada**: habilitar Shadow it Discovery usando o Microsoft defender ATP  
**Detalhe**: Cloud Discovery analisa os logs de tráfego coletados pelo Microsoft defender ATP e avalia os aplicativos identificados no catálogo de aplicativos de nuvem para fornecer informações de conformidade e segurança. Ao configurar Cloud Discovery, você obterá visibilidade do uso da nuvem, da ti de sombra e do monitoramento contínuo dos aplicativos não aprovados que estão sendo usados por seus usuários.  
**Para obter mais informações**:

* [Integração do Microsoft defender ATP com o Cloud App Security](wdatp-integration.md)
* [Configurar o Cloud Discovery](set-up-cloud-discovery.md)
* [Descobrir e gerenciar o TI sombra na sua rede](tutorial-shadow-it.md)

---

**Prática recomendada**: configurar políticas de descoberta de aplicativo para identificar proativamente aplicativos arriscados, não compatíveis e de tendência  
**Detalhes**: as políticas de descoberta de aplicativos facilitam o controle dos aplicativos descobertos significativos em sua organização para ajudá-lo a gerenciar esses aplicativos com eficiência. Crie políticas para receber alertas ao detectar novos aplicativos que são identificados como arriscados, sem conformidade, tendência ou alto volume.  
**Para obter mais informações**:

* [Políticas do Cloud Discovery](cloud-discovery-policies.md)
* [Política de detecção de anomalias do Cloud Discovery](cloud-discovery-anomaly-detection-policy.md)
* [Obtenha análise comportamental e detecção de anomalias instantâneas](anomaly-detection-policy.md)

---

**Prática recomendada**: gerenciar aplicativos OAuth que são autorizados por seus usuários  
**Detalhe**: muitos usuários concedem casualmente permissões OAuth a aplicativos de terceiros para acessar suas informações de conta e, ao fazer isso, também fornecem acesso inadvertidamente a seus dados em outros aplicativos de nuvem. Normalmente, não tem visibilidade nesses aplicativos, dificultando a pesar o risco de segurança de um aplicativo contra o benefício de produtividade que ele fornece.

Cloud App Security fornece a capacidade de investigar e monitorar as permissões de aplicativo concedidas pelos usuários. Você pode usar essas informações para identificar um aplicativo potencialmente suspeito e, se determinar que ele é arriscado, você poderá proibir o acesso a ele.  
**Para obter mais informações**:

* [Gerenciar aplicativos OAuth](manage-app-permissions.md)
* [Políticas de aplicativo OAuth](app-permission-policy.md)

---
---
---
---

## <a name="apply-cloud-governance-policies"></a>Aplicar políticas de governança de nuvem

**Prática recomendada**: marcar aplicativos e exportar scripts de bloco  
**Detalhe**: depois de examinar a lista de aplicativos descobertos em sua organização, você pode proteger seu ambiente contra o uso indesejado do aplicativo. Você pode aplicar a **marcação aprovada a aplicativos** que são aprovados pela sua organização e pela **marca não** aprovada para aplicativos que não são. Você pode monitorar aplicativos não aprovados usando filtros de descoberta ou exportar um script para bloquear aplicativos não aprovados usando seus dispositivos de segurança locais. O uso de marcas e scripts de exportação permite organizar seus aplicativos e proteger seu ambiente apenas para permitir que os aplicativos seguros sejam acessados.  
**Para obter mais informações**:

* [Controlar aplicativos descobertos](governance-discovery.md)

---
---
---
---

## <a name="limit-exposure-of-shared-data-and-enforce-collaboration-policies"></a>Limitar a exposição de dados compartilhados e impor políticas de colaboração

**Prática recomendada**: conectar o Office 365  
**Detalhe**: conectar o Office 365 ao Cloud app Security fornece visibilidade imediata das atividades dos usuários, arquivos que estão acessando e fornece ações de governança para o Office 365, SharePoint, onedrive, Teams, Power bi, Exchange e Dynamics.  
**Para obter mais informações**:

* [Conectar aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)
* [Conectar o Office 365 ao Microsoft Cloud App Security](connect-office-365-to-microsoft-cloud-app-security.md)

---

**Prática recomendada**: conectar aplicativos de terceiros  
**Detalhe**: a conexão de aplicativos de terceiros ao Cloud app Security oferece informações aprimoradas sobre as atividades dos usuários, a detecção de ameaças e os recursos de governança. Há suporte para as seguintes APIs de aplicativo de terceiros: [Amazon Web Services (AWS)](connect-aws-to-microsoft-cloud-app-security.md), [Box](connect-box-to-microsoft-cloud-app-security.md), [Dropbox](connect-dropbox-to-microsoft-cloud-app-security.md), [G Suite](connect-google-apps-to-microsoft-cloud-app-security.md), [Okta](connect-okta-to-microsoft-cloud-app-security.md), [Salesforce](connect-salesforce-to-microsoft-cloud-app-security.md), [ServiceNow](connect-servicenow-to-microsoft-cloud-app-security.md), [WebEx](connect-webex-to-microsoft-cloud-app-security.md)e [workday](connect-workday-to-microsoft-cloud-app-security.md).  
**Para obter mais informações**:

* [Conectar aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)

---

**Prática recomendada**: revise a exposição de dados da sua organização  
**Detalhe**: Use os relatórios de exposição de arquivo para obter visibilidade sobre como os usuários estão compartilhando arquivos com aplicativos de nuvem. Os relatórios a seguir estão disponíveis e podem ser exportados para o para análise adicional em ferramentas como o Microsoft Power BI:

* **Visão geral do compartilhamento de dados**: lista os arquivos por permissões de acesso armazenadas em cada um de seus aplicativos de nuvem
* **Compartilhamento de saída por domínio**: lista os domínios com os quais os arquivos corporativos são compartilhados por seus funcionários
* **Proprietários de arquivos compartilhados**: lista os usuários que estão compartilhando arquivos corporativos com o mundo exterior  
**Para obter mais informações**:

* [Gerar relatórios de gerenciamento de dados](built-in-reports.md)

---

**Prática recomendada**: criar políticas para remover o compartilhamento com contas pessoais  
**Detalhe**: conectar o Office 365 ao Cloud app Security fornece visibilidade imediata das atividades dos usuários, arquivos que estão acessando e fornece ações de governança para o Office 365, SharePoint, onedrive, Teams, Power bi, Exchange e Dynamics.  
**Para obter mais informações**:

* [Controlando aplicativos conectados](governance-actions.md)

---
---
---
---

## <a name="discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud"></a>Descobrir, classificar, rotular e proteger dados regulamentados e confidenciais armazenados na nuvem

**Prática recomendada**: integrar com a proteção de informações do Azure  
**Detalhe**: a integração com a proteção de informações do Azure oferece a capacidade de aplicar automaticamente rótulos de classificação e, opcionalmente, adicionar proteção de criptografia. Depois que a integração é ativada, você pode aplicar rótulos como uma ação de governança, exibir arquivos por classificação, investigar arquivos por nível de classificação e criar políticas granulares para garantir que os arquivos classificados estejam sendo tratados corretamente. Se você não ativar a integração, não poderá se beneficiar da capacidade de verificar, rotular e criptografar automaticamente os arquivos na nuvem.  
**Para obter mais informações**:

* [Integração à Proteção de Informações do Azure](azip-integration.md)
* [Tutorial: aplicar automaticamente rótulos de classificação da proteção de informações do Azure](use-case-information-protection.md)

---

**Prática recomendada**: criar políticas de exposição de dados  
**Detalhe**: Use políticas de arquivo para detectar o compartilhamento de informações e verificar informações confidenciais em seus aplicativos de nuvem. Crie as seguintes políticas de arquivo para alertá-lo quando forem detectadas exposições de dados:

* Arquivos compartilhados externamente contendo dados confidenciais
* Arquivos compartilhados externamente e rotulados como **confidenciais**
* Arquivos compartilhados com domínios não autorizados
* Proteger arquivos confidenciais em aplicativos SaaS

**Para obter mais informações**:

* [Inspeção de conteúdo](content-inspection.md)
* [Políticas de arquivos](data-protection-policies.md)
* [Políticas de proteção de informações](policies-information-protection.md)

---

**Prática recomendada**: examinar relatórios na página **arquivos**  
**Detalhe**: depois de conectar vários aplicativos SaaS usando os conectores de aplicativos, Cloud app Security examina os arquivos armazenados por esses aplicativos. Além disso, cada vez que um arquivo é modificado, ele é verificado novamente. Você pode usar a página **arquivos** para entender e investigar os tipos de dados que estão sendo armazenados em seus aplicativos de nuvem. Para ajudá-lo a investigar, você pode filtrar por domínios, grupos, usuários, data de criação, extensão, nome de arquivo e tipo, ID de arquivo, rótulo de classificação e muito mais. O uso desses filtros coloca você no controle de como você opta por investigar os arquivos para garantir que nenhum dos seus dados esteja em risco. Depois de entender melhor como seus dados estão sendo usados, você pode criar políticas para verificar o conteúdo confidencial nesses arquivos.  
**Para obter mais informações**:

* [Conectar aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)
* [Filtros de arquivos](file-filters.md)
* [Inspeção de conteúdo](content-inspection.md)

---
---
---
---

## <a name="enforce-dlp-and-compliance-policies-for-data-stored-in-the-cloud"></a>Impor políticas de conformidade e DLP (proteção contra perda de dados) para dados armazenados na nuvem

**Prática recomendada**: proteger dados confidenciais de serem compartilhados com usuários externos  
**Detalhe**: Crie uma política de arquivo que detecta quando um usuário tenta compartilhar um arquivo com o rótulo de classificação **confidencial** com alguém externo à sua organização e configura sua ação de governança para remover usuários externos. Essa política garante que seus dados confidenciais não deixem sua organização e os usuários externos não podem obter acesso a ele.  
**Para obter mais informações**:

* [Controlando aplicativos conectados](governance-actions.md)

---
---
---
---

## <a name="block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices"></a>Bloquear e proteger o download de dados confidenciais para dispositivos não gerenciados ou arriscados

**Prática recomendada**: gerenciar e controlar o acesso a dispositivos de alto risco  
**Detalhe**: Use controle de aplicativos de acesso condicional para definir controles em seus aplicativos SaaS. Você pode criar políticas de sessão para monitorar suas sessões de alto risco e de confiança baixa. Da mesma forma, você pode criar políticas de sessão para bloquear e proteger downloads por usuários tentando acessar dados confidenciais de dispositivos não gerenciados ou arriscados. Se você não criar políticas de sessão para monitorar sessões de alto risco, perderá a capacidade de bloquear e proteger os downloads no cliente Web, bem como a capacidade de monitorar a sessão de baixa confiança tanto na Microsoft quanto em aplicativos de terceiros.  
**Para obter mais informações**:

* [Proteger aplicativos com o Controle de Aplicativo de Acesso Condicional do Microsoft Cloud App Security](proxy-intro-aad.md)
* [Políticas de sessão](session-policy-aad.md)

---
---
---
---

## <a name="secure-collaboration-with-external-users-by-enforcing-real-time-session-controls"></a>Proteger a colaboração com usuários externos ao impor controles de sessão em tempo real

**Prática recomendada**: monitorar sessões com usuários externos usando controle de aplicativos de acesso condicional  
**Detalhe**: para proteger a colaboração em seu ambiente, você pode criar uma política de sessão para monitorar sessões entre seus usuários internos e externos. Isso não apenas oferece a capacidade de monitorar a sessão entre os usuários (e notificá-los de que suas atividades de sessão estão sendo monitoradas), mas também permite que você limite atividades específicas também. Ao criar políticas de sessão para monitorar a atividade, você pode escolher os aplicativos e os usuários que deseja monitorar.  
**Para obter mais informações**:

* [Proteger aplicativos com o Controle de Aplicativo de Acesso Condicional do Microsoft Cloud App Security](proxy-intro-aad.md)
* [Políticas de sessão](session-policy-aad.md)

---
---
---
---

## <a name="detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware"></a>Detectar ameaças à nuvem, contas comprometidas, pessoas mal-intencionadas e ransomware

**Prática recomendada**: ajustar as políticas de anomalias, definir intervalos de IP, enviar comentários para alertas  
**Detalhe**: as políticas de detecção de anomalias fornecem Ueba (análise comportamental do usuário e entidade) e o ml (aprendizado de máquina) prontos para que você possa executar imediatamente a detecção avançada de ameaças em seu ambiente de nuvem.

As políticas de detecção de anomalias são disparadas quando há atividades incomuns executadas pelos usuários em seu ambiente. Cloud App Security monitora continuamente as atividades dos usuários e usa UEBA e ML para aprender e entender o comportamento *normal* dos usuários. Você pode ajustar as configurações de política para atender aos requisitos de sua organização, por exemplo, você pode definir a sensibilidade de uma política, bem como o escopo de uma política para um grupo específico.

* **Ajuste e escopo políticas de detecção de anomalias**: por exemplo, para reduzir o número de falsos positivos dentro do alerta de viagem impossível, você pode definir o controle deslizante de sensibilidade da política como baixo. Se você tiver usuários em sua organização que estejam com viajantes corporativos frequentes, você poderá adicioná-los a um grupo de usuários e selecionar esse grupo no escopo da política.

* **Definir intervalos de IP**: Cloud app Security pode identificar endereços IP conhecidos depois que os intervalos de endereços IP são definidos. Com os intervalos de endereços IP configurados, você pode marcar, categorizar e personalizar a maneira como os logs e alertas são exibidos e investigados. A adição de intervalos de endereços IP ajuda a reduzir as detecções de falsos positivos e a aumentar a precisão dos alertas. Se optar por não adicionar seus endereços IP, você poderá ver um número maior de possíveis falsos positivos e alertas a serem investigados.

* **Enviar comentários para alertas**

    Ao descartar ou resolver alertas, lembre-se de enviar comentários com o motivo pelo qual você ignorou o alerta ou como ele foi resolvido. Essas informações auxiliam Cloud App Security a melhorar nossos alertas e a reduzir os falsos positivos.

**Para obter mais informações**:

* [Obtenha análise comportamental e detecção de anomalias instantâneas](anomaly-detection-policy.md)
* [Trabalhando com intervalos de IP e marcas](ip-tags.md)
* [Monitorar alertas no Cloud App Security](monitor-alerts.md)

---

**Prática recomendada**: detectar atividade de locais ou países inesperados  
**Detalhe**: Crie uma política de atividade para notificá-lo quando os usuários entrarem de locais ou países inesperados. Essas notificações podem alertá-lo sobre sessões possivelmente comprometidas em seu ambiente para que você possa detectar e corrigir ameaças antes que elas ocorram.  
**Para obter mais informações**:

* [Políticas de proteção contra ameaças](policies-threat-protection.md)

---

**Prática recomendada**: criar políticas de aplicativo OAuth  
**Detalhe**: Crie uma política de aplicativo OAuth para notificá-lo quando um aplicativo OAuth atender a determinados critérios. Por exemplo, você pode optar por ser notificado quando um aplicativo específico que requer um nível de permissão alto foi acessado por mais de 100 usuários.  
**Para obter mais informações**:

* [Políticas de aplicativo OAuth](app-permission-policy.md)

---
---
---
---

## <a name="use-the-audit-trail-of-activities-for-forensic-investigations"></a>Usar a trilha de auditoria das atividades para investigações forenses

**Prática recomendada**: usar a trilha de auditoria de atividades ao investigar alertas  
**Detalhe**: os alertas são disparados quando as atividades de usuário, administrador ou entrada não estão em conformidade com suas políticas. É importante investigar alertas para entender se há uma possível ameaça em seu ambiente.

Você pode investigar um alerta selecionando-o na página **alertas** e examinando a trilha de auditoria das atividades relacionadas a esse alerta. A trilha de auditoria fornece visibilidade das atividades do mesmo tipo, do mesmo usuário, do mesmo endereço IP e local, para fornecer a história geral de um alerta. Se um alerta exigir mais investigação, crie um plano para resolver esses alertas em sua organização.

Ao ignorar alertas, é importante investigar e entender por que eles não têm importância ou se são falsos positivos. Se houver um alto volume dessas atividades, talvez você queira analisar e ajustar a política que dispara o alerta.  
**Para obter mais informações**:

* [Atividades](activity-filters.md)

---
---
---
---

## <a name="secure-iaas-services-and-custom-apps"></a>Proteger serviços de IaaS (infraestrutura como serviço) e aplicativos personalizados

**Prática recomendada**: conectar o Azure e o AWS  
**Detalhe**: conectar cada um desses aplicativos de armazenamento em nuvem para Cloud app Security ajuda a melhorar seus recursos de detecções de ameaças. Ao monitorar atividades administrativas e de entrada para esses serviços, você pode detectar e ser notificado sobre possíveis ataques de força bruta, uso mal-intencionado de uma conta de usuário com privilégios e outras ameaças em seu ambiente. Por exemplo, você pode identificar riscos como exclusões incomuns de VMs ou até mesmo atividades de representação nesses aplicativos.  
**Para obter mais informações**:

* [Conectar o Microsoft Azure ao Microsoft Cloud App Security](connect-azure-to-microsoft-cloud-app-security.md)
* [Conectar o AWS ao Microsoft Cloud App Security](connect-aws-to-microsoft-cloud-app-security.md)

---

**Prática recomendada**: examinar as avaliações de configuração de segurança do Azure e do AWS  
**Detalhe**: a integração com a central de segurança do Azure fornece uma avaliação de configuração de segurança de seu ambiente do Azure. A avaliação fornece recomendações para a configuração e o controle de segurança ausentes. A revisão dessas recomendações ajuda a identificar anomalias e possíveis vulnerabilidades em seu ambiente e navegar diretamente no local relevante no portal de segurança do Azure para resolvê-las.

O AWS oferece a capacidade de obter visibilidade de suas recomendações de configurações de segurança sobre como melhorar sua segurança de nuvem. Com essas recomendações, você pode monitorar o status de conformidade de suas contas do AWS.  
**Para obter mais informações**:

* [Configuração de segurança para o Azure](security-config.md)
* [Configuração de segurança para AWS](security-config-aws.md)

---

**Prática recomendada**: integrar aplicativos personalizados  
**Detalhe**: para obter visibilidade adicional das atividades de seus aplicativos de linha de negócios, você pode integrar aplicativos personalizados para Cloud app Security. Depois que os aplicativos personalizados são configurados, você vê informações sobre como usá-los, os endereços IP dos quais eles estão sendo usados e a quantidade de tráfego que entra e sai do aplicativo.

Além disso, você pode integrar um aplicativo personalizado como um aplicativo Controle de Aplicativos de Acesso Condicional para monitorar suas sessões de baixa confiança.  
**Para obter mais informações**:

* [Adicionar aplicativos personalizados ao Cloud Discovery](cloud-discovery-custom-apps.md)
* [Integração e implantação de Controle de Aplicativos de Acesso Condicional para qualquer aplicativo](proxy-deployment-any-app.md)

---
title: Novidades no Cloud App Security
description: Este artigo é atualizado com frequência para você saber quais são as novidades na versão mais recente do Cloud App Security.
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/24/2020
ms.topic: overview
ms.service: cloud-app-security
ms.collection: M365-security-compliance
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 619bce7e6f3931a53a5891c6c5ff0db223c384cf
ms.sourcegitcommit: 2cf3c78a1b45a5b6ca534fdd12fd97afc51726e3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291244"
---
# <a name="whats-new-with-microsoft-cloud-app-security"></a>Novidades do Microsoft Cloud App Security

*Aplica-se a: Microsoft Cloud App Security*

Este artigo é atualizado com frequência para você saber quais são as novidades na versão mais recente do Cloud App Security.

Feed RSS: Receba uma notificação quando esta página for atualizada copiando e colando a seguinte URL em seu leitor de feed: `https://docs.microsoft.com/api/search/rss?search=%22This+article+is+updated+frequently+to+let+you+know+what%27s+new+in+the+latest+release+of+Cloud+App+Security%22&locale=en-us`

## <a name="cloud-app-security-release-170-and-171"></a>Cloud App Security versão 170 e 171

Lançado em 22 de março de 2020

- **Nova detecção de anomalia: uso de região incomum para recursos da nuvem (versão prévia)**  
Expandimos nossa capacidade atual de detecção de comportamentos anômalos para a AWS. A nova detecção já está disponível e pronta para uso, habilitada automaticamente para alertá-lo quando um recurso é criado em uma região da AWS onde atividades geralmente não são executadas. Os invasores geralmente aproveitam os créditos da AWS de uma organização para realizar atividades mal-intencionadas, como criptomineração. Detectar esse comportamento anômalo pode ajudar a mitigar um ataque.

- **Novos modelos de política de atividade para o Microsoft Teams**  
O Cloud App Security agora oferece os novos modelos de política de atividade abaixo, permitindo detectar atividades potencialmente suspeitas no Microsoft Teams:
  - **Alteração do nível de acesso (Teams):** alerta quando o nível de acesso de uma equipe é alterado de privado para público.
  - **Usuário externo adicionado (Teams):** alerta quando um usuário externo é adicionado a uma equipe.
  - **Exclusão em massa (Teams):** alerta quando um usuário exclui um grande número de equipes.

- **Integração com a Proteção de Identidade do Azure AD (Azure Active Directory)**  
Agora você pode controlar a gravidade dos alertas da Proteção de Identidade do Azure AD que são inseridos no Cloud App Security. E você ainda pode habilitar a detecção de **Entrada suspeita do Azure AD**, caso ainda não o tenha feito, para receber automaticamente alertas de alta severidade. Para obter mais informações, confira [Integração com a Proteção de Identidade do Azure AD](aadip-integration.md).

## <a name="cloud-app-security-release-169"></a>Cloud App Security versão 169

Lançado em 1º de março de 2020

- **Nova detecção para Workday**  
Nós expandimos nossos alertas atuais de comportamento anormal para o Workday. Os novos alertas incluem as seguintes detecções de localização geográfica de usuário:
  - [Atividade de endereços IP anônimos](anomaly-detection-policy.md#activity-from-anonymous-ip-addresses)
  - [Atividade de país não frequente](anomaly-detection-policy.md#activity-from-infrequent-country)
  - [Atividade de endereços IP suspeitos](anomaly-detection-policy.md#activity-from-suspicious-ip-addresses)
  - [Viagem impossível](anomaly-detection-policy.md#impossible-travel)

- **Coleta aprimorada de logs do Salesforce**  
O Cloud App Security agora dá suporte ao log de eventos por hora do Salesforce. Os logs de eventos por hora oferecem monitoramento acelerado, quase em tempo real, das atividades do usuário. Para saber mais, confira [Conectar o Salesforce](connect-salesforce-to-microsoft-cloud-app-security.md).

- **Suporte para a configuração de segurança do AWS usando uma conta principal**  
O Cloud App Security agora dá suporte ao uso de uma conta principal. Conectar sua conta principal permite que você receba recomendações de segurança para todas as contas de membros em todas as regiões. Para obter mais informações sobre como se conectar a uma conta principal, confira [Como conectar a configuração de segurança do AWS ao Cloud App Security](connect-aws-to-microsoft-cloud-app-security.md#how-to-connect-aws-security-configuration-to-cloud-app-security).

- **Suporte a controles de sessão para navegadores modernos**  
Agora os controles de sessão do Cloud App Security incluem suporte para o novo navegador Microsoft Edge baseado no Chromium. Apesar de continuarmos a dar suporte às versões mais recentes do Internet Explorer e à versão herdada do Microsoft Edge, o suporte será limitado, e recomendamos usar o novo navegador Microsoft Edge.

## <a name="cloud-app-security-release-165-166-167-and-168"></a>Cloud App Security versão 165, 166, 167 e 168

Lançado em 16 de fevereiro de 2020

- **Novo bloqueio de aplicativos não sancionados com a Microsoft Defender ATP**  
O Cloud App Security estendeu a integração nativa com a Microsoft Defender ATP (Proteção Avançada contra Ameaças). Agora, você pode bloquear o acesso a aplicativos marcados como não sancionados usando o recurso de proteção de rede do Microsoft Defender ATP. Para saber mais, confira [Bloquear o acesso a aplicativos na nuvem não sancionados](wdatp-integration.md#block-access-to-unsanctioned-cloud-apps).

- **Nova detecção de anomalias de aplicativos OAuth**  
Expandimos nossa capacidade atual de detectar consentimento a aplicativos OAuth mal-intencionados. A nova detecção já está disponível e pronta para uso, habilitada de forma automática para alertar você quando um aplicativo OAuth potencialmente mal-intencionado é autorizado em seu ambiente. Essa detecção aproveita a especialização da Microsoft em pesquisa de segurança e inteligência contra ameaças para identificar aplicativos mal-intencionados.

- **Atualizações do coletor de logs**  
O coletor de logs baseado no Docker foi aprimorado com as seguintes atualizações importantes:

  - Atualização da versão do SO do contêiner

  - Patches de vulnerabilidades de segurança do Java

  - Atualização do serviço de Syslog

  - Melhorias de estabilidade e desempenho

    Recomendamos que você atualize seu ambiente para essa nova versão. Para saber mais, confira [Modos de implantação do coletor de logs](discovery-docker.md#deployment-modes).

- **Suporte para ServiceNow New York**  
O Cloud App Security agora dá suporte à versão mais recente (New York) do ServiceNow. Para saber mais, confira [Conectar o ServiceNow ao Microsoft Cloud App Security](connect-servicenow-to-microsoft-cloud-app-security.md).

- **Lógica de detecção aprimorada: viagem impossível**  
Atualizamos a lógica de detecção para viagem impossível a fim de oferecer melhor cobertura e maior precisão. Como parte dessa atualização, também atualizamos a lógica de detecção para [viagem impossível de redes corporativas](anomaly-detection-policy.md#impossible-travel).

- **Novo limite para políticas de atividades**  
Adicionamos um limite para [políticas de atividades](user-activity-policies.md) a fim de ajudar a gerenciar os volumes de alertas. Políticas que disparam um grande volume de correspondências por vários dias são desabilitadas automaticamente. Se você receber um alerta do sistema sobre isso, experimente refinar as políticas adicionando filtros ou, se você estiver usando políticas para fins de relatórios, considere salvá-las como consultas.

## <a name="cloud-app-security-release-162-163-and-164"></a>Cloud App Security versão 162, 163 e 164

Lançado em 8 de dezembro de 2019

- **Alterar para atividades e alertas do SIEM no formato CEF**  
O [formato de URL do portal (CS1)](siem.md#sample-cloud-app-security-alerts-in-cef-format) para informações de atividades e alertas enviadas pelo Cloud App Security para SIEMs foi alterado para `https://<tenant_name>.portal.cloudappsecurity.com` e não contém mais o local do data center. Os clientes que usam a correspondência de padrões para a URL do portal devem atualizar o padrão para refletir essa alteração.

## <a name="cloud-app-security-release-160-and-161"></a>Cloud App Security versão 160 e 161

Lançado em 3 de novembro de 2019

- **Dados de descoberta no Azure Sentinel (versão prévia)**  
O Cloud App Security agora está integrado ao Azure Sentinel. O compartilhamento de dados de alerta e de descoberta com o Azure Sentinel oferece os seguintes benefícios:

  - Habilite a correlação de dados de descoberta com outras fontes de dados para obter uma análise mais profunda.

  - Exiba dados no Power BI com painéis prontos para uso ou crie suas próprias visualizações.

  - Aproveite períodos de retenção mais longos com o Log Analytics.

  Para saber mais, confira [Integração ao Azure Sentinel](siem-sentinel.md).

- **Conector de Google Cloud Platform (versão prévia)**  
O Cloud App Security está estendendo seus recursos de monitoramento de IaaS para além do Amazon Web Services e agora dá suporte ao Google Cloud Platform. Isso permite que você se conecte e monitore perfeitamente todas as suas cargas de trabalho do GCP com o Cloud App Security. A conexão fornece um conjunto avançado de ferramentas para proteger seu ambiente do GCP, incluindo:

  - Visibilidade de todas as atividades realizadas por meio do console de administração e de chamadas à API.

  - Capacidade de criar políticas personalizadas e usar modelos predefinidos para alertar sobre eventos arriscados.

  - Nosso mecanismo de detecção de anomalias abrange todas as atividades do GCP e alerta automaticamente sobre todos os comportamentos suspeitos, como tráfego impossível, atividades em massa suspeitas e atividade em um novo país.

  Para saber mais, confira [Conectar o Google Cloud Platform ao Microsoft Cloud App Security](connect-google-gcp-to-microsoft-cloud-app-security.md).

- **Novos modelos de políticas**  
Agora, o Cloud App Security inclui novos modelos de políticas de atividade internos para melhores práticas de segurança do Google Cloud Platform.

- **Analisador de log do Cloud Discovery aprimorado**  
O Cloud Discovery do Cloud App Security analisa uma ampla variedade de logs de tráfego para classificar e pontuar os aplicativos. Agora, o analisador de log interno do Cloud Discovery dá suporte ao formato de log do IronPort WSA 10.5.1.

- **Página de aterrissagem de usuário personalizável para controles de sessão**  
Lançamos para os administradores a capacidade de personalizar a página de aterrissagem que os usuários veem quando navegam para um aplicativo ao qual uma política de sessão está aplicada. Agora, você pode exibir o logotipo da sua organização e personalizar a mensagem mostrada. Para iniciar a personalização, vá para a página **Configurações** e, em **Controle de Aplicativo de Acesso à Nuvem**, selecione **Monitoramento de usuário**.

- **Novas detecções**  

  - **Alterações suspeitas no serviço de log do AWS (versão prévia)** : alerta quando um usuário faz alterações no serviço de log CloudTrail. Por exemplo, os invasores geralmente desativam a auditoria no CloudTrail para ocultar os vestígios de seu ataque.

  - **Múltiplas atividades de criação de VM**: Alerta quando um usuário executa um número incomum de atividades de criação de VM em comparação com a linha de base aprendida. Agora se aplica ao AWS.

## <a name="cloud-app-security-release-159"></a>Cloud App Security versão 159

Lançado em 6 de outubro de 2019

- **Novo analisador de log ContentKeeper do Cloud Discovery**  
O Cloud Discovery do Cloud App Security analisa uma ampla variedade de logs de tráfego para classificar e pontuar os aplicativos. Agora o Cloud Discovery inclui um analisador de log interno para dar suporte aos formatos de log do ContentKeeper. Para acessar a lista de dispositivos com suporte, confira [Proxies e firewalls com suporte](set-up-cloud-discovery.md#supported-firewalls-and-proxies).

- **Novas detecções**  
As novas políticas de detecção de anomalias a seguir estão prontas para uso e são habilitadas automaticamente:

  - **Atividade de exclusão de email suspeito (versão prévia)**  
    Alerta quando um usuário executa atividades incomuns de exclusão de email. Essa política pode ajudá-lo a detectar caixas de correio do usuário que podem estar comprometidas por possíveis vetores de ataque, como a comunicação de comando e controle (C&C/C2) por email.

  - **Múltiplos compartilhamentos de relatórios do Power BI (versão prévia)**  
    Alerta quando um usuário executa um número incomum de atividades de compartilhamento de relatório no Power BI em comparação com a linha de base aprendida.

  - **Múltiplas atividades de criação de VM (versão prévia)**  
    Alerta quando um usuário executa um número incomum de atividades de criação de VM em comparação com a linha de base aprendida. Atualmente aplica-se ao Azure.

  - **Múltiplas atividades de exclusão de armazenamento (versão prévia)**  
    Alerta quando um usuário executa um número incomum de atividades de exclusão de armazenamento em comparação com a linha de base aprendida. Atualmente aplica-se ao Azure.

## <a name="cloud-app-security-release-158"></a>Cloud App Security, versão 158

Lançado em 15 de setembro de 2019

- **Personalizar o nome do relatório executivo do Cloud Discovery**  
O relatório executivo do Cloud Discovery fornece uma visão geral do uso de TI sombra em sua organização. Agora você tem a opção de personalizar o nome do relatório antes de gerá-lo. Para obter mais informações, confira [Gerar relatório executivo do Cloud Discovery](discovered-apps.md#generate-cloud-discovery-executive-report).

- **Novo relatório de visão geral das políticas**  
O Cloud App Security detecta correspondências de políticas e, quando definido, registra alertas que você pode usar para entender de forma avançada seu ambiente de nuvem. Agora você pode exportar um relatório de visão geral de políticas mostrando as métricas de alerta agregadas por política para ajudá-lo a monitorar, compreender e personalizar suas políticas para proteger melhor sua organização. Para obter mais informações sobre como exportar o relatório, confira o [Relatório de visão geral de políticas](control-cloud-apps-with-policies.md#policies-overview-report).

## <a name="cloud-app-security-release-157"></a>Cloud App Security, versão 157

Lançado em 1º de setembro de 2019

- **Lembrete: Fim do suporte para o TLS 1.0 e 1.1 em 8 de setembro**  
A Microsoft está migrando todos os seus serviços online para o protocolo TLS 1.2+ para fornecer a melhor criptografia. Portanto, a partir de 8 de setembro de 2019, o Cloud App Security não dará mais suporte a TLS 1.0 e 1.1, e as conexões que usam esses protocolos não serão compatíveis. Para obter mais informações sobre como a alteração afeta você, confira [nossa postagem no blog](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/End-of-support-for-TLS-1-0-and-1-1-in-Microsoft-Cloud-App/ba-p/770507).

- **Nova detecção – Compartilhamento suspeito do Microsoft Power BI (versão prévia)**  
A nova política de compartilhamento suspeito de relatório do Power BI agora está disponível para uso e é habilitada automaticamente para alertar você quando um relatório potencialmente confidencial do Power BI for compartilhado de forma suspeita fora da sua organização.

- **Novo recurso de exportação para auditoria do aplicativo OAuth**  
O Cloud App Security audita todas as atividades de autorização do OAuth para fornecer monitoramento e investigação abrangentes das atividades executadas. Agora também é possível exportar os detalhes de usuários que autorizaram um aplicativo OAuth específico, fornecendo informações adicionais sobre os usuários, que você pode usar para análise posterior.

- **Auditoria de eventos do Okta aprimorada**  
O Cloud App Security agora é compatível com a nova API de log do sistema lançada pelo Okta. Para obter mais informações sobre como conectar o Okta, consulte [Conectar o Okta](connect-okta-to-microsoft-cloud-app-security.md).

- **Conector Workday (versão prévia)**  
Um novo conector de aplicativos agora está disponível para o Workday. Agora é possível conectar o Workday ao Cloud App Security para monitorar atividades e proteger os usuários e atividades. Para obter mais informações, consulte [Conectar o Workday](connect-workday-to-microsoft-cloud-app-security.md).

- **Avaliação avançada para o fator de risco "Política de senha"**  
O Catálogo de Aplicativos de Nuvem agora fornece uma avaliação granular para o fator de risco da **Política de senha**. Ao focalizar o ícone de informações, é possível ver um detalhamento das políticas específicas que são impostas pelo aplicativo.

## <a name="cloud-app-security-release-156"></a>Cloud App Security versão 156

Lançado em 18 de agosto de 2019

- **Novos analisadores de log do Cloud Discovery**  
O Cloud Discovery do Cloud App Security analisa uma ampla variedade de logs de tráfego para classificar e pontuar os aplicativos. Agora o Cloud Discovery inclui um analisador de log interno para dar suporte aos formatos de log Stormshield e Forcepoint LEEF.

- **Melhorias no log de atividades**  
O Cloud App Security agora oferece maior visibilidade sobre atividades não classificadas executadas por aplicativos em seu ambiente. Essas atividades estão disponíveis no Log de atividades e também nas Políticas de atividades. Para ver atividades não classificadas, no filtro **Tipo** selecione **Não especificado**. Para obter mais informações sobre filtros de atividade, confira [Filtros de atividade e consultas](activity-filters-queries.md).

- **Melhoria na investigação de usuários arriscados**  
O Cloud App Security fornece a capacidade de identificar usuários arriscados na página **Usuários e contas** por grupos, aplicativos e até mesmo funções específicos. Agora você também pode investigar os usuários da sua organização pela pontuação de **Prioridade de investigação**. Para obter mais informações, confira [Entenda a pontuação de prioridade de investigação](tutorial-ueba.md#risk-score).

- **Melhorias na política de atividades**  
Agora você pode criar alertas para a política de atividades com base nos objetos da atividade. Por exemplo, essa funcionalidade permite que você crie alertas para as alterações nas funções administrativas do Azure Active Directory. Para obter mais informações sobre os objetos da atividade, confira [Filtros de atividade](activity-filters-queries.md#activity-filters).

## <a name="cloud-app-security-release-155"></a>Cloud App Security, versão 155

Lançado em 4 de agosto de 2019

- **Novos modelos de políticas**  
Agora o Cloud App Security inclui novos modelos de políticas de atividade interna para melhores práticas de segurança do AWS.

- **Aviso: Fim do suporte para o TLS 1.0 e 1.1 em 8 de setembro**  
A Microsoft está migrando todos os seus serviços online para o protocolo TLS 1.2+ para fornecer a melhor criptografia. Portanto, a partir de 8 de setembro de 2019, o Cloud App Security não dará mais suporte a TLS 1.0 e 1.1, e as conexões que usam esses protocolos não serão compatíveis. Para obter mais informações sobre como a alteração afeta você, confira [nossa postagem no blog](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/End-of-support-for-TLS-1-0-and-1-1-in-Microsoft-Cloud-App/ba-p/770507).

- **Lógica aprimorada para atividades de entrada interativas (distribuição gradual)**  
Estamos fazendo a distribuição gradual de uma nova lógica para identificar se uma atividade de entrada do Azure Active Directory é interativa. A nova lógica aprimora a capacidade do Cloud App Security de exibir apenas atividades de entrada iniciadas por um usuário.

## <a name="cloud-app-security-release-154"></a>Cloud App Security versão 154

Lançado em 21 de julho de 2019

- **A integração e a implantação do Controle de Aplicativos de Acesso Condicional para qualquer aplicativo estão agora em disponibilidade geral**  
Desde que liberamos a versão prévia do Controle de Aplicativos de Acesso Condicional para qualquer aplicativo no mês passado, recebemos comentários excelentes e estamos empolgados em anunciar a disponibilidade geral. Essa nova funcionalidade permite implantar qualquer aplicativo Web para funcionar com políticas de acesso e sessão, permitindo monitoramento e controle eficientes em tempo real.

- **Avaliação da configuração de segurança do AWS**  
O Cloud App Security está lançando gradualmente a capacidade de fazer uma avaliação da configuração de segurança do ambiente do Amazon Web Services para conformidade com CIS e oferece recomendações sobre controles de segurança e configurações ausentes. Essa capacidade fornece às organizações uma exibição única para monitorar o status de conformidade de todas as contas do AWS conectadas.

- **Detecções de anomalias do aplicativo OAuth**  
Expandimos nossa capacidade atual de detectar aplicativos OAuth suspeitos. Agora há quatro novas detecções prontas para uso, que analisam os metadados de aplicativos OAuth autorizados em sua organização para identificar aqueles que são potencialmente mal-intencionados.

## <a name="cloud-app-security-release-153"></a>Cloud App Security versão 153

Lançado em 7 de julho de 2019

- **Suporte aprimorado do Dropbox**  
Agora o Cloud App Security dá suporte à ação de governança **Jogar no lixo** para Dropbox – Esta ação de governança pode ser usada manual ou automaticamente como parte de uma política de arquivo.
- **Novos aplicativos em destaque para Controle de Aplicativos de Acesso à Nuvem**  
O Controle de Aplicativos de Acesso Condicional dos seguintes aplicativos em destaque agora está em disponibilidade geral:

    - OneDrive for Business
    - SharePoint online
    - Azure DevOps
    - Exchange Online
    - Power BI

- **Autorizar arquivos identificados como malware**  
O Cloud App Security examina os arquivos de seus aplicativos conectados quanto à exposição de DLP e a malware. Agora é possível autorizar arquivos que foram identificados como malware mas que foram confirmados como sendo seguros após uma investigação. Autorizar um arquivo o remove do relatório de detecção de malware e suprime correspondências futuras nele. Para saber mais sobre a detecção de malware, confira [Detecção de anomalias do Cloud App Security](anomaly-detection-policy.md).

## <a name="cloud-app-security-release-152"></a>Cloud App Security versão 152

Lançado em 23 de junho de 2019

- **Implantar Controle de Aplicativos de Acesso Condicional para qualquer aplicativo (versão prévia)**  
Temos a satisfação de anunciar que expandimos nosso suporte para o Controle de Aplicativos de Acesso Condicional para qualquer aplicativo Web, além do suporte avançado que já oferecíamos para [nossos aplicativos em destaque](proxy-intro-aad.md). Essa nova funcionalidade permite implantar qualquer aplicativo Web para funcionar com políticas de acesso e sessão, permitindo monitoramento e controle eficientes em tempo real. Por exemplo, você pode proteger downloads com rótulos de Proteção de Informações do Azure, bloquear o upload de documentos confidenciais, fornecer auditoria entre muitas outras ações.
- **Auditoria de atividades do Portal**  
O Cloud App Security audita todas as atividades do administrador no portal para fornecer monitoramento e investigação abrangentes das atividades executadas. Agora você também pode exportar até 90 dias de atividades para mais investigação e análise, por exemplo, auditoria de um administrador investigando um usuário específico ou exibindo alertas específicos. Para exportar o log, vá para a página de configurações **Gerenciar acesso de administrador**.
- **Saída da sessão personalizada do portal do Cloud App Security**  
Agora você pode configurar a saída automática de sessões de administrador para o portal que estejam ociosas por mais de um período especificado.

## <a name="cloud-app-security-release-151"></a>Cloud App Security, versão 151

Lançado em 9 de junho de 2019

- **UEBA híbrido - integração nativa com o ATP do Azure (versão prévia)**  
O Cloud App Security agora nativamente é integrado com o ATP do Azure para fornecer uma exibição única de atividades de identidade em aplicativos de nuvem e sua rede local. Para saber mais, confira [Integração com a Proteção Avançada contra Ameaças do Azure](aatp-integration.md).
- **Aprimoramentos do UEBA**  
Para ajudá-lo a identificar ameaças que não são tão evidentes, o Cloud App Security agora usa a exclusiva criação de perfil para fornecer as pontuações de risco para alertas e atividades individuais. As pontuações de risco podem ser usadas para identificar as atividades que não são suficientemente suspeitas para disparar alertas. No entanto, ao agregar as pontuações de risco à **Pontuação de prioridade de investigação** de um usuário, o Cloud App Security ajuda a identificar comportamentos de risco e concentrar sua investigação. Essas novas funcionalidades agora estão disponíveis em nossa página de usuário reprojetada.
- **Novo fator de risco adicionado ao Catálogo de aplicativos de nuvem**  
O Catálogo de aplicativos de nuvem agora inclui o fator de risco do Plano de Recuperação de Desastres para que você possa avaliar os aplicativos no Catálogo de aplicativos de nuvem para suporte a continuidade de negócios.
- **Conector GA do Microsoft Flow**  
O conector está disponível amplamente desde o suporte à versão prévia do Microsoft Cloud App Security para o conector do Microsoft Flow, no ano passado.
- **Aprimoramento de governança automatizada para políticas de arquivo**  
O Cloud App Security agora dá suporte à configuração da ação de governança da **Lixeira** para políticas de arquivo – essa ação de governança fornece a capacidade de mover arquivos automaticamente para a pasta da lixeira.
- **Suporte aprimorado para o Google Drive**  
O Cloud App Security agora dá suporte à ação de governança da **Lixeira** para o Google Drive – essa ação de governança fornece a capacidade de mover arquivos do Google Drive para a pasta da lixeira.
- **Nova permissão para as funções de administrador do aplicativo e administrador de grupo**  
As funções *Administrador de aplicativo/instância* e *Administrador de grupo de usuários* agora dão suporte ao acesso somente leitura.
- **Atividades de entrada com autenticação herdada (distribuição gradual)**  
O Cloud App Security agora exibe atividades de entrada do Azure Active Directory que usam protocolos herdados, como o ActiveSync. Essas atividades de entrada podem ser exibidas no log de atividades e usadas durante a configuração de políticas.

## <a name="cloud-app-security-release-150"></a>Cloud App Security, lançamento 150

Lançado em 26 de maio de 2019

- **Melhoria na exportação de alertas**  
Quando você exporta alertas para um arquivo CSV na página de **Alertas**, os resultados agora incluem a data de resolução ou de descarte do alerta.

## <a name="cloud-app-security-release-148-and-149"></a>Cloud App Security versão 148 e 149

Lançado em 12 de maio de 2019

- **Conector do aplicativo WebEx disponível**  
Agora um novo conector de aplicativo está disponível para o Cisco WebEx Teams em visualização pública. Você pode conectar o Microsoft Cloud App Security ao Cisco Webex Teams para monitorar e proteger usuários, atividades e arquivos dele. Para saber mais, confira [Conectar o Webex](connect-webex-to-microsoft-cloud-app-security.md)

- **Novos locais do serviço de classificação de dados da Microsoft**  
O [Serviço de Classificação de Dados da Microsoft](dcs-inspection.md) já está disponível em quatro novos locais: Austrália, Índia, Canadá e Japão. Se seu locatário do Office estiver localizado em um desses países, agora você pode utilizar o Serviço de classificação de dados da Microsoft como o método de inspeção de conteúdo nas políticas de arquivo do Microsoft Cloud App Security.

- **Discovery para PaaS e IaaS sombras**  
O Microsoft Cloud App Security ampliou os recursos do Cloud Discovery e agora também fornece TI sombra para os recursos hospedados em soluções de IaaS e PaaS, como o Microsoft Azure, Amazon Web Services e Google Cloud Platform. O Cloud Discovery fornece a visibilidade de quais aplicativos personalizados são executados sobre seu IaaS e PaaS, as contas de armazenamento que estão sendo criadas e muito mais. Use essa nova funcionalidade para descobrir quais recursos existirem, quem acessa cada um deles e a quantidade de tráfego transmitida.

- **Atestado de aplicativo**  
A avaliação de conformidade e risco do Microsoft Cloud App Security agora permite que provedores de nuvem atestem o aplicativo para estar atualizado no Catálogo de Aplicativos de Nuvem. Esse piloto permite que provedores de nuvem preencham um questionário de autocertificação com base nos atributos de risco do Catálogo de aplicativos de nuvem para garantir que sua avaliação de risco no Cloud App Security seja precisa e atualizada. Assim, os usuários podem obter uma indicação de quais atributos de risco foram atestados pelo provedor (em vez de avaliados pela equipe do Cloud App Security) e quando cada atributo foi enviado pelo provedor. Para saber mais, confira [Atestar seu aplicativo](attest-your-app.md).

- **Granularidade da carga de trabalho do Office 365**  
Agora, ao conectar o Office 365 ao Microsoft Cloud App Security, você tem controle sobre quais cargas de trabalho deseja conectar. Por exemplo, os clientes interessados apenas em conectar o Office 365 para o monitoramento de atividade agora podem fazê-lo durante o processo de conexão ou ao editar um conector existente do Office 365. Como parte desta alteração, o OneDrive e o SharePoint Online não serão mais mostrados como conectores separados, mas eles serão incluídos no conector do Office 365 como a carga de trabalho de _arquivos do Office 365_. Os clientes com um conector existente do Office 365 não são afetados por essa alteração.

- **Suporte aprimorado do Teams**  
Agora você pode monitorar e bloquear o envio de mensagens no aplicativo Web do Teams em tempo real, configurando uma política de sessão com base no conteúdo confidencial.

## <a name="cloud-app-security-release-147"></a>Cloud App Security, versão 147

Lançado em 14 de abril de 2019

- **Novo analisador de log do Cloud Discovery**  
O Cloud App Security Cloud Discovery agora inclui um analisador de log integrado para dar suporte ao formato de log Palo Alto LEEF.

- **Atualizações de políticas de sessão**  
  - **Método adicional de inspeção de conteúdo para políticas de sessão**:  Agora, você terá a opção de escolher o Serviço de Classificação de Dados como um método de inspeção de conteúdo para arquivos ao definir uma política de sessão. O Serviço de Classificação de Dados oferece ao usuário uma ampla variedade de tipos confidenciais incorporados para identificar informações confidenciais.
  - **Melhoria no controle de permissões de arquivos nas políticas de sessão**:  Quando quiser criar uma política de sessão para controlar downloads usando o Cloud App Security, agora você poderá aplicar automaticamente permissões por usuário, como somente leitura para acesso a documentos após o download dos aplicativos na nuvem. Isso fornece um nível muito maior de flexibilidade e a capacidade de proteger as informações além dos rótulos corporativos pré-configuradas.
  - **Controle de download de arquivo grande**:  Quando a inspeção de conteúdo estiver habilitada nas políticas de sessão, você poderá controlar o que acontece quando um usuário tentar baixar um arquivo muito grande. Se o arquivo for grande demais para ser examinado no download, você poderá escolher se ele será bloqueado ou permitido.

## <a name="cloud-app-security-release-146"></a>Cloud App Security, versão 146

Lançada em 31 de março de 2019

- **Melhoria de viagem impossível**  
A detecção de viagem impossível foi aprimorada com suporte dedicado para países vizinhos.
- **Suporte de atributo adicional para o analisador de CEF genérico**  
O suporte do analisador de log do Cloud Discovery para o formato CEF genérico foi aprimorado para dar suporte a atributos adicionais.
- **Acesso com escopo aos relatórios do Cloud Discovery**  
Além da função de Administrador de descoberta, agora você pode definir o acesso com escopo a relatórios específicos de Descoberta. Esse aprimoramento permite configurar privilégios a dados de sites específicos e de unidades de negócios.
- **Novo suporte à função: Leitor global**  
O Microsoft Cloud App Security agora dá suporte à função de Leitor Global do Azure AD. O Leitor Global tem acesso completo somente para leitura de todos os aspectos do Microsoft Cloud App Security, mas não pode alterar nenhuma configuração nem realizar nenhuma ação.

## <a name="cloud-app-security-release-145"></a>Cloud App Security versão 145

Lançado em 17 de março de 2019

- **A integração do Microsoft Defender ATP agora está em disponibilidade geral**  
No ano passado, anunciamos a [integração com a Proteção Avançada contra Ameaças do Windows Defender](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Microsoft-Cloud-App-Security-and-Windows-Defender-ATP-better/ba-p/263265), que aprimora a Descoberta de TI Sombra em sua organização e ultrapassa a rede corporativa. [Habilitado com um único clique](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RWtNmG), estamos empolgados em anunciar que essa integração exclusiva já está disponível para o público em geral.
- **Suporte para Dynamics 365 CRM**  
O Cloud App Security adicionou monitoramento e controle em tempo real no Dynamics 365 CRM para que você possa proteger seus aplicativos de negócios e o conteúdo confidencial armazenado dentro deles. Para obter mais informações sobre o que pode ser feito com o Dynamics 365 CRM, confira [este artigo](proxy-intro-aad.md#how-it-works).

## <a name="cloud-app-security-release-144"></a>Cloud App Security versão 144

Lançada em 3 de março de 2019

- **Investigação de SecOps unificada para ambientes híbridos**  
Como muitas organizações têm ambientes híbridos, os ataques começam na nuvem e, em seguida, mudam para o local, o que significa que as equipes de SecOps precisam investigar esses ataques de vários locais. Ao combinar sinais de fontes locais e de nuvem, incluindo o Microsoft Cloud App Security, a Proteção Avançada contra Ameaças do Azure e a Azure AD Identity Protection, a Microsoft capacita os analistas de segurança ao fornecer informações de usuário e identidade unificadas em um único console, o que acaba com a necessidade de alternar entre soluções de segurança. Assim, suas equipes de SecOps terão mais tempo e as informações certas para melhorar a tomada de decisões e corrigir ativamente as ameaças e os riscos reais de identidade. Saiba mais em [Investigação de SecOps unificada para ambientes híbridos](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Unified-SecOps-Investigation-for-Hybrid-Environments/ba-p/360850)

- **Recursos de área restrita para detecção de malware** (distribuição gradual)  
Os recursos de detecção de malware do Cloud App Security estão sendo expandidos para incluir a capacidade de identificação de malware de dia zero por meio da tecnologia avançada de Área Restrita.  
Como parte desse recurso, o Cloud App Security identifica automaticamente os arquivos suspeitos e os detona para procurar por comportamentos suspeitos e indicadores de que o arquivo é mal-intencionado (malware).
Como parte dessa alteração, agora as políticas de detecção de malware incluem um campo Tipo de detecção, que permite filtrar por inteligência contra ameaças, bem como a área restrita.

- **Atualizações de Acesso Condicional**  
O Controle de Aplicativos de Acesso Condicional adicionou a capacidade de monitorar e bloquear as seguintes atividades:
  - Carregamentos de arquivos em aplicativo – habilitação de cenários que impedem o upload de extensões de malware conhecidas e garantia de que os usuários protejam arquivos com o AIP antes do carregamento.
  - Copiar e colar em qualquer aplicativo – implementação de controles robustos de exfiltração dos dados, que já incluíam controle de download, impressão e atividades personalizadas, como compartilhamento.
  - Enviar mensagem – garantia de que dados de PII, como senhas, não sejam compartilhados em ferramentas de colaboração populares, como Slack, Salesforce e Workplace by Facebook.
  - Agora, as políticas de sessão incluem modelos internos para permitir que sua organização habilite com facilidade os populares monitoramento e controle em tempo real de seus aplicativos aprovados, como o **Carregamento de blocos com base na inspeção de conteúdo em tempo real**.

## <a name="cloud-app-security-release-143"></a>Cloud App Security versão 143

Lançado em 17 de fevereiro de 2019

- **Implantação de escopo para instâncias de aplicativo**  
Agora a implantação de escopo pode ser configurada no nível da instância do aplicativo, permitindo maior granularidade e controle.
- **Aprimoramentos de função**  
  - Agora o Cloud App Security dá suporte às funções de administrador de dados e operador de segurança do Office 365. A função administrador de dados permite que os usuários gerenciem tudo relacionado ao arquivo e que exibam os relatórios do Cloud Discovery. Os operadores de segurança têm permissão para gerenciar alertas e exibir a configuração de políticas.
  - Agora, a função leitor de segurança tem a capacidade de configurar o agente SIEM, o que permite melhorar o escopo de permissão.

- **Suporte do Microsoft Flow**  
O Cloud App Security agora monitora as atividades dos usuários no Microsoft Flow. As atividades com suporte são aquelas relatadas pelo Flow para o log de auditoria do Office 365.

- **Agrupamento de entidade de alerta**  
A página **Alerta** agora agrupa entidades relacionadas que foram envolvidas em um alerta para ajudar na sua investigação.

## <a name="cloud-app-security-release-142"></a>Cloud App Security versão 142

Lançado em 3 de fevereiro de 2019

- **Configuração de política de sessão no Azure AD**  
Agora você pode configurar políticas de sessão para monitorar usuários ou bloquear downloads em tempo real diretamente no acesso condicional do Azure AD. Você ainda pode configurar políticas de sessão avançadas diretamente no Cloud App Security. Confira um tutorial dessa implantação em [Implantar o Controle de Aplicativos de Acesso Condicional para aplicativos do Azure AD](proxy-deployment-aad.md).

- **Consultas sugeridas e salvas para aplicativos OAuth**  
As consultas sugeridas foram adicionadas à página de aplicativos OAuth que fornecem modelos de investigação prontos para uso para filtrar seus aplicativos OAuth. As consultas sugeridas incluem filtros personalizados para identificar aplicativos arriscados, como aplicativos autorizados por administradores. As consultas salvas permitem salvar consultas personalizadas para uso futuro, como as consultas salvas disponíveis hoje nas páginas Log de atividades e Descoberta.

- **Configuração padrão de auditoria do Office 365**  
Se você quiser habilitar o monitoramento das atividades do Office 365 no Cloud App Security, agora será necessário habilitar a auditoria no [Centro de Conformidade e Segurança do Office](/office365/securitycompliance/turn-audit-log-search-on-or-off#turn-on-audit-log-search), que é resultado de uma [alteração na auditoria do Office 365](/office/office-365-management-api/office-365-management-activity-api-faq#what-happens-if-i-disable-auditing-for-my-office-365-organization-will-i-still-get-events-via-the-management-activity-api). Essa alteração só precisará ser executada se você ainda não tiver habilitado o monitoramento das atividades do Office 365 no Cloud App Security.

- **Suporte avançado para caixas de correio**  
O Cloud App Security agora dá suporte a duas novas ações de governança para caixas de correio:

  - **Expirar link compartilhado** – essa ação de governança fornece a capacidade de definir uma data de validade para um link compartilhado, depois disso ele não estará mais ativo.

  - **Alterar o nível de acesso do link de compartilhamento** – essa ação de governança fornece a capacidade de alterar o nível de acesso do link compartilhado somente na empresa, somente entre colaboradores e com o público.

- **Suporte a vários locais no OneDrive**  
Agora, o Cloud App Security fornece visibilidade total dos arquivos do OneDrive, mesmo se estiverem dispersos em várias localizações geográficas. A proteção agora está disponível para os arquivos localizados nos locais adicionais, bem como no local principal.

- **Melhoria na navegação do Portal**  
O portal do Cloud App Security foi aprimorado para melhorar sua navegação e alinhamento com os outros serviços de segurança da Microsoft, e para facilitar e simplificar o uso.

## <a name="cloud-app-security-release-141"></a>Cloud App Security versão 141

Lançado em 20 de janeiro de 2019

- **Aprimoramentos na avaliação de riscos na nuvem**  
  - A avaliação de risco do aplicativo Cloud foi aprimorada com duas novas experiências.
    - O novo atributo **Tipo de dados** avalia o tipo de conteúdo que os usuários podem carregar no aplicativo. É possível usar esse atributo para avaliar um aplicativo de acordo com a confidencialidade de cada tipo de dados em sua organização.
    - Para obter a visão geral de risco mais abrangente de um aplicativo, agora você pode facilmente passar da avaliação de risco do aplicativo para a avaliação de risco da empresa de hospedagem clicando no atributo **Empresa de hospedagem**.

- **Aprimoramento do contexto de arquivo para a investigação de alertas de detecção de anomalias**  
  - A investigação de detecção de anomalias foi aprimorada para permitir que você veja informações adicionais associadas aos arquivos envolvidos em um alerta. Quando os alertas são acionados para atividades incomuns relacionadas a arquivos (download, compartilhamento, exclusão), esse detalhamento fica disponível. Por exemplo, se a maioria dos arquivos afetados for da mesma pasta ou compartilhar a mesma extensão de arquivo, você verá essas informações na seção Risco adicional do alerta.

- **Consultas para investigação de arquivo**  
  - A capacidade do Cloud App Security de criar e salvar consultas personalizadas foi estendida para a página de **Arquivos**. As consultas na página **Arquivo** permitem que você crie modelos de consulta que podem ser reutilizados em investigação aprofundada.

## <a name="cloud-app-security-release-139-140"></a>Cloud App Security versão 139, 140

Lançado em 6 de janeiro de 2019

- **Alteração na detecção de arquivos**  
Agora, os arquivos compartilhados com todos no SharePoint e no OneDrive são considerados como **internos** [devido a alterações feitas no SharePoint e no OneDrive](https://support.microsoft.com/help/4089534/how-to-grant-the-everyone-claim-to-external-users-in-office-365). Portanto, se for detectado que um arquivo está compartilhado com todos, ele será tratado como um arquivo interno, o que afeta a forma como o arquivo é manipulado por políticas e exibido na página de arquivos.

- **Alteração no monitoramento de arquivos**  
O comportamento do monitoramento de arquivo padrão mudou para clientes novos e ociosos. Agora, você precisa ativar o monitoramento de arquivos para habilitar o recurso, em **Configurações** > **Arquivos**. Os clientes ativos existentes não serão afetados por essa alteração.

- **Ajuste avançado para políticas de detecção de anomalias**  
Agora, você pode afetar o mecanismo de detecção de anomalias para suprimir ou exibir alertas de acordo com suas preferências.
  - Na política Viagem Impossível, você pode definir o controle deslizante de sensibilidade para determinar o nível de comportamento anormal necessário antes que um alerta seja disparado.
  - Você também pode configurar se os alertas de atividade de um país infrequente, endereços IP anônimos, endereços IP suspeitos e viagens impossíveis devem analisar logons com falha e com êxito ou apenas logons bem-sucedidos.

- **Suporte a várias cadeias confiáveis**  
O Controle de Aplicativos de Acesso Condicional agora é compatível com a adição e o uso de vários certificados raiz confiáveis ou intermediários como uma forma de gerenciamento de dispositivo.

- **Nova função do Cloud Discovery** (distribuição gradual)  
Agora, o Cloud App Security fornece uma nova função de administrador para os usuários do Cloud Discovery. Essa função pode ser usada para definir o escopo do acesso de um usuário administrador apenas para as configurações e dados do Cloud Discovery no portal do Cloud App Security.

- **Suporte a rótulos unificados da Proteção de Informações da Microsoft** (distribuição gradual)  
O Cloud App Security agora dá suporte a rótulos unificados da Proteção de Informações da Microsoft. Para clientes que já [migraram os rótulos de classificação para o Centro de Segurança e Conformidade do Office 365](/azure/information-protection/configure-policy-migrate-labels), o Cloud App Security identificará e trabalhará com esses rótulos, conforme descrito em [Integrando com a Proteção de Informações do Azure](azip-integration.md).

**Suporte a rotulagem de arquivos PDF** (distribuição gradual)  
Para clientes que usam rótulos unificados, o Cloud App Security agora é compatível com a rotulagem automática para arquivos PDF.

## <a name="cloud-app-security-release-138"></a>Cloud App Security versão 138

Lançado em 9 de dezembro de 2018

- **Upload de log automático usando o Docker no Windows**  
Agora o Cloud App Security dá suporte ao upload automático de log para o Windows 10 (Fall Creators Update) e o Windows Server (versão 1709 e posterior) usando um Docker for Windows. Para mais informações e instruções sobre como isso pode ser configurado, confira [Docker no Windows local](discovery-docker-windows.md).

- O Cloud App Security integra-se ao [Microsoft Flow](/flow/getting-started) para fornecer guias estratégicos de orquestração e automação de alerta personalizada. Para saber mais sobre instruções de integração, confira [Integração com o Microsoft Flow](flow-integration.md).

## <a name="cloud-app-security-release-137"></a>Cloud App Security versão 137

Lançado em 25 de novembro de 2018

- **Suporte adicionado ao Dynamics**  
Agora o Cloud App Security conta com suporte para atividades do Microsoft Dynamics compatíveis no log de auditoria do Office 365.

- **Exame de conteúdo criptografado (versão prévia)**  
Agora o Cloud App Security possibilita examinar o conteúdo protegido pelos rótulos da Proteção de Informações do Azure. Assim é possível encontrar o conteúdo confidencial, mesmo em arquivos que já foram criptografados pela Proteção de Informações do Azure.

- **Atenção – nova terminologia!**  
Para proporcionar mais clareza, o nome dos recursos de permissões de aplicativos foi alterado para **aplicativos OAuth**.

## <a name="cloud-app-security-release-136"></a>Cloud App Security versão 136

Lançado em 11 de novembro de 2018

- **Atualizações do Cloud Discovery**  
O analisador de log personalizado foi aprimorado para dar suporte formatos adicionais e mais completos para logs de tráfego da web. Como parte desses aprimoramentos, agora os usuários podem incluir cabeçalhos personalizados para arquivos de log em CSV sem cabeçalhos, usar delimitadores especiais para arquivos com chave-valor, processar o formato de arquivo Syslog e mais.

- **Novas políticas de detecção de anomalias**  
Regras de manipulação suspeita da caixa de entrada: essa política cria um perfil do ambiente e dispara alertas quando regras suspeitas que excluem ou movem mensagens ou pastas são definidas na caixa de entrada de um usuário. Isso pode indicar que a conta de usuário está comprometida, que as mensagens foram ocultadas de forma intencional e que a caixa de correio está sendo usada para enviar spam e malware em sua organização.

- **Suporte para grupos nas políticas de permissão de aplicativos**  
Agora o Cloud App Security proporciona a capacidade de definir as políticas de permissão de aplicativo de forma mais granular com base nas associações de grupos dos usuários que autorizaram os aplicativos. Por exemplo, um administrador pode decidir por configurar uma política que revoga aplicativos incomuns se eles solicitarem permissões altas, somente se o usuário que autorizou as permissões for membro do grupo de administradores.

- **Agora, o Controle de Aplicativos de Acesso Condicional se integra ao aplicativos locais por meio do Proxy de Aplicativo do Azure Active Directory**  
  - O [Proxy de Aplicativo do Azure AD](/azure/active-directory/manage-apps/application-proxy) fornece SSO (logon único) e acesso remoto seguro para aplicativos Web hospedados no local.
  - Esses aplicativos Web no local agora podem ser roteados para o Microsoft Cloud App Security por meio do acesso condicional do Azure AD para fornecer controles e monitoramento em tempo real pelas políticas de [acesso](access-policy-aad.md) e [sessão](session-policy-aad.md).

## <a name="cloud-app-security-release-133-134-135"></a>Cloud App Security versão 133, 134, 135

Lançado em outubro de 2018

- **Novas políticas de detecção de anomalias a implantar gradualmente**  
  - A nova política Exfiltração dos dados para aplicativos não sancionados é habilitada automaticamente para alertar quando um usuário ou endereço IP estiver usando um aplicativo que não está aprovado para executar uma atividade que pode ser uma tentativa de extrair informações de sua organização.
    - A nova política Várias atividades de exclusão de VM executa o perfil do seu ambiente e aciona alertas quando usuários excluem várias VMs em uma única sessão, em relação à linha de base de sua organização.

- **Serviço de classificação de dados disponível para APAC**  
  - Agora a inspeção do serviço de classificação de dados está disponível para clientes do APAC. Confira alista completa do suporte regional em [Integração dos Serviços de Classificação de Dados da Microsoft](dcs-inspection.md).

- **Suporte do Cloud Discovery para i-Filter**  
  - O recurso de Cloud Discovery do Cloud App Security agora oferece suporte aprimorado para o analisador de syslog do i-Filter.

## <a name="cloud-app-security-release-132"></a>Cloud App Security versão 132

Lançado em 25 de setembro de 2018

- **O Controle de Aplicativos de Acesso Condicional para Office 365 está disponível na Visualização Pública**  
  - O Controle de Aplicativos de Acesso Condicional agora oferece suporte para Office 365 e para qualquer aplicativo configurado com o Open ID Connect.
  - Forneça comentários em uma sessão: essa nova ferramenta permite fornecer comentários para a equipe do Cloud App Security em relação ao desempenho de um aplicativo na sessão controle, diretamente na sessão.

- **Integração nativa com o Microsoft Defender ATP para Shadow IT Discovery além da sua corporação**  
  - O Microsoft Cloud App Security agora se integra de forma nativa à Windows Defender ATP (Proteção Avançada contra Ameaças) para fornecer recursos de descoberta de TI sombra sem implantação para o uso dentro e fora da rede corporativa de aplicativos de nuvem.  Isso permite executar o Cloud Discovery em computadores, mesmo que eles não estejam em sua rede corporativa. Também permite investigações baseadas em computadores: depois de identificar um usuário suspeito, é possível verificar todas as máquinas que ele acessou para identificar possíveis riscos; se você identificar uma máquina suspeita, poderá verificar todos os usuários que a usaram para investigar possíveis riscos. Para saber mais, confira Integração da Proteção Avançada contra Ameaças do Windows Defender com o [Microsoft Cloud App Security](wdatp-integration.md).

- **Inspeção de conteúdo para arquivos criptografados**  
  - O Cloud App Security dá suporte à inspeção de conteúdo de arquivos criptografados que foram protegidos usando a Proteção de Informações do Azure. Agora é possível inspecionar esses arquivos criptografados para propostas de reclassificação e inspecionar uma exposição adicional de DLP e violações da política de segurança.

## <a name="cloud-app-security-release-131"></a>Cloud App Security versão 131

Lançado em 2 de setembro de 2018

- **Revogar permissões automaticamente em aplicativos OAuth suspeitos**  
Você pode controlar a quais aplicativos OAuth seus usuários têm acesso, revogando as permissões para aplicativos do OAuth no Office, Google ou Salesforce. Quando você cria uma **Política de permissão de aplicativo**, pode definir a política para revogar a permissão de um aplicativo.

- **Analisador adicional interno do Cloud Discovery com suporte**  
O Cloud Discovery agora dá suporte ao formato de log do Forcepoint Web Security Cloud.

## <a name="cloud-app-security-release-130"></a>Cloud App Security versão 130

Lançado em 22 de agosto de 2018

- **Nova barra de menus**  
Para oferecer uma experiência de administrador mais consistente nos produtos do Microsoft 365 e permitir que você alterne com mais facilidade entre as soluções de segurança da Microsoft, a barra de menus do portal do Cloud App Security foi movida para o lado esquerdo da tela. Essa experiência de navegação consistente ajuda você a se orientar ao mudar de um portal de segurança da Microsoft para outro.

- **Impactar a pontuação do aplicativo OAuth**  
Você pode enviar comentários à equipe do Cloud App Security para informar se há um aplicativo OAuth descoberto em sua organização que parece mal-intencionado. Esse novo recurso permite que você faça parte de nossa comunidade de segurança e aprimore a análise e a pontuação de risco do aplicativo OAuth. Para mais informações, confira [Gerenciar aplicativo permiOAuth appsssions](manage-app-permissions.md).

- **Novos analisadores do Cloud Discovery**  
Os analisadores do Cloud Discovery agora dão suporte a iboss Secure Cloud Gateway e Sophos XG.

## <a name="cloud-app-security-release-129"></a>Cloud App Security versão 129

Lançado em 5 de agosto de 2018

- **Novas políticas de detecção de anomalias – regras de email suspeito**  
Foram incluídas novas políticas de detecção de anomalias que detectam regras de encaminhamento de email suspeito, por exemplo, se um usuário criou uma regra de caixa de entrada que encaminha uma cópia de todos os emails para um endereço externo.

- Essa versão inclui correções e melhorias para vários problemas.

## <a name="cloud-app-security-release-128"></a>Cloud App Security versão 128

Lançado em 22 de julho de 2018

- **Ações de aplicativos OAuth em vários aplicativos**  
Para aplicativos OAuth que receberam permissões de aplicativo, é possível vetar ou aprovar vários aplicativos em uma única ação. Por exemplo, você pode revisar todos os aplicativos que receberam permissões por usuários em sua organização, selecionar todos os aplicativos que você queira vetar e clicar em vetar aplicativos para revogar todo o consentimento dado, e os usuários não poderão mais conceder permissões para esses aplicativos.  Para saber mais, confira [Gerenciar aplicativos OAuth](manage-app-permissions.md).

- **Suporte aprimorado para aplicativos do Azure**  
Para o Azure, estamos implementando gradativamente a capacidade de detectar aplicativos como atividades de conta de usuário realizadas por aplicativos do Azure (internos e externos). Isso permite criar políticas que alertarão você se um aplicativo realizar atividades inesperadas e não autorizadas. Para saber mais, confira [Conectar o Azure ao Microsoft Cloud App Security](connect-azure-to-microsoft-cloud-app-security.md).

- **Mecanismo de Classificação de Dados atualizado com novos tipos confidenciais do GDPR**  
O [Serviço de Classificação de Dados do Cloud App Security](dcs-inspection.md) adicionou novos tipos confidenciais do GDPR a nosso Mecanismo de Classificação de Dados para permitir a detecção de conteúdo relacionado ao GDPR em seus arquivos.

- **Atualizações do Catálogo de Aplicativos de Nuvem**  
O Catálogo de Aplicativos de Nuvem inclui uma categoria de risco legal (além de Geral, Segurança e Conformidade) para ajudar você a gerenciar a privacidade dos dados e a conformidade da propriedade, o que inclui a preparação para o GDPR.
Para ajudar a avaliar a preparação para o GDPR de cada aplicativo de nuvem, a nova categoria de risco contém a declaração de preparação para o GDPR do serviço de nuvem e o status de cada controle da estrutura do GDPR.
Observe que, como parte dessa melhoria, os seguintes atributos de risco foram movidos de outras categorias de risco para a categoria Legal:
  - DMCA
  - Propriedade dos dados
  - Política de retenção de dados

  Além disso, a nova categoria de risco é classificada separadamente para que você possa configurar o peso da pontuação de acordo com suas preferências e prioridades. Confira mais informações em [Pontuação de risco](risk-score.md).

- **Nova consulta sugerida: pronto para o GDPR**  
Há uma nova consulta sugerida para permitir que você identifique aplicativos descobertos prontos para o GDPR. Como o GDPR recentemente se tornou uma prioridade máxima para administradores de segurança, essa consulta ajuda você a identificar facilmente os aplicativos que estão em conformidade com o regulamento, assim como mitigar ameaças por meio da avaliação do risco de aplicativos "não infectados".

## <a name="cloud-app-security-release-127"></a>Cloud App Security versão 127

Lançado em 8 de julho de 2018

- Agora você tem a capacidade de ver atividades genéricas do Office 365. No **Log de atividades** e nas **Políticas de atividades**, agora você pode filtras as atividades do Office 365 como **Não especificadas**. A revisão dessas atividades permite investigar informações sobre atividades executadas que ainda não estão classificadas por tipo no Cloud App Security, e você pode usar essas atividades a fim de enviar solicitações à equipe de Cloud App Security para criar novos tipos de atividade com base nessas atividades.

## <a name="cloud-app-security-release-126"></a>Cloud App Security versão 126

Lançado em 24 de junho de 2018

- **Disponibilidade geral do Controle de Aplicativos de Acesso Condicional**  
O Controle de Aplicativos de Acesso Condicional do Microsoft Cloud App Security (proxy reverso) já está disponível para qualquer aplicativo SAML. O Controle de Aplicativos de Acesso Condicional se integra diretamente às suas políticas de acesso condicional do Azure AD para **monitorar e controlar as sessões de seus usuários em tempo real**, sem interferir na produtividade deles. Desde a primeira versão prévia do recurso, muitas funcionalidades e aprimoramentos foram incluídos, como:
  - A capacidade de criar uma [política de acesso](access-policy-aad.md) para gerenciar o acesso aos mesmos aplicativos de clientes nativos, além de criar uma política de sessão para o tráfego do navegador.
  - O processo de integração do aplicativo foi simplificado para dar suporte a aplicativos SAML personalizados em sua organização.
  - Como parte da rede mundial do Azure, a integração e a interface foram aprimoradas para uma experiência perfeita para usuários localizados em qualquer lugar do mundo.

- **Disponibilidade geral da inspeção de conteúdo com o Serviço de Classificação de Dados da Microsoft**  
A integração do Microsoft Cloud App Security com os Serviços de Classificação de Dados da Microsoft já está disponível. Essa integração permite a você utilizar o Serviço de classificação de dados da Microsoft nativamente para classificar os arquivos em seus aplicativos de nuvem. Saiba mais em [Integração dos Serviços de Classificação de Dados da Microsoft](dcs-inspection.md). Atualmente, esse recurso só está disponível nos EUA e na Europa (exceto na França).

- **Relatório executivo do Cloud Discovery**  
O Microsoft Cloud App Security está lançando gradualmente a capacidade de gerar um relatório executivo em PDF do Cloud Discovery. Esse relatório fornece uma visão geral do uso da TI sombra identificada em sua organização, destacando os principais aplicativos e usuários em uso no geral e em categorias líderes, e se concentra no risco que a TI sombra representa em sua organização. Além disso, o relatório fornece uma lista de recomendações sobre como melhorar a visibilidade e o controle da TI sombra em sua organização. Use esse relatório para garantir que riscos e ameaças em potencial sejam removidos e que sua organização permaneça protegida e segura.

- **Detecção de malware**  
A funcionalidade de detecção de malware está sendo lançada gradualmente para **detectar arquivos mal-intencionados automaticamente no armazenamento em nuvem**, independentemente do tipo de arquivo. O Microsoft Cloud App Security usa a inteligência contra ameaças da Microsoft para reconhecer se determinados arquivos estão associados a ataques de malware conhecidos ou se são potencialmente mal-intencionados. Confira mais informações em [Políticas de detecção de anomalias](anomaly-detection-policy.md).

- **Correção automatizada para atividades suspeitas**  
Agora é possível definir ações de correção automáticas de sessão suspeita disparadas pelas políticas de detecção de anomalias. Esse aprimoramento permite que você receba alertas instantaneamente em caso de violação e **aplique ações de governança de forma automática**, como suspender um usuário. Confira mais informações em [Políticas de detecção de anomalias](anomaly-detection-policy.md#adp-automated-gov).

- **Avaliação da configuração de segurança do Azure**  
O Microsoft Cloud App Security está lançando gradualmente a capacidade de fazer uma avaliação da configuração de segurança do ambiente do Azure e oferece recomendações sobre configurações ausentes e controle de segurança. Por exemplo, ele informará se você não tiver MFA para usuários administrativos. Confira mais informações em [Integração com o Gerenciamento da situação de segurança na nuvem](security-config.md).

- **Detecção automatizada de aplicativos OAuth suspeitos**  
Além da investigação existente dos aplicativos OAuth conectados ao ambiente, o Microsoft Cloud App Security agora está lançando gradualmente a capacidade de definir notificações automatizadas para informá-lo quando um aplicativo OAuth atende a determinados critérios. Por exemplo, você poderá receber um alerta automaticamente quando houver aplicativos que exijam um nível de permissão elevado e que tenham sido autorizados por mais de 50 usuários. Para mais informações, confira [Políticas de permissão de aplicativo](app-permission-policy.md).

- **Suporte ao gerenciamento de MSSP (provedores de serviço de segurança gerenciada)**  
O Microsoft Cloud App Security agora fornece uma melhor experiência de gerenciamento para MSSPs. Os usuários externos agora podem ser configurados como administradores e atribuídos a qualquer uma das [funções disponíveis atualmente no Microsoft Cloud App Security](manage-admins.md). Além disso, para permitir que os MSSPs forneçam serviços entre vários locatários de clientes, os administradores que têm direitos de acesso a mais de um locatário agora podem alternar facilmente os locatários no portal. Para obter informações sobre como gerenciar administradores, confira [Gerenciar administradores](manage-admins.md).

- **Disponibilidade geral da integração com DLP externa**  
O Microsoft Cloud App Security permite que você [utilize os investimentos existentes em sistemas de classificação de terceiros](icap-stunnel.md), como soluções de DLP (prevenção de perda de dados) e permite examinar o conteúdo de aplicativos de nuvem usando as implantações em execução no seu ambiente. Para obter mais informações, confira [Integração de DLP externa](icap-stunnel.md).

## <a name="cloud-app-security-release-125"></a>Cloud App Security versão 125

Lançamento em 10 de junho de 2018

- **Novo recurso de investigação dos principais usuários:**  
O Microsoft Cloud App Security adicionou um novo widget de investigação no painel que mostra os principais usuários pelo número de alertas de detecção de ameaças em aberto. Este widget de investigação permite que você concentre sua investigação de ameaças em usuários com o maior número de sessões suspeitas.

- **Suporte para buckets AWS S3:**  
Agora o Microsoft Cloud App Security pode detectar buckets AWS S3 e seus níveis de compartilhamento. Isso fornece alertas e visibilidade em buckets AWS publicamente acessíveis. Também permite que você crie políticas com base em buckets e aplique governança automática. Além disso, há um novo modelo de política disponível chamado **AWS (buckets S3 acessíveis publicamente)** que você pode usar para criar facilmente uma política para controlar seu armazenamento AWS. Para habilitar esses novos recursos, atualize seus aplicativos conectados do AWS adicionando as novas permissões descritas em [Conectar o AWS](connect-aws-to-microsoft-cloud-app-security.md).

- **Privilégios de administrador com base em grupos de usuários**:  
Agora você pode definir permissões administrativas para administradores do Microsoft Cloud App Security por grupo de usuários. Por exemplo, você pode definir um usuário específico como administrador somente para usuários na Alemanha. Isso permitirá ao usuário exibir e modificar informações no Microsoft Cloud App Security somente para o grupo de usuários "Alemanha – todos os usuários". Para saber mais, confira [Gerenciar acesso de administrador](manage-admins.md).

## <a name="cloud-app-security-release-124"></a>Cloud App Security versão 124

Lançamento: 27 de maio de 2018

- **Avaliação de risco do GDPR adicionada ao Catálogo de aplicativos de nuvem**  
13 novos fatores de risco foram adicionados ao Microsoft Cloud App Security. Esses fatores de risco seguem a lista de verificação da estrutura do GDPR para permitir que você avalie os aplicativos no Catálogo de aplicativos de nuvem de acordo com as regulamentações do GDPR.

- **Integrado ao Serviço de classificação de dados da Microsoft**  
Agora o Microsoft Cloud App Security permite a você utilizar o Serviço de classificação de dados da Microsoft nativamente para classificar os arquivos em seus aplicativos de nuvem.   
O Serviço de classificação de dados da Microsoft fornece uma experiência unificada de proteção de informações no Office 365, na Proteção de Informações do Azure e no Microsoft Cloud App Security. Ele permite que você estenda a mesma estrutura de classificação de dados para os aplicativos de nuvem de terceiros protegidos pelo Microsoft Cloud App Security, aproveitando as decisões que você já tomou em um número ainda maior de aplicativos.

- **Conectar ao Microsoft Azure** (distribuição gradual)  
O Microsoft Cloud App Security está estendendo seus recursos de monitoramento de IaaS para além do Amazon Web Services e agora dá suporte ao Microsoft Azure. Isso permite que você se conecte e monitore perfeitamente todas as suas assinaturas do Azure com o Cloud App Security. Essa conexão fornece um conjunto avançado de ferramentas para proteger seu ambiente do Azure, incluindo:

  - Visibilidade de todas as atividades realizadas por meio do portal

  - Capacidade de criar políticas personalizadas para alertar sobre comportamentos indesejados, bem como a capacidade de proteger automaticamente possíveis usuários suspeitos, suspendendo-os ou forçando uma nova entrada.

  - Nosso mecanismo de detecção de anomalias abrange todas as atividades do Azure e alerta automaticamente sobre todos os comportamentos suspeitos no portal do Azure, como viagem impossível, atividades em massa suspeitas e atividade em um novo país.  

  Para saber mais, confira [Conectar o Azure ao Microsoft Cloud App Security](connect-azure-to-microsoft-cloud-app-security.md).

- **Implantação com escopo** (distribuição gradual)  
O Microsoft Cloud App Security fornece às empresas a capacidade de determinar granularmente quais usuários elas desejam monitorar e proteger com base na associação de grupo. Esse recurso permite selecionar usuários cujas atividades não serão exibidas para nenhum dos aplicativos protegidos. O recurso de monitoramento com escopo definido é especialmente útil para:
  - Conformidade – se os seus regulamentos de conformidade exigirem que você não monitore usuários de determinados países devido a regulamentos locais.
  - Licenciamento – se você quiser monitorar menos usuários para permanecer dentro dos limites de suas licenças do Microsoft Cloud App Security.
  Para saber mais, confira [Implantação com escopo](scoped-deployment.md).

- **Alerta de aplicativo violado para aplicativos descobertos**  
 Agora temos um alerta interno para notificá-lo quando qualquer um dos aplicativos descobertos de um locatário for violado. O alerta fornecerá informações sobre a hora e data da violação e quais usuários usaram o aplicativo, além de vincular fontes publicamente disponíveis que fornecem informações sobre a violação.

- **Novo servidor de email**  
 O servidor de email do Cloud App Security foi alterado e usa intervalos de endereços IP diferentes. Para garantir que você possa receber notificações, adicione os novos endereços IP à sua lista de permissões de antispam. Para usuários que personalizam suas notificações, o Microsoft Cloud App Security permite que você use um serviço de email de terceiros, o MailChimp&reg;. Para obter a lista de endereços IP do servidor de email e instruções para habilitar o trabalho com o MailChimp, confira [Requisitos de rede](network-requirements.md#mail-server) e [Configurações de email](mail-settings.md).

## <a name="cloud-app-security-release-123"></a>Cloud App Security versão 123

Lançado em 13 de maio de 2018

- **Definição de escopo da política de detecção de anomalias**:  
Agora, as políticas de detecção de anomalias podem ter escopos definidos. Isso permite definir cada política de detecção de anomalias para incluir apenas usuários ou grupos específicos e para excluir determinados usuários ou grupos. Por exemplo, você pode definir a detecção de Atividade de região pouco frequente para ignorar um usuário específico que viaja com frequência.

## <a name="cloud-app-security-release-122"></a>Cloud App Security versão 122

Lançado em 29 de abril de 2018

- Distribuição gradual: Agora você pode **definir permissões administrativas para administradores do Microsoft Cloud App Security por aplicativo**. Por exemplo, você pode definir um usuário específico como administrador somente para o G Suite. Isso permitiria ao usuário exibir e modificar no Microsoft Cloud App Security apenas informações exclusivamente relacionadas ao G Suite. Para saber mais, confira [Gerenciar acesso de administrador](manage-admins.md).

- Distribuição gradual: **As funções de administrador do Okta agora estão visíveis** no Microsoft Cloud App Security e estão disponíveis para cada função como uma marca em **Configurações** > **Grupos de usuários**.

## <a name="cloud-app-security-release-121"></a>Cloud App Security versão 121

Lançado em 22 de abril de 2018

- A visualização pública do **Controle de Aplicativos de Acesso Condicional (anteriormente conhecido como Cloud App Security Proxy)** foi aprimorada com recursos que facilitam a visibilidade avançada e o controle de vários aplicativos. Agora você pode criar uma Política de sessão com um filtro *Tipo de atividade*, para monitorar e bloquear uma variedade de atividades específicas do aplicativo. Esse novo filtro aprimora os recursos de controle de download de arquivo existentes, para fornecer a você um controle abrangente dos aplicativos em sua organização, e trabalha em conjunto com o acesso condicional do Azure Active Directory, para fornecer visibilidade em tempo real e controle de sessões de usuário suspeitas — por exemplo, sessões com usuários de colaboração B2B ou usuários provenientes de um dispositivo não gerenciado. Para mais informações, confira [Políticas da sessão](session-policy-aad.md).

- Distribuição gradual: As **políticas de detecção de anomalias do Cloud App Security foram aprimoradas** para incluir dois novos tipos de detecção de ameaças: atividade de ransomware e atividade de usuário encerrado. O Cloud App Security ampliou seus recursos de detecção de ransomware com a detecção de anomalias para garantir uma cobertura mais abrangente contra ataques sofisticados de ransomware. Usando nossa experiência de pesquisa de segurança para identificar os padrões comportamentais que refletem a atividade de ransomware, o Cloud App Security garante uma proteção holística e robusta. A atividade de usuário encerrado permite monitorar as contas de usuários encerrados, que podem ter sido desprovisionados de aplicativos corporativos, mas, em muitos casos, ainda mantêm o acesso a determinados recursos corporativos. Confira mais informações em [Obter análise comportamental instantânea e detecção de anomalias](anomaly-detection-policy.md).

## <a name="cloud-app-security-release-120"></a>Cloud App Security versão 120

Lançado em 8 de abril de 2018

- Para o Office 365 e o AAD, estamos implementando gradativamente a capacidade de detectar aplicativos internos como atividades de conta de usuário realizadas pelos aplicativos do Office 365 e do AAD (internos e externos). Isso permite criar políticas que alertarão você se um aplicativo realizar atividades inesperadas e não autorizadas.

- Ao exportar uma lista de permissões de aplicativo para csv, campos adicionais, como editor, nível de permissões e uso da comunidade, são incluídos para auxiliar no processo de conformidade e investigação.

- O aplicativo conectado do ServiceNow foi aprimorado para que as atividades de serviço interno não sejam mais registradas como realizadas por "Convidado" e não disparem mais alertas de falsos positivos. Agora, essas atividades são representadas como N/A, igual a todos os outros aplicativos conectados.

## <a name="cloud-app-security-release-119"></a>Cloud App Security versão 119

Lançada em 18 de março de 2018

- A página de intervalos de endereços IP inclui os endereços IP internos que são descobertos pelo Cloud App Security. Isso inclui endereços IP para serviços de nuvem identificados, como o Azure e o Office 365, bem como o feed de Inteligência contra ameaças, que aprimora automaticamente os endereços IP com informações sobre endereços IP suspeitos conhecidos.

- Quando o Cloud App Security tenta executar uma ação de governança em um arquivo, mas falha porque o arquivo está bloqueado, ele agora tenta novamente a ação de governança de forma automática.

## <a name="cloud-app-security-release-118"></a>Cloud App Security versão 118

Lançado em 4 de março de 2018

- Agora você pode aproveitar os recursos de monitoramento e descoberta de TI sombra do Microsoft Cloud App Security em seus próprios aplicativos personalizados. A nova capacidade de adicionar aplicativos personalizados ao Cloud Discovery permite que você monitore o uso do aplicativo e seja alertado sobre alterações no padrão de uso. Para obter mais informações, confira [Proteger seus aplicativos personalizados](cloud-discovery-custom-apps.md). Esse recurso está sendo implantado gradativamente.

- As páginas de **Configurações** do portal do Cloud App Security foram reformuladas. O novo design consolida todas as páginas de configurações e fornece funcionalidade de pesquisa e um design aprimorado.

- Agora, o Cloud Discovery dá suporte a firewalls e streaming de log da Web de firewall da Série F da Barracuda.

- A funcionalidade de pesquisa nas páginas de usuário e endereço IP agora habilita o preenchimento automático para facilitar a localização do que você estiver procurando.

- Agora você pode executar ações em massa nas páginas de configurações de Excluir entidades e Excluir endereço IP. Desse modo, é fácil selecionar vários usuários e grupos ou endereços IP e excluí-los do monitoramento como parte do Cloud Discovery em sua organização.

## <a name="cloud-app-security-release-117"></a>Cloud App Security versão 117

Lançado em 20 de fevereiro de 2018

- A integração profunda do Cloud App Security com a Proteção de Informações do Azure agora permite que você proteja os arquivos no G Suite. Esse recurso de visualização pública permite examinar e classificar arquivos no G Suite, e aplicar automaticamente os rótulos da Proteção de Informações do Azure para proteção. Confira mais informações em [Integração da Proteção de Informações do Azure](azip-integration.md).

- Agora, o Cloud Discovery dá suporte a [Digital Arts i-FILTER](https://www.daj.jp/en/products/if/).

- A tabela de agentes do SIEM agora inclui mais detalhes para um gerenciamento mais fácil.

## <a name="cloud-app-security-release-116"></a>Cloud App Security versão 116

Lançado em 4 de fevereiro de 2018

- A política de detecção de anomalias do Cloud App Security foi aprimorada com novas **detecções baseadas em cenários**, incluindo viagem impossível, atividade de um endereço IP suspeito e várias tentativas de logon com falha. As novas políticas são habilitadas automaticamente, fornecendo uma detecção de ameaças pronta para uso em seu ambiente de nuvem. Além disso, as novas políticas expõem mais dados do mecanismo de detecção do Cloud App Security para ajudar a agilizar o processo de investigação e conter as ameaças em andamento. Confira mais informações em [Obter análise comportamental instantânea e detecção de anomalias](/cloud-app-security/anomaly-detection-policy).

- Distribuição gradual: agora, o Cloud App Security correlaciona os usuários e suas contas nos aplicativos SaaS. Assim, você pode investigar todas as atividades com facilidade, em todos os diversos aplicativos SaaS correlacionados, em qualquer aplicativo ou conta utilizados.

- Distribuição gradual: agora, o Cloud App Security dá suporte a várias instâncias do mesmo aplicativo conectado. Se você tiver várias instâncias, por exemplo, do Salesforce (uma para vendas, uma para marketing), será possível conectá-las ao Cloud App Security e gerenciá-las no mesmo console para criar políticas granulares e aprofundar a investigação.

- Os analisadores do Cloud Discovery agora dão suporte a dois formatos adicionais de Ponto de verificação, XML e KPC.

## <a name="cloud-app-security-release-115"></a>Cloud App Security versão 115

Lançado em 21 de janeiro de 2018

- Essa versão oferece uma experiência aprimorada ao selecionar pastas específicas em políticas de arquivos. Agora, você pode facilmente exibir e selecionar várias pastas a incluir em uma política.
- Na página **Aplicativos descobertos**:
  - O recurso de marcação em lote possibilita aplicar marcas personalizadas (além das marcas sancionado e não sancionado).
  - Ao **Gerar um relatório de endereços IP** ou **Gerar um relatório de usuários**, agora os relatórios exportados informam se o tráfego foi proveniente de aplicativos sancionados ou não.
- Agora, você pode solicitar o novo conector de aplicativos de API diretamente para a equipe do Microsoft Cloud App Security no portal, na página **Conectar um aplicativo**.

## <a name="cloud-app-security-release-114"></a>Cloud App Security versão 114

Lançado em 7 de janeiro de 2018

- A partir da versão 114, implantaremos gradualmente a capacidade de criar e salvar consultas personalizadas nas páginas Aplicativos descobertos e Log de atividades. As consultas personalizadas possibilitam criar modelos de filtro que podem ser reutilizados em investigações detalhadas. Além disso, as **Consultas sugeridas** foram adicionadas a fim de fornecer modelos de investigação prontos para uso para filtrar suas atividades e aplicativos descobertos. As **Consultas sugeridas** incluem filtros personalizados que identificam riscos, como atividades de usurpação de identidade, atividades de administrador, aplicativos de armazenamento em nuvem suspeitos e sem conformidade, aplicativos empresariais com criptografia fraca e riscos à segurança. Você pode usar as **Consultas sugeridas** como ponto inicial e modificá-las como desejar, para depois salvá-las como uma nova consulta. Confira mais informações em [Consultas e filtros de atividades](activity-filters-queries.md) e [Consultas e filtros de aplicativos descobertos](discovered-app-queries.md).

- Agora, você pode verificar o status atual do serviço do Cloud App Security acessando [status.cloudappsecurity.com](https://status.cloudappsecurity.com) ou diretamente no portal ao clicar em **Ajuda**>**Status do sistema**.

## <a name="see-also"></a>Consulte Também

Confira uma descrição das versões anteriores às listadas aqui em [Versões anteriores do Microsoft Cloud App Security](release-note-archive.md).

[!INCLUDE [Open support ticket](includes/support.md)]

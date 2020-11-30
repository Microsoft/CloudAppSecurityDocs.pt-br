---
title: Arquivos de atualizações anteriores do Cloud App Security
description: Este artigo é um arquivo que descreve as atualizações feitas em lançamentos anteriores do Cloud App Security.
ms.date: 11/25/2020
ms.topic: conceptual
ms.openlocfilehash: 50f8bc735743d1506ac9ad18e6b10b659de7ab6e
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96315541"
---
# <a name="past-release-archive-of-microsoft-cloud-app-security"></a>Arquivo Morto de atualizações anteriores do Microsoft Cloud App Security

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Este artigo é um arquivo que descreve as atualizações feitas em lançamentos anteriores do Cloud App Security. Para ver a lista de novidades, confira [Novidades sobre o Cloud App Security](release-notes.md).

## <a name="updates-made-in-2019"></a>Atualizações feitas no 2019

### <a name="cloud-app-security-release-162-163-and-164"></a>Cloud App Security versão 162, 163 e 164

Lançado em 8 de dezembro de 2019

- **Alterar para atividades e alertas do SIEM no formato CEF**  
O [formato de URL do portal (CS1)](siem.md#sample-cloud-app-security-alerts-in-cef-format) para informações de atividades e alertas enviadas pelo Cloud App Security para SIEMs foi alterado para `https://<tenant_name>.portal.cloudappsecurity.com` e não contém mais o local do data center. Os clientes que usam a correspondência de padrões para a URL do portal devem atualizar o padrão para refletir essa alteração.

### <a name="cloud-app-security-release-160-and-161"></a>Cloud App Security versão 160 e 161

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

  - **Alterações suspeitas no serviço de log da AWS (versão prévia)** : alerta quando um usuário faz alterações no serviço de log CloudTrail. Por exemplo, os invasores geralmente desativam a auditoria no CloudTrail para ocultar os vestígios de seu ataque.

  - **Múltiplas atividades de criação de VM**: Alerta quando um usuário executa um número incomum de atividades de criação de VM em comparação com a linha de base aprendida. Agora se aplica ao AWS.

### <a name="cloud-app-security-release-159"></a>Cloud App Security versão 159

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

### <a name="cloud-app-security-release-158"></a>Cloud App Security, versão 158

Lançado em 15 de setembro de 2019

- **Personalizar o nome do relatório executivo do Cloud Discovery**  
O relatório executivo do Cloud Discovery fornece uma visão geral do uso de TI sombra em sua organização. Agora você tem a opção de personalizar o nome do relatório antes de gerá-lo. Para obter mais informações, confira [Gerar relatório executivo do Cloud Discovery](discovered-apps.md#generate-cloud-discovery-executive-report).

- **Novo relatório de visão geral das políticas**  
O Cloud App Security detecta correspondências de políticas e, quando definido, registra alertas que você pode usar para entender de forma avançada seu ambiente de nuvem. Agora você pode exportar um relatório de visão geral de políticas mostrando as métricas de alerta agregadas por política para ajudá-lo a monitorar, compreender e personalizar suas políticas para proteger melhor sua organização. Para obter mais informações sobre como exportar o relatório, confira o [Relatório de visão geral de políticas](control-cloud-apps-with-policies.md#policies-overview-report).

### <a name="cloud-app-security-release-157"></a>Cloud App Security, versão 157

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

### <a name="cloud-app-security-release-156"></a>Cloud App Security versão 156

Lançado em 18 de agosto de 2019

- **Novos analisadores de log do Cloud Discovery**  
O Cloud Discovery do Cloud App Security analisa uma ampla variedade de logs de tráfego para classificar e pontuar os aplicativos. Agora o Cloud Discovery inclui um analisador de log interno para dar suporte aos formatos de log Stormshield e Forcepoint LEEF.

- **Melhorias no log de atividades**  
O Cloud App Security agora oferece maior visibilidade sobre atividades não classificadas executadas por aplicativos em seu ambiente. Essas atividades estão disponíveis no Log de atividades e também nas Políticas de atividades. Para ver atividades não classificadas, no filtro **Tipo** selecione **Não especificado**. Para obter mais informações sobre filtros de atividade, confira [Filtros de atividade e consultas](activity-filters-queries.md).

- **Melhoria na investigação de usuários arriscados**  
O Cloud App Security fornece a capacidade de identificar usuários arriscados na página **Usuários e contas** por grupos, aplicativos e até mesmo funções específicos. Agora você também pode investigar os usuários da sua organização pela pontuação de **Prioridade de investigação**. Para obter mais informações, confira [Entenda a pontuação de prioridade de investigação](tutorial-ueba.md#risk-score).

- **Melhorias na política de atividades**  
Agora você pode criar alertas para a política de atividades com base nos objetos da atividade. Por exemplo, essa funcionalidade permite que você crie alertas para as alterações nas funções administrativas do Azure Active Directory. Para obter mais informações sobre os objetos da atividade, confira [Filtros de atividade](activity-filters-queries.md#activity-filters).

### <a name="cloud-app-security-release-155"></a>Cloud App Security, versão 155

Lançado em 4 de agosto de 2019

- **Novos modelos de políticas**  
Agora o Cloud App Security inclui novos modelos de políticas de atividade interna para melhores práticas de segurança do AWS.

- **Aviso: Fim do suporte para o TLS 1.0 e 1.1 em 8 de setembro**  
A Microsoft está migrando todos os seus serviços online para o protocolo TLS 1.2+ para fornecer a melhor criptografia. Portanto, a partir de 8 de setembro de 2019, o Cloud App Security não dará mais suporte a TLS 1.0 e 1.1, e as conexões que usam esses protocolos não serão compatíveis. Para obter mais informações sobre como a alteração afeta você, confira [nossa postagem no blog](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/End-of-support-for-TLS-1-0-and-1-1-in-Microsoft-Cloud-App/ba-p/770507).

- **Lógica aprimorada para atividades de entrada interativas (distribuição gradual)**  
Estamos fazendo a distribuição gradual de uma nova lógica para identificar se uma atividade de entrada do Azure Active Directory é interativa. A nova lógica aprimora a capacidade do Cloud App Security de exibir apenas atividades de entrada iniciadas por um usuário.

### <a name="cloud-app-security-release-154"></a>Cloud App Security versão 154

Lançado em 21 de julho de 2019

- **A integração e a implantação do Controle de Aplicativos de Acesso Condicional para qualquer aplicativo estão agora em disponibilidade geral**  
Desde que liberamos a versão prévia do Controle de Aplicativos de Acesso Condicional para qualquer aplicativo no mês passado, recebemos comentários excelentes e estamos empolgados em anunciar a disponibilidade geral. Essa nova funcionalidade permite implantar qualquer aplicativo Web para funcionar com políticas de acesso e sessão, permitindo monitoramento e controle eficientes em tempo real.

- **Avaliação da configuração de segurança do AWS**  
O Cloud App Security está lançando gradualmente a capacidade de fazer uma avaliação da configuração de segurança do ambiente do Amazon Web Services para conformidade com CIS e oferece recomendações sobre controles de segurança e configurações ausentes. Essa capacidade fornece às organizações uma exibição única para monitorar o status de conformidade de todas as contas do AWS conectadas.

- **Detecções de anomalias do aplicativo OAuth**  
Expandimos a nossa capacidade atual de detectar aplicativos OAuth suspeitos. Agora há quatro novas detecções prontas para uso, que analisam os metadados de aplicativos OAuth autorizados em sua organização para identificar aqueles que são potencialmente mal-intencionados.

### <a name="cloud-app-security-release-153"></a>Cloud App Security versão 153

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

### <a name="cloud-app-security-release-152"></a>Cloud App Security versão 152

Lançado em 23 de junho de 2019

- **Implantar Controle de Aplicativos de Acesso Condicional para qualquer aplicativo (versão prévia)**  
Temos a satisfação de anunciar que expandimos nosso suporte para o Controle de Aplicativos de Acesso Condicional para qualquer aplicativo Web, além do suporte avançado que já oferecíamos para [nossos aplicativos em destaque](proxy-intro-aad.md). Essa nova funcionalidade permite implantar qualquer aplicativo Web para funcionar com políticas de acesso e sessão, permitindo monitoramento e controle eficientes em tempo real. Por exemplo, você pode proteger downloads com rótulos de Proteção de Informações do Azure, bloquear o upload de documentos confidenciais, fornecer auditoria entre muitas outras ações.
- **Auditoria de atividades do Portal**  
O Cloud App Security audita todas as atividades do administrador no portal para fornecer monitoramento e investigação abrangentes das atividades executadas. Agora você também pode exportar até 90 dias de atividades para mais investigação e análise, por exemplo, auditoria de um administrador investigando um usuário específico ou exibindo alertas específicos. Para exportar o log, vá para a página de configurações **Gerenciar acesso de administrador**.
- **Saída da sessão personalizada do portal do Cloud App Security**  
Agora você pode configurar a saída automática de sessões de administrador para o portal que estejam ociosas por mais de um período especificado.

### <a name="cloud-app-security-release-151"></a>Cloud App Security, versão 151

Lançado em 9 de junho de 2019

- **UEBA híbrido – Integração nativa com o ATP do Azure (versão prévia)**  
O Cloud App Security agora nativamente é integrado com o ATP do Azure para fornecer uma exibição única de atividades de identidade em aplicativos de nuvem e sua rede local. Para saber mais, confira [Integração com a Proteção Avançada contra Ameaças do Azure](mdi-integration.md).
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

### <a name="cloud-app-security-release-150"></a>Cloud App Security, lançamento 150

Lançado em 26 de maio de 2019

- **Melhoria na exportação de alertas**  
Quando você exporta alertas para um arquivo CSV na página de **Alertas**, os resultados agora incluem a data de resolução ou de descarte do alerta.

### <a name="cloud-app-security-release-148-and-149"></a>Cloud App Security versão 148 e 149

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
Agora, ao conectar o Office 365 ao Microsoft Cloud App Security, você tem controle sobre quais cargas de trabalho deseja conectar. Por exemplo, os clientes interessados apenas em conectar o Office 365 para o monitoramento de atividade agora podem fazê-lo durante o processo de conexão ou ao editar um conector existente do Office 365. Como parte dessa alteração, o OneDrive e o SharePoint não serão mais mostrados como conectores separados, mas serão incluídos no conector do Office 365 como uma carga de trabalho de _arquivos do Office 365_. Os clientes com um conector existente do Office 365 não são afetados por essa alteração.

- **Suporte aprimorado do Teams**  
Agora você pode monitorar e bloquear o envio de mensagens no aplicativo Web do Teams em tempo real, configurando uma política de sessão com base no conteúdo confidencial.

### <a name="cloud-app-security-release-147"></a>Cloud App Security, versão 147

Lançado em 14 de abril de 2019

- **Novo analisador de log do Cloud Discovery**  
O Cloud App Security Cloud Discovery agora inclui um analisador de log integrado para dar suporte ao formato de log Palo Alto LEEF.

- **Atualizações de políticas de sessão**  
  - **Método adicional de inspeção de conteúdo para políticas de sessão**:  Agora, você terá a opção de escolher o Serviço de Classificação de Dados como um método de inspeção de conteúdo para arquivos ao definir uma política de sessão. O Serviço de Classificação de Dados oferece ao usuário uma ampla variedade de tipos confidenciais incorporados para identificar informações confidenciais.
  - **Melhoria no controle de permissões de arquivos nas políticas de sessão**:  Quando quiser criar uma política de sessão para controlar downloads usando o Cloud App Security, agora você poderá aplicar automaticamente permissões por usuário, como somente leitura para acesso a documentos após o download dos aplicativos na nuvem. Isso fornece um nível muito maior de flexibilidade e a capacidade de proteger as informações além dos rótulos corporativos pré-configuradas.
  - **Controle de download de arquivo grande**:  Quando a inspeção de conteúdo estiver habilitada nas políticas de sessão, você poderá controlar o que acontece quando um usuário tentar baixar um arquivo muito grande. Se o arquivo for grande demais para ser examinado no download, você poderá escolher se ele será bloqueado ou permitido.

### <a name="cloud-app-security-release-146"></a>Cloud App Security, versão 146

Lançada em 31 de março de 2019

- **Melhoria de viagem impossível**  
A detecção de viagem impossível foi aprimorada com suporte dedicado para países/regiões vizinhos.
- **Suporte de atributo adicional para o analisador de CEF genérico**  
O suporte do analisador de log do Cloud Discovery para o formato CEF genérico foi aprimorado para dar suporte a atributos adicionais.
- **Acesso com escopo aos relatórios do Cloud Discovery**  
Além da função de Administrador de descoberta, agora você pode definir o acesso com escopo a relatórios específicos de Descoberta. Esse aprimoramento permite configurar privilégios a dados de sites específicos e de unidades de negócios.
- **Novo suporte à função: Leitor global**  
O Microsoft Cloud App Security agora dá suporte à função de Leitor Global do Azure AD. O Leitor Global tem acesso completo somente para leitura de todos os aspectos do Microsoft Cloud App Security, mas não pode alterar nenhuma configuração nem realizar nenhuma ação.

### <a name="cloud-app-security-release-145"></a>Cloud App Security versão 145

Lançado em 17 de março de 2019

- **A integração do Microsoft Defender ATP agora está em disponibilidade geral**  
No ano passado, anunciamos a [integração com a Proteção Avançada contra Ameaças do Windows Defender](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Microsoft-Cloud-App-Security-and-Windows-Defender-ATP-better/ba-p/263265), que aprimora a Descoberta de TI Sombra em sua organização e ultrapassa a rede corporativa. [Habilitado com um único clique](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RWtNmG), estamos empolgados em anunciar que essa integração exclusiva já está disponível para o público em geral.
- **Suporte para Dynamics 365 CRM**  
O Cloud App Security adicionou monitoramento e controle em tempo real no Dynamics 365 CRM para que você possa proteger seus aplicativos de negócios e o conteúdo confidencial armazenado dentro deles. Para obter mais informações sobre o que pode ser feito com o Dynamics 365 CRM, confira [este artigo](proxy-intro-aad.md#how-it-works).

### <a name="cloud-app-security-release-144"></a>Cloud App Security versão 144

Lançada em 3 de março de 2019

- **Investigação de SecOps unificada para ambientes híbridos**  
Como muitas organizações têm ambientes híbridos, os ataques começam na nuvem e, em seguida, mudam para o local, o que significa que as equipes de SecOps precisam investigar esses ataques de vários locais. Ao combinar sinais de fontes locais e de nuvem, incluindo o Microsoft Cloud App Security, a Proteção Avançada contra Ameaças do Azure e a Azure AD Identity Protection, a Microsoft capacita os analistas de segurança ao fornecer informações de usuário e identidade unificadas em um único console, o que acaba com a necessidade de alternar entre soluções de segurança. Assim, suas equipes de SecOps terão mais tempo e as informações certas para melhorar a tomada de decisões e corrigir ativamente as ameaças e os riscos reais de identidade. Saiba mais em [Investigação de SecOps unificada para ambientes híbridos](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Unified-SecOps-Investigation-for-Hybrid-Environments/ba-p/360850)

- **Recursos de área restrita para detecção de malware** (distribuição gradual)  
Os recursos de detecção de malware do Cloud App Security estão sendo expandidos para incluir a capacidade de identificação de malware de dia zero por meio da tecnologia avançada de Área Restrita.  
Como parte desse recurso, o Cloud App Security identifica automaticamente os arquivos suspeitos e os detona para procurar por comportamentos suspeitos e indicadores de que o arquivo é mal-intencionado (malware).
Como parte dessa alteração, agora as políticas de detecção de malware incluem um campo Tipo de detecção, que permite filtrar por inteligência contra ameaças, bem como a área restrita.

- **Atualizações de Acesso Condicional**  
O Controle de Aplicativos de Acesso Condicional adicionou a capacidade de monitorar e bloquear as seguintes atividades:
  - Uploads de arquivo em qualquer aplicativo – habilitação de cenários que impedem o upload de extensões de malware conhecidas e garantia de que os usuários protejam arquivos com a Proteção de Informações do Azure antes do upload.
  - Copiar e colar em qualquer aplicativo – implementação de controles robustos de exfiltração dos dados, que já incluíam controle de download, impressão e atividades personalizadas, como compartilhamento.
  - Enviar mensagem – garantia de que dados pessoais, como senhas, não sejam compartilhados em ferramentas de colaboração populares, como Slack, Salesforce e Workplace by Facebook.
  - Agora, as políticas de sessão incluem modelos internos para permitir que sua organização habilite com facilidade os populares monitoramento e controle em tempo real de seus aplicativos aprovados, como o **Carregamento de blocos com base na inspeção de conteúdo em tempo real**.

### <a name="cloud-app-security-release-143"></a>Cloud App Security versão 143

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

### <a name="cloud-app-security-release-142"></a>Cloud App Security versão 142

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

### <a name="cloud-app-security-release-141"></a>Cloud App Security versão 141

Lançado em 20 de janeiro de 2019

- **Aprimoramentos na avaliação de riscos na nuvem**  
  - A avaliação de risco do aplicativo Cloud foi aprimorada com duas novas experiências.
    - O novo atributo **Tipo de dados** avalia o tipo de conteúdo que os usuários podem carregar no aplicativo. É possível usar esse atributo para avaliar um aplicativo de acordo com a confidencialidade de cada tipo de dados em sua organização.
    - Para obter a visão geral de risco mais abrangente de um aplicativo, agora você pode facilmente passar da avaliação de risco do aplicativo para a avaliação de risco da empresa de hospedagem clicando no atributo **Empresa de hospedagem**.

- **Aprimoramento do contexto de arquivo para a investigação de alertas de detecção de anomalias**  
  - A investigação de detecção de anomalias foi aprimorada para permitir que você veja informações adicionais associadas aos arquivos envolvidos em um alerta. Quando os alertas são acionados para atividades incomuns relacionadas a arquivos (download, compartilhamento, exclusão), esse detalhamento fica disponível. Por exemplo, se a maioria dos arquivos afetados for da mesma pasta ou compartilhar a mesma extensão de arquivo, você verá essas informações na seção Risco adicional do alerta.

- **Consultas para investigação de arquivo**  
  - A capacidade do Cloud App Security de criar e salvar consultas personalizadas foi estendida para a página de **Arquivos**. As consultas na página **Arquivo** permitem que você crie modelos de consulta que podem ser reutilizados em investigação aprofundada.

### <a name="cloud-app-security-release-139-140"></a>Cloud App Security versão 139, 140

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

## <a name="updates-made-in-2018"></a>Atualizações feitas no 2018

### <a name="cloud-app-security-release-138"></a>Cloud App Security versão 138

Lançado em 9 de dezembro de 2018

- **Upload de log automático usando o Docker no Windows**  
Agora o Cloud App Security dá suporte ao upload automático de log para o Windows 10 (Fall Creators Update) e o Windows Server (versão 1709 e posterior) usando um Docker for Windows. Para mais informações e instruções sobre como isso pode ser configurado, confira [Docker no Windows local](discovery-docker-windows.md).

- O Cloud App Security integra-se ao [Microsoft Flow](/flow/getting-started) para fornecer guias estratégicos de orquestração e automação de alerta personalizada. Para saber mais sobre instruções de integração, confira [Integração com o Microsoft Flow](flow-integration.md).

### <a name="cloud-app-security-release-137"></a>Cloud App Security versão 137

Lançado em 25 de novembro de 2018

- **Suporte adicionado ao Dynamics**  
Agora o Cloud App Security conta com suporte para atividades do Microsoft Dynamics compatíveis no log de auditoria do Office 365.

- **Exame de conteúdo criptografado (versão prévia)**  
Agora o Cloud App Security possibilita examinar o conteúdo protegido pelos rótulos da Proteção de Informações do Azure. Assim é possível encontrar o conteúdo confidencial, mesmo em arquivos que já foram criptografados pela Proteção de Informações do Azure.

- **Atenção – nova terminologia!**  
Para proporcionar mais clareza, o nome dos recursos de permissões de aplicativos foi alterado para **aplicativos OAuth**.

### <a name="cloud-app-security-release-136"></a>Cloud App Security versão 136

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

### <a name="cloud-app-security-release-133-134-135"></a>Cloud App Security versão 133, 134, 135

Lançado em outubro de 2018

- **Novas políticas de detecção de anomalias a implantar gradualmente**  
  - A nova política Exfiltração dos dados para aplicativos não sancionados é habilitada automaticamente para alertar quando um usuário ou endereço IP estiver usando um aplicativo que não está aprovado para executar uma atividade que pode ser uma tentativa de extrair informações de sua organização.
    - A nova política Várias atividades de exclusão de VM executa o perfil do seu ambiente e aciona alertas quando usuários excluem várias VMs em uma única sessão, em relação à linha de base de sua organização.

- **Serviço de classificação de dados disponível para APAC**  
  - Agora a inspeção do serviço de classificação de dados está disponível para clientes do APAC. Confira alista completa do suporte regional em [Integração dos Serviços de Classificação de Dados da Microsoft](dcs-inspection.md).

- **Suporte do Cloud Discovery para i-Filter**  
  - O recurso de Cloud Discovery do Cloud App Security agora oferece suporte aprimorado para o analisador de syslog do i-Filter.

### <a name="cloud-app-security-release-132"></a>Cloud App Security versão 132

Lançado em 25 de setembro de 2018

- **O Controle de Aplicativos de Acesso Condicional para Office 365 está disponível na Visualização Pública**  
  - O Controle de Aplicativos de Acesso Condicional agora oferece suporte para Office 365 e para qualquer aplicativo configurado com o Open ID Connect.
  - Forneça comentários em uma sessão: essa nova ferramenta permite fornecer comentários para a equipe do Cloud App Security em relação ao desempenho de um aplicativo na sessão controle, diretamente na sessão.

- **Integração nativa com o Microsoft Defender ATP para Shadow IT Discovery além da sua corporação**  
  - O Microsoft Cloud App Security agora se integra de forma nativa à Windows Defender ATP (Proteção Avançada contra Ameaças) para fornecer recursos de descoberta de TI sombra sem implantação para o uso dentro e fora da rede corporativa de aplicativos de nuvem.  Isso permite executar o Cloud Discovery em computadores, mesmo que eles não estejam em sua rede corporativa. Também permite investigações baseadas em computadores: depois de identificar um usuário suspeito, é possível verificar todas as máquinas que ele acessou para identificar possíveis riscos; se você identificar uma máquina suspeita, poderá verificar todos os usuários que a usaram para investigar possíveis riscos. Para saber mais, confira Integração da Proteção Avançada contra Ameaças do Windows Defender com o [Microsoft Cloud App Security](mde-integration.md).

- **Inspeção de conteúdo para arquivos criptografados**  
  - O Cloud App Security dá suporte à inspeção de conteúdo de arquivos criptografados que foram protegidos usando a Proteção de Informações do Azure. Agora é possível inspecionar esses arquivos criptografados para propostas de reclassificação e inspecionar uma exposição adicional de DLP e violações da política de segurança.

### <a name="cloud-app-security-release-131"></a>Cloud App Security versão 131

Lançado em 2 de setembro de 2018

- **Revogar permissões automaticamente em aplicativos OAuth suspeitos**  
Você pode controlar a quais aplicativos OAuth seus usuários têm acesso, revogando as permissões para aplicativos do OAuth no Office, Google ou Salesforce. Quando você cria uma **Política de permissão de aplicativo**, pode definir a política para revogar a permissão de um aplicativo.

- **Analisador adicional interno do Cloud Discovery com suporte**  
O Cloud Discovery agora dá suporte ao formato de log do Forcepoint Web Security Cloud.

### <a name="cloud-app-security-release-130"></a>Cloud App Security versão 130

Lançado em 22 de agosto de 2018

- **Nova barra de menus**  
Para fornecer uma experiência de administrador mais consistente em todos os produtos do Office 365, bem como permitir que você alterne com facilidade entre as soluções de segurança da Microsoft, a barra de menus do portal do Cloud App Security foi movida para o lado esquerdo da tela. Essa experiência de navegação consistente ajuda você a se orientar ao mudar de um portal de segurança da Microsoft para outro.

- **Impactar a pontuação do aplicativo OAuth**  
Você pode enviar comentários à equipe do Cloud App Security para informar se há um aplicativo OAuth descoberto em sua organização que parece mal-intencionado. Esse novo recurso permite que você faça parte de nossa comunidade de segurança e aprimore a análise e a pontuação de risco do aplicativo OAuth. Para mais informações, confira [Gerenciar aplicativo permiOAuth appsssions](manage-app-permissions.md).

- **Novos analisadores do Cloud Discovery**  
Os analisadores do Cloud Discovery agora dão suporte a iboss Secure Cloud Gateway e Sophos XG.

### <a name="cloud-app-security-release-129"></a>Cloud App Security versão 129

Lançado em 5 de agosto de 2018

- **Novas políticas de detecção de anomalias – regras de email suspeito**  
Foram incluídas novas políticas de detecção de anomalias que detectam regras de encaminhamento de email suspeito, por exemplo, se um usuário criou uma regra de caixa de entrada que encaminha uma cópia de todos os emails para um endereço externo.

- Essa versão inclui correções e melhorias para vários problemas.

### <a name="cloud-app-security-release-128"></a>Cloud App Security versão 128

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

### <a name="cloud-app-security-release-127"></a>Cloud App Security versão 127

Lançado em 8 de julho de 2018

- Agora você tem a capacidade de ver atividades genéricas do Office 365. No **Log de atividades** e nas **Políticas de atividades**, agora você pode filtras as atividades do Office 365 como **Não especificadas**. A revisão dessas atividades permite investigar informações sobre atividades executadas que ainda não estão classificadas por tipo no Cloud App Security, e você pode usar essas atividades a fim de enviar solicitações à equipe de Cloud App Security para criar novos tipos de atividade com base nessas atividades.

### <a name="cloud-app-security-release-126"></a>Cloud App Security versão 126

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

### <a name="cloud-app-security-release-125"></a>Cloud App Security versão 125

Lançamento em 10 de junho de 2018

- **Novo recurso de investigação dos principais usuários:**  
O Microsoft Cloud App Security adicionou um novo widget de investigação no painel que mostra os principais usuários pelo número de alertas de detecção de ameaças em aberto. Este widget de investigação permite que você concentre sua investigação de ameaças em usuários com o maior número de sessões suspeitas.

- **Suporte para buckets AWS S3:**  
Agora o Microsoft Cloud App Security pode detectar buckets AWS S3 e seus níveis de compartilhamento. Isso fornece alertas e visibilidade em buckets AWS publicamente acessíveis. Também permite que você crie políticas com base em buckets e aplique governança automática. Além disso, há um novo modelo de política disponível chamado **AWS (buckets S3 acessíveis publicamente)** que você pode usar para criar facilmente uma política para controlar seu armazenamento AWS. Para habilitar esses novos recursos, atualize seus aplicativos conectados do AWS adicionando as novas permissões descritas em [Conectar o AWS](connect-aws-to-microsoft-cloud-app-security.md).

- **Privilégios de administrador com base em grupos de usuários**:  
Agora você pode definir permissões administrativas para administradores do Microsoft Cloud App Security por grupo de usuários. Por exemplo, você pode definir um usuário específico como administrador somente para usuários na Alemanha. Isso permitirá ao usuário exibir e modificar informações no Microsoft Cloud App Security somente para o grupo de usuários "Alemanha – todos os usuários". Para saber mais, confira [Gerenciar acesso de administrador](manage-admins.md).

### <a name="cloud-app-security-release-124"></a>Cloud App Security versão 124

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
  - Conformidade – se os seus regulamentos de conformidade exigirem que você não monitore usuários de determinados países/regiões devido a regulamentos locais.
  - Licenciamento – se você quiser monitorar menos usuários para permanecer dentro dos limites de suas licenças do Microsoft Cloud App Security.
  Para saber mais, confira [Implantação com escopo](scoped-deployment.md).

- **Alerta de aplicativo violado para aplicativos descobertos**  
 Agora temos um alerta interno para notificá-lo quando qualquer um dos aplicativos descobertos de um locatário for violado. O alerta fornecerá informações sobre a hora e data da violação e quais usuários usaram o aplicativo, além de vincular fontes publicamente disponíveis que fornecem informações sobre a violação.

- **Novo servidor de email**  
 O servidor de email do Cloud App Security foi alterado e usa intervalos de endereços IP diferentes. Para verificar se você pode receber notificações, adicione os novos endereços IP à sua lista de permissões de antispam. Para usuários que personalizam suas notificações, o Microsoft Cloud App Security permite que você use um serviço de email de terceiros, o MailChimp&reg;. Para obter a lista de endereços IP do servidor de email e instruções para habilitar o trabalho com o MailChimp, confira [Requisitos de rede](network-requirements.md#mail-server) e [Configurações de email](mail-settings.md).

### <a name="cloud-app-security-release-123"></a>Cloud App Security versão 123

Lançado em 13 de maio de 2018

- **Definição de escopo da política de detecção de anomalias**:  
Agora, as políticas de detecção de anomalias podem ter escopos definidos. Isso permite definir cada política de detecção de anomalias para incluir apenas usuários ou grupos específicos e para excluir determinados usuários ou grupos. Por exemplo, você pode definir a detecção de Atividade de região pouco frequente para ignorar um usuário específico que viaja com frequência.

### <a name="cloud-app-security-release-122"></a>Cloud App Security versão 122

Lançado em 29 de abril de 2018

- Distribuição gradual: Agora você pode **definir permissões administrativas para administradores do Microsoft Cloud App Security por aplicativo**. Por exemplo, você pode definir um usuário específico como administrador somente para o G Suite. Isso permitiria ao usuário exibir e modificar no Microsoft Cloud App Security apenas informações exclusivamente relacionadas ao G Suite. Para saber mais, confira [Gerenciar acesso de administrador](manage-admins.md).

- Distribuição gradual: **As funções de administrador do Okta agora estão visíveis** no Microsoft Cloud App Security e estão disponíveis para cada função como uma marca em **Configurações** > **Grupos de usuários**.

### <a name="cloud-app-security-release-121"></a>Cloud App Security versão 121

Lançado em 22 de abril de 2018

- A visualização pública do **Controle de Aplicativos de Acesso Condicional (anteriormente conhecido como Cloud App Security Proxy)** foi aprimorada com recursos que facilitam a visibilidade avançada e o controle de vários aplicativos. Agora você pode criar uma Política de sessão com um filtro *Tipo de atividade*, para monitorar e bloquear uma variedade de atividades específicas do aplicativo. Esse novo filtro aprimora os recursos de controle de download de arquivo existentes, para fornecer a você um controle abrangente dos aplicativos em sua organização, e trabalha em conjunto com o acesso condicional do Azure Active Directory, para fornecer visibilidade em tempo real e controle de sessões de usuário suspeitas — por exemplo, sessões com usuários de colaboração B2B ou usuários provenientes de um dispositivo não gerenciado. Para mais informações, confira [Políticas da sessão](session-policy-aad.md).

- Distribuição gradual: As **políticas de detecção de anomalias do Cloud App Security foram aprimoradas** para incluir dois novos tipos de detecção de ameaças: atividade de ransomware e atividade de usuário encerrado. O Cloud App Security ampliou seus recursos de detecção de ransomware com a detecção de anomalias para garantir uma cobertura mais abrangente contra ataques sofisticados de ransomware. Usando nossa experiência de pesquisa de segurança para identificar os padrões comportamentais que refletem a atividade de ransomware, o Cloud App Security garante uma proteção holística e robusta. A atividade de usuário encerrado permite monitorar as contas de usuários encerrados, que podem ter sido desprovisionados de aplicativos corporativos, mas, em muitos casos, ainda mantêm o acesso a determinados recursos corporativos. Confira mais informações em [Obter análise comportamental instantânea e detecção de anomalias](anomaly-detection-policy.md).

### <a name="cloud-app-security-release-120"></a>Cloud App Security versão 120

Lançado em 8 de abril de 2018

- Para o Office 365 e o AAD, estamos implementando gradativamente a capacidade de detectar aplicativos internos como atividades de conta de usuário realizadas pelos aplicativos do Office 365 e do AAD (internos e externos). Isso permite criar políticas que alertarão você se um aplicativo realizar atividades inesperadas e não autorizadas.

- Ao exportar uma lista de permissões de aplicativo para csv, campos adicionais, como editor, nível de permissões e uso da comunidade, são incluídos para auxiliar no processo de conformidade e investigação.

- O aplicativo conectado do ServiceNow foi aprimorado para que as atividades de serviço interno não sejam mais registradas como realizadas por "Convidado" e não disparem mais alertas de falsos positivos. Agora, essas atividades são representadas como N/A, igual a todos os outros aplicativos conectados.

### <a name="cloud-app-security-release-119"></a>Cloud App Security versão 119

Lançada em 18 de março de 2018

- A página de intervalos de endereços IP inclui os endereços IP internos que são descobertos pelo Cloud App Security. Isso inclui endereços IP para serviços de nuvem identificados, como o Azure e o Office 365, bem como o feed de Inteligência contra ameaças, que aprimora automaticamente os endereços IP com informações sobre endereços IP suspeitos conhecidos.

- Quando o Cloud App Security tenta executar uma ação de governança em um arquivo, mas falha porque o arquivo está bloqueado, ele agora tenta novamente a ação de governança de forma automática.

### <a name="cloud-app-security-release-118"></a>Cloud App Security versão 118

Lançado em 4 de março de 2018

- Agora você pode aproveitar os recursos de monitoramento e descoberta de TI sombra do Microsoft Cloud App Security em seus próprios aplicativos personalizados. A nova capacidade de adicionar aplicativos personalizados ao Cloud Discovery permite que você monitore o uso do aplicativo e seja alertado sobre alterações no padrão de uso. Para obter mais informações, confira [Proteger seus aplicativos personalizados](cloud-discovery-custom-apps.md). Esse recurso está sendo implantado gradativamente.

- As páginas de **Configurações** do portal do Cloud App Security foram reformuladas. O novo design consolida todas as páginas de configurações e fornece funcionalidade de pesquisa e um design aprimorado.

- Agora, o Cloud Discovery dá suporte a firewalls e streaming de log da Web de firewall da Série F da Barracuda.

- A funcionalidade de pesquisa nas páginas de usuário e endereço IP agora habilita o preenchimento automático para facilitar a localização do que você estiver procurando.

- Agora você pode executar ações em massa nas páginas de configurações de Excluir entidades e Excluir endereço IP. Desse modo, é fácil selecionar vários usuários ou endereços IP e excluí-los do monitoramento como parte do Cloud Discovery em sua organização.

### <a name="cloud-app-security-release-117"></a>Cloud App Security versão 117

Lançado em 20 de fevereiro de 2018

- A integração profunda do Cloud App Security com a Proteção de Informações do Azure agora permite que você proteja os arquivos no G Suite. Esse recurso de visualização pública permite examinar e classificar arquivos no G Suite, e aplicar automaticamente os rótulos da Proteção de Informações do Azure para proteção. Confira mais informações em [Integração da Proteção de Informações do Azure](azip-integration.md).

- Agora, o Cloud Discovery dá suporte a [Digital Arts i-FILTER](https://www.daj.jp/en/products/if/).

- A tabela de agentes do SIEM agora inclui mais detalhes para um gerenciamento mais fácil.

### <a name="cloud-app-security-release-116"></a>Cloud App Security versão 116

Lançado em 4 de fevereiro de 2018

- A política de detecção de anomalias do Cloud App Security foi aprimorada com novas **detecções baseadas em cenários**, incluindo viagem impossível, atividade de um endereço IP suspeito e várias tentativas de logon com falha. As novas políticas são habilitadas automaticamente, fornecendo uma detecção de ameaças pronta para uso em seu ambiente de nuvem. Além disso, as novas políticas expõem mais dados do mecanismo de detecção do Cloud App Security para ajudar a agilizar o processo de investigação e conter as ameaças em andamento. Confira mais informações em [Obter análise comportamental instantânea e detecção de anomalias](anomaly-detection-policy.md).

- Distribuição gradual: agora, o Cloud App Security correlaciona os usuários e suas contas nos aplicativos SaaS. Assim, você pode investigar todas as atividades com facilidade, em todos os diversos aplicativos SaaS correlacionados, em qualquer aplicativo ou conta utilizados.

- Distribuição gradual: agora, o Cloud App Security dá suporte a várias instâncias do mesmo aplicativo conectado. Se você tiver várias instâncias, por exemplo, do Salesforce (uma para vendas, uma para marketing), será possível conectá-las ao Cloud App Security e gerenciá-las no mesmo console para criar políticas granulares e aprofundar a investigação.

- Os analisadores do Cloud Discovery agora dão suporte a dois formatos adicionais de Ponto de verificação, XML e KPC.

### <a name="cloud-app-security-release-115"></a>Cloud App Security versão 115

Lançado em 21 de janeiro de 2018

- Essa versão oferece uma experiência aprimorada ao selecionar pastas específicas em políticas de arquivos. Agora, você pode facilmente exibir e selecionar várias pastas a incluir em uma política.
- Na página **Aplicativos descobertos**:
  - O recurso de marcação em lote possibilita aplicar marcas personalizadas (além das marcas sancionado e não sancionado).
  - Ao **Gerar um relatório de endereços IP** ou **Gerar um relatório de usuários**, agora os relatórios exportados informam se o tráfego foi proveniente de aplicativos sancionados ou não.
- Agora, você pode solicitar o novo conector de aplicativos de API diretamente para a equipe do Microsoft Cloud App Security no portal, na página **Conectar um aplicativo**.

### <a name="cloud-app-security-release-114"></a>Cloud App Security versão 114

Lançado em 7 de janeiro de 2018

- A partir da versão 114, implantaremos gradualmente a capacidade de criar e salvar consultas personalizadas nas páginas Aplicativos descobertos e Log de atividades. As consultas personalizadas possibilitam criar modelos de filtro que podem ser reutilizados em investigações detalhadas. Além disso, as **Consultas sugeridas** foram adicionadas a fim de fornecer modelos de investigação prontos para uso para filtrar suas atividades e aplicativos descobertos. As **Consultas sugeridas** incluem filtros personalizados que identificam riscos, como atividades de usurpação de identidade, atividades de administrador, aplicativos de armazenamento em nuvem suspeitos e sem conformidade, aplicativos empresariais com criptografia fraca e riscos à segurança. Você pode usar as **Consultas sugeridas** como ponto inicial e modificá-las como desejar, para depois salvá-las como uma nova consulta. Confira mais informações em [Consultas e filtros de atividades](activity-filters-queries.md) e [Consultas e filtros de aplicativos descobertos](discovered-app-queries.md).

- Agora, você pode verificar o status atual do serviço do Cloud App Security acessando [status.cloudappsecurity.com](https://status.cloudappsecurity.com) ou diretamente no portal ao clicar em **Ajuda**>**Status do sistema**.

## <a name="updates-made-in-2017"></a>Atualizações feitas em 2017

### <a name="cloud-app-security-release-113"></a>Cloud App Security versão 113

Lançado em 25 de dezembro de 2017

- Temos o prazer de anunciar que o Cloud App Security agora é compatível com uma integração mais profunda com a Proteção de Informações do Azure. Esse recurso de visualização pública permite examinar e classificar arquivos em aplicativos na nuvem e aplicar automaticamente os rótulos da Proteção de Informações do Azure para proteção. Esse recurso está disponível para Box, SharePoint e OneDrive. Confira mais informações em [Integração da Proteção de Informações do Azure](azip-integration.md).

- Os analisadores de log do Cloud Discovery agora têm suporte para formatos genéricos: LEEF, CEF e W3C.

### <a name="cloud-app-security-release-112"></a>Lançamento 112 do Cloud App Security

Lançado em 10 de dezembro de 2017

- Agora, para acessar a gaveta de informações relevante, basta clicar em um nome de usuário ou endereço IP no log de atividades.
- Ao investigar atividades, agora você pode facilmente exibir todas as atividades dentro do mesmo período de dentro da gaveta de insights clicando no ícone de relógio. O ícone de relógio permite que você exiba todas as atividades realizadas dentro de 48 horas da atividade que você está exibindo.
- Melhorias implementadas no analisador de logs do Cloud Discovery para Juniper SRX.
- Para atividades monitoradas pelo proxy, o **Objeto da atividade** foi expandido para incluir informações relevantes para verificações DLP. Políticas correspondentes foram expandidas para incluir violações de DLP se existirem.

### <a name="cloud-app-security-release-111"></a>Cloud App Security versão 111

Lançado em 26 de novembro de 2017

- Agora as políticas de descoberta oferecem suporte a marcas do aplicativo como uma condição e uma ação de governança. Essa adição permite que você marque automaticamente os aplicativos recém-descobertos com marcas personalizadas, como **Aplicativos populares**. Você também pode usar a marca do aplicativo como um filtro. Por exemplo, "alertar-me quando um aplicativo em ' Watchlist ' tiver mais de 100 usuários em um único dia".

- O filtro **Tempo** foi aprimorado para torná-lo mais fácil de usar.

- A inspeção de conteúdo agora permite distinguir entre o conteúdo, metadados e nome de arquivo, permitindo que você selecione qual deles deseja inspecionar.

- Uma nova ação de governança foi adicionada ao G Suite. Agora, você pode **Reduzir o acesso público** para arquivos compartilhados. Essa ação permite que você defina os arquivos disponíveis publicamente a serem disponibilizados somente com um link compartilhado.

- Todas as atividades de logon para outros aplicativos agora aparecerão no Cloud App Security como proveniente do OKTA. Você pode exibir e filtrar com base no aplicativo de destino no qual o logon foi executado no campo **objetos de atividade** da atividade.

### <a name="cloud-app-security-release-110"></a>Cloud App Security versão 110

Lançado em 12 de novembro de 2017

- Agora geralmente disponível: estamos começando a implementar um novo modo de implantação para o coletor de logs. Além da atual implantação baseada em dispositivo virtual, o novo coletor de logs baseado em Docker (contêiner) pode ser instalado como um pacote em [computadores Ubuntu](discovery-docker.md), tanto localmente quanto no Azure. Ao usar o Docker, o computador host é de propriedade do cliente, que pode fazer patch livremente e monitorá-lo.

- Usando o novo ponto de interrogação azul no canto, é possível agora acessar a página de documentação relevante do Cloud App Security em docs.microsoft.com de dentro das páginas do portal. Cada link é sensível ao contexto, levando você para as informações necessárias com base na página em que você está.
- Agora, você pode enviar comentários de qualquer página do portal do Cloud App Security. Os comentários permitem que você informe bugs, solicite novos recursos e compartilhe sua experiência diretamente com a equipe do Cloud App Security.
- Foram feitas melhorias na capacidade de descoberta de nuvem de reconhecer subdomínios para investigações aprofundadas no uso da nuvem de sua organização. Para saber mais, confira [Trabalhando com aplicativos descobertos](discovered-apps.md).

### <a name="cloud-app-security-release-109"></a>Cloud App Security versão 109

Lançado em 29 de outubro de 2017

- A distribuição do recurso de proxy do Microsoft Cloud App Security foi iniciada. O proxy do Microsoft Cloud App Security fornece as ferramentas necessárias para ter exibição em tempo real e controle sobre o acesso ao seu ambiente de nuvem e as atividades dentro dele. Por exemplo:

  - Evite o vazamento de dados bloqueando os downloads antes que eles ocorram.
  - Defina as regras que forçam os dados armazenados na e baixados da nuvem a serem protegidos com criptografia.
  - Obtenha visibilidade para pontos de extremidade desprotegidos para que você possa monitorar o que está sendo feito em dispositivos não gerenciados.
  - Controle o acesso por meio de redes não corporativas ou endereços IP arriscados.

  Saiba mais em [Proteger aplicativos com o Controle de Aplicativo de Acesso Condicional](proxy-intro-aad.md).

- Estamos distribuindo gradualmente a capacidade de filtrar de acordo com os nomes de atividades de serviços específicos. Esse novo filtro de tipo de atividade é mais granular, para que você possa monitorar as atividades de aplicativos específicas, em vez de tipos de atividade mais gerais. Por exemplo, anteriormente, você podia filtrar por **Executar o comando**, e agora você pode filtrar para cmdlets EXO específicos. O nome da atividade também pode ser visto na gaveta de atividade em **Tipo (em aplicativo)**. Essa funcionalidade substituirá o filtro de tipo de atividade.

- O Cloud Discovery agora é compatível a Cisco ASA com FirePOWER.

- Foram feitas melhorias de desempenho nas páginas de Usuário de Discovery e IP para melhorar a experiência do usuário.

### <a name="cloud-app-security-releases-105-106-107-108"></a>Cloud App Security versões 105, 106, 107, 108

Lançadas em setembro/outubro de 2017

- O Cloud App Security agora inclui um data center localizado na UE. Além de nosso data center dos EUA, o data center da UE permitirá que os clientes do Cloud App Security estejam em total conformidade com a nova e futura padronização e as certificações europeias.
- Novos filtros foram adicionados à página de **Conectores de aplicativos**, que lhe fornecem filtragem mais simples e análise adicional.
- O Cloud Discovery em arquivos de log que têm apenas informações de IP de destino foi aprimorado.

### <a name="cloud-app-security-release-104"></a>Cloud App Security versão 104

Lançado em 27 de agosto de 2017

- Agora você pode adicionar intervalos de IP em massa por meio da criação de um script usando a **API de intervalos de endereço IP**. A API podem ser encontradas na barra de menus do portal do Cloud App Security clicando no ponto de interrogação e, em seguida na **documentação da API**.
- O Cloud Discovery agora fornece melhor visibilidade para transações bloqueadas, apresentando o total de transações e as transações bloqueadas.
- Agora você pode filtrar aplicativos de nuvem com base em se eles são certificados com a **ISO 27017**. Esse novo fator de risco do Catálogo de Aplicativos de Nuvem determina se o provedor do aplicativo tem essa certificação. A norma ISO 27017 estabelece controles e diretrizes comumente aceitos para processar e proteger as informações do usuário num ambiente de computação em nuvem pública.
- Para ajudá-lo a se preparar para a conformidade com o GDPR, reunimos as instruções de preparação dos aplicativos de nuvem no Catálogo de Aplicativos de Nuvem. Ele ainda não afeta a pontuação de risco do aplicativo, mas fornece um link para você para a página de preparação do GDPR do editor do aplicativo, quando fornecida. A Microsoft ainda não verificou o conteúdo, portanto não é responsável pela respectiva validade.

### <a name="cloud-app-security-release-103"></a>Cloud App Security versão 103

Lançado em 13 de agosto de 2017

- O Cloud App Security adicionou suporte de proteção nativa da Proteção de Informações do Azure para os seguintes arquivos do Office .docm, .docx, .dotm, .dotx, .xlam, .xlsb, .xlsm, .xlsx, .xltx, .xps, .potm, .potx, .ppsx, .ppsm, .pptm, .pptx, .thmx, .vsdx, .vsdm, .vssx, .vssm, .vstx, .vstm (em lugar da proteção genérica).

- Qualquer administrador de Conformidade do Azure Active Directory receberá automaticamente permissões semelhantes no Cloud App Security. As permissões incluem a capacidade de apenas ler e de gerenciar alertas, criar e modificar políticas de arquivo, permitir ações de governança de arquivo e exibir todos os relatórios internos em Gerenciamento de Dados.

- Estendemos o contexto de violação da DLP de 40 para 100 caracteres a fim de ajudar você a entender melhor o contexto da violação.

- Mensagens de erro detalhadas para o carregador de log personalizado do Cloud Discovery para permitir que você solucione erros facilmente no upload do log.

- O script de bloqueio do Cloud Discovery foi estendido para dar suporte ao formato Zscaler.

- Novo fator de risco do Catálogo de aplicativos de nuvem: retenção de dados após o encerramento da conta. Isso permite que você se certifique de que seus dados foram completamente removidos depois de encerrar uma conta dentro de um aplicativo de nuvem.

### <a name="cloud-app-security-release-102"></a>Cloud App Security versão 102

Lançado em 30 de julho de 2017

- Como as informações de endereço IP são cruciais para quase todas as investigações, agora você pode exibir informações detalhadas sobre endereços IP na Gaveta de atividades. De dentro de uma atividade específica, você agora pode clicar na guia Endereços IP para exibir os dados consolidados sobre o endereço IP. Os dados incluem o número de alertas abertos para o endereço IP específico, um gráfico de tendência de atividade recente e um mapa do local. Esse recurso permite fazer busca detalhada facilmente. Por exemplo, quando estiver investigando alertas de viagem impossíveis, você pode compreender facilmente em que local o endereço IP foi usado e se ele estava envolvido em atividades suspeitas ou não. Você pode executar ações diretamente na gaveta do endereço IP que permite que você marque um endereço IP como arriscado, VPN ou corporativo para facilitar a criação de políticas e a futura investigação. Para obter mais informações, consulte [insights de endereço IP](activity-filters.md#ip-address-insights)

- No Cloud Discovery, agora você pode usar [formatos de log personalizado](custom-log-parser.md) para [uploads de log automatizados](discovery-docker.md). Formatos de log personalizados permitem que você automatize facilmente o upload de logs de seus SIEMs como servidores Splunk ou qualquer outro formato sem suporte.

- As novas ações de investigação de usuário permitem um nível adicional de análise para investigações do usuário. Nas páginas de **Investigação**, você agora pode clicar com o botão direito do mouse em uma atividade, usuário ou conta e aplicar um dos seguintes novos filtros para investigação e filtragem avançadas: **Exibir atividade relacionada**, **Exibir controle relacionado**, **Exibir alertas relacionados**, **Exibir arquivos de propriedade**, **Exibir arquivos compartilhados com esse usuário**.

- O catálogo do Cloud App agora contém um novo campo para retenção de dados após o encerramento da conta. Esse fator de risco permite que você tenha certeza de que seus dados foram completamente removidos depois de encerrar uma conta dentro de um aplicativo de nuvem.

- O Cloud App Security agora tem visibilidade aprimorada de atividades relativas a objetos do Salesforce. Os objetos incluem clientes potenciais, contas, campanhas, oportunidades, perfis e casos. Por exemplo, a visibilidade do acesso de páginas de conta permite que você configure uma política que alerta se um usuário exibe um número muito grande de páginas de conta. Isso está disponível por meio do Salesforce App Connector, quando você tiver habilitado o Salesforce Event Monitoring (parte do Salesforce Shield).

- Não rastrear agora está disponível para clientes de visualização privada! Agora você pode controlar quais dados de atividade dos usuários são processados. Esse recurso permite que você defina grupos específicos no Cloud App Security como "não rastrear". Por exemplo, agora você pode decidir não processar nenhum dado de atividade de usuários localizados na Alemanha ou em qualquer país que não esteja vinculado a uma lei de conformidade específica. Isso pode ser implementado em todos os aplicativos no Cloud App Security, para um aplicativo específico ou até mesmo um subaplicativo específico. Além disso, esse recurso pode ser utilizado para facilitar a distribuição gradual do Cloud App Security. Para saber mais ou para participar da visualização privada para esse recurso, entre em contato com o suporte ou seu representante de conta.

### <a name="cloud-app-security-release-100"></a>Cloud App Security versão 100

Lançado em 3 de julho de 2017

**Novos recursos**

- **Extensões de segurança:** extensões de segurança é um novo painel para gerenciamento centralizado de todas as extensões de segurança ao Cloud App Security.  Extensões incluem gerenciamento de token de API, agentes SIEM e conectores de DLP Externo. O novo painel está disponível em Cloud App Security em "configurações".

  - Tokens de API – gere e gerencie seus próprios [tokens de API](api-tokens.md) para integrar o Cloud App Security com software de terceiros usando nossas APIs RESTful.
  - Agentes SIEM – a [integração do Siem](siem.md) foi localizada anteriormente diretamente em "configurações", agora disponível como uma guia em extensões de segurança.
  - DLP externo (Versão Prévia) – o Cloud App Security permite que você [utilize os investimentos existentes em sistemas de classificação de terceiros](icap-stunnel.md), como soluções de DLP (prevenção de perda de dados) e permite examinar o conteúdo de aplicativos usando as implantações existentes em execução no seu ambiente de nuvem. Entre em contato com seu gerente de conta para ingressar na versão prévia.

- **Sancionar/cancelar sanção automaticamente:** as novas políticas de detecção de aplicativo dão ao Cloud Discovery a capacidade de definir automaticamente aplicativos com rótulo Sancionado/Não sancionado. Isso lhe dá a capacidade de identificar automaticamente os aplicativos que estão violando a política e os regulamentos da sua organização e adicioná-los ao script de bloqueio gerado.
- **Rótulos de arquivo de segurança do Cloud App Security:** agora você pode aplicar rótulos de arquivo do Cloud App Security para fornecer mais informações nos arquivos verificados. Para cada arquivo verificado pelo DLP do Cloud App Security, você poderá saber se os arquivos foram bloqueados de serem inspecionados porque foram criptografados ou corrompidos. Por exemplo, você pode configurar políticas para alertá- e arquivos protegidos por senha em quarentena que são compartilhados externamente. Este recurso está disponível para arquivos examinados após 3 de julho de 2017.

    Você pode filtrar esses arquivos usando os **Rótulos de classificação** de filtro  >  **Cloud app Security**:

  - **Azure RMS criptografado** – arquivos cujo conteúdo não foi inspecionado porque têm um conjunto de criptografia do Azure RMS.
  - **Criptografado por senha** – arquivos cujo conteúdo não foi inspecionado porque são protegidos por senha pelo usuário.
  - **Arquivo corrompido** – arquivos cujo conteúdo não foi inspecionado porque seu conteúdo não pôde ser lido.

- **Insights do usuário**: a experiência de investigação foi atualizada para permitir informações prontas sobre o usuário em ação. Com um único clique, agora você pode obter uma visão geral abrangente dos usuários da Gaveta de atividades. Os insights incluem de que localização eles se conectaram, com quantos alertas em aberto eles estão envolvidos e suas informações de metadados.
- **Insights do conector de aplicativo:** em **Conectores de Aplicativos**, cada aplicativo conectado agora inclui uma gaveta de aplicativos na tabela para análise mais fácil de seu status. Os detalhes fornecidos incluem quando o conector de aplicativos foi conectado e integridade da última verificação no conector. Você também pode monitorar o status da verificação de DLP em cada aplicativo: o número total de arquivos inspecionados pelo DLP, bem como o status das verificações em tempo real (solicitadas verificações versus verificações reais). Você poderá saber se a taxa de arquivos examinados pelo Cloud App Security em tempo real é menor do que o número solicitado e se o locatário pode ser exceder sua capacidade e a experiência de um atraso de resultados de DLP.

- **Personalização do Catálogo de aplicativos de nuvem:**

  - **Marcas de aplicativo**: agora você pode criar marcas personalizadas para aplicativos. Essas marcas podem ser usadas como filtros para aprofundar-se nos tipos específicos de aplicativos que você deseja investigar. Por exemplo, lista de observação personalizada, atribuição para uma unidade de negócios específica ou aprovações personalizadas, como "aprovadas por ofício".
  - **Notas personalizadas**: conforme você examina e avalia os diferentes aplicativos que foram descobertos em seu ambiente, agora você pode salvar suas conclusões e ideias em Notas.
  - **Pontuação de risco personalizada**: agora você pode substituir a pontuação de risco de um aplicativo. Por exemplo, se a pontuação de risco de um aplicativo for 8 e esse for um aplicativo sancionado na sua organização, você poderá alterar a pontuação de risco para 10 para sua organização. Você também pode adicionar observações para tornar a justificativa da alteração clara quando qualquer pessoa analisar o aplicativo.

- **Novo modo de implantação do coletor de log:** estamos começando a implementar um novo modo de implantação que agora está disponível para o coletor de logs. Além da implantação baseada em dispositivo virtual atual, o novo coletor de log baseado em Docker (contêiner) pode ser instalado como um pacote nos computadores com Windows e Ubuntu, tanto localmente quanto no Azure. Ao usar o Docker, o computador host é de propriedade do cliente, que pode fazer patch livremente e monitorá-lo.

**Anúncios**

- O catálogo do Cloud App agora oferece suporte a mais de 15.000 aplicativos detectáveis
- Conformidade: o Cloud App Security oficialmente é certificado para SOC1/2/3 pelo Azure. Para obter a lista completa de certificações, consulte [ofertas de conformidade](https://www.microsoft.com/trustcenter/compliance/complianceofferings) e filtrar os resultados para Cloud app Security.

**Outros aprimoramentos:**

- **Melhor análise:** foram feitas melhorias no mecanismo de análise de log do Cloud Discovery. Erros internos têm probabilidade significativamente menor de ocorrer.
- **Formatos de log esperados:** o formato esperado de log para logs de Cloud Discovery agora fornece exemplos de ambos os formatos de Syslog e FTP.
- **Status de upload do coletor de logs:** agora, você pode ver o status do coletor de logs no portal e solucionar problemas de erros mais rapidamente com as notificações de status no portal e os alertas do sistema.

### <a name="cloud-app-security-release-99"></a>Cloud App Security versão 99

Lançado em 18 de junho de 2017

**Novos recursos**

- Agora você pode exigir que os usuários entrem novamente para todos os aplicativos do Azure AD e do Office 365. Exija entrada novamente como uma correção rápida e eficaz para alertas de atividade de usuário suspeitos e contas comprometidas. Você pode encontrar a nova governança nas configurações de política e nas páginas de alertas, ao lado da opção Suspender usuário.
- Agora você pode filtrar para atividades de **Adicionar atribuição de função de representação** no log de atividades. Esta atividade permite que você detecte quando um administrador concedeu uma função de **Representação de aplicativo** a qualquer usuário ou conta de sistema, usando o cmdlet **ManagementRoleAssignment novo**. Essa função permite que o representante execute operações usando as permissões associadas à conta representada, em vez das permissões associadas à conta do representante.

**Melhorias do Cloud Discovery:**

- Os dados do Cloud Discovery agora podem ser aprimorados com os dados de nome de usuário do Azure Active Directory. Quando você habilita esse recurso, o nome de usuário recebido nos logs de tráfego de descoberta é correspondido e substituído pelo nome de usuário do Azure AD. O enriquecimento permite os seguintes novos recursos:
  - Você pode investigar o uso de TI sombra pelo usuário do Azure Active Directory.
  - Você pode correlacionar o uso do aplicativo de nuvem Descoberto com as atividades coletadas pela API.
  - Então, você pode criar logs personalizados com base nos grupos de usuários do Azure AD. Por exemplo, um relatório de TI sombra para um departamento de Marketing específico.
- Foram feitos aperfeiçoamentos ao analisador de syslog Juniper. Agora, ele dá suporte aos formatos de welf e sd-syslog.
- Aprimoramentos foram feitos ao analisador Palo Alto para melhor descoberta de aplicativo.
- Para verificar se os logs estão sendo carregados com êxito, agora você pode ver o status dos seus Coletores de log no portal do Cloud App Security.

**Aprimoramentos gerais:**

- Marcas de endereço IP internas e marcas de IP personalizadas são consideradas hierarquicamente agora, com marcas de IP personalizadas, tendo precedência sobre as marcas de IP internas. Por exemplo, se um endereço IP estiver marcado como **Arriscado** com base em inteligência de ameaça, mas houver uma marca IP personalizada que o identifique como **Corporativo**, as marcas e a categoria personalizada terão precedência.

### <a name="cloud-app-security-release-98"></a>Cloud App Security versão 98

Lançado em 4 de junho de 2017

**Atualizações de Cloud Discovery:**

- Os usuários agora podem executar a filtragem avançada em aplicativos descobertos. A filtragem permite que você execute a investigação profunda. Por exemplo, a filtragem de aplicativos com base no uso. Muito tráfego de upload de aplicativos descobertos de determinados tipos? Quantos usuários utilizaram determinadas categorias de aplicativos? Você também pode executar várias seleções no painel esquerdo para selecionar várias categorias.
- Distribuição iniciada de novos modelos para Cloud Discovery, que se baseiam em pesquisas populares, por exemplo, "aplicativo de armazenamento de nuvem sem conformidade". Esses filtros básicos podem ser usados como modelos para executar análise em seus aplicativos descobertos.
- Para facilidade de uso, você pode executar ações como sancionar e cancelar a sanção de vários aplicativos em uma ação.
- Agora estamos lançando a capacidade de criar relatórios de descoberta personalizados com base em grupos de usuários do Azure Active Directory. Por exemplo, se você quiser ver o uso de nuvem de seu departamento de marketing, poderá importar o grupo de marketing usando o recurso importar grupo de usuários e, em seguida, criar um relatório personalizado para este grupo.

**Novos recursos:**

- O RBAC para leitores de segurança concluiu a distribuição. Esse recurso permite que você gerencie as permissões concedidas aos seus administradores dentro do console do Cloud App Security. Por padrão, todos os administradores do Azure Active Directory, os administradores globais do Office 365 e os administradores de Segurança têm permissão total no portal. Todos os leitores de segurança no Azure Active Directory e do Office 365 têm acesso somente leitura no Cloud App Security. Você pode adicionar outros administradores ou substituir permissões usando a opção "gerenciar acesso". Para obter mais informações, consulte [Gerenciando permissões de administrador](manage-admins.md).
- Agora estamos lançando relatórios de inteligência de ameaça detalhados para endereços IP arriscados detectados pelo gráfico de segurança inteligente da Microsoft. Quando uma atividade é executada por um botnet, você verá o nome do botnet (se disponível) com um link para um relatório detalhado sobre o botnet específico.

### <a name="cloud-app-security-release-97"></a>Cloud App Security versão 97

Lançado em 24 de maio de 2017

**Novos recursos:**

- Investigue os arquivos e as violações de política: agora você pode ver todas as correspondências de política na página de arquivos. Além disso, a página de alerta do arquivo foi aprimorada para incluir uma guia separada para o Histórico do arquivo específico. A melhoria permite fazer busca detalhada no histórico de violação entre todas as políticas para o arquivo específico. Cada evento histórico inclui um instantâneo do arquivo no momento do alerta. Isso incluirá uma indicação de se o arquivo foi excluído ou colocado em quarentena.
- [Quarentena do administrador](use-case-admin-quarantine.md) agora está disponível em versão prévia privada para o Office 365 SharePoint e o OneDrive for Business. Esse recurso permite que você coloque em quarentena os arquivos que correspondem a políticas ou defina uma ação automatizada para colocá-los em quarentena. A quarentena remove os arquivos do diretório do SharePoint do usuário e copia os originais para o local de quarentena do administrador que você escolher.

**Aprimoramentos de Cloud Discovery:**

- O suporte do Cloud Discovery aos logs Cisco Meraki foi aprimorado para melhorar a visibilidade.
- A opção para sugerir um aperfeiçoamento ao Cloud Discovery permite que você sugira um novo fator de risco.
- O analisador de log personalizado foi aprimorado para dar suporte a formatos de log, separando a configuração de data e hora e lhe dá a opção de definir o carimbo de data/hora.
- Começando o lançamento da capacidade de criar relatórios de descoberta personalizados com base em grupos de usuários do Azure Active Directory. Por exemplo, se você quiser ver o uso de nuvem de seu departamento de marketing, poderá importar o grupo de marketing usando o recurso importar grupo de usuários e, em seguida, criar um relatório personalizado para este grupo.

**Outras atualizações:**

- Agora, o Cloud App Security conta com suporte para atividades do Microsoft Power BI com suporte no log de auditoria do Office 365. Esse recurso está sendo implantado gradativamente. Você precisa habilitar [essa funcionalidade no portal do Power BI](https://powerbi.microsoft.com/documentation/powerbi-admin-auditing/).
- Nas políticas de atividade, agora você pode definir ações de notificação e suspensão a serem realizadas no usuário em todos os aplicativos conectados. Por exemplo, você pode definir uma política para sempre notificar o gerente do usuário e suspender o usuário imediatamente, sempre que o usuário tiver vários logons com falha em qualquer aplicativo conectado.

### <a name="oob-release"></a>Versão OOB

- Em uma reação rápida para a varredura de ransomware do globo, no domingo, a equipe do Cloud App Security adicionou o moo modelo de [Política de detecção de atividade ransomware potencial](use-case-ransomware.md) ao portal que inclui a extensão de assinatura de WannaCrypt. Aconselhamos que você defina esta política ainda hoje.

### <a name="cloud-app-security-release-96"></a>Cloud App Security versão 96

Lançamento: 8 de maio de 2017

**Novos recursos:**

- Continuando a distribuição gradual da permissão de Leitor de Segurança, que permite que você gerencie as permissões concedidas aos seus administradores dentro do console do Cloud App Security. Por padrão, todos os administradores globais do Azure Active Directory, do Office 365 e de Segurança têm permissão total no portal. Todos os leitores de segurança no Azure Active Directory e do Office 365 terão acesso somente leitura no Cloud App Security. Para obter mais informações, consulte [Gerenciando permissões de administrador](manage-admins.md).
- Distribuição concluída do suporte ao Cloud App Security para analisadores de log definidos pelo usuário para logs baseados em CSV. O Cloud App Security permite que você configure um analisador para seus dispositivos anteriormente sem suporte fornecendo as ferramentas para delinear quais colunas se correlacionam com dados específicos. Para obter mais informações, consulte [analisador de log personalizado](custom-log-parser.md).

**Aperfeiçoamentos:**

- Agora, o Cloud Discovery dá suporte a dispositivos Juniper SSG.
- O suporte do Cloud Discovery aos logs Cisco ASA foi aprimorado para melhorar a visibilidade.
- Agora você pode executar com mais facilidade ações em lote e selecionar vários registros nas tabelas do portal do Cloud App Security: o tamanho da página aumentou para melhorar as operações em lote.
- Agora, os relatórios internos **Compartilhamento de saída por domínio** e **Proprietários dos arquivos compartilhados** podem ser executados para os dados do Salesforce.
- Estamos iniciando a distribuição de atividades adicionais do Salesforce, permitindo que você acompanhe informações interessantes extraídas dos dados da atividade. Essas atividades incluem exibição e edição de contas, leads, oportunidades e vários outros objetos interessantes da Salesforce.
- Novas atividades foram adicionadas ao Exchange a fim de permitir que você possa monitorar quais permissões foram concedidas para pastas de caixa de correio ou caixas de correio do usuário. Essas atividades incluem:
  - Adicionar permissões de destinatário
  - Remover permissões de destinatário
  - Adicionar permissões de pasta de caixa de correio
  - Remover permissões de pasta de caixa de correio
  - Definir permissões de pasta de caixa de correio

   Por exemplo, agora você pode monitorar os usuários que receberam as permissões **sendas** para as caixas de correio de outros usuários e, como resultado, agora podem enviar emails em seu nome.

### <a name="cloud-app-security-release-95"></a>Cloud App Security versão 95

Lançado em 24 de abril de 2017

**Actualiza**

- A página **Contas** foi atualizada com aprimoramentos que facilitam a detecção de riscos. Você agora pode filtrar mais facilmente para contas internas e externas. Veja rapidamente se um usuário tem permissões de administrador. Você pode executar ações em cada conta por aplicativo, como remover permissões, remover colaborações do usuário, suspender usuário. Além disso, [grupos de usuários](user-groups.md) importados para cada conta serão exibidos.

- Para as contas de trabalho da Microsoft (Office 365 e Azure Active Directory), o Cloud App Security agrupa diferentes identificadores de usuário como endereços de proxy, aliases, SIDs e muito mais em uma única conta. Todos os aliases relacionados a uma conta aparecerão sob o endereço de email principal. Com base na lista de identificadores de usuário, para atividades cujo ator é um identificador de usuário, o ator será exibido como o nome UPN do nome de usuário primário. Com base no nome UPN, serão atribuídos a grupos e políticas aplicadas. Essa alteração vai melhorar a investigação de atividades e unirá todas as atividades relacionadas à mesma sessão de anomalias e políticas baseadas em grupo. Este recurso será implantado gradualmente no próximo mês.

- A marca de Robô foi adicionada como um possível fator de risco no relatório interno de uso do navegador. Agora, além de o uso do navegador ser marcado como obsoleto, você pode ver quando o uso do navegador foi executado por um robô.
- Ao criar uma política de arquivo de inspeção de conteúdo, agora você pode definir o filtro para incluir apenas os arquivos com pelo menos 50 correspondências.

### <a name="cloud-app-security-release-94"></a>Cloud App Security versão 94

Lançado em 2 de abril de 2017

**Novos recursos:**

- O Cloud App Security agora está integrado ao Azure RMS. Você pode proteger arquivos no OneDrive e no Sharepoint Online do Office 365 com o Microsoft Rights Management diretamente do portal do Cloud App Security. A proteção pode ser obtida na página **Arquivos**. Para obter mais informações, consulte [integrando com a proteção de informações do Azure](azip-integration.md). Aplicativos adicionais terão suporte em versões futuras.
- Até agora, era especialmente difícil identificar quando as atividades de bots e rastreadores ocorriam em sua rede porque as atividades não eram executadas por um usuário em sua rede. Sem o seu conhecimento, bots e rastreadores podem executar ferramentas maliciosas em seus computadores. Agora, o Cloud App Security fornece as ferramentas para ver quando bots e rastreadores estão realizando atividades em sua rede. Você pode usar a nova marca de agente do usuário para filtrar atividades no log correspondente. A marca de agente do usuário permite que filtrar todas as atividades realizadas por bots e você pode usá-la para criar uma política que o alerta sempre que esse tipo de atividade for detectado. Você será informado quando versões futuras incluírem essas atividades de risco, que estarão incorporadas aos alertas de detecção de anomalias.
- A nova página de permissões de aplicativo unificada permite investigar mais facilmente as permissões que os usuários tem fornecido a aplicativos de terceiros. Ao clicar em **investigar**  >  **as permissões do aplicativo**, você poderá exibir uma lista de todas as permissões que os usuários forneciam a aplicativos de terceiros. Uma página de permissões de aplicativo por aplicativo conectado permite comparar melhor os diversos aplicativos e as permissões concedidas. Para saber mais, veja [Gerenciar permissões de aplicativos](manage-app-permissions.md).
- Você pode filtrar os dados diretamente da Gaveta da tabela para uma análise mais fácil.
No **Log de atividades**, a tabela **Arquivos** e as páginas **Permissões de aplicativo** agora são aprimoradas com novas ações contextuais que tornam a dinamização do processo de investigação muito mais fácil. Também adicionamos links rápidos para as páginas de configuração e a capacidade de copiar dados com um único clique. Para obter mais informações, consulte as informações sobre como [trabalhar com os empates de arquivo e atividade](file-filters.md).
- Concluída a implementação do suporte para logs de atividades e alertas do Microsoft Teams para Office 365.

### <a name="cloud-app-security-release-93"></a>Cloud App Security versão 93

Lançado em 20 de março de 2017

**Novos recursos:**

- Agora, você pode aplicar políticas para incluir ou excluir grupos de usuários importados.
- A Anonimização do Cloud App Security agora permite que você configure uma chave de criptografia personalizada. Para obter mais informações, consulte [Cloud Discovery anonimato](cloud-discovery-anonymizer.md).
- Para ter mais controle sobre o gerenciamento de usuário e conta, agora, você tem acesso direto às configurações da conta do Azure AD para cada usuário e conta da página **Conta**. Basta clicar na engrenagem ao lado de cada usuário. Essa alteração facilita o acesso aos recursos avançados de gerenciamento de usuários, de grupos, ao gerenciamento de grupos, à configuração de MFA, aos detalhes sobre logons de usuário e à possibilidade de bloquear a entrada.
- Agora você pode exportar um script de bloqueio para aplicativos não sancionados por meio da API do Cloud App Security. Aprenda sobre nossas APIs no portal do Cloud App Security clicando no ponto de interrogação na barra de menus, seguido por **documentação da API**.
- O conector do aplicativo do Cloud App Security para ServiceNow foi expandido para incluir suporte para tokens de OAuth (como apresentado em Genebra, Helsinque, Istambul). Essa alteração fornece uma conexão de API mais robusta para o ServiceNow não depende do usuário que está implantando. Para obter mais informações, consulte [conectar o ServiceNow ao Microsoft Cloud app Security](connect-servicenow-to-microsoft-cloud-app-security.md). Os clientes existentes podem atualizar as configurações na página de conector do Aplicativo ServiceNow.
- Se você tiver configurado scanners DLP adicionais de terceiros, o status de verificação de DLP agora mostrará o status de cada conector de forma independente para melhorar a visibilidade.
- Agora, o Cloud App Security conta com suporte para atividades de Equipes da Microsoft que são suportadas no log de auditoria do Office 365. Esse recurso está sendo implantado gradativamente.
- Para eventos de representação do Exchange Online, agora você pode filtrar pelo nível de permissão usado-delegado, administrador ou administrador delegado. Você pode pesquisar eventos que exibam o nível de representação que lhe interessa no **log de atividades** pesquisando o item objetos de **atividade**  >  **Item**.
- Na gaveta de aplicativos na guia **Permissões do Aplicativo** dos aplicativos do Office 365, você pode ver o **Editor** de cada aplicativo. Você também pode usar o Editor como um filtro para investigar outros aplicativos do mesmo editor.
- Agora, os endereços IP com risco são exibidos como um fator de risco independente em vez de ponderados no fator de risco de **Localização** geral.
- Quando os rótulos de Proteção de Informações do Azure estiverem desabilitados em um arquivo, os rótulos desabilitados serão exibidos como desabilitados no Cloud App Security. Rótulos excluídos não serão exibidos.

**Suporte adicional do Salesforce:**

- Agora, você pode suspender e cancelar a suspensão de usuários do Salesforce no Cloud App Security. Essa ação pode ser realizada na guia **Contas** do Conector do Salesforce. Clique na engrenagem ao final da linha de um usuário específico e selecione **Suspender** ou **Cancelar suspensão**. Suspender e cancelar suspensão também podem ser aplicados como uma ação de governança como parte de uma política. Todas as atividades suspensas e não suspensas realizadas no Cloud App Security serão registradas no [Log de governança](governance-actions.md).
- Melhor visibilidade ao compartilhamento de conteúdo do Salesforce: agora você pode ver quais arquivos foram compartilhados e com quem, incluindo arquivos compartilhados publicamente, arquivos compartilhados com grupos e arquivos compartilhados com todo o domínio do Salesforce. Uma maior visibilidade será implantada retroativamente a aplicativos do Salesforce novos e conectados atualmente. Poderá levar algum tempo para essas informações serem atualizadas pela primeira vez.
- Aprimoramos a cobertura para os seguintes eventos do Salesforce e os separamos da atividade **Gerenciar usuários**:
  - Editar permissões
  - Criar usuário
  - Alterar a função
  - Redefinir senha

### <a name="cloud-app-security-release-90-91-92"></a>Cloud App Security versão 90, 91, 92

Lançado em fevereiro de 2017

**Anúncio especial:**

Agora o Cloud App Security está oficialmente certificado com a Conformidade da Microsoft para ISO, HIPAA, CSA STAR, cláusulas de modelo da UE e muito mais. Confira a lista completa das certificações no artigo [Ofertas de Conformidade da Microsoft](https://www.microsoft.com/trustcenter/compliance/complianceofferings) selecionando o Cloud App Security.

**Novos recursos:**

- **Importar grupos de usuários (visualização)** Agora, quando você conecta aplicativos usando conectores de API, o Cloud App Security permite que você importe grupos de usuários do Office 365 e do Azure Active Directory. Os cenários típicos que tiram vantagem dos grupos de usuários importados incluem: investigar os documentos que as pessoas de RH observam, verificar se há algo incomum acontecendo no grupo de executivos ou se alguém do grupo administradores realizou uma atividade fora dos EUA. Para obter detalhes e instruções, consulte [importando grupos de usuários](user-groups.md).

- Agora, no Log de atividades, você pode filtrar os usuários e grupos de usuários para mostrar quais atividades foram realizadas por um usuário específico e quais foram realizadas em um usuário específico. Por exemplo, você pode investigar atividades em que o usuário representou outras pessoas e atividades em que outras pessoas representaram esse usuário. Para obter mais informações, consulte [Atividades](activity-filters.md).

- Ao investigar um arquivo na página **Arquivos**, se você fizer uma busca detalhada dos **Colaboradores** de um arquivo específico, agora você poderá ver mais informações sobre os colaboradores. Essas informações incluem se eles são Internos ou Externos, gravadores ou leitores (permissões de arquivo) e, quando um arquivo é compartilhado com um grupo, você agora pode ver todos os usuários que são membros do grupo. Ver todos os usuários permite que você veja se os membros do grupo são usuários externos.

- O suporte a IPv6 agora está disponível para todos os dispositivos.

- O Cloud Discovery agora dá suporte a dispositivos Barracuda.

- Os alertas do sistema do Cloud App Security agora cobrem erros de conectividade do SIEM. Para obter mais informações, consulte [Integração SIEM](siem.md).

- O Cloud App Security agora inclui suporte para as seguintes atividades:

  - **O Office 365, SharePoint/OneDrive**: atualizar configuração de aplicativo, Remover proprietário do grupo, Excluir site, Criar pasta

  - **Dropbox**: Adicionar membro ao grupo, Remover membro do grupo, Criar grupo, Renomear grupo, Alterar nome de membro da equipe

  - **Box**: Remover item do grupo, Atualizar compartilhamento de item, Adicionar usuário ao grupo, Remover usuário do grupo

### <a name="cloud-app-security-release-89"></a>Cloud App Security versão 89

Lançado em 22 de janeiro de 2017

**Novos recursos:**

- Estamos começando a distribuir a capacidade de exibir os eventos de DLP do Centro de Conformidade e Segurança do Office 365 no Cloud App Security. Se você tiver configurado políticas DLP no Centro de Conformidade e Segurança do Office 365, quando forem detectadas correspondências de política, elas serão exibidas no log de atividades do Cloud App Security. As informações no log de atividades incluirão o arquivo ou email que disparou a correspondência e a política ou o alerta correspondente. A atividade de **evento de segurança** permite que você veja correspondências de política de DLP do Office 365 no log de atividades Cloud app Security. Usando esse recurso, você pode:
  - Ver todas as correspondências de DLP provenientes do mecanismo de DLP do Office 365.
  - Alertar sobre as correspondências de políticas DLP do Office 365 para um arquivo, um site do SharePoint ou uma política específica.
  - Investigar as correspondências de DLP em um contexto mais amplo, por exemplo, usuários externos que acessaram ou baixaram algum arquivo que disparou uma correspondência de política DLP.

- As descrições das atividades foram melhoradas ficando mais consistentes e claras. Cada atividade agora fornece um botão de comentários. Se houver alguma coisa que você não entende ou que tenha dúvidas, você pode nos informar.

**Aperfeiçoamentos:**

- Foi adicionada uma nova ação de governança para o Office 365 que permite remover todos os usuários externos de um arquivo. Por exemplo, essa ação permite que você implemente políticas que **removem compartilhamentos externos de arquivos com classificação somente interna**.
- Melhoria na identificação de usuários externos no SharePoint Online. Ao filtrar o grupo "usuários externos", a conta do sistema de aplicativos @"sharepoint" não será exibida.

### <a name="cloud-app-security-release-88"></a>Cloud App Security versão 88

Lançado em 8 de janeiro de 2017

**Novos recursos:**

- Conecte o SIEM ao Cloud App Security. Agora você pode enviar alertas e atividades automaticamente ao SIEM da sua escolha configurando agentes do SIEM. Agora disponível como uma visualização pública.  Para obter a documentação e os detalhes completos, confira Integrando ao SIEM.
- Agora o Cloud Discovery dá suporte a IPv6. Já lançamos o suporte para Palo Alto e Juniper, e mais dispositivos serão lançados nas próximas versões.

**Aperfeiçoamentos:**

- Há um novo fator de risco no catálogo de aplicativos de nuvem. Agora você pode classificar um aplicativo considerando se ele requer autenticação do usuário. Aplicativos que impõem autenticação e não permitem o uso anônimo receberão uma pontuação de risco mais íntegra.
- Estamos lançando novas descrições de atividades que são mais úteis e consistentes. A pesquisa de atividades não será afetada por essa alteração.
- Incluímos melhorias na identificação de dispositivo de usuário, permitindo que o Cloud App Security enriqueça um grande número de eventos com informações de dispositivo.

## <a name="updates-made-in-2016"></a>Atualizações feitas em 2016

### <a name="cloud-app-security-release-87"></a>Cloud App Security versão 87

Liberada em 25 de dezembro de 2016

**Novos recursos:**

- Estamos em processo de lançamento da [anonimização de dados](cloud-discovery-anonymizer.md) para que você possa aproveitar o Cloud Discovery e ainda proteger a privacidade do usuário. A anonimização de dados é executada criptografando as informações de nome de usuário.
- Estamos em processo de lançamento da capacidade de exportar um script de bloqueio do Cloud App Security para dispositivos adicionais. O script permitirá reduzir facilmente a TI sombra bloqueando o tráfego para aplicativos não sancionados. Essa opção está disponível agora para:
  - BlueCoat ProxySG
  - Cisco ASA
  - Fortinet
  - Juniper SRX
  - Palo Alto
  - Websense
- Uma nova ação de governança de Arquivo foi adicionada, a qual permite forçar um arquivo a Herdar permissões do pai, excluindo quaisquer permissões exclusivas configuradas para o arquivo ou pasta. Essa ação de governança de arquivo permite que você altere as permissões de seu arquivo ou pasta para serem herdadas da pasta pai.
- Um novo grupo de usuários chamado Externo foi adicionado. Esse grupo é um grupo de usuários padrão pré-configurado pelo Cloud App Security para incluir todos os usuários que não fazem parte dos seus domínios internos. Você pode usar esse grupo de usuários como um filtro. Por exemplo, você pode encontrar as atividades executadas por usuários externos.
- O recurso Cloud Discovery agora dá suporte a dispositivos Sophos Cyberoam.

**Correções de bugs:**

- Os arquivos SharePoint online e One Drive for Business foram exibidos no relatório de política de Arquivo e na página Arquivos como Internos em vez de Particulares. Esse bug foi corrigido.

### <a name="cloud-app-security-release-86"></a>Cloud App Security versão 86

Liberada em 13 de dezembro de 2016

**Novos recursos:**

- Todas as licenças autônomas do Cloud App Security fornecem a capacidade de habilitar a verificação da Proteção de Informações do Azure nas configurações gerais (sem a necessidade de criação de uma política).

**Aperfeiçoamentos:**

- Agora você pode usar "or" no filtro de arquivo para o nome do arquivo e no filtro de tipo MIME para arquivos e políticas. Essa alteração permite cenários como inserir a palavra "Passport" ou "driver" ao criar uma política para dados pessoais. O filtro corresponderá a qualquer arquivo que tenha "Passport" ou "driver" no nome do arquivo.
- Por padrão, quando uma política DPL de inspeção de conteúdo é executada, os dados nas violações resultantes são mascarados. Agora você poderá cancelar a máscara dos últimos quatro caracteres da violação.

**Pequenos aprimoramentos:**

- Novos eventos relacionados à caixa de correio do Office 365 (Exchange) com relação às regras de encaminhamento, bem como adição e remoção de permissões de caixa de correio delegada.
- Novo evento que audita a concessão de autorização para novos aplicativos no Azure Active Directory.

### <a name="cloud-app-security-release-85"></a>Cloud App Security versão 85

Lançado em 27 de novembro de 2016

**Novos recursos:**

- Foi feita uma distinção entre aplicativos sancionados e aplicativos conectados. Sancionar e não sancionar agora é uma marca que pode ser aplicada a aplicativos descobertos e a qualquer aplicativo no catálogo de aplicativos. Aplicativos conectados são aqueles que você conectou usando o conector de API para aumentar a visibilidade e o controle. Agora você pode marcar aplicativos como sancionados ou não sancionados, ou conectá-los usando o conector de aplicativos, quando estiver disponível.
- Como parte dessa alteração, a página Aplicativos sancionados foi substituída por uma página reformulada chamada **Aplicativos conectados** que exibe dados de status sobre os conectores.
- Os coletores de log são acessados com mais facilidade em suas próprias linhas no menu **Configurações** em **Fontes**.
- Ao criar um filtro de política de atividade, você pode reduzir os falsos positivos optando por ignorar atividades repetidas quando elas são executadas no mesmo objeto de destino pelo mesmo usuário. Por exemplo, várias tentativas de baixar o mesmo arquivo pela mesma pessoa não disparam um alerta.
- Foram feitas melhorias na gaveta de atividades. Agora, ao clicar em um objeto de atividade na gaveta de atividades, você pode fazer uma busca detalhada para obter mais informações.

**Aperfeiçoamentos:**

- Foram feitas melhorias no mecanismo de detecção de anomalias, incluindo os alertas de viagem impossível, para os quais as informações de IP agora estão disponíveis na descrição do alerta.
- Foram feitas melhorias nos filtros complexos para habilitar a adição do mesmo filtro mais de uma vez para ajustar os resultados filtrados.
- As atividades de arquivos e pastas no Dropbox foram separadas para melhorar a visibilidade.

**Correções de bugs:**

- Foi corrigido um bug no mecanismo de alertas do sistema que criava falsos positivos.

### <a name="cloud-app-security-release-84"></a>Cloud App Security versão 84

Lançada em 13 de novembro de 2016

**Novos recursos:**

- O Cloud App Security agora dá suporte à Proteção de Informações do Microsoft Azure incluindo a integração aprimorada e provisionamento automático. Você pode filtrar os Arquivos e definir políticas de arquivo usando a Classificação de marca segura e definir o rótulo de classificação que deseja exibir. Os rótulos também indicam se a classificação foi definida por alguém na sua organização ou por pessoas de outro locatário (Externo). Você também pode definir políticas de atividade com base nos rótulos de classificação da Proteção de Informações do Azure e habilitar a verificação automática para rótulos de classificação no Office 365. Para obter mais informações sobre como aproveitar esse novo recurso, consulte [Integração com o Proteção de Informações do Azure](azip-integration.md).

**Aperfeiçoamentos:**

- Foram feitas melhorias para o log de atividades do Cloud App Security:
  - Eventos do Office 365 do Centro de conformidade e segurança agora estão integrados com o Cloud App Security e são visíveis no **Log de atividade**.
  - Todas as atividades do Cloud App Security são registradas no log de atividades do Cloud App Security como atividades administrativas.
- Para ajudá-lo a investigar os alertas relacionados a arquivos, em cada alerta que resultar de uma política de arquivo, agora você pode exibir a lista de atividades que foram executadas no arquivo correspondente.
- O algoritmo de viagem impossível no mecanismo de detecção de anomalias foi aprimorado para fornecer um melhor suporte para locatários pequenos.

**Pequenos aprimoramentos:**

- O **Limite de exportação de atividade** foi ampliado para 10.000.
- Ao criar um **relatório de instantâneo** no processo de upload do log manual do Cloud Discovery, você agora recebe uma estimativa precisa de quanto tempo levará o processamento do log.
- Em uma política de arquivo, a ação de governança **Remover colaborador** agora funciona em grupos.
- Pequenos aperfeiçoamentos foram feitos na página **Permissões de aplicativo**.
- Quando mais de 10.000 usuários tiverem permissões para um aplicativo que se conecta ao Office 365, a lista é carregada lentamente. Essa lentidão foi corrigida.
- Atributos adicionais foram adicionados ao **Catálogo de aplicativos** sobre a indústria de cartões de pagamento.

### <a name="cloud-app-security-release-83"></a>Cloud App Security versão 83

Lançado em 30 de outubro de 2016

**Novos recursos:**

- Para simplificar a filtragem no [log de atividades](activity-filters.md) e [arquivo de log](file-filters.md), filtros semelhantes foram consolidados. Use os filtros de atividade: objeto Atividade, Endereço IP e Usuário. Use o filtro de arquivo Colaboradores para localizar exatamente o que você precisa.
- Na gaveta do log de atividades, em **Fonte**, você pode clicar no link para **Exibir dados brutos**. Essa ação baixa os dados brutos usados para gerar o log de atividades para fazer uma busca mais detalhada dos eventos de aplicativo.
- Adição de suporte para atividades extras de logon no Okta. [Visualização privada]
- Adição de suporte para atividades extras de logon no Salesforce.

**Aperfeiçoamentos:**

- Melhor utilização de relatórios de instantâneo e solução de problemas do Cloud Discovery.
- Maior visibilidade da lista de alertas em vários aplicativos.
- Melhor utilização na criação de novos relatórios contínuos do Cloud Discovery.
- Melhor utilização do log Governança.

### <a name="cloud-app-security-release-82"></a>Cloud App Security versão 82

Lançado em 9 de outubro de 2016

**Aperfeiçoamentos:**

- As atividades **Alterar email** e **Alterar senha** agora são independentes da atividade genérica **Gerenciar usuários** no Salesforce.
- Foi adicionado um esclarecimento sobre o limite de alerta por SMS diário. Um máximo de 10 mensagens são enviadas por telefone por dia (UTC).
- Foi adicionado um novo certificado para os atributos do Cloud Discovery para a Defesa de Privacidade que substituiu o Safe Harbor (relevante apena para fornecedores dos EUA).
- A solução de problemas foi adicionada às mensagens de falha do conector de API para facilitar a correção de problemas.
- Melhoria na frequência de atualização da verificação de aplicativos de terceiros do Office 365.
- Melhorias no painel do Cloud Discovery.
- O analisador de Syslog de Ponto de Verificação foi aprimorado.
- Melhorias no Log de Governança para veto e cancelamento de veto de aplicativos de terceiros.

**Correções de bugs:**

- Melhoria no processo de upload de logotipo.

### <a name="cloud-app-security-release-81"></a>Cloud App Security versão 81

Lançado em 18 de setembro de 2016

**Aperfeiçoamentos:**

- O Cloud App Security agora é um aplicativo primário no Office 365! De agora em diante, você pode conectar o Office 365 ao Cloud App Security com um único clique.

- Nova aparência para o Log de governança – Agora ele foi atualizado para o mesmo visual nítido e prático que o Log de atividades e a Tabela de arquivos. Use os novos filtros para localizar facilmente o que você precisa e monitorar suas ações de governança.
- Melhorias implementadas no mecanismo de detecção de anomalias para vários logons com falha e fatores de risco adicionais.
- Melhorias implementadas nos relatórios de instantâneo do Cloud Discovery.
- Melhorias implementadas nas atividades administrativas no log de atividades; Alterar a senha, Atualizar usuário e Redefinir senha agora indicam se a atividade foi executada como uma atividade administrativa.
- Os filtros de alerta para os alertas do sistema foram aprimorados.
- O rótulo de uma política em um alerta agora é vinculado ao relatório de política.
- Se não houver nenhum proprietário especificado para um arquivo do Dropbox, as mensagens de email de notificação serão enviadas para o destinatário definido.
- O Cloud App Security dá suporte a 24 idiomas adicionais, ampliando nosso suporte para um total de 41 idiomas.

### <a name="cloud-app-security-release-80"></a>Cloud App Security versão 80

Lançado em 4 de setembro de 2016

**Aperfeiçoamentos:**

- Quando a verificação DLP falhar, agora você receberá uma explicação de por que o Cloud App Security não pôde verificar o arquivo. Para obter mais informações, consulte [Inspeção de Conteúdo](./content-inspection.md).
- Melhorias implementadas nos mecanismos de detecção de anomalias, incluindo melhorias nos alertas de viagem impossível.
- Foram feitas melhorias à experiência de dispensar alerta. Você também pode adicionar comentários para que possa informar a equipe do Cloud App Security se o alerta foi interessante e por quê. Seus comentários serão usados para aprimorar as detecções do Cloud App Security.
- Os analisadores do Cloud Discovery do Cisco ASA foram aprimorados.
- Agora você recebe uma notificação por email quando o upload manual do log do Cloud Discovery é descoberto.

### <a name="cloud-app-security-release-79"></a>Cloud App Security versão 79

Lançado em 21 de agosto de 2016

**Novos recursos:**

- **Novo Painel do Cloud Discovery** – um novo painel do Cloud Discovery está disponível, projetado para fornecer mais informações sobre como os aplicativos de nuvem estão sendo usados na sua organização. Ele fornece uma visão geral rápida de quais tipos de aplicativos estão sendo usados, seus alertas abertos e os níveis de risco dos aplicativos na sua organização. Ele também informa quem são os principais usuários de aplicativo na sua organização e fornece um mapa de localização da Matriz de Aplicativo. O novo Painel tem mais opções para filtrar os dados, para que você possa gerar exibições específicas dependendo do que mais lhe interessa e gráficos de fácil compreensão para fornecer um panorama completo rápido.

- **Novos relatórios do Cloud Discovery** – para exibir os resultados do Cloud Discovery, agora você pode gerar dois tipos de relatórios, Relatórios de Instantâneo e Contínuos. Relatórios de instantâneo fornecem visibilidade ad hoc em um conjunto de logs de tráfego que são carregados manualmente dos seus firewalls e proxies. Relatórios contínuos mostram os resultados de todos os logs que são encaminhados da sua rede usando coletores de log de Cloud App Security. Esses novos relatórios fornecem maior visibilidade em todos os dados, identificação automática de uso anormal conforme identificado pelo mecanismo de detecção de anomalias do aprendizado de máquina do Cloud App Security e identificação de uso anormal definido por você usando o mecanismo de políticas robusto e granular. Para obter mais informações, consulte [configurar Cloud Discovery](set-up-cloud-discovery.md).

**Aperfeiçoamentos:**

- Aperfeiçoamentos de usabilidade geral nas páginas a seguir: Páginas de políticas, Configurações gerais, Configurações de email.
- Na tabela Alertas, é mais fácil distinguir entre alertas lidou e não lidos. Os alertas lidos têm uma linha azul à esquerda e estão esmaecidos para indicar que já foram.
- Os parâmetros da política de Atividade **Atividade repetida** foram atualizados.
- Na página Contas, uma coluna de **Tipo** de usuário foi adicionada, agora você pode ver o tipo de conta de cada usuário. Os tipos de usuário são específicos de aplicativo.
- Suporte quase em tempo real adicionado para as atividades relacionadas a arquivos no OneDrive e no SharePoint. Quando um arquivo é alterado, o Cloud App Security dispara uma verificação quase imediatamente.

### <a name="cloud-app-security-release-78"></a>Cloud App Security versão 78

Lançado em 7 de agosto de 2016

**Aperfeiçoamentos:**

- Em um arquivo específico, agora você pode clicar com o botão direito do mouse e **Localizar relacionados**. No Log de atividades, você pode usar o filtro do objeto de Destino e selecionar o arquivo específico.

- Analisadores de arquivo de log do Cloud Discovery melhorados, incluindo a adição do Juniper e Cisco ASA.
- O Cloud App Security agora permite que você forneça comentários para a melhoria de alertas ao ignorá-los. Você pode ajudar a melhorar a qualidade do recurso de alerta do Cloud App Security informando-nos do motivo pelo qual você está ignorando o alerta. Por exemplo, não é interessante, você recebeu muitos alertas semelhantes, a gravidade real deve ser menor, o alerta não é preciso.
- Foi adicionado o novo link para Políticas correspondentes na exibição de Política de arquivo ou ao exibir um arquivo. Ao clicar nele, você pode exibir todas as correspondências e agora é possível ignorar todas.
- A unidade organizacional à qual um usuário pertence agora é adicionada para todos os alertas relevantes.
- Agora uma notificação por email é enviada para informar quando o processamento de logs manualmente carregados for concluído.

### <a name="cloud-app-security-release-77"></a>Cloud App Security versão 77

Lançado em 24 de julho de 2016

**Aperfeiçoamentos:**

- O ícone do botão Exportar do Cloud Discovery foi aprimorado para facilitar o uso.
- Ao investigar uma atividade, se o agente do usuário não tiver sido analisado, agora você poderá ver os dados brutos.
- Dois novos fatores de risco foram adicionados ao mecanismo de Detecção de Anomalias:
  - O Cloud App Security agora usa as marcas de endereço IP associadas um botnet e endereços IP anônimos como parte do cálculo de risco.
  - Atividade do Office 365 agora é monitorada para altas taxas de download. Se a taxa de download do Office 365 for muito maior do que a da sua organização ou do que a taxa de download normal de um usuário específico, um alerta de detecção de anomalias será disparado.
- O Cloud App Security agora é compatível com a nova API da [funcionalidade de Compartilhamento Seguro](https://blogs.dropbox.com/dropbox/2016/06/new-dropbox-productivity-tools/) do Dropbox.
- Melhorias implementadas para adicionar detalhes aos erros de análise do Log de descoberta, incluindo: Nenhuma nuvem transação de nuvem relacionada, Todos os eventos estão desatualizados, Arquivo corrompido, Formato de log não correspondente.
- O filtro de dados do Log de atividades foi aprimorado, agora ele inclui a capacidade de filtrar por tempo.
- A página de intervalos de endereço IP foi aprimorada para facilitar o uso.
- O Cloud App Security agora inclui suporte para a Proteção de Informações do Microsoft Azure (versão prévia). Você pode filtrar os arquivos e definir políticas de arquivo usando a classificação de marca segura. Em seguida, defina o nível de rótulo de classificação que você deseja exibir. Os rótulos também indicam se a classificação foi definida por alguém na sua organização ou por pessoas de outro locatário (Externo).

### <a name="cloud-app-security-release-76"></a>Cloud App Security versão 76

Lançado em 10 de julho de 2016

**Aperfeiçoamentos:**

- Listas de usuários em relatórios internos agora podem ser exportadas.
- Melhoria na utilização de política de atividade agregada.
- Suporte aprimorado para o analisador de mensagem do log de firewall do TMG W3C.
- Maior facilidade de uso para o menu suspenso de ação de governança de arquivo, que agora está separado em ações de colaboração, segurança e investigação.
- Detecção de viagem impossível aprimorada para a atividade de: Enviar email do Exchange Online.
- Uma nova lista de títulos (trilhas) foi adicionada à parte superior das páginas de Alertas e Política para facilitar a navegação.

**Correções de bugs:**

- A expressão predefinida para Cartão de Crédito nas definição de DLP para as Políticas de Arquivo foi alterada para Todos: Finanças: Cartão de Crédito.

### <a name="cloud-app-security-release-75"></a>Cloud App Security versão 75

Lançado em 27 de junho de 2016

**Novos recursos:**

- Novas adições à crescente lista de eventos do Salesforce com suporte.  Eventos incluem fornecer informações sobre relatórios, links compartilhados, distribuição de conteúdo, logon representado e muito mais.
- Os ícones de aplicativo conectado no painel do Cloud App Security foram alinhados com o status dos aplicativos conforme exibido no painel para refletir os últimos 30 dias.
- Suporte para telas de largura inteira.

**Correções de bugs:**

- Os números de telefone de alerta por SMS agora são validados mediante inserção.

### <a name="cloud-app-security-release-74"></a>Cloud App Security versão 74

Lançamento: 13 de junho de 2016

- A tela Alerta foi atualizada para fornecer mais informações em uma visão geral. As atualizações incluem a capacidade de ver todas as atividades do usuário rapidamente, um mapa de atividades, logs de governança de usuário relacionado, uma descrição do motivo pelo qual o alerta foi disparado e gráficos e mapas adicionais da página do usuário.
- Eventos gerados pelo Cloud App Security agora incluem o tipo de evento, formato, grupos de políticas, objetos relacionados e uma descrição.
- Novas marcas de endereço IP foram adicionadas para aplicativos do Office 365 para Enterprise, OneNote, Office Online e proteção do Exchange Online.
- Agora você tem a opção de fazer upload de logs do menu de descoberta principal.
- O filtro de categoria de endereço IP foi aprimorado. A categoria de endereço IP nula agora é chamada de não categorizada. Uma nova categoria chamada Sem valor foi adicionada para incluir todas as atividades sem dados de endereço IP.
- Os grupos de segurança no Cloud App Security agora são chamados de grupos de usuários para evitar confusão com grupos de segurança do Active Directory.
- Agora é possível filtrar por endereço IP e filtrar eventos sem um endereço IP.
- Foram feitas alterações para as configurações de emails de notificação enviados quando correspondências são detectadas em políticas de atividade e políticas de arquivos. Agora você pode adicionar endereços de email para destinatários que deseja colocar em CC na notificação.

### <a name="cloud-app-security-release-73"></a>Cloud App Security versão 73

Lançamento: 29 de maio de 2016

- Recursos de alerta atualizados: agora, você pode definir alertas por política para serem enviados por email ou como mensagem de texto.
- Página de alertas: design aprimorado para permitir melhor gerenciamento de incidentes e opções avançadas de resolução.
- Ajustar a política: os alertas agora permitem que você mova das opções de resolução de alerta diretamente para a página de configurações de política para habilitar um ajuste fino mais fácil baseado em alertas.
- Melhorias no cálculo de pontuação de risco de detecção de anomalias e taxas de falso-positivos reduzidas com base nos comentários dos clientes.
- A exportação do log de atividades agora inclui a ID de Evento, a Categoria de Evento e o Nome do tipo de Evento.
- Aparência aprimorada e usabilidade de criação das Ações de Governança de criação de política.
- Investigação simplificada e controle para o Office 365 - A seleção do Office 365 escolhe automaticamente todos os aplicativos que fazem parte do Pacote do Office 365.
- Agora as notificações são enviadas para o endereço de email, conforme configurado no aplicativo conectado.
- Em caso de erro de conexão, uma descrição detalhada do erro agora é fornecida pelo aplicativo de nuvem.
- Quando um arquivo corresponde a uma política, uma URL para acessar o arquivo agora é fornecida na gaveta do arquivo.
- Quando um alerta for disparado por uma política de atividade ou por uma política de detecção de anomalias, uma nova notificação detalhada que fornece informações sobre a correspondência é enviada.
- Um alerta de sistema automatizado é disparado quando um conector de aplicativo é desconectado.
- Agora, você pode ignorar e resolver um único alerta ou uma seleção em massa de alertas da página de alertas.

### <a name="cloud-app-security-release-72"></a>Cloud App Security versão 72

Lançamento: 15 de maio de 2016

- Melhorias na aparência e infraestrutura gerais, incluindo:

  - Novo diagrama para fornecer mais assistência com o processo para carregar logs manualmente do Cloud Discovery.
  - Processo aprimorado para atualizar arquivos de log não reconhecidos ("Outro"). Esse processo inclui uma pop-up que permite que você saiba que o arquivo requer análise adicional. Você será notificado quando os dados estiverem disponíveis.
  - Mais atividades e violações de arquivo são realçadas ao investigar uma atividade e o arquivo de log para sistemas operacionais e navegadores desatualizados.

- Analisadores de arquivo de log do Cloud Discovery melhorados, incluindo a adição do Cisco ASA, Cisco FWSM, Cisco Meraki e W3C.
- Melhorias dos problemas conhecidos do Cloud Discovery.
- Novos filtros de atividade adicionados para o domínio do proprietário e afiliação interna/externa.
- Um novo filtro foi adicionado, que permite que você pesquise qualquer objeto do Office 365 (arquivos, pastas, URLs).
- A capacidade foi adicionada ao configurar uma pontuação de risco mínimo para as políticas de detecção de anomalias.
- Ao definir que um alerta será enviado quando uma política for violada, você poderá definir um nível de gravidade mínimo naquela sobre a qual você deseja ser alertado. Você pode optar por usar as configurações padrão da sua organização para isso e também pode definir uma configuração de alerta específica como o padrão para sua organização.

[!INCLUDE [Open support ticket](includes/support.md)]
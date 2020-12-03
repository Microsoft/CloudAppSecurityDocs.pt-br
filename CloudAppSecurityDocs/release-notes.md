---
title: Novidades no Cloud App Security
description: Este artigo é atualizado com frequência para você saber quais são as novidades na versão mais recente do Cloud App Security.
ms.date: 10/25/2020
ms.topic: overview
ms.openlocfilehash: a98d6305b20b7cca12754edc8804781d20dd0f4e
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96315473"
---
# <a name="whats-new-with-microsoft-cloud-app-security"></a>Novidades do Microsoft Cloud App Security

*Aplica-se a: Microsoft Cloud App Security*

Este artigo é atualizado com frequência para você saber quais são as novidades na versão mais recente do Cloud App Security.

Feed RSS: Receba uma notificação quando esta página for atualizada copiando e colando a seguinte URL em seu leitor de feed: `https://docs.microsoft.com/api/search/rss?search=%22This+article+is+updated+frequently+to+let+you+know+what%27s+new+in+the+latest+release+of+Cloud+App+Security%22&locale=en-us`

> [!IMPORTANT]
>
> Os nomes dos produtos de proteção contra ameaças da Microsoft estão mudando. Leia mais sobre essa e outras atualizações [aqui](https://www.microsoft.com/security/blog/?p=91813). Usaremos os novos nomes em versões futuras.

## <a name="cloud-app-security-release-187-and-188"></a>Cloud App Security versões 187 e 188

Lançado em 22 de novembro de 2020

- **Nova integração da TI sombra com a Menlo Security**  
Adicionamos integração nativa à Menlo Security, fornecendo visibilidade de TI sombra sobre o uso de aplicativos e controle sobre o acesso deles. Para obter mais informações, confira [Integrar o Cloud App Security à Menlo Security](menlo-integration.md).

- **Novo analisador de log WatchGuard do Cloud Discovery**  
O Cloud Discovery do Cloud App Security analisa uma ampla variedade de logs de tráfego para classificar e pontuar os aplicativos. Agora o Cloud Discovery inclui um analisador de log interno para dar suporte ao formato WatchGuard. Para acessar a lista de dispositivos com suporte, confira [Proxies e firewalls com suporte](set-up-cloud-discovery.md#supported-firewalls-and-proxies).

- **Nova permissão para função de administrador global do Cloud Discovery**  
O Cloud App Security agora permite que os usuários com a função de administrador global do Cloud Discovery criem tokens de API e usem todas as APIs relacionadas ao Cloud Discovery. Para obter mais informações sobre a função, confira [Funções de administrador internas do Cloud App Security](manage-admins.md#built-in-cloud-app-security-admin-roles).

- **Controle deslizante de confidencialidade avançado: viagem impossível**  
Atualizamos o controle deslizante de confidencialidade de viagem impossível para configurar diferentes níveis de confidencialidade em escopos de usuário distintos, permitindo o controle aprimorado sobre a fidelidade de alertas para escopos de usuário. Por exemplo, você pode definir um nível de confidencialidade mais alto para administradores do que para outros usuários da organização. Confira mais informações sobre essa política de detecção de anomalias em [Viagem impossível](anomaly-detection-policy.md#impossible-travel).

- **Sufixo de URL de proxy avançado para controles de sessão (distribuição gradual)**  
Em 7 de junho de 2020, começamos a distribuir gradualmente nossos controles avançados de sessão de proxy para usar um sufixo unificado que não inclui regiões nomeadas. Por exemplo, os usuários verão o sufixo `<AppName>.mcas.ms` em vez de `<AppName>.<Region>.cas.ms`. Se você bloqueia com frequência domínios em seus dispositivos de rede ou gateways, verifique se colocou na lista de permissões todos os domínios indicados em [Controles de acesso e sessão](network-requirements.md#access-and-session-controls).

## <a name="cloud-app-security-release-184-185-and-186"></a>Cloud App Security versão 184, 185 e 186

Lançado em 25 de outubro de 2020

- **Nova experiência aprimorada de monitoramento e gerenciamento de alertas**  
Como parte de nossas melhorias contínuas no monitoramento e gerenciamento de alertas, a página Alertas do Cloud App Security foi aprimorada com base em seus comentários. Na experiência aprimorada, os status **Resolvido** e **Ignorado** foram substituídos pelo status **Fechado** com um tipo de resolução. [Saiba mais](monitor-alerts.md#deployment-of-our-enhanced-alert-monitoring-and-management-experience)

- **Nova configuração de severidade global para sinais enviados ao Microsoft Defender para Ponto de Extremidade**  
Adicionamos a capacidade de definir a configuração de severidade global para sinais enviados ao Microsoft Defender para Ponto de Extremidade. Para obter mais informações, confira [Como integrar o Microsoft Defender para Ponto de Extremidade ao Cloud App Security](mde-integration.md#how-to-integrate-microsoft-defender-for-endpoint-with-cloud-app-security).

- **Novo relatório de recomendações de segurança**  
O Cloud App Security oferece avaliações da configuração de segurança do Azure, do AWS (Amazon Web Services) e da GCP (Google Cloud Platform), fornecendo insights sobre as lacunas de configuração de segurança em seu ambiente de várias nuvens. Agora você pode exportar relatórios detalhados de recomendação de segurança que ajudam a monitorar, compreender e personalizar os ambientes de nuvem para proteger melhor sua organização. Para obter mais informações sobre como exportar o relatório, confira o [Relatório de recomendações de segurança](security-config.md#security-recommendations-report).

- **Sufixo de URL de proxy avançado para controles de sessão (distribuição gradual)**  
Em 7 de junho de 2020, começamos a distribuir gradualmente nossos controles avançados de sessão de proxy para usar um sufixo unificado que não inclui regiões nomeadas. Por exemplo, os usuários verão o sufixo `<AppName>.mcas.ms` em vez de `<AppName>.<Region>.cas.ms`. Se você bloqueia com frequência domínios em seus dispositivos de rede ou gateways, verifique se colocou na lista de permissões todos os domínios indicados em [Controles de acesso e sessão](network-requirements.md#access-and-session-controls).

- **Atualizações do Catálogo de Aplicativos de Nuvem**  
Fizemos as seguintes atualizações em nosso Catálogo de Aplicativos na Nuvem:

  - O Centro de Administração do Teams foi atualizado como um aplicativo independente
  - O Centro de Administração do Microsoft Office 365 foi renomeado para Portal do Office

- **Atualização de terminologia**  
Atualizamos o termo **computador** para **dispositivo** como parte do esforço geral da Microsoft para alinhar a terminologia entre os produtos.

## <a name="cloud-app-security-release-182-and-183"></a>Cloud App Security versão 182 e 183

Lançado em 6 de setembro de 2020

- **Controles de acesso e sessão para a GA do portal do Azure**  
O Controle de Aplicativos de Acesso Condicional para o portal do Azure já está em disponibilidade geral. Para obter informações sobre como configurar esses controles, confira o [Guia de implantação](proxy-deployment-aad.md).

## <a name="cloud-app-security-release-181"></a>Cloud App Security versão 181

Lançado em 9 de agosto de 2020

- **Novo analisador de log Cloud Discovery da Menlo Security**  
O Cloud Discovery do Cloud App Security analisa uma ampla variedade de logs de tráfego para classificar e pontuar os aplicativos. Agora o Cloud Discovery inclui um analisador de log interno para compatibilidade com o formato CEF da Menlo Security. Para acessar a lista de dispositivos com suporte, confira [Proxies e firewalls com suporte](set-up-cloud-discovery.md#supported-firewalls-and-proxies).

- **O nome do Cloud App Discovery do Azure AD (Active Directory) é exibido no portal**  
Para licenças P1 e P2 do Azure AD, atualizamos o nome do produto no portal para **Cloud App Discovery**. Saiba mais sobre o [Cloud App Discovery](editions-cloud-app-security-aad.md).

## <a name="cloud-app-security-release-179-and-180"></a>Cloud App Security versões 179 e 180

Lançado em 26 de julho de 2020

- **Nova detecção de anomalia: Atividades suspeitas de download de arquivo do aplicativo OAuth**  
Ampliamos nossas detecções de anomalias para incluir atividades suspeitas de download por um aplicativo OAuth. A nova detecção já está disponível, pronta para uso e habilitada automaticamente para alertar você quando um aplicativo OAuth baixa vários arquivos do Microsoft SharePoint ou do Microsoft OneDrive de maneira incomum para o usuário.

- **Melhorias de desempenho com o cache de proxy para controles de sessão (distribuição gradual)**  
Fizemos melhorias de desempenho adicionais em nossos controles de sessão, aprimorando nossos mecanismos de cache de conteúdo. O serviço aprimorado é ainda mais simplificado e fornece maior capacidade de resposta ao usar controles de sessão. Observe que os controles de sessão não armazenam em cache o conteúdo privado, alinhando-se com os padrões apropriados de armazenamento somente do conteúdo compartilhado (público). Para saber mais, confira [Como o controle de sessão funciona](proxy-intro-aad.md#how-session-control-works).

- **Novo recurso: Salvar consultas de configuração de segurança**  
Adicionamos a capacidade de salvar consultas dos nossos filtros de painel de configuração de segurança para o Azure, o AWS (Amazon Web Services) e o GCP (Google Cloud Platform). Isso pode ajudar a tornar futuras investigações ainda mais simples, reutilizando consultas comuns. Saiba mais sobre as [recomendações de configuração de segurança](security-config.md).

- **Aprimoramento dos alertas de detecção de anomalias**  
Ampliamos as informações fornecidas nos alertas de detecção de anomalias para incluir um mapeamento da tática MITRE ATT\&CK correspondente. Esse mapeamento ajudará você a entender a fase e o impacto do ataque e auxiliará nas suas investigações. Saiba mais sobre [Como investigar alertas de detecção de anomalias](investigate-anomaly-alerts.md).

- **Lógica de detecção aprimorada: Atividade de ransomware**  
Atualizamos a lógica de detecção para atividade de ransomware a fim de aumentar a precisão e reduzir o volume de alertas. Para saber mais sobre essa política de detecção de anomalias, confira [Atividade de ransomware](anomaly-detection-policy.md#ransomware-activity).

- **Relatórios de Situação de Segurança de Identidade: Visibilidade das marcas**  
Adicionamos marcas de entidade a relatórios de Situação de Segurança de Identidade que fornecem informações adicionais sobre as entidades. Por exemplo, a marca **Confidencial** ajuda a identificar usuários suspeitos e priorizar as investigações. Saiba mais sobre como [Investigar usuários suspeitos](tutorial-ueba.md).

## <a name="cloud-app-security-release-178"></a>Cloud App Security versão 178

Lançado em 28 de junho de 2020

- **Novas configurações de segurança para a Google Cloud Platform (distribuição gradual)**  
Expandimos as nossas configurações de segurança de várias nuvens para fornecer recomendações de segurança para a Google Cloud Platform, com base no parâmetro de comparação da CIS para GCP. Com essa nova funcionalidade, o Cloud App Security fornece às organizações uma única exibição para monitorar o status de conformidade em todas as plataformas de nuvem, incluindo [assinaturas do Azure](security-config-azure.md), [contas da AWS](security-config-aws.md) e agora [projetos da GCP](security-config-gcp.md).

- **Novos conectores de aplicativos em GA**  
Adicionamos os seguintes conectores de aplicativos ao nosso portfólio de conectores de API em disponibilidade geral, proporcionando a você mais visibilidade e controle sobre como os seus aplicativos são usados na sua organização:
  - [GitHub Enterprise Cloud](protect-github.md)
  - [Google Cloud Platform](protect-gcp.md)
  - [Workday](protect-workday.md)

- **Nova detecção de malware em tempo real em GA**  
Expandimos os nossos controles de sessão para detectar um possível malware usando a Inteligência contra Ameaças da Microsoft em uploads ou downloads de arquivos. A nova detecção agora está em disponibilidade geral pronta para uso e pode ser configurada para bloquear automaticamente os arquivos identificados como possível malware. Para obter mais informações, confira [Bloquear malware no upload](session-policy-aad.md#block-malware-on-upload).

- **Controles de acesso e de sessão aprimorados com qualquer IdP em GA**  
O suporte aos controles de acesso e de sessão para aplicativos SAML configurados com qualquer provedor de identidade agora está em disponibilidade geral. Para obter informações sobre como configurar esses controles, confira o [Guia de implantação](proxy-deployment-aad.md).

- **Aprimoramento na investigação de computadores suspeitos**  
O Cloud App Security fornece a capacidade de identificar computadores suspeitos como parte da sua investigação de descoberta de TI sombra. Agora, adicionamos o **Nível de risco do computador** da Proteção Avançada contra Ameaças do Microsoft Defender à página **computadores** fornecendo mais contexto a analistas quando eles investigarem computadores na sua organização. Para obter mais informações, confira [Investigar dispositivo no Cloud App Security](mde-integration.md#investigate-devices-in-cloud-app-security).

- **Novo recurso: conector de aplicativo de desabilitação de autoatendimento (distribuição gradual)**  
Adicionamos a capacidade de desabilitar conectores de aplicativos diretamente no Cloud App Security. Para mais informações, confira [Desabilitar conectores do aplicativo](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md#disable-app-connectors).

## <a name="cloud-app-security-release-177"></a>Cloud App Security versão 177

Lançado em 14 de junho de 2020

- **Nova detecção de malware em tempo real (versão prévia, distribuição gradual)**  
Expandimos os nossos controles de sessão para detectar um possível malware usando a Inteligência contra Ameaças da Microsoft em uploads ou downloads de arquivos. A nova detecção agora está disponível pronta para uso e pode ser configurada para bloquear automaticamente os arquivos identificados como possível malware. Para obter mais informações, confira [Bloquear malware no upload](session-policy-aad.md#block-malware-on-upload).

- **Novo suporte de token de acesso para controles de acesso e sessão**  
Adicionamos a capacidade de tratar o token de acesso e as solicitações de código como logons ao integrar aplicativos a controles de sessão e acesso. Para usar tokens, clique no ícone de engrenagem de configurações, selecione **Controle de Aplicativos de Acesso Condicional**, edite o aplicativo relevante (menu de três pontos > **Editar aplicativo**), selecione **Tratar as solicitações de token de acesso e código como logons de aplicativo** e clique em **Salvar**. Para obter mais informações sobre a integração de aplicativos, confira [Integrar e implantar qualquer aplicativo](proxy-deployment-any-app.md) e [Implantar aplicativos em destaque](proxy-deployment-aad.md).

- **Sufixo de URL de proxy avançado para controles de sessão (distribuição gradual)**  
Em 7 de junho de 2020, começamos a distribuir gradualmente nossos controles avançados de sessão de proxy para usar um sufixo unificado que não inclui regiões nomeadas. Por exemplo, os usuários verão o sufixo `<AppName>.mcas.ms` em vez de `<AppName>.<Region>.cas.ms`. Se você bloqueia com frequência domínios em seus dispositivos de rede ou gateways, verifique se colocou na lista de permissões todos os domínios indicados em [Controles de acesso e sessão](network-requirements.md#access-and-session-controls).

- **Nova documentação**  
A documentação do Cloud App Security foi expandida para incluir o novo conteúdo a seguir:

  - **[Usar a API REST do Cloud App Security](api-introduction.md)** : saiba mais sobre nossas funcionalidades de API e comece a integrar seus aplicativos com o Cloud App Security.
  - **[Investigar alertas de detecção de anomalias](investigate-anomaly-alerts.md)** : familiarize-se com os alertas de UEBA disponíveis e o que eles significam, identifique o risco que eles representam, compreenda o escopo de uma violação e a ação que pode corrigir a situação.

## <a name="cloud-app-security-release-176"></a>Cloud App Security versão 176

Lançado em 31 de maio de 2020

- **Novo recurso de privacidade da atividade**  
Aprimoramos sua capacidade de determinar de forma granular quais usuários você deseja monitorar com a funcionalidade de tornar as atividades privadas. Esse novo recurso permite que você especifique usuários com base na associação de grupo cujas atividades estarão ocultas por padrão. Somente administradores autorizados têm a opção de exibir essas atividades privadas, com cada instância sendo auditada no log de governança. Para obter mais informações, confira [Privacidade de atividades](activity-privacy.md).

- **Nova integração com a Galeria do Azure AD (Azure Active Directory)**  
Aproveitamos nossa integração nativa com o Azure AD para dar a você a capacidade de navegar diretamente de um aplicativo no catálogo de aplicativos na nuvem para o aplicativo da Galeria do Azure AD correspondente e gerenciá-lo na galeria. Para obter mais informações, confira [Gerenciar aplicativos com a Galeria do Azure AD](tutorial-shadow-it.md#gallery-apps).

- **Nova opção de comentários disponível em políticas selecionadas**  
Estamos interessados em receber seus comentários e saber como podemos ajudar. Agora, uma nova caixa de diálogo de comentários oferece a você a oportunidade de ajudar a melhorar o Cloud App Security, ao criar, modificar ou excluir um arquivo, a detecção de anomalias ou uma política de sessão.

- **Sufixo de URL de proxy avançado para controles de sessão (distribuição gradual)**  
A partir de 7 de junho de 2020, distribuiremos gradualmente nossos controles avançados de sessão de proxy para usar um sufixo unificado que não inclui regiões nomeadas. Por exemplo, os usuários verão o sufixo `<AppName>.mcas.ms` em vez de `<AppName>.<Region>.cas.ms`. Se você adiciona com frequência domínios na lista de bloqueio de seus dispositivos de rede ou gateways, verifique se colocou todos os domínios listados na lista de permissões [Controles de acesso e sessão](network-requirements.md#access-and-session-controls).

- **Melhorias de desempenho para controles de sessão (distribuição gradual)**  
Fizemos melhorias significativas no desempenho da rede para nosso serviço de proxy. O serviço aprimorado é ainda mais simplificado e fornece maior capacidade de resposta ao usar controles de sessão.

- **Nova detecção de atividade arriscada: falha de logon incomum**  
Expandimos a nossa capacidade atual de detecção de comportamentos suspeitos. A nova detecção agora está disponível pronta para uso e habilitada automaticamente para alertá-lo quando uma tentativa de logon com falha incomum for identificada. Tentativas de logon com falha incomum podem ser uma indicação de um possível ataque de força bruta de *password spraying* (também conhecido como o método *baixo e lento*). Essa detecção afeta a [pontuação de prioridade de investigação](tutorial-ueba.md) geral do usuário.

- **Experiência de tabela avançada**  
Adicionamos a capacidade de redimensionar larguras das colunas de tabela para que você possa ampliá-las ou estreitá-las a fim de personalizar e aprimorar a forma como as tabelas são exibidas. Você também pode restaurar o layout original selecionando o menu configurações de tabela e escolhendo **Largura padrão**.

## <a name="cloud-app-security-release-175"></a>Cloud App Security versão 175

Lançado em 17 de maio de 2020

- **Nova integração do Shadow IT Discovery ao Corrata (versão prévia)**  
Adicionamos integração nativa ao Corrata fornecendo visibilidade do Shadow IT sobre o uso do aplicativo e o controle do acesso dele. Para obter mais informações, confira [Integrar o Cloud App Security ao Corrata](corrata-integration.md).

- **Novos analisadores de log do Cloud Discovery**  
O Cloud Discovery do Cloud App Security analisa uma ampla variedade de logs de tráfego para classificar e pontuar os aplicativos. Agora o Cloud Discovery inclui um analisador de log interno para dar suporte aos formatos de log do Corrata e do Cisco ASA com FirePOWER 6.4. Para acessar a lista de dispositivos com suporte, confira [Proxies e firewalls com suporte](set-up-cloud-discovery.md#supported-firewalls-and-proxies).

- **Painel aprimorado (implementação gradual)** Como parte dos nossos aprimoramentos contínuos no design do portal, agora estamos implementando gradualmente o painel do Cloud App Security aprimorado. O painel foi modernizado com base em seus comentários e oferece uma experiência de usuário aprimorada com conteúdo e dados atualizados. Para obter mais informações, confira [Implantação gradual do nosso painel aprimorado](daily-activities-to-protect-your-cloud-environment.md).

- **Governança aprimorada: Confirmar Usuário Comprometido para detecções de anomalias**  
Expandimos as nossas ações de governança atuais para políticas de anomalias para incluir **Confirmar Usuário Comprometido** permitindo que você proteja proativamente o seu ambiente contra atividades suspeitas do usuário. Para obter mais informações, confira [Ações de governança de atividade](governance-actions.md#activity-governance-actions).

## <a name="cloud-app-security-release-173-and-174"></a>Cloud App Security versões 173 e 174

Lançado em 26 de abril de 2020

- **Novo formato CEF de agente SIEM para alertas**  
Como parte do nosso esforço para enriquecer as informações de alerta fornecidas nos arquivos CEF usados por servidores SIEM genéricos, estendemos o formato para incluir os seguintes campos de cliente:
  - Endereço IPv4
  - Endereço IPv6
  - Local do endereço IP

    Para obter mais informações, confira [Formato de arquivo CEF](siem.md#sample-cloud-app-security-alerts-in-cef-format).
- **Lógica de detecção aprimorada: viagem impossível**  
Atualizamos a lógica de detecção para viagem impossível a fim de fornecer precisão aprimorada e volume de alerta reduzido. Confira mais informações sobre essa política de detecção de anomalias em [Viagem impossível](anomaly-detection-policy.md#impossible-travel).

## <a name="cloud-app-security-release-172"></a>Cloud App Security versão 172

Lançado em 5 de abril de 2020

- **Controles de acesso e de sessão aprimorados com qualquer IdP (versão prévia)**  
Agora os controles de acesso e sessão têm suporte para aplicativos SAML configurados com qualquer provedor de identidade. A versão prévia pública desse novo recurso está sendo distribuída gradualmente. Para configurar esses controles, consulte o [Guia de implantação](proxy-deployment-aad.md).

- **Nova identificação em massa de usuários e computadores**  
Expandimos e simplificamos o processo de identificação de um ou mais usuários e computadores sob investigação. Para obter mais informações sobre a identificação em massa, consulte [Como funciona a anonimização de dados](cloud-discovery-anonymizer.md#how-data-anonymization-works).

## <a name="cloud-app-security-release-170-and-171"></a>Cloud App Security versão 170 e 171

Lançado em 22 de março de 2020

- **Nova detecção de anomalia: região incomum para recurso de nuvem (versão prévia)**  
Expandimos a nossa capacidade atual de detecção de comportamentos anormais para a AWS. A nova detecção já está disponível e pronta para uso, habilitada automaticamente para alertá-lo quando um recurso é criado em uma região da AWS onde atividades geralmente não são executadas. Os invasores geralmente aproveitam os créditos da AWS de uma organização para realizar atividades mal-intencionadas, como criptomineração. Detectar esse comportamento anômalo pode ajudar a mitigar um ataque.

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
Expandimos os nossos alertas atuais de comportamento anormal para o Workday. Os novos alertas incluem as seguintes detecções de geolocalização de usuário:
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
O Cloud App Security estendeu a integração nativa com a Microsoft Defender ATP (Proteção Avançada contra Ameaças). Agora, você pode bloquear o acesso a aplicativos marcados como não sancionados usando o recurso de proteção de rede do Microsoft Defender ATP. Para saber mais, confira [Bloquear o acesso a aplicativos na nuvem não sancionados](mde-integration.md#block-access-to-unsanctioned-cloud-apps).

- **Nova detecção de anomalias de aplicativos OAuth**  
Expandimos a nossa capacidade atual de detectar consentimento a aplicativos OAuth mal-intencionados. A nova detecção já está disponível e pronta para uso, habilitada de forma automática para alertar você quando um aplicativo OAuth potencialmente mal-intencionado é autorizado em seu ambiente. Essa detecção aproveita a especialização da Microsoft em pesquisa de segurança e inteligência contra ameaças para identificar aplicativos mal-intencionados.

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

## <a name="see-also"></a>Consulte Também

Confira uma descrição das versões anteriores às listadas aqui em [Versões anteriores do Microsoft Cloud App Security](release-note-archive.md).

[!INCLUDE [Open support ticket](includes/support.md)]
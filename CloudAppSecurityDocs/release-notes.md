---
title: Novidades do Cloud App Security | Microsoft Docs
description: Este tópico é atualizado com frequência para você saber quais são as novidades na versão mais recente do Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 9/3/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: d418ef3d-76ee-45d5-b5ae-21346e5239a3
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 0f0cc3758f09ae77966ace3622e5c658a4e2cf9d
ms.sourcegitcommit: 0ac08ca7b3140b79f1d36ff7152476c188fa12b3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44144645"
---
*Aplica-se ao: Microsoft Cloud App Security*


# <a name="whats-new-with-microsoft-cloud-app-security"></a>Novidades do Microsoft Cloud App Security


## <a name="cloud-app-security-release-131"></a>Versão 131 do Cloud App Security

Lançado em 2 de setembro de 2018

- **Revogar automaticamente as permissões em aplicativos OAuth arriscados**<br>
Agora é possível controlar a quais aplicativos OAuth seus usuários têm acesso, revogando a permissão para aplicativos OAuth no Office, no Google ou no Salesforce. Ao criar uma **política de permissão do aplicativo**, defina a política para revogar a permissão de um aplicativo. 

- **Analisador adicional interno do Cloud Discovery com suporte**<br>O Cloud Discovery agora dá suporte ao formato de log do Forcepoint Web Security Cloud.

 
## <a name="cloud-app-security-release-130"></a>Cloud App Security versão 130

Lançado em 22 de agosto de 2018


- **Nova barra de menus**<br>
Para oferecer uma experiência de administrador mais consistente em todos os produtos do Microsoft 365 e permitir alternar com mais facilidade entre as soluções de segurança da Microsoft, a barra de menus do portal Cloud App Security foi transferida para o lado esquerdo da tela. Essa experiência de navegação consistente ajuda você a se orientar ao mudar de um portal de segurança da Microsoft para outro.

- **Impacto da pontuação do aplicativo OAuth**<br>
Agora você pode enviar os comentários para a equipe do Cloud App Security informando se algum aplicativo OAuth que pareça mal-intencionado foi descoberto na sua organização. Esse novo recurso permite que você participe da nossa comunidade de segurança e melhore a análise e a pontuação de risco do aplicativo OAuth. Saiba mais em [Gerenciar permissões de aplicativos](manage-app-permissions.md).

- **Novos analisadores do Cloud Discovery**<br>
Os analisadores do Cloud Discovery agora oferecem suporte ao iboss Secure Cloud Gateway e Sophos XG.


## <a name="cloud-app-security-release-129"></a>Cloud App Security versão 129

Lançamento de 5 de agosto de 2018

- **Novas políticas de detecção de anomalias – regras de email suspeito**<br>Foram incluídas novas políticas de detecção de anomalias que detectam regras de encaminhamento de email suspeito, por exemplo, se um usuário criou uma regra de caixa de entrada que encaminha uma cópia de todos os emails para um endereço externo. 
- Esta versão inclui correções e melhorias para vários problemas. 

## <a name="cloud-app-security-release-128"></a>Cloud App Security versão 128

Lançado em 22 de julho de 2018

-   **Ações de permissões de aplicativo entre vários aplicativos**<br>
Agora, é possível vetar ou aprovar vários aplicativos em uma única ação caso eles tenham recebido permissões de aplicativo. Por exemplo, é possível analisar todos os aplicativos que receberam permissões de usuários da sua organização, selecionar todos os aplicativos que você deseja vetar e, em seguida, clicar nos aplicativos vetados para revogar todas as permissões concedidas e impedir os usuários de conceder permissões a esses aplicativos.  Para saber mais, confira [Gerenciar permissões de aplicativos](manage-app-permissions.md).
-   **Suporte aprimorado para aplicativos do Azure**<br>
No caso do Azure, estamos distribuindo gradualmente a capacidade de detectar aplicativos como atividades de conta de usuário realizadas por aplicativos do Azure (internos e externos). Isso permite criar políticas que alertarão você caso um aplicativo execute atividades inesperadas e não autorizadas. Para saber mais, confira [Conectar o Azure ao Microsoft Cloud App Security](connect-azure-to-microsoft-cloud-app-security.md).
-   **Mecanismo de classificação de dados atualizado com novos tipos confidenciais do RGPD**<br>
O [Serviço de Classificação de Dados do Cloud App Security](dcs-inspection.md) adicionou novos tipos confidenciais do RGPD ao nosso Mecanismo de Classificação de Dados para que você possa detectar conteúdo relacionado ao RGPD nos seus arquivos.
-   **Atualizações no catálogo do Cloud App**<br>
Agora, o catálogo do Cloud App inclui uma categoria de risco legal (além de Geral, Segurança e Conformidade) para ajudar a gerenciar a privacidade de dados e a conformidade com a propriedade, incluindo preparação para o RGPD.
Para ajudar a avaliar a preparação para o RGPD de cada aplicativo de nuvem, a nova categoria de risco conta com uma instrução de preparação para o RGPD do serviço de nuvem e o status de cada controle de estrutura do RGPD.
Como parte dessa melhoria, os seguintes atributos de risco foram movidos de outra categoria de risco para a categoria Legal:
     - DMCA
     - Propriedade dos dados
     - Política de retenção de dados

     Além disso, a nova categoria de risco é pontuada separadamente para que você possa configurar a pontuação de acordo com suas preferências e prioridades. Para saber mais, confira [Pontuação de risco](risk-score.md).

-   **Nova consulta sugerida: preparação para o RGPD** <br>
Há uma nova consulta sugerida para que você possa identificar aplicativos descobertos preparados para o RGPD. Como o RGPD se tornou uma prioridade para os administradores de segurança recentemente, essa consulta ajuda a identificar facilmente os aplicativos que estão preparados para o RGPD e reduz as ameaças ao avaliar o risco dos aplicativos que não estão preparados para o RGPD.


## <a name="cloud-app-security-release-127"></a>Lançamento 127 do Cloud App Security

Lançado em 8 de julho de 2018

- Agora é possível ver atividades genéricas do Office 365: no **Log de atividades** e em **Políticas de atividades**, você pode filtrar as atividades do Office 365 para atividades **Não especificadas**. Analisar essas atividades permite investigar informações sobre atividades realizadas que ainda não foram classificadas por tipo no Cloud App Security, e é possível usar essas atividades para enviar solicitações à equipe do Cloud App Security para criar novos tipos de atividades com base nessas atividades. 

## <a name="cloud-app-security-release-126"></a>Cloud App Security versão 126

Lançado em 24 de junho de 2018

-   **Disponibilidade geral do Controle de Aplicativos de Acesso Condicional**<br>O Controle de Aplicativos de Acesso Condicional do Microsoft Cloud App Security (proxy reverso) já está disponível para qualquer aplicativo SAML. O Controle de Aplicativos de Acesso Condicional integra-se diretamente às políticas de acesso condicional do Azure AD para **monitorar e controlar as sessões dos usuários em tempo real**, permitindo que elas fiquem produtivas. Desde a primeira versão prévia do recurso, muitos recursos e melhorias foram feitos, incluindo: 
    -   A capacidade de criar uma [política de acesso](access-policy-aad.md) para gerenciar o acesso aos mesmos aplicativos de clientes nativos, além de criar uma política de sessão para o tráfego do navegador.
    -   O processo de integração de aplicativo foi simplificado para dar suporte a aplicativos SAML personalizados em sua organização.
    -   Como parte da rede global do Azure, a integração e a interface foram melhoradas para oferecer uma experiência perfeita para usuários localizados em qualquer lugar do mundo.
 

-   **Disponibilidade geral da inspeção de conteúdo com o Serviço de Classificação de Dados da Microsoft**<br>A integração do Microsoft Cloud App Security com os Serviços de Classificação de Dados da Microsoft já está disponível. Essa integração permite que você utilize de forma nativa o Serviço de Classificação de Dados da Microsoft para classificar os arquivos em seus aplicativos de nuvem. Para obter mais informações, confira [Integração dos Serviços de Classificação de Dados da Microsoft](dcs-inspection.md). Atualmente, este recurso está disponível somente nos EUA e na Europa (exceto na França).

- **Relatório executivo de Cloud Discovery**<br>O Microsoft Cloud App Security está lançando gradualmente a capacidade de gerar um relatório executivo em PDF do Cloud Discovery. Esse relatório oferece uma visão geral do uso de Shadow IT identificado na organização, destacando os principais aplicativos e usuários em uso geral e em categorias líderes, e concentra-se no risco que a Shadow IT apresenta para a organização. Além disso, o relatório oferece uma lista de recomendações de como melhorar a visibilidade e o controle sobre a Shadow IT na organização. Use esse relatório para garantir que os possíveis riscos e ameaças sejam removidos e que a organização permaneça segura e protegida.

-   **Detecção de malware**<br>A funcionalidade de detecção de malware está sendo lançada gradualmente para **detectar arquivos mal-intencionados automaticamente no armazenamento em nuvem**, independentemente do tipo de arquivo. O Microsoft Cloud App Security usa a Inteligência Contra Ameaças da Microsoft para reconhecer se determinados arquivos estão associados a ataques de malware conhecidos ou são possivelmente mal-intencionados. Para obter mais informações, confira [Políticas de detecção de anomalias](anomaly-detection-policy.md).
 
-   **Correção automatizada para atividades suspeitas**<br>Agora é possível definir ações de correção automáticas de sessão suspeita disparadas pelas políticas de detecção de anomalias. Essa melhoria permite que você seja alertado instantaneamente quando ocorre uma violação de segurança e **aplica ações de governança automaticamente**, como a suspensão de um usuário. Para obter mais informações, confira [Políticas de detecção de anomalias](anomaly-detection-policy.md#adp-automated-gov). 
 
-   **Avaliação da configuração de segurança do Azure**<br>O Microsoft Cloud App Security está lançando gradualmente a capacidade de fazer uma avaliação da configuração de segurança do ambiente do Azure e oferece recomendações sobre configurações ausentes e controle de segurança. Por exemplo, ele informará se está faltando a MFA para usuários administrativos. Para obter mais informações, confira [Cloud Security Posture Management integration](security-config.md) (Integração do Gerenciamento de Situação do Cloud Security).  
  
-   **Detecção automática de aplicativos OAuth arriscados**<br>Além da investigação existente dos aplicativos OAuth conectados ao ambiente, o Microsoft Cloud App Security agora está lançando gradualmente a capacidade de definir notificações automatizadas para informá-lo quando um aplicativo OAuth atende a determinados critérios. Por exemplo, você poderá ser alertado automaticamente quando houver aplicativos que requerem um alto nível de permissão e foram autorizados por mais de 50 usuários. Para obter mais informações, confira [Políticas de permissão de aplicativo](app-permission-policy.md).
 
-   **Suporte para gerenciamento de MSSP (Provedores de Serviço de Segurança Gerenciada)**<br>Agora, o Microsoft Cloud App Security fornece uma experiência de gerenciamento melhor para MSSPs. Agora, os usuários externos podem ser configurados como administradores e atribuídos a uma das [funções disponíveis atualmente no Microsoft Cloud App Security](manage-admins.md). Além disso, para permitir que os MSSPs forneçam serviços entre vários locatários de clientes, os administradores que têm direitos de acesso a mais de um locatário agora podem mudar de locatário facilmente no portal. Para obter informações sobre o gerenciamento de administradores, confira [Gerenciar administradores](manage-admins.md).
  
-   **Disponibilidade geral da integração com DLP externa**<br>O Microsoft Cloud App Security permite que você [utilize os investimentos existentes em sistemas de classificação de terceiros](icap-stunnel.md), como soluções de DLP (prevenção contra perda de dados) e examine o conteúdo dos aplicativos de nuvem usando as implantações existentes em execução no seu ambiente de nuvem. Para obter mais informações, confira [Integração com DLP externa](icap-stunnel.md).


## <a name="cloud-app-security-release-125"></a>Lançamento 125 do Cloud App Security

Lançamento em 10 de junho de 2018


- **Nova funcionalidade de investigação por usuários principais:**<br>
Adicionamos um novo widget de investigação ao painel do Microsoft Cloud App Security, que mostra os principais usuários pelo número de alertas abertos de detecção de ameaças. Com este widget, você pode concentrar a investigação de ameaças sobre os usuários que apresentem uma quantidade elevada de sessões suspeitas.

- **Suporte para os buckets AWS S3:**<br>
O Microsoft Cloud App Security já pode detectar buckets do S3 do AWS e os respectivos níveis de compartilhamento. Ele fornece alertas e visibilidade para os buckets do AWS acessíveis publicamente. O programa permite também criar políticas baseadas em buckets e aplicar governança automaticamente. Além disso, temos um novo modelo de política disponível chamado **Buckets do S3 acessíveis publicamente (AWS)**, com o qual você pode facilmente criar uma política para gerenciar o armazenamento do AWS. Para habilitar esses novos recursos, atualize os aplicativos conectados ao AWS adicionando as novas permissões descritas em [Conectar o AWS](connect-aws-to-microsoft-cloud-app-security.md).

- **Privilégios de administrador baseados em grupos de usuários**: agora você pode definir permissões administrativas aos administradores do Microsoft Cloud App Security por grupo de usuários. Por exemplo, é possível definir um usuário específico como administrador apenas para os usuários da Alemanha. Isso permitiria ao usuário exibir e modificar as informações no Microsoft Cloud App Security, somente quando se relacionassem exclusivamente ao grupo de usuários "Alemanha – Todos os usuários". Saiba mais em [Gerenciar acesso de administrador](manage-admins.md).


## <a name="cloud-app-security-release-124"></a>Cloud App Security versão 124

Lançamento: 27 de maio de 2018

-   **Avaliação de risco RGPD adicionada ao catálogo do Cloud App**<br>
Adicionamos 13 fatores novos de risco ao Microsoft Cloud App Security. Esses fatores de risco seguem a lista de verificação do framework do RGPD para que você possa avaliar os aplicativos no catálogo do Cloud App de acordo com as normas de RGPD.

-   **Integrar com o Serviço de Classificação de Dados da Microsoft**<br>
O Microsoft Cloud App Security agora permite que você utilize de forma nativa o Serviço de Classificação de Dados da Microsoft, para classificar os arquivos em seus aplicativos de nuvem. <br>
O Serviço de Classificação de Dados da Microsoft fornece uma experiência de proteção de informações unificada no Office 365, na Proteção de Informações do Azure e no Microsoft Cloud App Security. Ele permite que você estenda a mesma estrutura de classificação de dados para aplicativos de nuvem de terceiros protegidos pelo Microsoft Cloud App Security, aproveitando as decisões já tomadas em uma quantidade ainda maior de aplicativos. 

-   **Conectar-se ao Microsoft Azure** (distribuição gradual)<br>
O Microsoft Cloud App Security está estendendo seus recursos de monitoramento de IaaS para além do Amazon Web Services, e agora dá suporte ao Microsoft Azure. Isso permite que você se conecte e monitore perfeitamente todas as suas assinaturas do Azure com o Cloud App Security. Essa conexão fornece um conjunto avançado de ferramentas para proteger seu ambiente do Azure, incluindo: 

       -    Visibilidade de todas as atividades realizadas por meio do portal

       -    A capacidade de criar políticas personalizadas para alertar sobre comportamento indesejado, bem como a capacidade de proteger automaticamente contra possíveis usuários arriscados por meio de suspensão ou forçando-os a entrar novamente.

       -    Nosso mecanismo de detecção de anomalias abrange todas as atividades do Microsoft Azure, e alerta automaticamente sobre todos os comportamentos suspeitos no Portal do Azure, como viagem impossível, atividades em massa suspeitas e atividade em um novo país.<br>

  Para saber mais, confira [Conectar o Azure ao Microsoft Cloud App Security](connect-azure-to-microsoft-cloud-app-security.md).
 
-   **Implantações com escopo** (distribuição gradual) <br>
O Microsoft Cloud App Security fornece às empresas a capacidade de determinar de forma granular quais usuários eles querem monitorar e proteger com base na associação de grupo. Esse recurso permite que você selecione os usuários cujas atividades não serão exibidas para qualquer um dos aplicativos protegidos. O recurso de monitoramento com escopo é especialmente útil para: 

    -   Conformidade: se as suas regulamentações de conformidade exigirem que você evite o monitoramento de usuários de determinados países devido à legislação local.

       -    Licenciamento: se você deseja monitorar menos usuários a fim de permanecer dentro dos limites de suas licenças do Microsoft Cloud App Security.
   Para saber mais, confira [Implantação com escopo](scoped-deployment.md).

-   **Alerta de aplicativo violado para aplicativos descobertos**<br>
 Agora, temos um alerta interno para notificar você quando houver violação de algum aplicativo descoberto do locatário. O alerta fornecerá informações sobre a data e hora da violação, quais usuários utilizaram o aplicativo e criará um link para fontes publicamente disponíveis que fornecem informações sobre a violação.

-   **Novo servidor de emails**<br>
 O servidor de email do Cloud App Security mudou e usa intervalos de endereço IP diferentes. Para certificar-se de que você pode obter notificações, adicione os novos endereços IP à lista de permissões antispam. Para usuários que personalizam suas notificações, o Microsoft Cloud App Security permite essa opção usando MailChimp®, um serviço de email de terceiros. Para obter a lista de endereços IP do servidor de email e instruções para habilitar o trabalho com o MailChimp, confira [Requisitos de rede](https://docs.microsoft.com/cloud-app-security/network-requirements#email-server) e [Configurações de email](mail-settings.md).


## <a name="cloud-app-security-release-123"></a>Cloud App Security versão 123

Lançamento: 13 de maio de 2018

- **Escopo da política de detecção de anomalias**:<br>
As políticas de detecção de anomalias agora podem ser definidas. Isso permite que você defina cada política de detecção de anomalias para incluir apenas usuários ou grupos específicos e para excluir usuários ou grupos específicos. Por exemplo, você pode definir a Atividade de detecção de regiões pouco frequentes para ignorar um usuário específico que viaja com frequência. 


## <a name="cloud-app-security-release-122"></a>Cloud App Security versão 122
Lançado em 29 de abril de 2018

-   Distribuição gradual: agora é possível **definir permissões administrativas aos administradores do Microsoft Cloud App Security por aplicativo**. Por exemplo, é possível definir um usuário específico como um administrador apenas para o G Suite. Isso permitiria que o usuário exibisse e modificasse as informações no Microsoft Cloud App Security, somente quando se relaciona exclusivamente ao G Suite. Saiba mais em [Gerenciar acesso de administrador](manage-admins.md).
- Distribuição gradual: **agora, as funções de administrador do Okta estão visíveis** no Microsoft Cloud App Security e disponíveis para cada função como uma marca em **Configurações** > **Grupos de usuários**.


## <a name="cloud-app-security-release-121"></a>Cloud App Security versão 121
Lançado em 22 de abril de 2018

-   A visualização pública do **Controle de Aplicativo de Acesso Condicional (anteriormente conhecido como Proxy do Cloud App Security)** foi aprimorada com recursos que possibilitam maior visibilidade e controle sobre vários aplicativos. Agora, você pode criar uma política de sessão com um filtro de *Tipo de atividade* para monitorar e bloquear diversas atividades específicas de aplicativos. Esse novo filtro amplia os recursos existentes de controle de download de arquivos para fornecer controle abrangente dos aplicativos em sua organização e funciona em conjunto com o acesso condicional do Azure Active Directory para fornecer visibilidade em tempo real e controle de sessões de usuário arriscadas; por exemplo, sessões com usuários de colaboração B2B ou provenientes de um dispositivo não gerenciado. Para saber mais, confira [Políticas de sessão](session-policy-aad.md).
-   Implementação gradual: as **políticas de detecção de anomalias do Cloud App Security foram aprimoradas** para incluir dois novos tipos de detecção de ameaças: atividade de ransomware e atividade de usuário demitido. O Cloud App Security estendeu seus recursos de detecção de ransomware com a detecção de anomalias para garantir uma cobertura mais ampla contra ataques de Ransomware sofisticados. Usando nossa experiência com pesquisa de segurança para identificar padrões de comportamentos que refletem a atividade de ransomware, o Cloud App Security garante a proteção holística e robusta. A atividade de usuários demitidos permite que você monitore as contas de usuários demitidos, que podem ter sido desprovisionadas de aplicativos corporativos, mas, em muitos casos, ainda mantêm o acesso a determinados recursos corporativos. Para saber mais, confira o artigo [Obter análise comportamental e detecção de anomalias instantaneamente](anomaly-detection-policy.md).


## <a name="cloud-app-security-release-120"></a>Cloud App Security versão 120
Lançado em 8 de abril de 2018

-   No caso do Office 365 e do Microsoft Azure AD, estamos distribuindo gradualmente a capacidade de detectar aplicativos internos como atividades de conta de usuário realizadas por aplicativos do Office 365 e do Azure AD (internos e externos). Isso permite criar políticas que alertarão você caso um aplicativo execute atividades inesperadas e não autorizadas. 
-   Ao exportar uma lista de permissões de aplicativo para um arquivo CSV, campos adicionais como editor, nível de permissões e uso da comunidade são incluídos para auxiliar no processo de investigação e na conformidade.
-   O aplicativo conectado ServiceNow foi aprimorado para que atividades de serviço internas não sejam mais registradas como tendo sido executadas por "Convidado" e não disparem mais alertas falsos positivos. Agora essas atividades são representadas como N/D, assim como todos os outros aplicativos conectados.


## <a name="cloud-app-security-release-119"></a>Cloud App Security versão 119
Lançado em 18 de março de 2018

-   A página de intervalos de endereços IP inclui os endereços IP internos descobertos pelo Cloud App Security. São incluídos endereços IP de serviços de nuvem identificados, como o Office 365 e o Azure, bem como o feed de inteligência contra ameaças que enriquece automaticamente os endereços IP com informações sobre endereços IP arriscados conhecidos. 
-   Agora, quando tenta executar uma ação de governança em um arquivo e falha porque o arquivo está bloqueado, o Cloud App Security automaticamente tenta a ação de governança novamente. 

## <a name="cloud-app-security-release-118"></a>Cloud App Security versão 118
Lançado em 4 de março de 2018

- Agora você pode tirar proveito dos recursos de descoberta e monitoramento de TI sombra do Microsoft Cloud App Security em seus próprios aplicativos personalizados. A nova capacidade de adicionar aplicativos personalizados ao Cloud Discovery permite monitorar o uso do aplicativo e receber alertas sobre alterações no padrão de uso. Para saber mais, confira [Protegendo os aplicativos personalizados](cloud-discovery-custom-apps.md). Esse recurso está sendo implantado gradativamente.

- As páginas de **Configurações** do portal do Cloud App Security foram reformuladas. O novo design consolida todas as páginas de configurações, fornece a funcionalidade de pesquisa e um design aprimorado. 

- Agora, o Cloud Discovery dá suporte a Firewalls Barracuda série F e streaming de log da Web do Firewall Barracuda série F.

- Agora, a funcionalidade de pesquisa nas páginas de endereço IP e de usuário permite o preenchimento automático para facilitar a localização do conteúdo que você está procurando.

- Agora você pode executar ações em massa nas páginas de configurações Excluir entidades e Excluir endereços IP. Isso facilita a seleção de vários usuários e grupos ou endereços IP e os exclui do monitoramento como parte do Cloud Discovery em sua organização. 

## <a name="cloud-app-security-release-117"></a>Cloud App Security versão 117
Lançado em 20 de fevereiro de 2018

-   Agora, a integração avançada do Cloud App Security com a Proteção de Informações do Azure permite que você proteja arquivos no G Suite. Esse recurso de visualização pública permite examinar e classificar arquivos no G Suite, e aplicar automaticamente os rótulos da Proteção de Informações do Azure para proteção. Para saber mais, confira [Integração com a Proteção de Informações do Azure](azip-integration.md).

-   Agora, o Cloud Discovery dá suporte a [Digital artes i-FILTER](http://www.daj.jp/en/products/if/).

-   A tabela de agentes do SIEM agora inclui mais detalhes para um gerenciamento mais fácil.

## <a name="cloud-app-security-release-116"></a>Cloud App Security versão 116
Lançado em 4 de fevereiro de 2018
- Aprimoramos a política de detecção de anomalias do Cloud App Security com novas **detecções baseadas em cenários**, como viagem impossível, atividade de endereço IP suspeito e várias tentativas de logon com falha. As novas políticas são habilitadas automaticamente, fornecendo a detecção de ameaças pronta para uso no ambiente de nuvem. Além disso, as novas políticas expõem mais dados do mecanismo de detecção do Cloud App Security para ajudar a acelerar o processo de investigação e conter as ameaças em andamento. Para saber mais, confira o artigo [Obter análise comportamental e detecção de anomalias instantaneamente](https://docs.microsoft.com/en-us/cloud-app-security/anomaly-detection-policy).

- Implementação gradual: o Cloud App Security agora correlaciona os usuários e suas contas em aplicativos SaaS. Isso permite investigar facilmente todas as atividades de um usuário, em todos os vários aplicativos SaaS correlacionados, independentemente de qual aplicativo ou conta usaram.  

-   Implementação gradual: o Cloud App Security agora dá suporte a várias instâncias do mesmo aplicativo conectado. Se você tiver várias instâncias do Salesforce (uma para venda, uma para marketing), por exemplo, poderá conectar os dois ao Cloud App Security e gerenciá-los no mesmo console para criar políticas granulares e uma investigação mais detalhada. 

- Os analisadores do Cloud Discovery agora fornecem suporte para dois formatos de ponto de verificação adicionais, XML e KPC.



## <a name="cloud-app-security-release-115"></a>Lançamento 115 do Cloud App Security
Lançado em 21 de janeiro de 2018

- Este lançamento fornece uma experiência aprimorada ao selecionar pastas específicas nas políticas de arquivo. Agora, é possível exibir e selecionar rapidamente várias pastas para incluir em uma política. 
- Na página **Aplicativos descobertos**: 
  - o recurso de marcação em lotes permite aplicar marcações personalizadas, além das marcações Sancionado e Não Sancionado. 
  - Quando você **Gerar um relatório de endereço IP** ou **Gerar o relatório de um usuário**, os relatórios exportados agora incluirão informações sobre a proveniência do tráfego de aplicativos sancionados ou não sancionados. 
- Você já pode solicitar um novo Conector de aplicativos da API à equipe do Microsoft Cloud App Security diretamente no portal, na página **Conectar um aplicativo**. 


## <a name="cloud-app-security-release-114"></a>Cloud App Security versão 114
Lançado em 7 de janeiro de 2018

- A partir da versão 114, gradualmente, desenvolvemos a capacidade de criar e salvar consultas personalizadas no log de Atividades e nas páginas de Aplicativos descobertos. As consultas personalizadas possibilitam criar modelos de filtro que podem ser reutilizados para uma investigação profunda. Além disso, as **Consultas sugeridas** foram adicionadas para fornecer modelos de investigação prontos para uso, a fim de filtrar as atividades e os aplicativos descobertos. As **Consultas sugeridas** incluem filtros personalizados para identificar riscos, como atividades de representação, atividades de administrador, aplicativos de armazenamento em nuvem que apresentam riscos e que estão fora de conformidade, aplicativos empresariais com criptografia fraca e riscos de segurança. Use as **Consultas sugeridas** como ponto de partida, modifique-as conforme considerar adequado e, em seguida, salve-as como uma nova consulta. Para saber mais, confira [Filtros e consultas de atividades](activity-filters-queries.md) e [Filtros e consultas de aplicativos descobertos](discovered-app-queries.md).
 
- Agora você pode verificar o status atual do serviço do Cloud App Security acessando [status.cloudappsecurity.com](https://status.cloudappsecurity.com) ou diretamente no portal clicando em **Ajuda**>**Status do sistema**. 
 


## <a name="see-also"></a>Consulte Também  

Confira a descrição dos lançamentos anteriores aos relacionados aqui em [Lançamentos anteriores do Microsoft Cloud App Security](release-note-archive.md).

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
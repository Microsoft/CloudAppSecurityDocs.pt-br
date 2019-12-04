---
title: Arquivos de atualizações anteriores do Cloud App Security
description: Este artigo é um arquivo que descreve as atualizações feitas em lançamentos anteriores do Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 673c69637b1efce249d0ae54fc6115d08229b9af
ms.sourcegitcommit: 7c93b6f93d2699d466b172590710ed01697bbdad
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74720916"
---
# <a name="past-release-archive-of-microsoft-cloud-app-security"></a>Arquivo Morto de atualizações anteriores do Microsoft Cloud App Security

*Aplica-se ao: Microsoft Cloud App Security*

Este artigo é um arquivo que descreve as atualizações feitas em lançamentos anteriores do Cloud App Security. Para ver a lista de novidades, confira [Novidades sobre o Cloud App Security](release-notes.md).

## <a name="updates-made-in-2017"></a>Atualizações feitas em 2017

### <a name="cloud-app-security-release-113"></a>Cloud App Security versão 113

Lançado em 25 de dezembro de 2017

- Temos o prazer de anunciar que o Cloud App Security agora é compatível com uma integração mais profunda com a Proteção de Informações do Azure. Esse recurso de visualização pública permite examinar e classificar arquivos em aplicativos na nuvem e aplicar automaticamente os rótulos da Proteção de Informações do Azure para proteção. Esse recurso está disponível para Box, SharePoint e OneDrive. Para saber mais, confira [Integração com a Proteção de Informações do Azure](azip-integration.md).

- Os analisadores de log do Cloud Discovery agora têm suporte para formatos genéricos: LEEF, CEF e W3C.

### <a name="cloud-app-security-release-112"></a>Lançamento 112 do Cloud App Security

Lançado em 10 de dezembro de 2017

- Agora, para acessar a gaveta de informações relevante, basta clicar em um nome de usuário ou endereço IP no log de atividades.
- Ao investigar atividades, agora você pode facilmente exibir todas as atividades dentro do mesmo período de dentro da gaveta de insights clicando no ícone de relógio. O ícone de relógio permite que você exiba todas as atividades realizadas dentro de 48 horas da atividade que você está exibindo.
- Melhorias implementadas no analisador de logs do Cloud Discovery para Juniper SRX.
- Para atividades monitoradas pelo proxy, o **Objeto da atividade** foi expandido para incluir informações relevantes para verificações DLP. Políticas correspondentes foram expandidas para incluir violações de DLP se existirem.

### <a name="cloud-app-security-release-111"></a>Cloud App Security versão 111

Lançado em 26 de novembro de 2017

- Agora as políticas de descoberta oferecem suporte a marcas do aplicativo como uma condição e uma ação de governança. Essa adição permite que você marque automaticamente os aplicativos recém-descobertos com marcas personalizadas, como **Aplicativos populares**. Você também pode usar a marca do aplicativo como um filtro. Por exemplo, "Alerte-me quando um aplicativo na 'Watchlist' tiver mais de 100 usuários em um único dia".

- O filtro **Tempo** foi aprimorado para torná-lo mais fácil de usar.

- A inspeção de conteúdo agora permite distinguir entre o conteúdo, metadados e nome de arquivo, permitindo que você selecione qual deles deseja inspecionar.

- Uma nova ação de governança foi adicionada ao G Suite. Agora, você pode **Reduzir o acesso público** para arquivos compartilhados. Essa ação permite que você defina os arquivos disponíveis publicamente a serem disponibilizados somente com um link compartilhado.

- Todas as atividades de logon para outros aplicativos agora aparecerão no Cloud App Security como proveniente do OKTA. Você pode visualizar e filtrar com base no aplicativo de destino para o qual o logon foi executado no campo **Objetos da atividade**.

### <a name="cloud-app-security-release-110"></a>Cloud App Security versão 110

Lançado em 12 de novembro de 2017

- Agora geralmente disponível: estamos começando a implementar um novo modo de implantação para o coletor de logs. Além da atual implantação baseada em dispositivo virtual, o novo coletor de logs baseado em Docker (contêiner) pode ser instalado como um pacote em [computadores Ubuntu](discovery-docker.md), tanto localmente quanto no Azure. Ao usar o Docker, o computador host é de propriedade do cliente, que pode fazer patch livremente e monitorá-lo.

- Usando o novo ponto de interrogação azul no canto, é possível agora acessar a página de documentação relevante do Cloud App Security em docs.microsoft.com de dentro das páginas do portal. Cada link é contextual e direciona você para as informações de que precisa com base na página que você está usando.
- Agora, você pode enviar comentários de qualquer página do portal do Cloud App Security. Os comentários permitem que você informe bugs, solicite novos recursos e compartilhe sua experiência diretamente com a equipe do Cloud App Security.
- Foram feitas melhorias na capacidade do Cloud Discovery de reconhecer subdomínios para investigações aprofundadas sobre o uso de nuvem de sua organização. Para saber mais, confira [Trabalhando com aplicativos descobertos](discovered-apps.md).

### <a name="cloud-app-security-release-109"></a>Cloud App Security versão 109

Lançado em 29 de outubro de 2017

- A distribuição do recurso de proxy do Microsoft Cloud App Security foi iniciada. O proxy do Microsoft Cloud App Security fornece as ferramentas necessárias para ter exibição em tempo real e controle sobre o acesso ao seu ambiente de nuvem e as atividades dentro dele. Por exemplo:

  - Evite o vazamento de dados bloqueando os downloads antes que eles ocorram.
  - Defina as regras que forçam os dados armazenados na e baixados da nuvem a serem protegidos com criptografia.
  - Obtenha visibilidade para pontos de extremidade desprotegidos para que você possa monitorar o que está sendo feito em dispositivos não gerenciados.
  - Controle o acesso por meio de redes não corporativas ou endereços IP arriscados.

  Saiba mais em [Proteger aplicativos com o Controle de Aplicativo de Acesso Condicional](proxy-intro-aad.md).

- Estamos distribuindo gradualmente a capacidade de filtrar de acordo com os nomes de atividades de serviços específicos. Esse novo filtro de tipo de atividade é mais granular, para que você possa monitorar as atividades de aplicativos específicas, em vez de tipos de atividade mais gerais. Por exemplo, anteriormente, você podia filtrar por **Executar o comando**, e agora você pode filtrar para cmdlets EXO específicos. O nome da atividade também pode ser visto na gaveta de atividade em **Tipo (em aplicativo)** . Essa funcionalidade substituirá o filtro de tipo de atividade.

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
- Para ajudá-lo a se preparar para a conformidade com o GDPR, reunimos as instruções de preparação dos aplicativos de nuvem no Catálogo de Aplicativos de Nuvem. Isso ainda não afeta a pontuação de risco do aplicativo, mas fornecerá um link para a página de preparação do GDPR do distribuidor do aplicativo, assim que estiver disponível. A Microsoft ainda não verificou o conteúdo, portanto não é responsável pela respectiva validade.

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

- Como as informações de endereço IP são cruciais para quase todas as investigações, agora você pode exibir informações detalhadas sobre endereços IP na Gaveta de atividades. De dentro de uma atividade específica, você agora pode clicar na guia Endereços IP para exibir os dados consolidados sobre o endereço IP. Os dados incluem o número de alertas abertos para o endereço IP específico, um gráfico de tendência de atividade recente e um mapa do local. Esse recurso permite fazer busca detalhada facilmente. Por exemplo, quando estiver investigando alertas de viagem impossíveis, você pode compreender facilmente em que local o endereço IP foi usado e se ele estava envolvido em atividades suspeitas ou não. Você pode executar ações diretamente na gaveta do endereço IP que permite que você marque um endereço IP como arriscado, VPN ou corporativo para facilitar a criação de políticas e a futura investigação. Para saber mais, confira [Insights sobre endereço IP](activity-filters.md#ip-address-insights)

- No Cloud Discovery, agora você pode usar [formatos de log personalizado](custom-log-parser.md) para [uploads de log automatizados](discovery-docker.md). Formatos de log personalizados permitem que você automatize facilmente o upload de logs de seus SIEMs como servidores Splunk ou qualquer outro formato sem suporte.

- As novas ações de investigação de usuário permitem um nível adicional de análise para investigações do usuário. Nas páginas de **Investigação**, você agora pode clicar com o botão direito do mouse em uma atividade, usuário ou conta e aplicar um dos seguintes novos filtros para investigação e filtragem avançadas: **Exibir atividade relacionada**, **Exibir controle relacionado**, **Exibir alertas relacionados**, **Exibir arquivos de propriedade**, **Exibir arquivos compartilhados com esse usuário**.

- O catálogo do Cloud App agora contém um novo campo para retenção de dados após o encerramento da conta. Esse fator de risco permite que você tenha certeza de que seus dados foram completamente removidos depois de encerrar uma conta dentro de um aplicativo de nuvem.

- O Cloud App Security agora tem visibilidade aprimorada de atividades relativas a objetos do Salesforce. Os objetos incluem clientes potenciais, contas, campanhas, oportunidades, perfis e casos. Por exemplo, a visibilidade do acesso de páginas de conta permite que você configure uma política que alerta se um usuário exibe um número muito grande de páginas de conta. Isso está disponível por meio do Salesforce App Connector, quando você tiver habilitado o Salesforce Event Monitoring (parte do Salesforce Shield).

- Não rastrear agora está disponível para clientes de visualização privada! Agora você pode controlar quais os dados de atividade do usuários são processados. Esse recurso permite definir grupos específicos no Cloud App Security como "Não rastrear". Por exemplo, agora você pode decidir não processar nenhum dado de atividade de usuários localizados na Alemanha ou em qualquer país que não esteja vinculado a uma lei de conformidade específica. Isso pode ser implementado em todos os aplicativos no Cloud App Security, para um aplicativo específico ou até mesmo um subaplicativo específico. Além disso, esse recurso pode ser utilizado para facilitar a distribuição gradual do Cloud App Security. Para saber mais ou para participar da visualização privada para esse recurso, entre em contato com o suporte ou seu representante de conta.

### <a name="cloud-app-security-release-100"></a>Cloud App Security versão 100

Lançado em 3 de julho de 2017

**Novos recursos**

- **Extensões de segurança:** extensões de segurança é um novo painel para gerenciamento centralizado de todas as extensões de segurança ao Cloud App Security.  Extensões incluem gerenciamento de token de API, agentes SIEM e conectores de DLP Externo. O novo painel está disponível no Cloud App Security em "Configurações".

  - Tokens de API – gere e gerencie seus próprios [tokens de API](api-tokens.md) para integrar o Cloud App Security com software de terceiros usando nossas APIs RESTful.
  - Agentes SIEM – [integração SIEM](siem.md) estava localizada anteriormente em "Configurações", agora disponível como um guia de Extensões de Segurança.
  - DLP externo (Versão Prévia) – o Cloud App Security permite que você [utilize os investimentos existentes em sistemas de classificação de terceiros](icap-stunnel.md), como soluções de DLP (prevenção de perda de dados) e permite examinar o conteúdo de aplicativos usando as implantações existentes em execução no seu ambiente de nuvem. Entre em contato com seu gerente de conta para ingressar na versão prévia.

- **Sancionar/cancelar sanção automaticamente:** as novas políticas de detecção de aplicativo dão ao Cloud Discovery a capacidade de definir automaticamente aplicativos com rótulo Sancionado/Não sancionado. Isso lhe dá a capacidade de identificar automaticamente os aplicativos que estão violando políticas e regulamentos da sua organização e adicioná-los ao script de bloqueio gerado.
- **Rótulos de arquivo de segurança do Cloud App Security:** agora você pode aplicar rótulos de arquivo do Cloud App Security para fornecer mais informações nos arquivos verificados. Para cada arquivo verificado pelo DLP do Cloud App Security, você poderá saber se os arquivos foram bloqueados de serem inspecionados porque foram criptografados ou corrompidos. Por exemplo, você pode configurar políticas para alertá- e arquivos protegidos por senha em quarentena que são compartilhados externamente. Este recurso está disponível para arquivos examinados após 3 de julho de 2017.

    Você pode filtrar esses arquivos usando o filtro **Rótulos de classificação** > **Cloud App Security**:

  - **Azure RMS criptografado** – arquivos cujo conteúdo não foi inspecionado porque têm um conjunto de criptografia do Azure RMS.
  - **Criptografado por senha** – arquivos cujo conteúdo não foi inspecionado porque são protegidos por senha pelo usuário.
  - **Arquivo corrompido** – arquivos cujo conteúdo não foi inspecionado porque seu conteúdo não pôde ser lido.

- **Insights do usuário**: a experiência de investigação foi atualizada para permitir informações prontas sobre o usuário em ação. Com um único clique, agora você pode obter uma visão geral abrangente dos usuários da Gaveta de atividades. Os insights incluem de que localização eles se conectaram, com quantos alertas em aberto eles estão envolvidos e suas informações de metadados.
- **Insights do conector de aplicativo:** em **Conectores de Aplicativos**, cada aplicativo conectado agora inclui uma gaveta de aplicativos na tabela para análise mais fácil de seu status. Os detalhes fornecidos incluem quando o conector de aplicativos foi conectado e integridade da última verificação no conector. Você também pode monitorar o status da verificação de DLP em cada aplicativo: o número total de arquivos inspecionados pelo DLP, bem como o status das verificações em tempo real (solicitadas verificações versus verificações reais). Você poderá saber se a taxa de arquivos examinados pelo Cloud App Security em tempo real é menor do que o número solicitado e se o locatário pode ser exceder sua capacidade e a experiência de um atraso de resultados de DLP.

- **Personalização do Catálogo de aplicativos de nuvem:**

  - **Marcas de aplicativo**: agora você pode criar marcas personalizadas para aplicativos. Essas marcas podem ser usadas como filtros para aprofundar-se nos tipos específicos de aplicativos que você deseja investigar. Por exemplo, lista de observação personalizada, atribuição a uma unidade de negócios específica ou aprovações personalizadas, como "aprovado pelo departamento jurídico".
  - **Notas personalizadas**: conforme você examina e avalia os diferentes aplicativos que foram descobertos em seu ambiente, agora você pode salvar suas conclusões e ideias em Notas.
  - **Pontuação de risco personalizada**: agora você pode substituir a pontuação de risco de um aplicativo. Por exemplo, se a pontuação de risco de um aplicativo for 8 e esse for um aplicativo sancionado na sua organização, você poderá alterar a pontuação de risco para 10 para sua organização. Você também pode adicionar observações para tornar a justificativa da alteração clara quando qualquer pessoa analisar o aplicativo.

- **Novo modo de implantação do coletor de log:** estamos começando a implementar um novo modo de implantação que agora está disponível para o coletor de logs. Além da implantação baseada em dispositivo virtual atual, o novo coletor de log baseado em Docker (contêiner) pode ser instalado como um pacote nos computadores com Windows e Ubuntu, tanto localmente quanto no Azure. Ao usar o Docker, o computador host é de propriedade do cliente, que pode fazer patch livremente e monitorá-lo.

**Avisos:**

- O catálogo do Cloud App agora oferece suporte a mais de 15.000 aplicativos detectáveis
- Conformidade: o Cloud App Security oficialmente é certificado para SOC1/2/3 pelo Azure. Para obter a lista completa das certificações, confira [Ofertas de conformidade](https://www.microsoft.com/trustcenter/compliance/complianceofferings) e filtre os resultados por Cloud App Security.

**Outros aperfeiçoamentos:**

- **Melhor análise:** foram feitas melhorias no mecanismo de análise de log do Cloud Discovery. Erros internos têm probabilidade significativamente menor de ocorrer.
- **Formatos de log esperados:** o formato esperado de log para logs de Cloud Discovery agora fornece exemplos de ambos os formatos de Syslog e FTP.
- **Status de upload do coletor de logs:** agora, você pode ver o status do coletor de logs no portal e solucionar problemas de erros mais rapidamente com as notificações de status no portal e os alertas do sistema.

### <a name="cloud-app-security-release-99"></a>Cloud App Security versão 99

Lançado em 18 de junho de 2017

**Novos Recursos**

- Agora você pode exigir que os usuários entrem novamente para todos os aplicativos do Azure AD e do Office 365. Exija entrada novamente como uma correção rápida e eficaz para alertas de atividade de usuário suspeitos e contas comprometidas. Você pode encontrar a nova governança nas configurações de política e nas páginas de alertas, ao lado da opção Suspender usuário.
- Agora você pode filtrar para atividades de **Adicionar atribuição de função de representação** no log de atividades. Esta atividade permite que você detecte quando um administrador concedeu uma função de **Representação de aplicativo** a qualquer usuário ou conta de sistema, usando o cmdlet **ManagementRoleAssignment novo**. Esta função permite que o representante execute operações ao usar permissões associadas à conta representada, em vez de permissões associadas à conta do representante.

**Melhorias do Cloud Discovery:**

- Os dados do Cloud Discovery agora podem ser aprimorados com os dados de nome de usuário do Azure Active Directory. Quando você habilita esse recurso, o nome de usuário recebido nos logs de tráfego de descoberta é correspondido e substituído pelo nome de usuário do Azure AD. O enriquecimento permite os seguintes novos recursos:
  - Você pode investigar o uso de TI sombra pelo usuário do Azure Active Directory.
  - Você pode correlacionar o uso do aplicativo de nuvem Descoberto com as atividades coletadas pela API.
  - Então, você pode criar logs personalizados com base nos grupos de usuários do Azure AD. Por exemplo, um relatório de TI sombra para um departamento de Marketing específico.
- Foram feitos aperfeiçoamentos ao analisador de syslog Juniper. Agora, ele dá suporte aos formatos de welf e sd-syslog.
- Aprimoramentos foram feitos ao analisador Palo Alto para melhor descoberta de aplicativo.
- Para verificar se os logs estão sendo carregados com êxito, agora você pode ver o status dos seus Coletores de log no portal do Cloud App Security.

**Aperfeiçoamentos gerais:**

- Marcas de endereço IP internas e marcas de IP personalizadas são consideradas hierarquicamente agora, com marcas de IP personalizadas, tendo precedência sobre as marcas de IP internas. Por exemplo, se um endereço IP estiver marcado como **Arriscado** com base em inteligência de ameaça, mas houver uma marca IP personalizada que o identifique como **Corporativo**, as marcas e a categoria personalizada terão precedência.

### <a name="cloud-app-security-release-98"></a>Cloud App Security versão 98

Lançado em 4 de junho de 2017

**Atualizações do Cloud Discovery:**

- Os usuários agora podem executar a filtragem avançada em aplicativos descobertos. A filtragem permite que você execute a investigação profunda. Por exemplo, a filtragem de aplicativos com base no uso. Muito tráfego de upload de aplicativos descobertos de determinados tipos? Quantos usuários utilizaram determinadas categorias de aplicativos? Você também pode executar várias seleções no painel esquerdo para selecionar várias categorias.
- Distribuição iniciada de novos modelos para Cloud Discovery, que se baseiam em pesquisas populares, por exemplo, "aplicativo de armazenamento de nuvem sem conformidade". Esses filtros básicos podem ser usados como modelos para executar análise em seus aplicativos descobertos.
- Para facilidade de uso, você pode executar ações como sancionar e cancelar a sanção de vários aplicativos em uma ação.
- Agora estamos lançando a capacidade de criar relatórios de descoberta personalizados com base em grupos de usuários do Azure Active Directory. Por exemplo, se você quiser ver o uso de nuvem de seu departamento de marketing, poderá importar o grupo de marketing usando o recurso importar grupo de usuários e, em seguida, criar um relatório personalizado para este grupo.

**Novos recursos:**

- O RBAC para leitores de segurança concluiu a distribuição. Esse recurso permite que você gerencie as permissões concedidas aos seus administradores dentro do console do Cloud App Security. Por padrão, todos os administradores do Azure Active Directory, os administradores globais do Office 365 e os administradores de Segurança têm permissão total no portal. Todos os leitores de segurança no Azure Active Directory e do Office 365 têm acesso somente leitura no Cloud App Security. Você pode adicionar outros administradores ou substituir permissões usando a opção "Gerenciar acesso". Para saber mais, confira [Gerenciar permissões de administrador](manage-admins.md).
- Agora estamos lançando relatórios de inteligência de ameaça detalhados para endereços IP arriscados detectados pelo gráfico de segurança inteligente da Microsoft. Quando uma atividade é executada por um botnet, você verá o nome do botnet (se disponível) com um link para um relatório detalhado sobre o botnet específico.

### <a name="cloud-app-security-release-97"></a>Cloud App Security versão 97

Lançado em 24 de maio de 2017

**Novos recursos:**

- Investigue os arquivos e as violações de política: agora você pode ver todas as correspondências de política na página de arquivos. Além disso, a página de alerta do arquivo foi aprimorada para incluir uma guia separada para o Histórico do arquivo específico. A melhoria permite fazer busca detalhada no histórico de violação entre todas as políticas para o arquivo específico. Cada evento histórico inclui um instantâneo do arquivo no momento do alerta. Isso incluirá uma indicação de se o arquivo foi excluído ou colocado em quarentena.
- [Quarentena do administrador](use-case-admin-quarantine.md) agora está disponível em versão prévia privada para o Office 365 SharePoint e o OneDrive for Business. Esse recurso permite que você coloque em quarentena os arquivos que correspondem a políticas ou defina uma ação automatizada para colocá-los em quarentena. Colocar em quarentena remove os arquivos do diretório do usuário do SharePoint e copia os originais para a localização de quarentena de administrador que você escolher.

**Melhorias do Cloud Discovery:**

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

- Continuando a distribuição gradual da permissão de Leitor de Segurança, que permite que você gerencie as permissões concedidas aos seus administradores dentro do console do Cloud App Security. Por padrão, todos os administradores globais do Azure Active Directory, do Office 365 e de Segurança têm permissão total no portal. Todos os leitores de segurança no Azure Active Directory e do Office 365 terão acesso somente leitura no Cloud App Security. Para saber mais, confira [Gerenciar permissões de administrador](manage-admins.md).
- Distribuição concluída do suporte ao Cloud App Security para analisadores de log definidos pelo usuário para logs baseados em CSV. O Cloud App Security permite que você configure um analisador para seus dispositivos anteriormente sem suporte fornecendo as ferramentas para delinear quais colunas se correlacionam com dados específicos. Para saber mais, confira [Analisador de log personalizado](custom-log-parser.md).

**Melhorias:**

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

   Por exemplo, agora você pode monitorar os usuários que receberam permissões **SendAs** para as caixas de correio de outros usuários e, como resultado, podem enviar emails em nome deles.

### <a name="cloud-app-security-release-95"></a>Cloud App Security versão 95

Lançado em 24 de abril de 2017

**Atualizações:**

- A página **Contas** foi atualizada com aprimoramentos que facilitam a detecção de riscos. Você agora pode filtrar mais facilmente para contas internas e externas. Veja rapidamente se um usuário tem permissões de administrador. Você pode executar ações em cada conta por aplicativo, como remover permissões, remover colaborações do usuário, suspender o usuário. Além disso, [grupos de usuários](user-groups.md) importados para cada conta serão exibidos.

- Para as contas de trabalho da Microsoft (Office 365 e Azure Active Directory), o Cloud App Security agrupa diferentes identificadores de usuário como endereços de proxy, aliases, SIDs e muito mais em uma única conta. Todos os aliases relacionados a uma conta aparecerão sob o endereço de email principal. Com base na lista de identificadores de usuário, para atividades cujo ator é um identificador de usuário, o ator será exibido como o nome UPN do nome de usuário primário. Com base no nome UPN, serão atribuídos a grupos e políticas aplicadas. Essa alteração vai melhorar a investigação de atividades e unirá todas as atividades relacionadas à mesma sessão de anomalias e políticas baseadas em grupo. Este recurso será implantado gradualmente no próximo mês.

- A marca de Robô foi adicionada como um possível fator de risco no relatório interno de uso do navegador. Agora, além de o uso do navegador ser marcado como obsoleto, você pode ver quando o uso do navegador foi executado por um robô.
- Ao criar uma política de arquivo de inspeção de conteúdo, agora você pode definir o filtro para incluir apenas os arquivos com pelo menos 50 correspondências.

### <a name="cloud-app-security-release-94"></a>Cloud App Security versão 94

Lançado em 2 de abril de 2017

**Novos recursos:**

- O Cloud App Security agora está integrado ao Azure RMS. Você pode proteger arquivos no OneDrive e no Sharepoint Online do Office 365 com o Microsoft Rights Management diretamente do portal do Cloud App Security. A proteção pode ser obtida na página **Arquivos**. Para saber mais, confira [Integrar com a Proteção de Informações do Azure](azip-integration.md). Aplicativos adicionais terão suporte em versões futuras.
- Até agora, era especialmente difícil identificar quando as atividades de bots e rastreadores ocorriam em sua rede porque as atividades não eram executadas por um usuário em sua rede. Sem o seu conhecimento, bots e rastreadores podem executar ferramentas maliciosas em seus computadores. Agora, o Cloud App Security fornece as ferramentas para ver quando bots e rastreadores estão realizando atividades em sua rede. Você pode usar a nova marca de agente do usuário para filtrar atividades no log correspondente. A marca de agente do usuário permite que filtrar todas as atividades realizadas por bots e você pode usá-la para criar uma política que o alerta sempre que esse tipo de atividade for detectado. Você será informado quando versões futuras incluírem essas atividades de risco, que estarão incorporadas aos alertas de detecção de anomalias.
- A nova página de permissões de aplicativo unificada permite investigar mais facilmente as permissões que os usuários tem fornecido a aplicativos de terceiros. Ao clicar em **Investigar** > **Permissões de aplicativo**, agora você pode exibir uma lista de todas as permissões que os usuários forneceram a aplicativos de terceiros. Uma página de permissões de aplicativo por aplicativo conectado permite comparar melhor os diversos aplicativos e as permissões concedidas. Para saber mais, veja [Gerenciar permissões de aplicativos](manage-app-permissions.md).
- Você pode filtrar os dados diretamente da Gaveta da tabela para uma análise mais fácil.
No **Log de atividades**, a tabela **Arquivos** e as páginas **Permissões de aplicativo** agora são aprimoradas com novas ações contextuais que tornam a dinamização do processo de investigação muito mais fácil. Também adicionamos links rápidos para as páginas de configuração e a capacidade de copiar dados com um único clique. Para saber mais, confira as informações sobre [como trabalhar com as gavetas de atividades e de arquivos](file-filters.md).
- Concluída a implementação do suporte para logs de atividades e alertas do Microsoft Teams para Office 365.

### <a name="cloud-app-security-release-93"></a>Cloud App Security versão 93

Lançado em 20 de março de 2017

**Novos recursos:**

- Agora, você pode aplicar políticas para incluir ou excluir grupos de usuários importados.
- A Anonimização do Cloud App Security agora permite que você configure uma chave de criptografia personalizada. Para saber mais, veja [Anonimização do Cloud Discovery](cloud-discovery-anonymizer.md).
- Para ter mais controle sobre o gerenciamento de usuário e conta, agora, você tem acesso direto às configurações da conta do Azure AD para cada usuário e conta da página **Conta**. Basta clicar na engrenagem ao lado de cada usuário. Essa alteração facilita o acesso aos recursos avançados de gerenciamento de usuários, de grupos, ao gerenciamento de grupos, à configuração de MFA, aos detalhes sobre logons de usuário e à possibilidade de bloquear a entrada.
- Agora você pode exportar um script de bloqueio para aplicativos não sancionados por meio da API do Cloud App Security. Aprenda sobre nossas APIs no portal do Cloud App Security clicando no ponto de interrogação na barra de menus, seguido por **documentação da API**.
- O conector do aplicativo do Cloud App Security para ServiceNow foi expandido para incluir suporte para tokens de OAuth (como apresentado em Genebra, Helsinque, Istambul). Essa alteração fornece uma conexão de API mais robusta para o ServiceNow não depende do usuário que está implantando. Para saber mais, confira [Conectar o ServiceNow ao Microsoft Cloud App Security](connect-servicenow-to-microsoft-cloud-app-security.md). Os clientes existentes podem atualizar as configurações na página de conector do Aplicativo ServiceNow.
- Se você tiver configurado scanners DLP adicionais de terceiros, o status de verificação de DLP agora mostrará o status de cada conector de forma independente para melhorar a visibilidade.
- Agora, o Cloud App Security conta com suporte para atividades de Equipes da Microsoft que são suportadas no log de auditoria do Office 365. Esse recurso está sendo implantado gradativamente.
- Para eventos de representação do Exchange Online, agora você pode filtrar pelo nível de permissão usado-delegado, administrador ou administrador delegado. Você pode pesquisar eventos que exibam o nível de representação que lhe interessa no **log de atividades** pesquisando objetos de **atividade** > **Item**.
- Na gaveta de aplicativos na guia **Permissões do Aplicativo** dos aplicativos do Office 365, você pode ver o **Editor** de cada aplicativo. Você também pode usar o Editor como um filtro para investigar outros aplicativos do mesmo editor.
- Agora, os endereços IP com risco são exibidos como um fator de risco independente em vez de ponderados no fator de risco de **Localização** geral.
- Quando os rótulos de Proteção de Informações do Azure estiverem desabilitados em um arquivo, os rótulos desabilitados serão exibidos como desabilitados no Cloud App Security. Rótulos excluídos não serão exibidos.

**Suporte adicional do Salesforce:**

- Agora, você pode suspender e cancelar a suspensão de usuários do Salesforce no Cloud App Security. Essa ação pode ser realizada na guia **Contas** do Conector do Salesforce. Clique na engrenagem ao final da linha de um usuário específico e selecione **Suspender** ou **Cancelar suspensão**. Suspender e cancelar suspensão também podem ser aplicados como uma ação de governança como parte de uma política. Todas as atividades suspensas e não suspensas realizadas no Cloud App Security serão registradas no [Log de governança](governance-actions.md).
- Melhor visibilidade ao compartilhamento de conteúdo do Salesforce: agora você pode ver quais arquivos foram compartilhados e com quem, incluindo arquivos compartilhados publicamente, arquivos compartilhados com grupos e arquivos compartilhados com todo o domínio do Salesforce. Uma maior visibilidade será implantada retroativamente a aplicativos do Salesforce novos e conectados atualmente. Poderá levar algum tempo para essas informações serem atualizadas pela primeira vez.
- Aprimoramos a cobertura para os seguintes eventos do Salesforce e os separamos da atividade **Gerenciar usuários**:
  - Editar permissões
  - Criar usuário
  - Alterar função
  - Redefinir senha

### <a name="cloud-app-security-release-90-91-92"></a>Cloud App Security versão 90, 91, 92

Lançado em fevereiro de 2017

**Comunicado especial:**

Agora o Cloud App Security está oficialmente certificado com a Conformidade da Microsoft para ISO, HIPAA, CSA STAR, cláusulas de modelo da UE e muito mais. Confira a lista completa das certificações no artigo [Ofertas de Conformidade da Microsoft](https://www.microsoft.com/trustcenter/compliance/complianceofferings) selecionando o Cloud App Security.

**Novos recursos:**

- **Importar grupos de usuários (visualização)** Agora, quando você conecta aplicativos usando conectores de API, o Cloud App Security permite que você importe grupos de usuários do Office 365 e do Azure Active Directory. Os cenários típicos que tiram vantagem dos grupos de usuários importados incluem: investigar os documentos que as pessoas de RH observam, verificar se há algo incomum acontecendo no grupo de executivos ou se alguém do grupo administradores realizou uma atividade fora dos EUA. Para obter detalhes e instruções, consulte [Importar grupos de usuários](user-groups.md).

- Agora, no Log de atividades, você pode filtrar os usuários e grupos de usuários para mostrar quais atividades foram realizadas por um usuário específico e quais foram realizadas em um usuário específico. Por exemplo, você pode investigar atividades em que o usuário representou outras pessoas e atividades em que outras pessoas representaram esse usuário. Para obter mais informações, consulte [Atividades](activity-filters.md).

- Ao investigar um arquivo na página **Arquivos**, se você fizer uma busca detalhada dos **Colaboradores** de um arquivo específico, agora você poderá ver mais informações sobre os colaboradores. Essas informações incluem se eles são Internos ou Externos, gravadores ou leitores (permissões de arquivo) e, quando um arquivo é compartilhado com um grupo, você agora pode ver todos os usuários que são membros do grupo. Ver todos os usuários permite que você veja se os membros do grupo são usuários externos.

- O suporte a IPv6 agora está disponível para todos os dispositivos.

- O Cloud Discovery agora dá suporte a dispositivos Barracuda.

- Os alertas do sistema do Cloud App Security agora cobrem erros de conectividade do SIEM. Para obter mais informações, confira [Integração do SIEM](siem.md).

- O Cloud App Security agora inclui suporte para as seguintes atividades:

  - **O Office 365, SharePoint/OneDrive**: atualizar configuração de aplicativo, Remover proprietário do grupo, Excluir site, Criar pasta

  - **Dropbox**: Adicionar membro ao grupo, Remover membro do grupo, Criar grupo, Renomear grupo, Alterar nome de membro da equipe

  - **Box**: Remover item do grupo, Atualizar compartilhamento de item, Adicionar usuário ao grupo, Remover usuário do grupo

### <a name="cloud-app-security-release-89"></a>Cloud App Security versão 89

Lançado em 22 de janeiro de 2017

**Novos recursos:**

- Estamos começando a distribuir a capacidade de exibir os eventos de DLP do Centro de Conformidade e Segurança do Office 365 no Cloud App Security. Se você tiver configurado políticas DLP no Centro de Conformidade e Segurança do Office 365, quando forem detectadas correspondências de política, elas serão exibidas no log de atividades do Cloud App Security. As informações no log de atividades incluirão o arquivo ou email que disparou a correspondência e a política ou o alerta correspondente. A atividade **Evento de segurança** permite exibir as correspondências de políticas DLP do Office 365 no log de atividades do Cloud App Security. Usando esse recurso, você pode:
  - Ver todas as correspondências de DLP provenientes do mecanismo de DLP do Office 365.
  - Alertar sobre as correspondências de políticas DLP do Office 365 para um arquivo, um site do SharePoint ou uma política específica.
  - Investigar as correspondências de DLP em um contexto mais amplo, por exemplo, usuários externos que acessaram ou baixaram algum arquivo que disparou uma correspondência de política DLP.

- As descrições das atividades foram melhoradas ficando mais consistentes e claras. Cada atividade agora fornece um botão de comentários. Se houver algo que você não entenda ou tiver dúvidas, poderá nos informar.

**Melhorias:**

- Foi adicionada uma nova ação de governança para o Office 365 que permite remover todos os usuários externos de um arquivo. Por exemplo, essa ação permite que você implemente políticas que **removem compartilhamentos externos de arquivos com classificação somente interna**.
- Melhoria na identificação de usuários externos no SharePoint Online. Ao filtrar usando o grupo "usuários externos", a conta do sistema app@"sharepoint" não será exibida.

### <a name="cloud-app-security-release-88"></a>Cloud App Security versão 88

Lançado em 8 de janeiro de 2017

**Novos recursos:**

- Conecte o SIEM ao Cloud App Security. Agora você pode enviar alertas e atividades automaticamente ao SIEM da sua escolha configurando agentes do SIEM. Agora disponível como uma visualização pública.  Para obter a documentação e os detalhes completos, confira Integrando ao SIEM.
- Agora o Cloud Discovery dá suporte a IPv6. Já lançamos o suporte para Palo Alto e Juniper, e mais dispositivos serão lançados nas próximas versões.

**Melhorias:**

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
- Uma nova ação de governança de Arquivo foi adicionada, a qual permite forçar um arquivo a Herdar permissões do pai, excluindo quaisquer permissões exclusivas configuradas para o arquivo ou pasta. Essa ação de governança de arquivo permite alterar o arquivo ou as permissões da pasta a serem herdadas da pasta pai.
- Um novo grupo de usuários chamado Externo foi adicionado. Esse grupo é um grupo de usuários padrão pré-configurado pelo Cloud App Security para incluir todos os usuários que não fazem parte dos seus domínios internos. Você pode usar esse grupo de usuários como um filtro. Por exemplo, você pode encontrar as atividades executadas por usuários externos.
- O recurso Cloud Discovery agora dá suporte a dispositivos Sophos Cyberoam.

**Correções de bugs:**

- Os arquivos SharePoint online e One Drive for Business foram exibidos no relatório de política de Arquivo e na página Arquivos como Internos em vez de Particulares. Esse bug foi corrigido.

### <a name="cloud-app-security-release-86"></a>Cloud App Security versão 86

Liberada em 13 de dezembro de 2016

**Novos recursos:**

- Todas as licenças autônomas do Cloud App Security fornecem a capacidade de habilitar a verificação da Proteção de Informações do Azure nas configurações gerais (sem a necessidade de criação de uma política).

**Melhorias:**

- Você pode agora usar “or” no filtro de arquivo para o nome do arquivo e no filtro de tipo MIME para arquivos e políticas. Essa alteração permite cenários como inserir a palavra "passaporte" OR "driver" ao criar uma política para os dados pessoais. O filtro corresponderá a qualquer arquivo que tenha "passaporte" ou "driver" no nome do arquivo.
- Por padrão, quando uma política DPL de inspeção de conteúdo é executada, os dados nas violações resultantes são mascarados. Agora você poderá cancelar a máscara dos últimos quatro caracteres da violação.

**Pequenos aperfeiçoamentos:**

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

**Melhorias:**

- Foram feitas melhorias no mecanismo de detecção de anomalias, incluindo os alertas de viagem impossível, para os quais as informações de IP agora estão disponíveis na descrição do alerta.
- Foram feitas melhorias nos filtros complexos para habilitar a adição do mesmo filtro mais de uma vez para ajustar os resultados filtrados.
- As atividades de arquivos e pastas no Dropbox foram separadas para melhorar a visibilidade.

**Correções de bugs:**

- Foi corrigido um bug no mecanismo de alertas do sistema que criava falsos positivos.

### <a name="cloud-app-security-release-84"></a>Cloud App Security versão 84

Lançada em 13 de novembro de 2016

**Novos recursos:**

- O Cloud App Security agora dá suporte à Proteção de Informações do Microsoft Azure incluindo a integração aprimorada e provisionamento automático. Você pode filtrar os Arquivos e definir políticas de arquivo usando a Classificação de marca segura e definir o rótulo de classificação que deseja exibir. Os rótulos também indicam se a classificação foi definida por alguém na sua organização ou por pessoas de outro locatário (Externo). Você também pode definir políticas de atividade com base nos rótulos de classificação da Proteção de Informações do Azure e habilitar a verificação automática para rótulos de classificação no Office 365. Para obter mais informações sobre como aproveitar esse novo recurso, consulte [Integração com o Proteção de Informações do Azure](azip-integration.md).

**Melhorias:**

- Foram feitas melhorias para o log de atividades do Cloud App Security:
  - Eventos do Office 365 do Centro de conformidade e segurança agora estão integrados com o Cloud App Security e são visíveis no **Log de atividade**.
  - Todas as atividades do Cloud App Security são registradas no log de atividades do Cloud App Security como atividades administrativas.
- Para ajudá-lo a investigar os alertas relacionados a arquivos, em cada alerta que resultar de uma política de arquivo, agora você pode exibir a lista de atividades que foram executadas no arquivo correspondente.
- O algoritmo de viagem impossível no mecanismo de detecção de anomalias foi aprimorado para fornecer um melhor suporte para locatários pequenos.

**Pequenos aperfeiçoamentos:**

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

**Melhorias:**

- Melhor utilização de relatórios de instantâneo e solução de problemas do Cloud Discovery.
- Maior visibilidade da lista de alertas em vários aplicativos.
- Melhor utilização na criação de novos relatórios contínuos do Cloud Discovery.
- Melhor utilização do log Governança.

### <a name="cloud-app-security-release-82"></a>Cloud App Security versão 82

Lançado em 9 de outubro de 2016

**Melhorias:**

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

**Melhorias:**

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

**Melhorias:**

- Quando a verificação DLP falhar, agora você receberá uma explicação de por que o Cloud App Security não pôde verificar o arquivo. Para obter mais informações, consulte [Inspeção de Conteúdo](https://aka.ms/aka.ms/cas-contentinspection).
- Melhorias implementadas nos mecanismos de detecção de anomalias, incluindo melhorias nos alertas de viagem impossível.
- Foram feitas melhorias à experiência de dispensar alerta. Você também pode adicionar comentários para que possa informar a equipe do Cloud App Security se o alerta foi interessante e por quê. Seus comentários serão usados para aprimorar as detecções do Cloud App Security.
- Os analisadores do Cloud Discovery do Cisco ASA foram aprimorados.
- Agora você recebe uma notificação por email quando o upload manual do log do Cloud Discovery é descoberto.

### <a name="cloud-app-security-release-79"></a>Cloud App Security versão 79

Lançado em 21 de agosto de 2016

**Novos recursos:**

- **Novo Painel do Cloud Discovery** – um novo painel do Cloud Discovery está disponível, projetado para fornecer mais informações sobre como os aplicativos de nuvem estão sendo usados na sua organização. Ele fornece uma visão geral rápida de quais tipos de aplicativos estão sendo usados, seus alertas abertos e os níveis de risco dos aplicativos na sua organização. Ele também informa quem são os principais usuários de aplicativo na sua organização e fornece um mapa de localização da Matriz de Aplicativo. O novo Painel tem mais opções para filtrar os dados, para que você possa gerar exibições específicas dependendo do que mais lhe interessa e gráficos de fácil compreensão para fornecer um panorama completo rápido.

- **Novos relatórios do Cloud Discovery** – para exibir os resultados do Cloud Discovery, agora você pode gerar dois tipos de relatórios, Relatórios de Instantâneo e Contínuos. Relatórios de instantâneo fornecem visibilidade ad hoc em um conjunto de logs de tráfego que são carregados manualmente dos seus firewalls e proxies. Relatórios contínuos mostram os resultados de todos os logs que são encaminhados da sua rede usando os coletores de logs do Cloud App Security. Esses novos relatórios fornecem maior visibilidade em todos os dados, identificação automática de uso anormal conforme identificado pelo mecanismo de detecção de anomalias do aprendizado de máquina do Cloud App Security e identificação de uso anormal definido por você usando o mecanismo de políticas robusto e granular. Para obter mais informações, confira [Configurar o Cloud Discovery](set-up-cloud-discovery.md).

**Melhorias:**

- Aperfeiçoamentos de usabilidade geral nas páginas a seguir: Páginas de políticas, Configurações gerais, Configurações de email.
- Na tabela Alertas, é mais fácil distinguir entre alertas lidou e não lidos. Os alertas lidos têm uma linha azul à esquerda e estão esmaecidos para indicar que já foram.
- Os parâmetros da política de Atividade **Atividade repetida** foram atualizados.
- Na página Contas, uma coluna de **Tipo** de usuário foi adicionada, agora você pode ver o tipo de conta de cada usuário. Os tipos de usuário são específicos de aplicativo.
- Suporte quase em tempo real adicionado para as atividades relacionadas a arquivos no OneDrive e no SharePoint. Quando um arquivo é alterado, o Cloud App Security dispara uma verificação quase imediatamente.

### <a name="cloud-app-security-release-78"></a>Cloud App Security versão 78

Lançado em 7 de agosto de 2016

**Melhorias:**

- Em um arquivo específico, agora você pode clicar com o botão direito do mouse e **Localizar relacionados**. No Log de atividades, você pode usar o filtro do objeto de Destino e selecionar o arquivo específico.

- Analisadores de arquivo de log do Cloud Discovery melhorados, incluindo a adição do Juniper e Cisco ASA.
- O Cloud App Security agora permite que você forneça comentários para a melhoria de alertas ao ignorá-los. Você pode ajudar a melhorar a qualidade do recurso de alerta do Cloud App Security informando-nos do motivo pelo qual você está ignorando o alerta. Por exemplo, não é interessante, você recebeu muitos alertas semelhantes, a gravidade real deve ser menor, o alerta não é preciso.
- Foi adicionado o novo link para Políticas correspondentes na exibição de Política de arquivo ou ao exibir um arquivo. Ao clicar nele, você pode exibir todas as correspondências e agora é possível ignorar todas.
- A unidade organizacional à qual um usuário pertence agora é adicionada para todos os alertas relevantes.
- Agora uma notificação por email é enviada para informar quando o processamento de logs manualmente carregados for concluído.

### <a name="cloud-app-security-release-77"></a>Cloud App Security versão 77

Lançado em 24 de julho de 2016

**Melhorias:**

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

**Melhorias:**

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
- Foram adicionadas novas marcas de endereço IP para o Office 365 ProPlus, OneNote, Office Online e Proteção do Exchange Online.
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

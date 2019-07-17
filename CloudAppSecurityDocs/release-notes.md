---
title: Novidades do Cloud App Security
description: Este artigo é atualizado com frequência para mantê-lo informado das novidades na última versão do Cloud App Security.
keywords: ''
author: ShlomoSagir-MS
ms.author: shsagir
manager: ShlomoSagir-MS
ms.date: 7/7/2019
ms.topic: overview
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: d418ef3d-76ee-45d5-b5ae-21346e5239a3
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 96444fd79bebda2b7092e1dbae9a449f0be0bd06
ms.sourcegitcommit: 1b6b827c149b195a241440929970a2ccbb136b83
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/14/2019
ms.locfileid: "67870187"
---
# <a name="whats-new-with-microsoft-cloud-app-security"></a>Novidades do Microsoft Cloud App Security

*Aplica-se a: Microsoft Cloud App Security*

Este artigo é atualizado com frequência para mantê-lo informado das novidades na última versão do Cloud App Security.

RSS feed: receba uma notificação quando esta página for atualizada copiando e colando a seguinte URL em seu leitor de feeds: `https://docs.microsoft.com/api/search/rss?search=%22This+article+is+updated+frequently+to+let+you+know+what%27s+new+in+the+latest+release+of+Cloud+App+Security%22&locale=en-us`

## <a name="cloud-app-security-release-153"></a>Cloud App Security versão 153

Lançado em 7 de julho de 2019

- **Suporte aprimorado do Dropbox**<br>
Agora o Cloud App Security dá suporte à ação de governança **Jogar no lixo** para Dropbox – Esta ação de governança pode ser usada manual ou automaticamente como parte de uma política de arquivo.
- **Novos aplicativos em destaque para Controle de Aplicativos de Acesso à Nuvem**<br>
O Controle de Aplicativos de Acesso Condicional dos seguintes aplicativos em destaque agora está em disponibilidade geral:

    - OneDrive for Business
    - SharePoint online
    - Azure DevOps
    - Exchange Online
    - Power BI

- **Autorizar arquivos identificados como malware**<br>
O Cloud App Security examina os arquivos de seus aplicativos conectados quanto à exposição de DLP e a malware. Agora é possível autorizar arquivos que foram identificados como malware mas que foram confirmados como sendo seguros após uma investigação. Autorizar um arquivo o remove do relatório de detecção de malware e suprime correspondências futuras nele. Para saber mais sobre a detecção de malware, confira [Detecção de anomalias do Cloud App Security](anomaly-detection-policy.md).

## <a name="cloud-app-security-release-152"></a>Cloud App Security versão 152

Lançado em 23 de junho de 2019

- **Implantar Controle de Aplicativos de Acesso Condicional para qualquer aplicativo (versão prévia)**<br>
Temos a satisfação de anunciar que expandimos nosso suporte para o Controle de Aplicativos de Acesso Condicional para qualquer aplicativo Web, além do suporte avançado que já oferecíamos para [nossos aplicativos em destaque](proxy-intro-aad.md). Essa nova funcionalidade permite implantar qualquer aplicativo Web para funcionar com políticas de acesso e sessão, permitindo monitoramento e controle eficientes em tempo real. Por exemplo, você pode proteger downloads com rótulos de Proteção de Informações do Azure, bloquear o upload de documentos confidenciais, fornecer auditoria entre muitas outras ações.
- **Auditoria de atividades do Portal**<br>
O Cloud App Security audita todas as atividades do administrador no portal para fornecer monitoramento e investigação abrangentes das atividades executadas. Agora você também pode exportar até 90 dias de atividades para mais investigação e análise, por exemplo, auditoria de um administrador investigando um usuário específico ou exibindo alertas específicos. Para exportar o log, vá para a página de configurações **Gerenciar acesso de administrador**.
- **Saída da sessão personalizada do portal do Cloud App Security**<br>
Agora você pode configurar a saída automática de sessões de administrador para o portal que estejam ociosas por mais de um período especificado.

## <a name="cloud-app-security-release-151"></a>Cloud App Security, versão 151

Lançado em 9 de junho de 2019

- **UEBA híbrido - integração nativa com o ATP do Azure (versão prévia)**<br>
O Cloud App Security agora nativamente é integrado com o ATP do Azure para fornecer uma exibição única de atividades de identidade em aplicativos de nuvem e sua rede local. Para saber mais, confira [Integração com a Proteção Avançada contra Ameaças do Azure](aatp-integration.md).
- **Aprimoramentos do UEBA**<br>
Para ajudá-lo a identificar ameaças que não são tão evidentes, o Cloud App Security agora usa a exclusiva criação de perfil para fornecer as pontuações de risco para alertas e atividades individuais. As pontuações de risco podem ser usadas para identificar as atividades que não são suspeitas o suficiente para disparar alertas. No entanto, ao agregar as pontuações de risco à **Pontuação de prioridade de investigação** de um usuário, o Cloud App Security ajuda a identificar comportamentos de risco e concentrar sua investigação. Essas novas funcionalidades agora estão disponíveis em nossa página de usuário reprojetada.
- **Novo fator de risco adicionado ao Catálogo de aplicativos de nuvem**<br>
O Catálogo de aplicativos de nuvem agora inclui o fator de risco do Plano de Recuperação de Desastres para que você possa avaliar os aplicativos no Catálogo de aplicativos de nuvem para suporte a continuidade de negócios.
- **Conector GA do Microsoft Flow**<br>
Desde a visualização de suporte do Microsoft Cloud App Security para o conector do Microsoft Flow no ano passado, o conector agora está geralmente disponível.
- **Aprimoramento de governança automatizada para políticas de arquivo**<br>
O Cloud App Security agora dá suporte à configuração da ação de governança da **Lixeira** para políticas de arquivo – essa ação de governança fornece a capacidade de mover arquivos automaticamente para a pasta da lixeira.
- **Suporte aprimorado para o Google Drive**<br>
O Cloud App Security agora dá suporte à ação de governança da **Lixeira** para o Google Drive – essa ação de governança fornece a capacidade de mover arquivos do Google Drive para a pasta da lixeira.
- **Nova permissão para as funções de administrador do aplicativo e administrador de grupo**<br>
As funções *Administrador de aplicativo/instância* e *Administrador de grupo de usuários* agora dão suporte ao acesso somente leitura.

## <a name="cloud-app-security-release-150"></a>Cloud App Security, lançamento 150

Lançado em 26 de maio de 2019

- **Melhoria na exportação de alertas**<br>Quando você exporta alertas para um arquivo CSV na página de **Alertas**, os resultados agora incluem a data de resolução ou de descarte do alerta.


## <a name="cloud-app-security-release-148-and-149"></a>Cloud App Security versão 148 e 149

Lançado em 12 de maio de 2019

- **Conector do aplicativo WebEx disponível**<br>Agora um novo conector de aplicativo está disponível para o Cisco WebEx Teams em visualização pública. Você pode conectar o Microsoft Cloud App Security ao Cisco WebEx Teams para monitorar e proteger seus usuários, atividades e arquivos. Para saber mais, confira [Conectar o WebEx](connect-webex-to-microsoft-cloud-app-security.md)

- **Novos locais do serviço de classificação de dados da Microsoft**<br>O [Serviço de classificação de dados da Microsoft](dcs-inspection.md) agora está disponível em 4 novos locais: Austrália, Canadá, Índia e Japão. Se seu locatário do Office estiver localizado em um desses países, agora você pode utilizar o Serviço de classificação de dados da Microsoft como o método de inspeção de conteúdo nas políticas de arquivo do Microsoft Cloud App Security.

- **Discovery para PaaS e IaaS sombras**<br> O Microsoft Cloud App Security ampliou os recursos do Cloud Discovery e agora também fornece TI sombra para os recursos hospedados em soluções de IaaS e PaaS, como o Microsoft Azure, Amazon Web Services e Google Cloud Platform. O Cloud Discovery fornece a visibilidade de quais aplicativos personalizados são executados sobre seu IaaS e PaaS, as contas de armazenamento que estão sendo criadas e muito mais. Use essa nova funcionalidade para descobrir quais recursos existirem, quem acessa cada um deles e a quantidade de tráfego transmitida.

- **Atestado de aplicativo**<br>A conformidade e avaliação de risco do Microsoft Cloud App Security agora permite que provedores de nuvem atestem seu aplicativo para estar atualizado no Catálogo de Aplicativos de Nuvem. Esse piloto permite que provedores de nuvem preencham um questionário de autocertificação com base nos atributos de risco do Catálogo de aplicativos de nuvem para garantir que sua avaliação de risco no Cloud App Security seja precisa e atualizada. Assim, os usuários podem obter uma indicação de quais atributos de risco foram atestados pelo provedor (em vez de avaliados pela equipe do Cloud App Security) e quando cada atributo foi enviado pelo provedor. Para saber mais, confira [Atestar seu aplicativo](attest-your-app.md). 

- **Granularidade da carga de trabalho do Office 365**<br>Agora, ao conectar o Office 365 ao Microsoft Cloud App Security, você tem controle sobre quais cargas de trabalho deseja conectar. Por exemplo, os clientes interessados apenas em conectar o Office 365 para o monitoramento de atividade agora podem fazê-lo durante o processo de conexão ou ao editar um conector existente do Office 365. Como parte desta alteração, o OneDrive e o SharePoint Online não serão mais mostrados como conectores separados, mas eles serão incluídos no conector do Office 365 como a carga de trabalho de _arquivos do Office 365_. Os clientes com um conector existente do Office 365 não são afetados por essa alteração.

- **Suporte aprimorado do Teams**<br>Agora você pode monitorar e bloquear o envio de mensagens no aplicativo web do Teams em tempo real, configurando uma política de sessão com base no conteúdo confidencial. 

## <a name="cloud-app-security-release-147"></a>Cloud App Security, versão 147

Lançado em 14 de abril de 2019

- **Novo analisador de log do Cloud Discovery**<br>O Cloud App Security Cloud Discovery agora inclui um analisador de log integrado para dar suporte ao formato de log Palo Alto LEEF. 

- **Atualizações de políticas de sessão**
    - **Método adicional de inspeção de conteúdo para políticas de sessão**:<br>Agora, você terá a opção de escolher o Serviço de Classificação de Dados como um método de inspeção de conteúdo para arquivos ao definir uma política de sessão. O Serviço de Classificação de Dados oferece ao usuário uma ampla variedade de tipos confidenciais incorporados para identificar informações confidenciais.
    - **Melhoria no controle de permissões de arquivos nas políticas de sessão**:<br>Agora, você poderá aplicar automaticamente permissões por usuário, como somente leitura, aos documentos após o download de seus aplicativos na nuvem ao criar uma política de sessão para controlar os downloads usando o Cloud App Security. Isso fornece um nível muito maior de flexibilidade e a capacidade de proteger as informações além dos rótulos corporativos pré-configuradas.
    - **Controle de download de arquivo grande**:<br>Quando a inspeção de conteúdo estiver habilitada nas políticas de sessão, você poderá controlar o que acontece quando um usuário tentar baixar um arquivo muito grande. Se o arquivo for grande demais para ser examinado no download, você poderá escolher se ele será bloqueado ou permitido.


## <a name="cloud-app-security-release-146"></a>Cloud App Security, versão 146

Lançada em 31 de março de 2019

- **Melhoria de viagem impossível**<br>
A detecção de viagem impossível foi aprimorada com suporte dedicado para países vizinhos.
- **Suporte de atributo adicional para o analisador de CEF genérico**<br>
O suporte do analisador de log do Cloud Discovery para o formato CEF genérico foi aprimorado para dar suporte a atributos adicionais.
- **Acesso com escopo aos relatórios do Cloud Discovery**<br>
Além da função de Administrador de descoberta, agora você pode definir o acesso com escopo a relatórios específicos de Descoberta. Esse aprimoramento permite configurar privilégios a dados de sites específicos e de unidades de negócios.
- **Novo suporte à função: Leitor global**<br>
O Microsoft Cloud App Security agora dá suporte à função de Leitor Global do Azure AD. O Leitor Global tem acesso completo somente para leitura de todos os aspectos do Microsoft Cloud App Security, mas não pode alterar nenhuma configuração nem realizar nenhuma ação.

## <a name="cloud-app-security-release-145"></a>Cloud App Security versão 145

Lançado em 17 de março de 2019

- **A integração do Microsoft Defender ATP agora está em disponibilidade geral** <br>
Ano passado, anunciamos a [integração com a Proteção Avançada contra Ameaças do Windows Defender](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Microsoft-Cloud-App-Security-and-Windows-Defender-ATP-better/ba-p/263265) que aprimora a descoberta de TI sombra na sua organização e a estende além da rede corporativa. [Habilitado com um único clique](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RWtNmG), estamos animados em anunciar que essa integração exclusiva agora está disponível.
- **Suporte para Dynamics 365 CRM** <br>O Cloud App Security adicionou monitoramento e controle em tempo real no Dynamics 365 CRM para que você possa proteger seus aplicativos de negócios e o conteúdo confidencial armazenado dentro deles. 

## <a name="cloud-app-security-release-144"></a>Versão 144 do Cloud App Security

Lançado em 3 de março de 2019

- **Investigação de SecOps unificada para ambientes híbridos**<br> Como muitas organizações têm ambientes híbridos, os ataques começam na nuvem e, em seguida, mudam para o local, o que significa que as equipes de SecOps precisam investigar esses ataques de vários locais. Combinando sinais de fontes da nuvem e locais, incluindo o Microsoft Cloud App Security, o ATP do Azure e o Azure AD Identity Protection, a Microsoft capacita os analistas de segurança ao fornecer uma identidade unificada e as informações de usuário em um único console, encerrando a necessidade de alternar entre as soluções de segurança. Isso proporciona às suas equipes de SecOps mais tempo e as informações adequadas para tomar as melhores decisões, e corrigir ativamente os riscos e ameaças reais de identidade. Para obter mais informações, confira [Investigação de SecOps unificada para ambientes híbridos](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Unified-SecOps-Investigation-for-Hybrid-Environments/ba-p/360850)


- **Recursos de área restrita para detecção de malware** (distribuição gradual)<br>
Os recursos de detecção de malware do Cloud App Security estão se expandindo para incluir a capacidade de identificar malware de dia zero por meio da tecnologia avançada de área restrita.<br>
Como parte dessa funcionalidade, o Cloud App Security identifica automaticamente arquivos suspeitos e os vasculha, procurando comportamentos de arquivo suspeito e indicadores de que o arquivo é mal-intencionado (malware). <br>
Como parte dessa alteração, as políticas de detecção de malware agora incluem o campo Tipo de detecção que permite que você filtre por inteligência contra ameaças, bem como por áreas de segurança.
- **Atualizações de acesso condicional**<br> O Controle de Aplicativos de Acesso Condicional adicionou a capacidade de monitorar e bloquear as seguintes atividades:
    - Carregamentos de arquivos em qualquer aplicativo – habilitando cenários como impedir o carregamento de extensões de malwares conhecidos e para garantir que os usuários protejam os arquivos com AIP antes do carregamento.
    - Copiar e colar em qualquer aplicativo – refinando controles robustos de extração de dados que já incluíam o controle de atividades de download, impressão e personalizadas, como o compartilhamento.
    - Enviar mensagem – assegurando que os dados PII, como as senhas, não sejam compartilhados em ferramentas populares de colaboração, como o Slack, o Salesforce e o Workplace by Facebook.
- As políticas de sessão agora incluem modelos internos para permitir que sua organização habilite sem esforço o monitoramento popular em tempo real e o controle sobre seus aplicativos sancionados, tais como **Bloquear o upload com base na inspeção de conteúdo em tempo real**.



## <a name="cloud-app-security-release-143"></a>Versão 143 do Cloud App Security

Lançado em 17 de fevereiro de 2019

- **Implantação de escopo para instâncias do aplicativo** A implantação de escopo para instâncias do aplicativo agora pode ser configurada no nível da instância do aplicativo, permitindo maior granularidade e controle.
- **Aprimoramentos de funções** 
   - As funções do Office 365 de operador de segurança e administrador de dados agora têm suporte no Cloud App Security. A função de administrador de dados permite que os usuários gerenciem todo conteúdo relacionado a arquivos, além de exibir os relatórios do Cloud Discovery. Os operadores de segurança têm permissão para gerenciar alertas e exibir a configuração de política.
   - A função de leitor de segurança agora tem a capacidade de configurar o agente SIEM, permitindo melhor escopo de permissão.
- **Suporte do Microsoft Flow** O Cloud App Security agora monitora as atividades dos usuários no Microsoft Flow. As atividades com suporte são as atividades relatadas pelo Flow para o log de auditoria do Office 365.
- **Agrupamento de entidade de alerta** A página **Alerta** agora agrupa entidades relacionadas que foram envolvidas no alerta para ajudar em sua investigação.

## <a name="cloud-app-security-release-142"></a>Versão 142 do Cloud App Security

Lançada em 3 de fevereiro de 2019

- **Configuração de política de sessão no Azure AD**<br>
Agora você pode configurar políticas de sessão para monitorar usuários ou bloquear downloads em tempo real, diretamente no acesso condicional do Azure AD. Você ainda pode configurar as políticas de sessão avançadas diretamente no Cloud App Security. Para ver essa implantação, consulte [Implantar o Controle de Aplicativos de Acesso Condicional para aplicativos do Azure AD](proxy-deployment-aad.md). 

- **Consultas sugeridas e salvas para aplicativos OAuth** <br>
As consultas sugeridas foram adicionadas à página dos aplicativos OAuth para fornecer modelos de investigação prontos para uso, a fim de filtrar os aplicativos OAuth. As consultas sugeridas incluem filtros personalizados para identificar aplicativos arriscados como aplicativos autorizados por administradores. Consultas salvas permitem salvar consultas personalizadas para uso futuro, semelhante às consultas salvas disponíveis atualmente no log de atividades e nas páginas de descoberta. 

- **Configuração padrão de auditoria do Office 365**<br>
Se quiser habilitar o monitoramento de atividades do Office 365 no Cloud App Security, será necessário habilitar a auditoria no [Centro de Conformidade e Segurança do Office](https://docs.microsoft.com/office365/securitycompliance/turn-audit-log-search-on-or-off#turn-on-audit-log-search). Isso é resultado de uma [alteração na auditoria do Office 365](https://docs.microsoft.com/office/office-365-management-api/office-365-management-activity-api-faq#what-happens-if-i-disable-auditing-for-my-office-365-organization-will-i-still-get-events-via-the-management-activity-api). Só será preciso executar essa alteração se você ainda não tiver habilitado o monitoramento de atividades do Office 365 no Cloud App Security.

- **Suporte aprimorado do Box**<br>
O Cloud App Security agora dá suporte a duas novas ações de governança para o Box:

   - **Expiração de link compartilhado** – essa ação de governança fornece a capacidade de definir uma data de término para um link compartilhado, após a qual ele não estará mais ativo. 

   - **Alterar nível de acesso para compartilhamento de link** – essa ação de governança fornece a capacidade de alterar o nível de acesso do link compartilhado entre "somente a empresa", "somente colaboradores" e "público".

- **Suporte a vários locais no OneDrive**<br>
Agora, o Cloud App Security fornece visibilidade completa de arquivos do OneDrive, mesmo se eles estiverem distribuídos em várias localizações geográficas. A proteção agora está disponível para arquivos que estão em outros locais, além do local principal.

- **Melhoria de navegação do portal**<br>
O portal do Cloud App Security foi aprimorado para fornecer uma navegação melhor e alinhar melhor o Cloud App Security com outros serviços de segurança da Microsoft, para facilidade de uso.



## <a name="cloud-app-security-release-141"></a>Lançamento 141 do Cloud App Security

Lançado em 20 de janeiro de 2019

**Aprimoramentos da avaliação de risco de nuvem**
- A avaliação de risco de aplicativo de nuvem foi aperfeiçoada com duas novas experiências. 
    - O novo atributo **Tipo de dados** avalia o tipo de conteúdo que os usuários podem carregar no aplicativo. Você pode usar esse atributo para avaliar um aplicativo de acordo com o nível de confidencialidade de cada tipo de dados na organização. 
    - Para obter uma visão geral de riscos mais abrangente de um aplicativo, agora você pode alternar com facilidade entre a avaliação de risco do aplicativo e a avaliação de risco da empresa de hospedagem, clicando no atributo **Empresa de hospedagem**.

**Contexto de arquivo melhorado para investigação de alertas de detecção de anomalias**
- A investigação de detecção de anomalias foi aprimorada para exibir informações adicionais associadas aos arquivos envolvidos em um alerta. Quando os alertas são acionados para atividades incomuns relacionadas a arquivos (download, compartilhamento, exclusão), esse detalhamento fica disponível. Por exemplo, se a maioria dos arquivos afetados for da mesma pasta ou compartilhar a mesma extensão de arquivo, você verá essas informações na seção "Risco adicional" do alerta.

**Consultas para investigação de arquivo**
- A capacidade de criar e salvar consultas personalizadas foi estendida para a página **Arquivos** do Cloud App Security. Com as consultas na página **Arquivos**, você pode criar modelos de consulta que podem ser reutilizados para uma investigação profunda. 


## <a name="cloud-app-security-release-139-140"></a>Cloud App Security versão 139, 140

Lançado em 6 de janeiro de 2019

- **Alteração na detecção de arquivos**<br>
Os arquivos compartilhados com todas as pessoas no SharePoint e no One Drive agora são considerados **internos** [devido a alterações feitas no SharePoint e no One Drive](https://support.microsoft.com/help/4089534/how-to-grant-the-everyone-claim-to-external-users-in-office-365). Portanto, agora, se for detectado um arquivo compartilhado com todos, ele será tratado como um arquivo interno. Isso afeta como o arquivo é manipulado pelas políticas e mostrado na página de arquivos.

- **Alteração no monitoramento de arquivos**<br>
O comportamento padrão do monitoramento de arquivos foi alterado para clientes novos e ociosos. Agora você precisará habilitar o monitoramento de arquivos para habilitar o recurso, por meio de **Configurações** > **Arquivos**. Os clientes ativos existentes não serão afetados por essa alteração. 

- **Ajuste avançado para políticas de detecção de anomalias**<br>
Agora você pode afetar o mecanismo de detecção de anomalias para suprimir ou mostrar alertas de acordo com suas preferências. 
   - Na política de Viagem Impossível, você pode definir o controle deslizante de sensibilidade para determinar o nível de comportamento anômalo necessário antes que um alerta seja disparado. 
   - Você também pode configurar se os alertas de Atividade de país não frequente, endereços IP anônimos, endereços IP suspeitos e viagem impossível devem analisar os logons com falha e bem-sucedidos ou apenas os bem-sucedidos. 

-   **Suporte para várias cadeias de confiança** O Controle de Aplicativos de Acesso Condicional agora é compatível com a adição e o uso de vários certificados raiz confiáveis ou intermediários como uma forma de gerenciamento de dispositivo.

- **Nova função do Cloud Discovery** (distribuição gradual) Agora, o Cloud App Security fornece uma nova função de administrador para os usuários do Cloud Discovery. Essa função pode ser usada para definir o escopo de acesso de um usuário administrador apenas para as configurações e os dados do Cloud Discovery no portal do Cloud App Security.

- **Suporte para rótulos unificados da Proteção de Informações da Microsoft** (lançamento gradual) O Cloud App Security agora é compatível com os rótulos unificados da Proteção de Informações da Microsoft. Para clientes que já [migraram seus rótulos de classificação para o Centro de Segurança e Conformidade do Office 365](https://docs.microsoft.com/azure/information-protection/configure-policy-migrate-labels), o Cloud App Security identificará e trabalhará com esses rótulos, conforme descrito em [Integrando com a Proteção de Informações do Azure](azip-integration.md). 

**Suporte para rotulagem de arquivo PDF** (lançamento gradual) Para os clientes que usam os rótulos unificados, o Cloud App Security agora é compatível com a rotulagem automática de arquivos PDF.

## <a name="cloud-app-security-release-138"></a>Cloud App Security versão 138

Lançado em 9 de dezembro de 2018

- **Upload automático de log usando o Docker no Windows**<br>Agora o Cloud App Security oferece suporte ao upload automático de log para o Windows 10 (Fall Creators Update) e o Windows Server (versão 1709 e posterior) usando um Docker for Windows.
Confira [Docker no Windows local](discovery-docker-windows.md) para obter mais informações e instruções de como isso pode ser configurado.
- O Cloud App Security integra-se ao [Microsoft Flow](https://docs.microsoft.com/flow/getting-started) para fornecer guias estratégicos de automação e orquestração de alerta personalizadas. Para obter mais informações e instruções de integração, confira [Integrating with Microsoft Flow](flow-integration.md) (Integrando ao Microsoft Flow).


## <a name="cloud-app-security-release-137"></a>Cloud App Security versão 137

Lançado em 25 de novembro de 2018

-   **Adicionado suporte para Dynamics**<br>
Agora, o Cloud App Security conta com suporte para atividades do Microsoft Dynamics compatíveis com o log de auditoria do Office 365. 
-   **Verificação do conteúdo criptografado (Versão Prévia)**<br>
Cloud App Security agora permite que você examine o conteúdo protegido por rótulos de proteção da Proteção de Informações do Azure. Isso permitirá que você encontre conteúdo confidencial até mesmo em arquivos já criptografados pela Proteção de Informações do Azure. 
-   **Atenção – nova terminologia!**<br>
O nome das funcionalidades de permissões de Aplicativo foram foi alterado para maior clareza – agora é chamado **aplicativos de OAuth**. 

## <a name="cloud-app-security-release-136"></a>Cloud App Security versão 136

Lançado em 11 de novembro de 2018


- **Atualizações do Cloud Discovery**<br>
O analisador de log personalizado foi aperfeiçoado para dar suporte adicional e oferecer formatos de logs de tráfego Web mais complexo. Como parte desses aprimoramentos, os usuários agora podem inserir cabeçalhos personalizados para arquivos de log CSV sem cabeçalho, usar delimitadores especiais para arquivos de chave-valor, processar o formato de arquivo do Syslog e muito mais.
- **Novas políticas de detecção de anomalias**<br>
Regras suspeitas de manipulação de caixa de entrada: Essa política analisa o ambiente e dispara alertas quando regras suspeitas que excluem ou movem mensagens ou pastas são definidas na caixa de entrada de um usuário. Isso pode indicar que a conta do usuário está comprometida, que as mensagens estão sendo ocultadas intencionalmente e que a caixa de correio está sendo usada para distribuir spam ou malware em sua organização.
- **Suporte para grupos em políticas de permissão de aplicativo**<br>
O Cloud App Security agora fornece a capacidade de definir políticas de permissão do aplicativo de modo mais granular, com base nas associações a grupo de usuários que autorizaram os aplicativos. Por exemplo, um administrador poderá decidir definir uma política que revogue aplicativos incomuns se eles solicitarem permissões altas apenas se o usuário que autorizou as permissões for membro do grupo de administradores.
- **Controle de Aplicativos de Acesso Condicional agora integra-se aos seus aplicativos locais por meio do Proxy de Aplicativo do Azure Active Directory**
  - O [Proxy de Aplicativo do Azure AD](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy) fornece acesso remoto por logon único e seguro para seus aplicativos Web hospedados no local.
  - Esses aplicativos Web locais agora podem ser roteados para o Microsoft Cloud App Security por meio do acesso condicional do Azure AD para fornecer monitoramento e controles em tempo real por meio de políticas de [acesso](access-policy-aad.md) e [sessão](session-policy-aad.md).


## <a name="cloud-app-security-release-133-134-135"></a>Cloud App Security versão 133, 134, 135

Lançado em outubro de 2018

**Novas políticas de detecção de anomalias estão sendo gradualmente distribuídas**
- A nova política de Extração de dados para aplicativos não sancionados é habilitada automaticamente para alertá-lo quando um usuário ou endereço IP usa um aplicativo não aprovado para executar uma atividade que se parece com uma tentativa de remover informações de sua organização.
- A nova política de Atividades de exclusão múltipla de VM traça o perfil do seu ambiente e dispara alertas quando os usuários excluem várias VMs em uma única sessão em relação à linha de base em sua organização.

**Serviço de classificação de dados disponível para a Ásia-Pacífico**
- A inspeção de conteúdo do serviço de classificação de dados agora está disponível para clientes da Ásia-Pacífico. Para obter uma lista completa de suporte regional, veja [Integração de Serviços de Classificação de Dados da Microsoft](dcs-inspection.md).

**Suporte do Cloud Discovery para i-Filter**
-  O recurso Cloud App Security do Cloud Discovery agora tem suporte aprimorado para o analisador de syslog do i-Filter.

## <a name="cloud-app-security-release-132"></a>Cloud App Security versão 132

Lançado em 25 de setembro de 2018

- **Agora o Controle de Aplicativos de Acesso Condicional para o Office 365 está em versão prévia pública**
    - Agora o Controle de Aplicativos de Acesso Condicional também é compatível com o Office 365 e com qualquer aplicativo configurado com o Open ID Connect.
    - Fornecer comentários em uma sessão: Essa nova ferramenta permite que você forneça comentários à equipe do Cloud App Security sobre o desempenho de um aplicativo sob o controle da sessão, diretamente nela.


- **Integração nativa com o Microsoft Defender ATP para Shadow IT Discovery além da sua corporação**
    - Agora o Microsoft Cloud App Security integra-se nativamente ao Windows Defender ATP (Proteção Avançada contra Ameaças do Azure) para fornecer funcionalidades de descoberta do Shadow IT sem implantação para uso de aplicativos de nuvem dentro e fora da rede corporativa.  Isso permitirá que você execute o Cloud Discovery em computadores, mesmo quando eles não estiverem dentro da sua rede corporativa. Isso também permite a investigação baseada em computador: após identificar um usuário arriscado, será possível verificar todos os computadores que o usuário acessou para detectar potenciais riscos; se você identificar um computador arriscado, será possível verificar todos os usuários que o usaram para investigar potenciais riscos. Para saber mais, confira a integração da Proteção Avançada contra Ameaças do Azure do Windows Defender com o [Microsoft Cloud App Security](wdatp-integration.md).
- **Inspeção de conteúdo para arquivos criptografados**
    - Agora o Cloud App Security dá suporte à inspeção de conteúdo de arquivos protegidos criptografados que foram protegidos usando a Proteção de Informações do Azure. Agora é possível inspecionar esses arquivos criptografados para propostas de reclassificação e inspecionar uma exposição adicional de DLP e violações da política de segurança. 

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
Agora você pode enviar os comentários para a equipe do Cloud App Security informando se algum aplicativo OAuth que pareça mal-intencionado foi descoberto na sua organização. Esse novo recurso permite que você participe da nossa comunidade de segurança e melhore a análise e a pontuação de risco do aplicativo OAuth. Para obter mais informações, confira [Gerenciar aplicativo permiOAuth appsssions](manage-app-permissions.md).

- **Novos analisadores do Cloud Discovery**<br>
Os analisadores do Cloud Discovery agora oferecem suporte ao iboss Secure Cloud Gateway e Sophos XG.


## <a name="cloud-app-security-release-129"></a>Cloud App Security versão 129

Lançamento de 5 de agosto de 2018

- **Novas políticas de detecção de anomalias – regras de email suspeito**<br>Foram incluídas novas políticas de detecção de anomalias que detectam regras de encaminhamento de email suspeito, por exemplo, se um usuário criou uma regra de caixa de entrada que encaminha uma cópia de todos os emails para um endereço externo. 
- Esta versão inclui correções e melhorias para vários problemas. 

## <a name="cloud-app-security-release-128"></a>Cloud App Security versão 128

Lançado em 22 de julho de 2018

-   **Ações de aplicativos OAuth entre vários aplicativos**<br>
Para aplicativos OAuth que receberam permissões de aplicativo, você agora pode banir ou aprovar vários aplicativos em uma única ação. Por exemplo, é possível analisar todos os aplicativos que receberam permissões de usuários da sua organização, selecionar todos os aplicativos que você deseja vetar e, em seguida, clicar nos aplicativos vetados para revogar todas as permissões concedidas e impedir os usuários de conceder permissões a esses aplicativos.  Para obter mais informações, confira [Gerenciar aplicativos OAuth](manage-app-permissions.md).
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

-   **Nova consulta sugerida: Pronto para o RGPD** <br>
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
O Microsoft Cloud App Security já pode detectar buckets do S3 do AWS e os respectivos níveis de compartilhamento. Ele fornece alertas e visibilidade para os buckets do AWS acessíveis publicamente. O programa permite também criar políticas baseadas em buckets e aplicar governança automaticamente. Além disso, temos um novo modelo de política disponível chamado **Buckets do S3 acessíveis publicamente (AWS)** , com o qual você pode facilmente criar uma política para gerenciar o armazenamento do AWS. Para habilitar esses novos recursos, atualize os aplicativos conectados ao AWS adicionando as novas permissões descritas em [Conectar o AWS](connect-aws-to-microsoft-cloud-app-security.md).

- **Privilégios de administrador baseados em grupos de usuários**: Agora é possível definir permissões administrativas aos administradores do Microsoft Cloud App Security por grupo de usuários. Por exemplo, é possível definir um usuário específico como administrador apenas para os usuários da Alemanha. Isso permitiria ao usuário exibir e modificar as informações no Microsoft Cloud App Security, somente quando se relacionassem exclusivamente ao grupo de usuários "Alemanha – Todos os usuários". Saiba mais em [Gerenciar acesso de administrador](manage-admins.md).


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
 O servidor de email do Cloud App Security mudou e usa intervalos de endereço IP diferentes. Para certificar-se de que você pode obter notificações, adicione os novos endereços IP à lista de permissões antispam. Para usuários que personalizam suas notificações, o Microsoft Cloud App Security permite essa opção usando MailChimp®, um serviço de email de terceiros. Para obter a lista de endereços IP do servidor de email e instruções para habilitar o trabalho com o MailChimp, confira [Requisitos de rede](network-requirements.md#mail-server) e [Configurações de email](mail-settings.md).


## <a name="cloud-app-security-release-123"></a>Cloud App Security versão 123

Lançamento: 13 de maio de 2018

- **Escopo da política de detecção de anomalias**:<br>
As políticas de detecção de anomalias agora podem ser definidas. Isso permite que você defina cada política de detecção de anomalias para incluir apenas usuários ou grupos específicos e para excluir usuários ou grupos específicos. Por exemplo, você pode definir a Atividade de detecção de regiões pouco frequentes para ignorar um usuário específico que viaja com frequência. 


## <a name="cloud-app-security-release-122"></a>Cloud App Security versão 122
Lançado em 29 de abril de 2018

-   Distribuição gradual: Agora você pode **definir permissões administrativas aos administradores do Microsoft Cloud App Security por aplicativo**. Por exemplo, é possível definir um usuário específico como um administrador apenas para o G Suite. Isso permitiria que o usuário exibisse e modificasse as informações no Microsoft Cloud App Security, somente quando se relaciona exclusivamente ao G Suite. Saiba mais em [Gerenciar acesso de administrador](manage-admins.md).
- Distribuição gradual: **Agora as funções de administrador do Okta estão visíveis** no Microsoft Cloud App Security e disponíveis para cada função como uma marca em **Configurações** > **Grupos de usuários**.


## <a name="cloud-app-security-release-121"></a>Cloud App Security versão 121
Lançado em 22 de abril de 2018

-   A visualização pública do **Controle de Aplicativo de Acesso Condicional (anteriormente conhecido como Proxy do Cloud App Security)** foi aprimorada com recursos que possibilitam maior visibilidade e controle sobre vários aplicativos. Agora, você pode criar uma política de sessão com um filtro de *Tipo de atividade* para monitorar e bloquear diversas atividades específicas de aplicativos. Esse novo filtro amplia os recursos existentes de controle de download de arquivos para fornecer controle abrangente dos aplicativos em sua organização e funciona em conjunto com o acesso condicional do Azure Active Directory para fornecer visibilidade em tempo real e controle de sessões de usuário arriscadas; por exemplo, sessões com usuários de colaboração B2B ou provenientes de um dispositivo não gerenciado. Para saber mais, confira [Políticas de sessão](session-policy-aad.md).
-   Distribuição gradual: As **políticas de detecção de anomalias do Cloud App Security foram aprimoradas** para incluir dois novos tipos de detecção de ameaças: Atividade de ransomware e Atividade de usuário encerrado. O Cloud App Security estendeu seus recursos de detecção de ransomware com a detecção de anomalias para garantir uma cobertura mais ampla contra ataques de Ransomware sofisticados. Usando nossa experiência com pesquisa de segurança para identificar padrões de comportamentos que refletem a atividade de ransomware, o Cloud App Security garante a proteção holística e robusta. A atividade de usuários demitidos permite que você monitore as contas de usuários demitidos, que podem ter sido desprovisionadas de aplicativos corporativos, mas, em muitos casos, ainda mantêm o acesso a determinados recursos corporativos. Para saber mais, confira o artigo [Obter análise comportamental e detecção de anomalias instantaneamente](anomaly-detection-policy.md).


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

-   A integração profunda do Cloud App Security com a Proteção de Informações do Azure agora permite que você proteja os arquivos no G Suite. Esse recurso de visualização pública permite examinar e classificar arquivos no G Suite, e aplicar automaticamente os rótulos da Proteção de Informações do Azure para proteção. Para saber mais, confira [Integração com a Proteção de Informações do Azure](azip-integration.md).

-   Agora, o Cloud Discovery dá suporte a [Digital artes i-FILTER](https://www.daj.jp/en/products/if/).

-   A tabela de agentes do SIEM agora inclui mais detalhes para um gerenciamento mais fácil.

## <a name="cloud-app-security-release-116"></a>Cloud App Security versão 116
Lançado em 4 de fevereiro de 2018
- Aprimoramos a política de detecção de anomalias do Cloud App Security com novas **detecções baseadas em cenários**, como viagem impossível, atividade de endereço IP suspeito e várias tentativas de logon com falha. As novas políticas são habilitadas automaticamente, fornecendo a detecção de ameaças pronta para uso no ambiente de nuvem. Além disso, as novas políticas expõem mais dados do mecanismo de detecção do Cloud App Security para ajudar a acelerar o processo de investigação e conter as ameaças em andamento. Para saber mais, confira o artigo [Obter análise comportamental e detecção de anomalias instantaneamente](https://docs.microsoft.com/cloud-app-security/anomaly-detection-policy).

- Distribuição gradual: Agora o Cloud App Security correlaciona os usuários e suas contas em aplicativos SaaS. Isso permite investigar facilmente todas as atividades de um usuário, em todos os vários aplicativos SaaS correlacionados, independentemente de qual aplicativo ou conta usaram.  

-   Distribuição gradual: Agora o Cloud App Security dá suporte a várias instâncias do mesmo aplicativo conectado. Se você tiver várias instâncias do Salesforce (uma para venda, uma para marketing), por exemplo, poderá conectar os dois ao Cloud App Security e gerenciá-los no mesmo console para criar políticas granulares e uma investigação mais detalhada. 

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

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/)
---
title: "Versões e notas de versão do Cloud App Secuirty | Microsoft Docs"
description: "Este tópico é atualizado com frequência para você saber quais são as novidades na versão mais recente do Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/5/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: d418ef3d-76ee-45d5-b5ae-21346e5239a3
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 23870c7ba734acc3095f1dcd097f19954fee5e79
ms.sourcegitcommit: 064afc7148de42c0e81763f96ec13fb2c92f02a9
translationtype: HT
---
# <a name="release-notes"></a>Notas de versão


## <a name="cloud-app-security-release-90-91-92"></a>Cloud App Security versão 90, 91, 92
Lançado em fevereiro de 2017

**Comunicado especial**

Agora o Cloud App Security está oficialmente certificado com a Conformidade da Microsoft para ISO, HIPAA, CSA STAR, cláusulas de modelo da UE e muito mais. Veja a lista completa das certificações, acesse [Ofertas de conformidade da Microsoft](https://www.microsoft.com/trustcenter/compliance/complianceofferings) e selecione Cloud App Security.

**Novos recursos**

-  **Importar grupos de usuários (visualização)** Agora, quando você conecta aplicativos usando conectores de API, o Cloud App Security permite que você importe grupos de usuários do Office 365 e do Azure Active Directory. Os cenários típicos que tiram vantagem dos grupos de usuários importados incluem: investigar os documentos que as pessoas de RH observam, verificar se há algo incomum acontecendo no grupo de executivos ou se alguém do grupo administradores realizou uma atividade fora dos EUA. Para obter detalhes e instruções, consulte [Importar grupos de usuários](user-groups.md).

-  Agora, no Log de atividades, você pode filtrar os usuários e grupos de usuários para mostrar quais atividades foram realizadas por um usuário específico e quais foram realizadas em um usuário específico. Por exemplo, você pode investigar atividades em que o usuário representou outras pessoas e atividades em que outras pessoas representaram esse usuário. Para obter mais informações, consulte [Atividades](activity-filters.md).

- Agora, ao investigar um arquivo na página **Arquivos**, se você analisar os **Colaboradores** de um arquivo específico, você poderá ver mais informações sobre os colaboradores, incluindo se são ou não são Internos ou Externos, Gravadores ou Leitores (permissões de arquivo), e quando um arquivo for compartilhado com um grupo, você poderá ver todos os usuários que são membros do grupo. Isso permite verificar se os membros do grupo são usuários externos.

-  O suporte a IPv6 agora está disponível para todos os dispositivos.

-    O Cloud Discovery agora dá suporte a dispositivos Baracuda.

-    Os alertas do sistema do Cloud App Security agora cobrem erros de conectividade do SIEM. Para obter mais informações, consulte [Integração do SIEM](siem.md).

-    O Cloud App Security agora inclui suporte para as seguintes atividades:

     **O Office 365, SharePoint/OneDrive**: atualizar configuração de aplicativo, Remover proprietário do grupo, Excluir site, Criar pasta

     **Dropbox**: Adicionar membro ao grupo, Remover membro do grupo, Criar grupo, Renomear grupo, Alterar nome de membro da equipe

     **Box**: Remover item do grupo, Atualizar compartilhamento de item, Adicionar usuário ao grupo, Remover usuário do grupo


## <a name="cloud-app-security-release-89"></a>Cloud App Security versão 89
Lançado em 22 de janeiro de 2017

**Novos recursos**
-    Estamos começando a distribuir a capacidade de exibir os eventos de DLP do Centro de Conformidade e Segurança do Office 365 no Cloud App Security. Se você tiver configurado políticas DLP no Centro de Conformidade e Segurança do Office 365, quando forem detectadas correspondências de política, elas serão exibidas no log de atividades do Cloud App Security. As informações no log de atividades incluirão o arquivo ou email que disparou a correspondência e a política ou o alerta correspondente. A atividade "Evento de segurança" permite exibir as correspondências de políticas DLP do Office 365 no log de atividades do Cloud App Security. Usando esse recurso, você pode:
    -    Ver todas as correspondências de DLP provenientes do mecanismo de DLP do Office365.
    -    Alertar sobre as correspondências de políticas DLP do Office 365 para um arquivo, um site do SharePoint ou uma política específica.
    -    Investigar as correspondências de DLP em um contexto mais amplo, por exemplo, usuários externos que acessaram ou baixaram algum arquivo que disparou uma correspondência de política DLP.
 
-    As descrições das atividades foram melhoradas ficando mais consistentes e claras. Agora, cada atividade fornece um botão de comentários, portanto, se você não entender alguma ou tiver dúvidas, poderá nos informar. 
 
**Melhorias**  
-    Foi adicionada uma nova ação de governança para o Office 365 que permite remover todos os usuários externos de um arquivo. Por exemplo, isso permite implementar políticas que **removem compartilhamentos externos de arquivos com classificação somente interna**.
-    Melhoria na identificação de usuários externos no SharePoint Online. Ao filtrar usando o grupo "usuários externos", a conta do sistema app@sharepoint não será exibida.



## <a name="cloud-app-security-release-88"></a>Cloud App Security versão 88
Lançado em 8 de janeiro de 2017
 
**Novos recursos**
- Conecte o SIEM ao Cloud App Security. Agora você pode enviar alertas e atividades automaticamente ao SIEM da sua escolha configurando agentes do SIEM. Agora disponível como uma visualização pública.  Para obter a documentação e os detalhes completos, confira Integrando ao SIEM.
- Agora o Cloud Discovery dá suporte a IPv6. Já lançamos o suporte para Palo Alto e Juniper, e mais dispositivos serão lançados nas próximas versões.
 
**Melhorias**
- Há um novo fator de risco no catálogo de aplicativos de nuvem. Agora você pode classificar um aplicativo considerando se ele requer autenticação do usuário. Aplicativos que impõem autenticação e não permitem o uso anônimo receberão uma pontuação de risco mais íntegra.
- Estamos lançando novas descrições de atividades que são mais úteis e consistentes. A pesquisa de atividades não será afetada.
- Incluímos melhorias na identificação de dispositivo de usuário, permitindo que o Cloud App Security enriqueça um grande número de eventos com informações de dispositivo.
 
## <a name="cloud-app-security-release-87"></a>Cloud App Security versão 87
Liberada em 25 de dezembro de 2016

**Novos recursos**
-    Estamos em processo de lançamento da [anonimização de dados](cloud-discovery-anonymizer.md) para que você possa aproveitar o Cloud Discovery e ainda proteger a privacidade do usuário. A anonimização de dados é executada criptografando as informações de nome de usuário.
-    Estamos em processo de lançamento da capacidade de exportar um script de bloqueio do Cloud App Security para dispositivos adicionais. O script permitirá reduzir facilmente a TI sombra bloqueando o tráfego para aplicativos não sancionados. Essa opção está disponível agora para: 
    -    BlueCoat ProxySG
    -    Cisco ASA
    -    Fortinet
    -    Juniper SRX
    -    Palo Alto
    -    Websense
-    Uma nova ação de governança de Arquivo foi adicionada, a qual permite forçar um arquivo a Herdar permissões do pai, excluindo quaisquer permissões exclusivas configuradas para o arquivo ou pasta. Essa ação de governança de arquivo permite alterar o arquivo ou as permissões da pasta a serem herdadas da pasta pai. 
-    Um novo grupo de usuários chamado Externo foi adicionado. Trata-se de um grupo de usuários padrão pré-configurado pelo Cloud App Security para incluir todos os usuários que não fazem parte dos seus domínios internos. Você pode usar esse grupo de usuários como um filtro, por exemplo, para localizar atividades executadas por usuários externos.
-    O recurso Cloud Discovery agora dá suporte a dispositivos Sophos Cyberoam.
 
**Correções de bugs**
-    Os arquivos SharePoint online e One Drive for Business foram exibidos no relatório de política de Arquivo e na página Arquivos como Internos em vez de Particulares. Isso foi corrigido.
 


## <a name="cloud-app-security-release-86"></a>Cloud App Security versão 86
Liberada em 13 de dezembro de 2016

**Novos recursos**
- Todas as licenças autônomas do Cloud App Security fornecem a capacidade de habilitar a verificação da Proteção de Informações do Azure nas configurações gerais (sem a necessidade de criação de uma política). 
 
**Melhorias**
- Você pode agora usar “or” no filtro de arquivo para o nome do arquivo e no filtro de tipo MIME para arquivos e políticas. Isso permite cenários como inserir a palavra “passaporte” OR “driver” ao criar uma política com PII e ele fará a correspondência com arquivo que tenha “passaporte” ou “driver” no nome do arquivo. 
- Por padrão, quando uma política DPL de inspeção de conteúdo é executada, os dados nas violações resultantes são mascarados. Agora você poderá cancelar a máscara dos últimos quatro caracteres da violação. 

**Pequenos aperfeiçoamentos**
- Novos eventos relacionados à caixa de correio do Office 365 (Exchange) com relação às regras de encaminhamento, bem como adição e remoção de permissões de caixa de correio delegada.
- Novo evento que audita a concessão de autorização para novos aplicativos no Azure Active Directory. 




## <a name="cloud-app-security-release-85"></a>Cloud App Security versão 85
Lançado em 27 de novembro de 2016

**Novos recursos**
- Foi feita uma distinção entre aplicativos sancionados e aplicativos conectados. Sancionar e não sancionar agora é uma marca que pode ser aplicada a aplicativos descobertos e a qualquer aplicativo no catálogo de aplicativos. Aplicativos conectados são aqueles que você conectou usando o conector de API para aumentar a visibilidade e o controle. Agora você pode marcar aplicativos como sancionados ou não sancionados, ou conectá-los usando o conector de aplicativos, quando estiver disponível. 
 
- Como parte dessa alteração, a página Aplicativos sancionados foi substituída por uma página reformulada chamada **Aplicativos conectados** que exibe dados de status sobre os conectores. 
 
- Os coletores de log são acessados com mais facilidade em suas próprias linhas no menu **Configurações** em **Fontes**. 
- Ao criar um filtro de política de atividades, você pode reduzir os falsos positivos optando por ignorar atividades repetidas quando elas forem executadas no mesmo objeto de destino pelo mesmo usuário, por exemplo, se houver várias tentativas de baixar o mesmo arquivo pela mesma pessoa não será disparado um alerta. 
- Foram feitas melhorias na gaveta de atividades. Agora, ao clicar em um objeto de atividade na gaveta de atividades, você pode fazer uma busca detalhada para obter mais informações.

**Melhorias**
- Foram feitas melhorias no mecanismo de detecção de anomalias, incluindo os alertas de viagem impossível, para os quais as informações de IP agora estão disponíveis na descrição do alerta.
- Foram feitas melhorias nos filtros complexos para habilitar a adição do mesmo filtro mais de uma vez para ajustar os resultados filtrados. 
- As atividades de arquivos e pastas no Dropbox foram separadas para melhorar a visibilidade. 
  
**Correções de bugs**
- Foi corrigido um bug no mecanismo de alertas do sistema que criava falsos positivos.

## <a name="cloud-app-security-release-84"></a>Cloud App Security versão 84
Lançada em 13 de novembro de 2016

**Novos recursos**
-    O Cloud App Security agora dá suporte à Proteção de Informações do Microsoft Azure incluindo a integração aprimorada e provisionamento automático. Você pode filtrar os Arquivos e definir políticas de arquivo usando a Classificação de marca segura e definir o rótulo de classificação que deseja exibir. Os rótulos também indicam se a classificação foi definida por alguém na sua organização ou por pessoas de outro locatário (Externo). Você também pode definir políticas de atividade com base nos rótulos de classificação da Proteção de Informações do Azure e habilitar a verificação automática para rótulos de classificação no Office 365. Para obter mais informações sobre como aproveitar esse novo recurso, consulte [Integração com o Proteção de Informações do Azure](azip-integration.md).
 
**Melhorias**
-    Foram feitas melhorias para o log de atividades do Cloud App Security: 
   -    Eventos do Office 365 do Centro de conformidade e segurança agora estão integrados com o Cloud App Security e são visíveis no **Log de atividade**.
   -    Todas as atividades do Cloud App Security são registradas no log de atividades do Cloud App Security como atividades administrativas.
-    Para ajudá-lo a investigar os alertas relacionados a arquivos, em cada alerta que resultar de uma política de arquivo, agora você pode exibir a lista de atividades que foram executadas no arquivo correspondente.
-    O algoritmo de viagem impossível no mecanismo de detecção de anomalias foi aprimorado para fornecer um melhor suporte para locatários pequenos. 
 
**Pequenos aperfeiçoamentos**
-    O **Limite de exportação de atividade** foi ampliado para 10.000. 
-    Ao criar um **relatório de instantâneo** no processo de upload do log manual do Cloud Discovery, você agora recebe uma estimativa precisa de quanto tempo levará o processamento do log. 
-    Em uma política de arquivo, a ação de governança **Remover colaborador** agora funciona em grupos.
-    Pequenos aperfeiçoamentos foram feitos na página **Permissões de aplicativo**. 
-    Quando mais de 10.000 usuários tiverem permissões para um aplicativo que se conecta ao Office 365, a lista é carregada lentamente. Isso foi corrigido.
-    Atributos adicionais foram adicionados ao **Catálogo de aplicativos** sobre a indústria de cartões de pagamento.


## <a name="cloud-app-security-release-83"></a>Cloud App Security versão 83
Lançado em 30 de outubro de 2016

**Novos recursos**
-    Para simplificar a filtragem no [log de atividades](activity-filters.md) e [arquivo de log](file-filters.md), filtros semelhantes foram consolidados. Use os filtros de atividade: objeto Atividade, Endereço IP e Usuário. Use o filtro de arquivo Colaboradores para localizar exatamente o que você precisa.
-    Na gaveta do log de atividades, em **Origem**, você pode clicar no link de **Exibir dados brutos** para baixar os dados brutos usados para gerar o log de atividades, de modo a analisar mais detalhadamente os eventos de aplicativo. 
-    Adição de suporte para atividades extras de logon no Okta. [Visualização privada]
-    Adição de suporte para atividades extras de logon no Salesforce. 

**Melhorias**
-    Melhor utilização de relatórios de instantâneo e solução de problemas do Cloud Discovery.
-    Maior visibilidade da lista de alertas em vários aplicativos.
-    Melhor utilização na criação de novos relatórios contínuos do Cloud Discovery.
-    Melhor utilização do log Governança.



## <a name="cloud-app-security-release-82"></a>Cloud App Security versão 82
Lançado em 9 de outubro de 2016

**Melhorias**

- As atividades **Alterar email** e **Alterar senha** agora são independentes da atividade genérica **Gerenciar usuários** no Salesforce.
- Foi adicionado um esclarecimento sobre o limite de alerta por SMS diário. Um máximo de 10 mensagens são enviadas por telefone por dia (UTC).
- Foi adicionado um novo certificado para os atributos do Cloud Discovery para a Defesa de Privacidade que substituiu o Safe Harbor (relevante apena para fornecedores dos EUA).
- A solução de problemas foi adicionada às mensagens de falha do conector de API para facilitar a correção de problemas.
- Melhoria na frequência de atualização da verificação de aplicativos de terceiros do Office 365.
- Melhorias no painel do Cloud Discovery.
- O analisador de Syslog de Ponto de Verificação foi aprimorado.
- Melhorias no Log de Governança para veto e cancelamento de veto de aplicativos de terceiros.
 
**Correções de bugs**
 
- Melhoria no processo de upload de logotipo.
 
## <a name="cloud-app-security-release-81"></a>Cloud App Security versão 81
Lançado em 18 de setembro de 2016

**Melhorias**
- O Cloud App Security agora é um aplicativo primário no Office 365! De agora em diante, você pode conectar o Office 365 ao Cloud App Security com um único clique.

- Nova aparência para o Log de governança – Agora ele foi atualizado para o mesmo visual nítido e prático que o Log de atividades e a Tabela de arquivos. Use os novos filtros para localizar facilmente o que você precisa e monitorar suas ações de governança. 
- Melhorias implementadas no mecanismo de detecção de anomalias para vários logons com falha e fatores de risco adicionais.
- Melhorias implementadas nos relatórios de instantâneo do Cloud Discovery.
- Melhorias implementadas nas atividades administrativas no log de atividades; Alterar a senha, Atualizar usuário e Redefinir senha agora indicam se a atividade foi executada como uma atividade administrativa.
- Os filtros de alerta para os alertas do sistema foram aprimorados. 
- O rótulo de uma política em um alerta agora é vinculado ao relatório de política.
- Se não houver nenhum proprietário especificado para um arquivo do Dropbox, as mensagens de email de notificação serão enviadas para o destinatário definido. 
- O Cloud App Security dá suporte a 24 idiomas adicionais, ampliando nosso suporte para um total de 41 idiomas.  


## <a name="cloud-app-security-release-80"></a>Cloud App Security versão 80
Lançado em 4 de setembro de 2016 

**Melhorias**
- Quando a verificação DLP falhar, agora você receberá uma explicação de por que o Cloud App Security não pôde verificar o arquivo. Para obter mais informações, consulte [Inspeção de Conteúdo](https://aka.ms/aka.ms/cas-contentinspection).
- Melhorias implementadas nos mecanismos de detecção de anomalias, incluindo melhorias nos alertas de viagem impossível.
- Melhorias implementadas na experiência de dispensar alerta, agora você também pode adicionar comentários para informar a equipe do Cloud App Security se o alerta foi interessante e por quê, para que seus comentários possam ser usados para aprimorar as detecções do Cloud App Security.
- Os analisadores do Cloud Discovery do Cisco ASA foram aprimorados.
- Agora você recebe uma notificação por email quando o upload manual do log do Cloud Discovery é descoberto.
   



## <a name="cloud-app-security-release-79"></a>Cloud App Security versão 79
Lançado em 21 de agosto de 2016 

**Novos recursos**

- **Novo Painel do Cloud Discovery**  
Um novo painel do Cloud Discovery está disponível, projetado para fornecer mais informações sobre como os aplicativos de nuvem estão sendo usados na sua organização. Ele fornece uma visão geral rápida de quais tipos de aplicativos estão sendo usados, os alertas abertos e os níveis de risco dos aplicativos na sua organização. Ele também informa quem são os principais usuários de aplicativo na sua organização e fornece um mapa de localização da Matriz de Aplicativo.
O novo Painel tem mais opções para filtrar os dados, para que você possa gerar exibições específicas dependendo do que mais lhe interessa e gráficos de fácil compreensão para fornecer um panorama completo rápido.

- **Novos relatórios do Cloud Discovery** Para exibir os resultados do Cloud Discovery, agora você pode gerar dois tipos de relatórios, Relatórios de Instantâneo e Contínuos.
Relatórios de instantâneo fornecem visibilidade ad hoc em um conjunto de logs de tráfego que são carregados manualmente dos seus firewalls e proxies. Relatórios contínuos mostram os resultados de todos os logs que são encaminhados da sua rede usando os coletores de logs do Cloud App Security. Esses novos relatórios fornecem maior visibilidade em todos os dados, identificação automática de uso anormal conforme identificado pelo mecanismo de detecção de anomalias do aprendizado de máquina do Cloud App Security e identificação de uso anormal definido por você usando o robusto e granular mecanismo de políticas. Para obter mais informações, consulte [Configurar o Cloud Discovery](set-up-cloud-discovery.md).
 
**Melhorias**
- Aperfeiçoamentos de usabilidade geral nas páginas a seguir: Páginas de políticas, Configurações gerais, Configurações de email.
- Na tabela Alertas, é mais fácil distinguir entre alertas lidou e não lidos. Os alertas lidos têm uma linha azul à esquerda e estão esmaecidos para indicar que já foram.
- Os parâmetros da política de Atividade **Atividade repetida** foram atualizados. 
- Na página Contas, uma coluna de **Tipo** de usuário foi adicionada, agora você pode ver o tipo de conta de cada usuário. Os tipos de usuário são específicos de aplicativo. 
- Suporte quase em tempo real adicionado para as atividades relacionadas a arquivos no OneDrive e no SharePoint. Quando um arquivo é alterado, o Cloud App Security dispara uma verificação quase imediatamente.


## <a name="cloud-app-security-release-78"></a>Cloud App Security versão 78
Lançado em 7 de agosto de 2016

**Melhorias**
- Em um arquivo específico, agora você pode clicar com o botão direito do mouse e **Localizar relacionados**. No Log de atividades, você pode usar o filtro do objeto de Destino e selecionar o arquivo específico.

- Analisadores de arquivo de log do Cloud Discovery melhorados, incluindo a adição do Juniper e Cisco ASA.
- O Cloud App Security agora permite que você forneça comentários para a melhoria de alertas ao ignorá-los. Você pode ajudar a melhorar a qualidade do recurso de alertas do Cloud App Security contando para nós por que você está ignorando o alerta, por exemplo, por ele não se interessante, você recebeu muitos alertas semelhantes, a severidade real deveria ser menor ou o alerta não é preciso.
-Foi adicionado o novo link para Políticas correspondentes na exibição de Política de arquivo ou ao exibir um arquivo. Ao clicar nele, você pode exibir todas as correspondências e agora é possível ignorar todas. 
- A unidade organizacional à qual um usuário pertence agora é adicionada para todos os alertas relevantes.
- Agora uma notificação por email é enviada para informar quando o processamento de logs manualmente carregados for concluído.


## <a name="cloud-app-security-release-77"></a>Cloud App Security versão 77
Lançado em 24 de julho de 2016

**Melhorias:**
- O ícone do botão Exportar do Cloud Discovery foi aprimorado para facilitar o uso.
- Ao investigar uma atividade, se o agente do usuário não foi analisado, agora você poderá ver os dados brutos.
- Dois novos fatores de risco foram adicionados ao mecanismo de Detecção de Anomalias: 
    - O Cloud App Security agora usa as marcas de endereço IP associadas um botnet e endereços IP anônimos como parte do cálculo de risco. 
    - Atividade do Office 365 agora é monitorada para altas taxas de download. Se a taxa de download do Office 365 for muito maior do que a da sua organização ou do que a taxa de download normal de um usuário específico, um alerta de detecção de anomalias será disparado. 
- O Cloud App Security agora é compatível com a nova API da [funcionalidade de Compartilhamento Seguro](https://blogs.dropbox.com/dropbox/2016/06/new-dropbox-productivity-tools/) do Dropbox. 
- Melhorias implementadas para adicionar detalhes aos erros de análise do Log de descoberta, incluindo: Nenhuma nuvem transação de nuvem relacionada, Todos os eventos estão desatualizados, Arquivo corrompido, Formato de log não correspondente.
- O filtro de dados do Log de atividades foi aprimorado, agora ele inclui a capacidade de filtrar por tempo.
- A página de intervalos de endereço IP foi aprimorada para facilitar o uso.
- O Cloud App Security agora inclui suporte para a Proteção de Informações do Microsoft Azure (versão prévia). Você pode filtrar os Arquivos e definir Políticas de arquivo usando a Classificação de Marca Segura e definir o nível do rótulo de classificação que você deseja exibir. Os rótulos também indicarão se a classificação foi definida por alguém na sua organização ou por pessoas de outro locatário (Externo). 



## <a name="cloud-app-security-release-76"></a>Cloud App Security versão 76
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


## <a name="cloud-app-security-release-75"></a>Cloud App Security versão 75
Lançado em 27 de junho de 2016


**Novos recursos:**
* Novas adições à crescente lista de eventos do Salesforce com suporte, incluindo eventos que fornecem informações sobre relatórios, links compartilhados, distribuição de conteúdo, logon representado e muito mais.
* Os ícones de aplicativo conectado no painel do Cloud App Security foram alinhados com o status dos aplicativos conforme exibido no painel para refletir os últimos 30 dias.
* Suporte para telas de largura inteira.


**Correções de bugs:**
* Os números de telefone de alerta por SMS agora são validados mediante inserção.

## <a name="cloud-app-security-release-74"></a>Cloud App Security versão 74
Lançamento: 13 de junho de 2016
* A tela Alerta foi atualizada para fornecer mais informações rapidamente, incluindo a capacidade de ver todas as atividades do usuário rapidamente, um mapa de atividades, logs de governança do usuário relacionado, uma descrição do motivo de o alerta ser disparado e gráficos e mapas adicionais da página do usuário. 
* Eventos gerados pelo Cloud App Security agora incluem o tipo de evento, formato, grupos de políticas, objetos relacionados e uma descrição.
* Foram adicionadas novas marcas de endereço IP para o Office 365 ProPlus, OneNote, Office Online e Proteção do Exchange Online.
* Agora você tem a opção de carregar logs do menu de descoberta principal.
* O filtro de categoria de endereço IP foi aprimorado. A categoria de endereço IP nula agora é chamada de não categorizada e uma nova categoria chamada Sem valor foi adicionada para incluir todas as atividades que não têm dados de endereço IP.
* Os grupos de segurança no Cloud App Security agora são chamados de grupos de usuários para evitar confusão com grupos de segurança do Active Directory.
* Agora é possível filtrar por endereço IP e filtrar eventos sem um endereço IP. 
* Foram feitas alterações para as configurações de emails de notificação enviados quando correspondências são detectadas em políticas de atividade e políticas de arquivos. Agora você pode adicionar endereços de email para destinatários que deseja colocar em CC na notificação.


## <a name="cloud-app-security-release-73"></a>Cloud App Security versão 73
Lançamento: 29 de maio de 2016

* Recursos de alerta atualizados: agora, você pode definir alertas por política para serem enviados por email ou como mensagem de texto.
* Página de alertas: design aprimorado para permitir melhor gerenciamento de incidentes e opções avançadas de resolução.
* Ajustar a política: os alertas agora permitem que você mova das opções de resolução de alerta diretamente para a página de configurações de política para habilitar um ajuste fino mais fácil baseado em alertas.
* Melhorias no cálculo de pontuação de risco de detecção de anomalias e taxas de falso-positivos reduzidas com base nos comentários dos clientes.
* A exportação do log de atividade agora inclui a ID de Evento, a Categoria de Evento e o Nome do tipo de Evento.
* Aparência aprimorada e usabilidade de criação das Ações de Governança de criação de política.
* Investigação simplificada e controle para o Office 365 - A seleção do Office 365 escolhe automaticamente todos os aplicativos que fazem parte do Pacote do Office 365.
* Agora as notificações são enviadas para o endereço de email, conforme configurado no aplicativo conectado. 
* Em caso de erro de conexão, uma descrição detalhada do erro agora é fornecida pelo aplicativo de nuvem.
* Quando um arquivo corresponde a uma política, uma URL para acessar o arquivo agora é fornecida na gaveta do arquivo.
* Quando um alerta for disparado por uma política de atividade ou por uma política de detecção de anomalias, uma nova notificação detalhada que fornece informações sobre a correspondência é enviada. 
* Um alerta de sistema automatizado é disparado quando um conector de aplicativo é desconectado.
* Agora, você pode ignorar e resolver um único alerta ou uma seleção em massa de alertas da página de alertas.

## <a name="cloud-app-security-release-72"></a>Cloud App Security versão 72
Lançamento: 15 de maio de 2016

*  Melhorias na aparência e infraestrutura gerais, incluindo:
    * Novo diagrama para fornecer mais assistência com o processo para carregar logs manualmente do Cloud Discovery.
    * Processo melhorado para atualizar arquivos de log não reconhecidos ("Outros"), incluindo um pop-up que avisa que o arquivo requer revisão adicional e que você será notificado quando os dados estiverem disponíveis.
    * Mais atividades e violações de arquivo são realçadas ao investigar uma atividade e o arquivo de log para sistemas operacionais e navegadores desatualizados.
* Analisadores de arquivo de log do Cloud Discovery melhorados, incluindo a adição do Cisco ASA, Cisco FWSM, Cisco Meraki e W3C.
* Melhorias dos problemas conhecidos do Cloud Discovery.
* Novos filtros de atividade adicionados para o domínio do proprietário e afiliação interna/externa.
* Um novo filtro foi adicionado, que permite que você pesquise qualquer objeto do Office 365 (arquivos, pastas, URLs).
* A capacidade foi adicionada ao configurar uma pontuação de risco mínimo para as políticas de detecção de anomalias.
* Ao definir que um alerta será enviado quando uma política for violada, você poderá definir um nível de gravidade mínimo naquela sobre a qual você deseja ser alertado. Você pode optar por usar as configurações padrão da sua organização para isso e também pode definir uma configuração de alerta específica como o padrão para sua organização.

## <a name="see-also"></a>Veja também  
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
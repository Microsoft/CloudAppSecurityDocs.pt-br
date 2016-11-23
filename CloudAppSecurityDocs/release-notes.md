---
title: "Notas de versão | Microsoft Docs"
description: "Este tópico é atualizado com frequência para você saber quais são as novidades na versão mais recente do Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/13/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: d418ef3d-76ee-45d5-b5ae-21346e5239a3
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 759692e7b270d87dc1becf88453d095f2382c411
ms.openlocfilehash: 3161fd1c61779ba943d8269d2ec979050ee0ae1f


---

# <a name="release-notes"></a>Notas de versão


## <a name="cloud-app-security-release-84"></a>Cloud App Security versão 84
Lançada em 13 de novembro de 2016

**Novos recursos**
-   O Cloud App Security agora dá suporte à Proteção de Informações do Microsoft Azure incluindo a integração aprimorada e provisionamento automático. Você pode filtrar os Arquivos e definir políticas de arquivo usando a Classificação de marca segura e definir o rótulo de classificação que deseja exibir. Os rótulos também indicam se a classificação foi definida por alguém na sua organização ou por pessoas de outro locatário (Externo). Você também pode definir políticas de atividade com base nos rótulos de classificação da Proteção de Informações do Azure e habilitar a verificação automática para rótulos de classificação no Office 365. Para obter mais informações sobre como aproveitar esse novo recurso, consulte [Integração com o Proteção de Informações do Azure](azip-integration.md).
 
**Melhorias**
-   Foram feitas melhorias para o log de atividades do Cloud App Security: 
   -    Eventos do Office 365 do Centro de conformidade e segurança agora estão integrados com o Cloud App Security e são visíveis no **Log de atividade**.
   -    Todas as atividades do Cloud App Security são registradas no log de atividades do Cloud App Security como atividades administrativas.
-   Para ajudá-lo a investigar os alertas relacionados a arquivos, em cada alerta que resultar de uma política de arquivo, agora você pode exibir a lista de atividades que foram executadas no arquivo correspondente.
-   O algoritmo de viagem impossível no mecanismo de detecção de anomalias foi aprimorado para fornecer um melhor suporte para locatários pequenos. 
 
**Pequenos aperfeiçoamentos**
-   O **Limite de exportação de atividade** foi ampliado para 10.000. 
-   Ao criar um **relatório de instantâneo** no processo de upload do log manual do Cloud Discovery, você agora recebe uma estimativa precisa de quanto tempo levará o processamento do log. 
-   Em uma política de arquivo, a ação de governança **Remover colaborador** agora funciona em grupos.
-   Pequenos aperfeiçoamentos foram feitos na página **Permissões de aplicativo**. 
-   Quando mais de 10.000 usuários tiverem permissões para um aplicativo que se conecta ao Office 365, a lista é carregada lentamente. Isso foi corrigido.
-   Atributos adicionais foram adicionados ao **Catálogo de aplicativos** sobre a indústria de cartões de pagamento.


## <a name="cloud-app-security-release-83"></a>Cloud App Security versão 83
Lançado em 30 de outubro de 2016

**Novos recursos**
-   Para simplificar a filtragem no [log de atividades](activity-filters.md) e [arquivo de log](file-filters.md), filtros semelhantes foram consolidados. Use os filtros de atividade: objeto Atividade, Endereço IP e Usuário. Use o filtro de arquivo Colaboradores para localizar exatamente o que você precisa.
-   Na gaveta do log de atividades, em **Origem**, você pode clicar no link de **Exibir dados brutos** para baixar os dados brutos usados para gerar o log de atividades, de modo a analisar mais detalhadamente os eventos de aplicativo. 
-   Adição de suporte para atividades extras de logon no Okta. [Visualização privada]
-   Adição de suporte para atividades extras de logon no Salesforce. 

**Melhorias**
-   Melhor utilização de relatórios de instantâneo e solução de problemas do Cloud Discovery.
-   Maior visibilidade da lista de alertas em vários aplicativos.
-   Melhor utilização na criação de novos relatórios contínuos do Cloud Discovery.
-   Melhor utilização do log Governança.



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
  
  


<!--HONumber=Nov16_HO3-->



---
title: Conectar o Salesforce ao Cloud App Security
description: Este artigo fornece informações sobre como conectar o Salesforce ao Cloud App Security usando o conector de API para obter visibilidade e controle sobre o uso.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/10/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 776d7589-acdb-4cb6-99a0-3be2f7b6aab2
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 322e5d0564e70ff4e8ff85bdd3f798f43aacf235
ms.sourcegitcommit: b86c3afd1093fbc825fec5ba4103e3a95f65758e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53176732"
---
# <a name="connect-salesforce-to-microsoft-cloud-app-security"></a>Conectar o Salesforce ao Microsoft Cloud App Security

*Aplica-se a: Microsoft Cloud App Security*

Este artigo fornece instruções para conectar o Microsoft Cloud App Security à sua conta existente do Salesforce usando a API do conector de aplicativos. Essa conexão fornece visibilidade e controle sobre o uso do Salesforce. 
  
## <a name="how-to-connect-salesforce-to-cloud-app-security"></a>Como conectar o Salesforce ao Cloud App Security  
  
1.  É recomendável ter uma conta do administrador de serviço dedicada para o Cloud App Security.  
  
2.  Confirme se a API REST está habilitada no Salesforce.  
  
     Sua conta do Salesforce deve ser de uma das seguintes edições que incluem o suporte à API REST:  
  
     **Performance**, **Enterprise**, **Unlimited** ou **Developer**.  
  
     A edição **Professional** não tem a API REST por padrão, mas pode ser adicionada sob demanda.  
  
     Verifique se sua edição tem a API REST disponível e habilitada da seguinte maneira:  
  
    -   Entre em sua conta do Salesforce e acesse a página **Configuração**.  
  
    -   Em **Gerenciar Usuários**, vá para a página **Perfis de Usuário**.  
  
         ![gerenciar perfis de usuário do salesforce](./media/salesforce-manageusers-profiles.png "gerenciar perfis de usuário do salesforce")  
  
    -   Crie um novo perfil clicando em **Novo**. 
    - Escolha o perfil que você acabou de criar para implantar o Cloud App Security e clique em **Editar**.  este é o perfil a ser usado para a conta de serviço do Cloud App Security para configurar o Conector de aplicativo.  
  
         ![editar perfil do salesforce](./media/salesforce-edit-profile.png "editar perfil do salesforce")  
  
    -   Certifique-se de ter as seguintes caixas de seleção habilitadas:   
        - **API Habilitada**
        - **Exibir todos os dados** 
        - **Gerenciar Conteúdo CRM do Salesforce**
        - **Gerenciar usuários**
        
        Se essas caixas de seleção não estiverem selecionadas, poderá ser necessário contatar a Salesforce para adicioná-las à sua conta.  
             
3.  Se sua organização tiver **Salesforce CRM Content** habilitado, certifique-se de que a conta administrativa atual o tenha habilitado também.  
  
    1.  Vá para a página de configuração do Salesforce.  
  
         ![instalação do salesforce](./media/salesforce-setup.png "instalação do salesforce")  
  
    2.  No menu lateral, selecione **Gerenciar Usuários** e clique em **Usuários**.  
  
         ![usuários do menu do salesforce](./media/salesforce-menu-users.png "usuários do menu do salesforce")  
  
    3.  Selecione o usuário administrativo atual para seu usuário do Cloud App Security dedicado.  
  
    4.  Certifique-se de que a caixa de seleção **Usuário do Salesforce CRM Content** esteja marcada.  
  
         Se ela não estiver selecionada, clique em **Editar** e, em seguida, marque a caixa de seleção.  
  
         ![usuário do conteúdo crm do salesforce](./media/salesforce-crm-content-user.png "usuário do conteúdo crm do salesforce")  
  
    5.  Clique em **Salvar**.  
  
4.  No console do Cloud App Security, clique em **Investigar** e em **Aplicativos conectados**.  
  
5.  Na página **Conectores de aplicativos**, clique no botão de mais antes de **Salesforce**.  
  
     ![conectar salesforce](./media/connect-salesforce.png "conectar salesforce")  
  
6.  Na página de configurações do Salesforce, na guia API, clique em **Seguir este link**, dependendo de qual instância que você deseja instalar.  
  
7.  Isso abre a página de entrada do Salesforce. Insira suas credenciais para permitir que o Cloud App Security acesse o aplicativo do Salesforce da sua equipe.  
  
     ![entrada do salesforce](./media/salesforce-logon.png "logon do salesforce")  
  
8.  O Salesforce perguntará se você deseja permitir que o Cloud App Security acesse o log de atividades e as informações da sua equipe e realize quaisquer atividades como qualquer membro da equipe. Para continuar, clique em **Permitir**.  
  
9. Neste ponto, você receberá uma notificação de êxito ou de falha em relação à implantação. O Cloud App Security agora está autorizado no Salesforce.com.  
  
10. De volta ao console do Cloud App Security, você deverá ver a mensagem indicando que o Salesforce foi conectado com êxito.  
  
11. Certifique-se de que a conexão foi bem-sucedida clicando em **Testar API**.  
  
     O teste pode levar alguns minutos. Depois de receber uma notificação de êxito, clique em **Concluído**.  
  
  
Depois de conectar o Salesforce, você receberá Eventos da seguinte maneira: Gatilhos disparados no momento da conexão, Eventos de logon e Trilha de Auditoria de Configuração por 60 dias antes da conexão, EventMonitoring por 30 dias ou um dia antes, dependendo da licença de EventMonitoring do Salesforce. A API do Cloud App Security se comunica diretamente com as APIs disponíveis no Salesforce. Como o Salesforce limita o número de chamadas à API que ele pode receber, o Cloud App Security leva isso em consideração e respeita a limitação. As APIs do Salesforce enviam cada resposta com um campo para os contadores de API, incluindo total disponível e restante. O Cloud App Security calcula isso em um percentual e garante que sempre haja 10% de chamadas à API disponíveis restantes. 

> [!NOTE]
> A limitação do Cloud App Security é calculada apenas em suas próprias chamadas à API com o Salesforce, não com os outros aplicativos que fazem chamadas à API com o Salesforce.
> Limitar as chamadas à API devido à limitação poderá diminuir a taxa em que os dados são incluídos no Cloud App Security, mas normalmente voltará ao normal durante a noite.


Eventos do Salesforce são processados pelo Cloud App Security da seguinte maneira: 
  
- Eventos de entrada a cada 15 minutos
- Trilhas de auditoria de instalação a cada 15 minutos
- Os logs do Salesforce rastreiam a atividade de uso por um período de 24 horas, de 0:00 a 23:59, UTC. Os eventos no Salesforce geram dados de log em tempo real. No entanto, os arquivos de log são gerados pelo Salesforce no dia após um evento ocorrer, fora do horário de pico. Portanto, os dados do arquivo de log ficam indisponíveis por pelo menos um dia após um evento. Para saber mais sobre os eventos do Salesforce, veja [Usando o monitoramento de eventos](https://developer.salesforce.com/docs/atlas.en-us.api_rest.meta/api_rest/using_resources_event_log_files.htm).


## <a name="next-steps"></a>Próximas etapas  
[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)   

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
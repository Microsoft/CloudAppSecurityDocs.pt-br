---
title: Conectar o Salesforce ao Cloud App Security para obter visibilidade e controle de uso | Microsoft Docs
description: Este tópico fornece informações sobre como conectar seu aplicativo Salesforce ao Cloud App Security usando o conector de API.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/22/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 776d7589-acdb-4cb6-99a0-3be2f7b6aab2
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 52b24a6aa80ee3283a5f2f6b96a3b1b51ce07d8b
ms.sourcegitcommit: 0ac08ca7b3140b79f1d36ff7152476c188fa12b3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44143931"
---
*Aplica-se ao: Microsoft Cloud App Security*

# <a name="connect-salesforce-to-microsoft-cloud-app-security"></a>Conectar o Salesforce ao Microsoft Cloud App Security
Esta seção fornece instruções para conectar o Microsoft Cloud App Security à sua conta do Salesforce existente usando a API do conector de aplicativos.  
  
## <a name="how-to-connect-salesforce-to-cloud-app-security"></a>Como conectar o Salesforce ao Cloud App Security  
  
1.  É recomendável ter uma conta de administrador de serviço dedicada para o Cloud App Security.  
  
2.  Confirme se a API REST está habilitada no Salesforce.  
  
     Sua conta do Salesforce deve ser de uma das seguintes edições que incluem o suporte à API REST:  
  
     **Performance**, **Enterprise**, **Unlimited** ou **Developer**.  
  
     A edição **Professional** não tem a API REST por padrão, mas pode ser adicionada sob demanda.  
  
     Verifique se sua edição tem a API REST disponível e habilitada da seguinte maneira:  
  
    -   Faça logon em sua conta do Salesforce e vá para a página **Configuração**.  
  
    -   Em **Gerenciar Usuários**, vá para a página **Perfis de Usuário**.  
  
         ![gerenciar perfis de usuário do salesforce](./media/salesforce-manageusers-profiles.png "gerenciar perfis de usuário do salesforce")  
  
    -   Crie um novo perfil clicando em **Novo**. 
    - Escolha o perfil que você acabou de criar para implantar o Cloud App Security e clique em **Editar**. Este é o perfil a ser usado para a conta de serviço do Cloud App Security para configurar o Conector de aplicativo.  
  
         ![editar perfil do salesforce](./media/salesforce-edit-profile.png "editar perfil do salesforce")  
  
    -   Certifique-se de ter as seguintes caixas de seleção habilitadas:   
        - **API Habilitada**
        - **Exibir todos os dados** 
        - **Gerenciar Conteúdo CRM do Salesforce**
        - **Gerenciar usuários**
        
        Se eles não estiverem selecionados, talvez seja necessário contatar o Salesforce para adicioná-los a sua conta.  
             
3.  Se sua organização tiver **Salesforce CRM Content** habilitado, certifique-se de que a conta administrativa atual o tenha habilitado também.  
  
    1.  Vá para a página de configuração do Salesforce.  
  
         ![instalação do salesforce](./media/salesforce-setup.png "instalação do salesforce")  
  
    2.  No menu lateral, selecione **Gerenciar Usuários** e clique em **Usuários**.  
  
         ![usuários do menu do salesforce](./media/salesforce-menu-users.png "usuários do menu do salesforce")  
  
    3.  Selecione o usuário administrativo atual para seu usuário do Cloud App Security dedicado.  
  
    4.  Certifique-se de que a caixa de seleção **Usuário do Salesforce CRM Content** esteja marcada.  
  
         Se não estiver selecionada, clique em **Editar** e, em seguida, marque a caixa de seleção.  
  
         ![usuário do conteúdo crm do salesforce](./media/salesforce-crm-content-user.png "usuário do conteúdo crm do salesforce")  
  
    5.  Clique em **Salvar**.  
  
4.  No console do Cloud App Security, clique em **Investigar** e em **Aplicativos conectados**.  
  
5.  Na página **Conectores de aplicativos**, clique no botão de mais antes de **Salesforce**.  
  
     ![conectar salesforce](./media/connect-salesforce.png "conectar salesforce")  
  
6.  Na página de configurações do Salesforce, na guia API, clique em **Seguir este link**, dependendo de qual instância que você deseja instalar.  
  
7.  Isso abre a página de logon do Salesforce. Insira suas credenciais para permitir que o Cloud App Security acesse o aplicativo do Salesforce da sua equipe.  
  
     ![logon do salesforce](./media/salesforce-logon.png "logon do salesforce")  
  
8.  O Salesforce perguntará se você deseja permitir que o Cloud App Security acesse o log de atividades e as informações da sua equipe e realize quaisquer atividades como qualquer membro da equipe. Para continuar, clique em **Permitir**.  
  
9. Neste ponto, você receberá uma notificação de êxito ou falha em relação à implementação. O Cloud App Security agora está autorizado no Salesforce.com.  
  
10. De volta ao console do Cloud App Security, você deverá ver a mensagem indicando que o Salesforce foi conectado com êxito.  
  
11. Certifique-se de que a conexão foi bem-sucedida clicando em **Testar API**.  
  
     O teste pode levar alguns minutos. Depois de receber uma notificação de êxito, clique em **Concluído**.  
  
  
Após conectar o Salesforce, você receberá Eventos da seguinte maneira: gatilhos a partir do momento da conexão, Eventos de logon e Trilha de Auditoria de Instalação por 60 dias antes da conexão, EventMonitoring 30 dias ou um dia antes, dependendo da sua licença do Salesforce EventMonitoring. A API do Cloud App Security se comunica diretamente com as APIs disponíveis no Salesforce. Como o Salesforce limita o número de chamadas à API que ele pode receber, o Cloud App Security leva isso em consideração e respeita a limitação. As APIs do Salesforce enviam cada resposta com um campo para os contadores de API, incluindo total disponível e restante. O Cloud App Security calcula isso em um percentual e garante que sempre haja 10% de chamadas à API disponíveis restantes. 

> [!NOTE]
> A limitação do Cloud App Security é calculada apenas em suas próprias chamadas à API com o Salesforce, não com os outros aplicativos que fazem chamadas à API com o Salesforce.
> Limitar as chamadas à API devido à limitação poderá diminuir a taxa em que os dados são incluídos no Cloud App Security, mas normalmente voltará ao normal durante a noite.


Eventos do Salesforce são processados pelo Cloud App Security da seguinte maneira: 
  
- Registro em eventos a cada 15 minutos
- Definição de trilha de auditoria a cada 15 minutos
- Os logs do Salesforce rastreiam a atividade de uso por um período de 24 horas, de 0:00 a 23:59, UTC. Os eventos no Salesforce geram dados de log em tempo real. No entanto, os arquivos de log são gerados pelo Salesforce no dia após um evento ocorrer, fora do horário de pico. Portanto, os dados do arquivo de log ficam indisponíveis por pelo menos um dia após um evento. Para saber mais sobre os eventos do Salesforce, veja [Usando o monitoramento de eventos](https://developer.salesforce.com/docs/atlas.en-us.api_rest.meta/api_rest/using_resources_event_log_files.htm).


## <a name="see-also"></a>Consulte Também  
[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)   

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
---
title: Conectar o Salesforce ao Microsoft Cloud App Security | Microsoft Docs
description: "Este tópico fornece informações sobre como conectar seu aplicativo Salesforce ao Cloud App Security usando o conector de API."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/26/2016
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 776d7589-acdb-4cb6-99a0-3be2f7b6aab2
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 759692e7b270d87dc1becf88453d095f2382c411
ms.openlocfilehash: 28ce67bd096d82e3775a281359fc100e2c214715


---


# <a name="connect-salesforce-to-microsoft-cloud-app-security"></a>Conectar o Salesforce ao Microsoft Cloud App Security
Esta seção fornece instruções para conectar o Cloud App Security à sua conta do Salesforce existente usando a API do conector de aplicativos.  
  
## <a name="how-to-connect-salesforce-to-cloud-app-security"></a>Como conectar o Salesforce ao Cloud App Security  
  
1.  É recomendável ter uma conta de administrador de serviço dedicada para o Cloud App Security.  
  
2.  Confirme se a API REST está habilitada no Salesforce.  
  
     Sua conta do Salesforce deve ser de uma das seguintes edições que incluem o suporte à API REST:  
  
     **Performance**, **Enterprise**, **Unlimited** ou **Developer**.  
  
     A edição **Professional** não tem a API REST por padrão, mas pode ser adicionada sob demanda.  
  
     Verifique se sua edição tem a API REST disponível e habilitada da seguinte maneira:  
  
    -   Faça logon em sua conta do Salesforce e vá para a página **Configuração**.  
  
    -   Em **Gerenciar Usuários**, vá para a página **Perfis**.  
  
         ![perfis manageusers do salesforce](./media/salesforce-manageusers-profiles.png "salesforce manageusers profiles")  
  
    -   Escolha o perfil que você está usando para implantar o Cloud App Security e clique em **Editar**.  
  
         ![editar perfil do salesforce](./media/salesforce-edit-profile.png "salesforce edit profile")  
  
    -   Certifique-se de que a caixa de seleção **API Habilitada** esteja habilitada. Se não estiver selecionada, poderá ser necessário entrar em contato com a Salesforce para adicioná-la à sua conta.  
  
         ![api do salesforce habilitada](./media/salesforce-api-enabled.png "salesforce api enabled")  
  
3.  Se sua organização tiver **Salesforce CRM Content** habilitado, certifique-se de que a conta administrativa atual o tenha habilitado também.  
  
    1.  Vá para a página de configuração do Salesforce.  
  
         ![configuração do salesforce](./media/salesforce-setup.png "salesforce setup")  
  
    2.  No menu lateral, selecione **Gerenciar Usuários** e clique em **Usuários**.  
  
         ![usuários do menu do salesforce](./media/salesforce-menu-users.png "salesforce menu users")  
  
    3.  Selecione o usuário administrativo atual para seu usuário do Cloud App Security dedicado.  
  
    4.  Certifique-se de que a caixa de seleção **Usuário do Salesforce CRM Content** esteja marcada.  
  
         Se não estiver selecionada, clique em **Editar** e, em seguida, marque a caixa de seleção.  
  
         ![usuário do conteúdo crm do salesforce](./media/salesforce-crm-content-user.png "salesforce crm content user")  
  
    5.  Clique em **Salvar**.  
  
4.  No console do Cloud App Security, clique em **Investigar** e em **Aplicativos sancionados**.  
  
5.  Na linha Box, clique em **Conectar** na coluna **Status do Conector de Aplicativos** ou clique no botão **Conectar um aplicativo** seguido por **Salesforce**.  
  
     ![conectar o salesforce](./media/connect-salesforce.png "connect salesforce")  
  
6.  Na página de configurações do Salesforce, na guia API, clique em **Seguir este link**, dependendo de qual instância que você deseja instalar.  
  
7.  Isso abre a página de logon do Salesforce. Insira suas credenciais para permitir que o Cloud App Security acesse o aplicativo do Salesforce da sua equipe.  
  
     ![logon do salesforce](./media/salesforce-logon.png "salesforce logon")  
  
8.  O Salesforce perguntará se você deseja permitir que o Cloud App Security acesse o log de atividades e as informações da sua equipe e realize quaisquer atividades como qualquer membro da equipe. Para continuar, clique em **Permitir**.  
  
9. Neste ponto, você receberá uma notificação de êxito ou falha em relação à implementação. O Cloud App Security agora está autorizado no Salesforce.com.  
  
10. De volta ao console do Cloud App Security, você deverá ver a mensagem indicando que o Salesforce foi conectado com êxito.  
  
11. Certifique-se de que a conexão foi bem-sucedida clicando em **Testar API**.  
  
     O teste pode levar alguns minutos. Depois de receber uma notificação de êxito, clique em **Concluído**.  
  
  
Após conectar o SalesForce, você receberá Eventos da seguinte maneira: Gatilhos a partir do momento da conexão, Eventos de logon e Trilha de Auditoria de Instalação para os 60 dias antes da conexão, EventMonitoring de 30 dias ou 1 dia anterior, dependendo da sua licença do SalesForce EventMonitoring.
  
## <a name="see-also"></a>Veja também  
[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Nov16_HO3-->



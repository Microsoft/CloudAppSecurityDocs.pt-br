---
title: Gerenciar acesso de administrador ao portal do Cloud App Security | Microsoft Docs
description: "Este tópico fornece instruções para configurar o acesso ao portal do Cloud App Security para seus administradores."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/7/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: b718edad-350c-4d90-b045-92529d701dc5
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: ce7a3bb3951e16efeaeafa3e2fc463a3ac5d9dbc
ms.sourcegitcommit: 945cb3c047ae1bfc05be20cc7798c43005b27c9b
ms.translationtype: HT
ms.contentlocale: pt-BR
---
## <a name="managing-admin-access"></a>Gerenciar o acesso administrativo

O Cloud App Security oferece suporte às seguintes funções de administrador:

- Administrador global: os Administradores globais têm **Acesso completo**: os administradores com acesso completo terão permissão total no Cloud App Security para adicionar administradores, adicionar políticas e configurações, carregar logs e executar ações de controle.
- Administrador de segurança: os Administradores de segurança têm **Acesso completo**: os administradores com acesso completo terão permissão total no Cloud App Security para adicionar administradores, adicionar políticas e configurações, carregar logs e executar ações de controle.
- Leitor de segurança: o Leitor de segurança tem permissões somente leitura e pode gerenciar alertas. O Leitor de segurança não tem permissão para executar o seguinte:
      - Criar políticas e editar as existentes 
      - Executar ações de controle 
      - Carregar logs de descoberta
      - Proibir ou aprovar aplicativos de terceiros
      - Acessar e exibir a página de configurações de intervalo de endereço IP
      - Acessar e exibir páginas de configurações 
      - Acessar e exibir as configurações de Descoberta 
      - Acessar e exibir a página de Conectores de aplicativo
      - Acessar e exibir o Log de controle 
      - Acessar e exibir a página Gerenciar relatórios de instantâneo 

Os administradores com essas funções no Azure Active Directory ou no Office 365 terão as mesmas funções no Cloud App Security. Para saber mais sobre funções de administrador, confira [Atribuir funções de administrador no Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-assign-admin-roles).

Para adicionar outros administradores ao Cloud App Security:

1. Clique na engrenagem de configurações ![ícone de configurações](./media/settings-icon.png "ícone de configurações") e, em seguida, em **Gerenciar acesso de administrador**. 

2. Adicione os administradores que devem ter acesso ao Cloud App Security.
  
      
3. Em seguida, clique na lista suspensa para definir o tipo de acesso que o administrador terá, **Acesso completo** ou **Leitor de segurança**.

     >[!NOTE]
      >Qualquer **Leitor segurança** que tenta acessar uma página restrita ou executar uma ação restrita receberá um erro indicando que ele não tem permissão para acessar a página ou executar a ação.

4. Clique em **Fechar**.  

   >[!NOTE]
    >Qualquer usuário não convidado (com uma função adequada – Administrador Global, de Segurança e de Conformidade) pode convidar outros usuários para o Cloud App Security.
  
 ![gerenciar acesso de administrador](./media/manage-admin-access.png "gerenciar acesso de administrador")  

**Para substituir as permissões de administrador:**

Se você quiser substituir a permissão do administrador no Azure Active Directory ou no Office 365, faça isso manualmente adicionando o usuário ao Cloud App Security e atribuindo uma função de usuário.
Por exemplo, se você quiser atribuir à Stephanie, uma Leitora de segurança no Azure Active Directory, o Acesso total no Cloud App Security, adicione-a manualmente ao Cloud App Security e atribua a ela o Acesso completo a fim de substituir sua função e permitir a ela as permissões desejadas no Cloud App Security. 


##  <a name="Adminsettings"></a> Personalizar as configurações de administração  
Para configurar suas preferências como um administrador do Cloud App Security, clique em seu nome na barra de menus do portal e selecione **Configurações de usuário** para definir o seguinte:  
  
1.  Clique em **Configurações de conta**. Aqui você pode personalizar o idioma do portal para sua própria exibição. Você pode defini-lo para exibir o portal em um idioma padrão ou pode definir um idioma diferente para si mesmo.  
  
     ![configurações de usuário personalizadas](./media/custom-user-settings.png "configurações de usuário personalizadas")  
  
2.  Clique em **Notificações** e defina as preferências de notificação de email e texto para os emails recebidos do sistema.  Você pode definir a gravidade para quais alertas e violações deseja receber emails. A gravidade é definida por política, portanto, quando as violações forem disparadas, você receberá uma notificação por email dependendo das configurações daqui e da configuração de Gravidade na política que foi violada. Os emails serão enviados para o alias associado com a conta de usuário do administrador usada para fazer logon no Cloud App Security. Insira um número de telefone para permitir que o Cloud App Security envie mensagens de texto quando alertas e notificações forem enviados e defina o nível de gravidade para o qual você deseja receber notificações por mensagem de texto.  
  
   > [!NOTE] 
   > O número máximo de alertas que serão enviados por meio de mensagem de texto é 10 por número de telefone por dia. Observe que o dia é calculado de acordo com o fuso horário UTC. 
  
  ![configurações de notificação](./media/notification-settings.png "configurações de notificação")  
  
3. Quando terminar, clique em **Salvar**.  


## <a name="region-and-language-settings"></a>Configurações de região e idioma  
  
1. Defina o **Idioma** padrão a ser usado para o portal. Para modificar o idioma para um administrador específico, vá para **Configurações de usuário** > **Configurações de conta**.  
  
   ![idioma do fuso horário](./media/timezone-language.png "idioma do fuso horário")  
  
2. Defina o **Fuso horário mestre**. O Cloud App Security analisa e agrega os dados continuamente. Por padrão, o fuso horário para o portal do Cloud App Security é definido como UTC. É importante definir o fuso horário mestre, o que permite que o Cloud App Security date com precisão os incidentes em seu sistema. Por exemplo, no Gráfico de atividade, os dados são organizados por data; essas datas são afetadas pelo fuso horário do seu sistema, portanto, se você não modificou o fuso horário padrão, os dados serão organizados em dias de 24 horas de acordo com o fuso horário UTC, o que podem afetar seus dados em muitas horas.  
  
     ![fuso horário mestre](./media/master-time-zone.png "fuso horário mestre")  
  
## <a name="back-up-portal-settings"></a>Fazer backup das configurações do portal

Se a qualquer momento você desejar fazer o backup das suas configurações do portal, essa tela permitirá que você faça isso. Clique em Exportar configurações do portal para criar um arquivo json de todas as suas configurações do portal, incluindo as regras de política, grupos de usuários e intervalos de endereços IP.  
  
![console de backup](./media/backup-console.png "console de backup")  
  
##  <a name="mailsettings"></a> Personalizar sua experiência  
Na barra de menus, clique no ícone de configurações ![ícone de configurações](./media/settings-icon.png "ícone de configurações") e selecione **Configurações de Email** para definir os parâmetros para notificações por email enviadas do Cloud App Security para administradores que solicitam alertas e notificações enviadas para os usuários finais sobre violações em que estão envolvidos.  
  
![menu de configuração de email](./media/mail-setting-menu.png "menu de configuração de email")  
  
Configure o seguinte:  
  
1.  **Do endereço de email**: a conta de email que você deseja usar para enviar a notificação.  
  
     **Nome de exibição**: o nome a ser exibido no campo **De** da mensagem de email.  
  
     **Endereço de email para resposta**: a conta de email a ser usada para respostas à mensagem.  
  
     ![definição de configurações de email](./media/mail-settings-config.png "definição de configurações de email")  
  
2.  Você pode usar um arquivo html para personalizar e criar as mensagens de email enviadas do sistema. O arquivo html usado para o modelo deve incluir o seguinte:  
  
    -   Todo modelo CSS deve estar embutido no modelo.  
  
    -   O modelo deve ter três espaços reservados não editáveis:  
  
         %%logo%% ‑ Uma URL para o logotipo da sua empresa que foi carregado na página Configuração geral  
  
         %%title%% ‑ Um espaço reservado para o título do email, conforme definido pela política.  
  
         %%content%% ‑ Um espaço reservado para o conteúdo que será incluído para os usuários finais, conforme definido pela política.  
  
     A seguir está um exemplo de modelo de email: 
```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
  <html>  
       <head>  
            <meta http-equiv="Content-Type" content="text/html; charset=UTF-8"/>  
            <meta name="viewport" content="width=device-width, initial-scale=1.0"/>  
          </head>  
          <body class="end-user">  
          <table border="0" cellpadding="20%" cellspacing="0" width="100%" id="background-table">  
            <tr>  
              <td align="center">  
                <!--[if (gte mso 9)|(IE)]>  
                <table width="600" align="center" cellpadding="0" cellspacing="0" border="0">  
                  <tr>  
                    <td>  
                <![endif]-->  
                <table bgcolor="#ffffff" align="center" border="0" cellpadding="0" cellspacing="0" style="padding-bottom: 40px;" id="container-table">  
                  <tr>  
                    <td align="right" id="header-table-cell">  
                      <img src="%%logo%%" alt="Microsoft Cloud App Security" id="org-logo" />  
                    </td>  
                  </tr>  
                  <tr>  
                    <td style="padding-top: 58px;" align="center" valign="top">  
                      <table width="100%" cellpadding="12">  
                        <tr>  
                          <td align="center" class="round-title">  
                            %%title%%  
                          </td>  
                        </tr>  
                      </table>  
                    </td>  
                  </tr>  
                  <tr>  
                    <td style="padding: 0 40px 79px 40px;" class="content-table-cell" align="left" valign="top">  
                        %%content%%  
                    </td>  
                  </tr>  
                  <tr>  
                    <td class="last-row"></td>  
                  </tr>  
                </table>  
                <!--[if (gte mso 9)|(IE)]>  
                </td>  
                </tr>  
                </table>  
                  <![endif]-->  
              </td>  
              </tr>  
          </table>  
            </body>  
          </html>  
    ```

  
3.  Click **Upload a template...** and select the file you created.  
  
     Then, click **Send a test email** to send yourself a test email to see an example of the template you created.  
     The email will be sent to the account you used to log into the portal. In the test email you will be able to see the metadata fields, the template, the email subject, the title in the email body and the content.  
  
## Single sign-on  
Cloud App Security is coupled with Azure Active Directory for authentication, provisioning, and licensing related activities. For information on how to manage single sign-on, see [Azure Active Directory federation compatibility list: third-party identity providers that can be used to implement single sign-on](https://msdn.microsoft.com/library/azure/jj679342.aspx).  


> [!NOTE] 
> If you use ExpressRoute, Cloud App Security is deployed in Azure and fully integrated with [ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-introduction/). All interactions with the Cloud App Security apps and traffic sent to Cloud App Security, including upload of discovery logs, is routed via ExpressRoute **public peering** for improved latency, performance and security. There are no configuration steps required from the customer side.  
    For more information about  Public Peering, see [ExpressRoute circuits and routing domains](https://azure.microsoft.com/documentation/articles/expressroute-circuit-peerings/).  
    
## See Also  
[Set up Cloud Discovery](set-up-cloud-discovery.md)   
[For technical support, please visit the Cloud App Security assisted support page.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Premier customers can also choose Cloud App Security directly from the Premier Portal.](https://premier.microsoft.com/)  
  
  
---
title: Personalizar o portal de Cloud App Security para melhores resultados | Microsoft Docs
description: "Este tópico fornece as primeiras etapas para personalizar o portal."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/19/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 2e7e57b0-db54-4d75-896c-4700dd9abe48
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: f05a39b834178406a6b4b010cd7a1c6096f8c37f
ms.sourcegitcommit: 945cb3c047ae1bfc05be20cc7798c43005b27c9b
ms.translationtype: HT
ms.contentlocale: pt-BR
---
# <a name="customize-the-portal"></a>Personalizar o portal
O procedimento a seguir fornece instruções para personalizar o portal do Cloud App Security.
  
## <a name="set-up-the-portal"></a>Configurar o portal  
  
1.  No portal do Cloud App Security, na barra de menus, clique no ícone de configurações ![ícone de configurações](./media/settings-icon.png "ícone de configurações") e selecione **Configurações Gerais** para configurar o seguinte:  
  
3.  **Detalhes da organização**  
  
     É importante que você forneça um **Nome de exibição da organização** para sua organização. Ele será exibido em emails e páginas da Web enviadas do sistema.  
  
     Forneça um **Nome do ambiente** (locatário). Isso será especialmente importante se você gerenciar vários locatários.  
  
4. Também é possível fornecer um **logotipo** que será exibido em notificações de email enviadas do sistema e em páginas da web enviadas do sistema. O logotipo deve ser um arquivo png com um tamanho máximo de 150 x 50 pixels em uma tela de fundo transparente.  

4.  Adicione uma lista de seus **Domínios gerenciados**. Os domínios gerenciados são usados para ajudar o Cloud App Security a determinar quais usuários são internos, quais são externos e onde os arquivos devem e não devem ser compartilhados. Isso é usado para relatórios, bem como alertas.  
> [!NOTE] 
> - Os usuários em domínios que não estão configurados como interno serão marcados como externos e seus arquivos e atividades não serão verificados.
> - Se você estiver se integrando com a integração da Proteção de Informações do Azure, consulte [Integração da Proteção de Informações do Azure](azip-integration.md) para obter informações. 
  
4.  **Configurações de privacidade do email do log de atividades**  
  
     Quando as mensagens de email são detectadas do Exchange Online, é possível definir como elas são exibidas para preservar a privacidade. É possível configurar a mensagem de email para ser exibida com uma **Linha de assunto mascarada**, com o **Conteúdo completo** ou com um **Nº da Tarefa**.  
  
     ![configurações gerais](./media/general-settings.png "configurações gerais")  
  
5.  **Configurações de idioma e região**  
  
     Defina o **Idioma** padrão a ser usado para o portal. Para modificar o idioma para um administrador específico, vá para **Configurações de usuário** > **Configurações de conta**.  
  
     ![idioma do fuso horário](./media/timezone-language.png "idioma do fuso horário")  
  
     Defina o **Fuso horário mestre**. O Cloud App Security analisa e agrega os dados continuamente. Por padrão, o fuso horário para o portal do Cloud App Security é definido como UTC. É importante definir o fuso horário mestre, o que permite que o Cloud App Security date com precisão os incidentes em seu sistema. Por exemplo, no Gráfico de atividade, os dados são organizados por data; essas datas são afetadas pelo fuso horário do seu sistema, portanto, se você não modificou o fuso horário padrão, os dados serão organizados em dias de 24 horas de acordo com o fuso horário UTC, o que podem afetar seus dados em muitas horas.  
  
     ![fuso horário mestre](./media/master-time-zone.png "fuso horário mestre")  
  
6.  Se a qualquer momento você desejar fazer o backup das suas configurações do portal, essa tela permitirá que você faça isso. Clique em Exportar configurações do portal para criar um arquivo json de todas as suas configurações do portal, incluindo as regras de política, grupos de usuários e intervalos de endereços IP.  
  
     ![console de backup](./media/backup-console.png "console de backup")  
  
7.  Para adicionar administradores adicionais ao Cloud App Security, clique na engrenagem de configurações ![ícone de configurações](./media/settings-icon.png "ícone de configurações") e, em seguida, em **Gerenciar acesso de administrador**. Adicione os administradores que devem ter acesso ao Cloud App Security e clique em **Fechar**.  
>[!NOTE]
>Qualquer usuário não convidado (com uma função adequada – Administrador Global, de Segurança e de Conformidade) pode convidar outros usuários para o Cloud App Security.
  
![gerenciar acesso de administrador](./media/manage-admin-access.png "gerenciar acesso de administrador")  
  
##  <a name="Adminsettings"></a> Personalizar as configurações de administração  
Para configurar suas preferências como um administrador do Cloud App Security, clique em seu nome na barra de menus do portal e selecione **Configurações de usuário** para definir o seguinte:  
  
1.  Clique em **Configurações de conta**. Aqui você pode personalizar o idioma do portal para sua própria exibição. Você pode defini-lo para exibir o portal em um idioma padrão ou pode definir um idioma diferente para si mesmo.  
  
     ![configurações de usuário personalizadas](./media/custom-user-settings.png "configurações de usuário personalizadas")  
  
2.  Clique em **Notificações** e defina as preferências de notificação de email e texto para os emails recebidos do sistema.  Você pode definir a gravidade para quais alertas e violações deseja receber emails. A gravidade é definida por política, portanto, quando as violações forem disparadas, você receberá uma notificação por email dependendo das configurações daqui e da configuração de Gravidade na política que foi violada. Os emails serão enviados para o alias associado com a conta de usuário do administrador usada para fazer logon no Cloud App Security. Insira um número de telefone para permitir que o Cloud App Security envie mensagens de texto quando alertas e notificações forem enviados e defina o nível de gravidade para o qual você deseja receber notificações por mensagem de texto.  
  
> [!NOTE] 
> O número máximo de alertas que serão enviados por meio de mensagem de texto é 10 por número de telefone por dia. Observe que o dia é calculado de acordo com o fuso horário UTC. 
  
  ![configurações de notificação](./media/notification-settings.png "configurações de notificação")  
  
3. Quando terminar, clique em **Salvar**.  
  
##  <a name="IPtagsandRanges"></a> Definir intervalos IP  
Para identificar facilmente os endereços IP conhecidos, como seus endereços IP do escritório físico, é necessário definir intervalos de endereço IP, o que permite que você marque e categorize apropriadamente e personalize a forma como os logs e alertas são exibidos e investigados.   
Consulte [Marcas de IP](ip-tags.md) para obter mais informações.
  
## <a name="import-user-groups"></a>Importar grupos de usuários

Quando você conecta aplicativos usando conectores de API, o Cloud App Security permite que você importe grupos de usuários, por exemplo do Office 365 e do Azure Active Directory.

Consulte [Grupos de usuários](user-groups.md) para obter mais informações.

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
  
  
---
title: "Definir as preferências de notificação de email | Microsoft Docs"
description: "Este artigo oferece informações sobre como personalizar as notificações de email enviadas pelo Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/23/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 8402cdc9-4969-4150-b567-ccc9d75e5370
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: ce24e4c25ab4d8b85e4ddb6d6d574dd29b8c2003
ms.sourcegitcommit: 2f4474084c7e07ac4853945ab5aa1ea78950675d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/28/2017
---
##  <a name="mailsettings"></a> Definir as preferências de notificação de email  
Na barra de menus, clique no ícone de configurações ![ícone de configurações](./media/settings-icon.png "ícone de configurações") e selecione **Configurações de Email** para definir os parâmetros para notificações por email enviadas do Cloud App Security para administradores que solicitam alertas e notificações enviadas para os usuários finais sobre violações em que estão envolvidos.  
  
![menu de configuração de email](./media/mail-setting-menu.png "menu de configuração de email")  
  
Configure o seguinte:  
  
1.  **Do endereço de email**: a conta de email que você deseja usar para enviar a notificação.  
  
     **Nome de exibição**: o nome a ser exibido no campo **De** da mensagem de email.  
  
     **Endereço de email para resposta**: a conta de email a ser usada para respostas à mensagem.  
  
     ![definição de configurações de email](./media/mail-settings-config.png "definição de configurações de email")  

  >[!NOTE]
  >Para alterar o campo **Do endereço de email** para um domínio de sua preferência, consulte as instruções [aqui](https://mandrill.zendesk.com/hc/articles/205582277-How-do-I-add-DNS-records-for-my-sending-domains-).
  
2.  Para o **Design de email**, você pode usar um arquivo html para personalizar e criar as mensagens de email enviadas do sistema. O arquivo html usado para o modelo deve incluir o seguinte:  
  
    -   Todo modelo CSS deve estar embutido no modelo.  
  
    -   O modelo deve ter três espaços reservados não editáveis:  
  
         %%logo%% ‑ Uma URL para o logotipo da sua empresa que foi carregado na página Configuração geral  
  
         %%title%% ‑ Um espaço reservado para o título do email, conforme definido pela política.  

         %%content%% ‑ Um espaço reservado para o conteúdo que será incluído para os usuários finais, conforme definido pela política.  
     
3.  Clique em **Carregar um modelo...** e selecione o arquivo que você criou. 

4. Em seguida, clique em **Enviar um email de teste** para enviar um email de teste para você mesmo para ver um exemplo do modelo que você criou. O email será enviado para a conta usada para fazer logon no portal. No email de teste, você poderá ver os campos de metadados, o modelo, o assunto do email, o título no corpo do email e o conteúdo.  A seguir está um exemplo de modelo de email: 



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
  

  
  

  
    
## <a name="see-also"></a>Veja também  
[Configurar o Cloud Discovery](set-up-cloud-discovery.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
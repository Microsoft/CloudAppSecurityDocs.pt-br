---
title: "Definir as preferências de notificação de email | Microsoft Docs"
description: "Este artigo oferece informações sobre como personalizar as notificações de email enviadas pelo Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/3/2018
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 8402cdc9-4969-4150-b567-ccc9d75e5370
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: de4e7025f046f15e0aa36f2cf45d17a3502a0644
ms.sourcegitcommit: 9de7ed2224aeed049fc2a87e52307988f8837eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/08/2018
---
##  <a name="mailsettings"></a> Definir as preferências de notificação de email  

Para definir parâmetros para as notificações de email enviadas do Cloud App Security para administradores solicitando alertas e para as notificações enviadas para usuários finais informando sobre as violações nas quais estão envolvidos, faça este procedimento. Para obter informações sobre o endereço IP do servidor de email do Cloud App Security que você deve incluir na lista de permissões em seu serviço antispam, consulte [Requisitos de rede](network-requirements.md). 


1. Na barra de menus, clique na engrenagem de configurações ![ícone de configurações](./media/settings-icon.png "ícone de configurações"), selecione **Configurações** e depois a guia **Configurações de Email**.  

2. **Do endereço de email**: a conta de email que você deseja usar para enviar a notificação.  
   
   **Nome de exibição**: o nome a ser exibido no campo **De** da mensagem de email.  
  
   **Endereço de email para resposta**: a conta de email a ser usada para respostas à mensagem.  
  
     ![definição de configurações de email](./media/mail-settings-config.png "definição de configurações de email")  

  >[!NOTE]
  >Para alterar o campo **Do endereço de email** para um domínio de sua preferência, consulte as instruções [aqui](https://mandrill.zendesk.com/hc/articles/205582277-How-do-I-add-DNS-records-for-my-sending-domains-).
  
2.  Para o **Design de email**, você pode usar um arquivo html para personalizar e criar as mensagens de email enviadas do sistema. O arquivo html usado para o modelo deve incluir o seguinte:  
  
    -   Todos os arquivos CSS devem estar embutidos no modelo.  
  
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
  

  
  

  
    
## <a name="see-also"></a>Consulte Também  
[Configurar o Cloud Discovery](set-up-cloud-discovery.md)   

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
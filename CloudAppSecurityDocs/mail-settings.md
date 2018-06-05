---
title: Definir as preferências de notificação de email | Microsoft Docs
description: Este artigo oferece informações sobre como personalizar as notificações de email enviadas pelo Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/29/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 8402cdc9-4969-4150-b567-ccc9d75e5370
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 6d19e90b8eda14868f1b25e6d9a776b030aeedbd
ms.sourcegitcommit: af8fad9709171b200699ca1ed513e2831826ed7e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34568417"
---
*Aplica-se ao: Microsoft Cloud App Security*


##  <a name="mailsettings"></a> Definir as preferências de notificação de email  

Para definir parâmetros para as notificações de email enviadas do Microsoft Cloud App Security para administradores solicitando alertas e para as notificações enviadas para usuários finais informando sobre as violações nas quais estão envolvidos, faça este procedimento. Para obter informações sobre o endereço IP do servidor de email do Microsoft Cloud App Security que você deve incluir na lista de permissões em seu serviço antispam, consulte [Requisitos de rede](network-requirements.md). 


1. Na barra de menus, clique na engrenagem de configurações ![ícone de configurações](./media/settings-icon.png "ícone de configurações"), selecione **Configurações** e depois a guia **Configurações de Email**.  

   ![configurações de email](./media/mail-settings-config.png)

2. Em **Identidade do remetente de email**: se você estiver planejando usar as configurações de email padrão, não será necessário alterar qualquer coisa nesta seção. Se você quiser personalizar a identidade do remetente de email, defina uma destas configurações para personalizar o campo que você deseja alterar. É possível alterar qualquer uma destas opções: **Do nome de exibição**, **Do endereço de email**, **Endereço de email para resposta**. O Microsoft Cloud App Security faz isso para você por meio de um serviço de email de terceiros chamado MailChimp®. Revise e aceite os Termos de Serviço e a Declaração de Privacidade do MailChimp para habilitar isso. Caso contrário, o Microsoft Cloud App Security enviará as notificações usando as configurações padrão.
   
   > [!NOTE]
   > Somente caracteres unicode têm suporte no nome de exibição e no endereço de email, de acordo com o [padrão rfc822](http://www.rfc-editor.org/rfc/rfc822.txt).

  
3. Para o **Design de email**, você pode usar um arquivo html para personalizar e criar as mensagens de email enviadas do sistema. O arquivo html usado para o modelo deve incluir o seguinte:  
  
   -   Todos os arquivos CSS devem estar embutidos no modelo.  
  
   -   O modelo deve ter três espaços reservados não editáveis:  
  
        %%logo%% ‑ Uma URL para o logotipo da sua empresa que foi carregado na página Configuração geral  
  
        %%title%% ‑ Um espaço reservado para o título do email, conforme definido pela política.  

        %%content%% ‑ Um espaço reservado para o conteúdo que será incluído para os usuários finais, conforme definido pela política.  
     
4. Clique em **Carregar um modelo...** e selecione o arquivo que você criou. 

5. Em seguida, clique em **Enviar um email de teste** para enviar um email de teste para você mesmo para ver um exemplo do modelo que você criou. O email será enviado para a conta usada para fazer logon no portal. No email de teste, você poderá ver os campos de metadados, o modelo, o assunto do email, o título no corpo do email e o conteúdo.  A seguir está um exemplo de modelo de email: 



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
  
  
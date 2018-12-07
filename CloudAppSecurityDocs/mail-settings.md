---
title: Definir as preferências de notificação de email | Microsoft Docs
description: Este artigo oferece informações sobre como personalizar as notificações de email enviadas pelo Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/16/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 8402cdc9-4969-4150-b567-ccc9d75e5370
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 2d1621dd7a1e082631b941ecfb711a686a69991a
ms.sourcegitcommit: 851ff017c226435d38bed18dbece640a632cd2a0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2018
ms.locfileid: "51943694"
---
# <a name="email-notification-preferences"></a>Preferências de notificação por email

*Aplica-se ao: Microsoft Cloud App Security*

Este artigo oferece informações sobre como personalizar as notificações de email enviadas pelo Cloud App Security.

## <a name="mailsettings"></a> Definir as preferências de notificação de email  

 O Microsoft Cloud App Security envia notificações por email aos administradores solicitando alertas e aos usuários finais envolvidos em violações. Para definir parâmetros para notificações por email, siga este procedimento. Para obter informações sobre o endereço IP do servidor de email do Microsoft Cloud App Security que você deve incluir na lista de permissões em seu serviço antispam, consulte [Requisitos de rede](network-requirements.md).

1. Na barra de menus, clique na engrenagem de configurações, selecione **Configurações** e, em seguida, a guia **Configurações de email**.  

   ![configurações de email](./media/mail-settings-config.png)

2. Em **Identidade do remetente de email**: se você pretende usar as configurações de email padrão, não precisa alterar nada nesta seção. Se você quiser personalizar a identidade do remetente de email, defina uma destas configurações para personalizar o campo que você deseja alterar. Altere um ou todos os seguintes itens: **Do nome de exibição**, **Do endereço de email**, **Endereço de email para resposta**. O Microsoft Cloud App Security realiza a personalização usando um serviço de email de terceiros chamado MailChimp®. Lembre-se de examinar e aceitar os Termos de serviço e a Política de privacidade do MailChimp para habilitar a personalização. Caso contrário, o Microsoft Cloud App Security enviará as notificações usando as configurações padrão.
 
   > [!NOTE]
   > Somente caracteres unicode têm suporte no nome de exibição e no endereço de email, de acordo com o [padrão rfc822](http://www.rfc-editor.org/rfc/rfc822.txt).

  
3. Para o **Design de email**, você pode usar um arquivo html para personalizar e criar as mensagens de email enviadas do sistema. O arquivo HTML usado para o modelo deve incluir os seguintes itens:  
  
   - Todos os arquivos CSS devem estar embutidos no modelo.  
  
   - O modelo deve ter três espaços reservados não editáveis:  
  
        - **%%logo%%** – a URL para o logotipo de sua empresa que foi carregado na página Configuração geral.  
  
        - **%%title%%** – espaço reservado para o título do email, conforme definido pela política.  

        - **%%content%%** – espaço reservado para o conteúdo que será incluído para os usuários finais, conforme definido pela política.  

4. Clique em **Carregar um modelo...** e selecione o arquivo que você criou. 

5. Clique em **Enviar um email de teste** para enviar por email para você um exemplo do modelo criado. O email será enviado para a conta usada para fazer logon no portal. No email de teste, você verá e verificará os seguintes itens:
    - Os campos de metadados
    - O modelo
    - O assunto do email
    - O título no corpo do email
    - O conteúdo

## <a name="sample-email-template"></a>Modelo de email de exemplo

Veja abaixo um modelo de email de exemplo:

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

## <a name="next-steps"></a>Próximas etapas

[Configurar o Cloud Discovery](set-up-cloud-discovery.md)   

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
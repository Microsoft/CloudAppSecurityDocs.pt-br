---
title: "Configuração geral | Microsoft Docs"
description: "Este tópico fornece as primeiras etapas para colocar o Cloud App Security em funcionamento."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 2e7e57b0-db54-4d75-896c-4700dd9abe48
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 400741713d40422a3b1c7680663a572d18e9c692
ms.openlocfilehash: 5c93d5c0f15c0ed6dfd44c0629b8413cdc980e3f


---

# <a name="general-setup"></a>Configuração geral
O procedimento a seguir fornece instruções para configurar o [!INCLUDE[Adallom1](./includes/adallom1_md.md)] para trabalhar em seu ambiente de nuvem.  
  
## <a name="prerequisites"></a>Pré-requisitos  
  
-   Sua organização deve ter uma licença do Cloud App Security para usar o produto. Para obter mais informações, consulte [How to buy Cloud App Security](https://www.microsoft.com/server-cloud/products/cloud-app-security/default.aspx) (Como comprar o Cloud App Security) e verifique os [Licensing resources](https://www.microsoft.com/server-cloud/products/cloud-app-security/default.aspx) (Recursos de licenciamento).  
  
     Para obter suporte para a ativação de locatário, consulte [Contatar o suporte comercial do Office 365 ‑ Ajuda para Administradores](https://support.office.com/article/Contact-Office-365-for-business-support-Admin-Help-32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b).  
  
> [!NOTE] 
> Não é necessário ter uma licença do Office 365 para o Cloud App Security.  
  
-   Depois que tiver adquirido uma licença do Cloud App Security, você receberá um email com informações de ativação e um link para o portal do Cloud App Security.  
  
-   Para configurar o Cloud App Security, você deve ser um Administrador Global, um Administrador de Conformidade ou um Administrador de Segurança no Azure Active Directory ou Office 365. É importante entender que um usuário que está atribuído a uma função de administrador terá as mesmas permissões em todos os aplicativos de nuvem que sua organização tenha assinado, independentemente de você atribuir a função no portal do Office 365, no Portal Clássico do Azure ou usando o módulo do Azure AD para Windows PowerShell. Para obter mais informações, consulte [Atribuir funções de administrador no Office 365](https://support.office.com/article/Assigning-admin-roles-in-Office-365-eac4d046-1afd-4f1a-85fc-8219c79e1504) e [Atribuindo funções de administrador no Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-assign-admin-roles/).  
  
-   Para executar o portal do Cloud App Security, use o Internet Explorer 11, Microsoft Edge (mais recente), Google Chrome (mais recente), Mozilla Firefox (mais recente) ou Apple Safari (mais recente).  
  
-   ExpressRoute  
  
     O Cloud App Security é implantado no Azure e totalmente integrado com o [ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-introduction/). Todas as interações com os aplicativos do Cloud App Security e o tráfego enviado ele, incluindo o upload de logs de descoberta, são roteados por meio do **emparelhamento público** do ExpressRoute para latência, desempenho e segurança aprimorados. Não há nenhuma etapa de configuração necessária do lado do cliente.  
    Para obter mais informações sobre o emparelhamento público, consulte [Circuitos da Rota Expressa e domínios de roteamento](https://azure.microsoft.com/documentation/articles/expressroute-circuit-peerings/).  
  
## <a name="set-up-the-portal"></a>Configurar o portal  
  
1.  Para acessar o portal do Cloud App Security, acesse [https://portal.cloudappsecurity.com](https://portal.cloudappsecurity.com).  
  
     Como alternativa, você pode acessar o portal por meio do **Centro de Administração do Office 365** clicando no ícone dos Centros de administração ![ícone dos centros de administração do O365](./media/o365-admin-centers-icon.png "O365 admin centers icon"), seguido por **Cloud App Security**.  
  
     ![Acesso do O365](./media/access-from-o365.png "Access from O365")  
  
2.  No portal do Cloud App Security, na barra de menus, clique no ícone de configurações ![ícone de configurações](./media/settings-icon.png "settings icon") e selecione **Configurações gerais** para configurar o seguinte:  
  
3.  **Detalhes da organização**  
  
     É importante que você forneça um **Nome de exibição da organização** para sua organização. Ele será exibido em emails e páginas da Web enviadas do sistema.  
  
     Forneça um **Nome de ambiente** (locatário). Isso será especialmente importante se você gerenciar vários locatários.  
  
     Adicione uma lista de seus **Domínios gerenciados**. Os domínios gerenciados são usados para ajudar o Cloud App Security a determinar quais usuários são internos, quais são externos e onde os arquivos devem e não devem ser compartilhados. Isso é usado para relatórios, bem como alertas.  
> [!NOTE] 
> Os usuários em domínios que não estão configurados como interno serão marcados como externos e seus arquivos e atividades não serão verificados.
   
Também é possível fornecer um **logotipo** que será exibido em notificações de email enviadas do sistema e em páginas da web enviadas do sistema. O logotipo deve ser um arquivo png com um tamanho máximo de 150 x 50 pixels em uma tela de fundo transparente.  
  
4.  **Configurações de privacidade do email do log de atividades**  
  
     Quando as mensagens de email são detectadas do Exchange Online, é possível definir como elas são exibidas para preservar a privacidade. É possível configurar a mensagem de email para ser exibida com uma **Linha de assunto mascarada**, com o **Conteúdo completo** ou com um **Nº da Tarefa**.  
  
     ![configurações gerais](./media/general-settings.png "general settings")  
  
5.  **Configurações de idioma e região**  
  
     Defina o **Idioma** padrão a ser usado para o portal. Para modificar o idioma para um administrador específico, vá para **Configurações de usuário** > **Configurações de conta**.  
  
     ![idioma de fuso horário](./media/timezone-language.png "timezone language")  
  
     Defina o **Fuso horário mestre**. O Cloud App Security analisa e agrega os dados continuamente. Por padrão, o fuso horário para o portal do Cloud App Security é definido como UTC. É importante definir o fuso horário mestre, o que permite que o Cloud App Security date com precisão os incidentes em seu sistema. Por exemplo, no Gráfico de atividade, os dados são organizados por data; essas datas são afetadas pelo fuso horário do seu sistema, portanto, se você não modificou o fuso horário padrão, os dados serão organizados em dias de 24 horas de acordo com o fuso horário UTC, o que podem afetar seus dados em muitas horas.  
  
     ![fuso horário mestre](./media/master-time-zone.png "master time zone")  
  
6.  Se a qualquer momento você desejar fazer o backup das suas configurações do portal, essa tela permitirá que você faça isso. Clique em Exportar configurações do portal para criar um arquivo json de todas as suas configurações do portal, incluindo as regras de política, grupos de usuários e intervalos de endereços IP.  
  
     ![console de backup](./media/backup-console.png "backup console")  
  
7.  Para adicionar administradores adicionais ao Cloud App Security, clique na engrenagem de configurações ![ícone de configurações](./media/settings-icon.png "settings icon") e em **Gerenciar acesso de administrador**. Adicione os administradores que devem ter acesso ao Cloud App Security e clique em **Fechar**.  
>[!NOTE]
>Qualquer usuário não convidado (com uma função adequada – Administrador Global, de Segurança e de Conformidade) pode convidar outros usuários para o Cloud App Security.
  
![gerenciar o acesso administrativo](./media/manage-admin-access.png "manage admin access")  
  
##  <a name="a-nameadminsettingsa-customize-your-admin-settings"></a><a name="Adminsettings"></a> Personalizar as configurações de administração  
Para configurar suas preferências como um administrador do Cloud App Security, clique em seu nome na barra de menus do portal e selecione **Configurações de usuário** para definir o seguinte:  
  
1.  Clique em **Configurações de conta**. Aqui você pode personalizar o idioma do portal para sua própria exibição. Você pode defini-lo para exibir o portal em um idioma padrão ou pode definir um idioma diferente para si mesmo.  
  
     ![configurações personalizadas do usuário](./media/custom-user-settings.png "custom user settings")  
  
2.  Clique em **Notificações** e defina as preferências de notificação de email e texto para os emails recebidos do sistema.  Você pode definir a gravidade para quais alertas e violações deseja receber emails. A gravidade é definida por política, portanto, quando as violações forem disparadas, você receberá uma notificação por email dependendo das configurações daqui e da configuração de Gravidade na política que foi violada. Os emails serão enviados para o alias associado com a conta de usuário do administrador usada para fazer logon no Cloud App Security. Insira um número de telefone para permitir que o Cloud App Security envie mensagens de texto quando alertas e notificações forem enviados e defina o nível de gravidade para o qual você deseja receber notificações por mensagem de texto.  
  
> [!NOTE] 
> O número máximo de alertas que serão enviados por meio de mensagem de texto é 10 por número de telefone por dia. Observe que o dia é calculado de acordo com o fuso horário UTC. 
  
  ![configurações de notificação](./media/notification-settings.png "notification settings")  
  
  
3. Quando terminar, clique em **Salvar**.  
  
##  <a name="a-nameiptagsandrangesa-organize-the-data-according-to-your-needs"></a><a name="IPtagsandRanges"></a> Organizar os dados de acordo com suas necessidades  
Para identificar facilmente os endereços IP conhecidos, como seus endereços IP do escritório físico, é necessário definir intervalos de endereço IP, o que permite que você marque e categorize apropriadamente e personalize a forma como os logs e alertas são exibidos e investigados.   
Cada grupo de intervalos de IP pode ser categorizado com base em uma lista predefinida de categorias de IP ou marcado com suas próprias marcas de IP criadas. Além disso, essa configuração permite que você substitua as informações de geolocalização com base no seu conhecimento de rede interno.  
  
Há suporte para IPv4 e IPv6.  
  
Na barra de menus, clique no ícone de configurações ![ícone de configurações](./media/settings-icon.png "settings icon") e selecione **Intervalos de endereços IP**. Clique em **+Adicionar Intervalo de Endereços IP** e defina o seguinte:  
  
> [!NOTE]  
>  O local e o ISP registrado substituirão os padrões.   
> No entanto, as marcas de IP são adicionadas à atividade sem substituir os dados.  
  
1.  Atribua um **Nome** ao seu intervalo de IP. O nome não aparecerá no log de atividades, ele é usado apenas para gerenciar o intervalo de IP.  
  
     Para incluir o intervalo de IP em uma categoria de IP, selecione uma categoria no menu suspenso.  
  
2.  Insira o **Intervalo de endereços IP** que você deseja configurar e clique no botão "+". Você pode adicionar quantos endereços IP e sub-redes desejar usando a notação de prefixo de rede (também conhecida como notação CIDR), por exemplo, 192.168.1.0/32.  
  
3.  Para os campos **Substituir o local** ou Organização (ISP) para esses endereços, insira um novo valor. Por exemplo, se você tiver um endereço IP que é considerado publicamente como sendo da Irlanda, mas você sabe que é dos Estados Unidos, você poderá substituir essa configuração.  
  
4.  Insira um **ISP Registrado**. Isso substituirá os dados em suas atividades  
  
5.  Para **Marcar** as atividades desses endereços IP, insira uma marca. Inserir uma palavra na caixa cria a marca. Depois que você já tiver uma marca configurada, poderá adicioná-la facilmente a intervalos de IP adicionais selecionando-a na lista. Você pode adicionar quantas marcas de IP desejar para cada intervalo. As marcas de IP podem ser usadas ao criar políticas.  
  
     As **Marcas de IP** internas do Cloud App Security são definidas para endereços arriscados e são constantemente atualizadas. Essas marcas incluem proxies Anônimos, provedores de satélite, nós de saída Tor e a rede de proxy do Cloud App Security. Essas marcas internas não são visíveis.  
  
6.  As **Categorias de IP** são usadas para reconhecer facilmente atividades de endereços IP interessantes. As categorias estão disponíveis no portal embora precisem de configuração do usuário para determinar quais endereços IP estão incluídos em cada categoria, exceto para a categoria “Arriscados”, que inclui duas marcas de IP: proxy anônimo e Tor.  
  
     As seguintes categorias IP estão disponíveis:  
  
    -   **Administrativos**: esses devem ser todos os endereços IP dos seus administradores.  
  
    -   **Internos**: esses devem ser todos os endereços IP da sua rede interna, suas filiais e seus endereços de roaming de Wi-Fi.  
  
    -   **Arriscados**: esses devem ser quaisquer endereços IP que considerar arriscados. Eles podem incluir endereços IP suspeitos que você viu no passado, endereços IP em redes de seus concorrentes etc.  
  
    -   **VPN**: esses devem ser quaisquer endereços IP usados para funcionários remotos.  
  
    -   **Proxy de nuvem**: esse deve ser o endereço IP do seu proxy a nuvem.  
  
7.  Quando terminar, clique em **Criar**.  
  
     ![intervalo de newipaddress](./media/newipaddress-range.png "newipaddress range")  
  
##  <a name="a-nameadallommailsettingsa-personalize-your-experience"></a><a name="Adallom_mailsettings"></a> Personalizar sua experiência  
Na barra de menus, clique no ícone de configurações ![ícone de configurações](./media/settings-icon.png "settings icon") e selecione **Configurações de email** para definir os parâmetros para notificações de email enviadas do Cloud App Security para administradores que solicitam alertas e notificações enviadas para os usuários finais sobre violações em que estão envolvidos.  
  
![menu de configuração de email](./media/mail-setting-menu.png "mail setting menu")  
  
Configure o seguinte:  
  
1.  **Do endereço de email**: a conta de email que você deseja usar para enviar a notificação.  
  
     **Nome de exibição**: o nome a ser exibido no campo **De** da mensagem de email.  
  
     **Endereço de email para resposta**: a conta de email a ser usada para respostas à mensagem.  
  
     ![configuração de definições de email](./media/mail-settings-config.png "mail settings config")  
  
2.  Você pode usar um arquivo html para personalizar e criar as mensagens de email enviadas do sistema. O arquivo html usado para o modelo deve incluir o seguinte:  
  
    -   Todo modelo CSS deve estar embutido no modelo.  
  
    -   O modelo deve ter três espaços reservados não editáveis:  
  
         %%logo%% ‑ Uma URL para o logotipo da sua empresa que foi carregado na página Configuração geral  
  
         %%title%% ‑ Um espaço reservado para o título do email, conforme definido pela política.  
  
         %%content%% ‑ Um espaço reservado para o conteúdo que será incluído para os usuários finais, conforme definido pela política.  
  
     A seguir está um exemplo de modelo de email:  
  
    ```  
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
  
3.  Clique em **Carregar um modelo...** e selecione o arquivo que você criou.  
  
     Em seguida, clique em **Enviar um email de teste** para enviar um email de teste para você mesmo para ver um exemplo do modelo que você criou.  
     O email será enviado para a conta usada para fazer logon no portal. No email de teste, você poderá ver os campos de metadados, o modelo, o assunto do email, o título no corpo do email e o conteúdo.  
  
## <a name="single-signon"></a>Logon único  
O Cloud App Security é combinado a com o Azure Active Directory para atividades relacionadas ao licenciamento, provisionamento e autenticação. Para obter informações sobre como gerenciar o logon único, consulte a [Lista de compatibilidade de federação do Azure Active Directory: provedores de identidade de terceiros que podem ser usados para implementar o logon único](https://msdn.microsoft.com/library/azure/jj679342.aspx).  
  
## <a name="see-also"></a>Veja também  
[Configurar o Cloud Discovery](set-up-cloud-discovery.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Oct16_HO5-->



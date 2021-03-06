---
title: Conectar o Salesforce ao Cloud App Security
description: Este artigo fornece informações sobre como conectar o Salesforce ao Cloud App Security usando o conector de API para obter visibilidade e controle sobre o uso.
ms.date: 10/06/2019
ms.topic: how-to
ms.openlocfilehash: 45c1a74e860c155662d4e7ff66e16bea956b94e6
ms.sourcegitcommit: 40d17309b8729eb914ea91ba5fa7017340231488
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/29/2020
ms.locfileid: "97808939"
---
# <a name="connect-salesforce-to-microsoft-cloud-app-security"></a>Conectar o Salesforce ao Microsoft Cloud App Security

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Este artigo fornece instruções para conectar o Microsoft Cloud App Security à sua conta existente do Salesforce usando a API do conector de aplicativos. Essa conexão fornece visibilidade e controle sobre o uso do Salesforce. Para obter informações sobre como Cloud App Security protege o Salesforce, consulte [proteger o Salesforce](protect-salesforce.md).

## <a name="how-to-connect-salesforce-to-cloud-app-security"></a>Como conectar o Salesforce ao Cloud App Security

1. É recomendável ter uma conta do administrador de serviço dedicada para o Cloud App Security.

1. Confirme se a API REST está habilitada no Salesforce.

    Sua conta do Salesforce deve ser de uma das seguintes edições que incluem o suporte à API REST:

    **Performance**, **Enterprise**, **Unlimited** ou **Developer**.

    A edição **Professional** não tem a API REST por padrão, mas pode ser adicionada sob demanda.

    Verifique se sua edição tem a API REST disponível e habilitada da seguinte maneira:

    * Entre em sua conta do Salesforce e acesse a página **Configuração**.

    * Em **Gerenciar Usuários**, vá para a página **Perfis de Usuário**.

        ![perfis do Salesforce Manage Users](media/salesforce-manageusers-profiles.png)

    * Crie um novo perfil clicando em **Novo**.
    * Escolha o perfil que você acabou de criar para implantar o Cloud App Security e clique em **Editar**. Esse perfil será usado para a conta de serviço do Cloud App Security para configurar o conector do aplicativo.

         ![editar perfil do salesforce](media/salesforce-edit-profile.png)

    * Certifique-se de ter as seguintes caixas de seleção habilitadas:
      * **API Habilitada**
      * **Exibir todos os dados**
      * **Gerenciar Conteúdo CRM do Salesforce**
      * **Gerenciar usuários**
      * **[Consultar todos os arquivos](https://go.microsoft.com/fwlink/?linkid=2106480)**

      Se essas caixas de seleção não estiverem selecionadas, poderá ser necessário contatar a Salesforce para adicioná-las à sua conta.

1. Se sua organização tiver **Salesforce CRM Content** habilitado, certifique-se de que a conta administrativa atual o tenha habilitado também.

    1. Vá para a página de configuração do Salesforce.

        ![configuração do salesforce](media/salesforce-setup.png)

    1. No menu lateral, selecione **Gerenciar Usuários** e clique em **Usuários**.

        ![usuários do menu do salesforce](media/salesforce-menu-users.png)

    1. Selecione o usuário administrativo atual para seu usuário do Cloud App Security dedicado.

    1. Certifique-se de que a caixa de seleção **Usuário do Salesforce CRM Content** esteja marcada.

        Se ela não estiver selecionada, clique em **Editar** e, em seguida, marque a caixa de seleção.

        ![usuário do conteúdo crm do salesforce](media/salesforce-crm-content-user.png)

    1. Em **configurações de sessão**, verifique se a caixa de seleção selecionar **sessões de bloqueio para o endereço IP da qual se originou** **não** está marcada.

        ![configurações de sessão do Salesforce](media/salesforce-setup-session-settings.png)

    1. Clique em **Save** (Salvar).

1. No console do Cloud App Security, clique em **Investigar** e em **Aplicativos conectados**.

1. Na página **Conectores de aplicativos**, clique no botão de mais antes de **Salesforce**.

    ![conectar o salesforce](media/connect-salesforce.png)

1. Na página de configurações do Salesforce, na guia API, clique em **Seguir este link**, dependendo de qual instância que você deseja instalar.

1. Isso abre a página de entrada do Salesforce. Insira suas credenciais para permitir que o Cloud App Security acesse o aplicativo do Salesforce da sua equipe.

    ![entrada do Salesforce](media/salesforce-logon.png)

1. O Salesforce perguntará se você deseja permitir que o Cloud App Security acesse o log de atividades e as informações da sua equipe e realize quaisquer atividades como qualquer membro da equipe. Para continuar, clique em **Permitir**.

1. Neste ponto, você receberá uma notificação de êxito ou de falha em relação à implantação. O Cloud App Security agora está autorizado no Salesforce.com.

1. De volta ao console do Cloud App Security, você deverá ver a mensagem indicando que o Salesforce foi conectado com êxito.

1. Certifique-se de que a conexão foi bem-sucedida clicando em **Testar API**.

    O teste pode levar alguns minutos. Depois de receber uma notificação de êxito, clique em **Concluído**.

Após conectar o Salesforce, você receberá Eventos da seguinte maneira: gatilhos a partir do momento da conexão, Eventos de logon e Trilha de Auditoria de Instalação por 60 dias antes da conexão, EventMonitoring 30 dias ou um dia antes, dependendo da sua licença do Salesforce EventMonitoring. A API do Cloud App Security se comunica diretamente com as APIs disponíveis no Salesforce. Como o Salesforce limita o número de chamadas à API que ele pode receber, o Cloud App Security leva isso em consideração e respeita a limitação. As APIs do Salesforce enviam cada resposta com um campo para os contadores de API, incluindo total disponível e restante. O Cloud App Security calcula isso em um percentual e garante que sempre haja 10% de chamadas à API disponíveis restantes.

> [!NOTE]
> A limitação do Cloud App Security é calculada apenas em suas próprias chamadas à API com o Salesforce, não com os outros aplicativos que fazem chamadas à API com o Salesforce.
> Limitar as chamadas à API devido à limitação poderá diminuir a taxa em que os dados são incluídos no Cloud App Security, mas normalmente voltará ao normal durante a noite.

Eventos do Salesforce são processados pelo Cloud App Security da seguinte maneira:

* Eventos de entrada a cada 15 minutos
* Trilhas de auditoria de instalação a cada 15 minutos
* Logs de eventos a cada 1 hora. Para saber mais sobre os eventos do Salesforce, veja [Usando o monitoramento de eventos](https://developer.salesforce.com/docs/atlas.en-us.api_rest.meta/api_rest/using_resources_event_log_files.htm).

Se você tiver problemas para conectar o aplicativo, consulte [Solucionando problemas de conectores de aplicativos](troubleshooting-api-connectors-using-error-messages.md).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]

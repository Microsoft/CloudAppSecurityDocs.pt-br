---
title: Conectar o ServiceNow ao Cloud App Security
description: Este artigo fornece informações sobre como conectar seu aplicativo ServiceNow para Cloud App Security usando o conector de API para visibilidade e controle sobre o uso.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 6/24/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: a1214e0067d5c83ff001ff6c0e8a27fb227bc7e9
ms.sourcegitcommit: 9fe879ce7f07933866191724de5f108f43e3f923
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/24/2020
ms.locfileid: "77566836"
---
# <a name="connect-servicenow-to-microsoft-cloud-app-security"></a>Conectar o ServiceNow ao Microsoft Cloud App Security

*Aplica-se a: Microsoft Cloud App Security*

Este artigo fornece instruções para conectar Microsoft Cloud App Security à sua conta do ServiceNow existente usando a API do conector de aplicativo. Essa conexão fornece visibilidade e controle sobre o uso do ServiceNow. Para obter informações sobre como Cloud App Security protege o ServiceNow, consulte [proteger o servicenow](protect-servicenow.md).

> [!NOTE]
> É recomendável implantar o ServiceNow usando tokens de aplicativo OAuth, disponível para o Fuji e versões posteriores (consulte a documentação relevante do [ServiceNow](https://wiki.servicenow.com/index.php?title=OAuth_Applications#gsc.tab=0).
> Para versões anteriores, um [modo de conexão herdado](#legacy-servicenow-connection) está disponível com base no usuário/senha. O nome de usuário/senha fornecidos são usados somente para geração de token de API e não são salvos após o processo de conexão inicial.

> [!NOTE]
> O Cloud App Security dá suporte às versões do ServiceNow, Kingston, Eureka, Fiji, Geneva, Helsinque, Istambul, Londres e Madri. Para conectar o ServiceNow com o Cloud App Security, você deve ter o **administrador** da função e verificar se a instância do ServiceNow dá suporte ao acesso à API.  Para obter mais informações, consulte a [documentação do produto ServiceNow](https://wiki.servicenow.com/index.php?title=Base_System_Roles#gsc.tab=0).

## <a name="how-to-connect-servicenow-to-cloud-app-security-using-oauth"></a>Como conectar o ServiceNow ao Cloud App Security usando o OAuth

1. Entre com uma conta de administrador para sua conta do ServiceNow.

    > [!NOTE]
    > O nome de usuário/senha fornecidos são usados somente para geração de token de API e não são salvos após o processo de conexão inicial.

2. Na barra de pesquisa do **navegador de filtro** , digite **OAuth** e selecione **registro de aplicativo**.

3. Na barra de menus **registros de aplicativos** , clique em **novo** para criar um novo perfil OAuth.

    ![Novo perfil OAuth do ServiceNow](media/servicenow-app-registry.png)

4. Em **que tipo de aplicativo OAuth?**, clique em **criar um ponto de extremidade de API OAuth para clientes externos**.

    ![Tipo OAuth do ServiceNow](media/servicenow-oauth-app-type.png)

5. Em registros do aplicativo, preencha o **novo registro** nos seguintes campos:

    - **Nome** campo, nomeie o novo perfil OAuth, por exemplo, CloudAppSecurity.

    - A **ID do cliente** é gerada automaticamente. Copie essa ID, você precisa colá-la em Cloud App Security para concluir a conexão.

    - No campo **segredo do cliente** , insira uma cadeia de caracteres. Se deixado em branco, um segredo aleatório será gerado automaticamente. Copie e salve-o para mais tarde.

    - Aumente o tempo de **vida do token de acesso** para pelo menos 3.600.

    - Clique em **Enviar**.

    ![IDs de perfil do ServiceNow](media/servicenow-profile-ids.png)

6. No portal de Cloud App Security, clique em **investigar** e em **aplicativos conectados**.

7. Na página **conectores de aplicativos** , clique no botão de adição e, em seguida, **ServiceNow**.

    ![conectar o ServiceNow](media/connect-servicenow.png "conectar o ServiceNow")

8. No pop-up, adicione a ID de usuário do ServiceNow, a senha, a URL da instância, a ID do cliente e o segredo do cliente nas caixas apropriadas. Para localizar sua ID de usuário do ServiceNow, no portal do ServiceNow, vá para **usuários** e localize seu nome na tabela.

    ![ID de usuário do ServiceNow](media/servicenow-userid.png)

9. Clique em **Conectar**.

    ![ServiceNow conectar ao CAS](media/servicenow-portal-connect.png "Conexão do ServiceNow no portal")

10. Verifique se a conexão foi bem-sucedida clicando em **testar agora**.

    O teste pode levar alguns minutos. Depois de receber um aviso de êxito, clique em **fechar**.

Depois de conectar o ServiceNow, você receberá eventos por 7 dias antes da conexão.

## <a name="legacy-servicenow-connection"></a>Conexão do ServiceNow herdada

Para conectar o ServiceNow com o Cloud App Security, você deve ter permissões de nível de administrador e verificar se a instância do ServiceNow dá suporte ao acesso à API.

1. Entre com uma conta de administrador para sua conta do ServiceNow.

2. Crie uma nova conta de serviço para Cloud App Security e anexe a função de administrador à conta recém-criada.

3. Verifique se o plug-in da API REST está ativado.

    ![Conta do ServiceNow](media/servicenow-account.png "Conta do ServiceNow")

4. No portal de Cloud App Security, clique em **investigar** e em **aplicativos aprovados**.

5. Na linha ServiceNow, clique em **conectar** na coluna **status do conector de aplicativo** ou clique no botão **conectar um aplicativo** e, em seguida, **ServiceNow**.

   ![conectar o ServiceNow](media/connect-servicenow.png "conectar o ServiceNow")

6. Na página Configurações do ServiceNow, na guia API, adicione a ID de usuário, a senha e a URL da instância do ServiceNow nas caixas apropriadas.

7. Clique em **Conectar**.

    ![Senha de atualização do ServiceNow](media/servicenow-update-password.png "Senha de atualização do ServiceNow")

8. Certifique-se de que a conexão foi bem-sucedida clicando em **Testar API**.

    O teste pode levar alguns minutos. Depois de receber um aviso de êxito, clique em **fechar**.

Depois de conectar o ServiceNow, você receberá eventos por 7 dias antes da conexão.

Se você tiver problemas para conectar o aplicativo, consulte [Solucionando problemas de conectores de aplicativos](troubleshooting-api-connectors-using-error-messages.md).

## <a name="next-steps"></a>{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}

> [!div class="nextstepaction"]
> [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]

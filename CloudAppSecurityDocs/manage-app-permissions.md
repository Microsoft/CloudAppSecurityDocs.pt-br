---
title: Controlar quais aplicativos OAuth de nuvem de terceiros obtêm permissões-Cloud App Security | Microsoft Docs
description: Este artigo fornece informações sobre como você pode controlar, proibir e permitir aplicativos OAuth de terceiros.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 9/1/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 37b4f17539b0d160e8650f5478741f0941e50648
ms.sourcegitcommit: 4f3883a9e85d0aaf2802b10433b221c3f1838d88
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79285280"
---
# <a name="manage-oauth-apps"></a>Gerenciar aplicativos OAuth

*Aplica-se a: Microsoft Cloud App Security*

Muitos aplicativos de produtividade de terceiros que podem ser instalados por usuários empresariais em sua organização solicitam permissão para acessar informações e dados do usuário e entrar em nome do usuário em outros aplicativos de nuvem, como o Office 365, G Suite e Salesforce. Quando os usuários instalam esses aplicativos, eles geralmente clicam em aceitar sem revisar detalhadamente os detalhes no prompt, incluindo a concessão de permissões para o aplicativo. Esse problema é composto pelo fato de que pode não haver Insight suficiente para avaliar o risco de segurança de um aplicativo contra o benefício de produtividade que ele fornece. Como aceitar permissões de aplicativo de terceiros é um risco de segurança em potencial para sua organização, monitorando as permissões do aplicativo que os usuários concedem fornece a visibilidade e o controle necessários para proteger seus usuários e seus aplicativos. As permissões do aplicativo Microsoft Cloud App Security permitem que você veja quais aplicativos OAuth instalados pelo usuário têm acesso aos dados do Office 365, aos dados do G Suite e aos dados do Salesforce. Cloud App Security informa quais permissões os aplicativos têm e quais usuários concederam a esses aplicativos acesso às suas contas do Office 365, G Suite e Salesforce. As permissões de aplicativo ajudam você a decidir quais aplicativos você permite que os usuários acessem e quais você deseja proibir.

Para obter mais informações sobre a investigação de aplicativos OAuth, consulte [investigar aplicativos OAuth arriscados](investigate-risky-oauth.md).

## <a name="working-with-the-oauth-apps-page"></a>Trabalhando com a página de aplicativos OAuth

A página **OAuth** exibe informações sobre permissões de aplicativo em seus aplicativos conectados.

Para acessar a guia OAuth:

No portal de Cloud App Security, clique em **investigar**e, em seguida, em **aplicativos OAuth**.

![permissões de aplicativo](media/app-permissions.png)

A página aplicativos OAuth fornece as seguintes informações sobre cada aplicativo OAuth que recebeu permissões:

|Item|O que significa|Aplica-se a|
|-------|-------|-------|
|Ícone básico na barra de consulta do aplicativo  |Alterne para a consulta no modo de exibição básico.|Office 365, G Suite, Salesforce|
|Ícone avançado na barra de consulta do aplicativo  |Alterne para a consulta na exibição avançada.|Office 365, G Suite, Salesforce|
|Ícone abrir ou fechar todos os detalhes na lista de aplicativos  |Exiba mais ou menos detalhes sobre cada aplicativo.|
|Ícone exportar na lista de aplicativos  |Exporte um arquivo CSV que contém uma lista de aplicativos, número de usuários para cada aplicativo, permissões associadas ao nível do aplicativo, nível de permissões, estado do aplicativo e uso da Comunidade.|Office 365, G Suite, Salesforce|
|Aplicativo|Nome do aplicativo. Selecione o nome para exibir mais informações, incluindo a descrição, o Publicador (para o Office 365), o site do aplicativo e a ID.|Office 365, G Suite, Salesforce|
|Autorizado por|O número de usuários que autorizaram este aplicativo a acessar a conta de seu aplicativo e concedeu as permissões de aplicativo. Selecione o número para exibir mais informações, incluindo uma lista de emails do usuário e se um administrador consentiu o aplicativo anteriormente.|Office 365, G Suite, Salesforce|
|Nível de Permissões  |O ícone de nível de permissões e o texto que indica alto, médio ou baixo. O nível indica a quantidade de acesso que esse aplicativo tem aos dados do aplicativo. Por exemplo, baixo pode indicar que o aplicativo só acessa o nome e o perfil do usuário. Selecione o nível para exibir mais informações, incluindo as permissões concedidas ao aplicativo, ao uso da Comunidade ou à atividade relacionada no [log de governança](governance-actions.md).|Pacote do Office 365, G|
|Estado do aplicativo|Um administrador pode marcar um aplicativo como aprovado, banido ou deixar como não determinado.|Office 365, G Suite, Salesforce|
|Uso da Comunidade|Mostra o quão popular o aplicativo está em todos os seus usuários (comum, incomum, raro)|Office 365, G Suite, Salesforce|
|Último autorizado|A data mais recente na qual um usuário concedeu permissões para este aplicativo.|Office 365, Salesforce|
|Publisher|O nome do fornecedor que fornece o aplicativo.|Office 365|
|Última utilização|A data mais recente na qual esse aplicativo foi usado por qualquer pessoa em sua organização.|Salesforce|

## <a name="ban-or-approve-an-app"></a>Proibir ou aprovar um aplicativo

1. Na página **aplicativos OAuth** , clique no aplicativo para abrir a gaveta do **aplicativo** para exibir mais informações sobre o aplicativo e as permissões que ele recebeu.

    - Clique no link **permissões** para exibir uma lista completa de permissões que foram concedidas ao aplicativo.
    - Em **uso da Comunidade**, você pode exibir o quão comum o aplicativo está em outras organizações.
    - Clique no link **atividade relacionada** para exibir as atividades listadas no log de governança relacionado a esse aplicativo.

2. Para proibir o aplicativo, clique no ícone de Ban no final da linha de aplicativo na tabela.

    ![ícone de proibir aplicativo](media/ban-app-icon.png)

    - Você pode escolher se deseja informar aos usuários que o aplicativo instalado e autorizado foi banido. A notificação permite que os usuários saibam que o aplicativo será desabilitado e não terão acesso ao aplicativo conectado. Se você não quiser que eles saibam, desmarque a caixa de seleção **notificar os usuários que receberam acesso a esse aplicativo banido** .
    - É recomendável permitir que os usuários do aplicativo saibam que seu aplicativo está prestes a ser proibido de usar.

    ![proibir aplicativo](media/ban-app.png)

3. Digite a mensagem que você deseja enviar aos usuários do aplicativo na caixa Inserir uma mensagem de notificação personalizada. Clique em **proibir aplicativo** para enviar o email e proíba o aplicativo dos usuários do aplicativo conectado.

4. Para aprovar o aplicativo, clique no ícone aprovar no final da linha na tabela.

    ![aprovar aplicativo](media/approve-app.png)

    - O ícone fica verde e o aplicativo é aprovado para todos os usuários do aplicativo conectado.
    - Quando você marca um aplicativo como aprovado, não há nenhum efeito sobre o usuário final. Essa alteração de cor destina-se a ajudá-lo a ver os aplicativos que você aprovou para separá-los daqueles que você ainda não analisou.

## <a name="revoke-app-and-notify-user"></a>Revogar aplicativo e notificar usuário

Para o G Suite e o Salesforce, é possível revogar permissão para um aplicativo ou notificar o usuário de que ele deve alterar a permissão. Quando você revoga a permissão, ele remove todas as permissões que foram concedidas ao aplicativo em "aplicativos empresariais" no Azure AD.

1. Na página **aplicativos OAuth** , clique em três pontos no final da linha do aplicativo e selecione **notificar usuário**. Por padrão, o usuário será notificado da seguinte maneira: *você autorizou o aplicativo para acessar sua conta do G Suite. Este aplicativo está em conflito com a política de segurança da sua organização. Reconsidere a concessão ou a revogação das permissões que você deu a esse aplicativo em sua conta do G Suite. Para revogar o acesso ao aplicativo, acesse: https://security.google.com/settings/security/permissions?hl=en&pli=1 selecione o aplicativo e clique em ' revogar acesso ' na barra de menus à direita.* Você pode personalizar a mensagem que é enviada.
2. Você também pode revogar permissões para usar o aplicativo para o usuário. Clique no ícone no final da linha de aplicativo na tabela e selecione **revogar aplicativo**.

    ![revogar aplicativo](media/revoke-app.png)

## <a name="query-oauth-apps"></a>Consultar aplicativos OAuth

Você pode consultar aplicativos OAuth na exibição **básica** ou na exibição **avançada** . Selecione valores de um ou vários menus suspensos para exibir os aplicativos específicos no modo de exibição básico. Na exibição avançada, use a lista suspensa **selecionar um filtro** para restringir sua pesquisa. Adicione operadores, Equals ou não é igual a um valor selecionado para concluir a consulta.

- Escolha o ícone **Adicionar um filtro** para adicionar filtros adicionais para refinar ainda mais sua consulta. Os filtros são aplicados automaticamente e a lista de aplicativos é atualizada.

- Escolha o ícone **remover um filtro** ao lado do filtro para remover os filtros.

## <a name="oauth-app-auditing"></a>Auditoria de aplicativo OAuth

O Cloud App Security audita todas as atividades de autorização do OAuth para fornecer monitoramento e investigação abrangentes das atividades executadas. Você também pode exportar os detalhes de usuários que autorizam um aplicativo OAuth específico, fornecendo informações adicionais sobre os usuários, que você pode usar para análise posterior.

Para exportar o log, execute as seguintes etapas:

1. Na página **aplicativos OAuth** , na linha em que o aplicativo relevante aparece, em **autorizado por**, clique no link mostrando o número de usuários que autorizaram o aplicativo.

1. Na janela pop-up, clique em **Exportar**.

    ![Captura de tela mostrando a exportação da auditoria de aplicativo OAuth](media/oauth-export-users.png)

## <a name="send-feedback"></a>Enviar comentários

Se houver um aplicativo OAuth descoberto em sua organização que pareça mal-intencionado, você poderá enviar os comentários da equipe de Cloud App Security para nos informar. Esse recurso permite que você faça parte de nossa comunidade de segurança e aprimore a pontuação de risco do aplicativo OAuth e a análise.

1. Na página **aplicativos OAuth** , clique em três pontos no final da linha de aplicativo e selecione aplicativo de **relatório**.

    ![aplicativo de relatório](media/report-app.png)
2. Na tela **relatar este aplicativo** , você pode selecionar se deseja relatar o aplicativo como mal-intencionado ou relatar outro problema com a maneira como Cloud app Security percebe o aplicativo. Por exemplo, você pode usar o **Editor incorreto**, **permissões incorretas**ou **outras**. Os dados enviados serão usados para atualizar a pontuação de risco do aplicativo e outras análises sobre o aplicativo.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]

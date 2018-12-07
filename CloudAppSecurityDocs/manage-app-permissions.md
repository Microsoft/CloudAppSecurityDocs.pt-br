---
title: Controlar quais aplicativos OAuth de nuvem de terceiros recebem permissões | Microsoft Docs
description: Este artigo fornece informações sobre como você pode controlar, vetar e autorizar permissões de aplicativos OAuth de terceiros.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/16/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 137e0630-5440-4c49-bfe4-48bbc64575e2
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 7c528a57799d7a00c0f54d2e798dc0f5c281fd13
ms.sourcegitcommit: cae782d508db9d1a7c0c362e9a23e83f74d48b21
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2018
ms.locfileid: "52743566"
---
# <a name="manage-oauth-apps"></a>Gerenciar aplicativos OAuth

*Aplica-se ao: Microsoft Cloud App Security*

Muitos aplicativos de produtividade de terceiros, que podem ser instalados por usuários corporativos da sua organização, solicitam permissão para acessar dados e informações de usuário e entrar, em nome do usuário, em outros aplicativos de nuvem, como o Office 365, o G Suite e o Salesforce. Quando os usuários instalam esses aplicativos, eles geralmente clicam em aceitar sem examinar atentamente os detalhes na solicitação, incluindo a concessão de permissões para o aplicativo. Esse problema mistura-se ao fato de que o TI pode não ter informações suficientes para avaliar o risco de segurança de um aplicativo em relação aos benefícios de produtividade que ele oferece. Devido ao fato de que aceitar permissões de aplicativo de terceiros seja um risco de segurança para sua organização, monitorar as permissões de aplicativo que seus usuários concedem oferece a visibilidade e controle necessários para proteger os usuários e seus aplicativos. As permissões de aplicativo do Microsoft Cloud App Security permitem que você veja quais aplicativos OAuth instalados pelo usuário têm acesso a dados do Office 365, dados do G Suite e dados do Salesforce. Cloud App Security informa quais permissões os aplicativos têm e quais usuários concederam a esses aplicativos acesso às suas contas do Office 365, G Suite e Salesforce. As permissões de aplicativo ajudam na decisão de quais aplicativos você permite que os usuários acessem e quais você deseja vetar.

## <a name="working-with-the-oauth-apps-page"></a>Trabalhando com a página de aplicativos de OAuth

A página **OAuth** exibe informações sobre permissões de aplicativo em seus aplicativos conectados.

Para acessar a guia OAuth:

No portal do Cloud App Security, clique em **Investigar** e em **Aplicativos OAuth**.


 ![permissões de aplicativo](./media/app-permissions.png)

A página de aplicativos OAuth fornece as seguintes informações sobre cada aplicativo OAuth que recebeu permissões:

|Item|O que significa|Aplica-se a|
|-------|-------|-------|
|Ícone básico na barra de consulta de aplicativo  |Alterne para a consulta no modo de exibição básico.|Office 365, G Suite, Salesforce|
|Ícone Avançado na barra de consulta de aplicativo  |Alterne para a consulta no modo de exibição Avançado.|Office 365, G Suite, Salesforce|
|Abrir ou fechar todos os ícones de detalhes na lista de aplicativos  |Exiba mais ou menos detalhes sobre cada aplicativo.|
|Ícone de exportar na lista de aplicativos  |Exporte um arquivo CSV que contém uma lista de aplicativos, o número de usuários para cada aplicativo, as permissões associadas com o aplicativo, o nível das permissões, estado do aplicativo e nível de uso da comunidade.|Office 365, G Suite, Salesforce|
|Aplicativo|Nome do aplicativo. Selecione o nome para exibir mais informações, incluindo a descrição, o editor (para Office 365), o site do aplicativo e a ID.|Office 365, G Suite, Salesforce|
|Autorizado por|O número de usuários que autorizaram esse aplicativo a acessar suas contas de aplicativo e concederam permissões ao aplicativo. Selecione o número para exibir mais informações, incluindo uma lista de emails de usuário e se um administrador consentiu ou não com o aplicativo anteriormente.|Office 365, G Suite, Salesforce|
|Nível de permissões  |O ícone de nível de permissões e o texto que indica Alto, Médio ou Baixo. O nível indica quanto acesso esse aplicativo tem aos dados do aplicativo. Por exemplo, Baixo pode indicar que o aplicativo acessa apenas nome e o perfil do usuário. Selecione o nível para exibir mais informações, incluindo as permissões concedidas ao aplicativo, uso da comunidade ou a atividade relacionada no [Log de governança](governance-actions.md).|Office 365, G Suite|
|Estado do aplicativo|Um administrador pode marcar um aplicativo como aprovado, vetado ou deixar como indeterminado.|Office 365, G Suite, Salesforce|
|Uso da comunidade|Mostra quão popular o aplicativo é entre todos os seus usuários (comum, incomum, raro)|Office 365, G Suite, Salesforce|
|Última autorização|A data mais recente em que um usuário concedeu permissões para este aplicativo.|Office 365, Salesforce|
|Editor|O nome do fornecedor que oferece o aplicativo.|Office 365|
|Usado pela última vez|A data mais recente em que este aplicativo foi usado por alguém em sua organização.|Salesforce|


## <a name="ban-or-approve-an-app"></a>Vetar ou aprovar um aplicativo

1. Na página de **Aplicativos OAuth**, clique no aplicativo para abrir a **Gaveta de aplicativo** para exibir mais informações sobre o aplicativo e as permissões que foram concedida a ele.
   
   - Clique no link **Permissões** para exibir uma lista completa das permissões que foram concedidas ao aplicativo. 
   - Em **Uso da comunidade**, você pode exibir o quão comum o aplicativo é em outras organizações.  
   - Clique no link **Atividade relacionada** para exibir as atividades que estão listadas no log de governança relacionado a esse aplicativo.

2. Para vetar o aplicativo, clique no ícone de vetar no final da linha do aplicativo na tabela.
   
     ![ícone de vetar aplicativo](./media/ban-app-icon.png) 

    - Você pode escolher se deseja informar os usuários de que o aplicativo instalado e autorizado foi vetado. A notificação permite que os usuários saibam que o aplicativo será desabilitado e eles não terão acesso ao aplicativo conectado. Se não quiser que eles saibam, cancele a seleção de **Notificar os usuários que concederam acesso a esse aplicativo vetado** na caixa de diálogo. 
    - Recomendamos informar os usuários do aplicativo de que ele está prestes a ter o uso vetado.

      ![vetar aplicativo](./media/ban-app.png)

3. Digite a mensagem que você deseja enviar para os usuários do aplicativo em Inserir uma caixa de mensagem de notificação personalizada. Clique em **Vetar aplicativo** para enviar o email e vetar o aplicativo dos usuários do aplicativo conectado.


4. Para aprovar o aplicativo, clique no ícone de aprovar no final da linha na tabela. 

   ![aprovar aplicativo](./media/approve-app.png) 

   - O ícone fica verde e o aplicativo é aprovado para todos os usuários do aplicativo conectado.
   - Quando você marca um aplicativo como aprovado, não há nenhum efeito sobre o usuário final. Essa alteração de cor destina-se a ajudá-lo a ver os aplicativos que você aprovou para separá-los daqueles que você ainda não examinou.



## <a name="revoke-app-and-notify-user"></a>Revogar aplicativo e notificar o usuário

Para G Suite e Salesforce, é possível revogar a permissão para um aplicativo ou notificar o usuário de que ele deve alterar a permissão. 

1. Na página **Aplicativos OAuth**, clique nos três pontos no final da linha de aplicativo e selecione **Notificar usuário**. Por padrão, o usuário será notificado da seguinte maneira: *Você autorizou o aplicativo a acessar sua conta G Suite. Este aplicativo está em conflito com a política de segurança da sua organização. Reconsidere conceder ou revogar as permissões que você deu a esse aplicativo em sua conta G Suite. Para revogar o acesso ao aplicativo, vá para: https://security.google.com/settings/security/permissions?hl=en&pli=1 Selecione o aplicativo e clique em 'Revogar o acesso' na barra de menus à direita.* Você pode personalizar a mensagem que é enviada.
2. Você também pode revogar permissões para usar o aplicativo para o usuário. Clique no ícone no final da linha de aplicativo na tabela e selecionando **Revogar aplicativo**. 

   ![revogar aplicativo](./media/revoke-app.png)

## <a name="query-oauth-apps"></a>Aplicativos OAuth de consulta

Você pode consultar os aplicativos OAuth na exibição **Básica** ou na exibição **Avançada**. selecione valores de uma ou várias listas suspensas para exibir aplicativos específicos na exibição Básica. Na modo de exibição avançado, use a lista suspensa **Selecionar um filtro** para restringir sua pesquisa. Adicione operadores, é igual a ou não é igual a um valor selecionado para concluir a sua consulta.

- Selecione o ícone **Adicionar um filtro** para adicionar mais filtros para refinar sua consulta. Os filtros são aplicados automaticamente e a lista de aplicativos é atualizada.

- Selecione o ícone **Remover um filtro** ao lado do filtro para remover os filtros.

## <a name="send-feedback"></a>Enviar comentários

Se algum aplicativo OAuth que pareça mal-intencionado for descoberto na sua organização, informe a equipe do Cloud App Security. Esse recurso permite que você participe da nossa comunidade de segurança e melhore a análise e a pontuação de risco do aplicativo OAuth.
1. Na página **Aplicativos OAuth**, clique nos três pontos no final da linha de aplicativo e selecione **Relatar aplicativo**.  

   ![reportar aplicativo](./media/report-app.png)
2. Na tela **Relatar este aplicativo**, você pode selecionar se deseja relatar o aplicativo como mal-intencionado ou relatar outro problema com a maneira como o Cloud App Security percebe o aplicativo. Por exemplo, você pode usar **Editor incorreto**, **Permissões incorretas** ou **Outro**. Os dados que você envia são usados para atualizar a pontuação de risco do aplicativo, bem como outras análises sobre ele.

## <a name="next-steps"></a>Próximas etapas

[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)   

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  

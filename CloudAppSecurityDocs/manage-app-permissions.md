---
title: "Controlar quais aplicativos de nuvem de terceiros recebem permissões | Microsoft Docs"
description: "Este artigo fornece informações sobre como você pode controlar, vetar e autorizar permissões de aplicativo de terceiros."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/15/2018
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 137e0630-5440-4c49-bfe4-48bbc64575e2
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 6d6daa74269057595a34db7813d0cd6ba5eaf947
ms.sourcegitcommit: 458e936e1ac548eda37e9bf955b439199bbdd018
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2018
---
# <a name="manage-app-permissions"></a>Gerenciar permissões de aplicativo
Muitos aplicativos de produtividade de terceiros, que podem ser instalados por usuários corporativos da sua organização, solicitam permissão para acessar dados e informações de usuário e entrar, em nome do usuário, em outros aplicativos de nuvem, como o Office 365, o G Suite e o Salesforce.  Quando os usuários instalam esses aplicativos, eles geralmente clicam em aceitar sem examinar atentamente os detalhes na solicitação, incluindo a concessão de permissões para o aplicativo.  Esse problema mistura-se ao fato de que o TI pode não ter informações suficientes para avaliar o risco de segurança de um aplicativo em relação aos benefícios de produtividade que ele oferece. Devido ao fato de que aceitar permissões de aplicativo de terceiros seja um risco de segurança para sua organização, monitorar as permissões de aplicativo que seus usuários concedem oferece a visibilidade e controle necessários para proteger os usuários e seus aplicativos. As permissões do aplicativo Cloud App Security habilitam a visualização de quais aplicativos instalados pelo usuário têm acesso a dados do Office 365, do G Suite e do Salesforce, quais permissões os aplicativos têm e quais usuários concederam a esses aplicativos acesso às suas contas do Office 365, do G Suite e do Salesforce. As permissões de aplicativo ajudam na decisão de quais aplicativos você permite que os usuários acessem e quais você deseja vetar.


## <a name="working-with-the-app-permissions-page"></a>Trabalhando com a página de permissões de aplicativo

A página **Permissões de aplicativo** exibe informações sobre permissões de aplicativo em seus aplicativos conectados.

Para acessar a guia de Permissões de aplicativo:

No portal do Cloud App Security, clique em **Investigar** e em **Permissões de aplicativo**.


 ![permissões de aplicativo](./media/app-permissions.png)

A página de Permissões de aplicativo fornece as seguintes informações sobre cada aplicativo de terceiros, aos quais foram concedidas permissões:

|Item|O que significa|Aplica-se a|
|-------|-------|-------|
|Ícone básico na barra de consulta de aplicativo  |Selecione esta opção para mudar para a consulta no modo de exibição básico.|Office 365, G Suite, Salesforce|
|Ícone Avançado na barra de consulta de aplicativo  |Selecione esta opção para mudar para a consulta no modo de exibição Avançado.|Office 365, G Suite, Salesforce|
|Abrir ou fechar todos os ícones de detalhes na lista de aplicativos  |Selecione esse ícone para exibir mais ou menos detalhes sobre cada aplicativo.|
|Ícone de exportar na lista de aplicativos  |Selecione esse ícone para exportar um arquivo CSV que contém uma lista de aplicativos, o número de usuários para cada aplicativo, as permissões associadas com o aplicativo, o nível das permissões, estado do aplicativo e nível de uso da comunidade.|Office 365, G Suite, Salesforce|
|Aplicativo|Nome do aplicativo. Selecione o nome para exibir mais informações, incluindo a descrição, o editor (para Office 365), o site do aplicativo e a ID.|Office 365, G Suite, Salesforce|
|Autorizado por|O número de usuários que autorizaram esse aplicativo a acessar suas contas de aplicativo e concederam permissões ao aplicativo. Selecione o número para exibir mais informações, incluindo uma lista de emails de usuário e se um administrador houver ou não consentido o aplicativo anteriormente.|Office 365, G Suite, Salesforce|
|Nível de permissões  |O ícone de nível de permissões e o texto que indica Alto, Médio ou Baixo. O nível indica quanto acesso esse aplicativo tem aos dados do aplicativo. Por exemplo, Baixo pode indicar que o aplicativo acessa apenas nome e o perfil do usuário. Selecione o nível para exibir mais informações, incluindo as permissões concedidas ao aplicativo, uso da comunidade ou a atividade relacionada no [Log de governança](governance-actions.md).|Office 365, G Suite|
|Estado do aplicativo|Um administrador pode marcar um aplicativo como aprovado, vetado ou deixar como indeterminado.|Office 365, G Suite, Salesforce|
|Uso da comunidade|Selecione esta opção se você quiser saber o nível de popularidade do aplicativo entre todos os usuários (comum, incomum, raro)|Office 365, G Suite, Salesforce|
|Última autorização|A data mais recente em que um usuário concedeu permissões para este aplicativo.|Office 365, Salesforce|
|Editor|O nome do fornecedor que oferece o aplicativo.|Office 365|
|Usado pela última vez|A data mais recente em que este aplicativo foi usado por alguém em sua organização.|Salesforce|


## <a name="ban-or-approve-an-app"></a>Vetar ou aprovar um aplicativo
1. Na página de Permissões do aplicativo, clique no aplicativo para abrir a Gaveta de aplicativo para exibir mais informações sobre o aplicativo e as permissões que foram concedida a ele. Você pode clicar no link de Permissões para exibir uma lista completa das permissões que foram concedidas ao aplicativo. Em Uso da comunidade, você pode exibir o quão comum o aplicativo é em outras organizações. Você também pode clicar no link Relacionar atividade para exibir as atividades que estão listadas no log de governança relacionado a esse aplicativo.
2. Para vetar o aplicativo, clique no ícone de vetar no final da linha do aplicativo na tabela. <br></br>
 ![ícone Vetar aplicativo](./media/ban-app-icon.png) <br></br>
Ao vetar um aplicativo, você pode escolher se deseja que os usuários saibam que o aplicativo previamente instalado e autorizado foi vetado, será desabilitado e não terá acesso ao aplicativo conectado. Se não quiser que eles saibam, cancele a seleção de Notificar os usuários que concederam acesso a esse aplicativo vetado na caixa de diálogo de Vetar o aplicativo.

    ![vetar aplicativo](./media/ban-app.png)
> [!Note]
> É recomendável que você informe os usuários do aplicativo que ele está prestes a ter o uso vetado.

3. Para aprovar o aplicativo, clique no ícone de aprovar no final da linha na tabela. <br></br>
 ![aprovar aplicativo](./media/approve-app.png) <br></br>
O ícone fica verde e o aplicativo é aprovado para todos os usuários do aplicativo conectado.
> [!Note]
> Quando você marca um aplicativo como aprovado não há nenhum efeito sobre o usuário final. Isso serve apenas para ajudá-lo a marcar visualmente os aplicativos que você aprovou para separá-los daqueles que você ainda não examinou.

3. Digite a mensagem que você deseja enviar para os usuários do aplicativo na caixa Digite uma mensagem de notificação personalizada e atualize o endereço de email 'responder para', se for necessário. 
 Clique em **Vetar aplicativo** para enviar o email e vetar o aplicativo dos usuários do aplicativo conectado.

## <a name="revoke-app-and-notify-user"></a>Revogar aplicativo e notificar o usuário

Para G Suite e Salesforce, é possível revogar a permissão para um aplicativo ou para notificar o usuário que isso deve foi feito. 

1. Na página de Permissões de aplicativo, clique em três pontos no final da linha de aplicativo e selecione **Notificar usuário**. Por padrão, o usuário será notificado da seguinte maneira: *Você autorizou o aplicativo Adallom Google Protector a acessar sua conta G Suite. Este aplicativo está em conflito com a política de segurança da sua organização. Reconsidere conceder ou revogar as permissões que você deu a esse aplicativo em sua conta G Suite. Para revogar o acesso ao aplicativo, acesse: https://security.google.com/settings/security/permissions?hl=en&pli=1, selecione o aplicativo e clique em 'Revogar acesso' na barra de menus à direita.* Você pode personalizar a mensagem que é enviada.
2. Você também pode revogar permissões para usar o aplicativo para o usuário, clicando no ícone no final da linha do aplicativo na tabela e selecionando **Revogar aplicativo**. 

 ![revogar aplicativo](./media/revoke-app.png)

## <a name="query-app-permissions"></a>Consultar permissões de aplicativo

Você pode consultar as permissões de aplicativo no modo de exibição **Básico** ou **Avançado**. No modo de exibição básico, selecione valores de uma ou várias listas suspensas para exibir aplicativos específicos. Na modo de exibição avançado, use a lista suspensa **Selecionar um filtro** para restringir sua pesquisa. Adicione operadores, é igual a ou não é igual a um valor selecionado para concluir a sua consulta.

- Selecione o ícone **Adicionar um filtro** para adicionar filtros adicionais para refinar sua consulta. Os filtros são aplicados automaticamente e a lista de aplicativos é atualizada adequadamente.

- Selecione o ícone **Remover um filtro** ao lado do filtro para remover os filtros.


## <a name="see-also"></a>Consulte Também  
[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)   

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
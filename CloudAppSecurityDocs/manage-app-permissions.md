---
title: "Controlar quais aplicativos de nuvem de terceiros recebem permissões | Microsoft Docs"
description: "Este artigo fornece informações sobre como você pode controlar, vetar e autorizar permissões de aplicativo de terceiros."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/23/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 137e0630-5440-4c49-bfe4-48bbc64575e2
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 3866ae5606fd2add90338ac58a49edf646aa87c5
ms.sourcegitcommit: 355226ee21981563066d637e7db0bff0d53c2da6
translationtype: HT
---
# <a name="manage-app-permissions"></a>Gerenciar permissões de aplicativo
Muitos aplicativos de produtividade de terceiros, que podem ser instalados por usuários corporativos da sua organização, solicitam permissão para acessar dados e informações de usuário e entrar, em nome do usuário, em outros aplicativos de nuvem, como o Office 365.  Quando os usuários instalam esses aplicativos, eles geralmente clicam em aceitar sem examinar atentamente os detalhes na solicitação, incluindo a concessão de permissões para o aplicativo.  Esse problema mistura-se ao fato de que o TI pode não ter informações suficientes para avaliar o risco de segurança de um aplicativo em relação aos benefícios de produtividade que ele oferece. Devido ao fato de que aceitar permissões de aplicativo de terceiros seja um risco de segurança para sua organização, monitorar as permissões de aplicativo que seus usuários concedem oferece a visibilidade e controle necessários para proteger os usuários e seus aplicativos. As permissões do aplicativo Cloud App Security habilitam a visualização de quais aplicativos instalados pelo usuário têm acesso a dados do Office 365, quais permissões os aplicativos têm e quais usuários concederam a esses aplicativos acesso às suas contas do Office 365. As permissões de aplicativo ajudam na decisão de quais aplicativos você permite que os usuários acessem e quais você deseja vetar.


## <a name="working-with-the-app-permissions-page"></a>Trabalhando com a página de permissões de aplicativo

A guia **Permissões de aplicativo** exibe informações sobre permissões de aplicativo no seu locatário do Office 365.

Para acessar a guia de Permissões de aplicativo:

1. No portal do Cloud App Security, clique em **Investigar** e em **Aplicativos conectados**, selecione **Office 365**. 
> [!Note]
> Primeiro é necessário conectar o Cloud App Security com o Office 365 para trabalhar com Permissões do aplicativo.

2. Em seguida, no painel do Office 365, clique na guia de **Permissões de aplicativo**.


 ![permissões de aplicativo](./media/app-permissions.png)

A página de Permissões de aplicativo fornece as seguintes informações sobre cada aplicativo de terceiros, aos quais foram concedidas permissões:

|Item|O que significa|
|-------|----------------|
|Ícone básico na barra de consulta de aplicativo  |Selecione esta opção para mudar para a consulta no modo de exibição básico.|
|Ícone Avançado na barra de consulta de aplicativo  |Selecione esta opção para mudar para a consulta no modo de exibição Avançado.|
|Abrir ou fechar todos os ícones de detalhes na lista de aplicativos  |Selecione esse ícone para exibir mais ou menos detalhes sobre cada aplicativo.|
|Ícone de exportar na lista de aplicativos  |Selecione esse ícone para exportar um arquivo CSV que contém uma lista de aplicativos, o número de usuários para cada aplicativo, as permissões associadas com o aplicativo, o nível das permissões, estado do aplicativo e nível de uso da comunidade.|
|Aplicativo|Nome do aplicativo. Selecione o nome para exibir mais informações, incluindo a descrição, o editor, o site do aplicativo e a ID.|
|Autorizado por|O número de usuários que autorizaram esse aplicativo a acessar suas contas do Office 365 e concederam permissões ao aplicativo. Selecione o número para exibir mais informações, incluindo uma lista de emails de usuário e se um administrador houver ou não consentido o aplicativo anteriormente.|
|Nível de permissões  |O ícone de nível de permissões e o texto que indica Alto, Médio ou Baixo. O nível indica quanto acesso esse aplicativo tem aos dados do Office 365. Por exemplo, Baixo pode indicar que o aplicativo acessa apenas nome e o perfil do usuário. Selecione o nível para exibir mais informações, incluindo as permissões concedidas ao aplicativo, uso da comunidade ou a atividade relacionada no [Log de governança](governance-actions.md).|
|Estado do aplicativo, seja Vetado, Aprovado ou Indeterminado.  |Um administrador pode marcar um aplicativo como aprovado, vetado ou deixar como indeterminado.|


## <a name="ban-or-approve-an-app"></a>Vetar ou aprovar um aplicativo
1. Na página de Permissões do aplicativo, clique no aplicativo para abrir a Gaveta de aplicativo para exibir mais informações sobre o aplicativo e as permissões que foram concedida a ele. Você pode clicar no link de Permissões para exibir uma lista completa das permissões que foram concedidas ao aplicativo. Em Uso da comunidade, você pode exibir o quão comum o aplicativo é em outras organizações. Você também pode clicar no link Relacionar atividade para exibir as atividades que estão listadas no log de governança relacionado a esse aplicativo.
2. Para vetar o aplicativo, clique no ícone de vetar no final da linha do aplicativo na tabela. <br></br>
 ![ícone de vetar aplicativo](./media/ban-app-icon.png) <br></br>
Quando você veta um aplicativo, pode escolher se deseja que os usuários saibam que o aplicativo previamente instalado e autorizado foi vetado e será desabilitado e não terá acesso ao Office 365. Se não quiser que eles saibam, cancele a seleção de Notificar os usuários que concederam acesso a esse aplicativo vetado na caixa de diálogo de Vetar o aplicativo.

    ![vetar aplicativo](./media/ban-app.png)
> [!Note]
> É recomendável que você informe os usuários do aplicativo que ele está prestes a ter o uso vetado.

3. Para aprovar o aplicativo, clique no ícone de aprovar no final da linha na tabela. <br></br>
 ![aprovar aplicativo](./media/approve-app.png) <br></br>
O ícone fica verde e o aplicativo é aprovado para todos os usuários do Office 365.
> [!Note]
> Quando você marca um aplicativo como aprovado não há nenhum efeito sobre o usuário final. Isso serve apenas para ajudá-lo a marcar visualmente os aplicativos que você aprovou para separá-los daqueles que você ainda não examinou.

3. Digite a mensagem que você deseja enviar para os usuários do aplicativo na caixa Digite uma mensagem de notificação personalizada e atualize o endereço de email 'responder para', se for necessário. 
 Clique em **Vetar aplicativo** para enviar o email e vetar o aplicativo dos usuários do Office 365.


## <a name="query-app-permissions"></a>Consultar permissões de aplicativo

### <a name="query-in-the-advanced-view"></a>Consulta no modo de exibição Avançado 
1. Na modo de exibição avançado, use a lista suspensa **Selecionar um filtro** para restringir sua pesquisa. Adicione operadores, é igual a ou não é igual a um valor selecionado para concluir a sua consulta.
2. Selecione o ícone **Adicionar um filtro** para adicionar filtros adicionais para refinar sua consulta. Os filtros são aplicados automaticamente e a lista de aplicativos é atualizada adequadamente.
3. Selecione o ícone **Remover um filtro** ao lado do filtro para remover os filtros.
Os filtros que você pode escolher são:
- Aplicativo, exibe o(s) aplicativo(s) de terceiros com o(s) nome(s) selecionado(s) aos quais foram concedidos acesso ao Office 365.

- Usuário, exibe os aplicativos que esse usuário autorizou.

- Permissões, exibe os aplicativos que exigem as permissões selecionadas.

- Estado do aplicativo, exibe os aplicativos com base em seu estado, aprovado, vetado ou indeterminado.

- Nível de permissão, exibe os aplicativos com base no nível ou níveis de permissão selecionado.

- Uso da comunidade, exibe os aplicativos com base nos níveis de uso de comunidade, sendo: raros, incomuns ou comuns.

### <a name="query-in-the-basic-view"></a>Consulta em modo de exibição básico 
No modo de exibição básico, selecione valores de uma ou várias listas suspensas para exibir aplicativos específicos. Você pode selecionar vários valores nas listas suspensas. Os menus suspensos que você pode usar para consultar são: 
- Aplicativo, exibe o(s) aplicativo(s) de terceiros com o(s) nome(s) selecionado(s) aos quais foram concedidos acesso ao Office 365.

- Usuário, exibe os aplicativos que esse usuário autorizou.

- Permissões, exibe os aplicativos que exigem as permissões selecionadas.

- Estado do aplicativo, exibe os aplicativos com base em seu estado, aprovado, vetado ou indeterminado.

- Nível de permissão, exibe os aplicativos com base no nível ou níveis de permissão selecionado.

- Uso da comunidade, exibe os aplicativos com base nos níveis de uso de comunidade, sendo: raros, incomuns ou comuns.
Os filtros são aplicados automaticamente e a lista de aplicativos é atualizada adequadamente. 

## <a name="see-also"></a>Consulte Também  
[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
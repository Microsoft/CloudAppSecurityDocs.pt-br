---
title: Conectar o Box ao Cloud App Security para obter visibilidade e controle de uso | Microsoft Docs
description: Este tópico fornece informações sobre como conectar seu aplicativo do Box ao Cloud App Security usando o conector de API.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 7/15/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: b3e4713e-986f-4a5e-9fcc-f8de94dd0df7
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: a9a89450ed04b21159b7f4323f2e4b01a8e81d28
ms.sourcegitcommit: 70e685dc53c70b719b707e685d5ef45cec445891
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/15/2018
ms.locfileid: "39063938"
---
*Aplica-se ao: Microsoft Cloud App Security*


# <a name="connect-box-to-microsoft-cloud-app-security"></a>Conectar o Box ao Microsoft Cloud App Security
Esta seção fornece instruções para conectar o Microsoft Cloud App Security à sua conta do Box existente usando as APIs do Conector de Aplicativos.  
  
## <a name="how-to-connect-box-to-cloud-app-security"></a>Como conectar o Box ao Cloud App Security  
  
> [!NOTE]  
>  A implantação com uma conta que não seja uma conta de administrador leva a uma falha no teste da API e não permite que Cloud App Security verifique todos os arquivos no Box. Se isso for um problema para você, é possível realizar a implantação com um coadministrador que tenha todos os privilégios selecionados, mas o teste da API continuará a falhar e os arquivos pertencentes a outros administradores no Box não forem verificados.  
  
1.  Se você restringir o acesso de permissão do aplicativo, siga esta etapa. Caso contrário, pule para a etapa 2.  
  
    -   No console de administração do Box, clique no ícone de configurações seguido por **Business settings** ou **Enterprise settings**.  
  
         ![Configurações de negócios do Box](./media/box-business-settings.png "box business settings")  
  
    -   Clique na guia **Aplicativos**.  
  
         ![Aplicativos do Box](./media/box-apps.png "box apps")  
  
    -   Se **Aplicativos Não Publicados** for selecionado, na caixa de texto **Exceto para** adicione o número de série do aplicativo do Cloud App Security:
     
         |Data center|Número de série do Microsoft Cloud App Security|
         |----|----|    
         |US1| `nduj1o3yavu30dii7e03c3n7p49cj2qh`|
         |US2|`w0ouf1apiii9z8o0r6kpr4nu1pvyec75`|
         |US3|`dmcyvu1s9284i2u6gw9r2kb0hhve4a0r`|
         |EU1|`me9cm6n7kr4mfz135yt0ab9f5k4ze8qp`|
         |EU2|`uwdy5r40t7jprdlzo85v8suw1l4cdsbf`|

        Em seguida, clique em **Salvar**. Para obter informações sobre como ver a qual data center do Cloud App Security center você está conectado, consulte [Tokens de API](api-tokens.md). 
  
         ![Configurações de exceção no Box](./media/box-settings-except-for.png "box settings except for")  
  
    > [!NOTE]  
    >  Se você for um cliente Adallom existente e a URL do seu console for para o Adallom e não para o Cloud App Security, use este número de série do aplicativo: bwahmilhdlpbqy2ongkl119o3lrkoshc.  
  
2.  No portal do Cloud App Security, clique em **Investigar** e em **Aplicativos conectados**.  
  
3.  Na página **Conectores de aplicativos**, clique no botão de sinal de mais e selecione **Box**.  
  
     ![Conectar ao Box](./media/connect-box.png "connect box")  
  
4.  No pop-up **Configurações do Box**, clique em **Seguir esse link**.  
  
5.  A página de logon do Box é aberta. Insira suas credenciais para permitir que o Cloud App Security acesse o aplicativo do Box da sua equipe.  
  
6.  O Box pergunta se você deseja permitir que o Cloud App Security acesse o log de atividades e as informações da sua equipe e realize atividades como qualquer membro da equipe. Para continuar, clique em **Permitir**.  
  
7.  De volta ao portal do Cloud App Security, você deve receber uma mensagem dizendo que o Box foi conectado com êxito.  
  
8.  Certifique-se de que a conexão foi bem-sucedida clicando em **Testar API**.  
  
     O teste pode levar alguns minutos. Depois de receber uma notificação de êxito, clique em **Fechar**.  
  
O Box agora está conectado ao Cloud App Security.  
 
Depois de conectar o Box, você receberá eventos por 60 dias antes da conexão.
  
Após conectar o Box, o Cloud App Security realizará uma verificação completa. Dependendo de quantos arquivos e usuários você tiver, a verificação completa poderá levar algum tempo. Para habilitar a verificação quase em tempo real, os arquivos nos quais as atividades são detectadas são movidos para o início da fila de verificação. Por exemplo, um arquivo editado, atualizado ou compartilhado é verificado imediatamente, em vez de aguardar o processo de verificação normal. A verificação quase em tempo real não se aplica a arquivos que não são modificados por natureza. Por exemplo, os arquivos que são exibidos, visualizados, impressos ou exportados são verificados como parte da verificação agendada regularmente.
  
## <a name="see-also"></a>Consulte Também  
[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)   

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
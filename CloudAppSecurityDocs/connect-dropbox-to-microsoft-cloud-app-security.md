---
title: Conectar o Dropbox ao Cloud App Security para obter visibilidade e controle de uso | Microsoft Docs
description: "Este tópico fornece informações sobre como conectar seu aplicativo do Dropbox ao Cloud App Security usando o conector de API."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 9/25/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 4acd93f4-b885-4e1f-a385-43b5db02a3ee
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 56195253a603671d2f273616b652f5d821e80a51
ms.sourcegitcommit: 8759541301241e03784c5ac87b56986f22bd0561
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/28/2017
---
# <a name="connect-dropbox-to-microsoft-cloud-app-security"></a>Conectar o Dropbox ao Microsoft Cloud App Security
Esta seção fornece instruções para conectar o Cloud App Security à sua conta do Dropbox existente usando as APIs do conector.  
 
 
Como Dropbox concede acesso aos arquivos de links compartilhados sem precisar entrar, o Cloud App Security registra esses usuários como usuários não autenticados. Se você encontrar usuários não autenticados do Dropbox, isso poderá indicar usuários que não são da sua organização ou que podem ser usuários reconhecido da organização que não entraram.

## <a name="how-to-connect-dropbox-to-cloud-app-security"></a>Como conectar o Dropbox ao Cloud App Security  
  
1.  No console do Cloud App Security, clique em **Investigar** e em **Aplicativos conectados**.  
  
2.  Na página **Conectores de aplicativos**, clique no botão de mais após **Dropbox**.  
  
     ![Conectar ao Dropbox](./media/connect-dropbox.png "connect dropbox")  
  
3.  No pop-up, insira o endereço de email da conta do administrador.  
  
4.  Clique em **Gerar link**.  
  
5.  Clique em **Seguir este link**.  
  
     A página de logon do Dropbox é aberta. Insira suas credenciais para permitir que o Cloud App Security acesse a instância do Dropbox da sua equipe.  
  
6.  O Dropbox pergunta se você deseja permitir que o Cloud App Security acesse o log de atividades e as informações da sua equipe e realize atividades como qualquer membro da equipe. Para continuar, clique em **Permitir**.  
  
7.  De volta ao console do Cloud App Security, você deverá receber uma mensagem indicando que o Dropbox foi conectado com êxito.  
  
8.  Certifique-se de que a conexão foi bem-sucedida clicando em **Testar API**.  
  
     O teste pode levar alguns minutos. Depois de receber uma notificação de êxito, clique em **Fechar**.  
  
Depois de conectar o Dropbox, você receberá eventos por 60 dias antes da conexão.

> [!NOTE] 
> Todos os eventos do Dropbox de adição de arquivo são exibidos no Cloud App Security como Carregar arquivo para alinhamento com todos os outros aplicativos conectados ao Cloud App Security. 
 
## <a name="see-also"></a>Veja também  
[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
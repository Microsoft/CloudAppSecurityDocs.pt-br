---
title: Conectar o Dropbox ao Cloud App Security para obter visibilidade e controle de uso | Microsoft Docs
description: Este tópico fornece informações sobre como conectar seu aplicativo do Dropbox ao Cloud App Security usando o conector de API.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/29/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 4acd93f4-b885-4e1f-a385-43b5db02a3ee
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: b3e6e9a25c419aa9453e4771b477c068b9ad902c
ms.sourcegitcommit: bb010d8dd0a6eff39df31e33c2cc9c37ec321b46
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50217230"
---
*Aplica-se ao: Microsoft Cloud App Security*


# <a name="connect-dropbox-to-microsoft-cloud-app-security"></a>Conectar o Dropbox ao Microsoft Cloud App Security
Esta seção fornece instruções para conectar o Microsoft Cloud App Security à sua conta do Dropbox existente usando as APIs do conector.  
 
 
Como Dropbox concede acesso aos arquivos de links compartilhados sem precisar entrar, o Cloud App Security registra esses usuários como usuários não autenticados. Se encontrar usuários não autenticados do Dropbox, isso poderá indicar usuários que não são da sua organização ou eles poderão ser usuários reconhecidos de dentro da sua organização que não entraram.

## <a name="how-to-connect-dropbox-to-cloud-app-security"></a>Como conectar o Dropbox ao Cloud App Security  
  
1.  No console do Cloud App Security, clique em **Investigar** e em **Aplicativos conectados**.  
  
2.  Na página **Conectores de aplicativos**, clique no botão de mais após **Dropbox**.  
  
     ![Conectar ao Dropbox](./media/connect-dropbox.png "connect dropbox")  
  
3.  No pop-up, insira o endereço de email da conta do administrador.  
  
4.  Clique em **Gerar link**.  
  
5.  Clique em **Seguir este link**.  
  
     A página de entrada do Dropbox é aberta. Insira suas credenciais para permitir que o Cloud App Security acesse a instância do Dropbox da sua equipe.  
  
6.  O Dropbox pergunta se você deseja permitir que o Cloud App Security acesse o log de atividades e as informações da sua equipe e realize atividades como qualquer membro da equipe. Para continuar, clique em **Permitir**.  
  
7.  De volta ao console do Cloud App Security, você deverá receber uma mensagem indicando que o Dropbox foi conectado com êxito.  
  
8.  Certifique-se de que a conexão foi bem-sucedida clicando em **Testar API**.  
  
     O teste pode levar alguns minutos. Depois de receber uma notificação de êxito, clique em **Fechar**.  
  
Depois de conectar o Dropbox, você receberá eventos por 60 dias antes da conexão.

> [!NOTE] 
> Todos os eventos do Dropbox de adição de arquivo são exibidos no Cloud App Security como Carregar arquivo para alinhamento com todos os outros aplicativos conectados ao Cloud App Security. 
 
## <a name="next-steps"></a>Próximas etapas 
[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)   

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
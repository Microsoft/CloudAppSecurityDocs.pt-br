---
title: Conectar o Okta ao Cloud App Security para obter visibilidade e controle de uso | Microsoft Docs
description: Este tópico fornece informações sobre como conectar seu aplicativo Okta ao Cloud App Security usando o conector de API.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/22/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 9c3673b9-99bd-400c-9da1-5bf809ea5892
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: c03400dc2bf0840736125b5080fbf8783a4da1db
ms.sourcegitcommit: 0ac08ca7b3140b79f1d36ff7152476c188fa12b3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44144322"
---
*Aplica-se ao: Microsoft Cloud App Security*



# <a name="connect-okta-to-microsoft-cloud-app-security"></a>Conectar o Okta ao Microsoft Cloud App Security
Esta seção fornece instruções para conectar o Microsoft Cloud App Security à sua conta do Okta existente usando as APIs do conector.  
  
## <a name="how-to-connect-okta-to-cloud-app-security"></a>Como conectar o Okta ao Cloud App Security  
  
1.  É recomendável que você crie uma Conta de Serviço de administrador no Okta para o Cloud App Security.  
  
     Certifique-se de usar uma conta com permissões de Superadministrador.  
  
     Verifique se sua conta do Okta é verificada.  
  
2.  No console do Okta, clique em **Administração**.  
  
    -   Clique em **Segurança** e em **API**.  
  
         ![API do Okta](./media/okta-api.png "okta api")  
  
    -   Clique em **Create Token (Criar Token)**.  
  
         ![Criar token do Okta](./media/okta-createtoken.jpg "okta createtoken")  
  
    -   No pop-up **Create Token (Criar Token)**, nomeie o token do Cloud App Security e clique em **Create Token (Criar Token)**.  
  
         ![Pop-up do token do Okta](./media/okta-token-popup.png "okta token popup")  
  
    -   No pop-up **Token created successfully (Token criado com êxito)**, copie o **Token value (Valor do token)**.  
  
         ![Valor do token do Okta](./media/okta-token-value.png "okta token value")  
  
3.  No console do Cloud App Security, clique em **Investigar** e em **Aplicativos conectados**.  
  
4.  Na **página Conectores de aplicativos**, clique no botão de mais e depois em **Okta**.  
  
     ![Conectar ao Okta](./media/connect-okta.png "connect okta")  
  
5.  No pop-up que abrir, no campo **Domain (Domínio)**, insira seu domínio do Okta e cole seu token no campo **Token**.  
  
6.  Clique em **Conectar** para criar o token para o Okta no Cloud App Security.  
  
7.  Certifique-se de que a conexão foi bem-sucedida clicando em **Testar API**.  
  
     O teste pode levar alguns minutos. Depois de receber uma notificação de êxito, clique em **Fechar**.  
  
Depois de conectar o Okta, você receberá eventos por 60 dias antes da conexão.
  
## <a name="see-also"></a>Consulte Também  
[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)   

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
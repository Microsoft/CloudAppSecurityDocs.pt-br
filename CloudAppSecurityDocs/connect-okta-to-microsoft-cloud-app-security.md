---
title: Conectar o Okta ao Cloud App Security para obter visibilidade e controle de uso | Microsoft Docs
description: Este artigo fornece informações sobre como conectar o Okta ao Cloud App Security usando o conector de API.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/13/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 9c3673b9-99bd-400c-9da1-5bf809ea5892
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 5f3f6113e48ea1db2261786d54a2edc9f320663e
ms.sourcegitcommit: 77850c6777504c2478611cb71a387e7fcc5f2551
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/13/2018
ms.locfileid: "51597214"
---
# <a name="connect-okta-to-microsoft-cloud-app-security"></a>Conectar o Okta ao Microsoft Cloud App Security

*Aplica-se ao: Microsoft Cloud App Security*

Este artigo fornece instruções para conectar o Microsoft Cloud App Security à sua conta existente do Okta usando as APIs do conector.  
  
## <a name="how-to-connect-okta-to-cloud-app-security"></a>Como conectar o Okta ao Cloud App Security  
  
1.  É recomendável que você crie uma Conta de Serviço de administrador no Okta para o Cloud App Security.  
  
     Certifique-se de usar uma conta com permissões de Superadministrador.  
  
     Verifique se sua conta do Okta é verificada.  
  
2.  No console do Okta, clique em **Administração**.  
  
    -   Clique em **Segurança** e em **API**.  
  
         ![API do Okta](./media/okta-api.png "API do Okta")  
  
    -   Clique em **Create Token (Criar Token)**.  
  
         ![Criar token do Okta](./media/okta-createtoken.jpg "Criar token do Okta")  
  
    -   No pop-up **Criar Token**, dê um nome ao token do Cloud App Security e clique em **Criar Token**.  
  
         ![Pop-up do token do Okta](./media/okta-token-popup.png "Pop-up do token do Okta")  
  
    -   No pop-up **Token created successfully (Token criado com êxito)**, copie o **Token value (Valor do token)**.  
  
         ![Valor do token do Okta](./media/okta-token-value.png "Valor do token do Okta")  
  
3.  No console do Cloud App Security, clique em **Investigar** e em **Aplicativos conectados**.  
  
4.  Na **página Conectores de aplicativos**, clique no botão de mais e depois em **Okta**.  
  
     ![conectar Okta](./media/connect-okta.png "conectar Okta")  
  
5.  No pop-up que abrir, no campo **Domain (Domínio)**, insira seu domínio do Okta e cole seu token no campo **Token**.  
  
6.  Clique em **Conectar** para criar o token para o Okta no Cloud App Security.  
  
7.  Certifique-se de que a conexão foi bem-sucedida clicando em **Testar API**.  
  
     O teste pode levar alguns minutos. Depois de receber uma notificação de êxito, clique em **Fechar**.  
  
Depois de conectar o Okta, você receberá eventos por 60 dias antes da conexão.
  
## <a name="next-steps"></a>Próximas etapas  
[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)   

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  

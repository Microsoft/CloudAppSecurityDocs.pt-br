---
title: Conectar o Okta | Microsoft Docs
description: "Este tópico fornece informações sobre como conectar seu aplicativo Okta ao Cloud App Security usando o conector de API."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/26/2016
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 9c3673b9-99bd-400c-9da1-5bf809ea5892
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6beb9041b338406fb5b16f4bd045dbdc4592c6d9
ms.openlocfilehash: 1e82f94cb8423bdaa3dcdc8d4a4f04179089546c


---

# <a name="connect-okta-to-microsoft-cloud-app-security"></a>Conectar o Okta ao Microsoft Cloud App Security
Esta seção fornece instruções para conectar o Cloud App Security à sua conta do Okta existente usando as APIs do conector.  
  
## <a name="how-to-connect-okta-to-cloud-app-security"></a>Como conectar o Okta ao Cloud App Security  
  
1.  É recomendável que você crie uma Conta de Serviço de administrador no Okta para o Cloud App Security.  
  
     Certifique-se de usar uma conta com permissões de Superadministrador.  
  
     Verifique se sua conta do Okta é verificada.  
  
2.  No console do Okta, clique em **Administração**.  
  
    -   Clique em **Segurança** e em **API**.  
  
         ![api do okta](./media/okta-api.png "okta api")  
  
    -   Clique em **Create Token (Criar Token)**.  
  
         ![createtoken do okta](./media/okta-createtoken.jpg "okta createtoken")  
  
    -   No pop-up **Create Token (Criar Token)**, atribua um nome ao seu token do Cloud App Security e clique em **Create Token (Criar Token)**.  
  
         ![pop-up de token do okta](./media/okta-token-popup.png "okta token popup")  
  
    -   No **pop-up Token created successfully (Token criado com êxito)**, copie o **Token value (Valor do token)**.  
  
         ![valor do token do okta](./media/okta-token-value.png "okta token value")  
  
3.  No console do Cloud App Security, clique em **Investigar** e em **Aplicativos conectados**.  
  
4.  Na **página Conectores de aplicativos**, clique no botão de mais e depois em **Okta**.  
  
     ![conectar ao okta](./media/connect-okta.png "connect okta")  
  
5.  Na janela pop-up que abrir, no campo **Domínio**, insira seu domínio do Okta e cole seu token no campo **Token**.  
  
6.  Clique em **Conectar** para criar o token para o Okta no Cloud App Security.  
  
7.  Certifique-se de que a conexão foi bem-sucedida clicando em **Testar API**.  
  
     O teste pode levar alguns minutos. Depois de receber uma notificação de êxito, clique em **Fechar**.  
  
Depois de conectar o Okta, você receberá eventos por 60 dias antes da conexão.
  
## <a name="see-also"></a>Veja também  
[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Nov16_HO5-->



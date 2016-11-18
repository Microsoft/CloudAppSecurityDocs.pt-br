---
title: Conectar o Okta ao Microsoft Cloud App Security | Microsoft Docs
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
ms.sourcegitcommit: 759692e7b270d87dc1becf88453d095f2382c411
ms.openlocfilehash: 3fd8ada1ce622da339368c64ecc8b1d319b9c333


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
  
3.  No console do Cloud App Security, clique em **Investigar** e em **Aplicativos sancionados**.  
  
4.  Na linha Okta, clique em **Conectar** na coluna **Status do Conector de Aplicativos** ou clique no botão **Conectar um aplicativo** e em **Okta**.  
  
     ![conectar ao okta](./media/connect-okta.png "connect okta")  
  
5.  Na página da API, no campo **Domínio**, insira seu domínio do Okta e cole seu token no campo **Token**.  
  
6.  Clique em **Conectar** para criar o token para o Okta no Cloud App Security.  
  
7.  Certifique-se de que a conexão foi bem-sucedida clicando em **Testar API**.  
  
     O teste pode levar alguns minutos. Depois de receber uma notificação de êxito, clique em **Fechar**.  
  
Depois de conectar o Okta, você receberá eventos por 60 dias antes da conexão.
  
## <a name="see-also"></a>Veja também  
[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Nov16_HO3-->



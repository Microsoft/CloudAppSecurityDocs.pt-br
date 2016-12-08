---
title: Conectar o ServiceNow | Microsoft Docs
description: "Este tópico fornece informações sobre como conectar seu aplicativo do ServiceNow ao Cloud App Security usando o conector de API."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: c626d94d-2ffd-4daf-8fa4-4b6d308cf012
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6beb9041b338406fb5b16f4bd045dbdc4592c6d9
ms.openlocfilehash: 7935006b6b28ed93601ca60adf3c1a408440eae7


---

# <a name="connect-servicenow-to-microsoft-cloud-app-security"></a>Conectar o ServiceNow ao Microsoft Cloud App Security
Esta seção fornece instruções para conectar o Cloud App Security à sua conta do ServiceNow existente usando a API do conector de aplicativos.  
  
## <a name="how-to-connect-servicenow-to-cloud-app-security"></a>Como conectar o ServiceNow ao Cloud App Security  
  
> [!NOTE]  
>  O Cloud App Security dá suporte a versões do ServiceNow do Eureka e Fiji. Para conectar o ServiceNow ao Cloud App Security, você deve ter permissões do nível de administrador e verificar se a instância do ServiceNow dá suporte ao acesso à API.  
  
1.  Faça logon com uma conta de administrador na sua conta do ServiceNow.  
  
2.  Crie uma nova conta de serviço para o Cloud App Security e anexe a função de administrador à conta recém-criada.  
  
3.  Verifique se o plug-in da API REST está ativado.  
  
     ![conta do servicenow](./media/servicenow-account.png "servicenow account")  
  
4.  No portal do Cloud App Security, clique em **Investigar** e em **Aplicativos conectados**.  
  
5.  Na página **Conectores de aplicativos**, clique no botão de mais e depois em **ServiceNow**.  
  
     ![conectar o servicenow](./media/connect-servicenow.png "connect servicenow")  
  
6.  Na janela pop-up, adicione seu nome de usuário, senha e URL da instância do ServiceNow nas caixas apropriadas.  
  
7.  Clique em **Conectar**.  
  
     ![atualização de senha do servicenow](./media/servicenow-update-password.png "servicenow update password")  
  
8.  Certifique-se de que a conexão foi bem-sucedida clicando em **Testar API**.  
  
     O teste pode levar alguns minutos. Depois de receber uma notificação de êxito, clique em **Fechar**.  
  
Depois de conectar o ServiceNow, você receberá eventos por 60 dias antes da conexão.
  
## <a name="see-also"></a>Veja também  
[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Nov16_HO5-->



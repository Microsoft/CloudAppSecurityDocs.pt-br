---
title: Conectar o Office 365 | Microsoft Docs
description: "Este tópico fornece informações sobre como conectar seu Office 365 ao Cloud App Security usando o conector de API."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/26/2016
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: a79bf393-0d2c-44b6-8dab-86c740fd7333
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6beb9041b338406fb5b16f4bd045dbdc4592c6d9
ms.openlocfilehash: e0ca79daddaaa2cdcbc51308653b3ec05da1b5e2


---

# <a name="connect-office-365-to-microsoft-cloud-app-security"></a>Conectar o Office 365 ao Microsoft Cloud App Security
Esta seção fornece instruções para conectar o Cloud App Security à sua conta do Microsoft Office 365 existente usando a API do conector de aplicativos.  
  
  

## <a name="how-to-connect-office-365-to-cloud-app-security"></a>Como conectar o Office 365 ao Cloud App Security  
  
> [!NOTE]
>- Você deve ter pelo menos uma licença do Office 365 atribuída para conectar o Office 365 ao Cloud App Security.
>-  O log de auditoria de administrador do Exchange, que é habilitado por padrão no Office 365, registra um evento no log de auditoria do Office 365 quando um administrador (ou um usuário que tenha recebido privilégios administrativos) faz uma alteração em sua organização do Exchange Online. As alterações feitas usando o centro de administração do Exchange ou executando um cmdlet do Windows PowerShell são registradas no log de auditoria de administrador do Exchange. Para ver informações detalhadas sobre o log de auditoria de administrador do Exchange, consulte [Log de auditoria de administrador](http://go.microsoft.com/fwlink/p/?LinkID=619225).
>- O log de auditoria do Exchange Mailbox deve estar ativado para cada caixa de correio do usuário para que as atividades do usuário no Exchange Online sejam registrada em log; consulte [Atividades do Exchange Mailbox](https://support.office.com/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c).
>- Se os aplicativos do Office estiverem habilitados, os grupos que fazem parte do Office 365 também são criados nos aplicativos do Office; se o SharePoint estiver habilitado, por exemplo, os grupos do Office 365 serão criados nele.
 
1.  Na página **Aplicativos conectados**, clique no botão de mais e selecione **Office 365**.  

2.  No pop-up do Office 365, clique em Conectar o Office 365.

      ![conectar o 0365](./media/connect-0365.png) 
 
3.  Clique em “Testar agora” para testar a conexão para o Office 365. O teste pode levar alguns minutos.
  
    ![Testar conexão do O365](./media/o365-test-connection.png) 
 
4.   Depois de ser indicado que a conexão do Office 365 foi concluída com êxito, clique em **Fechar**.
  
     ![O365 conectado](./media/o365-connected.png) 

> [!NOTE] 
> Depois de conectar o Office 365, você verá os dados de uma semana atrás, incluindo quaisquer aplicativos de terceiros conectados ao Office 365 que recebem APIs. Para aplicativos de terceiros que não recebiam APIs antes da conexão, você verá os eventos a partir do momento que conectar o Office 365, pois o Cloud App Security ativa todas as APIs desativadas por padrão.

## <a name="see-also"></a>Veja também  
[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Nov16_HO5-->



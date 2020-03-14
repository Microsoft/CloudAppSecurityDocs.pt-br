---
title: Conectar o Office 365 ao Cloud App Security
description: Este artigo fornece informações sobre como conectar seu Office 365 para Cloud App Security usando o conector de API para visibilidade e controle sobre o uso.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 7/30/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 74b03bd9db046a7637ea84d69914d1e87b47c2ae
ms.sourcegitcommit: 4f3883a9e85d0aaf2802b10433b221c3f1838d88
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79285490"
---
# <a name="connect-office-365-to-microsoft-cloud-app-security"></a>Conectar o Office 365 ao Microsoft Cloud App Security

*Aplica-se a: Microsoft Cloud App Security*

Este artigo fornece instruções para conectar Microsoft Cloud App Security à sua conta existente do Microsoft Office 365 usando a API do conector de aplicativos. Essa conexão fornece visibilidade e controle sobre o uso do Office 365. Para obter informações sobre como Cloud App Security protege o Office 365, consulte [proteger o office 365](protect-office-365.md).
  
O Cloud App Security dá suporte à plataforma dedicada do Office 365, bem como às ofertas mais recentes dos serviços do Office 365 (normalmente conhecidos como a família de versões vNext do Office 365).  O Cloud App Security não dá suporte ao Microsoft Business Productivity Online Standard Suite (BPOS) herdado.

> [!NOTE]
> Em alguns casos, uma versão de serviço vNext difere ligeiramente nos níveis administrativo e de gerenciamento da oferta padrão do Office 365.

O Cloud App Security dá suporte aos seguintes aplicativos do Office 365:

- CRM do Dynamics 365
- O Exchange (só aparece depois que as atividades do Exchange são detectadas no portal e exige que você ative a auditoria)
- Office 365
- OneDrive
- Automatizar energia
- Power BI (só aparece depois que as atividades de Power BI são detectadas no portal e exige que você ative a auditoria)
- SharePoint
- Skype for Business
- Equipes (aparecem somente depois que as atividades de equipes são detectadas no Portal)
- Yammer

> [!NOTE]
> O Cloud App Security se integra diretamente aos [logs de auditoria do Office 365](https://docs.microsoft.com/microsoft-365/compliance/detailed-properties-in-the-office-365-audit-log?view=o365-worldwide) e recebe todos os eventos auditados de **todos os serviços com suporte**, como PowerApps, Forms, Sway e Stream.

## <a name="how-to-connect-office-365-to-cloud-app-security"></a>Como conectar o Office 365 ao Cloud App Security  

> [!NOTE]
>
>- Você deve ter pelo menos uma licença atribuída do Office 365 para conectar o Office 365 ao Cloud App Security.
>- Para habilitar o monitoramento das atividades do Office 365 no Cloud App Security, é necessário habilitar a auditoria no [centro de conformidade e segurança do Office](https://support.microsoft.com/help/4026501/office-auditing-in-office-365-for-admins).
>- O log de auditoria do administrador do Exchange, que é habilitado por padrão no Office 365, registra um evento no log de auditoria do Office 365 quando um administrador (ou um usuário que tenha sido atribuído a privilégios administrativos) faz uma alteração na sua organização do Exchange Online. As alterações feitas usando o centro de administração do Exchange ou executando um cmdlet no Windows PowerShell são registradas no log de auditoria do administrador do Exchange. Para obter informações mais detalhadas sobre o log de auditoria de administrador no Exchange, consulte [log de auditoria do administrador](https://docs.microsoft.com/exchange/security-and-compliance/exchange-auditing-reports/view-administrator-audit-log).
>- O log de auditoria da caixa de correio do Exchange deve ser ativado para cada caixa de correio do usuário antes que a atividade do usuário no Exchange Online seja registrada, consulte [atividades da caixa](https://support.office.com/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c)de
>- Se os aplicativos do Office estiverem habilitados, os grupos que fazem parte do Office 365 também serão importados para Cloud App Security dos aplicativos específicos do Office, por exemplo, se o SharePoint estiver habilitado, os grupos do Office 365 serão importados como grupos do SharePoint também.
>- Você deve [habilitar a auditoria no PowerBI](https://powerbi.microsoft.com/documentation/powerbi-admin-auditing/) para obter os logs a partir daí. Depois que a auditoria estiver habilitada, Cloud App Security começará a obter os logs (com um atraso de 24-72 horas).
>- Você deve [habilitar a auditoria no Dynamics 365](https://docs.microsoft.com/dynamics365/customer-engagement/admin/enable-use-comprehensive-auditing#enable-auditing) para obter os logs a partir daí. Depois que a auditoria estiver habilitada, Cloud App Security começará a obter os logs (com um atraso de 24-72 horas).
>- Se seu Azure Active Directory estiver configurado para sincronizar automaticamente com os usuários em seu ambiente do Active Directory local, as configurações no ambiente local substituirão as configurações do Azure AD e o uso da ação **suspender** governança do usuário será revertido.
>- Para atividades de entrada do Azure AD, Cloud App Security apenas superfícies atividades de entrada interativas e atividades de entrada de protocolos herdados, como o ActiveSync. As atividades de entrada não interativas podem ser exibidas no log de auditoria do Azure AD.

1. Na página **aplicativos conectados** , clique no botão de adição e selecione **Office 365**.

    ![conectar 0365](media/connect-0365.png)

2. No pop-up do Office 365, clique em **conectar o office 365**.

    ![conectar 0365](media/office-connect.png)

3. Depois que o Office 365 for exibido como conectado com êxito, clique em **fechar**.

> [!NOTE]
> Depois de conectar o Office 365, você verá os dados de uma semana de volta, incluindo todos os aplicativos de terceiros conectados ao Office 365 que estão recebendo APIs. Para aplicativos de terceiros que não estavam recebendo APIs antes da conexão, você vê eventos a partir do momento em que conecta o Office 365, porque Cloud App Security ativa as APIs que ficaram desativadas por padrão.

Se você tiver problemas para conectar o aplicativo, consulte [Solucionando problemas de conectores de aplicativos](troubleshooting-api-connectors-using-error-messages.md).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]

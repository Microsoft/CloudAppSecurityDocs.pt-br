---
title: Conectar o Office 365 ao Cloud App Security
description: Este artigo fornece informações sobre como conectar o Office 365 ao Cloud App Security usando o conector de API para obter visibilidade e controle sobre o uso.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 08/17/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 69d194d0921613b5e5741a7e20fb366875f0278c
ms.sourcegitcommit: 98c8dd439d1183af3d8598c676c8ff041a88bd88
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2020
ms.locfileid: "89666869"
---
# <a name="connect-office-365-to-microsoft-cloud-app-security"></a>Conectar o Office 365 ao Microsoft Cloud App Security

*Aplica-se a: Microsoft Cloud App Security*

Este artigo fornece instruções para conectar Microsoft Cloud App Security à sua conta existente do Office 365 usando a API do conector de aplicativo. Essa conexão fornece visibilidade e controle sobre o uso do Office 365. Para obter informações sobre como Cloud App Security protege o Office 365, consulte [proteger o office 365](protect-office-365.md).
  
O Cloud App Security dá suporte à Plataforma Dedicada herdada do Office 365 além das ofertas mais recentes de serviços do Office 365 (conhecidos como a família da versão vNext do Office 365).  O Cloud App Security não dá suporte ao Microsoft BPOS (Business Productivity Online Standard Suite) Herdado.

> [!NOTE]
> Em alguns casos, uma versão do serviço vNext difere um pouco nos níveis administrativos e de gerenciamento da oferta padrão do Office 365.

O Cloud App Security oferece suporte aos seguintes aplicativos do Office 365:

- CRM do Dynamics 365
- Exchange (exibido somente depois que as atividades do Exchange forem detectadas no portal e exige que você ative a auditoria)
- Office
- OneDrive
- Power Automate
- Power BI (exibido apenas depois que as atividades do Power BI são detectadas no portal e requer que você ative a auditoria)
- SharePoint
- Skype for Business
- Equipes (exibido somente depois que as Equipes forem detectadas no portal)
- Yammer

> [!NOTE]
> O Cloud App Security se integra diretamente aos [logs de auditoria do Office 365](/microsoft-365/compliance/detailed-properties-in-the-office-365-audit-log?view=o365-worldwide&preserve-view=true) e recebe todos os eventos auditados de **todos os serviços com suporte**, como PowerApps, Forms, Sway e Stream.

## <a name="how-to-connect-office-365-to-cloud-app-security"></a>Como conectar o Office 365 ao Cloud App Security  

> [!NOTE]
>
>- Você deve ter pelo menos uma licença do Office 365 atribuída para conectar o Office 365 ao Cloud App Security.
>- Para habilitar o monitoramento das atividades do Office 365 no Cloud App Security, é necessário habilitar a auditoria no [centro de conformidade e segurança do Office](https://support.microsoft.com/help/4026501/office-auditing-in-office-365-for-admins).
>- O log de auditoria de administrador do Exchange, que é habilitado por padrão no Office 365, registra um evento no log de auditoria do Office 365 quando um administrador (ou um usuário que tenha recebido privilégios administrativos) faz uma alteração em sua organização do Exchange Online. As alterações feitas usando o centro de administração do Exchange ou executando um cmdlet do Windows PowerShell são registradas no log de auditoria de administrador do Exchange. Para ver informações detalhadas sobre o log de auditoria de administrador do Exchange, consulte [Log de auditoria de administrador](/exchange/security-and-compliance/exchange-auditing-reports/view-administrator-audit-log).
>- O log de auditoria do Exchange Mailbox deve estar ativado para cada caixa de correio do usuário para que as atividades do usuário no Exchange Online sejam registrada em log, consulte [Atividades do Exchange Mailbox](https://support.office.com/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c).
>- Se os aplicativos do Office estiverem habilitados, os grupos que fazem parte do Office 365 também serão importados para o Cloud App Security nos aplicativos do Office; por exemplo, se o SharePoint estiver habilitado, os Grupos do Office 365 também serão importados como grupos do SharePoint.
>- Você deve [habilitar a auditoria no Power BI](https://powerbi.microsoft.com/documentation/powerbi-admin-auditing/) para obter os logs. Após a habilitação da auditoria, o Cloud App Security começará a obter os logs (com um atraso de 24 a 72 horas).
>- Você deve [habilitar a auditoria no Dynamics 365](/dynamics365/customer-engagement/admin/enable-use-comprehensive-auditing#enable-auditing) para obter os logs a partir daí. Após a habilitação da auditoria, o Cloud App Security começará a obter os logs (com um atraso de 24 a 72 horas).
>- Se o Azure Active Directory estiver definido para sincronizar automaticamente com os usuários no seu ambiente local do Active Directory, as configurações no ambiente local substituirão as configurações do Azure AD e o uso da ação de governança **Suspender usuário** será revertida.
>- Para atividades de entrada do Azure AD, Cloud App Security apenas superfícies atividades de entrada interativas e atividades de entrada de protocolos herdados, como o ActiveSync. As atividades de entrada não interativas podem ser exibidas no log de auditoria do Azure AD.
> - Só há suporte para [implantações de várias regiões](/office365/enterprise/office-365-multi-geo) no onedrive

1. Na página **Aplicativos conectados**, clique no botão de mais e selecione **Office 365**.

    ![opção de menu conectar O365](media/connect-o365.png)

1. No pop-up do Office 365, clique em **conectar o office 365**.

    ![conectar pop-up do O365](media/office-connect.png)

1. Na página componentes do Office 365, selecione as opções necessárias e clique em **conectar**.

    > [!NOTE]
    >
    > - Para obter a melhor proteção, é recomendável selecionar todos os componentes do Office 365.
    > - O componente **arquivos do Office 365** requer o componente **atividades do Office 365** e Cloud app Security monitoramento de arquivos (arquivos de**configurações**  >  **Files**  >  **habilitam o monitoramento de arquivos**).

    ![conectar componentes do O365](media/connect-o365-components.png)

1. Depois de ser indicado que a conexão do Office 365 foi concluída com êxito, clique em **Fechar**.

> [!NOTE]
> Depois de conectar o Office 365, você verá os dados de uma semana atrás, incluindo quaisquer aplicativos de terceiros conectados ao Office 365 que recebem APIs. Para aplicativos de terceiros que não estavam recebendo APIs antes da conexão, você vê eventos do momento em que conecta o Office 365 porque o Cloud App Security ativa as APIs que ficaram desativadas por padrão.

Se você tiver problemas para conectar o aplicativo, consulte [Solucionando problemas de conectores de aplicativos](troubleshooting-api-connectors-using-error-messages.md).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]

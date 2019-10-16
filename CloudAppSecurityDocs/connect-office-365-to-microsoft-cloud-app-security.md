---
title: Conectar o Office 365 ao Cloud App Security
description: Este artigo fornece informações sobre como conectar o Office 365 ao Cloud App Security usando o conector de API para obter visibilidade e controle sobre o uso.
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
ms.assetid: a79bf393-0d2c-44b6-8dab-86c740fd7333
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: e8be0a2cd23a23d223fff12e956eb7152fa9fa14
ms.sourcegitcommit: c342abeec95359ddabdabcc3a081a0f91d52407c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72335610"
---
# <a name="connect-office-365-to-microsoft-cloud-app-security"></a>Conectar o Office 365 ao Microsoft Cloud App Security

*Aplica-se ao: Microsoft Cloud App Security*

Este artigo fornece instruções para conectar o Microsoft Cloud App Security à sua conta existente do Microsoft Office 365 usando a API do conector de aplicativos.  Essa conexão fornece visibilidade e controle sobre o uso do Office 365.
  
O Cloud App Security dá suporte à Plataforma Dedicada herdada do Office 365 além das ofertas mais recentes de serviços do Office 365 (conhecidos como a família da versão vNext do Office 365).  O Cloud App Security não dá suporte ao Microsoft BPOS (Business Productivity Online Standard Suite) Herdado. 

> [!NOTE]
> Em alguns casos, uma versão do serviço vNext difere um pouco nos níveis administrativos e de gerenciamento da oferta padrão do Office 365.

O Cloud App Security oferece suporte aos seguintes aplicativos do Office 365:

- Office 365
- SharePoint
- OneDrive
- Equipes (exibido somente depois que as Equipes forem detectadas no portal)
- Power BI (exibido apenas depois que as atividades do Power BI são detectadas no portal e requer que você ative a auditoria)
- Exchange (exibido somente depois que as atividades do Exchange forem detectadas no portal e exige que você ative a auditoria)
- Dynamics 365

## <a name="how-to-connect-office-365-to-cloud-app-security"></a>Como conectar o Office 365 ao Cloud App Security  

> [!NOTE]
>- Você deve ter pelo menos uma licença do Office 365 atribuída para conectar o Office 365 ao Cloud App Security.
>- Para habilitar o monitoramento das atividades do Office 365 no Cloud App Security, é necessário habilitar a auditoria no [centro de conformidade e segurança do Office](https://support.microsoft.com/help/4026501/office-auditing-in-office-365-for-admins).
>- O log de auditoria de administrador do Exchange, que é habilitado por padrão no Office 365, registra um evento no log de auditoria do Office 365 quando um administrador (ou um usuário que tenha recebido privilégios administrativos) faz uma alteração em sua organização do Exchange Online. As alterações feitas usando o centro de administração do Exchange ou executando um cmdlet do Windows PowerShell são registradas no log de auditoria de administrador do Exchange. Para ver informações detalhadas sobre o log de auditoria de administrador do Exchange, consulte [Log de auditoria de administrador](https://docs.microsoft.com/exchange/security-and-compliance/exchange-auditing-reports/view-administrator-audit-log).
>- O log de auditoria do Exchange Mailbox deve estar ativado para cada caixa de correio do usuário para que as atividades do usuário no Exchange Online sejam registrada em log, consulte [Atividades do Exchange Mailbox](https://support.office.com/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c).
>- Se os aplicativos do Office estiverem habilitados, os grupos que fazem parte do Office 365 também serão importados para o Cloud App Security nos aplicativos do Office; por exemplo, se o SharePoint estiver habilitado, os Grupos do Office 365 também serão importados como grupos do SharePoint.
>- Você deve [habilitar a auditoria no Power BI](https://powerbi.microsoft.com/documentation/powerbi-admin-auditing/) para obter os logs. Após a habilitação da auditoria, o Cloud App Security começará a obter os logs (com um atraso de 24 a 72 horas).
>- Você deve [habilitar a auditoria no Dynamincs 365](https://docs.microsoft.com/dynamics365/customer-engagement/admin/enable-use-comprehensive-auditing#enable-auditing-in-dynamics-365-for-customer-engagement/) para obter os logs a partir daí. Após a habilitação da auditoria, o Cloud App Security começará a obter os logs (com um atraso de 24 a 72 horas).
>- Se o Azure Active Directory estiver definido para sincronizar automaticamente com os usuários no seu ambiente local do Active Directory, as configurações no ambiente local substituirão as configurações do Azure AD e o uso da ação de governança **Suspender usuário** será revertida.
>- Para atividades de entrada do Azure AD, Cloud App Security apenas superfícies atividades de entrada interativas e atividades de entrada de protocolos herdados, como o ActiveSync. As atividades de entrada não interativas podem ser exibidas no log de auditoria do Azure AD.

1. Na página **Aplicativos conectados**, clique no botão de mais e selecione **Office 365**.  

      ![conectar o 0365](./media/connect-0365.png) 

2. No pop-up do Office 365, clique em **Conectar o Office 365**.

      ![conectar o 0365](./media/office-connect.png) 

3. Depois de ser indicado que a conexão do Office 365 foi concluída com êxito, clique em **Fechar**.

> [!NOTE]
> Depois de conectar o Office 365, você verá os dados de uma semana atrás, incluindo quaisquer aplicativos de terceiros conectados ao Office 365 que recebem APIs. Para aplicativos de terceiros que não recebiam APIs antes da conexão, você verá os eventos a partir do momento que conectar o Office 365, pois o Cloud App Security ativa todas as APIs desativadas por padrão.

## <a name="next-steps"></a>Próximas etapas

[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/)
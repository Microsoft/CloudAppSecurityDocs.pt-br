---
title: Connect Workday to Cloud App Security (Preview)
description: This article provides information about how to connect your Workday app to Cloud App Security using the API connector for visibility and control over use.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 9/8/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 3a0756e8e2ffc9d351013b03e037fa996cbf341f
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2019
ms.locfileid: "74460992"
---
# <a name="connect-workday-to-microsoft-cloud-app-security-preview"></a>Connect Workday to Microsoft Cloud App Security (Preview)

*Aplica-se ao: Microsoft Cloud App Security*

This article provides instructions for connecting Microsoft Cloud App Security to your existing Workday account using the app connector API. This connection gives you visibility into and control over Workday use.

## <a name="prerequisites"></a>Pré-requisitos

The Workday account used for connecting to Cloud App Security must be a member of a security group (new or existing). We recommended using a Workday Integration System User. The security group must have the following permissions selected for the following domain security policies:

| Functional area | Domain Security policy | Subdomain Security policy | Permissões de relatório/tarefa | Permissões de integração |
| --- | --- | --- | --- | --- |
| System (sistema) | Set Up: Tenant Setup – General | Set Up: Tenant Setup –  Security | View, Modify | Get, Put |
| System (sistema) | Administração de Segurança | | View, Modify | Get, Put |
| System (sistema) | System auditing | | Exiba os | Get |
| Pessoal | Worker Data: Staffing | Worker Data: Public Worker Reports | Exiba os | Get |

> [!NOTE]
>
> * The account that is used to set up permissions for the security group must be a Workday Administrator.
> * To set permissions, search for "Domain Security Policies for Functional Area", then search for each functional area ("System"/"Staffing") and grant the permissions listed in the table.
> * Once all permissions have been set, search for "Activate Pending Security Policy Changes" and approve the changes.

For more information about setting up Workday integration users, security groups, and permissions, see steps 1 to 4 of the [Grant Integration or External Endpoint Access to Workday](https://go.microsoft.com/fwlink/?linkid=2103212) guide (accessible with Workday documentation/community credentials).

## <a name="how-to-connect-workday-to-cloud-app-security-using-oauth"></a>How to connect Workday to Cloud App Security using OAuth

1. Sign in to Workday with an account that is a member of the security group mentioned in the prerequisites.

1. Search for "Edit tenant setup – system", and under **User Activity Logging**, select **Enable User Activity Logging**.

    ![Screenshot of allowing user activity logging](media/connect-workday-enable-logging.png)

1. Search for "Edit tenant setup – security", and under **OAuth 2.0 Settings**, select **OAuth 2.0 Clients Enabled**.

1. Search for "Register API Client" and select **Register API Client – Task**.

1. On the **Register API Client** page, fill out the following information, and then click **OK**.

    | Nome do campo | Valor |
    | ---- | ---- |
    | Client Name | Microsoft Cloud App Security |
    | Client Grant Type | Authorization Code Grant |
    | Access Token Type | Portador |
    | Redirection URI | `https://portal.cloudappsecurity.com/api/oauth/connect` |
    | OAuth2 Scopes | **Staffing** and **System** |
    | Scope (Functional Areas) | **Staffing** and **System** |

    ![Screenshot of registering API client](media/connect-workday-register-api-client.png)

1. Once registered, make a note for the following parameters, and then click **Done**.

    * ID do Cliente
    * Client Secret
    * Workday REST API Endpoint
    * Token Endpoint
    * Authorization Endpoint

    ![Screenshot of confirming registration of API client](media/connect-workday-register-api-client-confirm.png)

1. In the Cloud App Security portal, click **Investigate** and then click **Connected Apps**.

1. In the **App connectors** page, click the plus button and then **Workday**.

    ![Screenshot of adding app connector](media/connect-workday-add-app.png)

1. In the popup, add your instance name and then click **Connect Workday**.

    ![Screenshot of adding instance name](media/connect-workday-add-app-connect.png)

1. On the next page, fill out the details with the information you noted earlier, and then click **Connect in Workday**.

    ![Screenshot of filling out app details](media/connect-workday-add-app-connect-details.png)

1. In Workday, a popup will ask you if you want to allow Cloud App Security access to your Workday account. Para continuar, clique em **Permitir**.

    ![Screenshot of authorizing access to app](media/connect-workday-add-app-allow.png)

1. Back in the Cloud App Security portal, you should see a message that Workday was successfully connected. Certifique-se de que a conexão foi bem-sucedida clicando em **Testar API**.

    O teste pode levar alguns minutos. Depois de receber uma notificação de êxito, clique em **Fechar**.

> [!NOTE]
> After connecting Workday, you'll receive events for seven days prior to connection.

## <a name="next-steps"></a>Próximas etapas

[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]

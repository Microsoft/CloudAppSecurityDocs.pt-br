---
title: Conectar o workday ao Cloud App Security
description: Este artigo fornece informações sobre como conectar seu aplicativo WORKDAY para Cloud App Security usando o conector de API para visibilidade e controle sobre o uso.
keywords: ''
author: ShlomoSagir-MS
ms.author: shsagir
manager: ShlomoSagir-MS
ms.date: 7/18/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: c626d94d-2ffd-4daf-8fa4-4b6d308cf012
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 7b591250343b97534fc4dba6b3322289b1adb4ce
ms.sourcegitcommit: d1eb8ccf09840c659ba7170a2b92cd62d9d97a02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68496721"
---
# <a name="placeholder-article"></a>Artigo de espaço reservado
<!--
# Connect Workday to Microsoft Cloud App Security

*Applies to: Microsoft Cloud App Security*

This article provides instructions for connecting Microsoft Cloud App Security to your existing Workday account using the app connector API. This connection gives you visibility into and control over Workday use.

## How to connect Workday to Cloud App Security using OAuth

1. Sign in with an Admin account to your Workday account.

1. Search for "Edit tenant setup – system", and under **User Activity Logging**, select **Enable User Activity Logging**.

    ![Screenshot of allowing user activity logging](media/connect-workday-enable-logging.png)

1. Search for "Register API Client" and select **Register API Client – Task**.

1. On the **Register API Client** page, fill out the following information, and then click **OK**.

    | Field name | Value |
    | ---- | ---- |
    | Client Name | Microsoft Cloud App Security |
    | Client Grant Type | Authorization Code Grant |
    | Access Token Type | Bearer |
    | Redirection URI | https://portal.cloudappsecurity.com/api/oauth/connect |
    | OAuth2 Scopes | **Staffing** and **System** |
    | Scope (Functional Areas) | **Staffing** and **System** |

    ![Screenshot of registering API client](media/connect-workday-register-api-client.png)

1. Once registered, make a note for the following parameters, and then click **Done**.

    - Client ID
    - Client Secret
    - Workday REST API Endpoint
    - Token Endpoint
    - Authorization Endpoint

    ![Screenshot of confirming registration of API client](media/connect-workday-register-api-client-confirm.png)

1. In the Cloud App Security portal, click **Investigate** and then click **Connected Apps**.

1. In the **App connectors** page, click the plus button and then **Workday**.

    ![Screenshot of adding app connector](media/connect-workday-add-app.png)

1. In the popup, add your instance name and then click **Connect Workday**.

    ![Screenshot of adding instance name](media/connect-workday-add-app-connect.png)

1. On the next page, fill out the details with the information you noted earlier, and then click **Connect in Workday**.

    ![Screenshot of filling out app details](media/connect-workday-add-app-connect-details.png)

1. In Workday, a popup will ask you if you want to allow Cloud App Security access to your Workday account. To proceed, click **Allow**.

    ![Screenshot of authorizing access to app](media/connect-workday-add-app-allow.png)

1. Back in the Cloud App Security console, you should see a message that Workday was successfully connected. Make sure the connection succeeded by clicking **Test API**.

    Testing may take a couple of minutes. After receiving a success notice, click **Close**.

## Next steps 
[Control cloud apps with policies](control-cloud-apps-with-policies.md)   

[Premier customers can also create a new support request directly in the Premier Portal.](https://premier.microsoft.com/)-->
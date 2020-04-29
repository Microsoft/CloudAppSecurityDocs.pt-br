---
title: Conectar o Okta ao Cloud App Security
description: Este artigo fornece informações sobre como conectar o Okta ao Cloud App Security usando o conector de API para obter visibilidade e controle sobre o uso.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 9/1/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: b86f8ef6eef534301b21371021295587c6535786
ms.sourcegitcommit: ecb1835d1cd880de38f32ce7a7031b0015f3cae5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81229717"
---
# <a name="connect-okta-to-microsoft-cloud-app-security"></a>Conectar o Okta ao Microsoft Cloud App Security

*Aplica-se a: Microsoft Cloud App Security*

Este artigo fornece instruções para conectar o Microsoft Cloud App Security à sua conta existente do Okta usando as APIs do conector. Essa conexão fornece visibilidade e controle sobre o uso do Okta. Para obter informações sobre como Cloud App Security protege o Okta, consulte [proteger o Okta](protect-okta.md).

## <a name="how-to-connect-okta-to-cloud-app-security"></a>Como conectar o Okta ao Cloud App Security

1. É recomendável que você crie uma Conta de Serviço de administrador no Okta para o Cloud App Security.

    Certifique-se de usar uma conta com permissões de Superadministrador.

    Verifique se sua conta do Okta é verificada.

1. No console do Okta, clique em **Administração**.

    - Clique em **Segurança** e em **API**.

         ![API Okta](media/okta-api.png "API Okta")

    - Clique em **Create Token (Criar Token)**.

         ![Okta criar token](media/okta-createtoken.jpg "Okta criar token")

    - No pop-up **criar token** , nomeie seu Token de Cloud app Security e clique em **criar token**.

         ![Pop-up de token Okta](media/okta-token-pop-up.png)

    - No pop-up **Token created successfully (Token criado com êxito)**, copie o **Token value (Valor do token)**.

         ![Valor do token Okta](media/okta-token-value.png "Valor do token Okta")

1. No console do Cloud App Security, clique em **Investigar** e em **Aplicativos conectados**.

1. Na **página Conectores de aplicativos**, clique no botão de mais e depois em **Okta**.

    ![conectar Okta](media/connect-okta.png "conectar Okta")

1. No pop-up que abrir, no campo **Domain (Domínio)**, insira seu domínio do Okta e cole seu token no campo **Token**.

1. Clique em **Conectar** para criar o token para o Okta no Cloud App Security.

1. Certifique-se de que a conexão foi bem-sucedida clicando em **Testar API**.

    O teste pode levar alguns minutos. Depois de receber uma notificação de êxito, clique em **Fechar**.

Depois de conectar o Okta, você receberá eventos por 60 dias antes da conexão.

Se você tiver problemas para conectar o aplicativo, consulte [Solucionando problemas de conectores de aplicativos](troubleshooting-api-connectors-using-error-messages.md).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]

---
title: Conectar o Okta ao Cloud App Security
description: Este artigo fornece informações sobre como conectar o Okta ao Cloud App Security usando o conector de API para obter visibilidade e controle sobre o uso.
keywords: ''
author: ShlomoSagir-MS
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
ms.openlocfilehash: 59798c191a90f9be252e42ff9a9d4582f7d2221e
ms.sourcegitcommit: 0b78b13bc163bfcd6f2ae13b1f57acee05e5b423
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2019
ms.locfileid: "70208817"
---
# <a name="connect-okta-to-microsoft-cloud-app-security"></a>Conectar o Okta ao Microsoft Cloud App Security

*Aplica-se a: Microsoft Cloud App Security*

Este artigo fornece instruções para conectar o Microsoft Cloud App Security à sua conta existente do Okta usando as APIs do conector. Essa conexão fornece visibilidade e controle sobre o uso do Okta.

## <a name="how-to-connect-okta-to-cloud-app-security"></a>Como conectar o Okta ao Cloud App Security

1. É recomendável que você crie uma Conta de Serviço de administrador no Okta para o Cloud App Security.

    Certifique-se de usar uma conta com permissões de Superadministrador.

    Verifique se sua conta do Okta é verificada.

1. No console do Okta, clique em **Administração**.

    - Clique em **Segurança** e em **API**.

         ![API do Okta](./media/okta-api.png "API do Okta")

    - Clique em **Create Token (Criar Token)** .

         ![Criar token do Okta](./media/okta-createtoken.jpg "Criar token do Okta")

    - No pop-up **Criar Token**, dê um nome ao token do Cloud App Security e clique em **Criar Token**.

         ![Pop-up do token do Okta](./media/okta-token-popup.png "Pop-up do token do Okta")

    - No pop-up **Token created successfully (Token criado com êxito)** , copie o **Token value (Valor do token)** .

         ![Valor do token do Okta](./media/okta-token-value.png "Valor do token do Okta")

1. No console do Cloud App Security, clique em **Investigar** e em **Aplicativos conectados**.

1. Na **página Conectores de aplicativos**, clique no botão de mais e depois em **Okta**.

    ![conectar Okta](./media/connect-okta.png "conectar Okta")

1. No pop-up que abrir, no campo **Domain (Domínio)** , insira seu domínio do Okta e cole seu token no campo **Token**.

1. Clique em **Conectar** para criar o token para o Okta no Cloud App Security.

1. Certifique-se de que a conexão foi bem-sucedida clicando em **Testar API**.

    O teste pode levar alguns minutos. Depois de receber uma notificação de êxito, clique em **Fechar**.

Depois de conectar o Okta, você receberá eventos por 60 dias antes da conexão.

## <a name="next-steps"></a>Próximas etapas

[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/)

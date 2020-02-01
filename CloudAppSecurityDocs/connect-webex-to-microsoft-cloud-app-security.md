---
title: Conectar WebEx a Cloud App Security
description: Este artigo fornece informações sobre como conectar seu aplicativo WebEx para Cloud App Security usando o conector de API para visibilidade e controle sobre o uso.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 04/16/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: f50ff4ae3b3a5a04ab9ffe052b0fb1e8ecdb2f7d
ms.sourcegitcommit: 00599ac6c64a4c62ed9ebdda3edb58f90f92c24d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912122"
---
# <a name="connect-cisco-webex-to-microsoft-cloud-app-security"></a>Conectar o Cisco WebEx ao Microsoft Cloud App Security

*Aplica-se ao: Microsoft Cloud App Security*

Este artigo fornece instruções para conectar Microsoft Cloud App Security à sua conta do Cisco WebEx existente usando as APIs do conector. Essa conexão fornece visibilidade e controle sobre usuários, atividades e arquivos WebEx. Para obter informações sobre como Cloud App Security protege o Cisco WebEx, consulte [proteger o Cisco WebEx](protect-webex.md).

## <a name="prerequisites"></a>Pré-requisitos

- Sugerimos que você crie uma conta de serviço dedicada para a conexão. Isso permite que você veja que ações de governança executadas em WebEx como sendo executadas dessa conta, como excluir mensagens enviadas no WebEx. Caso contrário, o nome do administrador que se conectou Cloud App Security ao WebEx será exibido como o usuário que realizou as ações.
- Você deve ter permissões totais de administrador **e** administrador de conformidade no WebEx.

## <a name="how-to-connect-webex-to-cloud-app-security"></a>Como conectar o WebEx ao Cloud App Security

1. No console do Cloud App Security, clique em **Investigar** e em **Aplicativos conectados**.

1. Na página **conectores de aplicativos** , clique no botão de adição seguido pelo **Cisco WebEx**.

    ![conectar WebEx](media/cisco-webex.png "conectar WebEx")

1. No pop-up, insira o nome da instância deste conector.

1. Clique em **conectar Cisco WebEx**. A página de entrada do WebEx é aberta. Insira suas credenciais para permitir que Cloud App Security acesso à instância WebEx de sua equipe.

1. WebEx pergunta se você deseja permitir Cloud App Security acesso às informações da sua equipe, ao log de atividades e executar atividades como um membro da equipe. Para continuar, clique em **Permitir**.

1. De volta ao console do Cloud App Security, você deve receber uma mensagem de que o WebEx foi conectado com êxito.

1. Certifique-se de que a conexão foi bem-sucedida clicando em **Testar API**.

    O teste pode levar alguns minutos. Depois de receber uma notificação de êxito, clique em **Fechar**.

Depois de conectar o WebEx, você receberá eventos por 7 dias antes da conexão. Cloud App Security examina eventos nos últimos três meses. Para aumentar isso, você deve ter uma licença do Cisco WebEx pro e abrir um tíquete com suporte a Cloud App Security.

Se você tiver problemas para conectar o aplicativo, consulte [Solucionando problemas de conectores de aplicativos](troubleshooting-api-connectors-using-error-messages.md).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]

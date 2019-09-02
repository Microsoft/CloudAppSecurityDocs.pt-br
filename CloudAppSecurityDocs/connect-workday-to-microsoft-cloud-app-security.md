---
title: Conectar o workday ao Cloud App Security
description: Este artigo fornece informações sobre como conectar seu aplicativo WORKDAY para Cloud App Security usando o conector de API para visibilidade e controle sobre o uso.
keywords: ''
author: ShlomoSagir-MS
ms.author: shsagir
manager: ShlomoSagir-MS
ms.date: 9/1/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 1b467600661209d299ca5f5f4079a572aa3016c2
ms.sourcegitcommit: 0b78b13bc163bfcd6f2ae13b1f57acee05e5b423
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2019
ms.locfileid: "70208934"
---
# <a name="connect-workday-to-microsoft-cloud-app-security"></a>Conectar o workday ao Microsoft Cloud App Security

*Aplica-se a: Microsoft Cloud App Security*

Este artigo fornece instruções para conectar Microsoft Cloud App Security à sua conta do workday existente usando a API do conector de aplicativos. Essa conexão fornece visibilidade e controle sobre o uso do workday.

## <a name="prerequisites"></a>Pré-requisitos

A conta workday usada para se conectar a Cloud App Security deve ser um membro de um grupo de segurança que tenha os seguintes domínios habilitados para eles:

- Administração de segurança do sistema
- Sistema-auditoria de sistema
- Equipe-dados de trabalho: Relatórios públicos de trabalho

Recomendamos o uso de um usuário do sistema de integração do workday.

## <a name="how-to-connect-workday-to-cloud-app-security-using-oauth"></a>Como conectar o workday ao Cloud App Security usando o OAuth

1. Entre com uma conta de administrador para sua conta do workday.

1. Pesquise "Editar configuração de locatário – sistema" e, em **log de atividades do usuário**, selecione **habilitar log de atividades do usuário**.

    ![Captura de tela de permitir o log de atividades do usuário](media/connect-workday-enable-logging.png)

1. Pesquise "Editar configuração de locatário – segurança" e, em **configurações do OAuth 2,0**, selecione **clientes OAuth 2,0 habilitados**.

1. Pesquise "registrar cliente de API" e selecione **registrar cliente de API – tarefa**.

1. Na página **registrar cliente de API** , preencha as informações a seguir e clique em **OK**.

    | Nome do campo | Valor |
    | ---- | ---- |
    | Nome do cliente | Microsoft Cloud App Security |
    | Tipo de concessão de cliente | Concessão de código de autorização |
    | Tipo de token de acesso | Portador |
    | URI de redirecionamento | `https://portal.cloudappsecurity.com/api/oauth/connect` |
    | Escopos OAuth2 | **Equipe** e **sistema** |
    | Escopo (áreas funcionais) | **Equipe** e **sistema** |

    ![Captura de tela do registro do cliente de API](media/connect-workday-register-api-client.png)

1. Depois de registrado, anote os parâmetros a seguir e clique em **concluído**.

    - ID do cliente
    - Segredo do cliente
    - Ponto de extremidade da API REST do workday
    - Ponto de extremidade do token
    - Ponto de extremidade de autorização

    ![Captura de tela de confirmando o registro do cliente de API](media/connect-workday-register-api-client-confirm.png)

1. No portal de Cloud App Security, clique em **investigar** e em **aplicativos conectados**.

1. Na página **conectores de aplicativos** , clique no botão de adição e, em seguida, em **workday**.

    ![Captura de tela da adição do conector de aplicativos](media/connect-workday-add-app.png)

1. No pop-up, adicione o nome da instância e clique em **conectar workday**.

    ![Captura de tela da adição do nome da instância](media/connect-workday-add-app-connect.png)

1. Na próxima página, preencha os detalhes com as informações anotadas anteriormente e clique em **conectar no workday**.

    ![Captura de tela de preenchimento de detalhes do aplicativo](media/connect-workday-add-app-connect-details.png)

1. No workday, um pop-up perguntará se você deseja permitir Cloud App Security acesso à sua conta do workday. Para continuar, clique em **Permitir**.

    ![Captura de tela da autorização do acesso ao aplicativo](media/connect-workday-add-app-allow.png)

1. De volta ao portal de Cloud App Security, você deverá ver uma mensagem informando que o workday foi conectado com êxito. Certifique-se de que a conexão foi bem-sucedida clicando em **Testar API**.

    O teste pode levar alguns minutos. Depois de receber uma notificação de êxito, clique em **Fechar**.

> [!NOTE]
> Depois de conectar o workday, você receberá eventos por sete dias antes da conexão.

## <a name="next-steps"></a>Próximas etapas

[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/)

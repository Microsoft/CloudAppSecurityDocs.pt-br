---
title: Conectar o workday ao Cloud App Security (versão prévia)
description: Este artigo fornece informações sobre como conectar seu aplicativo WORKDAY para Cloud App Security usando o conector de API para visibilidade e controle sobre o uso.
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
ms.openlocfilehash: b31876240187e3f95ff2a8d10632b54de37e6ed6
ms.sourcegitcommit: 7c93b6f93d2699d466b172590710ed01697bbdad
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74720754"
---
# <a name="connect-workday-to-microsoft-cloud-app-security-preview"></a>Conectar o workday ao Microsoft Cloud App Security (versão prévia)

*Aplica-se ao: Microsoft Cloud App Security*

Este artigo fornece instruções para conectar Microsoft Cloud App Security à sua conta do workday existente usando a API do conector de aplicativos. Essa conexão fornece visibilidade e controle sobre o uso do workday.

## <a name="prerequisites"></a>Pré-requisitos

A conta workday usada para se conectar a Cloud App Security deve ser membro de um grupo de segurança (novo ou existente). Recomendamos o uso de um usuário do sistema de integração do workday. O grupo de segurança deve ter as seguintes permissões selecionadas para as seguintes políticas de segurança de domínio:

| Área funcional | Política de segurança de domínio | Política de segurança de subdomínio | Permissões de relatório/tarefa | Permissões de integração |
| --- | --- | --- | --- | --- |
| System (sistema) | Configurar: configuração do locatário – geral | Configuração: configuração do locatário – segurança | Exibir, modificar | Obter, colocar |
| System (sistema) | Administração de Segurança | | Exibir, modificar | Obter, colocar |
| System (sistema) | Auditoria do sistema | | Exiba os | Get |
| Pessoal | Dados de trabalho: pessoal | Dados de trabalho: relatórios de trabalho públicos | Exiba os | Get |

> [!NOTE]
>
> * A conta usada para configurar permissões para o grupo de segurança deve ser um administrador do workday.
> * Para definir permissões, pesquise "políticas de segurança de domínio para a área funcional" e procure cada área funcional ("sistema"/"equipe") e conceda as permissões listadas na tabela.
> * Depois que todas as permissões tiverem sido definidas, pesquise "ativar alterações de política de segurança pendentes" e aprove as alterações.

Para obter mais informações sobre como configurar usuários de integração do workday, grupos de segurança e permissões, consulte as etapas 1 a 4 da [integração de concessão ou acesso de ponto de extremidade externo ao](https://go.microsoft.com/fwlink/?linkid=2103212) guia do workday (acessível com documentação/credenciais da Comunidade).

## <a name="how-to-connect-workday-to-cloud-app-security-using-oauth"></a>Como conectar o workday ao Cloud App Security usando o OAuth

1. Entre no workday com uma conta que seja membro do grupo de segurança mencionado nos pré-requisitos.

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

    * ID do Cliente
    * Segredo do cliente
    * Ponto de extremidade da API REST do workday
    * Ponto de extremidade do token
    * Ponto de extremidade de autorização

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

> [!div class="nextstepaction"]
> [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]

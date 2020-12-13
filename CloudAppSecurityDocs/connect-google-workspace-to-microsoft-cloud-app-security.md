---
title: Conectar o Google Workspace ao Cloud App Security
description: Este artigo fornece informações sobre como conectar seu Google Workspace ao Cloud App Security usando o conector de API para visibilidade e controle sobre o uso.
ms.date: 11/27/2019
ms.topic: how-to
ms.openlocfilehash: 5c2385f59572434b07730213232c6701589a654f
ms.sourcegitcommit: 72ddcd0f9a83251d588009abf506676612c50267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/13/2020
ms.locfileid: "97370376"
---
# <a name="connect-google-workspace-to-microsoft-cloud-app-security"></a>Conectar o Google Workspace ao Microsoft Cloud App Security

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Este artigo fornece instruções para conectar Microsoft Cloud App Security à sua conta existente do Google Workspace usando as APIs do conector. Essa conexão fornece visibilidade e controle sobre o uso do Google Workspace. Para obter informações sobre como Cloud App Security protege o Google Workspace, consulte [proteger o Google Workspace](protect-google-workspace.md).

## <a name="configure-google-workspace"></a>Configurar o Google Workspace

1. Como um superadministrador do Google Workspace, entre no <a href="https://cloud.google.com/console/project" target="_blank">https://cloud.google.com/console/project</a> .

1. Clique em **Criar projeto** para iniciar um novo projeto.

    ![Criar projeto do Google](media/connect-google-workspace/google-workspace-create-new-project.png)

1. Na página **novo projeto** , nomeie o projeto da seguinte maneira: **Cloud app Security** e clique em **criar**.

    ![Pop-up do novo projeto do Google](media/connect-google-workspace/google-workspace-create-new-project-popup.png)

1. Depois que o projeto for criado, na barra de ferramentas, clique em **Google Cloud Platform**. Verifique se o projeto certo foi selecionado no menu suspenso na parte superior.

    ![Clique em Google Cloud Platform na barra de ferramentas](media/connect-google-workspace/google-workspace-verify-project.png)

1. Selecione menu, vá para **APIs &**  >  **biblioteca** de serviços e habilite as seguintes APIs (use a linha de pesquisa se a API não estiver listada):

    - API do SDK do admin

    - Audit API (API de Auditoria)
    - API do Google Drive
    - SDK do Marketplace do Google Workspace

    > [!NOTE]
    > Para cada API, clique em **habilitar para ativar** a ti.
    >
    > ![habilitar o Google APPI](media/connect-google-workspace/google-workspace-api.png)
    >
    > Ignore o aviso **Credentials (Credenciais)** por enquanto.

1. Selecione menu, vá para **APIs &**  >  **painel** de serviços e verifique se você tem as seguintes APIs habilitadas:

    - API do SDK do admin

    - Audit API (API de Auditoria)
    - API do Google Drive
    - SDK do Marketplace do Google Workspace

1. Na página **da página de consentimento do OAuth** , faça o seguinte:
    1. Em **tipo de usuário**, escolha **externo** e, em seguida, clique em **criar**.

        ![Tipo de usuário de consentimento do Google OAuth](media/connect-google-workspace/google-workspace-oauth-consent-user-type.png)

    1. Preencha as informações a seguir e clique em **salvar**.

        | Nome do campo | Valor |
        | --- | --- |
        | Tipo de aplicativo | Público |
        | Nome do aplicativo | Microsoft Cloud App Security |
        | Email de suporte | `<your_email_address>` |

        Todos os outros campos são opcionais.

        ![Tipo de aplicativo de consentimento do Google OAuth](media/connect-google-workspace/google-workspace-oauth-consent-app-type.png)

1. Na página **credenciais** , faça o seguinte:
    1. Selecione **criar credenciais** e, em seguida, selecione **conta de serviço**.
    1. Em **detalhes da conta de serviço**, forneça um nome e uma descrição e, em seguida, clique em **criar**.
    1. Em **conceder a essa conta de serviço acesso ao projeto**, para **função** , selecione **projeto**, selecione **Editor** e, em seguida, clique em **concluído**.

    ![Conta de serviço do Google Create](media/connect-google-workspace/google-workspace-create-service-account.png)

1. Na página **conta de serviço** , faça o seguinte:
    1. Em **contas de serviço**, localize e edite a conta de serviço que você criou anteriormente.

        ![Conta de serviço do Google Edit](media/connect-google-workspace/google-workspace-edit-service-account.png)

    1. Faça uma cópia do endereço de email. Você precisará dessas informações posteriormente.
    1. Em **chaves**, no menu **Adicionar chave** , selecione **criar nova chave**, selecione **P12** e clique em **criar**. Salve o arquivo baixado, você precisará dele mais tarde.
    1. Em **status da conta de serviço**, selecione **habilitar delegação do G Suite em todo o domínio** e clique em **salvar**.

    ![Conta do serviço de atualização do Google](media/connect-google-workspace/google-workspace-update-service-account.png)

1. Na página **credenciais** , em **IDs de cliente do OAuth 2,0**, copie a **ID do cliente** atribuída à sua conta de serviço-você precisará dela mais tarde.

    ![Conta de serviço de credenciais do Google Workspace](media/connect-google-workspace/google-workspace-copy-service-account-client-id.png)

1. Acesse [admin.google.com](https://admin.google.com/) e navegue até controles de API de **segurança**  >    >  **gerenciar delegação em todo o domínio**, clique em **Adicionar novo** e faça o seguinte:

    1. Na caixa **ID do cliente** , insira a **ID do cliente** que você copiou anteriormente.
    1. Na caixa **escopos do OAuth** , insira a seguinte lista de escopos necessários (Copie o texto e cole-o na caixa):  
    `https://www.googleapis.com/auth/admin.reports.audit.readonly,https://www.googleapis.com/auth/admin.reports.usage.readonly,https://www.googleapis.com/auth/drive,https://www.googleapis.com/auth/drive.appdata,https://www.googleapis.com/auth/drive.apps.readonly,https://www.googleapis.com/auth/drive.file,https://www.googleapis.com/auth/drive.metadata.readonly,https://www.googleapis.com/auth/drive.readonly,https://www.googleapis.com/auth/drive.scripts,https://www.googleapis.com/auth/admin.directory.user.readonly,https://www.googleapis.com/auth/admin.directory.user.security,https://www.googleapis.com/auth/admin.directory.user.alias,https://www.googleapis.com/auth/admin.directory.orgunit,https://www.googleapis.com/auth/admin.directory.notifications,https://www.googleapis.com/auth/admin.directory.group.member,https://www.googleapis.com/auth/admin.directory.group,https://www.googleapis.com/auth/admin.directory.device.mobile.action,https://www.googleapis.com/auth/admin.directory.device.mobile,https://www.googleapis.com/auth/admin.directory.user`

    1. Clique em **autorizar**.

    ![Adicionar novo ID de cliente ao Google Workspace](media/connect-google-workspace/google-workspace-add-new-client-id.png)

## <a name="configure-cloud-app-security"></a>Configurar o Microsoft Cloud App Security

1. No portal do Cloud App Security, clique em **Investigar** e em **Aplicativos conectados**.

1. Para fornecer os detalhes de conexão do Google Workspace, em **conectores de aplicativos**, siga um destes procedimentos:

    **Para uma organização do Google Workspace que já tem uma instância GCP conectada**

    - Na lista de conectores, no final da linha em que a instância GCP é exibida, clique nos três pontos e, em seguida, clique em **Adicionar Google Workspace**.

    **Para uma organização do Google Workspace que ainda não tem uma instância GCP conectada**

    - Na página **aplicativos conectados** , clique no sinal de adição e selecione **Google Workspace**.

1. No pop-up, preencha as seguintes informações:

    ![Configuração do Google Workspace no Cloud App Security](media/connect-google-workspace/cas-config-google-workspace.png "Configuração do Google Workspace no Cloud App Security")

    1. Insira a **ID da conta de serviço**, o **email** que você copiou anteriormente.

    1. Insira o **número do projeto (ID do aplicativo)** que você copiou anteriormente.

    1. Carregue o arquivo de **certificado** P12 que você salvou anteriormente.

    1. Insira um **email de conta de administrador** de seu administrador do Google Workspace.

    1. Se você tiver uma conta comercial ou empresarial do Google Workspace, marque essa caixa de seleção. Para obter informações sobre quais recursos estão disponíveis no Cloud App Security para o Google Workspace Business ou Enterprise, consulte [habilitar ações instantâneas de visibilidade, proteção e governança para seus aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

    1. Clique em **Salvar alterações**.

    1. **Siga o link** para se conectar ao Google Workspace. Isso abre o Google Workspace e você será solicitado a autorizar o acesso para Cloud App Security.

    1. Certifique-se de que a conexão foi bem-sucedida clicando em **Testar agora**.  
    O teste pode levar alguns minutos.  
    Depois de receber um aviso de êxito, clique em **concluído** e feche a página do Google Workspace.

Depois de conectar o Google Workspace, você receberá eventos de 60 dias antes da conexão.

Depois de conectar o Google Workspace, Cloud App Security executa uma verificação completa. Dependendo de quantos arquivos e usuários você tiver, a verificação completa poderá levar algum tempo. Para habilitar a verificação quase em tempo real, os arquivos nos quais a atividade é detectada são movidos para o início da fila de verificação. Por exemplo, um arquivo editado, atualizado ou compartilhado é verificado imediatamente. Isso não é aplicável a arquivos que não são modificados por natureza. Por exemplo, os arquivos que são exibidos, visualizados, impressos ou exportados são verificados durante a verificação regular.

Se você tiver problemas para conectar o aplicativo, consulte [Solucionando problemas de conectores de aplicativos](troubleshooting-api-connectors-using-error-messages.md).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]

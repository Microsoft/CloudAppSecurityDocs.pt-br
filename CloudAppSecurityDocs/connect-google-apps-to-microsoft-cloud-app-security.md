---
title: Conectar o G Suite ao Cloud App Security
description: Este artigo fornece informações sobre como conectar o G Suite ao Cloud App Security usando o conector de API para obter visibilidade e controle sobre o uso.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 11/27/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 06c6a2db19332bb49e86220464a7eff459657b4b
ms.sourcegitcommit: 00599ac6c64a4c62ed9ebdda3edb58f90f92c24d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912272"
---
# <a name="connect-g-suite-to-microsoft-cloud-app-security"></a>Conectar o G Suite ao Microsoft Cloud App Security

*Aplica-se ao: Microsoft Cloud App Security*

Este artigo fornece instruções para conectar o Microsoft Cloud App Security à sua conta existente do G Suite usando as APIs do conector. Essa conexão fornece visibilidade e controle sobre o uso do G Suite. Para obter informações sobre como Cloud App Security protege o G Suite, consulte [proteger g Suite](protect-gsuite.md).

## <a name="configure-g-suite"></a>Configurar G Suite

1. Como um Superadministrador do G Suite, entre em <a href="https://cloud.google.com/console/project" target="_blank">https://cloud.google.com/console/project</a>.

1. Clique em **Criar projeto** para iniciar um novo projeto.

    ![google1](media/google1.png)

1. Na tela **novo projeto** , nomeie o projeto da seguinte maneira: **Cloud app Security** e clique em **criar**.

    ![google2](media/google2.png)

1. Depois que o projeto for criado, na barra de ferramentas, clique em **Google Cloud Platform**. Verifique se o projeto certo foi selecionado no menu suspenso na parte superior.

    ![projeto do Google](media/googleverify-project.png)

1. Selecione menu, vá para **APIs & serviços** > **biblioteca** e habilite as seguintes APIs (use a linha de pesquisa se a API não estiver listada):

    * Admin SDK (SDK de Administração)

    * Audit API (API de Auditoria)

    * API do Google Drive

    * SDK do Marketplace do G Suite  
![APIs do Google](media/google4.png)

    > [!NOTE]
    > Para cada API, clique em **habilitar para ativar** a ti.
    >
    > ![habilitar o Google APPI](media/google-api.png)
    >
    > Ignore o aviso **Credentials (Credenciais)** por enquanto.

1. Selecione menu, vá para **APIs & serviços** > **painel**e verifique se você tem as seguintes APIs habilitadas:

    ![APIs habilitadas para Google](media/google5.png)

1. Vá para a guia de **tela de consentimento do OAuth** .

    * Em **nome do aplicativo**, digite **Microsoft Cloud app Security**.

    * Todos os outros campos são opcionais.

    * Clique em **Salvar**.

    ![Consentimento do Google OAuth](media/google-oauth-consent.png)

1. Na tela **credenciais** , clique na seta ao lado de **criar credenciais**e selecione **chave de conta de serviço**.

    ![Credenciais do Google](media/google7.png)

1. Para **conta de serviço**, escolha **nova conta de serviço**e forneça um nome para a conta, por exemplo, conta de **serviço 1**. Em **Função**, escolha **Projeto** e, depois, **Editor**. Em **Tipo de chave**, escolha **P12** e clique em **Criar**. Um arquivo de certificado P12 é salvo em seu computador.

    ![Criar chave de conta de serviço no Google](media/google9.png)

1. Na tela **Credentials (Credenciais)** , clique em **Manage service accounts (Gerenciar contas de serviço)** na extrema direita. Copie o **email** atribuído à sua conta de serviço-você precisará dele mais tarde.

    ![Conta de serviço de credenciais do G Suite](media/google10.png)

1. Clique nos três pontos à direita da conta de serviço que você criou e selecione **Editar**.

    ![edição do Google](media/google11.png "edição do Google")

1. Clique em **Mostrar delegação em todo o domínio**, selecione **habilitar delegação do G Suite domínio-todo**.

    ![ID do cliente do Google](media/google12.png "google12")

    1. Copie a **ID do cliente** -você precisará dela mais tarde.
    ![gerenciar o acesso de cliente de API](media/google12-2.png "google12-2")

    1. Clique em **salvar**

    1. Vá para [admin.google.com](https://admin.google.com/) e, em seguida, escolha **Segurança**.

    1. Expanda **Configurações avançadas**e, em **autenticação**, selecione **gerenciar acesso de cliente de API**.

    1. Na caixa **nome do cliente** , insira a **ID do cliente** que você copiou anteriormente.  

    1. Na caixa **um ou mais escopos de API** , insira a seguinte lista de escopos necessários (Copie o texto e cole-o na caixa):  
`https://www.googleapis.com/auth/admin.reports.audit.readonly,https://www.googleapis.com/auth/admin.reports.usage.readonly,https://www.googleapis.com/auth/drive,https://www.googleapis.com/auth/drive.appdata,https://www.googleapis.com/auth/drive.apps.readonly,https://www.googleapis.com/auth/drive.file,https://www.googleapis.com/auth/drive.metadata.readonly,https://www.googleapis.com/auth/drive.readonly,https://www.googleapis.com/auth/drive.scripts,https://www.googleapis.com/auth/admin.directory.user.readonly,https://www.googleapis.com/auth/admin.directory.user.security,https://www.googleapis.com/auth/admin.directory.user.alias,https://www.googleapis.com/auth/admin.directory.orgunit,https://www.googleapis.com/auth/admin.directory.notifications,https://www.googleapis.com/auth/admin.directory.group.member,https://www.googleapis.com/auth/admin.directory.group,https://www.googleapis.com/auth/admin.directory.device.mobile.action,https://www.googleapis.com/auth/admin.directory.device.mobile,https://www.googleapis.com/auth/admin.directory.user`

    1. Clique em **autorizar**.

1. Na [Google Cloud Platform](https://console.cloud.google.com/), selecione menu e vá para **APIs e serviços** > **painel**.

1. No painel, role para baixo até a lista de APIs habilitadas e clique em **API do Google Drive**.
    ![selecionar o Google Drive](media/google14.png)

1. Clique na **Integração de interface do usuário da unidade** e preencha as informações a seguir:

    * **Application Name (Nome do Aplicativo)** : Microsoft Cloud App Security.

    * **Short Description & Long Description (Descrição curta e descrição longa)** (opcional): o Microsoft Cloud App Security fornece a visibilidade dos aplicativos de nuvem, ajudando a controlar, investigar e administrar o uso do aplicativo de nuvem, proteger dados corporativos e detectar atividades suspeitas para qualquer aplicativo de nuvem.

    * O Google exige que você carregue pelo menos um ícone do aplicativo. Acesse [https://go.microsoft.com/fwlink/?linkid=862826](https://go.microsoft.com/fwlink/?linkid=862826) para baixar um arquivo zip que contém os ícones do Cloud App Security. Em seguida, no **ícone do aplicativo**, clique em **Selecionar** ao lado da imagem 128x128 e arraste-a para a tela pop-up. Clique em **Selecionar** ao lado da imagem 32x32 e arraste-a para a tela pop-up.

    * Role para baixo e, na seção **integração de unidade** , digite a seguinte URL em **abrir url:** 
    `https://portal.cloudappsecurity.com/#/services/11770?tab=files`

    ![Editar o Google Drive](media/google15.png)

1. Clique em **Enviar**.

1. Volte para a lista **APIs habilitadas**. Clique no **SDK do Marketplace do G Suite**.

1. Selecione a guia **Configuração**.

    1. Copie o **Número do projeto (ID do Aplicativo)** que aparece na parte superior para usar mais tarde.

    1. No **Nome do Aplicativo** digite o **Microsoft Cloud App Security**.  
Na **Descrição do aplicativo** digite "O Microsoft Cloud App Security fornece visibilidade dos aplicativos de nuvem, ajudando a controlar, investigar e administrar o uso do aplicativo de nuvem, proteger dados corporativos e detectar atividades suspeitas para qualquer aplicativo de nuvem”.

    1. Verifique se você clicou em **Concluído** na janela **Novo item**.

    ![novo item do Google](media/google-new-item.png)

    * Desmarque a caixa de seleção **habilitar instalação individual** .

    * Configure as quatro imagens necessárias em **Application icons (Ícones de aplicativo)** .

    As imagens podem ser encontradas em: [https://go.microsoft.com/fwlink/?linkid=862826](https://go.microsoft.com/fwlink/?linkid=862826)

    * Preencha as seguintes **Support URLs (URLs de suporte)** :

    * **URL dos Termos de serviço**: https://go.microsoft.com/fwlink/?LinkID=733268

    * **URL da Política de privacidade**: https://go.microsoft.com/fwlink/?LinkId=512132

    * Em **Escopos do OAuth 2.0**, copie e cole as seguintes URLs (copie-as uma por uma e pressione Enter após cada uma):  
`https://www.googleapis.com/auth/admin.reports.audit.readonly`  
`https://www.googleapis.com/auth/admin.reports.usage.readonly`  
`https://www.googleapis.com/auth/drive`  
`https://www.googleapis.com/auth/drive.appdata`  
`https://www.googleapis.com/auth/drive.apps.readonly`  
`https://www.googleapis.com/auth/drive.file`  
`https://www.googleapis.com/auth/drive.metadata.readonly`  
`https://www.googleapis.com/auth/drive.readonly`  
`https://www.googleapis.com/auth/drive.scripts`  
`https://www.googleapis.com/auth/admin.directory.user.readonly`  
`https://www.googleapis.com/auth/admin.directory.user.security`  
`https://www.googleapis.com/auth/admin.directory.user.alias`  
`https://www.googleapis.com/auth/admin.directory.orgunit`  
`https://www.googleapis.com/auth/admin.directory.notifications`  
`https://www.googleapis.com/auth/admin.directory.group.member`  
`https://www.googleapis.com/auth/admin.directory.group`  
`https://www.googleapis.com/auth/admin.directory.device.mobile.action`  
`https://www.googleapis.com/auth/admin.directory.device.mobile`  
`https://www.googleapis.com/auth/admin.directory.user`

    * Em **Visibilidade**, selecione **Meu domínio** (não público).
    * Clique em **Save Changes (Salvar Alterações)** .
        ![](media/google-visibility.png) de visibilidade do Google
1. No console de administração do Google, vá para [gerenciar o controle de acesso do aplicativo](https://admin.google.com/). Localize a linha de **administrador do G Suite** e verifique se ela tem acesso **irrestrito** .

    ![segurança do Google](media/googlesec.png)

## <a name="configure-cloud-app-security"></a>Configurar o Microsoft Cloud App Security

1. No portal do Cloud App Security, clique em **Investigar** e em **Aplicativos conectados**.

1. Para fornecer os detalhes de conexão do G Suite, em **conectores de aplicativos**, siga um destes procedimentos:

    **Para uma organização do G Suite que já tem uma instância GCP conectada**

    * Na lista de conectores, no final da linha em que a instância GCP é exibida, clique nos três pontos e, em seguida, clique em **Adicionar G Suite**.

    **Para uma organização do G Suite que ainda não tem uma instância GCP conectada**

    * Na página **Aplicativos conectados**, clique no sinal de mais e selecione **G Suite**.

1. No pop-up, preencha as seguintes informações:

    ![Configuração do G Suite no Cloud App Security](media/gsuite-config-cas.png "Configuração do G Suite no Cloud App Security")

    1. Insira a **ID da conta de serviço**, o **email** que você copiou anteriormente.

    1. Insira o **número do projeto (ID do aplicativo)** que você copiou anteriormente.

    1. Carregue o arquivo de **certificado** P12 que você salvou anteriormente.

    1. Insira um **email da conta do administrador** do seu administrador do G Suite.

    1. Se você tiver uma conta do G Suite Business ou Enterprise, marque essa caixa de seleção. Para saber mais sobre quais recursos estão disponíveis no Cloud App Security para o G Suite Business ou Enterprise, confira [Habilitar ações de visibilidade, proteção e governança instantâneas para seus aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

    1. Clique em **Salvar configurações**.

    1. **Siga o link** para se conectar ao G Suite. Isso abre o G Suite e você deverá autorizar o acesso para o Cloud App Security.

    1. Certifique-se de que a conexão foi bem-sucedida clicando em **Testar agora**.  
    O teste pode levar alguns minutos.  
    Depois de receber uma notificação de êxito, clique em **Concluído** e feche a página do G Suite.

Depois de conectar o G Suite, você receberá eventos por 60 dias antes da conexão.

Após conectar o G Suite, o Cloud App Security realiza uma verificação completa. Dependendo de quantos arquivos e usuários você tiver, a verificação completa poderá levar algum tempo. Para habilitar a verificação quase em tempo real, os arquivos nos quais a atividade é detectada são movidos para o início da fila de verificação. Por exemplo, um arquivo editado, atualizado ou compartilhado é verificado imediatamente. Isso não é aplicável a arquivos que não são modificados por natureza. Por exemplo, os arquivos que são exibidos, visualizados, impressos ou exportados são verificados durante a verificação regular.

Se você tiver problemas para conectar o aplicativo, consulte [Solucionando problemas de conectores de aplicativos](troubleshooting-api-connectors-using-error-messages.md).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]

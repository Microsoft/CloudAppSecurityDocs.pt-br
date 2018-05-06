---
title: Conectar o G Suite ao Cloud App Security para obter visibilidade e controle de uso | Microsoft Docs
description: Este tópico fornece informações sobre como conectar o G Suite ao Cloud App Security usando o conector de API.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/22/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: b938e1e0-356d-4cc6-ba4a-862c0c59d709
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 670d5f479d53741d4cd047b9ad9c864e1239d5d8
ms.sourcegitcommit: 45311f2cafef79483e40d971a4c61c7673834d96
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2018
---
*Aplica-se ao: Microsoft Cloud App Security*

# <a name="connect-g-suite-to-microsoft-cloud-app-security"></a>Conectar o G Suite ao Microsoft Cloud App Security
Esta seção fornece instruções para conectar o Microsoft Cloud App Security à sua conta do G Suite existente usando as APIs do conector.
  
  
## <a name="configure-g-suite"></a>Configurar G Suite  
  
1. Como um Superadministrador do G Suite, faça logon em <a href="https://cloud.google.com/console/project" target="_blank">https://cloud.google.com/console/project</a>.  
  
2. Clique em **Criar projeto** para iniciar um novo projeto.  
  
    ![google1](./media/google1.png "google1")  
  
3. Na tela **Novo projeto**, nomeie o projeto da seguinte maneira:</br>
   **Microsoft Cloud App Security** e clique em **Criar**.  
          ![google2](./media/google2.png "google2")  
  
4. Depois que o projeto tiver sido criado, na barra de ferramentas, clique em **Google Cloud Platform** e certifique-se de que o projeto correto está selecionado na lista suspensa na parte superior.
       
      ![google project](./media/googleverify-project.png "googleverify project")  

5. Em **APIs**, clique **Ir para visão geral das APIs**.  
  
     ![google3](./media/google3.png "google3")  
  
6. Em **API**, desabilite todas as APIs listadas.  
      
7. Clique em **Biblioteca** e habilite as seguintes APIs (use a linha de pesquisa se a API não aparecer na lista **APIs Populares**):  
     
   -   Admin SDK (SDK de Administração)  
  
   -   Audit API (API de Auditoria)  
  
   -   API do Google Drive  
  
   -   SDK do Marketplace de Aplicativos  
  
   -   Gmail API (API do Gmail)  
            
   ![APIs Google](./media/google4.png "google4")  
  
   > [!NOTE]  
   >  Ignore o aviso **Credentials (Credenciais)** por enquanto.  

8. Clique em Habilitar para cada API.
     ![Habilitar API do Google ](./media/google-api.png "google-api")  
9. Você deve ter cinco **APIs habilitadas**, portanto, desabilitar quaisquer outras APIs:
  
     ![APIs habilitadas para Google](./media/google5.png "google5")  
  
10. Clique em **Credenciais** e, em seguida, selecione a guia **Tela de consentimento do OAuth**.
  
    - Em **Product name shown to users (Nome do produto mostrado aos usuários)**, digite **Microsoft Cloud App Security**.  
  
    - Todos os outros campos são opcionais.  
  
    - Clique em **Salvar**.  
  
      ![Nome do produto Google](./media/google6.png "google6")  
  
11. Na guia **Credenciais**, clique na seta ao lado de **Criar credenciais**.  
  
     ![Credenciais do Google](./media/google7.png "google7")  

12. Selecione **Chave de conta de serviço**.

     ![Chave da conta de serviço do Google](./media/google8.png "google8")  
  
13. Em **Criar chave de conta de serviço**, selecione **Nova conta de serviço** e digite qualquer nome, por exemplo **Conta de serviço 1**. Em **Função**, escolha **Projeto** e, depois, **Editor**. Em **Tipo de chave**, escolha **P12** e clique em **Criar**. Um arquivo de certificado P12 é salvo em seu computador.
 
     ![Criar chave da conta de serviço no Google](./media/google9.png "google9")  
  
14. Copie a **ID da conta de serviço** atribuída ao seu serviço, você precisará dela mais tarde.    
        
15. Na tela **Credentials (Credenciais)**, clique em **Manage service accounts (Gerenciar contas de serviço)** na extrema direita.  
     
    ![conta de serviço de credenciais do G Suite](./media/google10.png "conta de serviço de credenciais do G Suite")  
  
16. Clique nos três pontos à direita da conta de serviço que você criou e selecione **Editar**.  
  
     ![Editar Google](./media/google11.png "google edit")  
  
17. Marque a caixa de seleção **Habilitar a delegação em todo o domínio do G Suite** e clique em **Salvar**.  
  
     ![ID da conta de serviço do Google](./media/google12.png "google12")  
  
18. Abra o menu do Google clicando nas três linhas horizontais ao lado de Google Cloud Platform na barra de título. Clique em **Google Cloud Platform** e, em seguida, clique na guia **APIs e serviços** no menu à esquerda.  
    
19. No painel que abre, role para baixo até a lista de APIs habilitadas e clique na **API do Google Drive**.   
       ![Selecione Google Drive](./media/google14.png "google14")  

20. Clique na **Integração de interface do usuário da unidade** e preencha as informações a seguir:

    - **Application Name (Nome do Aplicativo)**: Microsoft Cloud App Security.  
  
    - **Short Description & Long Description (Descrição curta e descrição longa)** (opcional): o Microsoft Cloud App Security fornece a visibilidade dos aplicativos de nuvem, ajudando a controlar, investigar e administrar o uso do aplicativo de nuvem, proteger dados corporativos e detectar atividades suspeitas para qualquer aplicativo de nuvem.  
  
    - O Google exige que você carregue pelo menos um ícone do aplicativo. Acesse [https://go.microsoft.com/fwlink/?linkid=862826](https://go.microsoft.com/fwlink/?linkid=862826) para baixar um arquivo zip que contém os ícones do Cloud App Security. Em seguida, no **ícone do aplicativo**, clique em **Selecionar** ao lado da imagem 128x128 e arraste-a para a tela pop-up. Clique em **Selecionar** ao lado da imagem 32x32 e arraste-a para a tela pop-up.  
  
    - Role para baixo na seção **Integração de unidade**, digite a seguinte URL em **Abrir URL:**  
  
       https://portal.cloudappsecurity.com/#/services/11770?tab=files  
    
      ![Editar o Google Drive](./media/google15.png "google15")  

21. Clique em **Salvar alterações**.

22. Volte para a lista **APIs habilitadas**. Clique em **SDK do Marketplace de Aplicativos**. 
      
23. Selecione a guia **Configuração**. 
  
    -   Copie o **Número do projeto (ID do Aplicativo)** que aparece na parte superior para usar mais tarde.  
  
    -   No **Nome do Aplicativo** digite o **Microsoft Cloud App Security**.
  
         Na **Descrição do aplicativo** digite "O Microsoft Cloud App Security fornece visibilidade dos aplicativos de nuvem, ajudando a controlar, investigar e administrar o uso do aplicativo de nuvem, proteger dados corporativos e detectar atividades suspeitas para qualquer aplicativo de nuvem”.  
  
    -   Desmarque a caixa de seleção **Enable individual install (Habilitar instalação individual)**.  
  
    -   Configure as quatro imagens necessárias em **Application icons (Ícones de aplicativo)**.  
  
         As imagens podem ser encontradas em: [https://go.microsoft.com/fwlink/?linkid=862826](https://go.microsoft.com/fwlink/?linkid=862826)  
  
    -   Preencha as seguintes **Support URLs (URLs de suporte)**:  
  
        -   **URL dos Termos de serviço**: http://go.microsoft.com/fwlink/?LinkID=733268  
  
        -   **URL da Política de privacidade**: http://go.microsoft.com/fwlink/?LinkId=512132  
  
    -   Em **Escopos do OAuth 2.0**, copie e cole as seguintes URLs (copie-as uma por uma e pressione Enter após cada uma):  
  
           https://www.googleapis.com/auth/admin.reports.audit.readonly  
  
           https://www.googleapis.com/auth/admin.reports.usage.readonly  
  
           https://www.googleapis.com/auth/drive  
  
           https://www.googleapis.com/auth/drive.appdata  
  
           https://www.googleapis.com/auth/drive.apps.readonly  
  
           https://www.googleapis.com/auth/drive.file  
  
           https://www.googleapis.com/auth/drive.metadata.readonly  
  
           https://www.googleapis.com/auth/drive.readonly  
  
           https://www.googleapis.com/auth/drive.scripts  
  
           https://www.googleapis.com/auth/admin.directory.user.readonly  
  
           https://www.googleapis.com/auth/admin.directory.user.security  
  
           https://www.googleapis.com/auth/admin.directory.user.alias  
  
           https://www.googleapis.com/auth/admin.directory.orgunit  
  
           https://www.googleapis.com/auth/admin.directory.notifications  
  
           https://www.googleapis.com/auth/admin.directory.group.member  
  
           https://www.googleapis.com/auth/admin.directory.group  
  
           https://www.googleapis.com/auth/admin.directory.device.mobile.action  
  
           https://www.googleapis.com/auth/admin.directory.device.mobile  
  
           https://www.googleapis.com/auth/admin.directory.user  

    -   Em **Visibilidade**, selecione **Meu domínio** (não público). 
    -   Clique em **Save Changes (Salvar Alterações)**.  
        ![visibilidade do Google](./media/google-visibility.png "visibilidade do google")  
24. Vá para [admin.google.com](https://admin.google.com/) e, em seguida, escolha **Segurança**. 
   
      ![segurança do google](./media/googlesec.png "segurança do google")  
 
25. Selecione **API reference (Referência da API)**.  
       ![habilitar api do google](./media/googleapi.png "api do google")  
      
26. Selecione **Enable API Access (Habilitar acesso à API)** e clique em **Save changes (Salvar alterações)**.  
  
    ![Referência de API Google](./media/googleapiref.png "google8")  

  
## <a name="configure-cloud-app-security"></a>Configurar o Microsoft Cloud App Security  
  
1.  No portal do Cloud App Security, clique em **Investigar** e em **Aplicativos conectados**.  
  
2.  Na página **Aplicativos conectados**, clique no sinal de mais e selecione **G Suite**.  
       
  
3.  No pop-up, preencha as seguintes informações:  
  
     ![Configuração do G Suite no Cloud App Security](./media/gsuite-config-cas.png "Configuração do G Suite no Cloud App Security")  
  
    1.  **ID da conta de serviço** copiada na etapa 13.  
  
    2.  **Número do projeto (ID do aplicativo)** que você copiou na etapa 21.  
  
    3.  Carregue o **Certificado** P12 que você salvou na etapa 12. Você precisa da senha salva para fazer isso.  
  
    4.  Insira um **email da conta do administrador** do seu administrador do G Suite.  
  
    5.  Se você tiver uma conta do G Suite Business ou Enterprise, marque essa caixa de seleção. Para saber mais sobre quais recursos estão disponíveis no Cloud App Security para o G Suite Business ou Enterprise, confira [Habilitar ações de visibilidade, proteção e governança instantâneas para seus aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).  
  
    6.  Clique em **Salvar configurações**.  
  
    7.  **Siga o link** para se conectar ao G Suite. Isso abre o G Suite, e você será solicitado a autorizar o acesso ao Cloud App Security.  
         
    8.  Certifique-se de que a conexão foi bem-sucedida clicando em **Testar agora**.  
  
         O teste pode levar alguns minutos.  
  
         Depois de receber uma notificação de êxito, clique em **Concluído** e feche a página do G Suite.  
  
  
Depois de conectar o G Suite, você receberá eventos por 60 dias antes da conexão.
  
Após conectar o G Suite, o Cloud App Security realiza uma verificação completa. Dependendo de quantos arquivos e usuários você tiver, a verificação completa poderá levar algum tempo. Para habilitar a verificação quase em tempo real, os arquivos nos quais a atividade é detectada são movidos para o início da fila de verificação. Por exemplo, um arquivo editado, atualizado ou compartilhado é verificado imediatamente. Isso não se aplica a arquivos que não são modificados por natureza. Por exemplo, os arquivos que são exibidos, visualizados, impressos ou exportados são verificados durante a verificação regular.
  
  
## <a name="see-also"></a>Consulte Também  
[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)   

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
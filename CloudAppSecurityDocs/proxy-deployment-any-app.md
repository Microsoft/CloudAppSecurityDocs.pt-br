---
title: Implantar Cloud App Security Controle de Aplicativos de Acesso Condicional para qualquer aplicativo
description: Este artigo fornece informações sobre como implantar o Microsoft Cloud App Security Controle de Aplicativos de Acesso Condicional recursos de proxy reverso para qualquer aplicativo.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 9/23/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.suite: ems
ms.openlocfilehash: 384147ba2a84090fe6f33fc6f6ea0586124666bd
ms.sourcegitcommit: c342abeec95359ddabdabcc3a081a0f91d52407c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "71185131"
---
# <a name="onboard-and-deploy-conditional-access-app-control-for-any-app"></a>Integração e implantação de Controle de Aplicativos de Acesso Condicional para qualquer aplicativo

*Aplica-se ao: Microsoft Cloud App Security*

>[!div class="step-by-step"]
[«Anterior: implantar Controle de Aplicativos de Acesso Condicional para aplicativos em destaque](proxy-deployment-aad.md)<br>
[Próximo: Como criar uma política de sessão »](session-policy-aad.md)

Os controles de sessão no Microsoft Cloud App Security podem ser configurados para trabalhar com qualquer aplicativo Web. Este artigo descreve como integrar e implantar aplicativos de linha de negócios personalizados, aplicativos SaaS sem recursos e aplicativos locais hospedados por meio do proxy de aplicativo Azure Active Directory (Azure AD) com controles de sessão.

Para obter uma lista de aplicativos que são apresentados por Cloud App Security para trabalhar prontos para uso, consulte [proteger aplicativos com Microsoft Cloud App Security controle de aplicativos de acesso condicional](proxy-intro-aad.md#featured-apps).

## <a name="prerequisites"></a>Pré-requisitos

- Sua organização deve ter as seguintes licenças para usar Controle de Aplicativos de Acesso Condicional:

  - Azure Active Directory Premium P1 ou superior
  - Microsoft Cloud App Security

- Os aplicativos devem ser configurados com logon único no Azure AD
- Os aplicativos devem usar os protocolos SAML ou Open ID Connect 2,0

## <a name="to-deploy-any-app"></a>Para implantar qualquer aplicativo

Siga estas etapas para configurar qualquer aplicativo a ser controlado pelo Cloud App Security Controle de Aplicativos de Acesso Condicional.

**Etapa 1: [Configurar a política de acesso condicional do Azure ad para rotear aplicativos relevantes para Cloud app Security](#conf-azure-ad)**

**Etapa 2: [configurar os usuários que implantarão o aplicativo](#conf-users)**

**Etapa 3: [Configurar o aplicativo que você está implantando](#conf-app)**

**Etapa 4: [verificar se o aplicativo está funcionando corretamente](#verify-app)**

**Etapa 5: [habilitar o aplicativo para uso em sua organização](#enable-app)**

**Etapa 6: [atualizar a política do Azure ad](#update-azure-ad)**

> [!NOTE]
> Para implantar Controle de Aplicativos de Acesso Condicional para aplicativos do Azure AD, você precisa de uma [licença válida para Azure Active Directory Premium P1 ou superior](https://docs.microsoft.com/azure/active-directory/license-users-groups) , bem como uma licença de Cloud app Security.

## Etapa 1: configurar a política de acesso condicional do Azure AD para rotear aplicativos relevantes para Cloud App Security<a name="conf-azure-ad"></a>  

1. No Azure AD, o navegador para **segurança**  > **acesso condicional**.

1. Na folha **acesso condicional** , na barra de ferramentas na parte superior, clique em **nova política**.

1. Na folha **novo** , na caixa de texto **nome** , insira o nome da política.

1. Em **atribuições**, clique em **usuários e grupos**, atribua os usuários que estarão integrados (logon inicial e verificação) no aplicativo e clique em **concluído**.

1. Em **atribuições**, clique em **aplicativos de nuvem**, atribua os aplicativos que você deseja controlar com controle de aplicativos de acesso condicional e, em seguida, clique em **concluído**.

1. Em **controles de acesso**, clique em **sessão**, selecione **usar controle de aplicativos de acesso condicional** e escolha as políticas internas (**monitorar somente** ou **bloquear downloads**) ou **use a política personalizada** para definir uma política avançada na nuvem Segurança do aplicativo e, em seguida, clique em **selecionar**.

   ![Acesso condicional do Azure AD](./media/azure-ad-caac-policy.png)

1. Opcional: Adicione condições e conceda controles conforme necessário.

1. Defina **habilitar política** como **ativado** e, em seguida, clique em **criar**.

## Etapa 2: configurar os usuários que implantarão o aplicativo<a name="conf-users"></a>

1. No Cloud App Security, na barra de menus, clique no ícone configurações engrenagem ![configurações](./media/settings-icon.png "ícone de configurações") e selecione **configurações**.

1. Em **controle de aplicativos de acesso condicional**, selecione **integração do aplicativo/manutenção**.

1. Insira o nome principal do usuário ou o email para os usuários que estarão integrando o aplicativo e clique em **salvar**.

    ![Captura de tela de configurações para integração de aplicativos e manutenção.](media/app-onboarding-settings.png)

## Etapa 3: configurar o aplicativo que você está implantando<a name="conf-app"></a>

Vá para o aplicativo que você está implantando. A página que você vê depende se o aplicativo é reconhecido. Execute um destes procedimentos:

| Status do aplicativo | Description | Etapas |
| --- | --- | --- |
| Não reconhecido | Você verá uma página aplicativo não reconhecido solicitando que você configure seu aplicativo. | 1. [adicione o aplicativo ao controle de aplicativos de acesso condicional](#add-app).<br> 2. [adicione os domínios para o aplicativo](#add-domains)e, em seguida, retorne ao aplicativo e atualize a página.<br> 3. [Instale os certificados para o aplicativo](#install-certs). |
| Identificado | Você verá uma página de integração solicitando que você continue o processo de configuração do aplicativo. | - [instalar os certificados para o aplicativo](#install-certs). <br><br> **Observação:** Verifique se o aplicativo está configurado com todos os domínios necessários para que o aplicativo funcione corretamente. Para configurar domínios adicionais, vá para [adicionar os domínios do aplicativo](#add-domains)e, em seguida, retorne à página do aplicativo. |

### Para adicionar um novo aplicativo<a name="add-app"></a>

1. Na barra de menus, clique no ícone configurações engrenagem ![configurações](./media/settings-icon.png "ícone de configurações")e selecione **controle de aplicativos de acesso condicional**.

1. Clique em **Exibir novos aplicativos**.

    ![Controle de Aplicativos de Acesso Condicional, exibir novos aplicativos](media/caac-view-apps.png)

1. Na tela que é aberta, você pode ver uma lista de novos aplicativos. Para cada aplicativo que você estiver integrando, clique no sinal de **+** e, em seguida, clique em **Adicionar**.

   > [!NOTE]
   > Se um aplicativo não for exibido no catálogo de aplicativos do Cloud App Security, ele será exibido na caixa de diálogo nos aplicativos não identificados juntamente com a URL de logon. Ao clicar no sinal + desses aplicativos, você pode integrar o aplicativo como um aplicativo personalizado.

    ![Controle de Aplicativos de Acesso Condicional, aplicativos do Azure AD descobertos](media/caac-discovered-aad-apps.png)

### Para adicionar domínios a um aplicativo<a name="add-domains"></a>

A Associação dos domínios corretos a um aplicativo permite que Cloud App Security imponha políticas e atividades de auditoria.

Por exemplo, se você tiver configurado uma política que bloqueia o download de arquivos para um domínio associado, os downloads de arquivo do aplicativo desse domínio serão bloqueados. No entanto, os downloads de arquivo pelo aplicativo de domínios não associados ao aplicativo não serão bloqueados e a ação não será auditada no log de atividades.
> [!NOTE]
> Cloud App Security ainda adiciona um sufixo aos domínios não associados ao aplicativo para garantir uma experiência de usuário tranqüila.

1. De dentro do aplicativo, na barra de ferramentas Cloud App Security admin, clique em **domínios descobertos**.
    > [!NOTE]
    > A barra de ferramentas de administração só é visível para os usuários com permissões para aplicativos integrados ou de manutenção.
1. No painel domínios descobertos, anote os nomes de domínio ou exporte a lista como um arquivo. csv.
    > [!NOTE]
    > O painel exibe uma lista de domínios descobertos que não estão associados no aplicativo. Os nomes de domínio são totalmente qualificados.
1. Vá para Cloud App Security, na barra de menus, clique no ícone configurações engrenagem ![configurações](./media/settings-icon.png "ícone de configurações") e selecione **controle de aplicativos de acesso condicional**.
1. Na lista de aplicativos, na linha na qual o aplicativo que você está implantando aparece, escolha os três pontos no final da linha e, em **detalhes do aplicativo**, escolha **Editar**.
    > [!TIP]
    > Para exibir a lista de domínios configurados no aplicativo, clique em **Exibir domínios de aplicativo**.
1. Em **domínios definidos pelo usuário**, insira todos os domínios que você deseja associar a esse aplicativo e, em seguida, clique em **salvar**.
    > [!NOTE]
    > Você pode usar o caractere curinga * como um espaço reservado para qualquer caractere. Ao adicionar domínios, decida se deseja adicionar domínios específicos (`sub1.contoso.com`, `sub2.contoso.com`) ou vários domínios (`*.contoso.com`).

### Para instalar certificados raiz<a name="install-certs"></a>

1. Repita as etapas a seguir para instalar a **autoridade de certificação atual** e os próximos certificados raiz autoassinados **da CA** .
    1. Selecione o certificado.
    1. Clique em **abrir**e, quando solicitado, clique em **abrir** novamente.
    1. Clique em **Instalar certificado**.
    1. Escolha o **usuário atual** ou o **computador local**.
    1. Selecione **Coloque todos os certificados no repositório a seguir** e clique em **procurar**.
    1. Selecione **autoridades de certificação raiz confiáveis** e clique em **OK**.
    1. Clique em **concluir**.

    > [!NOTE]
    > Para que os certificados sejam reconhecidos, depois de instalar o certificado, você deve reiniciar o navegador e ir para a mesma página.<!-- You'll see a check-mark by the certificates links confirmation they are installed.-->

1. Clique em **Continuar**.

## Etapa 4: verificar se o aplicativo está funcionando corretamente<a name="verify-app"></a>

1. Verifique se o fluxo de entrada funciona corretamente.
    <!--
    > [!NOTE]
    > Some apps issue a nonce hash during authentication that may break the sign-in process. If this happens, see the Troubleshooting Guide to resolve the issue.-->
1. Quando você estiver no aplicativo, execute as seguintes verificações:
    1. Visite todas as páginas dentro do aplicativo que fazem parte do processo de trabalho de um usuário e verifique se as páginas são renderizadas corretamente.
    1. Verifique se o comportamento e a funcionalidade do aplicativo não são afetados negativamente executando ações comuns, como baixar e carregar arquivos.
    1. Examine a lista de domínios associados ao aplicativo. Para obter mais informações, consulte [adicionar os domínios para o aplicativo](#add-domains).

## Etapa 5: habilitar o aplicativo para uso em sua organização<a name="enable-app"></a>

Quando estiver pronto para habilitar o aplicativo para uso no ambiente de produção de sua organização, execute as etapas a seguir.

1. Em Cloud App Security, clique no ícone configurações engrenagem ![configurações](./media/settings-icon.png "ícone de configurações")e, em seguida, selecione **controle de aplicativos de acesso condicional**.
1. Na lista de aplicativos, na linha na qual o aplicativo que você está implantando aparece, escolha os três pontos no final da linha e escolha **Editar aplicativo**.
1. Selecione **usar com controle de aplicativos de acesso condicional** e, em seguida, clique em **salvar**.

## Etapa 6: atualizar a política do Azure AD<a name="update-azure-ad"></a>

1. No Azure AD, em **segurança**, clique em **acesso condicional**.
1. Atualize a política criada anteriormente para incluir os usuários, grupos e controles relevantes necessários.
1. Em **sessão**  > **usar controle de aplicativos de acesso condicional**, se você tiver selecionado **usar política personalizada**, vá para Cloud app Security e crie uma política de sessão correspondente. Para saber mais, confira [Políticas de sessão](session-policy-aad.md).

>[!div class="step-by-step"]
[«Anterior: implantar Controle de Aplicativos de Acesso Condicional para aplicativos em destaque](proxy-deployment-aad.md)<br>
[Próximo: Como criar uma política de sessão »](session-policy-aad.md)

## <a name="next-steps"></a>Próximas etapas

[Trabalhar com o Controle de Aplicativo de Acesso Condicional do Microsoft Cloud App Security](proxy-intro-aad.md)

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/)
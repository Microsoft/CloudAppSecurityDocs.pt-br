---
title: Implantar Cloud App Security Controle de Aplicativos de Acesso Condicional para qualquer aplicativo
description: Este artigo fornece informações sobre como implantar o Microsoft Cloud App Security Controle de Aplicativos de Acesso Condicional recursos de proxy reverso para qualquer aplicativo.
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
ms.suite: ems
ms.openlocfilehash: 1bb39de6eafda31df7df07d177050cbb0f02031a
ms.sourcegitcommit: cad2ead82bb76e4749c75eb7a0594e97f40545db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/22/2019
ms.locfileid: "68372348"
---
# <a name="onboard-and-deploy-conditional-access-app-control-for-any-app"></a>Integração e implantação de Controle de Aplicativos de Acesso Condicional para qualquer aplicativo

*Aplica-se a: Microsoft Cloud App Security*

>[!div class="step-by-step"]
[« Anterior: Implantar Controle de Aplicativos de Acesso Condicional para aplicativos em destaque](proxy-deployment-aad.md)<br>
[Próximo: Como criar uma política de sessão »](session-policy-aad.md)

Os controles de sessão no Microsoft Cloud App Security podem ser configurados para trabalhar com qualquer aplicativo Web. Este artigo descreve como integrar e implantar aplicativos de linha de negócios personalizados, aplicativos SaaS sem recursos e aplicativos locais hospedados por meio do proxy de aplicativo Azure Active Directory (Azure AD) com controles de sessão.

Para obter uma lista de aplicativos que são apresentados por Cloud App Security para trabalhar prontos para uso, consulte [proteger aplicativos com Microsoft Cloud App Security controle de aplicativos de acesso condicional](proxy-intro-aad.md).

## <a name="prerequisites"></a>Pré-requisitos

- Sua organização deve ter as seguintes licenças para usar Controle de Aplicativos de Acesso Condicional:

  - Azure Active Directory Premium P1 ou superior
  - Microsoft Cloud App Security

- Os aplicativos devem ser configurados com logon único no Azure AD
- Os aplicativos devem usar os protocolos SAML ou Open ID Connect 2,0

## <a name="to-deploy-any-app"></a>Para implantar qualquer aplicativo

Siga estas etapas para configurar qualquer aplicativo a ser controlado pelo Cloud App Security Controle de Aplicativos de Acesso Condicional.

**Etapa 1: [Configurar a política de acesso condicional do Azure AD para rotear aplicativos relevantes para Cloud App Security](#conf-azure-ad)**

**Etapa 2: [Configurar os usuários que implantarão o aplicativo](#conf-users)**

**Etapa 3: [Configurar o aplicativo que você está implantando](#conf-app)**

**Etapa 4: [Adicionar os domínios para o aplicativo](#add-domains)**

**Etapa 5: [Verifique se o aplicativo está funcionando corretamente](#verify-app)**

**Etapa 6: [Habilitar o aplicativo para uso em sua organização](#enable-app)**

**Etapa 7: [Atualizar a política do Azure AD](#update-azure-ad)**

> [!NOTE]
> Para implantar Controle de Aplicativos de Acesso Condicional para aplicativos do Azure AD, você precisa de uma [licença válida para Azure Active Directory Premium P1 ou superior](https://docs.microsoft.com/azure/active-directory/license-users-groups) , bem como uma licença de Cloud app Security.

## Etapa 1: Configurar a política de acesso condicional do Azure AD para rotear aplicativos relevantes para Cloud App Security<a name="conf-azure-ad"></a>  

1. No Azure AD, o navegador para**acesso condicional**de **segurança** > .

1. Na folha **acesso condicional** , na barra de ferramentas na parte superior, clique em **nova política**.

1. Na folha **novo** , na caixa de texto **nome** , insira o nome da política.

1. Em **atribuições**, clique em **usuários e grupos**, atribua os usuários que estarão integrados (logon inicial e verificação) no aplicativo e clique em **concluído**.

1. Em **atribuições**, clique em **aplicativos de nuvem**, atribua os aplicativos que você deseja controlar com controle de aplicativos de acesso condicional e, em seguida, clique em **concluído**.

1. Em **controles de acesso**, clique em **sessão**, selecione **usar controle de aplicativos de acesso condicional** e escolha as políticas internas (**monitorar somente** ou **bloquear downloads**) ou **use a política personalizada** para definir uma política avançada na nuvem Segurança do aplicativo e, em seguida, clique em **selecionar**.

   ![Acesso condicional do Azure AD](./media/azure-ad-caac-policy.png)

1. Opcional: Adicione condições e conceda controles conforme necessário.

1. Defina **habilitar política** como **ativado** e, em seguida, clique em **criar**.

## Etapa 2: Configurar os usuários que implantarão o aplicativo<a name="conf-users"></a>

1. No Cloud App Security, na barra de menus, clique no ícone configurações configurações ![de engrenagem ícone](./media/settings-icon.png "configurações") e selecione **configurações**.

1. Em **controle de aplicativos de acesso condicional**, selecione **integração do aplicativo/manutenção**.

1. Insira o nome principal do usuário ou o email para os usuários que estarão integrando o aplicativo e clique em **salvar**.

    ![Captura de tela de configurações para integração de aplicativos e manutenção.](media/app-onboarding-settings.png)

## Etapa 3: Configurar o aplicativo que você está implantando<a name="conf-app"></a>

1. Vá para o aplicativo que você está implantando. Se o seu domínio de aplicativo for reconhecido, você será solicitado a continuar o processo de configuração do aplicativo. Se o seu domínio de aplicativo não for reconhecido, você será solicitado a configurar os domínios do aplicativo. Clique em **Configurar aplicativo** e vá para [adicionar os domínios para o aplicativo](#add-domains).

    > [!NOTE]
    > Para domínios de aplicativo reconhecidos, verifique se o aplicativo está configurado com todos os domínios necessários para que o aplicativo funcione corretamente. Para configurar domínios adicionais, vá para [adicionar os domínios para o aplicativo](#add-domains).

1. Repita as etapas a seguir para instalar a **autoridade de certificação atual** e os próximos certificados raiz autoassinados **da CA** .
    1. Selecione o certificado.
    1. Clique em **abrir**e, quando solicitado, clique em **abrir** novamente.
    1. Clique em **Instalar certificado**.
    1. Escolha o **usuário atual** ou o **computador local**.
    1. Selecione **Coloque todos os certificados no repositório a seguir** e clique em **procurar**.
    1. Selecione **autoridades de certificação raiz confiáveis** e clique em **OK**.
    1. Clique em **Finalizar**.

    > [!NOTE]
    > Para que os certificados sejam reconhecidos, depois de instalar o certificado, você deve reiniciar o navegador e ir para a mesma página. Você verá uma marca de seleção pelos links de certificado confirmando que um certificado válido está instalado.

1. Clique em **Continue**.

## Etapa 4: Adicionar os domínios para o aplicativo<a name="add-domains"></a>

A Associação dos domínios corretos a um aplicativo permite que Cloud App Security imponha políticas e atividades de auditoria.

Por exemplo, se você tiver configurado uma política que bloqueia o download de arquivos para um domínio associado, os downloads de arquivo do aplicativo desse domínio serão bloqueados. No entanto, os downloads de arquivo pelo aplicativo de domínios não associados ao aplicativo não serão bloqueados e a ação não será auditada no log de atividades.
> [!NOTE]
> Cloud App Security ainda adiciona um sufixo aos domínios não associados ao aplicativo para garantir uma experiência de usuário tranqüila.

1. De dentro do aplicativo, na barra de ferramentas Cloud App Security admin, clique em **domínios**descobertos.
    > [!NOTE]
    > A barra de ferramentas de administração só é visível para os usuários com permissões para aplicativos integrados ou de manutenção.
1. No painel domínios descobertos, anote os nomes de domínio ou exporte a lista como um arquivo. csv.
    > [!NOTE]
    > O painel exibe uma lista de domínios descobertos que não estão associados no aplicativo. Os nomes de domínio são totalmente qualificados.
1. Vá para Cloud App Security, na barra de menus, clique no ícone configurações configurações ![de engrenagem ícone](./media/settings-icon.png "configurações") e selecione **controle de aplicativos de acesso condicional**.
1. Na lista de aplicativos, na linha na qual o aplicativo que você está implantando aparece, escolha os três pontos no final da linha e, em **detalhes do aplicativo**, escolha **Editar**.
    > [!TIP]
    > Para exibir a lista de domínios configurados no aplicativo, clique em **Exibir domínios de aplicativo**.
1. Em **domínios definidos pelo usuário**, insira todos os domínios que você deseja associar a esse aplicativo e, em seguida, clique em **salvar**.
    > [!NOTE]
    > Você pode usar o caractere curinga * como um espaço reservado para qualquer caractere. Ao adicionar domínios, decida se deseja adicionar domínios específicos (`sub1.contoso.com`,`sub2.contoso.com`) ou vários domínios (`*.contoso.com`).

## Etapa 5: Verifique se o aplicativo está funcionando corretamente<a name="verify-app"></a>

1. Verifique se o fluxo de entrada funciona corretamente.
    <!--
    > [!NOTE]
    > Some apps issue a nonce hash during authentication that may break the sign-in process. If this happens, see the Troubleshooting Guide to resolve the issue.-->
1. Quando você estiver no aplicativo, execute as seguintes verificações:
    1. Visite todas as páginas dentro do aplicativo que fazem parte do processo de trabalho de um usuário e verifique se as páginas são renderizadas corretamente.
    1. Verifique se o comportamento e a funcionalidade do aplicativo não são afetados negativamente executando ações comuns, como baixar e carregar arquivos.
    1. Examine a lista de domínios associados ao aplicativo. Para obter mais informações, consulte [adicionar os domínios para o aplicativo](#add-domains).

## Etapa 6: Habilitar o aplicativo para uso em sua organização<a name="enable-app"></a>

Quando estiver pronto para habilitar o aplicativo para uso no ambiente de produção de sua organização, execute as etapas a seguir.

1. No Cloud App Security, na barra de menus, clique no ícone configurações configurações ![de engrenagem ícone](./media/settings-icon.png "configurações") e selecione **controle de aplicativos de acesso condicional**.
1. Na lista de aplicativos, na linha na qual o aplicativo que você está implantando aparece, escolha os três pontos no final da linha e escolha **Editar aplicativo**.
1. Selecione **usar com controle de aplicativos de acesso condicional** e, em seguida, clique em **salvar**.

## Etapa 7: Atualizar a política do Azure AD<a name="update-azure-ad"></a>

1. No Azure AD, em **segurança**, clique em **acesso condicional**.
1. Atualize a política criada anteriormente para incluir os usuários, grupos e controles relevantes necessários.
1. Em**uso**da **sessão** > controle de aplicativos de acesso condicional, se você selecionou **usar política personalizada**, vá para Cloud app Security e crie uma política de sessão correspondente. Para saber mais, confira [Políticas de sessão](session-policy-aad.md).

>[!div class="step-by-step"]
[« Anterior: Implantar Controle de Aplicativos de Acesso Condicional para aplicativos em destaque](proxy-deployment-aad.md)<br>
[Próximo: Como criar uma política de sessão »](session-policy-aad.md)

## <a name="next-steps"></a>Próximas etapas 
[Trabalhar com o Controle de Aplicativo de Acesso Condicional do Microsoft Cloud App Security](proxy-intro-aad.md)

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/)
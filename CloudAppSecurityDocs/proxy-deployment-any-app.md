---
title: Implantar o controle de aplicativo de acesso condicional do Cloud App Security para todos os aplicativos
description: Este artigo fornece informações sobre como implantar os recursos de proxy reverso do Microsoft Cloud App Security condicional aplicativo controle de acesso para todos os aplicativos.
keywords: ''
author: ShlomoSagir-MS
ms.author: shsagir
manager: ShlomoSagir-MS
ms.date: 7/2/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.suite: ems
ms.openlocfilehash: 4fc756d2c077d97bef295b40cefd2336ecb25c16
ms.sourcegitcommit: 8fd13c10c2f66a553a8a8fc413555ca837fc9c56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/07/2019
ms.locfileid: "67610707"
---
# <a name="onboard-and-deploy-conditional-access-app-control-for-any-app"></a>Carregar e implantar o controle de aplicativo de acesso condicional para qualquer aplicativo

*Aplica-se a: Microsoft Cloud App Security*

>[!div class="step-by-step"]
[« Anterior: Introdução ao Controle de Aplicativos de Acesso Condicional](proxy-intro-aad.md)<br>
[Próximo: Como criar uma política de sessão »](session-policy-aad.md)

Controles de sessão no Microsoft Cloud App Security podem ser configurados para funcionar com todos os aplicativos web. Este artigo descreve como integrar e implantar aplicativos de linha de negócios personalizados, não em destaque aplicativos de SaaS e aplicativos locais hospedados por meio do Proxy de aplicativo do AD do Azure com controles de sessão.

Para obter uma lista de aplicativos em destaque do Cloud App Security para trabalhar fora da caixa, consulte [proteger aplicativos com o Microsoft Cloud App Security condicional aplicativo controle de acesso](proxy-intro-aad.md).

## <a name="prerequisites"></a>Pré-requisitos

- Sua organização deve ter licenças a seguir para usar o controle de aplicativo de acesso condicional:

  - Azure Active Directory Premium edition
  - Segurança de aplicativos de nuvem

- Aplicativos devem ser configurados com logon único do AD do Azure
- Aplicativos devem usar protocolos SAML ou Open ID 2.0 se conectar

## <a name="to-deploy-a-any-app"></a>Para implantar um aplicativo de qualquer

Siga estas etapas para configurar qualquer aplicativo para ser controlados pelo controle de aplicativo do Cloud App Security condicional acesso.

**Etapa 1: [Configurar o recurso de política de acesso condicional do Azure Active Directory para rotear os aplicativos relevantes ao Cloud App Security](#conf-azure-ad).**

**Etapa 2: [Configurar os usuários que implantarão o aplicativo](#conf-users).**

**Etapa 3: [Configurar o aplicativo que você está implantando](#conf-app)**

**Etapa 4: [Adicionar os domínios do aplicativo](#add-domains)**

**Etapa 5: [Verificar se o aplicativo está funcionando corretamente](#verify-app)**

**Etapa 6: [Habilitar o aplicativo para uso em sua organização](#enable-app)**

**Etapa 7: [Atualizar a política do Azure AD](#update-azure-ad)**

> [!NOTE]
> Para implantar o Controle de Aplicativos de Acesso Condicional nos aplicativos do Azure AD, você precisa de uma [licença do Azure AD Premium P1](https://docs.microsoft.com/azure/active-directory/license-users-groups) válida, bem como uma licença do Cloud App Security.

## Etapa 1: Configurar o recurso de política de acesso condicional do Azure Active Directory para rotear os aplicativos relevantes ao Cloud App Security<a name="conf-azure-ad"></a>  

1. No Azure Active Directory, sob **segurança**, clique em **acesso condicional**.

1. Sobre o **acesso condicional** página, na barra de ferramentas na parte superior, clique em **nova política**.

1. No **New** página, o **nome** caixa de texto, digite **teste**.

1. Sobre o **usuários e grupos** página, atribua os usuários de teste relevantes que serão a integração de aplicativos.

1. Sobre o **aplicativos de nuvem** página, atribua os aplicativos que você deseja controlar com o controle de aplicativo de acesso condicional.

1. Sob **sessão**, selecione **uso controle de aplicativo de acesso condicional** e, em seguida, selecione **monitorar somente**.

   ![Acesso condicional do Azure AD](./media/azure-ad-caac-policy.png)

1. Clique em **habilitar** e **salvar**.

## Etapa 2: Configurar os usuários que implantarão o aplicativo<a name="conf-users"></a>

1. No Cloud App Security, na barra de menus, clique na engrenagem de configurações ![ícone de configurações](./media/settings-icon.png "ícone configurações") e selecione **configurações**.

1. Sob **controle de aplicativo de acesso condicional**, selecione **integração de aplicativo/manutenção**.

1. Insira o nome principal do usuário ou o aplicativo de email para os usuários que serão a integração e, em seguida, clique em **salvar**.

    ![Captura de tela das configurações de integração de aplicativo e manutenção.](media/app-onboarding-settings.png)

## Etapa 3: Configurar o aplicativo que você está implantando<a name="conf-app"></a>

1. Vá para o aplicativo que você está implantando. Se seu domínio do aplicativo for reconhecido, você será solicitado para continuar o processo de configuração do aplicativo. Se seu domínio de aplicativo não for reconhecido, você precisará configurar domínios do aplicativo. Clique em **configurar aplicativo** e vá até [adicionar os domínios para o aplicativo](#add-domains).

    > [!NOTE]
    > Para os domínios de aplicativo reconhecido, verifique se que o aplicativo é configurado com todos os domínios necessários para o aplicativo funcione corretamente. Para configurar adicionais, vá para [adicionar os domínios para o aplicativo](#add-domains).

1. Repita as etapas a seguir para instalar o **autoridade de certificação atual** e **AC próxima** certificados raiz autoassinados.
    1. Selecione o certificado.
    1. Clique em **aberto**e, quando solicitado clique **abrir** novamente.
    1. Clique em **instalar o certificado**.
    1. Escolha **usuário atual** ou **Máquina Local**.
    1. Selecione **colocar todos os certificados no repositório a seguir** e, em seguida, clique em **procurar**.
    1. Selecione **autoridades de certificação raiz confiáveis** e, em seguida, clique em **Okey**.
    1. Clique em **Finalizar**.

    > [!NOTE]
    > Para que os certificados sejam reconhecidos, depois de instalar o certificado, você deve reiniciar o navegador e vá para a mesma página. Você verá uma marca de seleção, a confirmação de links de certificados que são instalados.

1. Clique em **Continue**.

## Etapa 4: Adicionar os domínios do aplicativo<a name="add-domains"></a>

Associar os domínios corretos para um aplicativo permite que o Cloud App Security para impor políticas e as atividades de auditoria.

Por exemplo, se você tiver configurado uma política que bloqueia o download de arquivos para um domínio associado, downloads de arquivos pelo aplicativo desse domínio serão bloqueados. No entanto, os downloads de arquivos pelo aplicativo de domínios não está associada com o aplicativo não serão bloqueados e a ação não será auditada no log de atividades.
> [!NOTE]
> Ainda, o Cloud App Security adiciona um sufixo para domínios que não está associados com o aplicativo para garantir uma experiência perfeita ao usuário.

1. De dentro do aplicativo, na barra de ferramentas de administração do Cloud App Security, clique em **descobertos domínios**.
    > [!NOTE]
    > A barra de ferramentas de administração só é visível para os usuários com permissões para carregar ou aplicativos de manutenção.
1. No painel de domínios descobertos, tome nota dos nomes de domínio ou exportar a lista como um arquivo. csv.
    > [!NOTE]
    > O painel exibe uma lista de domínios descobertos que não são associados no aplicativo. Os nomes de domínio são totalmente qualificados.
1. Vá para o Cloud App Security, na barra de menus, clique na engrenagem de configurações ![ícone de configurações](./media/settings-icon.png "ícone configurações") e selecione **Acccess App controle condicional**.
1. Na lista de aplicativos, na linha em que o aplicativo que você está implantando for exibida, selecione os três pontos no final da linha e, em **detalhes do aplicativo**, escolha **editar**.
    > [!TIP]
    > Para exibir a lista de domínios configurados no aplicativo, clique em **exibir os domínios de aplicativo**.
1. Na **domínios definidos pelo usuário**, insira todos os domínios que você deseja associar a esse aplicativo e, em seguida, clique em **salvar**.
    > [!NOTE]
    > Você pode usar o * caractere curinga como um espaço reservado para qualquer caractere. Ao adicionar domínios, decida se deseja adicionar domínios específicos (`sub1.contoso.com`,`sub2.contoso.com`) ou vários domínios (`*.contoso.com`).

## Etapa 5: Verificar se o aplicativo está funcionando corretamente<a name="verify-app"></a>

1. Verifique se que o fluxo de entrada funciona corretamente.
    > [!NOTE]
    > Alguns aplicativos emitem um nonce hash durante a autenticação que pode interromper o processo de logon. Se isso acontecer, consulte o guia de solução de problemas para resolver o problema.
1. Quando você estiver no aplicativo, execute as seguintes verificações:
    1. Visite todas as páginas dentro do aplicativo que fazem parte do processo de trabalho dos usuários e verificar que as páginas sejam renderizadas corretamente.
    1. Verifique se que o comportamento e a funcionalidade do aplicativo não serão prejudicados por executar ações comuns, como baixar e carregar arquivos.
    1. Examine a lista de domínios associada ao aplicativo. Para obter mais informações, consulte [adicionar os domínios para o app4](#add-domains).

## Etapa 6: Habilitar o aplicativo para uso em sua organização<a name="enable-app"></a>

Depois que você está pronto para ativar o aplicativo para uso em ambiente de produção da sua organização, execute as seguintes etapas.

1. No Cloud App Security, na barra de menus, clique na engrenagem de configurações ![ícone de configurações](./media/settings-icon.png "ícone configurações") e selecione **controle de aplicativo de acesso condicional**.
1. Na lista de aplicativos, na linha em que o aplicativo que você está implantando for exibida, selecione os três pontos no final da linha e, em seguida, escolha **Editar aplicativo**.
1. Selecione **uso com o controle de aplicativo de acesso condicional** e, em seguida, clique em **salvar**.

## Etapa 7: Atualizar a política do Azure AD<a name="update-azure-ad"></a>

1. No Azure Active Directory, sob **segurança**, clique em **acesso condicional**.
1. Atualizar a política que você criou na [configurar o recurso de política de acesso condicional do Azure Active Directory](#conf-azure-ad) para incluir os usuários relevantes, grupos e controles que você precisa.
1. Sob **sessão** > **usar controle de aplicativo de acesso condicional**, se você selecionou **usar a política personalizada**, vá para o Cloud App Security e crie um correspondente política de sessão. Para saber mais, confira [Políticas de sessão](session-policy-aad.md).

>[!div class="step-by-step"]
[« Anterior: Implantar o controle de aplicativo de acesso condicional para aplicativos em destaque](proxy-deployment-aad.md)<br>
[Próximo: Como criar uma política de sessão »](session-policy-aad.md)

## <a name="next-steps"></a>Próximas etapas 
[Trabalhar com o Controle de Aplicativo de Acesso Condicional do Microsoft Cloud App Security](proxy-intro-aad.md)

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/)
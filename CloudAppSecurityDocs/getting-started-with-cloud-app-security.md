---
title: Implantar o Cloud App Security
description: Esse início rápido descreve o processo para pôr o Cloud App Security em funcionamento e ter o uso, o insight e o controle do aplicativo na nuvem.
ms.date: 06/07/2020
ms.topic: quickstart
ms.openlocfilehash: 95f4d916fc60db4d8ddbe2a9a87dc1af580e4be9
ms.sourcegitcommit: 7fc4d916a43d188b1aa4e3cee2e8bd1de230d135
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98206484"
---
# <a name="quickstart-get-started-with-microsoft-cloud-app-security"></a>Início Rápido: introdução ao Microsoft Cloud App Security

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Esse início rápido fornece etapas para pôr o Cloud App Security em funcionamento. O Microsoft Cloud App Security pode ajudar você a aproveitar os benefícios dos aplicativos na nuvem, mantendo o controle dos recursos corporativos. Ele atua na melhoria da visibilidade da atividade na nuvem e ajudando a aumentar a proteção dos dados corporativos. Nesse artigo, mostraremos cada etapa para configurar e trabalhar com o Microsoft Cloud App Security.

Sua organização deve ter uma licença de uso do Cloud App Security. Para obter detalhes do preço, consulte a [folha de dados de licenciamento do Cloud App Security](https://aka.ms/mcaslicensing).

>[!NOTE]
>O Cloud App Security não requer nenhuma licença do Office 365.

## <a name="prerequisites"></a>Pré-requisitos

- Sua organização deve ter uma licença de uso do Cloud App Security. Para obter detalhes do preço, consulte a [folha de dados de licenciamento do Cloud App Security](https://aka.ms/mcaslicensing).

    Para obter suporte na ativação do locatário, confira [Maneiras de contatar o suporte para produtos comerciais – Ajuda para Administradores](https://support.office.com/article/Contact-Office-365-for-business-support-Admin-Help-32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b).
- Assim que tiver uma licença do Cloud App Security, você receberá um email com informações de ativação e um link para o portal do Cloud App Security.

- Para configurar o Cloud App Security, você deve ser um Administrador Global ou um Administrador de Segurança no Azure Active Directory ou Office 365. É importante entender que um usuário ao qual seja atribuída uma função de administrador terá as mesmas permissões em todos os aplicativos na nuvem que sua organização tenha assinado. Isso ocorre independentemente de você atribuir a função no centro de administração do Microsoft 365, no portal clássico do Azure ou usando o módulo do Azure AD para [Windows PowerShell](/microsoft-365/enterprise/assign-roles-to-user-accounts-with-microsoft-365-powershell?view=o365-worldwide&preserve-view=true). Para obter mais informações, consulte [Atribuir funções de administrador](https://support.office.com/article/Assigning-admin-roles-in-Office-365-eac4d046-1afd-4f1a-85fc-8219c79e1504) e [Como atribuir funções de administrador no Azure Active Directory](/azure/active-directory/users-groups-roles/directory-assign-admin-roles).

- Para executar o portal do Cloud App Security, use o Internet Explorer 11, o Microsoft Edge (mais recente), o Google Chrome (mais recente), o Mozilla Firefox (mais recente) ou o Apple Safari (mais recente).

## <a name="to-access-the-portal"></a>Para acessar o portal

Para acessar o portal do Cloud App Security, acesse [https://portal.cloudappsecurity.com](https://portal.cloudappsecurity.com). Você também pode acessar o portal por meio do **[Centro de administração do Microsoft 365](https://security.microsoft.com)** , da seguinte maneira:

1. No centro de administração do Microsoft 365, no menu lateral, clique em **Mostrar tudo** e selecione **Segurança**.

    ![Acesso do centro de administração do Microsoft 365](media/access-from-o365.png)

1. Na página de segurança do Microsoft 365, clique em **Mais recursos** e selecione **Cloud App Security**.

    ![Selecionar o Cloud App Security](media/access-from-o365-s2.png)

## <a name="step-1-set-instant-visibility-protection-and-governance-actions-for-your-apps"></a>Etapa 1. [Definir ações de visibilidade, proteção e governança instantâneas para os aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)

Tarefa obrigatória: Conectar aplicativos

1. Na engrenagem de configurações, selecione **Conectores de aplicativos**.
1. Clique no sinal de mais ( **+** ) para adicionar um aplicativo e selecione um aplicativo.
1. Siga as etapas de configuração para conectar o aplicativo.

**Por que conectar um aplicativo?**
Depois de conectar um aplicativo, você pode ter uma visibilidade mais profunda para poder investigar atividades, arquivos e contas dos aplicativos em seu ambiente na nuvem.

## <a name="step-2-control-cloud-apps-with-policies"></a>Etapa 2. [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

Tarefa obrigatória: Criar políticas

### <a name="to-create-policies"></a>Para criar políticas

1. Acesse **Controle** > **Modelos**.
1. Selecione um modelo de política na lista e, depois, escolha (+) **Criar política**.
1. Personalize a política (selecione filtros, ações e outras configurações) e, depois, escolha **Criar**.
1. Na guia **Políticas**, escolha a política para ver as correspondências relevantes (atividades, arquivos, alertas).
 Dica: para abranger todos os seus cenários de segurança de ambiente na nuvem, crie uma política para cada **categoria de risco**.

### <a name="how-can-policies-help-your-organization"></a>Como as políticas podem ajudar sua organização?

Você pode usar políticas para ajudar você a monitorar tendências, ver ameaças de segurança e gerar relatórios e alertas personalizados. Com as políticas, você pode criar ações de governança e definir a prevenção contra perda de dados e os controles de compartilhamento de arquivos.

## <a name="step-3-set-up-cloud-discovery"></a>Etapa 3. [Configurar o Cloud Discovery](set-up-cloud-discovery.md)

Tarefa obrigatória: Habilitar o Cloud App Security para exibir o uso do aplicativo na nuvem

1. [Integrar-se ao Microsoft Defender para Ponto de Extremidade](mde-integration.md) para habilitar automaticamente o Cloud App Security para monitorar seus dispositivos Windows 10 dentro e fora da sua empresa.
1. Caso você use o [Zscaler, integre-o](zscaler-integration.md) com o Cloud App Security.
1. Para obter cobertura completa, crie um relatório contínuo do Cloud Discovery

    1. Na engrenagem de configurações, selecione **Configurações do Cloud Discovery**.
    1. Escolha **Carregamento de log automático**.
    1. Na guia **Fontes de dados**, adicione suas fontes.
    1. Na guia **Coletores de log**, configure o coletor de logs.

### <a name="to-create-a-snapshot-cloud-discovery-report"></a>Criar um relatório de instantâneos do Cloud Discovery

 Vá para **Descobrir** > **Relatório de instantâneos** e siga as etapas mostradas.

### <a name="why-should-you-configure-cloud-discovery-reports"></a>Por que você deve configurar os relatórios do Cloud Discovery?

Ter visibilidade da TI sombra em sua organização é fundamental.
Depois que os logs forem analisados, você consegue descobrir facilmente quais aplicativos na nuvem estão sendo usados, por quais pessoas e em quais dispositivos.

## <a name="step-4-personalize-your-experience"></a>Etapa 4. [Personalizar sua experiência](mail-settings.md)

Tarefa recomendada: adicionar os detalhes da organização

### <a name="to-enter-email-settings"></a>Inserir as configurações de email

1. Na engrenagem de configurações, selecione **Configurações de email**.
1. Em **Identidade do remetente de email**, insira seus endereços de email e o nome de exibição.
1. Em **Design de email**, carregue o modelo de email da sua organização.

### <a name="to-set-admin-notifications"></a>Definir as notificações de administrador

1. Na barra de navegação, escolha seu nome de usuário e vá para **Configurações de usuário**.
1. Em **Notificações**, configure os métodos que você deseja definir para as notificações do sistema.
1. Selecione **Salvar**.

### <a name="to-customize-the-score-metrics"></a>Personalizar as métricas de pontuação

1. Na engrenagem de configurações, selecione **Configurações do Cloud Discovery**.
1. Na engrenagem de configurações, selecione **Configurações do Cloud Discovery**.
1. Em **Métricas de pontuação**, configure a importância de vários valores de risco.
1. Selecione **Salvar**.

Agora, as pontuações de risco dadas a aplicativos descobertos são configuradas precisamente de acordo com as necessidades e prioridades da sua organização.

### <a name="why-personalize-your-environment"></a>Por que personalizar seu ambiente?

Alguns recursos funcionam melhor quando são personalizados para conforme as suas necessidades.
Ofereça uma experiência melhor aos seus usuários com seus próprios modelos de email. Decida quais notificações você receberá e personalize sua métrica de pontuação de risco para se ajustar às preferências da sua organização.

## <a name="step-5-organize-the-data-according-to-your-needs"></a>Etapa 5. [Organizar os dados de acordo com as suas necessidades](ip-tags.md)

Tarefa recomendada: configurar recursos importantes

### <a name="to-create-ip-address-tags"></a>Para criar marcas de endereço IP

1. Na engrenagem de configurações, selecione **Configurações do Cloud Discovery**.
1. Na engrenagem de configurações, selecione **Intervalos de endereço IP**.
1. Clique no sinal de mais ( **+** ) para adicionar um intervalo de endereços IP.
1. Insira os **detalhes**, o **local**, as **marcas** e a **categoria** do intervalo de IP.
1. Escolha **Criar**.

    Agora você pode usar marcas de IP ao criar políticas e ao filtrar e criar relatórios contínuos.

### <a name="to-create-continuous-reports"></a>Para criar relatórios contínuos

1. Na engrenagem de configurações, selecione **Configurações do Cloud Discovery**.
1. Em **Relatórios contínuos**, escolha **Criar relatório**.
1. Siga as etapas de configuração.
1. Escolha **Criar**.

Agora você pode exibir dados descobertos com base em suas próprias preferências, como unidades de negócios ou intervalos de IP.

### <a name="to-add-domains"></a>Para adicionar domínios

1. Na engrenagem de configurações, selecione **Configurações**.
1. Em **Detalhes da organização**, adicione os domínios internos da sua organização.
1. Selecione **Salvar**.

### <a name="why-should-you-configure-these-settings"></a>Por que você deve definir essas configurações?

Essas configurações ajudam a fornecer um controle melhor dos recursos no console. Com as marcas de IP, fica mais fácil criar políticas que atendam às suas necessidades, filtrar dados com precisão e muito mais. Use as Exibições de dados para agrupar seus dados em categorias lógicas.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md).

[!INCLUDE [Open support ticket](includes/support.md)].

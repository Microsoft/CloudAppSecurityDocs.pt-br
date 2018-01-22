---
title: "Implantar Cloud App Security para informações de uso em aplicativo de nuvem e controle | Microsoft Docs"
description: "Este tópico descreve o processo para colocar o Cloud App Security em funcionamento."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/15/2018
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: cf040b18-93d1-41e8-a26a-647c56afb00f
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 4526b93a0d95f4bd1cc0a97867ba585002408130
ms.sourcegitcommit: 458e936e1ac548eda37e9bf955b439199bbdd018
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2018
---
# <a name="deploy-cloud-app-security"></a>Implantar o Cloud App Security
O Cloud App Security pode ajudar você a aproveitar os benefícios de aplicativos na nuvem sem deixar de manter o controle dos recursos corporativos. Ele funciona ao melhorar a visibilidade de atividade de nuvem e ajuda a aumentar a proteção de dados corporativos. Neste tópico, o guiaremos pelas etapas utilizadas para configurar e trabalhar com o Cloud App Security.  

Sua organização deve ter uma licença para usar o Cloud App Security. Para obter mais informações, consulte a seção [Como comprar o Cloud App Security](https://www.microsoft.com/cloud-platform/cloud-app-security) na home page do Cloud App Security.  

>[!NOTE]
>Você não precisa de uma licença do Office 365 para usar o Cloud App Security.  

## <a name="prerequisites"></a>Pré-requisitos  
  
-   Sua organização deve ter uma licença do Cloud App Security para usar o produto. Para obter mais informações, consulte a seção [Como comprar o Cloud App Security](https://www.microsoft.com/cloud-platform/cloud-app-security) na home page do Cloud App Security.  
  
     Para obter suporte para a ativação de locatário, consulte [Contatar o suporte comercial do Office 365 ‑ Ajuda para Administradores](https://support.office.com/article/Contact-Office-365-for-business-support-Admin-Help-32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b).  
  
> [!NOTE] 
> Não é necessário ter uma licença do Office 365 para o Cloud App Security.  
  
-   Depois que tiver adquirido uma licença do Cloud App Security, você receberá um email com informações de ativação e um link para o portal do Cloud App Security.  
  
-   Para configurar o recurso Cloud App Security, é necessário ser Administrador global, Administrador de conformidade ou Leitor de segurança no Azure Active Directory ou no Office 365. É importante entender que um usuário atribuído a uma função de administrador terá as mesmas permissões em todos os aplicativos de nuvem que sua organização tenha assinado, independentemente de você atribuir a função no portal do Office 365, no Portal Clássico do Azure ou usando o módulo do Azure AD para [Windows PowerShell](https://technet.microsoft.com/library/mt736914.aspx). Para obter mais informações, consulte [Atribuir funções de administrador no Office 365](https://support.office.com/article/Assigning-admin-roles-in-Office-365-eac4d046-1afd-4f1a-85fc-8219c79e1504) e [Atribuindo funções de administrador no Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-assign-admin-roles/).  
  
-   Para executar o portal do Cloud App Security, use o Internet Explorer 11, Microsoft Edge (mais recente), Google Chrome (mais recente), Mozilla Firefox (mais recente) ou Apple Safari (mais recente).  

## <a name="to-access-the-portal"></a>Para acessar o portal

Para acessar o portal do Cloud App Security, acesse [https://portal.cloudappsecurity.com](https://portal.cloudappsecurity.com).  
  
Como alternativa, você pode acessar o portal por meio do **Centro de administração do Office 365** clicando no ícone dos Centros de administração ![ícone dos Centros de administração do O365](./media/o365-admin-centers-icon.png "ícone dos Centros de administração do O365") seguido por **Cloud App Security**.  
  
![Acesso do O365](./media/access-from-o365.png "Acesso do O365")  
  



## <a name="get-started-quickly-with-cloud-app-security"></a>Começar a trabalhar rapidamente com o Cloud App Security  

 

### <a name="step-1-set-up-cloud-discoveryset-up-cloud-discoverymd"></a>Etapa 1. [Configurar o Cloud Discovery](set-up-cloud-discovery.md).
Tarefa necessária: carregar logs de tráfego **Para criar um relatório contínuo do Cloud Discovery**

 1. Vá para **Configurações** > **Configurações de Cloud Discovery**.
 2. Selecione **Carregar log automaticamente**.
 3. Na guia **Fontes de dados**, adicione suas fontes.
 4. Na guia **Coletores de logs**, configure o coletor de logs.
 
**Para criar um relatório de instantâneo do Cloud Discovery**

 1. Vá para **Descobrir** > **Criar um novo relatório de instantâneo** e siga as etapas exibidas.

**Por que você deve configurar os relatórios do Cloud Discovery?**
Obter a visibilidade da TI Invisível na sua organização é essencial.
Depois que os logs são analisados, você pode facilmente descobrir quais aplicativos de nuvem são usados, por quais pessoas e em quais dispositivos.


### <a name="step-2-set-instant-visibility-protection-and-governance-actions-for-your-appsenable-instant-visibility-protection-and-governance-actions-for-your-appsmd"></a>Etapa 2. [Definir visibilidade, proteção e governança instantâneas para seus aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).
Tarefa necessária: Conectar aplicativos

1. Vá até **configurações** > **Conectores de aplicativo**.
2. Escolha **Conectar aplicativo** e selecione um aplicativo.
3. Siga as etapas de configuração para conectar o aplicativo.

**Por que conectar um aplicativo?**
Depois de conectar um aplicativo, você pode obter maior visibilidade para poder investigar atividades, arquivos e contas para os aplicativos em seu ambiente de nuvem.


### <a name="step-3-control-cloud-apps-with-policiescontrol-cloud-apps-with-policiesmd"></a>Etapa 3. [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md).
Tarefa necessária: Criar políticas

**Para criar políticas**

1. Vá para **Controlar** > **Modelos**.
2. Selecione um modelo de política na lista e selecione (+) **Criar política**.
3. Personalize a política (selecione filtros, ações e outras configurações) e, em seguida, escolha **Criar**.
4. No guia **Políticas**, selecione a política para ver as correspondências relevantes (atividades, arquivos, alertas).
 Dica: para cobrir todos os seus cenários de segurança de ambiente de nuvem, crie uma política para cada **categoria de risco**.

**Como as políticas podem ajudar sua organização?**
Você pode usar políticas para ajudar a monitorar as tendências, ver as ameaças de segurança e gerar alertas e relatórios personalizados. Com as políticas, você pode criar ações de governança e definir controles de compartilhamento de arquivos e prevenção de perda de dados.


### <a name="step-4-personalize-your-experiencemail-settingsmd"></a>Etapa 4. [Personalizar sua experiência](mail-settings.md).
Tarefa recomendada: Adicionar os detalhes da sua organização

**Para inserir as configurações de email**

1. Vá para **Configurações** > **Configurações de email**.
2. Em **Identidade do remetente de email** insira os endereços de email e o nome de exibição.
3. Em **Design de emails**, carregue o modelo de email da sua organização.

**Para definir as notificações de administrador**

1. Na barra de navegação, escolha seu nome de usuário e, em seguida, vá para **Configurações de usuário**.
2. Em **Notificações**, configure os métodos que você deseja definir para notificações do sistema.
3. Escolha **Salvar**.

**Para personalizar as métricas de pontuação**

1. Vá para **Configurações** > **Configurações de Cloud Discovery**.
2. Em **Configuração de métrica de pontuação**, configure a importância de vários valores de risco.
3. Escolha **Salvar**.

Agora as pontuações de risco atribuídas aos aplicativos descobertos são configuradas exatamente de acordo com as necessidades e prioridades da sua organização.

**Por que personalizar seu ambiente?**
Alguns recursos funcionam mais bem quando personalizados para suas necessidades. Forneça uma experiência melhor para os usuários com seus próprios modelos de email, decida quais notificações são recebidas e personalize sua métrica de pontuação de risco de acordo com as preferências da sua organização.


### <a name="step-5-organize-the-data-according-to-your-needsip-tagsmd"></a>Etapa 5. [Organizar os dados de acordo com suas necessidades](ip-tags.md).
Tarefa recomendada: Definir as configurações importantes

**Para criar marcas de endereço IP**

1. Vá para **Configurações** > **Marcas de endereço IP**.
2. Selecione (+) **Adicionar intervalo de endereços IP**.
3. Insira os **detalhes**, o **local**, as **marcas** e a **categoria** do intervalo de IP.
4. Escolha **Criar**.

 Agora, você pode usar marcas de IP ao criar políticas e ao filtrar e criar relatórios contínuos.

**Para criar relatórios contínuos**

1. Vá para **Configurações** > **Configurações de Cloud Discovery**.
2. Em **Gerenciar relatórios contínuos**, escolha **Criar relatório**.
3. Siga as etapas de configuração.
4. Escolha **Criar**.

Agora, você pode exibir dados descobertos com base em suas próprias preferências, como unidades de negócios ou intervalos de IP.

**Para adicionar domínios**

1. Vá para **Configurações** > **Configurações gerais**.
2. Em **Detalhes da organização**, adicione os domínios internos da sua organização.
3. Escolha **Salvar**.

**Por que você deve definir essas configurações?**
Essas configurações ajudam a oferecer um melhor controle dos recursos no console. Com marcas de IP, é mais fácil criar políticas que atendem às suas necessidades, filtrar os dados com precisão e muito mais. Use exibições de dados para agrupar seus dados em categorias lógicas.
  

## <a name="see-also"></a>Consulte Também

Configurar políticas [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md).    

Os clientes Premier também podem escolher o Cloud App Security diretamente no [Portal Premier](https://premier.microsoft.com/).   

---
title: Implantar o Cloud App Security
description: Este guia de início rápido descreve o processo usado para colocar o Cloud App Security em funcionamento, de modo que você possa usar o aplicativo na nuvem, além de obter insights e controle sobre ele.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: barbkess
ms.date: 1/27/2019
ms.topic: quickstart
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: cf040b18-93d1-41e8-a26a-647c56afb00f
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: d6e6206b9d361ad9a5b47c3ec76ecc8dac4a1e20
ms.sourcegitcommit: fd1bf30af3117d8ad6cf241f3e02ad5e4c4bc9a1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2019
ms.locfileid: "56409606"
---
#  <a name="quickstart-get-started-with-microsoft-cloud-app-security"></a>Início Rápido: Começar a usar o Microsoft Cloud App Security

*Aplica-se a: Microsoft Cloud App Security*

Este guia de início rápido apresenta as etapas para começar a usar o Cloud App Security. O Microsoft Cloud App Security pode ajudar você a aproveitar os benefícios de aplicativos na nuvem sem deixar de manter o controle dos recursos corporativos. Ele trabalha melhorando a visibilidade da atividade na nuvem e ajuda a aumentar a proteção de dados corporativos. Neste artigo, descreveremos as etapas utilizadas para configurar e trabalhar com o Microsoft Cloud App Security.  

Sua organização deve ter uma licença para usar o Cloud App Security. Para obter mais informações, consulte a seção [Como comprar o Cloud App Security](https://www.microsoft.com/cloud-platform/cloud-app-security) na home page do Cloud App Security.  

>[!NOTE]
>Você não precisa de uma licença do Office 365 para usar o Cloud App Security.  

## <a name="prerequisites"></a>Pré-requisitos  
  
- Sua organização precisa ter uma licença do Cloud App Security para usar o produto. Para obter mais informações, consulte a seção [Como comprar o Cloud App Security](https://www.microsoft.com/cloud-platform/cloud-app-security) na home page do Cloud App Security.  
  
     Para obter suporte para a ativação de locatário, consulte [Contatar o suporte comercial do Office 365 ‑ Ajuda para Administradores](https://support.office.com/article/Contact-Office-365-for-business-support-Admin-Help-32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b).  
- Depois de obter uma licença do Cloud App Security, você receberá um email com informações de ativação e um link para o portal do Cloud App Security.  
  
- Para configurar o Cloud App Security, você precisa ser Administrador global, Administrador de conformidade ou Leitor de segurança no Azure Active Directory ou no Office 365. É importante entender que um usuário que recebe uma função administrativa terá as mesmas permissões em todos os aplicativos na nuvem assinados por sua organização. Isso ocorrerá independentemente de você atribuir a função no portal do Office 365, no portal clássico do Azure ou usando o módulo do Azure AD para o [Windows PowerShell](https://technet.microsoft.com/library/mt736914.aspx). Para obter mais informações, consulte [Atribuir funções de administrador no Office 365](https://support.office.com/article/Assigning-admin-roles-in-Office-365-eac4d046-1afd-4f1a-85fc-8219c79e1504) e [Atribuindo funções de administrador no Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-assign-admin-roles/).  
  
- Para executar o portal do Cloud App Security, use o Internet Explorer 11, o Microsoft Edge (mais recente), o Google Chrome (mais recente), o Mozilla Firefox (mais recente) ou o Apple Safari (mais recente).  

## <a name="to-access-the-portal"></a>Para acessar o portal

Para acessar o portal do Cloud App Security, vá para [https://portal.cloudappsecurity.com](https://portal.cloudappsecurity.com).  
Acesse também o portal por meio do **Centro de administração do Office 365** clicando no ícone dos Centros de administração. ![Ícone dos centros de administração do O365](./media/o365-admin-centers-icon.png "O365 admin centers icon") Em seguida, selecione **Cloud App Security**.  
  
![Acesso do O365](./media/access-from-o365.png "Acesso do O365")  
  



## <a name="step-1-set-instant-visibility-protection-and-governance-actions-for-your-appsenable-instant-visibility-protection-and-governance-actions-for-your-appsmd"></a>Etapa 1. [Definir visibilidade, proteção e governança instantâneas para seus aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).
Tarefa necessária: Conectar aplicativos

1.Na engrenagem de configurações, selecione **Conectores de aplicativos**.
2. Clique no sinal de adição para adicionar um aplicativo e selecionar um aplicativo.
3. Siga as etapas de configuração para conectar o aplicativo.

**Por que conectar um aplicativo?**
Depois de conectar um aplicativo, você pode obter maior visibilidade para poder investigar atividades, arquivos e contas para os aplicativos em seu ambiente de nuvem.


## <a name="step-2-control-cloud-apps-with-policiescontrol-cloud-apps-with-policiesmd"></a>Etapa 2. [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md).
Tarefa necessária: Criar políticas

**Para criar políticas**

1. Vá para **Controlar** > **Modelos**.
2. Selecione um modelo de política na lista e selecione (+) **Criar política**.
3. Personalize a política (selecione filtros, ações e outras configurações) e, em seguida, escolha **Criar**.
4. No guia **Políticas**, selecione a política para ver as correspondências relevantes (atividades, arquivos, alertas).
 Dica: Para abranger todos os cenários de segurança do ambiente de nuvem, crie uma política para cada **categoria de risco**.

**Como as políticas podem ajudar sua organização?**
Você pode usar políticas para ajudar a monitorar as tendências, ver as ameaças de segurança e gerar alertas e relatórios personalizados. Com as políticas, você pode criar ações de governança e definir controles de compartilhamento de arquivos e prevenção de perda de dados.


## <a name="step-3-set-up-cloud-discoveryset-up-cloud-discoverymd"></a>Etapa 3. [Configurar o Cloud Discovery](set-up-cloud-discovery.md).

Tarefa necessária: Habilitar o Cloud App Security para exibir o uso do aplicativo na nuvem

1. [Integrar-se ao Windows Defender ATP](wdatp-integration.md) para habilitar automaticamente o Cloud App Security para monitorar seus dispositivos Windows 10 dentro e fora da sua empresa.
2. Se você usar o [Zscaler, integre-o](zscaler-integration.md) ao Cloud App Security.
3. Para ter a cobertura completa, crie um relatório contínuo do Cloud Discovery

   1. No ícone de engrenagem, selecione **Configurações do Cloud Discovery**.
   2. Escolha **Upload automático de log**.
   3. Na guia **Fontes de dados**, adicione suas fontes.
   4. Na guia **Coletores de logs**, configure o coletor de logs.
 
**Para criar um relatório de instantâneo do Cloud Discovery**

 Acesse **Descobrir** > **Relatório de instantâneo** e execute as etapas exibidas.

**Por que você deve configurar os relatórios do Cloud Discovery?**
Obter a visibilidade da TI Invisível na sua organização é essencial.
Depois que os logs são analisados, você pode descobrir com facilidade quais aplicativos na nuvem estão sendo usados, por quais pessoas e em quais dispositivos.

## <a name="step-4-personalize-your-experiencemail-settingsmd"></a>Etapa 4. [Personalizar sua experiência](mail-settings.md).
Tarefa recomendada: Adicionar os detalhes da organização

**Para inserir as configurações de email**

1. Na engrenagem de configurações, selecione **Configurações de email**.
2. Em **Identidade do remetente de email** insira os endereços de email e o nome de exibição.
3. Em **Design de emails**, carregue o modelo de email da sua organização.

**Para definir as notificações de administrador**

1. Na barra de navegação, escolha seu nome de usuário e, em seguida, vá para **Configurações de usuário**.
2. Em **Notificações**, configure os métodos que você deseja definir para notificações do sistema.
3. Escolha **Salvar**.

**Para personalizar as métricas de pontuação**

1. Na engrenagem de configurações, selecione **Configurações do Cloud Discovery**.
1. No ícone de configurações, selecione **Configurações do Cloud Discovery**.
2. Em **Métricas de pontuação**, configure a importância de vários valores de risco.
3. Escolha **Salvar**.

Agora as pontuações de risco atribuídas aos aplicativos descobertos são configuradas exatamente de acordo com as necessidades e prioridades da sua organização.

**Por que personalizar seu ambiente?**
Alguns recursos funcionam melhor quando personalizados para suas necessidades. Forneça uma experiência melhor para seus usuários com seus próprios modelos de email. Decida quais notificações serão recebidas e personalize sua métrica de pontuação de risco de acordo com as preferências de sua organização.


## <a name="step-5-organize-the-data-according-to-your-needsip-tagsmd"></a>Etapa 5. [Organizar os dados de acordo com suas necessidades](ip-tags.md).
Tarefa recomendada: Definir configurações importantes

**Para criar marcas de endereço IP**

1. No ícone de configurações, selecione **Configurações do Cloud Discovery**.
1.Na engrenagem de configurações, selecione **Intervalos de endereço IP**.
2. Clique no sinal de adição para adicionar um intervalo de endereços IP.
3. Insira os **detalhes**, o **local**, as **marcas** e a **categoria** do intervalo de IP.
4. Escolha **Criar**.

   Agora, você pode usar marcas de IP ao criar políticas e ao filtrar e criar relatórios contínuos.

**Para criar relatórios contínuos**

1. Na engrenagem de configurações, **Configurações do Cloud Discovery**.
2. Em **Relatórios contínuos**, escolha **Criar relatório**.
3. Siga as etapas de configuração.
4. Escolha **Criar**.

Agora, você pode exibir dados descobertos com base em suas próprias preferências, como unidades de negócios ou intervalos de IP.

**Para adicionar domínios**

1. Na engrenagem de configurações, selecione **Configurações**.
2. Em **Detalhes da organização**, adicione os domínios internos da sua organização.
3. Escolha **Salvar**.

**Por que você deve definir essas configurações?**
Essas configurações ajudam a oferecer um melhor controle dos recursos no console. Com marcas de IP, é mais fácil criar políticas que atendem às suas necessidades, filtrar os dados com precisão e muito mais. Use exibições de dados para agrupar seus dados em categorias lógicas.
  

## <a name="next-steps"></a>Próximas etapas

Configurar políticas [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md).    

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/)   

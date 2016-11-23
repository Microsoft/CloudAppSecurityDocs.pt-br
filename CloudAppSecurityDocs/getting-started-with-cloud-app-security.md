---
title: "Introdução ao Cloud App Security | Microsoft Docs"
description: "Este tópico descreve o processo para colocar o Cloud App Security em funcionamento."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: cf040b18-93d1-41e8-a26a-647c56afb00f
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 224c7039ecb7200ad951774ac5fb76202543a35c
ms.openlocfilehash: 2e9307b5166566efa65f4766c0331c6aa15118e9


---

# <a name="getting-started-with-cloud-app-security"></a>Introdução ao Cloud App Security
O Cloud App Security pode ajudá-lo a aproveitar os benefícios de aplicativos de nuvem, mas mantém o controle dos recursos corporativos. Ele funciona ao melhorar a visibilidade de atividade de nuvem e ajuda a aumentar a proteção de dados corporativos. Neste tópico, o guiaremos pelas etapas utilizadas para configurar e trabalhar com o Cloud App Security.  

Sua organização deve ter uma licença para usar o Cloud App Security. Para obter mais informações, consulte a seção de recursos de licenciamento em [Como comprar o Cloud App Security](https://www.microsoft.com/en-us/cloud-platform/cloud-app-security).  

>[!NOTE]
>Você não precisa de uma licença do Office 365 para usar o Cloud App Security.  

## <a name="get-started-quickly-with-cloud-app-security"></a>Começar a trabalhar rapidamente com o Cloud App Security  

|O que você deve fazer|Tarefa|Necessário?|Como|Descrição|  
|-------------------------|----------|---------------|-------------|-----------------|  
|Etapa 1. [Configurar o Cloud Discovery](set-up-cloud-discovery.md).|Carregar os logs de tráfego|Necessária|**Para criar um relatório de Cloud Discovery contínuo**<br /><br /> 1. Vá para **Configurações** > **Configurações de Cloud Discovery**.<br /><br /> 2. Selecione **Carregar log automaticamente**.<br /><br /> 3. Na guia **Fontes de dados**, adicione suas fontes.<br /><br /> 4. Na guia **Coletores de logs**, configure o coletor de logs.<br /><br /> **Para criar um relatório de instantâneo do Cloud Discovery**<br /><br /> 1. Vá para **Descobrir** > **Criar um novo relatório de instantâneo** e siga as etapas exibidas.|**Por que você deve configurar os relatórios do Cloud Discovery?**<br /> Obter a visibilidade da TI Invisível na sua organização é essencial. <br />Depois que os logs são analisados, você pode facilmente descobrir quais aplicativos de nuvem são usados, por quais pessoas e em quais dispositivos.|
|Etapa 2. [Definir visibilidade, proteção e governança instantâneas para seus aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).|Conectar aplicativos|Necessária|1. Vá para **Configurações** > **Aplicativos sancionados**.<br /><br /> 2. Escolha **Conectar aplicativo** e selecione um aplicativo.<br /><br /> 3. Siga as etapas de configuração para conectar o aplicativo.|**Por que conectar um aplicativo?**<br />Depois de conectar um aplicativo, você pode obter maior visibilidade para poder investigar atividades, arquivos e contas para os aplicativos em seu ambiente de nuvem.|
|Etapa 3. [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md).|Criar políticas|Necessária|**Para criar políticas**<br /><br /> 1. Vá para **Controlar** > **Modelos**.<br /><br /> 2. Selecione um modelo de política na lista e selecione (+) **Criar política**.<br /><br /> 3. Personalize a política (selecione filtros, ações e outras configurações) e, em seguida, escolha **Criar**.<br /><br /> 4. No guia **Políticas**, selecione a política para ver as correspondências relevantes (atividades, arquivos, alertas).<br /><br /> Dica: para cobrir todos os seus cenários de segurança de ambiente de nuvem, crie uma política para cada **categoria de risco**.|**Como as políticas podem ajudar sua organização?**<br />Você pode usar políticas para ajudar a monitorar as tendências, ver as ameaças de segurança e gerar alertas e relatórios personalizados. Com as políticas, você pode criar ações de governança e definir controles de compartilhamento de arquivos e prevenção de perda de dados.|
|Etapa 4. [Personalizar sua experiência](general-setup.md#Adallom_mailsettings).|Adicionar os detalhes da organização|Recomendado|**Para inserir as configurações de email**<br /><br /> 1. Vá para **Configurações** > **Configurações de email**.<br /><br /> 2. Em **Identidade do remetente de email** insira os endereços de email e o nome de exibição.<br /><br /> 3. Em **Design de emails**, carregue o modelo de email da sua organização.<br /><br /> **Para definir as notificações de administrador**<br /><br /> 1. Na barra de navegação, escolha seu nome de usuário e, em seguida, vá para **Configurações de usuário**.<br /><br /> 2. Em **Notificações**, configure os métodos que você deseja definir para notificações do sistema.<br /><br /> 3. Escolha **Salvar**.<br /><br /> **Para personalizar as métricas de pontuação**<br /><br /> 1. Vá para **Configurações** > **Configurações de Cloud Discovery**.<br /><br /> 2. Em **Configuração de métrica de pontuação**, configure a importância de vários valores de risco.<br /><br /> 3. Escolha **Salvar**.<br /><br /> Agora as pontuações de risco atribuídas aos aplicativos descobertos são configuradas exatamente de acordo com as necessidades e prioridades da sua organização.|**Por que personalizar seu ambiente?**<br />Alguns recursos funcionam mais bem quando personalizados para suas necessidades. <br />Forneça uma experiência melhor para os usuários com seus próprios modelos de email, decida quais notificações são recebidas e personalize sua métrica de pontuação de risco de acordo com as preferências da sua organização.|
|Etapa 5. [Organizar os dados de acordo com suas necessidades](general-setup.md#IPtagsandRanges).|Definir configurações importantes|Recomendado|**Para criar marcas de endereço IP**<br /><br /> 1. Vá para **Configurações** > **Marcas de endereço IP**.<br /><br /> 2. Selecione (+) **Adicionar intervalo de endereços IP**.<br /><br /> 3. Insira os **detalhes**, o **local**, as **marcas** e a **categoria** do intervalo de IP.<br /><br /> 4. Escolha **Criar**.<br /><br /> Agora, você pode usar marcas de IP ao criar políticas e ao filtrar e criar modos de exibição de dados.<br /><br /> **Para criar exibições**<br /><br /> 1. Vá para **Configurações** > **Configurações de Cloud Discovery**.<br /><br /> 2. Em **Exibições de dados**, selecione (+) **Adicionar exibição de dados**.<br /><br /> 3. Siga as etapas de configuração.<br /><br /> 4. Escolha **Criar**.<br /><br /> Agora, você pode exibir dados descobertos com base em suas próprias preferências, como unidades de negócios ou intervalos de IP.<br /><br /> **Para adicionar domínios**<br /><br /> 1. Vá para **Configurações** > **Configurações gerais**.<br /><br /> 2. Em **Detalhes da organização**, adicione os domínios internos da sua organização.<br /><br /> 3. Escolha **Salvar**.|**Por que você deve definir essas configurações?**<br />Essas configurações ajudam a oferecer um melhor controle dos recursos no console. Com marcas de IP, é mais fácil criar políticas que atendem às suas necessidades, filtrar os dados com precisão e muito mais. Use exibições de dados para agrupar seus dados em categorias lógicas.|  

## <a name="see-also"></a>Consulte Também

Saiba mais sobre as noções básicas em [Introdução ao Cloud App Security](getting-started-with-cloud-app-security.md).    
Para obter suporte técnico, vá para a página de [suporte assistido do Cloud App Security](http://support.microsoft.com/oas/default.aspx?prid=16031).   
Os clientes Premier também podem escolher o Cloud App Security diretamente no [Portal Premier](https://premier.microsoft.com/).   



<!--HONumber=Nov16_HO3-->



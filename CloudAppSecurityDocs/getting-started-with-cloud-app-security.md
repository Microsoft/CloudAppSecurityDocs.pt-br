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
ms.sourcegitcommit: ed4ea71b24767d3602d40894d1cbac7447bcd8a2
ms.openlocfilehash: 8b454edde557c408b644c9bff6f7bf6136ba9819


---

# <a name="getting-started-with-cloud-app-security"></a>Introdução ao Cloud App Security
O Cloud App Security ajuda os clientes a aproveitar os benefícios dos aplicativos de nuvem enquanto mantêm o controle por meio da maior visibilidade da atividade e maior proteção sobre dados importantes da empresa.  Esta documentação guia você pelas etapas a seguir para trabalhar com o Cloud App Security.  
  
Sua organização deve ter uma licença do Cloud App Security para usar o produto. Para obter mais informações, consulte [How to buy Cloud App Security](https://www.microsoft.com/server-cloud/products/cloud-app-security/default.aspx) (Como comprar o Cloud App Security) e verifique os [Licensing resources](https://www.microsoft.com/server-cloud/products/cloud-app-security/default.aspx) (Recursos de licenciamento).  
  
>[!NOTE]
>Não é necessário ter uma licença do Office 365 para o Cloud App Security.  
  
## <a name="get-started-quickly-with-cloud-app-security"></a>Começar a trabalhar rapidamente com o Cloud App Security  
  
|O que você deve fazer:|Tarefa|Necessário?|Como:|Descrição|  
|-------------------------|----------|---------------|-------------|-----------------|  
|ETAPA 1. [Configurar o Cloud Discovery](set-up-cloud-discovery.md).|Carregar os logs de tráfego|Necessária|**Criar um relatório de Cloud Discovery contínuo**<br /><br /> 1.   Vá para **Configurações** -> **Configurações de Cloud Discovery**.<br /><br /> 2.    Clique em **Upload log automatically (Carregar o log automaticamente)**.<br /><br /> 3.   Adicione as fontes de dados na guia **Fontes de dados**.<br /><br /> 4.    Configure o coletor de logs na guia **Coletores de logs**.<br /><br /> Criar um instantâneo de relatório do Cloud Discovery<br /><br /> 1.    Vá para **Descobrir** -> **Criar um novo relatório de instantâneo** e siga as etapas|**Por que você deve configurar os relatórios do Cloud Discovery?** Obter a visibilidade da TI Invisível na sua organização é essencial.  <br />Depois que os logs são analisados, você pode facilmente descobrir quais aplicativos de nuvem são usados, por quais pessoas e em quais dispositivos.|  
|ETAPA 2. [Habilitar ações de visibilidade, proteção e governança instantâneas para seus aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).|Conectar aplicativos|Necessária|1.   Vá para **Configurações** -> **Aplicativos sancionados**.<br /><br /> 2. Clique em **Conectar aplicativo** e escolha um aplicativo.<br /><br /> 3. Siga as etapas de configuração para conectar o aplicativo.|**Por que conectar um aplicativo?**<br /><br /> Somente depois de conectar um aplicativo você poderá obter maior visibilidade para investigar atividades, arquivos e contas no ambiente de nuvem para os aplicativos de nuvem.|  
|ETAPA 3. [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md).|Criar políticas|Necessária|**Criar políticas**<br /><br /> 1.  Vá para **Controlar** -> **Modelos**.<br /><br /> 2.    Selecione um modelo de política na lista e clique em (+) **Criar política**.<br /><br /> 3.  Personalize a política para suas necessidades (selecione filtros, ações e outras configurações) e clique em **Criar**.<br /><br /> 4.    No guia **Políticas**, clique na política que você criou para ver as correspondências relevantes (atividades, arquivos, alertas etc.).<br /><br /> Dica ‑ Crie uma política para cada **Categoria de risco** para cobrir todos os seus cenários de segurança de ambiente de nuvem.|**Como as políticas podem ajudar sua organização?**<br /><br /> As políticas fornecem as ferramentas para monitorar as tendências, ver as ameaças de segurança e gerar alertas e relatórios personalizados. Com as políticas, você pode criar várias ações de governança, DLP e controles de compartilhamento de arquivos.|  
|ETAPA 4. [Personalizar sua experiência](general-setup.md#Adallom_mailsettings).|Adicionar os detalhes da organização|Recomendado|**Inserir as configurações de email**<br /><br /> 1. Vá para **Configurações** -> **Configurações de email**.<br /><br /> 2.   Em **Identidade do remetente de email** insira os endereços de email e o nome de exibição.<br /><br /> 3. Em **Design de emails**, carregue o modelo de email da sua organização.<br /><br /> **Definir as notificações de administrador**<br /><br /> 1.    Clique no seu nome de usuário na barra de navegação e vá para **Configurações de Usuário**.<br /><br /> 2.    Em **Notificações**, configure os métodos que você deseja definir para notificações do sistema.<br /><br /> 3.  Clique em **Salvar**.<br /><br /> **Personalizar as métricas de pontuação**<br /><br /> 1.  Vá para **Configurações** -> **Configurações de Cloud Discovery**.<br /><br /> 2.    Em **Score metric configuration (Configuração de métrica de pontuação)**, configure a importância de vários valores de risco.<br /><br /> 3.    Clique em **Salvar**.<br /><br /> Agora as pontuações de risco atribuídas aos aplicativos descobertos são configuradas exatamente de acordo com as necessidades e prioridades da sua organização.|**Por que personalizar seu ambiente?**<br /><br /> Alguns recursos funcionam melhor quando personalizados para suas necessidades.  <br />Forneça uma experiência melhor para os usuários com seus próprios modelos de email, decida quais notificações são recebidas e personalize sua métrica de pontuação de risco de acordo com as preferências da sua organização.|  
|ETAPA 5. [Organizar os dados de acordo com suas necessidades](general-setup.md#IPtagsandRanges).|Definir configurações importantes|Recomendado|**Criar marcas de endereço IP**<br /><br /> 1.   Vá para **Configurações** -> **Marcas de endereço IP**.<br /><br /> 2. Clique em (+) **Adicionar Intervalo de Endereços IP**.<br /><br /> 3.    Insira os **detalhes**, o **local**, as **marcas** e a **categoria** do intervalo de IP.<br /><br /> 4. Clique em **Criar**.<br /><br /> Agora você pode usar marcas de IP ao criar políticas, ao filtrar e ao criar exibições de dados.<br /><br /> **Cria exibições**<br /><br /> 1.  Vá para **Configurações** -> **Configurações de Cloud Discovery**.<br /><br /> 2.    Em **Exibições de dados**, clique em (+) **Adicionar exibição de dados**.<br /><br /> 3.  Siga as etapas de configuração.<br /><br /> 4.  Clique em **Criar**.<br /><br /> Agora você pode exibir dados descobertos com base em suas próprias preferências, como unidades de negócios ou intervalos de IP.<br /><br /> **Adicionar domínios**<br /><br /> 1.    Vá para **Configurações** -> **Configurações gerais**.<br /><br /> 2.    Em **Detalhes da organização**, adicione os domínios internos da sua organização.<br /><br /> 3. Clique em **Salvar**.|**Por que você deve definir essas configurações?**<br /><br /> Essas configurações levam a um controle melhor e mais fácil de diversos recursos no console. Com marcas de IP é mais fácil criar políticas que atendem às suas necessidades, filtrar os dados com precisão e muito mais. Use exibições de dados para agrupar seus dados em categorias lógicas.|  
  
## <a name="see-also"></a>Veja também  
[Configuração geral](general-setup.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Oct16_HO4-->



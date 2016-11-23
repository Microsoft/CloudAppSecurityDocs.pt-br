---
title: Controle | Microsoft Docs
description: "Este artigo fornece informações sobre as ações de governança que você pode realizar no Cloud App Security para controlar o uso de aplicativos de nuvem da sua organização."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: bc11bbfe-ec6c-458c-8302-8112c383199d
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2f158e2f3643629d215eb23281b17a58ee7f78fc
ms.openlocfilehash: 5a051fc106661fc2266587ac5dbbb8bbdabd88bc


---

# <a name="control"></a>Control
Você pode aplicar ações de governança aos arquivos de usuários em seu ambiente de nuvem. Depois investigar completamente e aprender sobre sua nuvem, você pode usar ações de governança para ajudar a proteger sua organização.  

## <a name="apply-governance-actions"></a>Aplicar ações de governança  
Você pode aplicar ações de governança de dentro de políticas, de dentro de alertas e do log **Arquivos**.  

A qualquer momento, você pode examinar e ver o status de todas as ações de governança aplicadas anteriormente acessando o **ícone de configurações** da engrenagem ![Configurações](./media/settings-icon.png "settings icon") e selecionando o **Log de governança**.  

Para qualquer ação de governança com falha, selecione o ícone de **tentar novamente** ![ícone Tentar novamente](./media/retry-icon.png "retry icon") para aplicá-la outra vez.  

Dependendo do tipo de política, violação e aplicativo, diferentes ações de governança estão disponíveis.  

## <a name="move-from-detection-to-automatic-remediation"></a>Passar da detecção para a correção automática  
Depois de definir e personalizar seus filtros de política, você pode selecionar ações de governança automatizadas que serão executadas após cada violação da sua política.  
Uma vez que as ações de correção utilizam as APIs do provedor de nuvem, as ações podem variar de um aplicativo para outro.  

> [!NOTE]  
>  Tome muito cuidado ao definir ações de governança. Elas podem levar a perda irreversível de permissões de acesso a seus arquivos.  
> É uma boa ideia restringir os filtros para representar exatamente os arquivos nos quais você deseja agir, usando vários campos de pesquisa. Quanto mais restritos forem os filtros, melhor.  
>   
>  Para obter diretrizes, você pode usar o botão **Editar e visualizar resultados** na seção **Filtros**.  

![Editar e visualizar resultados da política de arquivos](./media/file-policy-edit-and-preview-results.png "file policy edit and preview results")  

## <a name="migration"></a>Migração  
O Cloud App Security ajuda a distribuir suas migrações, permitindo que você saiba quem na sua organização está usando quais aplicativos e fornecendo as ferramentas para monitorar a adoção de novos aplicativos. Ele também pode ajudar a descobrir quais tipos de aplicativos você deve oferecer na sua organização, fornecendo as ferramentas para ver o que todos já estão usando.  

### <a name="migrate-your-users-to-a-new-app"></a>Migrar seus usuários para um novo aplicativo  
Considere este cenário: você adquiriu recentemente o Office 365 e deseja que todos os usuários em sua organização parem de usar todos os outros aplicativos de armazenamento em nuvem e comecem a usar o OneDrive. Aqui está o que você talvez queira fazer:  

1.   Vá para seu **Cloud Discovery Dashboard (Painel do Cloud Discovery)** e em **Categorias**, filtre os aplicativos por **Armazenamento em Nuvem**. Em seguida, classifique os resultados por **Usuários** ou **Endereços IP** e verifique qual aplicativo é mais popular.  

2.   Você pode ver quais usuários estão usando outros aplicativos. Também é possível analisar detalhadamente esses aplicativos e notificar os usuários que você deseja que elas migrem para o OneDrive da seguinte maneira:

    1.  No seu **Painel do Cloud Discovery**, clique em **Dropbox** e, em seguida, selecione a guia **Endereço IP** ou **Usuários**.  

    2.  Selecione a seta ![ícone de seta](./media/arrow-icon.png "arrow icon") e selecione **Exportar**.  

### <a name="find-more-secure-alternatives"></a>Encontrar alternativas mais seguras  
O catálogo de serviços do Cloud App Security pode ajudá-lo a encontrar alternativas que funcionem para sua organização, em vez de aplicativos arriscados que seus usuários podem estar utilizando.  

Considere este cenário: você está pensando em comprar uma ferramenta de produtividade, mas não tem certeza se seus usuários a usariam.  

1.   Vá para o **Cloud Discovery Dashboard (Painel do Cloud Discovery)**.  

2.   Em **Categorias**, filtre aplicativos por **Produtividade**.  

3.   Para cada aplicativo em uso, confira a **Pontuação** para ver se é seguro e, se não for, por que não.  

4.   Se decidir que deseja comprar uma licença empresarial para toda a organização, pode ser útil também olhar a coluna **usuários**. Lá, é possível ver o que é mais popular entre os usuários, consultar se é confiável e conferir quais recursos de segurança existem antes de tomar a decisão.  

## <a name="see-also"></a>Veja também  
Para saber como usar e configurar políticas para controlar o uso do aplicativo de nuvem, consulte [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md).   
Para obter suporte técnico, vá para a página de [suporte assistido do Cloud App Security](http://support.microsoft.com/oas/default.aspx?prid=16031).   
Os clientes Premier também podem escolher o Cloud App Security diretamente no [Portal Premier](https://premier.microsoft.com/).  



<!--HONumber=Nov16_HO3-->



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
ms.sourcegitcommit: ed4ea71b24767d3602d40894d1cbac7447bcd8a2
ms.openlocfilehash: 9dc74c35f32c9a3dff251d6e0ac6b35a3591f4b9


---

# <a name="control"></a>Control
As ações de governança podem ser aplicadas aos arquivos de usuários em seu ambiente de nuvem. Depois investigar completamente e aprender sobre sua nuvem, você pode usar ações de governança para proteger sua organização.  
  
## <a name="applying-governance-actions"></a>Aplicando ações de governança  
As ações de governança podem ser aplicadas de dentro de políticas, de dentro de alertas e do log **Arquivos**.  
  
A qualquer momento, você pode examinar e ver o status de todas as ações de governança aplicadas anteriormente acessando o **ícone de configurações** da engrenagem ![Configurações](./media/settings-icon.png "settings icon") e clicando no **Log de governança**.  
  
Para qualquer ação de governança com falha, clique no ícone de tentar novamente ![ícone de tentar novamente](./media/retry-icon.png "retry icon") para aplicá-lo novamente.  
  
Dependendo do tipo de política, violação e aplicativo, diferentes ações de governança estão disponíveis.  
  
## <a name="moving-from-detection-to-automatic-remediation"></a>Passando da detecção para a correção automática  
Depois de definir e personalizar seus filtros de política, você pode selecionar ações de governança automatizadas que serão executadas em cada violação da política.  
Uma vez que as ações de correção utilizam as APIs do provedor de nuvem, as ações podem variar de um aplicativo para outro.  
  
> [!NOTE]  
>  Tenha muito cuidado ao definir as ações de controle, elas podem causar uma perda irreversível de permissões de acesso para seus arquivos.  
> É recomendável restringir os filtros para representar exatamente os arquivos nos quais você deseja agir, usando vários campos de pesquisa. Quanto mais restritos forem os filtros, melhor.  
>   
>  Para obter orientação, você pode usar o botão **Editar e visualizar resultados** na seção Filtros.  
  
![edição de política de arquivo e visualizar os resultados](./media/file-policy-edit-and-preview-results.png "file policy edit and preview results")  
  
## <a name="migration"></a>Migração  
O Cloud App Security ajuda a distribuir suas migrações, permitindo que você saiba quem na sua organização está usando quais aplicativos e fornecendo as ferramentas para monitorar a adoção de novos aplicativos. Ele também pode ajudar a descobrir quais tipos de aplicativos você deve oferecer na sua organização, fornecendo as ferramentas para ver o que todos já estão usando.  
  
### <a name="how-to-migrate-your-users-to-a-new-app"></a>Como migrar seus usuários para um novo aplicativo  
Considere este cenário: você adquiriu recentemente o Office 365 e deseja que todos os usuários em sua organização parem de usar todos os outros aplicativos de armazenamento em nuvem e comecem a usar o OneDrive. Aqui está o que você talvez queira fazer:  
  
-   Vá para seu **Cloud Discovery Dashboard (Painel do Cloud Discovery)** e em **Categorias**, filtre os aplicativos por **Armazenamento em Nuvem**. Em seguida, classifique os resultados por **Usuários** ou **Endereços IP** e verifique qual aplicativo é mais popular.  
  
-   Você pode ver quais usuários estão usando outros aplicativos.  
  
     Também é possível analisar detalhadamente esses aplicativos e notificar as pessoas que os estão utilizando que você deseja que elas migrem para o OneDrive da seguinte maneira:  
  
    1.  No seu **Cloud Discovery Dashboard (Painel do Cloud Discovery)**, clique em Dropbox e, em seguida, clique na guia **Endereço IP** ou **Usuários**.  
  
    2.  Clique na seta ![ícone de seta](./media/arrow-icon.png "arrow icon") e selecione **Exportar**.  
  
### <a name="find-more-secure-alternatives"></a>Encontrar alternativas mais seguras  
O catálogo de serviços do Cloud App Security pode ajudá-lo a encontrar alternativas que funcionem para sua organização, em vez de aplicativos arriscados que seus usuários podem estar utilizando.  
  
Considere este cenário: você está pensando em comprar uma ferramenta de produtividade, mas não tem certeza se seus usuários a usariam ou não.  
  
-   Vá para o **Cloud Discovery Dashboard (Painel do Cloud Discovery)**.  
  
-   Em **Categorias**, filtre aplicativos por **Produtividade**.  
  
-   Para cada aplicativo em uso, confira a **Pontuação** para ver se é seguro e se não for, por que não.  
  
-   Se você decidir que deseja comprar uma licença corporativa para toda a organização, talvez você também deseje analisar a coluna **Usuários** para ver o que já está mais popular entre os usuários, ver se é confiável e quais recursos de segurança ela tem antes de tomar a decisão.  
  
## <a name="see-also"></a>Veja também  
[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Oct16_HO4-->



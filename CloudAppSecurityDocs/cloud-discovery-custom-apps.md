---
title: Adicionar aplicativos personalizados ao Cloud Discovery no Cloud App Security | Microsoft Docs
description: Este tópico fornece informações sobre como adicionar aplicativos personalizados ao Cloud Discovery no Cloud App Security a fim de monitorar a TI Sombra.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/22/2018
ms.topic: article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 98b0d841-b33d-4ae9-b48b-d9ee77785eaa
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 4eeaca599a51e110773555d1c6862d34f8fd99a2
ms.sourcegitcommit: 45311f2cafef79483e40d971a4c61c7673834d96
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2018
---
*Aplica-se ao: Microsoft Cloud App Security*

# <a name="add-custom-apps-to-cloud-discovery"></a>Adicionar aplicativos personalizados ao Cloud Discovery
    
O Cloud Discovery analisa seus logs de tráfego com base no catálogo de aplicativos de nuvem do Microsoft Cloud App Security, com mais de 15.000 aplicativos de nuvem. O catálogo contém apenas aplicativos de nuvem disponíveis publicamente, para os quais o Cloud App Security fornece visibilidade e informações sobre o risco.

Para ter visibilidade dos aplicativos de nuvem excluídos do Catálogo de aplicativos de nuvem, o Cloud App Security permite que você descubra o uso de aplicativos de nuvem personalizados (aplicativos LOB) que foram desenvolvidos ou atribuído especificamente para sua organização.

Ao adicionar um novo aplicativo de nuvem personalizado, o Cloud App Security é capaz de corresponder mensagens de log de tráfego de proxy e de firewall carregadas para o aplicativo e, em seguida, fornecer visibilidade sobre o uso desse aplicativo em sua organização nas páginas do Cloud Discovery, por exemplo, quantos usuários usam o aplicativo, quantos endereços IP de origem exclusivos usam o aplicativo e a quantidade de tráfego transmitido de e para o aplicativo. 

Para adicionar um novo aplicativo de nuvem personalizado:

1. No portal do Cloud App Security, clique em **Descobrir** e em **Painel do Cloud Discovery**. 
  
   ![menu do painel do cloud discovery](./media/cloud-discovery-dashboard-menu.png)

2. No canto superior direito, clique nas reticências e, em seguida, selecione **Adicionar novo aplicativo personalizado**. 

   ![menu adicionar aplicativo personalizado](./media/add-custom-app-menu.png)

3. Preencha os campos para definir o novo registro de aplicativo que será listado no Catálogo de aplicativos de nuvem e no Cloud Discovery, após a detecção em seus logs de firewall.

   ![aplicativo personalizado](./media/add-custom-app.png)

4. Em **Domínios**, preencha os domínios exclusivos que são usados ao acessar o aplicativo personalizado. Esses domínios são usados para corresponder às mensagens do log de tráfego para esse aplicativo. Se a fonte de dados que você estiver usando não contiver informações sobre a URL do aplicativo, verifique se você preencheu os campos de endereço **IPv4** e **IPv6**.
5. Recomendamos a adição de notas que permitirão o controle das alterações para este registro.

Após a criação do aplicativo, ele ficará disponível para você no Catálogo de aplicativos de nuvem.

A qualquer momento, você pode clicar nas reticências no final da linha para editar ou excluir um aplicativo personalizado.

>[!NOTE]
> - Aplicativos personalizados são marcados automaticamente com a marca **Aplicativo personalizado** depois de adicioná-los. A marca desse aplicativo não pode ser removida.
Para exibir todos os seus aplicativos personalizados, defina o filtro **Marca do aplicativo** igual a "Aplicativo personalizado". 
> - Por padrão, os aplicativos personalizados têm uma pontuação de risco de 10, mas você pode usar a ação **Substituir pontuação do aplicativo** para alterá-la a qualquer momento.

  
## <a name="see-also"></a>Consulte Também  
[Políticas de atividade de usuário](user-activity-policies.md)   

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
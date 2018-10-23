---
title: Crie políticas para controlar permissões de aplicativo no Cloud App Security | Microsoft Docs
description: Este tópico oferece instruções para criar e trabalhar com políticas de permissão de aplicativo no Microsoft Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/08/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 9f68302c-bb3d-450c-bbf5-f8130cb163e3
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: e9fc80f128cf463654b6a4dce1f08717df271ee1
ms.sourcegitcommit: c80c584c444b12dc8c788208cf973b46192b0cf0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/10/2018
ms.locfileid: "49072745"
---
*Aplica-se ao: Microsoft Cloud App Security*


# <a name="app-permission-policies"></a>Políticas de permissão de aplicativo

Além da [investigação existente dos aplicativos OAuth](manage-app-permissions.md) conectados ao seu ambiente, você pode definir políticas de permissão para obter notificações automatizadas quando um aplicativo OAuth atender a determinados critérios. Por exemplo, você poderá ser alertado automaticamente quando houver aplicativos que requerem um alto nível de permissão e foram autorizados por mais de 50 usuários. 

As políticas de permissão de aplicativo permitem que você investigue quais permissões cada aplicativo solicitou e quais usuários as autorizaram para Office 365, G Suite e Salesforce. Você também poderá marcar essas permissões como aprovadas ou banidas. Marcá-las como banidas revogará as permissões de cada aplicativo de cada usuário que as autorizou. 

## <a name="create-a-new-app-permission-policy"></a>Criar uma nova política de permissão de aplicativo
Há duas maneiras de criar uma nova política de permissão de aplicativo. A primeira maneira é em **Investigar** e a segunda é em **Controle**. 

Para criar uma nova política de permissão de aplicativo:

1. Em **Investigar** selecione **Permissões de aplicativo**.
2. Filtre os aplicativos de acordo com suas necessidades, por exemplo, é possível exibir todos os aplicativos que solicitaram **Permissões** para **Modificar calendários em sua caixa de correio**.
3. Clique no botão **Nova política da pesquisa**. 
    ![nova política da pesquisa](./media/app-permissions-filter.png)
4. É possível usar o filtro **Uso da comunidade** para receber informações se a permissão a esse aplicativo é comum, incomum ou rara. Esse filtro poderá ser útil se um aplicativo do caso raro solicitar permissões com um alto nível de gravidade ou solicitar permissão de muitos usuários. 

Como alternativa, também é possível criar a política clicando em **Controle** e, em seguida, em **Políticas**. Em seguida, clique em **Criar política** e em **Política de permissão de aplicativo**.

  
   ![nova política de permissões de aplicativo](./media/app-permissions-policy.png)



  ## <a name="next-steps"></a>Próximas etapas 
  [Políticas de proteção de dados](data-protection-policies.md)   

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
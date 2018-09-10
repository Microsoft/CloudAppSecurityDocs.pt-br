---
title: Crie políticas para controlar permissões de aplicativo no Cloud App Security | Microsoft Docs
description: Este tópico oferece instruções para criar e trabalhar com políticas de permissão de aplicativo no Microsoft Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 6/24/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 9f68302c-bb3d-450c-bbf5-f8130cb163e3
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 02af6d6c109812156f8b8a3cf38a6f0599f2fec4
ms.sourcegitcommit: 0ac08ca7b3140b79f1d36ff7152476c188fa12b3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44143131"
---
*Aplica-se ao: Microsoft Cloud App Security*


# <a name="app-permission-policies"></a>Políticas de permissão de aplicativo

Além da [investigação existente dos aplicativos OAuth](manage-app-permissions.md) conectados ao seu ambiente, você pode definir políticas de permissão para obter notificações automatizadas quando um aplicativo OAuth atender a determinados critérios. Por exemplo, você poderá ser alertado automaticamente quando houver aplicativos que requerem um alto nível de permissão e foram autorizados por mais de 50 usuários. 

As políticas de permissão de aplicativo permitem investigar, para o Office 365, o G Suite e o Salesforce, quais permissões cada aplicativo solicitou e quais usuários as autorizaram. Você também pode marcar essas permissões como aprovadas ou banidas. Marcá-las como banidas revogará as permissões de cada aplicativo de cada usuário que as autorizou. 

Para criar uma nova política de permissão de aplicativo:
1. Em **Investigar** selecione **Permissões de aplicativo**.
2. Filtre os aplicativos de acordo com suas necessidades, por exemplo, é possível exibir todos os aplicativos que solicitaram **Permissões** para **Modificar calendários em sua caixa de correio**.
3. Clique no botão **Nova política da pesquisa**. 
    ![nova política da pesquisa](./media/app-permissions-filter.png)
4. É possível usar o filtro **Uso da comunidade** para saber se a liberação de permissões para esse aplicativo é comum, incomum ou rara. Isso poderá ser útil se um aplicativo do caso raro solicitar permissões com um alto nível de gravidade ou solicitar permissão para muitos usuários. 

Como alternativa, também é possível criar a política clicando em **Controle** e, em seguida, em **Políticas**. Em seguida, clique em **Criar política** e em **Política de permissão de aplicativo**.

  
   ![nova política de permissões de aplicativo](./media/app-permissions-policy.png)



  ## <a name="see-also"></a>Consulte Também  
  [Políticas de proteção de dados](data-protection-policies.md)   

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
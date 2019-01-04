---
title: Criar políticas para controlar aplicativos OAuth no Cloud App Security
description: Este artigo oferece instruções para criar e trabalhar com políticas de permissão de aplicativo no Microsoft Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/10/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 9f68302c-bb3d-450c-bbf5-f8130cb163e3
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 49ef099623e23454c6699f40b8b2178bb8ebb784
ms.sourcegitcommit: b86c3afd1093fbc825fec5ba4103e3a95f65758e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53176698"
---
# <a name="oauth-app-policies"></a>Políticas de aplicativo OAuth

*Aplica-se a: Microsoft Cloud App Security*

Além da [investigação existente dos aplicativos OAuth](manage-app-permissions.md) conectados ao seu ambiente, você pode definir políticas de permissão para obter notificações automatizadas quando um aplicativo OAuth atender a determinados critérios. Por exemplo, você poderá ser alertado automaticamente quando houver aplicativos que requerem um alto nível de permissão e foram autorizados por mais de 50 usuários. 

As políticas de aplicativo OAuth permitem que você investigue quais permissões cada aplicativo solicitou e quais usuários as autorizaram para Office 365, G Suite e Salesforce. Você também poderá marcar essas permissões como aprovadas ou banidas. Marcá-las como banidas revogará as permissões de cada aplicativo de cada usuário que as autorizou. 

## <a name="create-a-new-oauth-app-policy"></a>Criar uma nova política de aplicativo OAuth
Há duas maneiras de criar uma nova política de aplicativo OAuth. A primeira maneira é em **Investigar** e a segunda é em **Controle**. 

Para criar uma nova política de aplicativo OAuth:

1. Em **Investigar**, selecione **Aplicativo OAuth**.
2. Filtre os aplicativos de acordo com suas necessidades, por exemplo, é possível exibir todos os aplicativos que solicitaram **Permissões** para **Modificar calendários em sua caixa de correio**.
3. Clique no botão **Nova política da pesquisa**. 
    ![nova política da pesquisa](./media/app-permissions-filter.png)
4. É possível usar o filtro **Uso da comunidade** para receber informações se a permissão a esse aplicativo é comum, incomum ou rara. Esse filtro poderá ser útil se um aplicativo do caso raro solicitar permissões com um alto nível de gravidade ou solicitar permissão de muitos usuários. 
5. Você pode definir a política de acordo com as associações a grupo dos usuários que autorizaram os aplicativos. Por exemplo, um administrador poderá decidir definir uma política que revogue aplicativos incomuns se eles solicitarem permissões altas apenas se o usuário que autorizou as permissões for membro do grupo de administradores.

Como alternativa, também é possível criar a política clicando em **Controle** e, em seguida, em **Políticas**. Em seguida, clique em **Criar política** seguido por **Política de aplicativo OAuth**.

  
   ![nova política de aplicativo OAuth](./media/app-permissions-policy.png)



  ## <a name="next-steps"></a>Próximas etapas 
  [Políticas de proteção de dados](data-protection-policies.md)   

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
---
title: Criar políticas para controlar aplicativos OAuth no Cloud App Security
description: Este artigo oferece instruções para criar e trabalhar com políticas de permissão de aplicativo no Microsoft Cloud App Security.
keywords: ''
author: ShlomoSagir-MS
ms.author: shsagir
manager: ShlomoSagir-MS
ms.date: 7/25/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 9f68302c-bb3d-450c-bbf5-f8130cb163e3
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 93d23f46dc5c0225d32f75876386375b402f3897
ms.sourcegitcommit: d1eb8ccf09840c659ba7170a2b92cd62d9d97a02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68494225"
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

## <a name="oauth-app-anomaly-detection-policies"></a>Políticas de detecção de anomalias do aplicativo OAuth

Além das políticas de aplicativo OAuth que você pode criar, há as seguintes políticas de detecção de anomalias prontas para uso que fazem o perfil de metadados de aplicativos OAuth para identificar aqueles que são potencialmente mal-intencionados:

| Nome da política | Descrição da política |
| --- | --- |
| Nome do aplicativo OAuth enganoso | Verifica os aplicativos OAuth conectados ao seu ambiente e dispara um alerta quando um aplicativo com um nome enganoso é detectado. Nomes enganosos, como cartas estrangeiras que se assemelham a letras latinas, podem indicar uma tentativa de disfarçar um aplicativo mal-intencionado como um aplicativo conhecido e confiável. |
| Nome do aplicativo OAuth suspeito | Verifica os aplicativos OAuth conectados ao seu ambiente e dispara um alerta quando um aplicativo com um nome suspeito é detectado. Nomes suspeitos, como nomes de aplicativos conhecidos publicados por editores desconhecidos, podem indicar uma tentativa de disfarçar um aplicativo mal-intencionado como um aplicativo conhecido e confiável. |
| A URL de redirecionamento não segura é usada por um aplicativo OAuth | Verifica os aplicativos OAuth conectados ao seu ambiente e dispara um alerta quando um aplicativo usa uma URL de redirecionamento não segura (por exemplo, não usa o protocolo HTTPS), que expõe dados confidenciais à interceptação. |
| Nome do editor enganoso para um aplicativo OAuth | Verifica os aplicativos OAuth conectados ao seu ambiente e dispara um alerta quando um aplicativo com um nome de editor enganoso é detectado. Nomes de Publicadores enganosos, como cartas estrangeiras semelhantes a letras latinas, podem indicar uma tentativa de disfarçar um aplicativo mal-intencionado como um aplicativo proveniente de um Publicador conhecido e confiável. |

> [!NOTE]
> As políticas de detecção de anomalias só estão disponíveis para aplicativos OAuth que são autorizados em seu Azure Active Directory.

  ## <a name="next-steps"></a>Próximas etapas 
  [Políticas de proteção de dados](data-protection-policies.md)

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/)
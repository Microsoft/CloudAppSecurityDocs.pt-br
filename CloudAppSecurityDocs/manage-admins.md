---
title: Gerenciar acesso de administrador ao portal do Cloud App Security | Microsoft Docs
description: "Este tópico fornece instruções para configurar o acesso ao portal do Cloud App Security para seus administradores."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/10/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: b718edad-350c-4d90-b045-92529d701dc5
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: f4d336b48dc7f3655a60d64ec4fe7e066db7f438
ms.sourcegitcommit: 50fac1cec86dfb8170ba9c63a8f58a4bf24e3c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2017
---
## <a name="managing-admin-access"></a>Gerenciar o acesso administrativo

O Cloud App Security dá suporte a controle de acesso baseado em função. Por padrão, as seguintes funções de administrador do Office 365 e o Azure AD têm acesso ao Cloud App Security:

- Administrador global e Administrador de segurança: os administradores com **Acesso completo** terão permissão total no Cloud App Security para adicionar administradores, adicionar políticas e configurações, carregar logs e executar ações de controle.

- Leitor de segurança: tem permissões somente leitura e pode gerenciar alertas. O Leitor de segurança não tem permissão para executar o seguinte:
      - Criar políticas e editar as existentes 
      - Executar ações de controle 
      - Carregar logs de descoberta
      - Proibir ou aprovar aplicativos de terceiros
      - Acessar e exibir a página de configurações de intervalo de endereço IP
      - Acessar e exibir páginas de configurações 
      - Acessar e exibir as configurações de Descoberta 
      - Acessar e exibir a página de Conectores de aplicativo
      - Acessar e exibir o Log de controle 
      - Acessar e exibir a página Gerenciar relatórios de instantâneo 

Para obter mais informações, consulte [Atribuindo funções de administrador no Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-assign-admin-roles).

Você também pode adicionar administradores adicionais de segurança ao Cloud App Security, sem adicionar usuários a funções administrativas do Azure Active Directory, fazendo o seguinte:

1. Clique na engrenagem de configurações ![ícone de configurações](./media/settings-icon.png "ícone de configurações") e, em seguida, em **Gerenciar acesso de administrador**. 

2. Adicione os administradores que devem ter acesso ao Cloud App Security.
  
      
3. Em seguida, clique na lista suspensa para definir o tipo de acesso que o administrador terá, **Acesso completo** ou **Alertas de gerenciamento e somente leitura**.

     >[!NOTE]
      >Qualquer administrador com acesso limitado a **Alertas de gerenciamento e somente leitura** que tenta acessar uma página restrita ou executar uma ação restrita receberá um erro indicando que ele não tem permissão para acessar a página ou executar a ação.

   ![gerenciar acesso de administrador](./media/manage-admin-access.png "gerenciar acesso de administrador")  

4. Clique em **Fechar**.  

   >[!NOTE]
    >Somente Administradores globais ou Administradores de segurança podem conceder acesso a outros usuários ao Cloud App Security.
  
**Para substituir as permissões de administrador:**

Se você quiser substituir a permissão do administrador no Azure Active Directory ou no Office 365, faça isso manualmente adicionando o usuário ao Cloud App Security e atribuindo permissões de usuário.
Por exemplo, se você quiser atribuir à Stephanie, uma Leitora de segurança no Azure Active Directory, o **Acesso completo** no Cloud App Security, adicione-a manualmente ao Cloud App Security e atribua a ela o **Acesso completo** a fim de substituir sua função e permitir a ela as permissões desejadas no Cloud App Security. 


Para adicionar outros administradores ao Cloud App Security:
1. Clique na engrenagem de configurações ![ícone de configurações](./media/settings-icon.png "ícone de configurações") e, em seguida, em **Gerenciar acesso de administrador**. 

2. Adicione os administradores que devem ter acesso ao Cloud App Security, selecione seu nível de acesso e clique em **Fechar**.



## <a name="see-also"></a>Veja também  
[Configurar o Cloud Discovery](set-up-cloud-discovery.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
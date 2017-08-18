---
title: "Implantação do proxy do Cloud App Security para Azure AD | Microsoft Docs"
description: "Este tópico fornece informações sobre como implantar o proxy do Cloud App Security para aplicativos do Azure AD."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 8/10/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 2490c5e5-e723-4fc2-a5e0-d0a3a7d01fc2
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 58b309ddcc893d47a8adc89e9b286eff97ec99ed
ms.sourcegitcommit: 4cf65f627f2d370ee4a4decae1acbb9658874056
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2017
---
# <a name="deploying-the-cloud-app-security-proxy-for-azure-ad"></a>Implantação do proxy do Cloud App Security para Azure AD

> [!NOTE]
> É altamente recomendável tentar a instalação em uma área restrita ou ambiente de teste antes de instalá-lo em um ambiente de produção.

As etapas descritas abaixo devem ser executadas para implantar o proxy do Cloud App Security e habilitar o controle de acesso e o controle de sessão.


## <a name="step-1-create-an-azure-ad-conditional-access-policy"></a>Etapa 1: Criar uma política de acesso condicional do Azure AD

1. No Azure Active Directory, em **Segurança**, clique em **Acesso condicional**.

 ![Acesso condicional do Azure AD](./media/conditional-access.png)

2. Clique em **Nova política** e crie uma nova política, certificando-se de, em **Sessão**, selecionar **Usar restrições impostas de proxy**.

## <a name="step-2-log-on-to-each-app"></a>Etapa 2: Fazer logon em cada aplicativo

Use suas credenciais para fazer logon em cada aplicativo que você deseja controlar com o proxy.

## <a name="step-3-add-the-apps-in-cloud-app-security"></a>Etapa 3: Adicionar os aplicativos no Cloud App Security

1.  No portal do Cloud App Security, vá até a engrenagem Configurações e escolha **Proxy**.

2. Agora os aplicativos dos quais você fez logon devem ser exibidos na tabela. 

3. Para cada aplicativo, clique nos três pontos no canto direito da linha da tabela e clique em **Continuar configuração**.

4. No assistente do proxy, clique em **Concluir**.


Em alguns minutos, todas as solicitações de logon para o seu aplicativo serão roteadas por meio do proxy do Cloud App Security. 

## <a name="test-the-configuration"></a>Testar a configuração

1.  Tente fazer logon no aplicativo. Se o logon falhar, verifique se você concluiu todas as etapas do Assistente de proxy corretamente. 

2.  No portal do Cloud App Security, em **Investigar**, selecione **Log de atividades** e verifique se há **log de logon único nos** eventos capturados pelo proxy.



## <a name="see-also"></a>Veja também  
[Trabalhando com o proxy do Cloud App Security](proxy-intro.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
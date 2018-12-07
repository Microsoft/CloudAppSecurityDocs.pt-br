---
title: Implantar o Controle de Aplicativo de Acesso Condicional do Microsoft Cloud App Security para aplicativos do Azure AD | Microsoft Docs
description: Este artigo fornece informações sobre como implantar os recursos de proxy reverso do Controle de Aplicativos de Acesso Condicional do Microsoft Cloud App Security para aplicativos do Azure AD.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/22/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 2490c5e5-e723-4fc2-a5e0-d0a3a7d01fc2
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: ef834c9b73af6a1bed34530b29bec4fd3581cc1e
ms.sourcegitcommit: b0b3e6c6f150fff8c286185826ce099601a12679
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2018
ms.locfileid: "52280554"
---
# <a name="deploy-conditional-access-app-control-for-azure-ad-apps"></a>Implantar o controle de aplicativo de acesso condicional para aplicativos do Azure AD

*Aplica-se ao: Microsoft Cloud App Security*

>[!div class="step-by-step"]
[« Anterior: Introdução ao Controle de Aplicativo de Acesso Condicional](proxy-intro-aad.md)<br>
[Próximo: Como criar uma política de sessão »](session-policy-aad.md)


Execute estas etapas para configurar aplicativos do Azure AD para ser controlados pelo Controle de Aplicativo de Acesso Condicional do Microsoft Cloud App Security.

**Etapa 1: [acesse o portal do Azure AD, crie uma política de acesso condicional para os aplicativos e roteie a sessão para o Cloud App Security](#add-azure-ad).**

**Etapa 2: [entre com um usuário no escopo para a política nos aplicativos](#sign-in-scoped).**

**Etapa 3: [retorne ao portal do Cloud App Security e selecione a notificação de faixa para adicionar os aplicativos](#banner-notification).**

**Etapa 4: [crie uma política de acesso](access-policy-aad.md) ou [crie uma política de sessão](session-policy-aad.md) para os aplicativos no Cloud App Security.**


> [!NOTE]
> Para implantar o Controle de Aplicativos de Acesso Condicional para aplicativos do Azure AD, será necessária uma [licença válida para o Azure AD Premium P1](https://docs.microsoft.com/azure/active-directory/license-users-groups).

## Etapa 1: adicione os aplicativos do Azure AD ao Cloud App Security <a name="add-azure-ad"></a>  

1. Crie uma política de TESTE de acesso condicional do Azure AD.

   1. No Azure Active Directory, em **Segurança**, clique em **Acesso condicional**.

      ![Acesso condicional do Azure AD](./media/aad-conditional-access.png)

   2. Clique em **Nova política** e crie uma política. Garanta que, em **Sessão**, você selecione **Usar restrições impostas pelo Controle de Aplicativos de Acesso Condicional**.

      ![Acesso condicional do Azure AD](./media/proxy-deploy-restrictions-aad.png)

   3. Na política de TESTE, em **Usuários**, atribua um usuário de teste ou um usuário que pode ser usado para um logon inicial.
    
   4. Na política de TESTE, em **Aplicativo de nuvem**, atribua os aplicativos que você deseja controlar com o Controle de Aplicativo de Acesso Condicional. 

      > [!NOTE]
      >Escolha aplicativos compatíveis com o Controle de Aplicativo de Acesso Condicional. O Controle de Aplicativos de Acesso Condicional é compatível com aplicativos configurados com aplicativos SAML e Open ID Connect com logon único no Azure AD. 

## Etapa 2: entre com um usuário no escopo para a política nos aplicativos <a name="sign-in-scoped"></a>

Depois de criar a política, entre em cada aplicativo configurado nessa política. Entre usando um usuário configurado na política. Lembre-se primeiro de sair das sessões existentes.

## Etapa 3: retorne ao portal do Cloud App Security e selecione a notificação de faixa para adicionar os aplicativos <a name="banner-notification"></a>

1. No portal do Cloud App Security, vá até a engrenagem de configurações e selecione **Controle de Aplicativo de Acesso Condicional**. 
    
     ![menu de proxy](./media/proxy-menu.png)

2. Você verá uma mensagem informando que novos aplicativos do Azure AD foram descobertos pelo Controle de Aplicativo de Acesso Condicional. Clique no link **Exibir novos aplicativos**.

   ![Controle de Aplicativo de Acesso Condicional exibir novos aplicativos](./media/proxy-view-new-apps.png)

3. Na caixa de diálogo que é aberta, você pode ver todos os aplicativos aos quais você se conectou na etapa anterior. Para cada aplicativo, clique no sinal de + e, em seguida, clique em **Adicionar**.

   ![Controle de Aplicativo de Acesso Condicional novos aplicativos](./media/proxy-new-app.png)

   > [!NOTE]
   > Se um aplicativo não for exibido no catálogo de aplicativos do Cloud App Security, ele será exibido na caixa de diálogo nos aplicativos não identificados juntamente com a URL de logon. Ao clicar no sinal de + para esses aplicativos, você poderá sugerir a adição do aplicativo ao catálogo. Depois que o aplicativo estiver no catálogo, execute as etapas novamente para implantar o aplicativo. 

4. Na tabela de aplicativos de Controle de Aplicativo de Acesso Condicional, examine a coluna de **Controles disponíveis** e verifique se são exibidos o acesso condicional do Azure AD e o controle de sessão. <br></br>Se o controle de Sessão não for exibido para um aplicativo, isso significará que ele ainda não está disponível para esse aplicativo específico. Em vez disso, você verá o link **Solicitar controle de sessão**. Clique para abrir uma caixa de diálogo e solicitar a integração do aplicativo ao controle de sessão. Nesse cenário, o processo de integração será executado junto com você pela equipe do Microsoft Cloud App Security.
  
   ![solicitar controle de sessão](./media/proxy-view-new-apps.png)

5. Opcional – Identifique os dispositivos usando certificados de cliente:

   1. Vá até a engrenagem de configurações e selecione **Identificação de dispositivo**.

   2. Faça upload de um certificado raiz.

      ![Identificação de dispositivo](./media/device-identification.png)
 
      Após o upload do certificado, você poderá criar políticas de acesso e políticas de sessão com base na **Marca de dispositivo** e no **Certificado do cliente válido**.
 
      > [!NOTE]
      >Um certificado será solicitado de um usuário somente se a sessão corresponder a uma política que usa o filtro de certificado de cliente válido. 

## <a name="test-the-deployment"></a>Testar a implantação

1. Primeiro saia das sessões existentes. Em seguida, tente entrar em cada aplicativo que foi implantado com êxito. Entre usando um usuário que corresponda à política configurada no Azure AD. 

2. No portal do Cloud App Security, em **Investigar**, selecione **Log de atividades** e garanta que as atividades de logon sejam capturadas para cada aplicativo.

3. Você pode filtrar clicando em **Avançado**e, em seguida, usando a filtragem **Origem é igual a acesso condicional do Azure Active Directory**.

    ![Filtre usando o acesso condicional do Azure AD](./media/sso-logon.png)

4. É recomendável que você entre em aplicativos móveis e da área de trabalho em dispositivos gerenciados e não gerenciados. Isso serve para garantir que as atividades sejam capturadas corretamente no log de atividades.<br></br>
   Para verificar se a atividade é capturada corretamente, clique em um log de logon único na atividade para abrir a gaveta de atividades. Verifique se a **Marca de agente do usuário** reflete corretamente se o dispositivo é um cliente nativo (o que significa um aplicativo móvel ou da área de trabalho) ou um dispositivo gerenciado (em conformidade, ingressado no domínio ou certificado do cliente válido).
 
   ![teste a marca de agente do usuário](./media/domain-joined.png)


Agora você está pronto para criar [políticas de acesso](access-policy-aad.md) e [políticas de sessão](session-policy-aad.md) para controlar seus aplicativos do Controle de Aplicativos de Acesso Condicional.


>[!div class="step-by-step"]
[« Anterior: Introdução ao Controle de Aplicativo de Acesso Condicional](proxy-intro-aad.md)<br>
[Próximo: Como criar uma política de sessão »](session-policy-aad.md)


## <a name="next-steps"></a>Próximas etapas 
[Trabalhar com o Controle de Aplicativo de Acesso Condicional do Microsoft Cloud App Security](proxy-intro-aad.md)   

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
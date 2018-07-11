---
title: Implantar o Controle de Aplicativo de Acesso Condicional do Microsoft Cloud App Security para aplicativos do Azure AD | Microsoft Docs
description: Este tópico fornece informações sobre como implantar recursos de proxy reverso do Controle de Aplicativo de Acesso Condicional do Microsoft Cloud App Security para aplicativos do Azure AD.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 7/4/2018
ms.topic: article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 2490c5e5-e723-4fc2-a5e0-d0a3a7d01fc2
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: c16e44132ec7047e5f1624907c184a0e03c6bf73
ms.sourcegitcommit: 2862ebeb9e886bea16e62eb87dfdace638cf67bb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/04/2018
ms.locfileid: "37799154"
---
*Aplica-se ao: Microsoft Cloud App Security*

# <a name="deploy-conditional-access-app-control-for-azure-ad-apps"></a>Implantar o controle de aplicativo de acesso condicional para aplicativos do Azure AD

>[!div class="step-by-step"]
[« Anterior: Introdução ao Controle de Aplicativo de Acesso Condicional](proxy-intro-aad.md)<br>
[Próximo: Como criar uma política de sessão »](session-policy-aad.md)


Execute estas etapas para configurar aplicativos do Azure AD para ser controlados pelo Controle de Aplicativo de Acesso Condicional do Microsoft Cloud App Security.

> [!NOTE]
> Para implantar o Controle de Aplicativos de Acesso Condicional para aplicativos do Azure AD, será necessária uma [licença válida para o Azure AD Premium P1](https://docs.microsoft.com/azure/active-directory/license-users-groups).

## <a name="step-1-add-azure-ad-apps-in-cloud-app-security"></a>Etapa 1: Adicione os aplicativos do Azure AD no Cloud App Security  

1. Crie uma política de TESTE de acesso condicional do Azure AD.

   1. No Azure Active Directory, em **Segurança**, clique em **Acesso condicional**.

      ![Acesso condicional do Azure AD](./media/aad-conditional-access.png)

   2. Clique em **Nova política** e crie uma nova política, certificando-se de, em **Sessão**, selecionar **Usar restrições impostas de Controle de Aplicativo de Acesso Condicional**.

      ![Acesso condicional do Azure AD](./media/proxy-deploy-restrictions-aad.png)

   3. Na política de TESTE, em **Usuários**, atribua um usuário de teste ou um usuário que pode ser usado para um logon inicial.
    
   4. Na política de TESTE, em **Aplicativo de nuvem**, atribua os aplicativos que você deseja controlar com o Controle de Aplicativo de Acesso Condicional. 

      > [!NOTE]
      >Escolha aplicativos compatíveis com o Controle de Aplicativo de Acesso Condicional. O Controle de Aplicativo de Acesso Condicional é compatível com aplicativos configurados com logon único SAML no Azure AD. Por exemplo, os aplicativos do Office 365 não estão configurados com SAML, não são compatíveis no momento.


2. Depois de criar a política, faça logon em cada aplicativo configurado na política com um usuário configurado na política. Certifique-se primeiro de fazer logoff de sessões existentes.

3. No portal do Cloud App Security, vá até a engrenagem de configurações e selecione **Controle de Aplicativo de Acesso Condicional**. 
    
     ![menu de proxy](./media/proxy-menu.png)

4. Você verá uma mensagem informando que novos aplicativos do Azure AD foram descobertos pelo Controle de Aplicativo de Acesso Condicional. Clique no link **Exibir novos aplicativos**.

   ![Controle de Aplicativo de Acesso Condicional exibir novos aplicativos](./media/proxy-view-new-apps.png)

5. Na caixa de diálogo que é aberta, você pode ver todos os aplicativos aos quais você se conectou na etapa anterior. Para cada aplicativo, clique no sinal de + e, em seguida, clique em **Adicionar**.

   ![Controle de Aplicativo de Acesso Condicional novos aplicativos](./media/proxy-new-app.png)

   > [!NOTE]
   > Se um aplicativo não for exibido no catálogo de aplicativos do Cloud App Security, ele será exibido na caixa de diálogo nos aplicativos não identificados juntamente com a URL de logon. Ao clicar no sinal de + para esses aplicativos, você poderá sugerir a adição do aplicativo ao catálogo. Depois que o aplicativo estiver no catálogo, execute as etapas novamente para implantar o aplicativo. 

6. Na tabela de aplicativos de Controle de Aplicativo de Acesso Condicional, examine a coluna de **Controles disponíveis** e verifique se são exibidos o acesso condicional do Azure AD e o controle de sessão. <br></br>Se o controle de sessão não aparece para um aplicativo, isso significa que ele ainda não está disponível para esse aplicativo específico e, em vez dele, você vê o link **Solicitar o controle de sessão**. Clique para abrir uma caixa de diálogo e solicitar a integração do aplicativo ao controle de sessão. Nesse cenário, o processo de integração será executado junto com você pela equipe do Microsoft Cloud App Security.
  
   ![solicitar controle de sessão](./media/proxy-view-new-apps.png)

7. Opcional – Identifique os dispositivos usando certificados de cliente:

   1. Vá até a engrenagem de configurações e selecione **Identificação de dispositivo**.

   2. Faça upload de um certificado raiz.

      ![Identificação de dispositivo](./media/device-identification.png)
 
      Depois que o certificado for carregado, você poderá criar políticas de acesso e políticas de sessão dependendo se a **Marca do dispositivo** é igual ou não ao **Certificado do cliente válido**.
 
      > [!NOTE]
      >Um certificado será solicitado de um usuário somente se a sessão corresponder a uma política que usa o filtro de certificado de cliente válido. 

## <a name="step-2-test-the-deployment"></a>Etapa 2: Teste a implantação

1. Primeiro faça logoff de quaisquer sessões existentes. Em seguida, tente fazer logon em cada aplicativo que foi implantado com êxito, usando um usuário que corresponda à política configurada no Azure AD. 

2. No portal do Cloud App Security, em **Investigar**, selecione **Log de atividades** e garanta que as atividades de logon sejam capturadas para cada aplicativo.

3. Você pode filtrar clicando em **Avançado**e, em seguida, usando a filtragem **Origem é igual a acesso condicional do Azure Active Directory**.

    ![Filtre usando o acesso condicional do Azure AD](./media/sso-logon.png)

4. É recomendável que você faça logon em aplicativos móveis e de área de trabalho por meio de dispositivos gerenciados e não gerenciados para garantir que as atividades sejam corretamente capturadas no log de atividades.<br></br>
   Para certificar-se de que a atividade será capturada corretamente, clique em um log de logon único na atividade para abrir a gaveta de atividades e verifique se a **Marca de agente do usuário** reflete corretamente se o dispositivo é um cliente nativo (que significa um aplicativo móvel ou de área de trabalho) ou o dispositivo é um dispositivo gerenciado (compatível, ingressado no domínio ou certificado de cliente válido).
 
   ![teste a marca de agente do usuário](./media/domain-joined.png)


Agora você está pronto para criar [políticas de acesso](access-policy-aad.md) e [políticas de sessão](session-policy-aad.md) para controlar seus aplicativos de Controle de Aplicativo de Acesso Condicional.


>[!div class="step-by-step"]
[« Anterior: Introdução ao Controle de Aplicativo de Acesso Condicional](proxy-intro-aad.md)<br>
[Próximo: Como criar uma política de sessão »](session-policy-aad.md)


## <a name="see-also"></a>Consulte Também  
[Trabalhar com o Controle de Aplicativo de Acesso Condicional do Microsoft Cloud App Security](proxy-intro-aad.md)   

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
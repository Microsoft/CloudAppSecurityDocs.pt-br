---
title: Implantar o Controle de Aplicativos de Acesso Condicional do Cloud App Security em aplicativos do Azure AD
description: Este artigo fornece informações sobre como implantar os recursos de proxy reverso do Controle de Aplicativos de Acesso Condicional do Microsoft Cloud App Security para aplicativos do Azure AD.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 7/12/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 2490c5e5-e723-4fc2-a5e0-d0a3a7d01fc2
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: b231e378da12c3b632fb58fb28097e7b49bee852
ms.sourcegitcommit: 8a49c166424fea83853b0a6895212367526abe78
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71085128"
---
# <a name="deploy-conditional-access-app-control-for-featured-apps"></a>Implantar o Controle de Aplicativos de Acesso Condicional para aplicativos em destaque

*Aplica-se a: Microsoft Cloud App Security*

>[!div class="step-by-step"]
[« Anterior: Introdução ao Controle de Aplicativos de Acesso Condicional](proxy-intro-aad.md)<br>
[Próximo: Integração e implantação de Controle de Aplicativos de Acesso Condicional para qualquer aplicativo»](proxy-deployment-any-app.md)

Siga estas etapas para configurar aplicativos em destaque para serem controlados pelo Microsoft Cloud App Security Controle de Aplicativos de Acesso Condicional.

**Etapa 1: [Vá para o portal do AD do Azure e crie uma política de acesso condicional para os aplicativos e encaminhe a sessão para Cloud App Security](#add-azure-ad)**

**Etapa 2: [Entrar em cada aplicativo usando um escopo de usuário para a política](#sign-in-scoped)**

**Etapa 3: Se você não selecionou uma política de Cloud App Security interna no Azure AD ou se quiser aplicar a política a um aplicativo qualquer, [vá para o portal de Cloud app Security](#portal)**

[**Etapa 4: Testar a implantação**](#test)

> [!NOTE]
> Para implantar o Controle de Aplicativos de Acesso Condicional nos aplicativos do Azure AD, você precisa de uma [licença do Azure AD Premium P1](https://docs.microsoft.com/azure/active-directory/license-users-groups) válida, bem como uma licença do Cloud App Security.

## Etapa 1: Crie uma política de teste de acesso condicional do Azure AD <a name="add-azure-ad"></a>  

1. Em Azure Active Directory, em **segurança**, clique em **acesso condicional**.

2. Clique em **Nova política** e crie uma política.

3. Na política TESTE, em **Usuários**, atribua um usuário de teste ou um usuário que possa ser usado para um logon e uma verificação iniciais.

4. Na política de TESTE, em **Aplicativo de nuvem**, atribua os aplicativos que você deseja controlar com o Controle de Aplicativo de Acesso Condicional. 

5. Em **Sessão**, defina a política para usar uma das políticas internas, **Somente monitorar** ou **Bloquear downloads**. Ou selecione **Usar política personalizada** para definir uma política avançada no portal do Cloud App Security. 

6. Adicione **Atribuições de condição** ou **Controles de concessão** aplicáveis (opcional).

   ![Acesso condicional do Azure AD](./media/azure-ad-caac-policy.png)

      > [!NOTE]
      >O Controle de Aplicativos de Acesso Condicional é compatível com qualquer aplicativo SAML ou Open ID Connect que esteja configurado com o logon único do Azure AD, incluindo esses aplicativos em destaque. Os aplicativos que não estão em destaque podem ser configurados com o controle de acesso no portal do Cloud App Security, por meio de uma solicitação para integrá-los no controle de sessão. 

7. Clique em **habilitar** e **salvar**.

## Etapa 2: Entrar em cada aplicativo usando um escopo de usuário para a política<a name="sign-in-scoped"></a>

Depois de criar a política, entre em cada aplicativo configurado nessa política. Entre usando um usuário configurado na política. Lembre-se primeiro de sair das sessões existentes.

Cloud App Security sincronizará os detalhes da política com seus servidores para cada novo aplicativo no qual você entrar.  Isso poderá levar até um minuto.

## Etapa 3: Configurar controles avançados e todos os aplicativos no portal de Cloud App Security<a name="portal"></a>

As instruções acima ajudaram a criar uma política interna do Cloud App Security para aplicativos em destaque diretamente no Azure AD.

Para configurar uma política avançada, crie uma política de [acesso](access-policy-aad.md) ou uma [política de sessão](session-policy-aad.md) no Cloud app Security.

Para aplicar a política a um aplicativo qualquer, siga as instruções para realizar a autointegração de [um aplicativo para uso com controle de aplicativos de acesso condicional](proxy-deployment-any-app.md).

Para solicitar suporte para um aplicativo qualquer:

1. No portal do Cloud App Security, vá até a engrenagem de configurações e selecione **Controle de Aplicativo de Acesso Condicional**. Você verá uma mensagem informando que novos aplicativos do Azure AD foram descobertos pelo Controle de Aplicativo de Acesso Condicional.

    ![Menu do Controle de Aplicativos de Acesso Condicional](./media/caac-menu.png)

2. Clique em **Exibir novos aplicativos**.

    ![Controle de Aplicativos de Acesso Condicional, exibir novos aplicativos](./media/caac-view-apps.png)

3. Na tela que é aberta, veja todos os aplicativos em que entrou na etapa anterior. Para cada aplicativo, clique no sinal de + e, em seguida, clique em **Adicionar**.

   > [!NOTE]
   > Se um aplicativo não for exibido no catálogo de aplicativos do Cloud App Security, ele será exibido na caixa de diálogo nos aplicativos não identificados juntamente com a URL de logon. Ao clicar no sinal + desses aplicativos, você pode integrar o aplicativo como um aplicativo personalizado.

   ![Controle de Aplicativos de Acesso Condicional, aplicativos do Azure AD descobertos](./media/caac-discovered-aad-apps.png)

4. Na tabela Controle de Aplicativos de Acesso Condicional, examine a coluna **Controles disponíveis** e verifique se **Acesso condicional do Azure AD** e **Controle de sessão** aparecem.

   > [!NOTE]
   > Se o Controle de sessão não aparecer para um aplicativo, ele ainda não estará disponível para esse aplicativo específico. Em vez disso, você verá o link **Solicitar controle de sessão**.

     ![Solicitação de Controle de Aplicativos de Acesso Condicional](./media/caac-request.png)

5. Clique em **Solicitar controle de sessão** para solicitar que o aplicativo seja integrado ao controle de sessão. O processo de integração será executado com você pela equipe do Microsoft Cloud App Security.

6. Para configurar uma política para aproveitar o gerenciamento de dispositivos por meio de certificados de cliente:
    1. Vá até a engrenagem de configurações e selecione **Identificação de dispositivo**.
    2. Carregue um ou mais certificados raiz ou intermediários.
    3. Após o upload do certificado, você poderá criar políticas de acesso e políticas de sessão com base na **Marca de dispositivo** e no **Certificado do cliente válido**.

       ![ID do dispositivo do Controle de Aplicativos de Acesso Condicional](./media/caac-device-id.png)

> [!NOTE]
> Um certificado será solicitado de um usuário apenas se a sessão corresponder a uma política que use o filtro de certificado do cliente válido.

## Etapa 4: Testar a implantação<a name="test"></a>

1. Primeiro saia das sessões existentes. Em seguida, tente entrar em cada aplicativo que foi implantado com êxito. Entre usando um usuário que corresponda à política configurada no Azure AD.

2. No portal do Cloud App Security, em **Investigar**, selecione **Log de atividades** e garanta que as atividades de logon sejam capturadas para cada aplicativo.

3. Você pode filtrar clicando em **Avançado** e, em seguida, usando a filtragem **Origem é igual a Controle de acesso**.

    ![Filtre usando o acesso condicional do Azure AD](./media/sso-logon.png)

4. É recomendável que você entre em aplicativos móveis e da área de trabalho em dispositivos gerenciados e não gerenciados. Isso serve para garantir que as atividades sejam capturadas corretamente no log de atividades.<br>
Para verificar se a atividade é capturada corretamente, clique em um log de logon único na atividade para abrir a gaveta de atividades. Verifique se a **Marca de agente do usuário** reflete corretamente se o dispositivo é um cliente nativo (o que significa um aplicativo móvel ou da área de trabalho) ou um dispositivo gerenciado (em conformidade, ingressado no domínio ou certificado do cliente válido).

> [!NOTE]
> Depois de implantado, você não pode remover um aplicativo da página de Controle de Aplicativos de Acesso Condicional. Desde que você não defina uma política de acesso ou sessão no aplicativo, o Controle de Aplicativos de Acesso Condicional não alterará comportamentos para o aplicativo.

>[!div class="step-by-step"]
[« Anterior: Introdução ao Controle de Aplicativos de Acesso Condicional](proxy-intro-aad.md)<br>[Próximo: Integração e implantação de Controle de Aplicativos de Acesso Condicional para qualquer aplicativo»](proxy-deployment-any-app.md)

## <a name="next-steps"></a>Próximas etapas 
[Trabalhando com Cloud App Security Controle de Aplicativos de Acesso Condicional](proxy-intro-aad.md)

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/)
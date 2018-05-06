---
title: Criar políticas de acesso do Cloud App Security para permitir e bloquear o acesso | Microsoft Docs
description: Este tópico descreve o procedimento para configurar uma política de acesso do Proxy do Cloud App Security para permitir e bloquear o acesso a aplicativos conectados por meio do Azure AD.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/22/2018
ms.topic: article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 9095cff1-f8b0-44a7-b1df-a83e674abbc6
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 4cf6ab04f91b2b834ba494870a62691d882ee556
ms.sourcegitcommit: 45311f2cafef79483e40d971a4c61c7673834d96
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2018
---
*Aplica-se ao: Microsoft Cloud App Security*

# <a name="access-policies"></a>Políticas de acesso 

> [!NOTE]
> Este é um recurso de versão prévia.

As políticas de acesso do Microsoft Cloud App Security permitem o monitoramento em tempo real e controle sobre o acesso a aplicativos na nuvem baseados em usuário, local, dispositivo e aplicativo. Crie políticas de acesso para qualquer dispositivo, incluindo dispositivos que não são ingressados em domínio e não gerenciados pelo Windows Intune distribuindo certificados do cliente para dispositivos gerenciados ou aproveitando os certificados existentes, como certificados MDM de terceiros. Por exemplo, implante certificados do cliente em dispositivos gerenciados e, em seguida, bloqueie o acesso em dispositivos sem um certificado. 

> [!NOTE]
> Em vez de permitir ou bloquear o acesso por completo, com as [políticas de sessão](session-policy-aad.md), é possível permitir o acesso durante o monitoramento da sessão e/ou limitar atividades de sessão específicas. 

## <a name="prerequisites-to-using-access-policies"></a>Pré-requisitos para uso das políticas de acesso

- Licença do Azure AD Premium P2
- Os aplicativos relevantes devem ser [implantados com o proxy](proxy-deployment-aad.md)
- Uma [política de acesso condicional do Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) que redireciona os usuários para o proxy do Cloud App Security deve estar em vigor, conforme descrito abaixo.

> [!NOTE]
> - As políticas de acesso também dão suporte a aplicativos configurados com provedores de identidade diferentes do Azure AD na Versão Prévia Privada. Para obter mais informações sobre a Versão Prévia Privada, envie um email para mcaspreview@microsoft.com.

## <a name="create-an-azure-ad-conditional-access-policy"></a>Criar uma política de acesso condicional do Azure AD

As políticas de acesso condicional do Azure Active Directory e as políticas de sessão do Cloud App Security trabalham juntas para examinar cada sessão de usuário e tomar decisões de política para cada aplicativo. Para configurar uma política de acesso condicional no Azure AD, siga este procedimento:

1. Configure uma [política de acesso condicional do Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) com atribuições de usuário ou grupo de usuários e o aplicativo SAML que você deseja controlar com o proxy do Cloud App Security. 

   > [!NOTE]
   > Apenas os aplicativos que foram [implantados com o proxy](proxy-deployment-aad.md) serão afetados por essa política.

2. Roteie usuários para o proxy do Cloud App Security selecionando **Usar restrições impostas pelo proxy** na folha **Sessão**.

   ![Acesso condicional do Azure AD às restrições do proxy](./media/proxy-deploy-restrictions-aad.png)

## <a name="create-a-cloud-app-security-access-policy"></a>Criar uma política de acesso do Cloud App Security 

Para criar uma nova política de acesso, siga este procedimento:

1. No portal, selecione **Controle** e, em seguida, **Políticas**.
2. Na página **Políticas**, clique em **Criar política** e selecione **Política de acesso**.  

   ![Criar política de acesso](./media/access-policy-menu.png)

3. Na janela **Política de acesso**, atribua um nome à política, como *Bloquear o acesso em dispositivos não gerenciados*.

   ![Nova política de acesso](./media/access-policy-screen.png)

4. Em **Origem da atividade** na seção **Atividades que correspondem a todos os seguintes**, selecione os filtros de atividade adicionais a serem aplicados na política. Eles podem incluir as seguintes opções: 
     
   - **Marcas de dispositivo**: use este filtro para identificar dispositivos não gerenciados.

   - **Local**: use este filtro para identificar locais desconhecidos (e, portanto, arriscados). 

   - **Endereço IP**: use nesse filtro para filtrar por endereços IP ou usar marcas de endereço IP atribuídas anteriormente. 

   - **Marca de agente do usuário**: use esse filtro para habilitar que a heurística identifique os aplicativos móveis e de área de trabalho. Esse filtro pode ser configurado como igual a ou não igual ao **Cliente nativo** e deve ser testado em relação a seus aplicativos móveis e de área de trabalho para cada aplicativo de nuvem.
  
       ![suporte de cliente nativo](./media/user-agent-tag.png)

5. Em **Ações**, selecione uma das seguintes opções: 

    - **Permitir**: defina essa ação para permitir o acesso explicitamente de acordo com os filtros de política definidos.

    - **Bloquear**: defina essa ação para bloquear o acesso explicitamente de acordo com os filtros de política definidos. 

6. Você pode **Criar um alerta para cada evento correspondente com a gravidade da política** e configurar um limite de alerta e selecionar se você deseja o alerta como um email, uma mensagem de texto ou ambos.




 
## <a name="see-also"></a>Consulte Também  
[Bloqueando downloads em dispositivos não gerenciados, usando funcionalidades de proxy do Microsoft Azure AD](use-case-proxy-block-session-aad.md)   

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
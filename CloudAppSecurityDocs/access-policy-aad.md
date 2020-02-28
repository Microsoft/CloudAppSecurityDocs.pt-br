---
title: Criar políticas de acesso de Cloud App Security para permitir e bloquear o acesso
description: Este artigo descreve o procedimento para configurar um Cloud App Security Controle de Aplicativos de Acesso Condicional política de acesso para permitir e bloquear o acesso a aplicativos conectados por meio do AD do Azure usando recursos de proxy reverso.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 4f0fc4fa4bef878f6b248357f8c9bae97e52bbce
ms.sourcegitcommit: 11ae264d365e403f7761e880e82aad80afc31228
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "77674588"
---
# <a name="access-policies"></a>Políticas de acesso

*Aplica-se a: Microsoft Cloud App Security*

Microsoft Cloud App Security políticas de acesso permitem o monitoramento em tempo real e o controle sobre o acesso a aplicativos de nuvem com base no usuário, no local, no dispositivo e no aplicativo. Você pode criar políticas de acesso para qualquer dispositivo, incluindo dispositivos que não são ingressados no domínio e não são gerenciados pelo Windows Intune, distribuindo certificados de cliente para dispositivos gerenciados ou usando certificados existentes, como certificados de MDM de terceiros. Por exemplo, você pode implantar certificados de cliente em dispositivos gerenciados e bloquear o acesso de dispositivos sem um certificado.

> [!NOTE]
> Em vez de permitir ou bloquear completamente o acesso, com [políticas de sessão](session-policy-aad.md) , você pode permitir o acesso enquanto monitora a sessão e/ou limita as atividades específicas da sessão.

## <a name="prerequisites-to-using-access-policies"></a>Pré-requisitos para usar políticas de acesso

- Licença do Azure AD Premium P1
- Os aplicativos relevantes devem ser [implantados com controle de aplicativos de acesso condicional](proxy-deployment-aad.md)
- Uma [política de acesso condicional do Azure ad](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) deve estar em vigor para redirecionar os usuários para Microsoft Cloud app Security, conforme descrito abaixo.

> [!NOTE]
> - As políticas de acesso também dão suporte a aplicativos configurados com provedores de identidade diferentes do Azure AD. Para obter mais informações, envie um email para mcaspreview@microsoft.com.

## <a name="create-an-azure-ad-conditional-access-policy"></a>Criar uma política de acesso condicional do Azure AD

Azure Active Directory políticas de acesso condicional e Cloud App Security políticas de sessão funcionam em conjunto para examinar cada sessão do usuário e tomar decisões sobre a política para cada aplicativo. Para configurar uma política de acesso condicional no Azure AD, siga este procedimento:

1. Configure uma [política de acesso condicional do Azure ad](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) com atribuições para usuário ou grupo de usuários e o aplicativo que você deseja controlar com controle de aplicativos de acesso condicional.

    > [!NOTE]
    > Somente os aplicativos que foram [implantados com controle de aplicativos de acesso condicional](proxy-deployment-aad.md) serão afetados por essa política.

2. Encaminhe os usuários para Microsoft Cloud App Security selecionando as **restrições de uso controle de aplicativos de acesso condicional impostas** em **sessão**.

## <a name="create-a-cloud-app-security-access-policy"></a>Criar uma política de acesso de Cloud App Security

Para criar uma nova política de acesso, siga este procedimento:

1. No portal, selecione **controle** seguido por **políticas**.
2. Na página **políticas** , clique em **criar política** e selecione **política de acesso**.

3. Na janela **política de acesso** , atribua um nome para a política, como *bloquear o acesso de dispositivos não gerenciados*.

4. Nas **atividades que correspondem a todas as seções a seguir** , em **origem da atividade**, selecione filtros de atividade adicionais a serem aplicados à política. Os filtros incluem as seguintes opções:

    - **Marcas de dispositivo**: Use este filtro para identificar dispositivos não gerenciados.

    - **Local**: Use este filtro para identificar locais desconhecidos (e, portanto, arriscados).

    - **Endereço IP**: Use este filtro para filtrar por endereços IP ou use marcas de endereço IP atribuídas anteriormente.

    - **Marca de agente do usuário**: Use este filtro para habilitar a heurística para identificar aplicativos móveis e da área de trabalho. Esse filtro pode ser definido como Equals ou não é igual a. Os valores devem ser testados em seus aplicativos móveis e de área de trabalho para cada aplicativo de nuvem.

5. Em **ações**, selecione uma das seguintes opções:

    - **Teste**: defina essa ação para permitir explicitamente o acesso de acordo com os filtros de política definidos por você.

    - **Bloquear**: defina essa ação para bloquear explicitamente o acesso de acordo com os filtros de política definidos.

6. Você pode **criar um alerta para cada evento de correspondência com a severidade da política** e definir um limite de alerta e selecionar se deseja o alerta como um email, uma mensagem de texto ou ambos.

## <a name="next-steps"></a>{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}

> [!div class="nextstepaction"]
> [Bloqueando downloads em dispositivos não gerenciados usando controles de sessão](use-case-proxy-block-session-aad.md)

## <a name="see-also"></a>Consulte também

> [!div class="nextstepaction"]
> [Como criar uma política de sessão](session-policy-aad.md)

> [!div class="nextstepaction"]
> [Explore os casos de uso populares»](use-case-proxy-block-session-aad.md)

[!INCLUDE [Open support ticket](includes/support.md)]

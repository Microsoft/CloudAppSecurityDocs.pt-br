---
title: Criar políticas de acesso do Cloud App Security para permitir e bloquear o acesso
description: Este artigo descreve o procedimento para configurar uma política de acesso do Controle de Aplicativos de Acesso Condicional do Cloud App Security para permitir e bloquear o acesso a aplicativos conectados por meio do Azure AD usando as funcionalidades de proxy reverso.
ms.date: 01/05/2021
ms.topic: how-to
ms.openlocfilehash: 951cde88df62054cf005d26e602d27acfb5aba23
ms.sourcegitcommit: ee66e70f711aa11501e308e53b1a4b46f2175e4e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97894596"
---
# <a name="access-policies"></a>Políticas de acesso

[!INCLUDE [Banner for top of topics](includes/banner.md)]

As políticas de acesso do Microsoft Cloud App Security permitem o monitoramento em tempo real e controle sobre o acesso a aplicativos na nuvem baseados em usuário, localização, dispositivo e aplicativo. Você pode criar políticas de acesso para qualquer dispositivo, incluindo dispositivos que não são uma junção híbrida do Azure AD e não são gerenciados pelo Microsoft Intune distribuindo certificados de cliente para dispositivos gerenciados ou usando certificados existentes, como certificados de MDM de terceiros. Por exemplo, implante certificados do cliente em dispositivos gerenciados e, em seguida, bloqueie o acesso em dispositivos sem um certificado.

> [!NOTE]
> Em vez de permitir ou bloquear o acesso por completo, com as [políticas de sessão](session-policy-aad.md), é possível permitir o acesso durante o monitoramento da sessão e/ou limitar atividades de sessão específicas.

## <a name="prerequisites-to-using-access-policies"></a>Pré-requisitos para uso das políticas de acesso

- Azure AD Premium licença P1 ou a licença exigida pela sua solução IdP (provedor de identidade)
- Os aplicativos relevantes devem ser [implantados com o Controle de Aplicativo de Acesso Condicional](proxy-deployment-aad.md)
- Para verificar se você configurou sua solução de IdP para trabalhar com o Cloud App Security, faça o seguinte:
  - Para [Acesso condicional do Azure AD](/azure/active-directory/active-directory-conditional-access-azure-portal), consulte [Configurar a integração com o Azure AD](proxy-deployment-aad.md#configure-integration-with-azure-ad)
  - Para outras soluções do IdP, consulte [Configurar a integração com outras soluções de IdP](proxy-deployment-aad.md#configure-integration-with-other-idp-solutions)

## <a name="create-a-cloud-app-security-access-policy"></a>Criar uma política de acesso do Cloud App Security

Para criar uma nova política de acesso, siga este procedimento:

1. Vá para **controle**  >  **políticas**  >  **acesso condicional**.

1. Clique em **Criar política** e selecione **Política de acesso**.

    ![Criar uma política de acesso condicional](media/create-policy-from-conditional-access-tab.png)

1. Na janela **Política de acesso**, atribua um nome à política, como *Bloquear o acesso em dispositivos não gerenciados*.

1. Na seção **Atividades que correspondem a todos os seguintes**, em **Origem da atividade**, selecione os filtros de atividade adicionais a serem aplicados à política. Os filtros incluem as seguintes opções:

    - **Marcas de dispositivo**: use este filtro para identificar dispositivos não gerenciados.

    - **Local**: use este filtro para identificar locais desconhecidos (e, portanto, arriscados).

    - **Endereço IP**: use nesse filtro para filtrar por endereços IP ou usar marcas de endereço IP atribuídas anteriormente.

    - **Marca de agente do usuário**: use esse filtro para habilitar que a heurística identifique os aplicativos móveis e de área de trabalho. Esse filtro pode ser definido como igual a ou não é igual a. Os valores devem ser testados nos aplicativos móveis e da área de trabalho para cada aplicativo na nuvem.

1. Em **Ações**, selecione uma das seguintes opções:

    - **Teste**: defina essa ação para permitir explicitamente o acesso de acordo com os filtros de política definidos por você.

    - **Bloquear**: defina essa ação para bloquear o acesso explicitamente de acordo com os filtros de política definidos.

1. Você pode **Criar um alerta para cada evento correspondente com a gravidade da política** e configurar um limite de alerta e selecionar se você deseja o alerta como um email, uma mensagem de texto ou ambos.

## <a name="related-videos"></a>Vídeos relacionados

> [!div class="nextstepaction"]
> [Controle de Aplicativos de Acesso Condicional Webinar](webinars.md#on-demand-webinars)

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [« ANTERIOR: Como criar uma política de sessão](session-policy-aad.md)

> [!div class="nextstepaction"]
> [PRÓXIMO: Explorar casos de uso populares »](use-case-proxy-block-session-aad.md)

## <a name="see-also"></a>Consulte também

> [!div class="nextstepaction"]
> [Bloqueando downloads em dispositivos não gerenciados usando controles de sessão](use-case-proxy-block-session-aad.md)

> [!div class="nextstepaction"]
> [Solução de problemas de controles de acesso e de sessão](troubleshooting-proxy.md)

[!INCLUDE [Open support ticket](includes/support.md)]
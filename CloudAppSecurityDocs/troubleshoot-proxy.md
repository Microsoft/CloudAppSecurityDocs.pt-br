---
title: Solucionar problemas Controle de Aplicativos de Acesso Condicional
description: Este artigo fornece uma lista de possíveis problemas de Controle de Aplicativos de Acesso Condicional e fornece possíveis resoluções.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 6/30/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: d98721a4ca08b3e415b8b0fff40676af1b3d37e6
ms.sourcegitcommit: 7c93b6f93d2699d466b172590710ed01697bbdad
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74720982"
---
# <a name="troubleshooting-conditional-access-app-control"></a>Solução de problemas Controle de Aplicativos de Acesso Condicional

*Aplica-se ao: Microsoft Cloud App Security*

Este artigo prohvides uma lista de possíveis problemas de Controle de Aplicativos de Acesso Condicional e fornece possíveis resoluções.

## <a name="troubleshooting-onboarded-apps"></a>Solução de problemas de aplicativos integrados

### <a name="the-sign-in-to-the-app-is-not-working"></a>A entrada no aplicativo não está funcionando

1. No Cloud App Security, na barra de menus, clique no ícone configurações engrenagem ![configurações](media/settings-icon.png "ícone de configurações") e selecione **controle de aplicativos de acesso condicional**.
1. Na lista de aplicativos, na linha na qual o aplicativo que você está configurando aparece, escolha os três pontos no final da linha e escolha **Editar aplicativo**.
1. Clique em **tratamento de nonce** para expandir a seção e, em seguida, selecione **habilitar manipulação de nonce**.

    ![Captura de tela da opção de tratamento de nonce.](media/troubleshooing-nonce-handling.png)

    > [!NOTE]
    > Se você tiver problemas ao navegar para páginas de aplicativo que não sejam a home page, consulte [Solucionando problemas de visitas subsequentes ao aplicativo não ir para a página esperada](#unexpected-page)

### Visitas subsequentes ao aplicativo não vão para a página esperada<a name="unexpected-page"></a>

As etapas a seguir se baseiam no uso do Fiddler como a ferramenta de registro de tráfego. A experiência pode ser diferente para outras ferramentas. Para obter mais informações sobre como usar o Fiddler, consulte [maneira fácil de coletar o log Fiddler](https://blogs.msdn.microsoft.com/maheshk/2016/05/03/easy-way-to-collect-fiddler-log-fiddlercap/).

1. Copie a URL da página no aplicativo que não vá para a página esperada-você precisará dela mais tarde.

    > [!NOTE]
    > Verifique se o domínio não inclui o sufixo de URL Cloud App Security (por exemplo, *. us2.CAS.ms*)

1. Use uma ferramenta de registro de tráfego como o Fiddler para monitorar a página.
1. Vá para a URL que você copiou anteriormente e autentique, se necessário.
1. Na ferramenta de registro de tráfego, procure a solicitação correspondente ao domínio e ao caminho com base no protocolo que você está usando.

    | Protocolo | Domain | Caminho | Nome do campo de estado |
    | --- | --- | --- | --- |
    | OIDC | `https://login.microsoftonline.com` | /common/oauth2/authorize | state |
    | SAML 2.0 | `https://login.microsoftonline.com` | *ID*de //saml2 | RelayState |

1. Selecione a solicitação e, na guia **inspetores** , selecione **WebForms**.
1. Criar uma cadeia de caracteres Regex com base no 

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Implantar o Cloud Discovery](set-up-cloud-discovery.md)

[!INCLUDE [Open support ticket](includes/support.md)]

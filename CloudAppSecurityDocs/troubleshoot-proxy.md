---
title: Solucionar problemas de controle de acesso condicional do aplicativo
description: Este artigo fornece uma lista de possíveis problemas de controle de aplicativo de acesso condicional e fornece as possíveis resoluções.
keywords: ''
author: ShlomoSagir-MS
ms.author: shsagir
manager: ShlomoSagir-MS
ms.date: 6/30/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: e051d00c118b8e41142f8c0d9cc726675dcea27d
ms.sourcegitcommit: ee00e0033bf45a5f795bfd3e1d71fa1f70f97acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67515037"
---
# <a name="troubleshooting-conditional-access-app-control"></a>Solução de problemas de controle de acesso condicional do aplicativo

*Aplica-se a: Microsoft Cloud App Security*

Prohvides neste artigo uma lista de controle de aplicativo de acesso condicional possíveis problemas e fornece as possíveis resoluções.

## <a name="troubleshooting-onboarded-apps"></a>Solucionar problemas de aplicativos integrados

### <a name="the-sign-in-to-the-app-is-not-working"></a>A entrada para o aplicativo não está funcionando

1. No Cloud App Security, na barra de menus, clique na engrenagem de configurações ![ícone de configurações](./media/settings-icon.png "ícone configurações") e selecione **controle de aplicativo de acesso condicional**.
1. Na lista de aplicativos, na linha na qual o aplicativo que você está configurando aparece, selecione os três pontos no final da linha e, em seguida, escolha **Editar aplicativo**.
1. Clique em **tratamento de Nonce** para expandir a seção e, em seguida, selecione **permitem o tratamento de nonce**.

    ![Captura de tela da opção de tratamento de nonce.](media/troubleshooing-nonce-handling.png)

    > [!NOTE]
    > Se você tiver problema navegar até as páginas de aplicativo que não seja a home page, consulte [visitas subsequentes de solução de problemas para o aplicativo não acesse a página esperada](#unexpected-page)

### Visitas subsequentes para o aplicativo não acesse a página esperada<a name="unexpected-page"></a>

As etapas a seguir baseiam-se sobre como usar o Fiddler como a ferramenta de registro em log de tráfego. A experiência pode ser diferente para outras ferramentas. Para obter mais informações sobre como usar o Fiddler, consulte [maneira fácil de coletar logs do fiddler](https://blogs.msdn.microsoft.com/maheshk/2016/05/03/easy-way-to-collect-fiddler-log-fiddlercap/).

1. Copie a URL da página no aplicativo que não vai para a página esperada – você precisará dele mais tarde.

    > [!NOTE]
    > Certifique-se de que o domínio não inclui o sufixo de URL de segurança do aplicativo de nuvem (por exemplo, *. us2.cas.ms*)

1. Use uma ferramenta de registro em log de tráfego, como o Fiddler para monitorar a página.
1. Vá para a URL que você copiou anteriormente e autenticar se necessário.
1. Na ferramenta de registro em log do tráfego, pesquise a solicitação de correspondência de domínio e o caminho com base para o protocolo que você está usando.

    | Protocol | Domain | Path | Nome do campo de estado |
    | --- | --- | --- | --- |
    | OIDC | `https://login.microsoftonline.com` | /Common/oauth2/Authorize | state |
    | SAML 2.0 | `https://login.microsoftonline.com` | /*id*/saml2 | RelayState |

1. Selecione a solicitação e, em seguida, nos **Inspectors** guia, selecione **WebForms**.
1. Criar uma cadeia de caracteres do regex com base no 

## <a name="next-steps"></a>Próximas etapas

[Implantar o Cloud Discovery](set-up-cloud-discovery.md)

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier](https://premier.microsoft.com/)

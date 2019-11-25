---
title: Set up your organization's settings in Cloud App Security
description: Este artigo explica como fornecer informações sobre sua organização no Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 11/01/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 2708e8606e1838678e7d2b66fcb4e32584d475fc
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2019
ms.locfileid: "74458754"
---
# <a name="basic-setup-for-cloud-app-security"></a>Configuração básica do Cloud App Security

*Aplica-se ao: Microsoft Cloud App Security*

O procedimento a seguir fornece instruções para personalizar o portal do Microsoft Cloud App Security.

## <a name="prerequisites"></a>Pré-requisitos

For portal access, it's necessary to add the following IP addresses to your Firewall's allow list to provide access for the Cloud App Security portal:

* 104.42.231.28

For US Government GCC High customers, it's also necessary to add the following IP addresses to your Firewall’s allow list to provide access for the Cloud App Security GCC High portal:

* 52.227.143.223
* 13.72.19.4

> [!NOTE]
> Para obter atualizações quando URLs e endereços IP forem alterados, assine o RSS conforme explicado em: [URLs e intervalos de endereços IP do Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).

## <a name="set-up-the-portal"></a>Configurar o portal

1. In the Cloud App Security portal, in the menu bar, click the settings cog ![settings icon](./media/settings-icon.png "ícone de configurações") and select **Settings** to configure your organization's details.

1. Em **Detalhes da organização**, é importante que você forneça um **Nome de exibição da organização** para sua organização. Ele é exibido em emails e páginas da Web enviadas do sistema.

1. Forneça um **Nome do ambiente** (locatário). Essa informação é especialmente importante se você gerencia mais de um locatário.

1. Também é possível fornecer um **Logotipo** que é exibido em notificações por email e páginas da Web enviadas do sistema. O logotipo deve ser um arquivo png com um tamanho máximo de 150 x 50 pixels em uma tela de fundo transparente.

1. Certifique-se de adicionar uma lista de seus **Domínios gerenciados**. A adição de domínios gerenciados é uma etapa crucial. O Cloud App Security usa os domínios gerenciados para determinar quais usuários são internos, externos e em que locais os arquivos devem e não devem ser compartilhados. Essas informações são usadas para relatórios e alertas.

    * Os usuários em domínios que não estão configurados como internos são marcados como externos. Os usuários externos não são verificados quanto a arquivos ou atividades.

1. Under **Auto sign out**, specify the amount of time a session can remain inactive before the session is automatically signed out.

1. Se você estiver se integrando com a integração da Proteção de Informações do Azure, confira [Integração da Proteção de Informações do Azure](azip-integration.md) para obter informações.

    * Para trabalhar com a integração da Proteção de Informações do Azure, habilite o [Conector de aplicativos para o Office 365](connect-office-365-to-microsoft-cloud-app-security.md).

1. If you're integrating with Azure Advanced Threat Protection integration, see [Azure Advanced Threat Protection Integration](azip-integration.md) for information.

1. Se a qualquer momento você desejar fazer o backup das suas configurações do portal, essa tela permitirá que você faça isso. Clique em **Exportar configurações do portal** para criar um arquivo JSON de todas as suas configurações do portal, incluindo regras de política, grupos de usuários e intervalos de endereços IP.

> [!NOTE]
> Se você usa o ExpressRoute, o Cloud App Security é implantado no Azure e totalmente integrado com o [ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-introduction/). Todas as interações com os aplicativos do Cloud App Security e o tráfego enviado a ele, incluindo o upload de logs de descoberta, são roteados por meio do **emparelhamento público** do ExpressRoute para aprimorar a latência, o desempenho e a segurança. Não há nenhuma etapa de configuração necessária do lado do cliente.
>
> Para obter mais informações sobre o emparelhamento público, consulte [Circuitos da Rota Expressa e domínios de roteamento](https://azure.microsoft.com/documentation/articles/expressroute-circuit-peerings/).

## <a name="next-steps"></a>Próximas etapas

[Configurar o Cloud Discovery](set-up-cloud-discovery.md)

[!INCLUDE [Open support ticket](includes/support.md)]

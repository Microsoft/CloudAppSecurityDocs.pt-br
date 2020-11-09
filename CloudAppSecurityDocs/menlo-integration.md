---
title: Integrar o Cloud App Security com segurança Menlo
description: Este artigo descreve como integrar o Microsoft Cloud App Security com o Menlo Security para Cloud Discovery contínuo e o bloqueio automatizado de aplicativos não aprovados.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 11/09/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 79d4e986632e33475be75a808244dc6a61226df5
ms.sourcegitcommit: 288f3011c0ce0e5f2d8cbaa9057a63be044465f7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2020
ms.locfileid: "94377740"
---
# <a name="integrate-cloud-app-security-with-menlo-security"></a>Integrar o Cloud App Security com segurança Menlo

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Se você trabalhar com a segurança Cloud App Security e Menlo, poderá integrar os dois produtos para aprimorar sua experiência de Cloud Discovery de segurança. A segurança do Menlo, como um gateway Web seguro autônomo, monitora o tráfego da sua organização, permitindo que você defina políticas para o bloqueio de transações. Juntos, Cloud App Security e segurança Menlo fornecem os seguintes recursos:

- Implantação direta de Cloud Discovery-use a segurança Menlo para fazer proxy de seu tráfego e enviá-lo para Cloud App Security. Isso elimina a necessidade de instalação dos coletores de logs em seus pontos de extremidade de rede para habilitar o Cloud Discovery.
- Os recursos de bloqueio da segurança do Menlo são automaticamente aplicados em aplicativos que você define como não aprovados no Cloud App Security.

## <a name="prerequisites"></a>Pré-requisitos

- Uma licença válida para Microsoft Cloud App Security, ou uma licença válida para Azure Active Directory Premium P1
- Uma licença válida para segurança do Menlo

## <a name="deployment"></a>Implantação

1. Faça logon no portal de administração do Menlo e use o [Guia de instalação da integração de segurança do Menlo com o Microsoft Cloud Access Security](https://admin.menlosecurity.com/docs/guides/web_admin_settings_casb.html?highlight=microsoft) para integrar os produtos.

1. Investigue os aplicativos na nuvem descobertos em sua rede. Para obter mais informações e as etapas de investigação, confira [Trabalhando com o Cloud Discovery](working-with-cloud-discovery-data.md).
1. Qualquer aplicativo definido como não aprovado no Cloud App Security será efetuado ping pela segurança do Menlo a cada duas horas e, em seguida, bloqueado automaticamente pela segurança do Menlo. Para saber mais sobre como cancelar a sanção de aplicativos, confira [Sanção/cancelamento de um aplicativo](governance-discovery.md#BKMK_SanctionApp).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]

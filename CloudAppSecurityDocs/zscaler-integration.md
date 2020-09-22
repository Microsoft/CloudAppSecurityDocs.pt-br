---
title: Integrar o Cloud App Security com o Zscaler
description: Este artigo descreve como integrar o Microsoft Cloud App Security ao Zscaler para habilitar o Cloud Discovery contínuo e o bloqueio automatizado de aplicativos não sancionados.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/03/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 73d475cea1f0fded9aea955e19a92ed88a493472
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90877230"
---
# <a name="integrate-cloud-app-security-with-zscaler"></a>Integrar o Cloud App Security com o Zscaler

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Se você trabalha com o Cloud App Security e o Zscaler, pode integrar os dois produtos para melhorar a experiência de segurança do Cloud Discovery. O Zscaler, como um proxy de nuvem autônomo, monitora o tráfego da sua organização, permitindo que você defina políticas para bloquear transações. Juntos, o Cloud App Security e o Zscaler oferecem os seguintes recursos:

- Implantação direta de Cloud Discovery-use Zscaler para fazer proxy de seu tráfego e enviá-lo para Cloud App Security. Isso elimina a necessidade de instalação dos coletores de logs em seus pontos de extremidade de rede para habilitar o Cloud Discovery.
- Os recursos de bloqueio do Zscaler são aplicados automaticamente nos aplicativos que você definiu como não sancionados no Cloud App Security.
- Aprimore o portal do Zscaler com a avaliação de risco do Cloud App Security para os 200 principais aplicativos na nuvem, que podem ser exibidos diretamente no portal do Zscaler.

## <a name="prerequisites"></a>Pré-requisitos

- Uma licença válida para Microsoft Cloud App Security, ou uma licença válida para Azure Active Directory Premium P1
- Uma licença válida do Zscaler Cloud 5.6
- Uma assinatura ativa do Zscaler NSS

## <a name="deployment"></a>Implantação

1. No portal do Zscaler, execute as etapas necessárias para concluir a [integração de parceiro do Zscaler com o Microsoft Cloud App Security](https://help.zscaler.com/zia/configuring-mcas-integration).
2. No portal do Cloud App Security, execute as seguintes etapas de integração:
    1. Clique no ícone de configurações e selecione **Configurações do Cloud Discovery**.
    2. Clique na guia **Carregamento de log automático** e em **Adicionar fonte de dados**.
    3. Na página **Adicionar fonte de dados**, insira as seguintes configurações:

        - Nome = NSS
        - Fonte = Zscaler QRadar LEEF
        - Tipo de receptor = Syslog - UDP

        ![fonte de dados Zscaler](media/data-source-zscaler.png)

        > [!NOTE]
        > Verifique se o nome da fonte de dados é **NSS.** Para obter mais informações sobre como configurar feeds do NSS, consulte [adicionando Cloud app Security feeds do NSS](https://help.zscaler.com/zia/adding-mcas-nss-feeds).

    4. Clique em **Exibir exemplo de arquivo de log esperado**. Em seguida, clique em **Baixar log de exemplo** para exibir um exemplo de log de descoberta e verificar se ele corresponde aos seus logs.<br />

3. Investigue os aplicativos na nuvem descobertos em sua rede. Para obter mais informações e as etapas de investigação, confira [Trabalhando com o Cloud Discovery](working-with-cloud-discovery-data.md).

4. Qualquer aplicativo que você definir como não sancionado no Cloud App Security receberá o ping do Zscaler a cada duas horas e será automaticamente bloqueado pelo Zscaler. Para saber mais sobre como cancelar a sanção de aplicativos, confira [Sanção/cancelamento de um aplicativo](governance-discovery.md#BKMK_SanctionApp).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]

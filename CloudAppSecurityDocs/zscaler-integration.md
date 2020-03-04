---
title: Integrar o Cloud App Security com o Zscaler
description: Este artigo descreve como integrar o Microsoft Cloud App Security com o Zscaler para Cloud Discovery contínuo e o bloqueio automatizado de aplicativos não aprovados.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/03/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: bc418943f4825c7433401f271d710333066039cc
ms.sourcegitcommit: 5a0ea6fe5b90aafadb90da25854dabc4cf05d5fc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78238370"
---
# <a name="integrate-cloud-app-security-with-zscaler"></a>Integrar o Cloud App Security com o Zscaler

*Aplica-se a: Microsoft Cloud App Security*

Se você trabalhar com Cloud App Security e Zscaler, poderá integrar os dois produtos para aprimorar sua experiência de Cloud Discovery de segurança. Zscaler, como um proxy de nuvem autônomo, monitora o tráfego da sua organização, permitindo que você defina políticas para o bloqueio de transações. Juntos, Cloud App Security e Zscaler fornecem os seguintes recursos:

- Implantação direta de Cloud Discovery-usando Zscaler para fazer proxy de seu tráfego e enviá-lo para Cloud App Security elimina a necessidade de instalar coletores de logs em seus pontos de extremidade de rede para habilitar o Cloud Discovery.
- Os recursos de bloco do Zscaler são automaticamente aplicados em aplicativos que você define como não aprovados no Cloud App Security.
- Aprimore seu portal do Zscaler com a avaliação de risco de Cloud App Security para aplicativos de nuvem líderes de 200, que podem ser exibidos diretamente no portal do Zscaler.

## <a name="prerequisites"></a>Prerequisites

- Uma licença válida do Microsoft Cloud App Security
- Uma licença válida para o Zscaler Cloud 5,6
- Uma assinatura do Zscaler NSS ativa

## <a name="deployment"></a>Implantação

1. No portal do Zscaler, execute as etapas para concluir a [integração de parceiros do Zscaler com o Microsoft Cloud app Security](https://help.zscaler.com/zia/configuring-mcas-integration).
2. No portal de Cloud App Security, execute as seguintes etapas de integração:
    1. Clique nas configurações engrenagem e selecione **configurações de Cloud Discovery**.
    2. Clique na guia **upload de log automático** e, em seguida, clique em **Adicionar fonte de dados**.
    3. Na página **Adicionar fonte de dados** , insira as seguintes configurações:

        - Nome = NSS
        - Origem = Zscaler QRadar LEEF
        - Tipo de receptor = syslog-UDP

        ![Zscaler da fonte de dados](media/data-source-zscaler.png)

        > [!NOTE]
        > Verifique se o nome da fonte de dados é idêntico ao nome do feed usado ao criar o feed Cloud App Security NSS. Para obter mais informações, consulte [adicionando Cloud app Security feeds do NSS](https://help.zscaler.com/zia/adding-mcas-nss-feeds).

    4. Clique em **Exibir exemplo de arquivo de log esperado**. Em seguida, clique em **baixar log de exemplo** para exibir um log de descoberta de exemplo e verifique se ele corresponde aos seus logs.<br />

3. Investigue os aplicativos de nuvem descobertos na sua rede. Para obter mais informações e etapas de investigação, consulte [trabalhando com Cloud Discovery](working-with-cloud-discovery-data.md).

4. Qualquer aplicativo definido como não aprovado no Cloud App Security será efetuado ping pelo Zscaler a cada duas horas e, em seguida, bloqueado automaticamente pelo Zscaler. Para obter mais informações sobre aplicativos desaprovados, consulte [aprovar/desaprovar um aplicativo](governance-discovery.md#BKMK_SanctionApp).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]

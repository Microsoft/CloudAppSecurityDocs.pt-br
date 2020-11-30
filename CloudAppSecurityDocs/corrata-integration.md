---
title: Integrar o Cloud App Security com o Corrata
description: Este artigo descreve como integrar o Microsoft Cloud App Security com o Corrata para Cloud Discovery contínuo e o bloqueio automatizado de aplicativos não aprovados.
ms.date: 05/17/2020
ms.topic: how-to
ms.openlocfilehash: b9ec2e83bd99db8c4e884e371edfa5be689813a0
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96312362"
---
# <a name="integrate-cloud-app-security-with-corrata"></a>Integrar o Cloud App Security com o Corrata

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Se você trabalhar com Cloud App Security e Corrata, poderá integrar os dois produtos para aprimorar sua experiência de Cloud Discovery de segurança para o uso do aplicativo móvel. Corrata, como um gateway móvel local, monitora o tráfego da sua organização de dispositivos móveis, permitindo que você defina políticas para o bloqueio de transações. Juntos, Cloud App Security e Corrata fornecem os seguintes recursos:

- Implantação direta de Cloud Discovery-use Corrata para coletar o tráfego do dispositivo móvel e enviá-lo para Cloud App Security. Isso elimina a necessidade de instalação dos coletores de logs em seus pontos de extremidade de rede para habilitar o Cloud Discovery.
- Os recursos de bloco do Corrata são automaticamente aplicados em aplicativos que você define como não aprovados no Cloud App Security.
- Aprimore seu portal do Corrata com a avaliação de risco do Cloud App Security para aplicativos de nuvem líderes, que podem ser exibidos diretamente no portal do Corrata.

## <a name="prerequisites"></a>Pré-requisitos

- Uma licença válida do Microsoft Cloud App Security
- Uma licença válida para o Corrata Cloud

## <a name="deployment"></a>Implantação

1. No portal do Corrata, execute as etapas para concluir a [integração de parceiros do Corrata com o Microsoft Cloud app Security](https://corrata.com/microsoft-mcas-onboarding).
2. No portal do Cloud App Security, execute as seguintes etapas de integração:
    1. Clique no ícone de configurações e selecione **Configurações do Cloud Discovery**.
    2. Clique na guia **Carregamento de log automático** e em **Adicionar fonte de dados**.
    3. Na página **Adicionar fonte de dados**, insira as seguintes configurações:

        - Nome = Corrata
        - Origem = Corrata
        - Tipo de receptor = FTP

        ![Corrata da fonte de dados](media/data-source-corrata.png)

    4. Clique em **Exibir exemplo de arquivo de log esperado**. Em seguida, clique em **Baixar log de exemplo** para exibir um exemplo de log de descoberta e verificar se ele corresponde aos seus logs.

3. Investigue os aplicativos na nuvem descobertos em sua rede. Para obter mais informações e as etapas de investigação, confira [Trabalhando com o Cloud Discovery](working-with-cloud-discovery-data.md).

4. Qualquer aplicativo definido como não aprovado no Cloud App Security será efetuado ping pelo Corrata e, em seguida, bloqueado automaticamente pelo Corrata. Para saber mais sobre como cancelar a sanção de aplicativos, confira [Sanção/cancelamento de um aplicativo](governance-discovery.md#BKMK_SanctionApp).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]

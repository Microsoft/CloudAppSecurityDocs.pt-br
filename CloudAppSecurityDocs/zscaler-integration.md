---
title: Integrar o Cloud App Security com o Zscaler
description: Este artigo descreve como integrar o Microsoft Cloud App Security ao Zscaler para habilitar o Cloud Discovery contínuo e o bloqueio automatizado de aplicativos sancionados.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/14/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 8abeab8e-3b7a-46a7-bbec-9aaf26f778a8
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 0acb52d2a22fe05a293db6158df13d174bad3e49
ms.sourcegitcommit: 475dc75456f4683336e3e4875e3155677e4fb827
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/16/2018
ms.locfileid: "53450538"
---
# <a name="integrate-cloud-app-security-with-zscaler"></a>Integrar o Cloud App Security com o Zscaler

*Aplica-se a: Microsoft Cloud App Security*

Se você trabalha com o Cloud App Security e o Zscaler, pode integrar os dois produtos para melhorar a experiência de segurança do Cloud Discovery. O Zscaler, como um proxy de nuvem autônomo, monitora o tráfego da sua organização, permitindo que você defina políticas para bloquear transações. Juntos, o Cloud App Security e o Zscaler oferecem os seguintes recursos:

- Implantação contínua do Cloud Discovery: use o Zscaler como proxy do tráfego e envie-o ao Cloud App Security para eliminar a necessidade de instalar os coletores de log em pontos de extremidade de rede para habilitar o Cloud Discovery.
- Os recursos de bloqueio do Zscaler são aplicados automaticamente nos aplicativos que você definiu como não sancionados no Cloud App Security.
- Aprimore o portal do Zscaler com a avaliação de risco do Cloud App Security para os 200 principais aplicativos na nuvem, que podem ser exibidos diretamente no portal do Zscaler.

## <a name="prerequisites"></a>Pré-requisitos

- Uma licença válida do Microsoft Cloud App Security
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

         ![fonte de dados Zscaler](./media/data-source-zscaler.png)

    4. Clique em **Exibir exemplo de arquivo de log esperado**. Em seguida, clique em **Baixar log de exemplo** para exibir um exemplo de log de descoberta e verificar se ele corresponde aos seus logs.<br>

3. Investigue os aplicativos na nuvem descobertos em sua rede. Para obter mais informações e as etapas de investigação, confira [Trabalhando com o Cloud Discovery](working-with-cloud-discovery-data.md).

4. Qualquer aplicativo que você definir como não sancionado no Cloud App Security receberá o ping do Zscaler a cada duas horas e será automaticamente bloqueado pelo Zscaler. Para saber mais sobre como cancelar a sanção de aplicativos, confira [Sanção/cancelamento de um aplicativo](governance-discovery.md#BKMK_SanctionApp).

## <a name="next-steps"></a>Próximas etapas

[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
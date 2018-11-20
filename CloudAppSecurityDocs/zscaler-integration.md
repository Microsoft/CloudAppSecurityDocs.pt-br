---
title: Integrar o Cloud App Security com o Zscaler para o Cloud Discovery e o bloqueio automatizado de aplicativos sancionados | Microsoft Docs
description: Integre o Cloud App Security com o Zscaler para o Cloud Discovery e o bloqueio automatizado de aplicativos sancionados.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 8/28/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 8abeab8e-3b7a-46a7-bbec-9aaf26f778a8
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 972ee25a77f491704b6ebc17a059c2d1f7e4d367
ms.sourcegitcommit: 79e5aa5a5f90223a5963eb8f6df81a80578e9ce9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/14/2018
ms.locfileid: "51644307"
---
*Aplica-se ao: Microsoft Cloud App Security*

# <a name="integrate-cloud-app-security-with-zscaler"></a>Integrar o Cloud App Security com o Zscaler

Se você trabalha com o Cloud App Security e o Zscaler, pode integrar os dois produtos para melhorar a experiência de segurança do Cloud Discovery. O Zscaler, como um proxy de nuvem autônomo, monitora o tráfego da sua organização, permitindo que você defina políticas para bloquear transações. Juntos, o Cloud App Security e o Zscaler oferecem os seguintes recursos:

- Implantação contínua do Cloud Discovery: use o Zscaler como proxy do tráfego e envie-o ao Cloud App Security para eliminar a necessidade de instalar os coletores de log em pontos de extremidade de rede para habilitar o Cloud Discovery.
- Os recursos de bloqueio do Zscaler são aplicados automaticamente nos aplicativos que você definiu como não sancionados no Cloud App Security.
- Aprimore o portal Zscaler com a avaliação de risco do Cloud App Security para os 200 principais aplicativos em nuvem, que podem ser visualizados diretamente no portal do Zscaler.
    

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

          ![zscaler de fonte de dados](./media/data-source-zscaler.png)

    4. Clique em **Exibir exemplo de arquivo de log esperado**. Em seguida, clique em **Baixar log de exemplo** para exibir um exemplo de log de descoberta e verificar se ele corresponde aos seus logs.<br>
    
3. Investigue os aplicativos de nuvem descobertos na sua rede, confira [Como trabalhar com o Cloud Discovery](working-with-cloud-discovery-data.md) para ver mais informações e as etapas de investigação.
 
4. Qualquer aplicativo que você definir como não sancionado no Cloud App Security receberá o ping do Zscaler a cada duas horas e será automaticamente bloqueado pelo Zscaler. Para saber mais sobre como cancelar a sanção de aplicativos, confira [Sanção/cancelamento de um aplicativo](governance-discovery.md#BKMK_SanctionApp).
    
    
    
    
    

 
## <a name="see-also"></a>Consulte Também  
[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)   

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
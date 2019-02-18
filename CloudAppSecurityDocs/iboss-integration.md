---
title: Integrar o Cloud App Security com o iboss
description: Este artigo descreve como integrar o Microsoft Cloud App Security ao gateway de nuvem seguro do iboss para habilitar o Cloud Discovery contínuo e o bloqueio automatizado de aplicativos não sancionados.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: barbkess
ms.date: 2/2/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 920d4272-685b-4c4d-9b31-94a2c6f3503e
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 829dbac07eca84a3468da0260bec1141aa05a2c9
ms.sourcegitcommit: 8ef0438fa35916c48625ff750cb85e9628d202f2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56281587"
---
# <a name="integrate-cloud-app-security-with-iboss"></a>Integrar o Cloud App Security com o iboss

*Aplica-se a: Microsoft Cloud App Security*

Se você trabalha com o Cloud App Security e o iboss, é possível integrar os dois produtos para melhorar a experiência de segurança do Cloud Discovery. O iboss é um gateway de nuvem seguro e autônomo que monitora o tráfego da sua organização e permite que você defina políticas que bloqueiam as transações. Juntos, o Cloud App Security e o iboss oferecem os seguintes recursos:

- Implantação contínua do Cloud Discovery – use o iboss para usar um proxy de seu tráfego e enviá-lo ao Cloud App Security. Isso elimina a necessidade de instalação dos coletores de logs em seus pontos de extremidade de rede para habilitar o Cloud Discovery.
- Os recursos de bloqueio do iboss são aplicados automaticamente nos aplicativos que você definiu como não sancionados no Cloud App Security.
- Aprimore seu portal de administração do iboss com avaliação de risco do Cloud App Security dos principais 100 aplicativos de nuvem em sua organização, que podem ser exibidos diretamente no portal de administração do iboss.

## <a name="prerequisites"></a>Pré-requisitos

- Uma licença válida do Microsoft Cloud App Security
- Uma licença válida para o gateway de nuvem seguro do iboss (versão 9.1.100.0 ou posterior)

## <a name="deployment"></a>Implantação

1. No portal do Cloud App Security, execute as seguintes etapas de integração:
    1. Clique no ícone de configurações e selecione **Configurações do Cloud Discovery**. 
    2. Selecione a guia **Upload de log automático** e, em seguida, **Adicionar fonte de dados**.
    3. Na página **Adicionar fonte de dados**, insira as seguintes configurações:

       - Nome = iboss
       - Fonte = gateway de nuvem seguro do iboss
       - Tipo de receptor = Syslog - UDP

         ![fonte de dados iboss](./media/iboss-integration.png)

    4. Clique em **Exibir exemplo de arquivo de log esperado**. Em seguida, clique em **Baixar log de exemplo** para exibir um exemplo de log de descoberta e verificar se ele corresponde aos seus logs.<br>

3. Investigue os aplicativos na nuvem descobertos em sua rede. Para obter mais informações e as etapas de investigação, confira [Trabalhando com o Cloud Discovery](working-with-cloud-discovery-data.md).

4. Qualquer aplicativo que você definir como não sancionado no Cloud App Security receberá o ping do iboss a cada dez minutos e será automaticamente bloqueado pelo iboss. Para saber mais sobre como cancelar a sanção de aplicativos, confira [Sanção/cancelamento de um aplicativo](governance-discovery.md#BKMK_SanctionApp).

5. Para configurar o iboss para enviar logs de tráfego ao Microsoft Cloud App Security, entre em contato com suporte do iboss.

## <a name="next-steps"></a>Próximas etapas

[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/)  
  

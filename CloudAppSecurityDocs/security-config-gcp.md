---
title: Obter recomendações de configuração de segurança para o GCP
description: Este artigo fornece informações sobre como obter recomendações de configuração de segurança no Cloud App Security integrando com Google Cloud Platform.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 06/28/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 6c2c4e5d48af1650dce4744568f9bdb3df051a07
ms.sourcegitcommit: b15034dd50142afd8e95de22a9232f711b1eae6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85716468"
---
# <a name="security-configuration-for-google-cloud-platform"></a>Configuração de segurança para Google Cloud Platform

*Aplica-se a: Microsoft Cloud App Security*

Microsoft Cloud App Security fornece uma avaliação de configuração de segurança do seu ambiente Google Cloud Platform (GCP). Essa avaliação fornece recomendações de segurança fundamentais com base no parâmetro de [comparação de CIS (centro de segurança da Internet) para GCP](https://www.cisecurity.org/benchmark/google_cloud_computing_platform/), versão 1.1.0.

Essa avaliação fornece uma exibição organizacional das recomendações de configuração de segurança de todos os projetos do GCP e permite que os administradores de segurança investiguem as lacunas de configuração de segurança e iniciem a correção pelos proprietários dos recursos.

## <a name="prerequisites"></a>Pré-requisitos

- Você deve configurar o GCP Security Command Center com a análise de integridade de segurança para todos os seus projetos do GCP em sua organização. Para obter mais informações, consulte [Configurando o centro de comando de segurança do GCP](https://cloud.google.com/security-command-center/docs/quickstart-scc-setup) e habilitar a análise de integridade de [segurança](https://cloud.google.com/security-command-center/docs/how-to-use-security-health-analytics).
- Seus projetos do GCP devem estar conectados a Cloud App Security. Para obter mais informações, consulte [conectar o GCP ao Microsoft Cloud app Security](connect-google-gcp-to-microsoft-cloud-app-security.md).

## <a name="how-to-view-gcp-security-recommendations"></a>Como exibir as recomendações de segurança do GCP

1. Em Cloud app Security, navegue para **investigar**  >  **configuração de segurança**e, em seguida, selecione a guia **Google Cloud Platform** .

    > [!NOTE]
    > Pode levar até 15 minutos para que as alterações entrem em vigor.

    ![menu de configuração de segurança](media/security-configuration-menu.png)

1. Você pode filtrar as recomendações por tipo, recurso e assinatura. Além disso, você pode clicar no ícone de configuração de segurança ![Ícone ASC](media/asc-icon.png) para abrir a recomendação no centro de comando do GCP Security para obter mais informações e aprofundar-se na recomendação.

    ![configuração de segurança](media/security-configuration-gcp.png)

1. Selecione uma recomendação para exibir informações adicionais sobre a recomendação, incluindo uma descrição e diretrizes de correção detalhadas.

    ![configuração de segurança](media/security-configuration-gcp-details.png)

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
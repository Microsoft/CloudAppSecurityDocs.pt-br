---
title: Obter recomendações de configuração de segurança para o Azure
description: Este artigo fornece informações sobre como obter recomendações de configuração de segurança no Cloud App Security integrando-se à central de segurança do Azure.
ms.date: 09/15/2020
ms.topic: how-to
ms.openlocfilehash: e34cd55f3e09b36c1bbb4641a7842e525f3c56d7
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96315507"
---
# <a name="security-configuration-for-azure"></a>Configuração de segurança para o Azure

[!INCLUDE [Banner for top of topics](includes/banner.md)]

O Microsoft Cloud App Security fornece uma avaliação de configuração de segurança do seu ambiente do Azure. A avaliação, da plataforma da central de segurança do Azure, fornece recomendações para controles de segurança e configuração ausentes.

## <a name="prerequisites"></a>Pré-requisitos

Sua organização deve ter licenças da central de segurança do Azure para todas as assinaturas para as quais você deseja fornecer avaliações de configuração de segurança do Azure.

## <a name="how-to-enable-azure-security-recommendations"></a>Como habilitar as recomendações de segurança do Azure

Para habilitar as recomendações de configuração de segurança no Cloud App Security, ative sua assinatura da central de segurança do Azure navegando até o <a href="https://ms.portal.azure.com/#blade/Microsoft_Azure_Security/SecurityMenuBlade/0" target="_blank">portal</a>.

## <a name="how-to-view-azure-security-recommendations"></a>Como exibir as recomendações de segurança do Azure

1. Em Cloud app Security, navegue para **investigar** a  >  **configuração de segurança** e, em seguida, selecione a guia **Azure** .

    > [!NOTE]
    > Pode levar até 15 minutos para que as alterações entrem em vigor.

    ![menu de configuração de segurança](media/security-configuration-menu.png)

1. Você pode filtrar as recomendações por tipo, recurso e assinatura. Além disso, você pode clicar no ícone de configuração de segurança ![Ícone ASC](media/asc-icon.png) para abrir a recomendação na Central de Segurança do Azure para obter mais informações e se aprofundar na recomendação.

    > [!NOTE]
    > Para simplificar ainda mais a investigação, você pode criar consultas personalizadas e salvá-las para uso posterior. Após concluir a criação da sua consulta, clique no botão **Salvar como** no canto superior direito dos filtros.  No pop-up **Salvar consulta** , nomeie sua consulta.

    ![configuração de segurança](media/security-configuration-azure.png)

Para obter informações de como implementar as recomendações de segurança, confira [Gerenciando recomendações de segurança na Central de Segurança do Azure](/azure/security-center/security-center-recommendations).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
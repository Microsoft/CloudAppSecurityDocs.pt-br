---
title: Conectar o Azure ao Cloud App Security
description: Este artigo fornece informações sobre como conectar o Azure ao Cloud App Security usando o conector de API para obter visibilidade e controle sobre o uso.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 28a2885be1bd98f9ef5b3905d6ed1dc50f64238f
ms.sourcegitcommit: 00599ac6c64a4c62ed9ebdda3edb58f90f92c24d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912037"
---
# <a name="connect-azure-to-microsoft-cloud-app-security"></a>Conectar o Azure ao Microsoft Cloud App Security

*Aplica-se ao: Microsoft Cloud App Security*

Este artigo fornece instruções para conectar o Microsoft Cloud App Security à sua conta existente do Azure usando a API do conector de aplicativos. Essa conexão fornece visibilidade e controle sobre o uso do Azure. Para obter informações sobre como Cloud App Security protege o Azure, consulte [proteger o Azure](protect-azure.md).

## <a name="how-to-connect-azure-to-cloud-app-security"></a>Como conectar o Azure ao Cloud App Security

> [!NOTE]
>
> - O usuário precisa ser administrador global no Azure AD para conectar o Azure ao Microsoft Cloud App Security.
> - O Cloud App Security exibe as atividades de **todas** as assinaturas.
> - Atualmente, o Cloud App Security monitora apenas as atividades ARM.

1. Na página **Aplicativos conectados**, clique no botão de mais e selecione **Microsoft Azure**.

    ![Conectar o Azure](media/connect-azure-menu.png)

2. No pop-up do Azure, clique em **Conectar o Microsoft Azure**.

    ![Conectar o Azure](media/connect-azure.png)

> [!NOTE]
> Após conectar o Azure, o pull dos dados será efetuado. A partir desse momento, você vê os dados.

Se você tiver problemas para conectar o aplicativo, consulte [Solucionando problemas de conectores de aplicativos](troubleshooting-api-connectors-using-error-messages.md).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]

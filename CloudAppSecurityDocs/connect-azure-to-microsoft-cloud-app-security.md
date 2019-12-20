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
ms.openlocfilehash: 20f8c2194631f09fc54eab997596d97e10c338c9
ms.sourcegitcommit: db5ec79d219dd6674939c872ace7cd2ca80860a4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75189699"
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

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]

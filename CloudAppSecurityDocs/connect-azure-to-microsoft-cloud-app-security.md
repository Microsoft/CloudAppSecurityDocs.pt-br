---
title: Conectar o Azure ao Cloud App Security
description: Este artigo fornece informações sobre como conectar o Azure ao Cloud App Security usando o conector de API para obter visibilidade e controle sobre o uso.
ms.date: 12/27/2020
ms.topic: how-to
ms.openlocfilehash: eb95630ac08763fa6b87a6fab410ec3629010ec8
ms.sourcegitcommit: 40d17309b8729eb914ea91ba5fa7017340231488
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/29/2020
ms.locfileid: "97808905"
---
# <a name="connect-azure-to-microsoft-cloud-app-security"></a>Conectar o Azure ao Microsoft Cloud App Security

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Este artigo fornece instruções para conectar o Microsoft Cloud App Security à sua conta existente do Azure usando a API do conector de aplicativos. Essa conexão fornece visibilidade e controle sobre o uso do Azure. Para obter informações sobre como Cloud App Security protege o Azure, consulte [proteger o Azure](protect-azure.md).

## <a name="how-to-connect-azure-to-cloud-app-security"></a>Como conectar o Azure ao Cloud App Security

> [!NOTE]
>
> - O usuário deve ser um administrador global ou de segurança no Azure AD para conectar o Azure ao Microsoft Cloud App Security.
> - O Cloud App Security exibe as atividades de **todas** as assinaturas.
> - As informações de conta de usuário são preenchidas na Cloud App Security à medida que os usuários executam atividades no Azure.
> - Atualmente, o Cloud App Security monitora apenas as atividades ARM.

1. Na página **aplicativos conectados** , clique no botão de adição e selecione **Microsoft Azure**.

    ![item de menu conectar do Azure](media/connect-azure-menu.png)

2. No pop-up do Azure, clique em **Conectar o Microsoft Azure**.

    ![Conectar o Azure](media/connect-azure.png)

> [!NOTE]
> Após conectar o Azure, o pull dos dados será efetuado. A partir desse momento, você vê os dados.

Se você tiver problemas para conectar o aplicativo, consulte [Solucionando problemas de conectores de aplicativos](troubleshooting-api-connectors-using-error-messages.md).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]

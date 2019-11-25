---
title: Bloqueando aplicativos descobertos – Cloud App Security | Microsoft Docs
description: Este artigo descreve o procedimento para exportar scripts de bloqueio para aplicativos descobertos.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 11/06/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 8464851432d8fce81baa624738c6f73da1d68413
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2019
ms.locfileid: "74461361"
---
# <a name="govern-discovered-apps"></a>Controlar aplicativos descobertos

*Aplica-se ao: Microsoft Cloud App Security*

After you've reviewed the list of discovered apps in your environment, you can secure your environment by approving safe apps (**Sanctioned**) or prohibiting unwanted apps (**Unsanctioned**) in the following ways.

## <a name="BKMK_SanctionApp"></a> Sanção/cancelamento de sanção de um aplicativo

Você pode cancelar a sanção um aplicativo de risco específico clicando nos três pontos no final da linha. Em seguida, selecione **Cancelar sanção**. O cancelamento de sanção de um aplicativo não bloqueia o uso, mas permite monitorar seu uso mais facilmente com os filtros do Cloud Discovery. Em seguida, você pode notificar os usuários do aplicativo não sancionado e sugerir um aplicativo alternativo seguro para seu uso.

![Marcar como não sancionado](./media/tag-as-unsanctioned.png)

Se você tiver uma lista de aplicativos que deseja sancionar ou cancelar a sanção, use a caixa de seleção para marcar os aplicativos que deseja gerenciar e, em seguida, selecione a ação.

Para consultar uma lista de aplicativos não sancionados, você pode [gerar um script de bloco usando as APIs do Cloud App Security](https://us.portal.cloudappsecurity.com/api-docs/#generate-block-script).

> [!NOTE]
> If your tenant uses Zscaler NSS or iboss, any app you mark as unsanctioned is automatically blocked by Cloud App Security, and the following sections regarding creating blocking scripts are unnecessary. For more information, see [Integrating with Zscaler](zscaler-integration.md) and [Integrate Cloud App Security with iboss](iboss-integration.md) respectively.

## <a name="export-a-block-script-to-govern-discovered-apps"></a>Exporte um script de bloqueio para controlar aplicativos descobertos

O Cloud App Security permite que você bloqueie o acesso a aplicativos não sancionados usando os dispositivos de segurança locais existentes. Gere um script de bloqueio dedicado e importe-o para seu dispositivo. Essa solução não exige o redirecionamento de todo o tráfego da Web da organização para um proxy.

1. No painel de Descoberta de nuvem, marque quaisquer aplicativos que você deseja bloquear como **Não sancionados**.

    ![Marcar como não sancionado](./media/tag-as-unsanctioned.png)

2. Na barra de título, clique nos três pontos e selecione **Gerar script de bloqueio...** .

    ![Gerar script de bloqueio](./media/generate-block-script.png)

3. Em **Gerar script de bloqueio**, selecione o dispositivo para o qual deseja gerar o script de bloqueio.

    ![Pop-up de Gerar script de bloqueio](./media/generate-block-script-popup.png)

4. Em seguida, clique no botão Gerar script para criar um script de bloqueio para todos os aplicativos não sancionados. Por padrão, o arquivo será nomeado com a data em que foi exportado e o tipo de dispositivo selecionado. *2017-02-19_CAS_Fortigate_block_script.txt* é um nome de arquivo de exemplo

   ![Botão Generate block script (Gerar script de bloqueio)](./media/generate-block-script-button.png)

5. Importe o arquivo criado para seu dispositivo.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]

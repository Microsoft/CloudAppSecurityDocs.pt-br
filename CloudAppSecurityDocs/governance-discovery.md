---
title: Bloqueando aplicativos descobertos-Cloud App Security
description: Este artigo descreve o procedimento para exportar scripts de bloqueio para aplicativos descobertos.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/12/2019
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: dc6eb398526c416af306881d9fd17c71992b8c86
ms.sourcegitcommit: 5367d8fdf99d61719a395728f2ef4b014604e3bc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/08/2020
ms.locfileid: "94370930"
---
# <a name="govern-discovered-apps"></a>Controlar aplicativos descobertos

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Depois de examinar a lista de aplicativos descobertos em seu ambiente, você pode proteger seu ambiente aprovando aplicativos seguros ( **aprovados** ) ou proibindo aplicativos indesejados (não **aprovados** ) das seguintes maneiras.

## <a name="sanctioningunsanctioning-an-app"></a><a name="BKMK_SanctionApp"></a> Aprovar/desaprovar um aplicativo

Você pode cancelar a sanção um aplicativo de risco específico clicando nos três pontos no final da linha. Em seguida, selecione **Cancelar sanção**. O cancelamento de sanção de um aplicativo não bloqueia o uso, mas permite monitorar seu uso mais facilmente com os filtros do Cloud Discovery. Em seguida, você pode notificar os usuários do aplicativo não sancionado e sugerir um aplicativo alternativo seguro para seu uso.

![Marcar como não sancionado](media/tag-as-unsanctioned.png)

Se você tiver uma lista de aplicativos que deseja sancionar ou cancelar a sanção, use a caixa de seleção para marcar os aplicativos que deseja gerenciar e, em seguida, selecione a ação.

Para consultar uma lista de aplicativos não sancionados, você pode [gerar um script de bloco usando as APIs do Cloud App Security](api-discovery-script.md).

> [!NOTE]
> Se seu locatário usar o Microsoft defender para EndPoint, Zscaler NSS ou iboss, qualquer aplicativo marcado como não aprovado será bloqueado automaticamente pelo Cloud App Security, e as seções a seguir sobre a criação de scripts de bloqueio serão desnecessárias. Para obter mais informações, consulte [integrar com o Microsoft defender para ponto de extremidade](mde-integration.md), [integrar com o Zscaler](zscaler-integration.md)e [integrar com o iboss](iboss-integration.md) , respectivamente.

## <a name="export-a-block-script-to-govern-discovered-apps"></a>Exporte um script de bloqueio para controlar aplicativos descobertos

O Cloud App Security permite que você bloqueie o acesso a aplicativos não sancionados usando os dispositivos de segurança locais existentes. Gere um script de bloqueio dedicado e importe-o para seu dispositivo. Essa solução não exige o redirecionamento de todo o tráfego da Web da organização para um proxy.

1. No painel do Cloud Discovery, marque quaisquer aplicativos que deseja bloquear como **Não sancionado**.

    ![Marcar como não sancionado](media/tag-as-unsanctioned.png)

2. Na barra de título, clique nos três pontos e selecione **Gerar script de bloqueio...**.

    ![Gerar script de bloco](media/generate-block-script.png)

3. Em **Gerar script de bloqueio** , selecione o dispositivo para o qual deseja gerar o script de bloqueio.

    ![Pop-up de Gerar script de bloqueio](media/generate-block-script-pop-up.png)

4. Em seguida, clique no botão Gerar script para criar um script de bloqueio para todos os aplicativos não sancionados. Por padrão, o arquivo será nomeado com a data em que foi exportado e o tipo de dispositivo selecionado. *2017-02-19_CAS_Fortigate_block_script.txt* é um nome de arquivo de exemplo

   ![Botão Gerar script de bloqueio](media/generate-block-script-button.png)

5. Importe o arquivo criado para seu dispositivo.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]

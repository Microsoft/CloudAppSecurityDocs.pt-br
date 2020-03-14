---
title: Bloqueando aplicativos descobertos-Cloud App Security | Microsoft Docs
description: Este artigo descreve o procedimento para exportar scripts de bloco para aplicativos descobertos.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/12/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: bc95cb2272d996752c60c49c7f7402550325b208
ms.sourcegitcommit: 4f3883a9e85d0aaf2802b10433b221c3f1838d88
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79285520"
---
# <a name="govern-discovered-apps"></a>Controlar aplicativos descobertos

*Aplica-se a: Microsoft Cloud App Security*

Depois de examinar a lista de aplicativos descobertos em seu ambiente, você pode proteger seu ambiente aprovando aplicativos seguros (**aprovados**) ou proibindo aplicativos indesejados (não**aprovados**) das seguintes maneiras.

## <a name="BKMK_SanctionApp"></a>Aprovar/desaprovar um aplicativo

Você pode desaprovar um aplicativo arriscado específico clicando nos três pontos no final da linha. Em seguida, selecione não **aprovar**. A dessanções de um aplicativo não bloqueia o uso, mas permite que você monitore com mais facilidade seu uso com os filtros de Cloud Discovery. Em seguida, você pode notificar os usuários sobre o aplicativo não aprovado e sugerir um aplicativo de segurança alternativo para seu uso.

![Marcar como não aprovado](media/tag-as-unsanctioned.png)

Se você tiver uma lista de aplicativos que deseja aprovar ou não aprovar, use a caixa de seleção para selecionar os aplicativos que deseja gerenciar e, em seguida, selecione a ação.

Para consultar uma lista de aplicativos não aprovados, você pode [gerar um script de bloco usando as APIs de Cloud app Security](https://us.portal.cloudappsecurity.com/api-docs/#generate-block-script).

> [!NOTE]
> Se seu locatário usa a ATP (proteção avançada contra ameaças) do Microsoft defender, o Zscaler NSS ou o iboss, qualquer aplicativo marcado como não aprovado é bloqueado automaticamente pelo Cloud App Security, e as seções a seguir sobre a criação de scripts de bloqueio são desnecessárias. Para obter mais informações, consulte [integrar com o Microsoft defender ATP](wdatp-integration.md), [integrar com o Zscaler](zscaler-integration.md)e [integrar com o iboss](iboss-integration.md) , respectivamente.

## <a name="export-a-block-script-to-govern-discovered-apps"></a>Exportar um script de bloco para controlar aplicativos descobertos

Cloud App Security permite bloquear o acesso a aplicativos não aprovados usando seus dispositivos de segurança local existentes. Você pode gerar um script de bloco dedicado e importá-lo para seu dispositivo. Essa solução não requer o redirecionamento de todo o tráfego da Web da organização para um proxy.

1. No painel Cloud Discovery, marque os aplicativos que você deseja bloquear como não **aprovados**.

    ![Marcar como não aprovado](media/tag-as-unsanctioned.png)

2. Na barra de título, clique nos três pontos e selecione **gerar script de bloco...** .

    ![Gerar script de bloco](media/generate-block-script.png)

3. Em **gerar script de bloco**, selecione o dispositivo para o qual você deseja gerar o script de bloco.

    ![Gerar pop-up de script de bloco](media/generate-block-script-popup.png)

4. Em seguida, clique no botão gerar script para criar um script de bloco para todos os seus aplicativos não aprovados. Por padrão, o arquivo será nomeado com a data em que foi exportado e o tipo de dispositivo selecionado. *2017-02-19_CAS_Fortigate_block_script. txt* seria um nome de arquivo de exemplo

   ![Botão gerar script de bloco](media/generate-block-script-button.png)

5. Importe o arquivo criado para seu dispositivo.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]

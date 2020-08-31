---
title: Enriquecer dados do Cloud App Security Discovery com nomes de usuário do Azure AD
description: Este artigo fornece informações sobre como aprimorar os dados do Cloud App Security Discovery com nomes de usuário do Azure AD.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/10/2018
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 0f7ce34e19fa1b4a62b8d3786eae6898a19a428f
ms.sourcegitcommit: c174a7ada5c6a14f0fea9870672898c54e5e3b52
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89149594"
---
# <a name="cloud-discovery-enrichment"></a>Aprimoramento do Cloud Discovery

*Aplica-se a: Microsoft Cloud App Security*

Os dados do Cloud Discovery agora podem ser aprimorados com os dados de nome de usuário do Azure Active Directory. Quando você habilita esse recurso, o nome de usuário recebido nos logs de tráfego de descoberta é correspondido e substituído pelo nome de usuário do Azure AD. O aprimoramento do Cloud Discovery habilita os seguintes recursos:

- Você pode investigar o uso de TI sombra pelo usuário do Azure Active Directory.
- Você pode correlacionar o uso do aplicativo de nuvem Descoberto com as atividades coletadas pela API.
- Então, você pode criar logs personalizados com base nos grupos de usuários do Azure AD. Por exemplo, um relatório de TI sombra para um departamento de Marketing específico.

## <a name="prerequisites"></a>Pré-requisitos

- A fonte de dados deve fornecer informações de nome de usuário
- Conector de aplicativo Microsoft 365 conectado

## <a name="enabling-user-data-enrichment"></a>Permitindo o aprimoramento de dados de usuário

1. Na engrenagem configurações, selecione **configurações de Cloud Discovery**.

2. Na guia **Aprimoramento do usuário**, selecione **Aprimorar os identificadores descobertos do usuário com os nomes de usuários do Azure Active Directory**. Essa opção permite que o Cloud App Security use dados do Azure Active Directory para aprimorar os nomes de usuário padrão.

3. Clique em **Save** (Salvar).

![Aprimorar o Cloud App Security Discovery com nomes de usuário do Azure AD](media/discovery-enrichment.png)

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]

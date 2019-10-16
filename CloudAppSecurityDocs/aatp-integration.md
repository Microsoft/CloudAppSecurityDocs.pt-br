---
title: Integre a proteção avançada contra ameaças do Azure com o Cloud App Security
description: Este artigo fornece informações sobre como aproveitar as ideias de proteção avançada contra ameaças do Azure no Cloud App Security para detecção de riscos híbridos.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 6/27/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 63e82b47-bb08-4614-af55-f85d04edfc5a
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: cd52e120f20e6b8ebaeacdd5a30a7c98d883fec9
ms.sourcegitcommit: c342abeec95359ddabdabcc3a081a0f91d52407c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72334878"
---
# <a name="azure-advanced-threat-protection-integration"></a>Integração da proteção avançada contra ameaças do Azure

*Aplica-se ao: Microsoft Cloud App Security*

O Microsoft Cloud App Security integra-se com o Azure ATP (proteção avançada contra ameaças do Azure) para fornecer UEBA (análise comportamental de entidade de usuário) em um ambiente híbrido – tanto no aplicativo de nuvem quanto no local, para obter mais informações, consulte [tutorial: investigar arriscado usuários](tutorial-ueba.md) para obter mais informações sobre o aprendizado de máquina e análise comportamental fornecidos pelo Azure ATP, consulte [o que é o Azure ATP?](https://docs.microsoft.com/azure-advanced-threat-protection/what-is-atp).

## <a name="prerequisites"></a>Pré-requisitos

Para fazer uma investigação completa em um ambiente híbrido, é necessário:

- Uma licença válida do ATP do Azure vinculada à instância do Azure Active Directory
- Você deve ser um administrador global para habilitar a integração entre o Azure ATP e o Microsoft Cloud App Security 
- Se não tiver o Azure ATP, experimente-o agora


>[!NOTE]
>Se você não tiver uma assinatura para Microsoft Cloud App Security, ainda poderá usar o portal de Cloud App Security para obter informações do Azure ATP.


## <a name="enable-azure-advanced-threat-protection"></a>Habilitar a proteção avançada contra ameaças do Azure

Para habilitar a integração do Cloud App Security com o Azure ATP:

1. Em Cloud App Security, na engrenagem configurações, selecione **configurações**.
    
   ![Menu configurações](./media/azip-system-settings.png)

1. Em **proteção contra ameaças**, selecione **Azure ATP**.
   
    ![habilitar a proteção avançada contra ameaças do Azure](./media/aatp-integration.png)

3. Marque a caixa de seleção para **conectar dados do Azure ATP, incluindo alertas e atividades com Cloud app Security**.


> [!NOTE]
> Pode levar até 12 horas até que a integração entre em vigor.
 
Depois de habilitar a integração da proteção avançada contra ameaças do Azure, você poderá ver as atividades locais para todos os usuários em sua organização. Você também obterá informações avançadas sobre seus usuários que combinam alertas e atividades suspeitas em seus ambientes de nuvem e locais.



## <a name="next-steps"></a>Próximas etapas 
[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)   

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/)  
  

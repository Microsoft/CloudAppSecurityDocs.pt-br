---
title: Integrar o Azure Advanced Threat Protection ao Cloud App Security
description: Este artigo fornece informações sobre como aproveitar os insights do Azure Advanced Threat Protection no Cloud App Security para detecção de riscos híbrido.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: rkarlin
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
ms.openlocfilehash: 99c866a8b2571c9572e042572d0f5160d0ae56e5
ms.sourcegitcommit: 3938edadc5f89f87cdeba607476cf3983b2413e8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67411934"
---
# <a name="azure-advanced-threat-protection-integration"></a>Integração da proteção avançada contra ameaças do Azure

*Aplica-se a: Microsoft Cloud App Security*

Microsoft Cloud App Security se integra com o Azure proteção avançada contra ameaças (ATP do Azure) para fornecer análises comportamentais de entidades de usuário (UEBA) em um ambiente híbrido – aplicativo de nuvem e locais, para obter mais informações, consulte [Tutorial: Investigar usuários arriscados]() para obter mais informações sobre o aprendizado de máquina e análise comportamental fornecido pelo Azure ATP, consulte [o que é o Azure ATP?](https://docs.microsoft.com/azure-advanced-threat-protection/what-is-atp).

## <a name="prerequisites"></a>Pré-requisitos

Para fazer uma investigação completa em um ambiente híbrido, é necessário:

- Uma licença válida do ATP do Azure vinculada à instância do Azure Active Directory
- Você deve ser um administrador global para habilitar a integração entre o Azure ATP e o Microsoft Cloud App Security 
- Se não tiver o Azure ATP, experimente agora


>[!NOTE]
>Se você não tiver uma assinatura do Microsoft Cloud App Security, você ainda poderá usar o portal do Cloud App Security para obter informações do Azure ATP.


## <a name="enable-azure-advanced-threat-protection"></a>Habilitar a proteção avançada de ameaças do Azure

Para habilitar o Cloud App Security para integrar com o Azure ATP:

1. No Cloud App Security, sob a engrenagem de configurações, selecione **configurações**.
    
   ![Menu de configurações](./media/azip-system-settings.png)

1. Sob **proteção contra ameaças**, selecione **do Azure ATP**.
   
    ![Habilitar a proteção avançada de ameaças do azure](./media/aatp-integration.png)

3. Selecione a caixa de seleção **dados de conectar o Azure ATP, incluindo alertas e atividades com o Cloud App Security**.


> [!NOTE]
> Pode levar até 12 horas até que a integração entrará em vigor.
 
Depois de habilitar a integração do Azure Advanced Threat Protection, você poderá ver as atividades de locais para todos os usuários em sua organização. Você também será obter avançados insights sobre os usuários que combinam alertas e atividades suspeitas em seus ambientes de nuvem e locais.



## <a name="next-steps"></a>Próximas etapas 
[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)   

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/)  
  

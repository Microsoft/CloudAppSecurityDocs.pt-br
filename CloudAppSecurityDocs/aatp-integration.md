---
title: Integrar o Azure Advanced Threat Protection ao Cloud App Security
description: Este artigo fornece informações sobre como aproveitar os insights do Azure Advanced Threat Protection no Cloud App Security para detecção de riscos híbrido.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: rkarlin
ms.date: 6/17/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 63e82b47-bb08-4614-af55-f85d04edfc5a
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 641151ff3db196e38786f970507f2a8dcf026ca6
ms.sourcegitcommit: 917d8cf85ac0b58a3b1788067c2ff92101eb3ccf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2019
ms.locfileid: "67237106"
---
# <a name="azure-advanced-threat-protection-integration"></a>Integração da proteção avançada contra ameaças do Azure

*Aplica-se a: Microsoft Cloud App Security*

Microsoft Cloud App Security integra-se com o Azure proteção avançada contra ameaças (ATP do Azure) para fornecer análises comportamentais de entidades de usuário (UEBA) em um ambiente híbrido - aplicativo de nuvem e locais. Para obter mais informações sobre o aprendizado de máquina e análise comportamental fornecido pelo Azure ATP, consulte [o que é o Azure ATP?](https://docs.microsoft.com/azure-advanced-threat-protection/what-is-atp).

Integrando com o Azure ATP, seu portal do Cloud App Security fornece alertas e informações sobre:
- O Microsoft Cloud App Security, que identifica ataques em uma sessão de nuvem, abrangendo produtos da Microsoft e aplicativos de terceiros
- Azure proteção avançada contra ameaças, que usa análise comportamental e aprendizado de máquina para identificar ataques entre sua rede local
- O Azure Active Directory Identity Protection, que detecta e impede proativamente os riscos de usuário e de entrada para identidades na nuvem


## <a name="prerequisites"></a>Pré-requisitos

Para fazer uma investigação completa em um ambiente híbrido, é necessário:

- Uma licença válida do Microsoft Cloud App Security
- Uma licença válida do ATP do Azure vinculada à instância do Azure Active Directory

>[!NOTE]
>Mesmo que não tenha uma assinatura do ATP do Azure, você ainda poderá usar o portal do Cloud App Security para investigar usuários, mas não receberá informações do ambiente local.


## <a name="enable-azure-advanced-threat-protection"></a>Habilitar a proteção avançada de ameaças do Azure

Tudo o que você precisa fazer para integrar o Azure Advanced Threat Protection ao Cloud App Security é clique em uma caixa de seleção. Habilitando a integração, permitir que Cloud App Security acesse e analise as atividades suspeitas de locais vistas pelo Azure ATP, coloque-as em que o Cloud App Security e fornecer uma visão completa do seu ambiente híbrido e todas as atividades arriscadas executada pelos usuários.

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
  

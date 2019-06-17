---
title: Integrar o Azure Advanced Threat Protection ao Cloud App Security
description: Este artigo fornece informações sobre como aproveitar os insights do Azure Advanced Threat Protection no Cloud App Security para detecção de riscos híbrido.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: rkarlin
ms.date: 6/21/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 63e82b47-bb08-4614-af55-f85d04edfc5a
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 4ca98ab0cb5655d774c6ee4e7f917a6e9456092a
ms.sourcegitcommit: a25543c14c35f159dd06f7c0c89d6bc0e36a0413
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67031070"
---
# <a name="azure-information-protection-integration"></a>Integração da Proteção de Informações do Azure

*Aplica-se a: Microsoft Cloud App Security*

Microsoft Cloud App Security integra-se com o Azure proteção avançada contra ameaças (ATP do Azure) para fornecer análises comportamentais de entidades de usuário (UEBA) em um ambiente híbrido - aplicativo de nuvem e locais. Para obter mais informações sobre o aprendizado de máquina e análise comportamental fornecido pelo Azure ATP, consulte [o que é o Azure ATP?](https://docs.microsoft.com/azure-advanced-threat-protection/what-is-atp).

Integrando com o Azure ATP, seu portal do Cloud App Security fornece alertas e informações sobre:
- Microsoft Cloud App Security, que identifica a ataques de dentro de uma sessão de nuvem, que abrange não apenas produtos da Microsoft, mas também os aplicativos de terceiros
- Azure proteção avançada contra ameaças, que usa análise comportamental e aprendizado de máquina para identificar ataques entre sua rede local
- Azure Active Directory Identity Protection, que detecta e impede proativamente os riscos de usuário e entrar para identidades na nuvem


## <a name="prerequisites"></a>Pré-requisitos

Investigação de usuário completa em um ambiente híbrido, você deve ter:

- Uma licença válida do Microsoft Cloud App Security
- Uma licença válida para o Azure ATP conectado à instância do Active Directory

>[!NOTE]
>Se você não tiver uma assinatura do Azure ATP, você ainda poderá usar o portal do Cloud App Security para investigar os usuários, mas você não receberá insights do seu ambiente local.


## <a name="enable-azure-advanced-threat-protection"></a>Habilitar a proteção avançada de ameaças do Azure

Tudo o que você precisa fazer para integrar o Azure Advanced Threat Protection ao Cloud App Security é clique em uma caixa de seleção. Habilitando a integração, permitir que Cloud App Security acesse e analise as atividades suspeitas de locais vistas pelo Azure ATP, coloque-as em que o Cloud App Security e fornecer uma visão completa do seu ambiente híbrido e todas as atividades arriscadas executada pelos usuários.

Para habilitar o Cloud App Security para integrar com o Azure ATP:

1. No Cloud App Security, sob a engrenagem de configurações, selecione **configurações**.
    
   ![Menu de configurações](./media/azip-system-settings.png)

1. Sob **proteção contra ameaças**, selecione **do Azure ATP**.
   
    ![Habilitar a proteção avançada de ameaças do azure](./media/aatp-integration.png)

3. Selecione a caixa de seleção **dados de conectar o Azure ATP, incluindo alertas e atividades com o Cloud App Security**.
 
Depois de habilitar a integração do Azure Advanced Threat Protection, você poderá ver as atividades de locais para todos os usuários em sua organização. Você também será obter avançados insights sobre os usuários que combinam alertas e atividades suspeitas em seus ambientes de nuvem e locais.



## <a name="next-steps"></a>Próximas etapas 
[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)   

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/)  
  

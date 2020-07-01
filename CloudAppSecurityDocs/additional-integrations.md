---
title: Integração adicional com o Cloud App Security
description: Este artigo fornece informações sobre como integrar soluções de terceiros com o Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 06/28/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: ca393149f9a0ae9a87ec087c6e94baba63ed9c91
ms.sourcegitcommit: 7811a0d33e1756782222f20df02acae2f3ea4afe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85795831"
---
# <a name="additional-integrations-with-external-solutions"></a>Integrações adicionais com soluções externas

*Aplica-se a: Microsoft Cloud App Security*

Você pode integrar Microsoft Cloud App Security com seus outros investimentos em segurança para aproveitar e aprimorar um ecossistema integrado de proteção. Por exemplo, você pode integrar com soluções externas de gerenciamento de dispositivo móvel, soluções de UEBA e feeds de inteligência contra ameaças externas.

A plataforma robusta do Cloud App Security permite que você se integre a uma ampla variedade de soluções de segurança externas, incluindo:

- **Feeds de TI (inteligência contra ameaças) (Traga seu próprio it)**  
    Você pode usar a [API do intervalo de endereços ip](api-data-enrichment.md) Cloud app Security para adicionar novos intervalos de endereços IP arriscados identificados por soluções de ti de terceiros. Uma vez definidas, os intervalos de endereços IP permitem marcar, categorizar e personalizar a maneira como os logs e alertas são exibidos e investigados.

- **Soluções de MDM (gerenciamento de dispositivo móvel)/MTD (defesa contra ameaças móveis)**  
    Cloud App Security fornece controles de sessão granulares em tempo real. Um fator importante na avaliação e proteção de sessões é o dispositivo usado pelo usuário, o que ajuda a criar uma identidade abrangente. O status de gerenciamento de um dispositivo pode ser identificado diretamente por meio do status de gerenciamento de dispositivo no [Azure Active Directory (Azure AD)](/azure/active-directory/conditional-access/overview), [Microsoft Intune](/intune/mobile-threat-defense)ou mais genericamente por meio da análise de certificados de cliente que permite a integração com uma variedade de soluções de MDM e MTD de terceiros.

    Cloud App Security pode aproveitar sinais de soluções externas de MDM e MTD para aplicar controles de sessão com base no [status de gerenciamento](proxy-intro-aad.md#managed-device-identification)de um dispositivo.

- **Soluções de UEBA**  
    Você pode usar várias soluções UEBA para atender a diferentes cargas de trabalho e cenários, em que cada solução UEBA depende de várias fontes de dados para identificar o comportamento suspeito e anormal do usuário. As soluções de UEBA externas podem ser integradas com o ecossistema de segurança da Microsoft por meio de Azure AD Identity Protection.

    Uma vez integrados, as políticas podem ser usadas para identificar usuários arriscados, aplicar controles adaptáveis e corrigir automaticamente os usuários arriscados definindo o nível de risco do usuário como alto. Depois que um usuário é definido como alto, as ações de política relevantes são impostas, como redefinir a senha de um usuário, exigir autenticação MFA ou forçar um usuário a usar um dispositivo gerenciado.

    Cloud App Security permite que as equipes de segurança confirmem automaticamente ou manualmente um usuário como comprometido, para garantir a rápida correção de usuários comprometidos.

    Para obter mais informações, consulte [como o AD do Azure usa meus comentários de risco](/azure/active-directory/identity-protection/howto-identity-protection-risk-feedback#how-does-azure-ad-use-my-risk-feedback) e [ações de governança](accounts.md#governance-actions).

[!INCLUDE [Open support ticket](includes/support.md)]

---
title: Visão geral do cenário de proteção contra ameaças – Cloud App Security | Microsoft Docs
description: Este tópico descreve o cenário para proteger sua organização contra ameaças em seu ambiente de nuvem.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/14/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 36cab094e0bd971ef9d36b0c9d7d3528a686e3da
ms.sourcegitcommit: 7c93b6f93d2699d466b172590710ed01697bbdad
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74720483"
---
# <a name="protecting-your-organization-from-ransomware"></a>Protegendo sua organização contra ransonware

*Aplica-se ao: Microsoft Cloud App Security*

No último grande ataque de ransomware, WannaCry atingiu o mundo cibernético com grande força, infectando uma estimativa de 200 mil computadores em 150 países. Com o aumento de ataques de ransomware nos últimos anos, uma média de 25 mil ataques por mês em 2015 e 56 mil em 2016, ser proativo em relação à garantia de que sua rede não esteja em risco está se tornando uma necessidade de segurança cibernética. Este artigo explica como você pode usar o Cloud App Security para monitorar sua nuvem, detectar e atenuar ameaças e aplicar as melhores práticas para proteger seu ambiente contra ransomware.

## <a name="what-is-ransomware"></a>O que é o ransomware?

O ransomware é um ataque cibernéticos em que o invasor envia um arquivo que pode impedir o acesso a seu computador e criptografar seus próprios arquivos. Os arquivos, às vezes, são mantidos para resgate e não são descriptografados até que você pague o invasor para recuperar o acesso ao seu computador, aos arquivos ou aos aplicativos LOB críticos. Ataques ransomware podem afetar qualquer computador, casa, escritório, rede ou servidor. Na verdade, como grandes organizações são compostas de vários usuários que inadvertidamente podem abrir um arquivo que libera o ransomware em sua rede, as organizações são sob um risco ainda maior de serem forçadas a pagar o invasor para interromper o ransomware e restaurar o acesso aos arquivos ou computadores.

>[!NOTE]
> Esse caso de uso aplica-se ao Office 365, G Suite, Box e Dropbox.

## <a name="the-threat"></a>A AMEAÇA

Um usuário em sua organização é o alvo de um ataque ransomware. O usuário pode abrir inadvertidamente um email infectado e executar o ransomware, que infecta todos os seus arquivos, incluindo os arquivos sincronizados na nuvem.

## <a name="the-solution"></a>A SOLUÇÃO

Detecte potencial ransomware em seu ambiente de nuvem ao criar uma política para atualizar quando atividade suspeita é detectada e configure ações automatizadas para impedir que arquivos ransomware sejam salvos em sua nuvem.

## <a name="out-of-the-box-protection"></a>Proteção pronta para uso

[Conecte](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md), pelo menos, um aplicativo na nuvem (Office 365, G Suite, Box e Dropbox) ao Cloud App Security.

1. Por padrão, o Cloud App Security examina sua rede para estabelecer uma linha de base, na qual aprende padrões sobre o que seus usuários costumam fazer na nuvem, quando o fazem e o que fazem normalmente.

2. As [políticas de detecção de ameaças](anomaly-detection-policy.md) automatizadas do Cloud App Security iniciam a execução em segundo plano no momento em que você se conecta. Uma dessas políticas procura atividade de ransomware para garantir uma cobertura abrangente contra ataques de ransomware sofisticados. Usando nossa experiência com pesquisa de segurança para identificar padrões de comportamentos que refletem a atividade de ransomware, o Cloud App Security garante a proteção holística e robusta. Por exemplo, se o Cloud App Security identificar uma taxa alta de uploads de arquivos ou atividades de exclusão de arquivo, isso poderá representar um processo de criptografia adverso. Esses dados são coletados nos logs recebidos de APIs conectadas e são combinados com padrões comportamentais aprendidos e inteligência contra ameaças, por exemplo, extensões de ransomware conhecidas.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]

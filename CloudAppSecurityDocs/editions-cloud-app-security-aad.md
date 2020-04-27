---
title: Diferenças de capacidade de descoberta do Cloud App Security e Azure AD
description: Esse artigo descreve as diferenças entre os recursos de descoberta no Microsoft Cloud App Security e no Azure AD.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 8/29/2019
ms.topic: overview
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 825a8532588cc479bcc37e5373bff23ccc841d8d
ms.sourcegitcommit: 0b929f7c8feed7dfb40d5294179fd5c6fc079614
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/21/2020
ms.locfileid: "74461026"
---
# <a name="what-are-the-differences-in-discovery-capabilities-for-azure-active-directory-and-microsoft-cloud-app-security"></a>Quais são as diferenças nos recursos de descoberta para Azure Active Directory e Microsoft Cloud App Security?

*Aplica-se a: Microsoft Cloud App Security*

Esse artigo descreve as diferenças entre os recursos de descoberta no Microsoft Cloud App Security e no Azure AD (Azure Active Directory).

Para obter mais informações sobre licenciamento, consulte a [folha de dados licenciamento do Microsoft Cloud App Security](https://aka.ms/mcaslicensing).

## <a name="microsoft-cloud-app-security"></a>Microsoft Cloud App Security

O Microsoft Cloud App Security é uma solução de SaaS cruzada abrangente que fornece visibilidade profunda, controles de dados fortes e proteção aprimorada contra ameaças aos seus aplicativos na nuvem. O Cloud Discovery é um dos recursos do Cloud App Security, o qual permite que você tenha visibilidade para a TI Sombra, descobrindo aplicativos de nuvem em uso.

## <a name="enhanced-cloud-app-discovery-in-azure-active-directory"></a>Cloud App Discovery aprimorado no Azure Active Directory

O Azure Active Directory Premium P1 inclui o [Cloud App Discovery do Azure Active Directory](https://aka.ms/caddocsnew) sem custo adicional. Esse recurso se baseia nos recursos do Cloud Discovery do Microsoft Cloud App Security, os quais fornecem uma visibilidade mais profunda do uso do aplicativo de nuvem em suas organizações. [Atualize para o Microsoft Cloud App Security](https://www.microsoft.com/cloud-platform/cloud-app-security) para receber o pacote completo de recursos do CASB (Cloud App Security Broker) oferecidos pelo Microsoft Cloud App Security.

### <a name="feature-comparison"></a>Comparação de recursos

A tabela a seguir mostra uma comparação entre os recursos de descoberta no Microsoft Cloud App Security e no Azure AD.

|Funcionalidade|Recurso|Microsoft Cloud App Security|Cloud App Discovery do Azure AD|
|----|----|----|----|
|Cloud Discovery|Aplicativos Descobertos|Mais de 16.000 aplicativos na nuvem|Mais de 16.000 aplicativos na nuvem|
||Implantação para a análise de descoberta|Upload manual e automático de log|Upload manual e automático de log|
||Anonimização de log para a privacidade do usuário|Sim|Sim|
||Acesso ao catálogo completo de aplicativos de nuvem|Sim|Sim|
||Avaliação de risco dos aplicativos na nuvem|Sim|Sim|
||Análise de uso de nuvem por aplicativo, usuário e endereço IP|Sim|Sim|
||Análises e relatórios contínuos|Sim|Sim|
||Detecção de anomalias para aplicativos descobertos|Sim||
|Proteção de Informações|Suporte de DLP (prevenção contra perda de dados)|DLP de SaaS cruzado e controle de compartilhamento de dados||
||Permissões de aplicativo e capacidade para revogar o acesso|Sim||
||Configuração de política e imposição|Sim||
||Integração à Proteção de Informações do Azure |Sim||
||Integração com soluções DLP de terceiros|Sim||
|Detecção de ameaças|Detecção de anomalias e análise comportamental|Para aplicativos SaaS cruzados||
||Correção manual e automática de alertas|Sim||
||Conector SIEM|Sim. Alertas e logs de atividade para aplicativos SaaS cruzados.||
||Integração ao Gráfico de Segurança Inteligente da Microsoft|Sim||
||Políticas de atividade|Sim||

## <a name="next-steps"></a>Próximas etapas

Saiba mais sobre as noções básicas em [Introdução ao Cloud App Security](getting-started-with-cloud-app-security.md).

[!INCLUDE [Open support ticket](includes/support.md)].

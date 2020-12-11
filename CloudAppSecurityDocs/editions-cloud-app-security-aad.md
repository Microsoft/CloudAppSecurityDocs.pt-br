---
title: Diferenças de capacidade de descoberta do Cloud App Security e Azure AD
description: Esse artigo descreve as diferenças entre os recursos de descoberta no Microsoft Cloud App Security e no Azure AD.
ms.date: 12/03/2020
ms.topic: overview
ms.openlocfilehash: c66173dc28d0e0f9d349327583afa30a328912db
ms.sourcegitcommit: 4177401f2f7948f230a6cb1f7af8ceeceb844fad
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96544693"
---
# <a name="what-are-the-differences-in-discovery-capabilities-for-azure-active-directory-and-microsoft-cloud-app-security"></a>Quais são as diferenças nos recursos de descoberta para Azure Active Directory e Microsoft Cloud App Security?

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Este artigo descreve as diferenças entre os recursos de descoberta do Microsoft Cloud App Security e do Azure AD (Azure Active Directory).

Para obter mais informações sobre licenciamento, consulte a [folha de dados licenciamento do Microsoft Cloud App Security](https://aka.ms/mcaslicensing).

## <a name="microsoft-cloud-app-security"></a>Microsoft Cloud App Security

O Microsoft Cloud App Security é uma solução entre SaaS completa que traz visibilidade profunda, controles de dados fortes e proteção contra ameaças aprimorada aos seus aplicativos de nuvem. O Cloud Discovery é um dos recursos do Cloud App Security, que permite que você ganhe visibilidade sobre TI Sombra descobrindo os aplicativos de nuvem em uso.

## <a name="enhanced-cloud-app-discovery-in-azure-active-directory"></a>Cloud App Discovery avançado no Azure Active Directory

O Azure Active Directory Premium P1 inclui o [Azure Active Directory Cloud App Discovery](./set-up-cloud-discovery.md) sem custo adicional. Esse recurso se baseia nas funcionalidades do Microsoft Cloud App Security Cloud Discovery que fornecem maior visibilidade do uso do aplicativo de nuvem em suas organizações. Escolha [Atualizar para o Microsoft Cloud App Security](https://www.microsoft.com/cloud-platform/cloud-app-security) para receber o pacote completo de funcionalidades CASB (Agente de Segurança de Aplicativo de Nuvem) oferecidas pelo Microsoft Cloud App Security.

### <a name="feature-comparison"></a>Comparação de recursos

A tabela a seguir é uma comparação dos recursos de descoberta no Microsoft Cloud App Security e no Azure AD.

|Funcionalidade|Recurso|Microsoft Cloud App Security|Cloud App Discovery do Azure AD|
|----|----|----|----|
|Cloud Discovery|Aplicativos Descobertos|Mais de 16.000 aplicativos na nuvem|Mais de 16.000 aplicativos na nuvem|
||Implantação para a análise de descoberta|Upload manual e automático de log|Upload de log manual e automático. [Saiba mais sobre como configurar o Cloud Discovery](set-up-cloud-discovery.md)|
||Anonimização de log para a privacidade do usuário|Sim|Sim|
||Acesso ao catálogo completo de aplicativos de nuvem|Sim|Sim|
||Avaliação de risco dos aplicativos na nuvem|Sim|Sim|
||Análise de uso de nuvem por aplicativo, usuário e endereço IP|Sim|Sim|
||Análises e relatórios contínuos|Sim|Sim|
||Detecção de anomalias para aplicativos descobertos|Sim||
|Proteção de Informações|Suporte de DLP (prevenção contra perda de dados)|DLP de SaaS cruzado e controle de compartilhamento de dados||
||Permissões de aplicativo e capacidade para revogar o acesso (aplicativos OAuth)|Sim||
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
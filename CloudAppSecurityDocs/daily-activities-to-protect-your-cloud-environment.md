---
title: Trabalhando com o painel do Cloud App Security
description: Este artigo fornece uma base em relação a como usar o painel do Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 05/06/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 367778c25f0a56dd0db8f6457b884b02d382da6c
ms.sourcegitcommit: e0c2a8fbdce9cc0fd0d6b85c92e112fd306ad950
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83203003"
---
# <a name="working-with-the-dashboard"></a>Trabalhar com o painel

*Aplica-se a: Microsoft Cloud App Security*

Este artigo descreve o que você deve fazer com o Cloud App Security diariamente.  Depois de ativar o Microsoft Cloud App Security, você precisará:

- Configurar fluxos de dados
- Sancione aplicativos que você deseja permitir que as pessoas usem
- Configure políticas para monitorar seu ambiente de nuvem.

Em seguida, você pode usar o Cloud App Security para controlar e proteger sua nuvem e gerenciar os riscos.

## <a name="check-the-dashboard"></a>Verificar o painel

![Painel do Cloud App Security](media/dashboard.png "painel Transações da Web")

O painel do Cloud App Security fornece uma visão geral das atividades e recursos, incluindo:

- Abrir alertas
- Violações de atividade
- Violações de conteúdo
- Um mapa de atividades que plota o local de origem da atividade do usuário
- Tendências de uso do aplicativo conectado no ambiente de nuvem
- Usuários principais por detecção de ameaças

É recomendável verificar o painel diariamente para ver quais novos alertas foram acionados. É um bom lugar para ficar atento à integridade do seu ambiente de nuvem. O painel ajuda você a ter uma noção do que está acontecendo.

## <a name="gradual-deployment-of-our-enhanced-dashboard"></a>Implantação gradual de nosso painel avançado

Como parte de nossos aprimoramentos contínuos no design do portal, o painel de Cloud App Security foi aprimorado com base em seus comentários. O painel oferece uma experiência de usuário aprimorada com conteúdo e dados atualizados.

As informações apresentadas no painel são uma visão geral de todas as informações mais importantes sobre sua organização. Cada cartão de informações fornece links para uma investigação mais profunda das informações apresentadas. Você também pode optar por exibir as informações do painel para um aplicativo específico usando o filtro fornecido.

![Painel do Cloud App Security](media/dashboard-enhanced.png)

### <a name="what-can-you-expect-to-see-in-the-dashboard"></a>O que você pode esperar ver no painel?

- **Abrir alertas**  
Mostra o número de alertas abertos, um grafo da distribuição de status de alerta e alertas recentes

- **Aplicativos Descobertos**  
Mostra o número de aplicativos descobertos, um grafo da distribuição de riscos do aplicativo e as principais categorias de aplicativo por tráfego.
- **Principais usuários a investigar**  
Mostra o número de usuários a investigar e os usuários com a prioridade de investigação mais alta.
- **Controle de Aplicativos de Acesso Condicional**  
Mostra o número de aplicativos protegidos por Controle de Aplicativos de Acesso Condicional, bem como o número de sessões e ações protegidas nos últimos 30 dias.
- **Status dos conectores de aplicativos**  
Mostra o número de instâncias do aplicativo conectado à API e seu status.
- **Arquivos infectados com malware**  
Mostra o número de arquivos infectados com malware.
- **Aplicativos OAuth do Office 365 com privilégios**  
Mostra o número de aplicativos OAuth raramente usados concedidos permissões altamente privilegiadas.
- **Configuração de segurança do Azure**  
Mostra o número e a gravidade das recomendações de configuração de segurança do Azure.
- **Configuração de segurança do AWS**  
Mostra o número e a gravidade das recomendações de configuração de segurança do AWS.
- **Alertas de DLP**  
Mostra um grafo de alertas DLP nos últimos 30 dias.
<!-- - **Activity map**  
Shows the global spread of activities performed by users over the last 30 days. -->

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Investigar alertas](investigate.md)

[!INCLUDE [Open support ticket](includes/support.md)]

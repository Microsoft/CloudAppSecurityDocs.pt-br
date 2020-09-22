---
title: API de Cloud Discovery de Cloud App Security
description: Este artigo fornece informações sobre como usar a API de Cloud Discovery.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: cdf70db4edd8b476a1915b9f54459a8d8b1a7bec
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90879762"
---
# <a name="cloud-discovery-api"></a>API de Cloud Discovery

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Cloud Discovery analisa os logs do sistema fornecidos pelo usuário para detectar aplicativos novos e desconhecidos em seu ambiente de nuvem. Use a API Cloud Discovery para automatizar o carregamento dos arquivos de log de descoberta da sua empresa. O processo de carregamento de arquivo consiste em 3 chamadas à API que devem ser chamadas consecutivamente.

Além disso, o Cloud App Security permite bloquear o acesso a aplicativos não aprovados usando seus dispositivos de segurança locais existentes. Use a chamada gerar script de bloco para obter um script de bloco dedicado e importá-lo para seu dispositivo.

O seguinte lista as solicitações com suporte:

- [Iniciar upload de arquivo](api-discovery-initiate.md)
- [Realizar upload de arquivo](api-discovery-perform.md)
- [Finalizar upload de arquivo](api-discovery-finalize.md)
- [Gerar script de bloco](api-discovery-script.md)

[!INCLUDE [Open support ticket](includes/support.md)]

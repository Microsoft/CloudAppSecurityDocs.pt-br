---
title: Solucionar problemas Controle de Aplicativos de Acesso Condicional
description: Este artigo fornece uma lista de possíveis problemas de Controle de Aplicativos de Acesso Condicional e fornece possíveis resoluções.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 6/30/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 6e43990b3ee3d3c5f33119643329381001707724
ms.sourcegitcommit: e8c40ab8901744314af19ede50e9017a92111721
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91205526"
---
# <a name="troubleshooting-conditional-access-app-control-issues"></a>Solucionando problemas de Controle de Aplicativos de Acesso Condicional

*Aplica-se a: Microsoft Cloud App Security*

Este artigo fornece uma lista de possíveis problemas de Controle de Aplicativos de Acesso Condicional e fornece possíveis resoluções.

## <a name="our-system-flagged-a-new-dns-entry-or-generated-a-certificate-for-casms-but-we-dont-use-microsoft-cloud-app-security"></a>Nosso sistema sinalizou uma nova entrada DNS ou gerou um certificado para *. cas.ms, mas não usamos Microsoft Cloud App Security

Isso é um comportamento normal e resulta de Cloud App Security proteger seu ambiente. Mesmo que sua organização não esteja usando Cloud App Security, quando alguém visita seu site ou serviço de um ambiente protegido pelo Controle de Aplicativos de Acesso Condicional do Cloud App Security, suas URLs são reescritas para proteger o acesso.

Por exemplo, quando um usuário da Contoso, uma empresa protegida por Cloud App Security, visita fabrikam.com, o usuário é automaticamente redirecionado para fabrikam.com.us.cas.ms. Como resultado, a equipe de phishing da Fabrikam verá uma nova entrada DNS e um certificado para fabrikam.com.us.cas.ms.

Neste exemplo, você pode ver que, embora a Fabrikam não use a Cloud App Security, porque a contoso faz, a entrada e o certificado DNS são criados.

**TBD [ALEX]:??? COMO RESOLVER? Entre em contato com a MS? Adicionar exceções????**

## <a name="i-see-casms-in-my-url-have-i-been-phished"></a>Vejo *. cas.ms em minha URL. Eu já fui Phish?

Em primeiro lugar, você não foi Phish! Esse tipo de URL é esperado e indica que sua organização aplica controles de segurança adicionais para proteger dados críticos para os negócios.

Eles fazem isso por...

Ao tentar acessar um aplicativo de nuvem como Salesforce, SharePoint Online ou AWS, você observará que a URL tem um sufixo `*.cas.ms` . Por exemplo, ao usar o aplicativo XYZ, a URL que você está acostumado a ver terá alterações de `XYZ.com` para `XYZ.com.us.cas.ms` .

Se a URL não corresponder exatamente ao padrão de substituição (por exemplo, redirecionando *. com para *. com.*.. cas.ms), ou se você tiver outras preocupações, entre em contato com seu departamento de ti.

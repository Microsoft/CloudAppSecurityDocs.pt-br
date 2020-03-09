---
title: Solução de problemas – o que é o cas.ms?
description: Este artigo fornece informações sobre o sufixo de URL cas.ms usado pelo Controle de Aplicativos de Acesso Condicional.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/08/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: e08fc2af75d59ac5697593a47e3a002dfb4986f9
ms.sourcegitcommit: 3f6ef6b97a0953470135d115323a00cf11441ab7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/08/2020
ms.locfileid: "78927874"
---
# <a name="troubleshooting---what-is-casms"></a>Solução de problemas – o que é o cas.ms?

*Aplica-se a: Microsoft Cloud App Security*

Este artigo fornece informações sobre o sufixo de URL `cas.ms` usado pelo Controle de Aplicativos de Acesso Condicional.

## <a name="our-system-flagged-a-new-dns-entry-or-generated-certificate-for-casms-but-we-dont-use-cloud-app-security"></a>Nosso sistema sinalizou uma nova entrada DNS ou um certificado gerado para `*.cas.ms`, mas não usamos Cloud App Security

Isso é um comportamento normal e resulta de Cloud App Security proteger seu ambiente. Mesmo que sua organização não use Cloud App Security, quando alguém visita seu site ou serviço de um ambiente que faz, suas URLs são reescritas para proteger o acesso.

Por exemplo, a contoso protege seu ambiente usando Controle de Aplicativos de Acesso Condicional fornecido pelo Cloud App Security. Quando um usuário da Contoso visita `fabrikam.com`, o usuário é automaticamente redirecionado para `fabrikam.com.<region>.cas.ms`. Como resultado, a equipe de phishing da Fabrikam verá uma nova entrada DNS e um certificado para `fabrikam.com.<region>.cas.ms`.

Portanto, embora a Fabrikam não use realmente Cloud App Security, ela vê a entrada ou o certificado DNS porque a contoso faz isso.

## <a name="heres-why-you-see-casms-in-your-url"></a>Aqui está o motivo pelo qual você vê `*.cas.ms` em sua URL

Em primeiro lugar, você não foi Phish! Esse tipo de URL é esperado e indica que sua organização aplica controles de segurança adicionais para proteger dados críticos para os negócios.

Eles fazem isso usando Cloud App Security, uma solução para proteger o ambiente de nuvem da sua organização, para substituir todas as URLs e cookies relevantes relacionados aos aplicativos de nuvem que seu uso.

Portanto, ao tentar acessar um aplicativo de nuvem, como Salesforce, SharePoint Online ou AWS, você observará que sua URL tem um sufixo com `<region>.cas.ms`. Por exemplo, ao usar o aplicativo XYZ, a URL que você está acostumado a ver as alterações de `XYZ.com` para `XYZ.com.<region>.cas.ms`.

Se a URL não corresponder exatamente ao padrão de substituição (por exemplo, `<app_site>.com` não for substituída por `<app_site>.com.<region>.cas.ms`) ou se você tiver outras preocupações, entre em contato com o departamento de ti.

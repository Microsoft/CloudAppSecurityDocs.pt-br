---
title: Solução de problemas – o que é cas.ms, mcas.ms ou mcas-gov.us?
description: Este artigo fornece informações sobre o sufixo de URL cas.ms, mcas.ms ou mcas-gov.us usado pelo Controle de Aplicativos de Acesso Condicional.
ms.date: 03/18/2020
ms.topic: conceptual
ms.openlocfilehash: a6dd901f5ed191f6c6a02514a7ddf44adf2b81ac
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96315898"
---
# <a name="troubleshooting---what-is-casms-mcasms-or-mcas-govus"></a>Solução de problemas – o que é `*.cas.ms` , `*.mcas.ms` ou `*.mcas-gov.us` ?

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Este artigo fornece informações sobre os `cas.ms` `mcas.ms` `mcas-gov.us` sufixos de URL,, e usados pelo controle de aplicativos de acesso condicional.

## <a name="our-system-flagged-a-new-dns-entry-or-generated-certificate-for-casms-mcasms-or-mcas-govus-but-we-dont-use-cloud-app-security"></a>Nosso sistema sinalizou uma nova entrada DNS ou um certificado gerado para `*.cas.ms` , `*.mcas.ms` ou `*.mcas-gov.us` , mas não usamos Cloud app Security

Isso é um comportamento normal e resulta de Cloud App Security proteger seu ambiente. Mesmo que sua organização não use Cloud App Security, quando alguém visita seu site ou serviço de um ambiente que faz, suas URLs são reescritas para proteger o acesso.

Por exemplo, a contoso protege seu ambiente usando Controle de Aplicativos de Acesso Condicional fornecido pelo Cloud App Security. Quando um usuário da Contoso visita `fabrikam.com` , o usuário é automaticamente redirecionado para `fabrikam.com.cas.ms` . Como resultado, a equipe de phishing da Fabrikam verá uma nova entrada e certificado DNS para o `fabrikam.com.cas.ms` .

Portanto, embora a Fabrikam não use realmente Cloud App Security, ela vê a entrada ou o certificado DNS porque a contoso faz isso.

> [!NOTE]
> Você também pode ver os seguintes domínios nos logs de transparência:
>
> - `*.admin-rs-mcas.ms`
> - `*.rs-mcas.ms`
> - `*.admin-rs2-mcas.ms`
> - `*.rs2-mcas.ms`
> - `*.admin-mcas.ms`
> - `*.mcas.ms`
> - `*.admin-mcas-gov.us`

## <a name="heres-why-you-see-casms-mcasms-or-mcas-govus-in-your-url"></a>Veja por que você vê `*.cas.ms` , `*.mcas.ms` ou `*.mcas-gov.us` em sua URL

Em primeiro lugar, você não foi Phish! Esse tipo de URL é esperado e indica que sua organização aplica controles de segurança adicionais para proteger dados críticos para os negócios.

Eles fazem isso usando Cloud App Security, uma solução para proteger o ambiente de nuvem da sua organização, para substituir todas as URLs e cookies relevantes relacionados aos aplicativos de nuvem que você usa.

Portanto, ao tentar acessar um aplicativo de nuvem, como Salesforce, SharePoint Online ou AWS, você observará que sua URL tem um sufixo `.cas.ms` , `.mcas.ms` ou `.mcas-gov.us` . Por exemplo, ao usar o aplicativo XYZ, a URL para a qual você está acostumado a ver alterações no `XYZ.com` `XYZ.com.cas.ms` .

Se a URL não corresponder exatamente a um dos padrões de substituição (por exemplo, `<app_site>.com` não é substituído por `<app_site>.com.cas.ms` ), ou se você tiver outras preocupações, entre em contato com o departamento de ti.

---
title: Cloud App Security filtros e consultas de aplicativo descobertos
description: Este artigo fornece uma lista de Cloud App Security consultas e filtros de aplicativo descobertos e explica como trabalhar com eles.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: ba9848bf0f9cbcee326cdebfaed09b95f38fe267
ms.sourcegitcommit: 445a7c208455e6ce2c4e13b028c811f4c3486290
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78342277"
---
# <a name="discovered-app-filters-and-queries"></a>Filtros e consultas do aplicativo descoberto

*Aplica-se a: Microsoft Cloud App Security*

Quando você tem um grande número de aplicativos descobertos, você achará útil filtrá-los e consultá-los. Este artigo descreve quais filtros estão disponíveis e como consultar seus aplicativos descobertos.

## <a name="discovered-app-filters"></a>Filtros dos aplicativos descobertos

Há filtros de aplicativos Descoberto básicos e avançados. Para obter um filtro complexo (como no exemplo acima), use a opção avançado, que inclui todos os seguintes filtros:

![Aplicativos Descobertos](media/discovered-apps.png)

- **Marca de aplicativo**: selecione se o aplicativo foi sancionado, não sancionado ou não está marcado. Além disso, você pode criar uma marca personalizada para seu aplicativo e, em seguida, usá-la para filtrar tipos específicos de aplicativos.
- **Aplicativos e domínios**: permite que você pesquise aplicativos específicos ou aplicativos usados em domínios específicos.
- **Categorias**: o filtro categorias, localizado à esquerda da página, permite Pesquisar tipos de aplicativos de acordo com as categorias de aplicativo. As categorias de exemplo incluem aplicativos de rede social, aplicativos de armazenamento em nuvem e serviços de hospedagem. Você pode selecionar várias categorias por vez, ou uma única categoria, aplicar os filtros básico e avançado na parte superior.
- **Fator de risco de conformidade**: permite que você pesquise padrões, certificações e conformidade específicos que o aplicativo possa obedecer (HIPAA, ISO 27001, SOC 2, PCI-DSS e muito mais).
- **Fator de risco geral**: permite que você pesquise fatores de risco gerais, como a popularidade do consumidor, a localidade Data Center e muito mais.
- **Pontuação de risco**: permite filtrar aplicativos por Pontuação de risco para que você possa se concentrar, por exemplo, revisando apenas aplicativos altamente arriscados. Você também pode substituir a pontuação de risco definida pelo Cloud App Security. Para obter mais informações, consulte [trabalhando com a pontuação de risco](risk-score.md).
- **Fator de risco de segurança**: habilita a filtragem com base em medidas específicas de segurança (como Criptografia em rest, autenticação multifator etc.).
- **Uso**: permite que você filtre com base nas estatísticas de uso deste aplicativo. Uso como aplicativos com menos de ou mais de um número especificado de **carregamentos de dados**, aplicativos com mais ou menos do que um número especificado de **usuários**.
- **Fator de risco legal**: permite que você filtre com base em todas as regulamentações e políticas que estão in-loco para garantir a proteção de dados e a privacidade dos usuários do aplicativo. Os exemplos incluem aplicativos de nuvem prontos para GDPR, DMCA e política de retenção de dados.

### <a name="creating-and-managing-custom-app-tags"></a>Criando e gerenciando marcas de aplicativo personalizadas

Você pode criar uma marca de aplicativo personalizada.
Essas marcas podem ser usadas como filtros para aprofundar-se nos tipos específicos de aplicativos que você deseja investigar. Por exemplo, lista de observação personalizada, atribuição a uma unidade de negócios específica ou aprovações personalizadas, como "aprovado pelo departamento jurídico".

Para criar uma marca de aplicativo personalizada:

1. Na engrenagem de **configurações** , selecione **configurações de Cloud Discovery**e, em seguida, a guia **marcas de aplicativo** . Clique no ícone de adição. ![ícone de adição](media/plus-icon.png)

   ![criar marca de aplicativo personalizada](media/create-app-tag.png)

2. Você pode usar a tabela de **marcas de aplicativo** para exibir quais aplicativos estão marcados atualmente com cada marca de aplicativo e pode excluir marcas de aplicativo não utilizadas.

3. Para aplicar uma marca de aplicativo, na guia **aplicativos descobertos** , clique nos três pontos na extrema direita do nome do aplicativo. Selecione a marca do aplicativo a ser aplicada.

> [!NOTE]
>Você também pode criar uma nova marca de aplicativo diretamente na tabela **Aplicativos descobertos** clicando na marca **Criar aplicativo** depois de selecionar os três pontos à direita de qualquer aplicativo selecionado. Ao criar a marca do aplicativo descoberto, você pode aplicá-la ao aplicativo. Você também pode acessar a tela de **marcas do aplicativo** clicando no link **gerenciar marcas** no canto.
> ![criar uma marca de aplicativo personalizada do aplicativo](media/create-app-tag-from-app.png)

## <a name="discovered-app-queries"></a>Consultas de aplicativo descobertas

Para tornar a investigação ainda mais simples, você pode criar consultas personalizadas e salvá-las para uso posterior.

1. Na página **aplicativos descobertos** , use os filtros conforme descrito acima para fazer uma busca detalhada em seus aplicativos, conforme necessário.

2. Depois de atingir os resultados desejados, clique no botão **salvar como** no canto superior direito dos filtros.

3. No pop-up **Salvar consulta** , nomeie sua consulta.

    ![nova consulta](media/new-query.png)

4. Para usar essa consulta novamente no futuro, em **consultas**, role para baixo até **consultas salvas** e selecione sua consulta.

    ![Abrir consulta](media/discovered-app-query.png)

Cloud App Security também fornece **consultas sugeridas** e permite salvar consultas personalizadas que você usa com frequência. As consultas sugeridas fornecem a você as avenidas recomendadas de investigação que filtram seus aplicativos descobertos usando as seguintes consultas sugeridas opcionais:

- **Aplicativos de nuvem que permitem uso anônimo** – filtra todos os seus aplicativos descobertos para exibir somente os aplicativos que são riscos de segurança porque eles não exigem autenticação de usuário e permitem que os usuários carreguem dados.

- **Aplicativos de nuvem que são certificados pelo CSA Star** – filtra todos os seus aplicativos descobertos para exibir somente os aplicativos que têm a certificação CSA Star por autoavaliação, certificação, atestado ou monitoramento contínuo.

- **Aplicativos de nuvem que são compatíveis com FedRAMP** – filtra todos os seus aplicativos descobertos para exibir somente aplicativos cujo fator de risco de conformidade FedRAMP seja alto, médio ou baixo.

- **Armazenamento em nuvem e aplicativos de colaboração que possuem dados de usuário** – filtra todos os seus aplicativos descobertos para exibir apenas os aplicativos arriscados porque eles não permitem que você tenha Propriedade sobre seus dados, mas eles mantêm seus dados.

- **Aplicativos de armazenamento em nuvem que são arriscados e não compatíveis** – filtra todos os seus aplicativos descobertos para exibir somente os aplicativos nos quais eles não são compatíveis com SoC 2 ou HIPAA, eles não oferecem suporte à versão PCI DSS e têm uma pontuação de risco de 5 ou menos.

- **Aplicativos de nuvem corporativa que têm autenticação fraca** – filtra todos os seus aplicativos descobertos para exibir somente aplicativos que não dão suporte a SAML, não têm nenhuma política de senha e não habilitam MFA.

- **Aplicativos de nuvem corporativa que têm criptografia fraca** – filtra todos os seus aplicativos descobertos para exibir somente aplicativos que são arriscados porque não criptografam dados em repouso e não oferecem suporte a nenhum protocolo de criptografia.

- **Aplicativos de nuvem prontos** para o GDPR – filtra todos os seus aplicativos descobertos para exibir somente os aplicativos que estão GDPR prontos. Como a conformidade do GDPR é uma prioridade máxima, essa consulta ajuda você a identificar facilmente os aplicativos que estão GDPR prontos e mitigar a ameaça, avaliando o risco daqueles que não são.

![consultar aplicativos descobertos](media/queries-discovered-apps.png)

Além disso, você pode usar as consultas sugeridas como um ponto de partida para uma nova consulta. Primeiro, selecione uma das consultas sugeridas. Em seguida, faça as alterações conforme necessário e, por fim, clique em **salvar como** para criar uma nova **consulta salva**.

## <a name="next-steps"></a>{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}

> [!div class="nextstepaction"]
> [Criar instantâneo de relatórios do Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

> [!div class="nextstepaction"]
> [Configurar upload de log automático para relatórios contínuos](configure-automatic-log-upload-for-continuous-reports.md)

> [!div class="nextstepaction"]
> [Trabalhando com os dados do Cloud Discovery](working-with-cloud-discovery-data.md)

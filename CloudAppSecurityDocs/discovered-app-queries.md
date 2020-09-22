---
title: Consultas e filtros de aplicativos descobertos do Cloud App Security
description: Este artigo fornece uma lista de consultas e filtros de aplicativos descobertos do Cloud App Security e explica como trabalhar com eles.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 07/07/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: ef61d90f23eb9e15b8b84f926b0b4424f4b3b36b
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90881679"
---
# <a name="discovered-app-filters-and-queries"></a>Filtros e consultas do aplicativo descoberto

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Quando você tiver um grande número de aplicativos descobertos, considerará útil filtrá-los e consultá-los. Este artigo descreve quais filtros estão disponíveis e como consultar os aplicativos descobertos.

## <a name="discovered-app-filters"></a>Filtros dos aplicativos descobertos

Há filtros de aplicativos Descoberto básicos e avançados. Para alcançar um filtro complexo (como no exemplo acima), use a opção avançada, que inclui todos os filtros a seguir:

![Aplicativos Descobertos](media/discovered-apps.png)

- **Marca de aplicativo**: selecione se o aplicativo foi sancionado, não sancionado ou não está marcado. Além disso, você pode criar uma marca personalizada para seu aplicativo e, em seguida, usá-la para filtrar tipos específicos de aplicativos.
- **Aplicativos e domínios**: permite que você pesquise aplicativos específicos ou aplicativos usados em domínios específicos.
- **Categorias**: o filtro de categorias, localizado à esquerda da página, permite que você pesquise tipos de aplicativos de acordo com as categorias de aplicativo. Exemplos de categorias incluem aplicativos de rede social, aplicativos de armazenamento em nuvem e serviços de hospedagem. Você pode selecionar várias categorias por vez ou uma única categoria e, em seguida, aplicar os filtros básicos e avançados sobre elas.
- **Fator de risco de conformidade**: permite que você pesquise padrões específicos, certificação e conformidade com os quais o aplicativo pode cumprir (HIPAA, ISO 27001, SOC 2, PCI-DSS, entre outros).
- **Fator de risco geral**: permite que você pesquise fatores de risco gerais, como a popularidade do consumidor, localidade do data center, entre outros.
- **Pontuação de risco**: permite que você filtre aplicativos por classificação de risco para que você possa se concentrar, por exemplo, revisando somente os aplicativos de alto risco. Você também pode substituir a pontuação de risco definida pelo Cloud App Security. Para obter mais informações, consulte [trabalhando com a pontuação de risco](risk-score.md).
- **Fator de risco de segurança**: habilita a filtragem com base em medidas específicas de segurança (como Criptografia em rest, autenticação multifator etc.).
- **Uso**: permite que você filtre com base nas estatísticas de uso desse aplicativo. Uso como aplicativos com um número maior ou menor que o especificado de **uploads de dados**, aplicativos com um número maior ou menor que o especificado de **Usuários**.
- **Fator de risco legal**: permite filtrar com base em todos os regulamentos e políticas que estão em vigor para garantir a proteção de dados e a privacidade dos usuários do aplicativo. Exemplos incluem aplicativos em nuvem prontos para RGPD, DMCA e política de retenção de dados.

### <a name="creating-and-managing-custom-app-tags"></a>Criando e gerenciando marcas de aplicativo personalizadas

Você pode criar uma marca de aplicativo personalizada. Essas marcas podem ser usadas como filtros para aprofundar-se nos tipos específicos de aplicativos que você deseja investigar. Por exemplo, lista de observação personalizada, atribuição para uma unidade de negócios específica ou aprovações personalizadas, como "aprovadas por ofício". As marcas de aplicativo também podem ser usadas em políticas de descoberta de aplicativo em filtros ou aplicando marcas a aplicativos como parte das ações de governança de política.

Para criar uma marca de aplicativo personalizada:

1. Na engrenagem de **configurações** , selecione **configurações de Cloud Discovery**e, em seguida, a guia **marcas de aplicativo** . Clique no ícone de adição. ![ícone de mais](media/plus-icon.png)

   ![criar marca de aplicativo personalizada](media/create-app-tag.png)

2. Você pode usar a tabela **Marcas de aplicativo** para exibir quais aplicativos estão atualmente marcados com cada marca de aplicativo e você pode excluir marcas de aplicativo não usadas.

3. Para aplicar uma marca de aplicativo, na guia **Aplicativos descobertos**, clique nos três pontos bem à direita do nome do aplicativo. Selecione a marca de aplicativo a ser aplicada.

> [!NOTE]
>Você também pode criar uma nova marca de aplicativo diretamente na tabela **Aplicativos descobertos** clicando na marca **Criar aplicativo** depois de selecionar os três pontos à direita de qualquer aplicativo selecionado. Quando você cria a marca do aplicativo descoberto, pode aplicá-la ao aplicativo. Você também pode acessar a tela **Marcas de aplicativo** clicando no link **Gerenciar marcas** no canto.
> ![criar marca de aplicativo personalizada usando o aplicativo](media/create-app-tag-from-app.png)

## <a name="discovered-app-queries"></a>Consultas de aplicativos descobertos

Para fazer uma investigação ainda mais simples, você pode criar consultas personalizadas e salvá-las para uso posterior.

1. Na página **Aplicativos descobertos**, use os filtros, conforme descrito acima, para fazer drill down em seus aplicativos, conforme necessário.

2. Depois de obter os resultados desejados, clique no botão **Salvar como** no canto superior direito dos filtros.

3. No pop-up **Salvar consulta** , nomeie sua consulta.

    ![nova consulta](media/new-query.png)

4. Para usar essa consulta novamente no futuro, em **Consultas**, role para baixo até **Consultas salvas** e selecione a consulta.

    ![abrir consulta](media/discovered-app-query.png)

O Cloud App Security também fornece **Consultas sugeridas** e permite salvar consultas personalizadas usadas com frequência. As consultas sugeridas fornecem vias de investigação recomendadas que filtram os aplicativos descobertos usando as seguintes consultas sugeridas opcionais:

- **Aplicativos de nuvem que permitem uso anônimo** – filtra todos os seus aplicativos descobertos para exibir somente os aplicativos que são riscos de segurança porque eles não exigem autenticação de usuário e permitem que os usuários carreguem dados.

- **Aplicativos de nuvem que são certificados pelo CSA Star** – filtra todos os seus aplicativos descobertos para exibir somente os aplicativos que têm a certificação CSA Star por autoavaliação, certificação, atestado ou monitoramento contínuo.

- **Aplicativos de nuvem que são compatíveis com FedRAMP** – filtra todos os seus aplicativos descobertos para exibir somente aplicativos cujo fator de risco de conformidade FedRAMP seja alto, médio ou baixo.

- **Aplicativos de armazenamento em nuvem e colaboração que têm dados do usuário** – filtra todos os aplicativos descobertos para exibir apenas os aplicativos que apresentam riscos porque não permitem que você tenha a propriedade sobre seus dados, pois são retidos por eles.

- **Aplicativos de armazenamento em nuvem que são arriscados e não compatíveis** – filtra todos os seus aplicativos descobertos para exibir somente os aplicativos nos quais eles não são compatíveis com SoC 2 ou HIPAA, eles não oferecem suporte à versão PCI DSS e têm uma pontuação de risco de 5 ou menos.

- **Aplicativos de nuvem corporativa que têm autenticação fraca** – filtra todos os seus aplicativos descobertos para exibir somente aplicativos que não dão suporte a SAML, não têm nenhuma política de senha e não habilitam MFA.

- **Aplicativos de nuvem corporativa que têm criptografia fraca** – filtra todos os seus aplicativos descobertos para exibir somente aplicativos que são arriscados porque não criptografam dados em repouso e não oferecem suporte a nenhum protocolo de criptografia.

- **Aplicativos na nuvem prontos para RGPD** – filtra todos os aplicativos descobertos para exibir apenas os aplicativos que estão prontos para o RGPD. Como a conformidade do GDPR é uma prioridade máxima, essa consulta ajuda você a identificar facilmente os aplicativos que estão GDPR prontos e mitigar a ameaça, avaliando o risco daqueles que não são.

![consultar aplicativos descobertos](media/queries-discovered-apps.png)

Além disso, use as consultas sugeridas como um ponto de partida para uma nova consulta. Primeiro, selecione uma das consultas sugeridas. Em seguida, faça as alterações necessárias e, por fim, clique em **Salvar como** para criar uma nova **Consulta salva**.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Criar instantâneo de relatórios do Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

> [!div class="nextstepaction"]
> [Configurar upload de log automático para relatórios contínuos](configure-automatic-log-upload-for-continuous-reports.md)

> [!div class="nextstepaction"]
> [Trabalhando com dados do Cloud Discovery](working-with-cloud-discovery-data.md)

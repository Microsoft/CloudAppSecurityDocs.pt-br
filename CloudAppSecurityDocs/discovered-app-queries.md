---
title: Trabalhando com consultas e filtros de aplicativos descobertos do Cloud App Security | Microsoft Docs
description: "Este tópico fornece uma lista de consultas e filtros de aplicativos descobertos do Cloud App Security e explica como trabalhar com eles."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/3/2018
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 1a2d3aeb-4e28-4c73-804b-95e862b08e43
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: ea1b0b150f1028e8a8d4edac32aa6d8a4f59b564
ms.sourcegitcommit: bbf4a2715d1ea3fd21c1a1b87c7f5a2947d2ca68
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/04/2018
---
# <a name="discovered-app-filters-and-queries"></a>Consultas e filtros de aplicativos descobertos

## <a name="discovered-app-filters"></a>Filtros dos aplicativos descobertos

Há filtros de aplicativos Descoberto básicos e avançados. Para alcançar um filtro complexo (como no exemplo acima), use a opção avançada, que inclui todos os itens a seguir:

![Aplicativos Descobertos](./media/discovered-apps.png)  


- **Marca de aplicativo**: selecione se o aplicativo foi sancionado, não sancionado ou não está marcado. Além disso, você pode criar uma marca personalizada para seu aplicativo e, em seguida, usá-la para filtrar tipos específicos de aplicativos. 
- **Aplicativos e domínios**: permite que você pesquise aplicativos específicos ou aplicativos usados em domínios específicos. 
- **Categorias**: o filtro de categorias, que está localizado à esquerda da página, permite pesquisar tipos de aplicativos de acordo com as categorias de aplicativo, por exemplo, aplicativos de rede Social, aplicativos de armazenamento em nuvem etc. Você pode selecionar várias categorias por vez ou uma única categoria e, em seguida, aplicar os filtros básicos e avançados sobre eles.
- **Fator de risco de conformidade**: permite que você pesquise padrões específicos, certificação e conformidades com as quais o aplicativo pode cumprir (HIPAA ISO 27001, SOC 2, PCI-DSS etc.).
- **Fator de risco geral**: permite que você pesquise fatores de risco gerais, como a popularidade do consumidor, Data center local etc.
- **Pontuação de risco**: permite que você filtre aplicativos por classificação de risco para que você possa se concentrar, por exemplo, revisando somente os aplicativos muito arriscados. Você também pode substituir a pontuação de risco definida pelo Cloud App Security. Para saber mais, confira [Trabalhando com pontuação de risco](risk-score.md).
- **Fator de risco de segurança**: habilita a filtragem com base em medidas específicas de segurança (como Criptografia em rest, autenticação multifator etc.).
- **Uso**: permite filtrar com base em estatísticas de uso deste aplicativo, como aplicativos com menos de ou mais de uma quantidade especificada de **carregamentos de dados**, aplicativos com maior ou menor que um número especificado de **Usuários**.

### <a name="creating-and-managing-custom-app-tags"></a>Criando e gerenciando marcas de aplicativo personalizadas

Você pode criar uma marca de aplicativo personalizada. Essas marcas podem ser usadas como filtros para aprofundar-se nos tipos específicos de aplicativos que você deseja investigar. Por exemplo, lista de observação personalizada, atribuição a uma unidade de negócios específica ou aprovações personalizadas, como "aprovado pelo departamento jurídico".

Para criar uma marca de aplicativo personalizada:

1. Na engrenagem **Configurações**, selecione **Cloud Discovery** e na guia **Gerenciar marcas de aplicativo**, clique no ícone ![de adição](./media/plus-icon.png). 

![criar marca de aplicativo personalizada](./media/create-app-tag.png)

2. Você pode usar a tabela **Gerenciar marcas de aplicativo** para exibir quais aplicativos atualmente são marcados com cada marca de aplicativo e você pode excluir marcas de aplicativo não utilizados.

3. Para aplicar uma marca de aplicativo, na guia **Aplicativos descobertos**, clique nos três pontos na extremidade direita da tabela e selecione a marca do aplicativo para aplicar. 

> [!NOTE]
>Você também pode criar uma nova marca de aplicativo diretamente na tabela **Aplicativos descobertos** clicando na marca **Criar aplicativo** depois de selecionar os três pontos à direita de qualquer aplicativo selecionado. Você também pode acessar a tela **Gerenciar marcas de aplicativo** clicando no link no canto do pop-up **Criar marca de aplicativo**.

## <a name="discovered-app-queries"></a>Consultas de aplicativos descobertos

Para simplificar ainda mais a investigação, agora você pode criar consultas personalizadas e salvá-las para uso posterior. 

1. Na página **Aplicativos descobertos**, use os filtros, conforme descrito acima, para fazer drill down em seus aplicativos, conforme necessário. 

2. Depois de obter os resultados desejados, clique no botão **Salvar como** no canto superior direito dos filtros. 

3. No pop-up **Salvar consulta**, nomeie a consulta.

 ![nova consulta](./media/new-query.png)

4. Para usar essa consulta novamente no futuro, em **Consultas**, role para baixo até **Consultas salvas** e selecione a consulta. 

 ![abrir consulta](./media/open-query.png)


O Cloud App Security também fornece **Consultas sugeridas** e permite salvar consultas personalizadas usadas com frequência. As consultas sugeridas fornecem vias de investigação recomendadas que filtram os aplicativos descobertos usando as seguintes consultas sugeridas opcionais:

 - Aplicativos na nuvem que permitem o uso anônimo – filtra todos os aplicativos descobertos para exibir apenas os aplicativos que apresentam riscos de segurança porque não exigem a autenticação do usuário e permitem que os usuários carreguem dados.

 - Aplicativos na nuvem que têm a certificação CSA STAR – filtra todos os aplicativos descobertos para exibir apenas os aplicativos que têm a certificação CSA STAR por autoavaliação, certificação, atestado ou monitoramento contínuo.

 - Aplicativos na nuvem em conformidade com o FedRAMP – filtra todos os aplicativos descobertos para exibir apenas os aplicativos cujo fator de risco de conformidade com o FedRAMP é alto, médio ou baixo. 

 - Aplicativos de armazenamento em nuvem e colaboração que têm dados do usuário – filtra todos os aplicativos descobertos para exibir apenas os aplicativos que apresentam riscos porque não permitem que você tenha a propriedade sobre seus dados, pois são retidos por eles.

 - Aplicativos de armazenamento em nuvem que apresentam riscos e não estão em conformidade – filtra todos os aplicativos descobertos para exibir apenas os aplicativos que não estão em conformidade com o SOC 2 ou o HIPAA, não dão suporte à versão do PCI DSS e têm uma pontuação de risco igual a 5 ou inferior.

 - Aplicativos em nuvem empresariais que têm autenticação fraca – filtra todos os aplicativos descobertos para exibir apenas os aplicativos para os quais não há suporte para o SAML, não têm nenhuma política de senha e não habilitam o MFA.

 - Aplicativos em nuvem empresariais que têm criptografia fraca – filtra todos os aplicativos descobertos para exibir apenas os aplicativos que apresentam riscos porque não criptografam dados em repouso e não dão suporte a nenhum protocolo de criptografia.

![consultar aplicativos descobertos](./media/queries-discovered-apps.png)

 
Além disso, use as consultas sugeridas como um ponto de partida para uma nova consulta. Primeiro, selecione uma das consultas sugeridas. Em seguida, faça as alterações necessárias e, por fim, clique em **Salvar como** para criar uma nova **Consulta salva**.


## <a name="see-also"></a>Consulte também
 
[Criar instantâneo de relatórios do Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

[Configurar upload de log automático para relatórios contínuos](configure-automatic-log-upload-for-continuous-reports.md)

[Trabalhando com os dados do Cloud Discovery](working-with-cloud-discovery-data.md)

---
title: Monitorar e proteger arquivos em aplicativos de nuvem – Cloud App Security | Microsoft Docs
description: Este artigo descreve o procedimento para configurar uma política de dados para monitorar e controlar os dados e arquivos no uso do aplicativo de nuvem da sua organização.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 10/7/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 2dcfbaa4cfb676aafcb996efaa243adeedaf93f7
ms.sourcegitcommit: 06437f58d452294cf53d1ad86f7cb857569cd5ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/16/2020
ms.locfileid: "77369550"
---
# <a name="file-policies"></a>Políticas de arquivos

*Aplica-se a: Microsoft Cloud App Security*

As políticas de arquivo permitem impor uma ampla variedade de processos automatizados usando as APIs do provedor de nuvem. As políticas podem ser definidas para fornecer verificações de conformidade contínuas, tarefas de eDiscovery legais, DLP para conteúdo confidencial compartilhado publicamente e muito mais casos de uso. Cloud App Security pode monitorar qualquer tipo de arquivo com base em mais de 20 filtros de metadados (por exemplo, nível de acesso, tipo de arquivo).

## <a name="supported-file-types"></a>Tipos de arquivos com suporte

Os mecanismos de DLP internos da Cloud App Security executam a inspeção de conteúdo extraindo o texto de todos os tipos de arquivo comuns (100 +), incluindo Office, Open Office, arquivos compactados, vários formatos de texto avançados, XML, HTML e muito mais.

## <a name="policies"></a>Políticas

O mecanismo combina três aspectos em cada política:

* Verificação de conteúdo com base em modelos predefinidos ou expressões personalizadas.

* Filtros de contexto, incluindo funções de usuário, metadados de arquivo, nível de compartilhamento, integração de grupo organizacional, contexto de colaboração e atributos personalizáveis adicionais.

* Ações automatizadas para governança e correção. Para obter mais informações, consulte [Control](control.md).
    > [!NOTE]
    > Somente a ação de governança da primeira política disparada é garantida para ser aplicada. Por exemplo, se uma política de arquivo já tiver aplicado um rótulo AIP a um arquivo, uma segunda política de arquivo não poderá aplicar outro rótulo de AIP a ele.

Uma vez habilitado, a política verifica continuamente o ambiente de nuvem e identifica os arquivos que correspondem ao conteúdo e filtros de contexto e aplica as ações automáticas solicitadas. Essas políticas detectam e corrigem quaisquer violações para informações em repouso ou quando um novo conteúdo é criado. As políticas podem ser monitoradas usando alertas em tempo real ou usando relatórios gerados pelo console.

Veja a seguir exemplos de políticas de arquivo que podem ser criadas:

* **Arquivos compartilhados publicamente** – receba um alerta sobre qualquer arquivo em sua nuvem que é compartilhado publicamente selecionando todos os arquivos cujo nível de compartilhamento é público.

* **O nome de arquivo compartilhado publicamente contém o nome da organização** -receba um alerta sobre qualquer arquivo que contenha o nome da sua organização e compartilhado publicamente. Selecione arquivos com um nome de arquivo que contém o nome da sua organização e que são compartilhados publicamente.

* **Compartilhamento com domínios externos** – receba um alerta sobre qualquer arquivo compartilhado com contas pertencentes a domínios externos específicos. Por exemplo, arquivos compartilhados com o domínio de um concorrente. Selecione o domínio externo com o qual você deseja limitar o compartilhamento.

* **Arquivos compartilhados em quarentena não modificados durante o último período** – receba um alerta sobre arquivos compartilhados que não foram modificados recentemente para colocá-los em quarentena ou optar por ativar uma ação automatizada. Exclua todos os arquivos particulares que não foram modificados durante um intervalo de datas especificado. No G Suite, você pode optar por colocar esses arquivos em quarentena, usando a caixa de seleção ' arquivo de quarentena ' na página de criação de política.

* **Compartilhamento com usuários não autorizados** – receba um alerta sobre arquivos compartilhados com o grupo de usuários não autorizados em sua organização. Selecione os usuários para os quais o compartilhamento não está autorizado.

* **Extensão de arquivo confidencial** – receba um alerta sobre arquivos com extensões específicas que são potencialmente altamente expostas. Selecione a extensão específica (por exemplo, CRT para certificados) ou nome de arquivo e exclua esses arquivos com o nível de compartilhamento privado.

## <a name="create-a-new-file-policy"></a>Criar uma nova política de arquivo

Para criar uma nova política de arquivo, siga este procedimento:

1. No console do, clique em **controle** seguido por **políticas**.

1. Clique em **criar política** e selecione política de **arquivo** .

1. Dê um nome e uma descrição à sua política, se você quiser que possa baseá-la em um modelo, para obter mais informações sobre modelos de política, consulte [controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md).

1. Dê à sua política uma **severidade de política**. Se você tiver definido Cloud App Security para enviar notificações sobre correspondências de política para um nível de severidade de política específico, esse nível será usado para determinar se as correspondências da política disparam uma notificação.

1. Na **categoria**, vincule a política ao tipo de risco mais apropriado. Este campo é apenas informativo e ajuda a Pesquisar políticas e alertas específicos mais tarde, com base no tipo de risco.  O risco já pode ter sido selecionado de acordo com a categoria para a qual você optou por criar a política. Por padrão, as políticas de arquivo são definidas como DLP.

1. **Crie um filtro para os arquivos que esta política atuará** para definir quais aplicativos descobertos disparam essa política. Restrinja os filtros de política até alcançar um conjunto preciso de arquivos com os quais você deseja agir. Seja o mais restritivo possível para evitar falsos positivos. Por exemplo, se você quiser remover permissões públicas, lembre-se de adicionar o filtro **público** , se desejar remover um usuário externo, use o filtro "externo", etc.
   > [!NOTE]
   > Ao usar os filtros de política, o **contém** pesquisas somente por palavras completas – separadas por comas, pontos, espaços ou sublinhados. Por exemplo, se você Pesquisar **malware** ou **vírus**, ele encontrará virus_malware_file. exe, mas não encontrará o malwarevirusfile. exe. Se você Pesquisar **malware. exe**, encontrará todos os arquivos com malware ou exe em seu nome de arquivo, enquanto se procurar por **"malware. exe"** (com as aspas), você encontrará apenas os arquivos que contêm exatamente "malware. exe". **Equals** pesquisa apenas a cadeia de caracteres completa, por exemplo, se você pesquisar por **malware. exe** , ele encontra malware. exe, mas não malware. exe. txt.
1. No primeiro filtro **aplicar a** , selecione **todos os arquivos, excluindo pastas selecionadas** ou **pastas selecionadas** para o box, SharePoint, Dropbox, onedrive, em que você pode impor a política de arquivo em todos os arquivos no aplicativo ou em pastas específicas. Você é redirecionado para entrar no aplicativo de nuvem e, em seguida, adiciona as pastas relevantes.

1. Sob o segundo **aplicar ao** filtro, selecione **todos os proprietários de arquivo**, **proprietários de arquivos de grupos de usuários selecionados** ou **todos os proprietários de arquivos, excluindo grupos selecionados**. Em seguida, selecione os grupos de usuários relevantes para determinar quais usuários e grupos devem ser incluídos na política.

1. Selecione o **método de inspeção de conteúdo**. Você pode selecionar o [**DLP interno**](content-inspection-built-in.md) ou [**os serviços de classificação de dados**](content-inspection.md). É recomendável usar **os serviços de classificação de dados**.

    Depois que a inspeção de conteúdo estiver habilitada, você poderá optar por usar expressões predefinidas ou pesquisar outras expressões personalizadas.

    Além disso, você pode especificar uma expressão regular para excluir um arquivo dos resultados. Essa opção será altamente útil se você tiver um padrão de palavra-chave de classificação interna que você deseja excluir da política.

    Você pode decidir definir o número mínimo de violações de conteúdo que deseja corresponder antes que o arquivo seja considerado uma violação. Por exemplo, você pode escolher 10 se deseja ser alertado em arquivos com pelo menos 10 números de cartão de crédito encontrados em seu conteúdo.

    Quando o conteúdo é correspondido em relação à expressão selecionada, o texto de violação é substituído por caracteres "X". Por padrão, as violações são mascaradas e mostradas em seu contexto exibindo 100 caracteres antes e depois da violação. Os números no contexto da expressão são substituídos por caracteres "#" e nunca são armazenados dentro de Cloud App Security. Você pode selecionar a opção para **remover a máscara dos últimos quatro caracteres de uma violação** para remover a máscara dos últimos quatro caracteres da violação em si. É necessário definir quais tipos de dados são pesquisados pela expressão regular: conteúdo, metadados e/ou nome do arquivo. Por padrão, ele pesquisa o conteúdo e os metadados.

1. Escolha as ações de **governança** que você deseja que Cloud app Security execute quando uma correspondência for detectada.

1. Depois de criar sua política, você poderá exibi-la na guia **política de arquivo** . Você sempre pode editar uma política, calibrar seus filtros ou alterar as ações automatizadas. A política é habilitada automaticamente após a criação e começa a verificar seus arquivos de nuvem imediatamente.  Tenha cuidado extra quando você definir ações de governança, elas podem levar à perda irreversível de permissões de acesso para seus arquivos. É recomendável restringir os filtros para representar exatamente os arquivos nos quais você deseja agir, usando vários campos de pesquisa. Quanto mais estreita os filtros, melhor. Para obter diretrizes, você pode usar o botão **Editar e Visualizar resultados** na seção filtros.

    ![resultados de edição e visualização da política de arquivo](media/file-policy-edit-and-preview-results.png)

1. Para exibir as correspondências de política de arquivo, os arquivos que suspeitam de violar a política, clique em **controle** e em **políticas**. Filtre os resultados para exibir apenas as políticas de arquivo usando o filtro de **tipo** na parte superior. Para obter mais informações sobre as correspondências para cada política, clique em uma política. Isso exibe os arquivos "correspondendo agora" para a política. Clique na guia **histórico** para ver um histórico de volta para até seis meses de arquivos que corresponderam à política.

## <a name="file-policy-reference"></a>Referência de política de arquivo

Esta seção fornece detalhes de referência sobre as políticas, fornecendo explicações para cada tipo de política e os campos que podem ser configurados para cada política.

Uma **política de arquivo** é uma política baseada em API que permite controlar o conteúdo da sua organização na nuvem, levando em conta mais de 20 filtros de metadados de arquivo (incluindo o proprietário e o nível de compartilhamento) e resultados de inspeção de conteúdo. Com base nos resultados da política, as ações de governança podem ser aplicadas. O mecanismo de inspeção de conteúdo pode ser estendido por meio de mecanismos de DLP de terceiros, bem como soluções antimalware.

Cada política é composta pelas seguintes partes:

* **Filtros de arquivo** – permite que você crie condições granulares com base em metadados.

* **Inspeção de conteúdo** – permite que você restrinja a política, com base nos resultados do mecanismo de DLP. Você pode incluir uma expressão personalizada ou uma expressão predefinida. As exclusões podem ser definidas e você pode escolher o número de correspondências. Você também pode usar a anonimato para mascarar o nome de usuário.

* **Ações** – a política fornece um conjunto de ações de governança que podem ser aplicadas automaticamente quando violações são encontradas.  Essas ações são divididas em ações de colaboração, ações de segurança e ações de investigação.

* **Extensões** -a inspeção de conteúdo pode ser executada por meio de mecanismos de terceiros para aprimorar os recursos de DLP ou anti-malware.

## <a name="file-queries"></a>Consultas de arquivo

Para tornar a investigação ainda mais simples, agora você pode criar consultas personalizadas e salvá-las para uso posterior.

1. Na página **arquivo** , use os filtros conforme descrito acima para fazer uma busca detalhada em seus aplicativos, conforme necessário.

1. Depois de concluir a criação da consulta, clique no botão **salvar como** no canto superior direito dos filtros.

1. No pop-up **Salvar consulta** , nomeie sua consulta.

1. Para usar essa consulta novamente no futuro, em **consultas**, role para baixo até **consultas salvas** e selecione sua consulta.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]

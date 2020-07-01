---
title: Monitorar e proteger arquivos em aplicativos de nuvem – Cloud App Security
description: Este artigo descreve o procedimento para configurar uma política de dados para monitorar e controlar os dados e os arquivos em uso nos aplicativos na nuvem de sua organização.
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
ms.openlocfilehash: 317595b377d19b1d6f9a06b316cb14e4d1ad4c1c
ms.sourcegitcommit: b15034dd50142afd8e95de22a9232f711b1eae6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85624588"
---
# <a name="file-policies"></a>Políticas de arquivos

*Aplica-se a: Microsoft Cloud App Security*

As políticas de arquivo permitem impor uma ampla variedade de processos automatizados usando as APIs do provedor de nuvem. As políticas podem ser configuradas para fornecer verificações de conformidade contínuas, tarefas de Descoberta Eletrônica legais, DLP para conteúdo confidencial compartilhado publicamente e muito mais casos de uso. O Cloud App Security pode monitorar qualquer tipo de arquivo com base em mais de 20 filtros de metadados (como por exemplo, nível de acesso e tipo de arquivo).

## <a name="supported-file-types"></a>Tipos de arquivo com suporte

Os mecanismos de DLP internos do Cloud App Security executam a inspeção de conteúdo extraindo o texto de todos os tipos de arquivo comuns (100 +), incluindo Office, Open Office, arquivos compactados, vários formatos de texto avançados, XML, HTML e muito mais.

## <a name="policies"></a>Políticas

O mecanismo combina três aspectos em cada política:

* Verificação de conteúdo com base em modelos predefinidos ou expressões personalizadas.

* Filtros de contexto, incluindo funções de usuário, metadados de arquivo, nível de compartilhamento, integração do grupo organizacional, contexto de colaboração e atributos personalizáveis adicionais.

* Ações automatizadas para governança e correção. Para obter mais informações, consulte [Control](control.md) (Controlar).
    > [!NOTE]
    > Somente a ação de governança da primeira política disparada é garantida para ser aplicada. Por exemplo, se uma política de arquivo já tiver aplicado um rótulo AIP a um arquivo, uma segunda política de arquivo não poderá aplicar outro rótulo de AIP a ele.

Quando habilitada, a política examina continuamente seu ambiente de nuvem, identifica arquivos que correspondem aos filtros de contexto e conteúdo e aplica as ações automatizadas solicitadas. Essas políticas detectam e corrigem violações de informações em repouso ou quando novo conteúdo é criado. As políticas podem ser monitoradas usando alertas em tempo real ou relatórios gerados do console.

A seguir estão exemplos das políticas de arquivos que podem ser criadas:

* **Arquivos compartilhados publicamente** – receba um alerta sobre qualquer arquivo em sua nuvem que esteja compartilhado publicamente selecionando todos os arquivos cujo nível de compartilhamento é público.

* **O nome de arquivo compartilhado publicamente contém o nome da organização** -receba um alerta sobre qualquer arquivo que contenha o nome da sua organização e compartilhado publicamente. Selecione os arquivos com um nome de arquivo que contenha o nome da sua organização e que estejam compartilhados publicamente.

* **Compartilhando com domínios externos** – receba um alerta sobre qualquer arquivo compartilhado com as contas pertencentes a domínios externos específicos. Por exemplo, arquivos compartilhados com o domínio de um concorrente. Selecione o domínio externo com o qual você deseja limitar o compartilhamento.

* **Arquivos compartilhados em quarentena não modificados durante o último período** – receba um alerta sobre arquivos compartilhados que ninguém modificou recentemente, para colocá-los em quarentena ou optar por ativar uma ação automatizada. Exclua todos os arquivos particulares que não foram modificados durante um intervalo de datas especificado. No G Suite, você pode optar por colocar esses arquivos em quarentena, usando a caixa de seleção ' arquivo de quarentena ' na página de criação de política.

* **Compartilhando com usuários não autorizados** – receba um alerta sobre os arquivos compartilhados com um grupo de usuários não autorizados em sua organização. Selecione os usuários para os quais o compartilhamento não é autorizado.

* **Extensão de arquivo confidencial** – receba um alerta sobre arquivos com extensões específicas com potencial de alta exposição. Selecione a extensão específica (por exemplo, crt para certificados) ou o nome do arquivo e exclua aqueles com o nível de compartilhamento privado.

## <a name="create-a-new-file-policy"></a>Criar uma política de arquivo

Para criar uma nova política de arquivos, siga este procedimento:

1. No console, clique em **Controlar** seguido por **Políticas**.

1. Clique em **criar política** e selecione política de **arquivo** .

1. Atribua um nome e uma descrição à sua política. Se desejar, poderá baseá-la em um modelo. Para obter mais informações sobre modelos de política, consulte [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md).

1. Forneça uma **Gravidade de política** à sua política. Se você configura o Cloud App Security para enviar notificações sobre correspondências de política para um nível de gravidade de política específico, esse nível é usado para determinar se essas correspondências disparam uma notificação.

1. Em **Categoria**, vincule a política ao tipo de risco mais apropriado. Este campo é somente informativo e ajuda você a pesquisar políticas e alertas específicos posteriormente, com base no tipo de risco.  O risco já pode estar pré-selecionado de acordo com a categoria para a qual você optou por criar a política. Por padrão, as políticas de arquivos são definidas para DLP.

1. **Crie um filtro para os arquivos em que esta política atuará** para definir quais aplicativos descobertos disparam essa política. Restrinja os filtros de política até chegar ao conjunto mais preciso de arquivos nos quais você deseja agir. Seja o mais restritivo possível para evitar falsos positivos. Por exemplo, se você quiser remover permissões públicas, lembre-se de adicionar o filtro **público** , se desejar remover um usuário externo, use o filtro "externo", etc.
   > [!NOTE]
   > Ao usar os filtros de política, **contém** pesquisa somente palavras inteiras: separadas por vírgulas, pontos, espaços ou sublinhados. Por exemplo, se você pesquisar **malware** ou **vírus**, ele localizará virus_malware_file.exe, mas não localizará malwarevirusfile.exe. Se você Pesquisar **malware.exe**, encontrará todos os arquivos com malware ou exe em seu nome de arquivo, enquanto se procurar por **"malware.exe"** (com as aspas), você encontrará apenas os arquivos que contêm exatamente "malware.exe". **É igual a** pesquisa apenas a cadeia de caracteres completa, por exemplo, se você pesquisar **malware.exe**, ele localizará malware.exe, mas não malware.exe.txt.
1. No primeiro filtro **Aplicar a**, selecione **todos os arquivos, excluindo pastas selecionadas** ou **pastas selecionadas** para Box, SharePoint, Dropbox, OneDrive, em que você pode aplicar a política a todas as políticas de arquivos a todos os arquivos no aplicativo ou a pastas específicas. Você é redirecionado a entrar no aplicativo de nuvem e, em seguida, adicionar as pastas relevantes.

1. No segundo filtro **Aplicar a**, selecione **todos os proprietários de arquivos**, **proprietários de arquivo de grupos de usuários selecionados** ou **todos os proprietários de arquivos, excluindo grupos selecionados**. Em seguida, selecione os grupos de usuários relevantes para determinar quais usuários e grupos devem ser incluídos na política.

1. Selecione o **Método de inspeção de conteúdo**. Você pode selecionar a [**DLP interna**](content-inspection-built-in.md) ou os [**Serviços de Classificação de Dados**](content-inspection.md). É recomendado usar os **Serviços de Classificação de Dados**.

    Depois que a inspeção for habilitada, você poderá optar por usar expressões predefinidas ou pesquisar outras expressões personalizadas.

    Além disso, você pode especificar uma expressão regular para excluir um arquivo dos resultados. Essa opção será muito útil se você tiver um padrão de palavra-chave de classificação interno que deseja excluir da política.

    Você pode definir o número mínimo de violações de conteúdo que deseja corresponder antes de o arquivo ser considerado uma violação. Por exemplo, você poderá escolher 10 se quiser ser alertado sobre arquivos com pelo menos 10 números de cartão de crédito encontrados em seu conteúdo.

    Quando o conteúdo é comparado com a expressão selecionada, o texto de violação é substituído por caracteres "X". Por padrão, as violações são mascaradas e mostradas em seu contexto, exibindo 100 caracteres antes e após a violação. Os números no contexto da expressão são substituídos por caracteres "#" e nunca são armazenados dentro de Cloud App Security. Você pode selecionar a opção para **Remover a máscara dos últimos quatro caracteres de uma violação** para remover a máscara dos últimos quatro caracteres da própria violação. É necessário definir quais tipos de dados a expressão regular pesquisa: conteúdo, metadados e/ou nome do arquivo. Por padrão, ela pesquisa o conteúdo e os metadados.

1. Escolha as ações de **Governança** que você deseja que o Cloud App Security realize quando uma correspondência for detectada.

1. Depois de criar sua política, você poderá exibi-la na guia **política de arquivo** . Você sempre pode editar uma política, calibrar seus filtros ou alterar as ações automatizadas. A política é habilitada automaticamente no momento da criação e inicia a verificação de seus arquivos de nuvem imediatamente.  Tenha muito cuidado ao definir as ações de controle, elas podem causar uma perda irreversível de permissões de acesso para seus arquivos. É recomendável restringir os filtros para representar exatamente os arquivos nos quais você deseja agir usando vários campos de pesquisa. Quanto mais restritos forem os filtros, melhor. Para obter diretrizes, você pode usar o botão **Editar e visualizar resultados** na seção Filtros.

    ![edição de política de arquivo e visualizar os resultados](media/file-policy-edit-and-preview-results.png)

1. Para exibir correspondências de política de arquivo, os arquivos com suspeita de violar a política, clique em **Controle** e **Políticas**. Filtre os resultados para exibir somente as políticas do arquivo usando o filtro **Tipo** na parte superior. Para obter mais informações sobre as correspondências para cada política, clique em uma política. Isso exibe os arquivos de "Correspondência agora" para a política. Clique na guia **Histórico** para ver um histórico de até seis meses anteriores de arquivos que correspondem à política.

## <a name="file-policy-reference"></a>Referência de política de arquivos

Esta seção fornece detalhes de referência sobre as políticas, fornecendo explicações sobre cada tipo de política e os campos que podem ser configurados para cada política.

Uma **Política de arquivos** é uma política baseada em API que permite que você controle o conteúdo da sua organização na nuvem, considerando mais de 20 filtros de metadados (incluindo o nível de compartilhamento e de proprietário) e resultados de inspeção de conteúdo. Com base nos resultados de política, as ações de governança podem ser aplicadas. O mecanismo de inspeção de conteúdo pode ser estendido por meio de mecanismos de DLP de terceiros, bem como soluções antimalware.

Cada política é composta pelas seguintes partes:

* **Filtros de arquivo** – permite que você crie condições granulares com base em metadados.

* **Inspeção de conteúdo** – permite que você restrinja a política, com base nos resultados do mecanismo de DLP. É possível incluir uma expressão personalizada ou uma expressão predefinida. As exclusões podem ser definidas, e é possível escolher o número de correspondências. Também é possível usar a anonimização para mascarar o nome de usuário.

* **Ações** – a política fornece um conjunto de ações de governança que podem ser aplicadas automaticamente quando violações são encontradas.  Essas ações são divididas em ações de colaboração, ações de segurança e ações de investigação.

* **Extensões** – a inspeção de conteúdo pode ser executada por meio de mecanismos de terceiros para funcionalidades aprimoradas de DLP ou antimalware.

## <a name="file-queries"></a>Consultas de arquivo

Para simplificar ainda mais a investigação, agora você pode criar consultas personalizadas e salvá-las para uso posterior.

1. Na página **arquivo** , use os filtros conforme descrito acima para fazer uma busca detalhada em seus aplicativos, conforme necessário.

1. Após concluir a criação da sua consulta, clique no botão **Salvar como** no canto superior direito dos filtros.

1. No pop-up **Salvar consulta** , nomeie sua consulta.

1. Para usar essa consulta novamente no futuro, em **Consultas**, role para baixo até **Consultas salvas** e selecione a consulta.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]

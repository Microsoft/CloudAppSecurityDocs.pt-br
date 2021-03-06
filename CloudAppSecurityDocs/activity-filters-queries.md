---
title: Trabalhando com consultas e filtros de atividades do Cloud App Security
description: Este artigo fornece uma lista de consultas e filtros de atividades do Cloud App Security e explica como trabalhar com eles.
ms.date: 12/10/2018
ms.topic: how-to
ms.openlocfilehash: f88d4f9fe4ef9906567a5408a58894bdacc6afd8
ms.sourcegitcommit: 72ddcd0f9a83251d588009abf506676612c50267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/13/2020
ms.locfileid: "97369847"
---
# <a name="activity-filters-and-queries"></a>Consultas e filtros de atividade

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Este artigo fornece descrições e instruções para consultas e filtros de atividades do Cloud App Security.

## <a name="activity-filters"></a>Filtros de atividade

Abaixo está uma lista de filtros de atividades que podem ser aplicados. A maioria dos filtros tem suporte para vários valores, embora NÃO forneça uma ferramenta avançada para a criação de políticas.

- ID da Atividade ‑ Pesquisa apenas atividades específicas por sua ID. Esse filtro é útil quando você conecta o Microsoft Cloud App Security ao SIEM (usando o agente SIEM) e deseja investigar ainda mais os alertas no portal do Cloud App Security.

- Objetos da atividade – Procura os objetos nos quais a atividade foi realizada. Este filtro se aplica ao arquivo, à pasta, ao usuário ou aos objetos do aplicativo.
  - ID de objeto de atividade – a ID do objeto (arquivo, pasta, usuário ou ID do aplicativo).
  <!-- - File, folder or site URL - Enables you to select files, folders and URLs that start with a specific string.-->
  <!-- - Target object (file/folder) - Enables you to select a specific file or folder. -->
  - Item – permite que você pesquise pelo nome ou ID de qualquer objeto de atividade (por exemplo: nomes de usuário, arquivos, parâmetros, sites). Para o filtro de **item de objeto de atividade** , você pode selecionar se deseja filtrar os itens que **contêm**, **iguais** ou **começam com** o item específico.

- Tipo de atividade — pesquise a atividade do aplicativo.

- Atividade administrativa – pesquisa apenas atividades administrativas.

- ID do alerta — pesquise por ID do alerta.

- Aplicativo – pesquisa apenas atividades em aplicativos específicos.

- Ação aplicada — pesquise pela ação de governança aplicada: Bloqueado, Ignorar proxy, Descriptografado, Criptografado, Falha de criptografia, Sem ação.

- Data – a data em que a atividade ocorreu. O filtro dá suporte a datas antes/depois e a um intervalo de datas.

<!--- Description – Specific keyword in the activity description, for example, all activities that include the string **user** in their description.  -->

- Marca do dispositivo – Pesquisar por **compatível com o Intune**, **ingressado no Azure ad híbrido** ou **certificado de cliente válido**.

- Tipo de dispositivo – Pesquisa apenas as atividades realizadas por meio de um tipo de dispositivo específico. Por exemplo, pesquise todas as atividades em dispositivos móveis, PCs ou tablets.

- Arquivos e pastas – pesquise arquivos e pastas nos quais a atividade foi executada.
  - ID do arquivo – permite que você pesquise pela ID do arquivo na qual a atividade foi executada.
  - Nome – filtros no nome de arquivos ou pastas. Será possível selecionar se o nome **terminar com**, **for igual a** ou **começar com** seu valor de pesquisa.
  - Arquivos ou pastas específicos – permite incluir ou excluir arquivos ou pastas específicos. Ao selecionar arquivos ou pastas, é possível filtrar a lista por **Aplicativo**, **Proprietário** ou **Nome do arquivo** parcial.

- Endereço IP – o endereço IP bruto, a categoria ou a marca do(a) qual a atividade foi executada.
  - Endereço IP bruto – Permite pesquisar atividades realizadas em ou por endereços IP brutos. Os IPs brutos podem ser iguais, não iguais, iniciar com ou não iniciar com uma sequência específica.
  - Categoria de IP – a categoria do endereço IP em que a atividade foi executada, por exemplo, todas as atividades do intervalo de endereços IP administrativo. As categorias precisam ser configuradas para incluir os endereços IP relevantes, exceto para a categoria "Arriscado", que é pré-configurada e inclui duas marcações de IP: proxy anônimo e Tor. Para saber como configurar as categorias de IP, consulte [Organizar os dados de acordo com suas necessidades](ip-tags.md).
  - Marca de IP ‑ A marca do endereço IP em que a atividade foi executada, por exemplo, todas as atividades de endereços IP de proxy anônimos. O Cloud App Security cria um conjunto de marcações internas de IP que não são configuráveis. Além disso, é possível configurar suas próprias marcas de IP. Para obter mais informações sobre como configurar as suas próprias marcações de IP, consulte [Organizar os dados de acordo com as suas necessidades](ip-tags.md).
  As marcações internas de IP incluem:
    - Aplicativos Microsoft (14 deles)
    - Proxy anônimo
    - Botnet (você verá que a atividade foi executada por um botnet com um link para saber mais sobre o botnet específico)
    - IP de verificação de Darknet
    - Servidor C&C de malware
    - Analisador de conectividade remota
    - Provedores satélite
    - Proxy inteligente e de acesso (deixados de fora de propósito)
    - Nós de saída do Tor
    - Zscaler

- Atividade representada – pesquisa somente atividades que foram realizadas no nome de outro usuário.

- Instância – a instância do aplicativo em que a atividade foi ou não foi executada.

- Local – o país/região do qual a atividade foi executada.

- Política correspondente – pesquisa atividades que corresponderam a uma política específica que foi definida no portal.

- ISP Registrado – o ISP do qual a atividade foi executada.

- Origem — pesquise pela origem na qual a atividade foi detectada. A origem pode ser um dos seguintes:
  - Conector de aplicativos-logs provenientes diretamente do conector de API do aplicativo.
  - Análise de conector de aplicativo — melhorias de segurança do Cloud App Security com base na verificação de informação do conector de API.

- Usuário — o usuário que executou a atividade, que pode ser filtrado no domínio, grupo, nome ou na organização. Para filtrar atividades sem usuário específico, você pode usar o operador ' não está definido '.
  - Domínio do usuário — pesquise um domínio de usuário específico.
  - Organização do usuário – A unidade organizacional do usuário que executou a atividade, por exemplo, todas as atividades realizadas pelos usuários de EMEA_marketing. Isso só é relevante para instâncias do Google Workspace conectadas usando unidades organizacionais.
  - Grupo de usuários – Grupos de usuários específicos que você pode importar de aplicativos conectados, por exemplo, administradores do Office 365.
  - Nome de usuário — pesquise por um nome de usuário específico. Para ver uma lista de usuários em um grupo de usuários específico, clique no nome do grupo de usuários na **Gaveta de atividade**. Clicar levará você à página de contas, que lista todos os usuários no grupo. Dali você pode analisar os detalhes das contas de usuários específicos do grupo.
  - Os filtros **Grupo de usuários** e **Nome de usuário** podem passar por filtragem adicional, usando o filtro **Como** e selecionando a função do usuário, que pode ser qualquer uma das seguintes:
    - Apenas objeto de atividade – isso significa que o usuário ou o grupo de usuários selecionado não realizou a atividade em questão; eles eram o objeto da atividade.
    - Apenas ator – isso significa que o usuário ou o grupo de usuários realizou a atividade.
    - Qualquer função – isso significa que o usuário ou o grupo de usuários foi envolvido na atividade, seja como a pessoa que realizou a atividade ou como o objeto da atividade.

- Agente do usuário – o agente do usuário do qual a atividade foi realizada.

- Marca de agente do usuário — marca de agente do usuário interna, por exemplo, todas as atividades de sistemas operacionais desatualizados ou navegador desatualizado.

<!--
>[!NOTE]
> If at any point you want to clear the filters, you can do so by clicking the clear filters icon ![clear filters icon](media/clear-filters.png). -->

## <a name="activity-queries"></a>Consultas de atividades

Para simplificar ainda mais a investigação, agora você pode criar consultas personalizadas e salvá-las para uso posterior.

1. Na página **Log de atividades**, use os filtros, conforme descrito acima, para fazer drill down em seus aplicativos, conforme necessário.

2. Após concluir a criação da sua consulta, clique no botão **Salvar como** no canto superior direito dos filtros.

3. No pop-up **Salvar consulta** , nomeie sua consulta.

   ![nova consulta](media/new-activity-query.png)

4. Para usar essa consulta novamente no futuro, em **Consultas**, role para baixo até **Consultas salvas** e selecione a consulta.

   ![abrir consulta](media/select-activity-query.png)

O Cloud App Security também fornece **Consultas sugeridas**. As consultas sugeridas fornecem caminhos de investigação recomendados que filtram as atividades. É possível editar essas consultas e salvá-las como consultas personalizadas. A seguir estão as consultas sugeridas opcionais:

- Atividades de administrador – filtra todas as atividades para exibir apenas as atividades que envolveram administradores.

- Baixar atividades – filtra todas as suas atividades para exibir somente as atividades que foram baixadas, incluindo baixar a lista de usuários como um arquivo. csv, baixar conteúdo compartilhado e baixar uma pasta.

- Logon com falha – filtra todas as suas atividades para exibir apenas os logons com falha e entrar com falha via SSO

- Atividades de arquivo e pasta – Filtra todas as atividades para exibir apenas as atividades que envolvem arquivos e pastas. O filtro inclui carregamento, download e acesso a pastas, além de criação, exclusão, carregamento, download, colocação em quarentena, acesso a arquivos e transferência de conteúdo.

- Atividades de representação – filtra todas as atividades para exibir apenas as atividades de representação.

- Atividades da caixa de correio – filtra todas as suas atividades para exibir somente atividades do Microsoft Exchange Online, como criar item, limpar mensagens da caixa de correio, atualizar mensagem e enviar mensagem usando as permissões Enviar como (representação).

- Alterações de senha e solicitações e redefinição – Filtra todas as atividades para exibir apenas as atividades que envolvem redefinição de senha, alteração de senha e forçar o usuário a alterar a senha na entrada seguinte.

- Riscos de segurança – filtra todas as atividades para exibir apenas as atividades que correspondem às políticas DLP.

- Atividades de compartilhamento – filtra todas as atividades para exibir apenas as atividades que envolvem compartilhamento pastas e arquivos, incluindo a criação de um vínculo da empresa, criação de um vínculo anônimo e concessão de permissões de leitura/gravação.

- Logon bem-sucedido – filtra todas as suas atividades para exibir somente as atividades que envolvem logons bem-sucedidos, incluindo a ação de representar, representar o logon, o logon único e o logon por meio de um novo dispositivo.

![consultar atividades](media/queries-activity.png)

Além disso, use as consultas sugeridas como um ponto de partida para uma nova consulta. Primeiro, selecione uma das consultas sugeridas. Em seguida, faça as alterações necessárias e, por fim, clique em **Salvar como** para criar uma nova **Consulta salva**.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)

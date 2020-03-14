---
title: Trabalhando com filtros de atividade Cloud App Security e consultas
description: Este artigo fornece uma lista de Cloud App Security de filtros de atividade e consultas e explica como trabalhar com eles.
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
ms.openlocfilehash: f37fab4f9d611577deecb4884838431144f1647d
ms.sourcegitcommit: 4f3883a9e85d0aaf2802b10433b221c3f1838d88
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79285270"
---
# <a name="activity-filters-and-queries"></a>Consultas e filtros de atividade

*Aplica-se a: Microsoft Cloud App Security*

Este artigo fornece descrições e instruções para Cloud App Security filtros de atividade e consultas.

## <a name="activity-filters"></a>Filtros de atividade

Abaixo está uma lista de filtros de atividades que podem ser aplicados. A maioria dos filtros dá suporte a vários valores, além de não fornecer uma ferramenta poderosa para a criação de políticas.

- ID da Atividade ‑ Pesquisa apenas atividades específicas por sua ID. Esse filtro é útil quando você se conecta Microsoft Cloud App Security ao SIEM (usando o agente SIEM) e deseja investigar ainda mais os alertas no portal de Cloud App Security.

- Objetos de atividade – pesquise os objetos em que a atividade foi feita. Esse filtro se aplica a objetos de arquivo, pasta, usuário ou aplicativo.
  - ID do objeto de atividade-a ID do objeto (arquivo, pasta, usuário ou ID do aplicativo).
  <!-- - File, folder or site URL - Enables you to select files, folders and URLs that start with a specific string.-->
  <!-- - Target object (file/folder) - Enables you to select a specific file or folder. -->
  - Item – permite que você pesquise pelo nome ou ID de qualquer objeto de atividade (por exemplo: nomes de usuário, arquivos, parâmetros, sites). Para o filtro de **item de objeto de atividade** , você pode selecionar se deseja filtrar os itens que **contêm**, **iguais**ou **começam com** o item específico.

- Tipo de atividade — pesquise a atividade do aplicativo.

- Atividade administrativa – pesquisa apenas atividades administrativas.

- ID do alerta — pesquise por ID do alerta.

- Aplicativo – pesquisa apenas atividades em aplicativos específicos.

- Ação aplicada — pesquise pela ação de governança aplicada: Bloqueado, Ignorar proxy, Descriptografado, Criptografado, Falha de criptografia, Sem ação.

- Data – a data em que a atividade ocorreu. O filtro dá suporte a datas antes/depois e um intervalo de datas.

<!--- Description – Specific keyword in the activity description, for example, all activities that include the string **user** in their description.  -->

- Marca do dispositivo — pesquise por dispositivo compatível, gerenciado ou verificado.

- Tipo de dispositivo – pesquise apenas atividades que foram feitas usando um tipo de dispositivo específico. Por exemplo, pesquise todas as atividades de dispositivos móveis, PCs ou Tablets.

- Arquivos e pastas-Procure arquivos e pastas em que a atividade foi executada.
  - ID do arquivo – permite pesquisar pela ID do arquivo na qual a atividade foi executada.
  - Nome-filtra no nome de arquivos ou pastas. Você pode selecionar se o nome **termina com**, **é igual**a ou **começa com** seu valor de pesquisa.
  - Arquivos ou pastas específicos – permite que você inclua ou exclua arquivos ou pastas específicas. Ao selecionar arquivos ou pastas, você pode filtrar a lista por **aplicativo**, **proprietário**ou nome de **arquivo**parcial.

- Endereço IP – o endereço IP bruto, a categoria ou a marca da qual a atividade foi executada.
  - Endereço IP bruto – permite pesquisar atividades que foram executadas em ou por endereços IP brutos. Os IPs brutos podem ser iguais, não iguais, começam com ou não começam com uma sequência específica.
  - Categoria de IP – a categoria do endereço IP em que a atividade foi executada, por exemplo, todas as atividades do intervalo de endereços IP administrativo. As categorias precisam ser configuradas para incluir os endereços IP relevantes, exceto para a categoria "arriscada", que é pré-configurada e inclui duas marcas de IP – proxy anônimo e Tor. Para saber como configurar as categorias de IP, consulte [Organizar os dados de acordo com suas necessidades](ip-tags.md).
  - Marca de IP ‑ A marca do endereço IP em que a atividade foi executada, por exemplo, todas as atividades de endereços IP de proxy anônimos. Cloud App Security cria um conjunto de marcas de IP internas que não são configuráveis. Além disso, você pode configurar suas próprias marcas de IP. Para obter mais informações sobre como configurar as suas próprias marcações de IP, consulte [Organizar os dados de acordo com as suas necessidades](ip-tags.md).
  As marcações internas de IP incluem:
    - Aplicativos Microsoft (14 deles)
    - Proxy anônimo
    - Botnet (você verá que a atividade foi executada por um botnet com um link para saber mais sobre a botnet específica)
    - IP de verificação de Darknet
    - Servidor C&C de malware
    - Analisador de conectividade remota
    - Provedores satélite
    - Proxy inteligente e de acesso (deixados de fora de propósito)
    - Nós de saída do Tor
    - Zscaler

- Atividade representada – pesquisa somente atividades que foram realizadas no nome de outro usuário.

- Instância-a instância do aplicativo em que a atividade foi ou não foi executada.

- Local – o país do qual a atividade foi executada.

- Política correspondente – pesquisa atividades que corresponderam a uma política específica que foi definida no portal.

- ISP Registrado – o ISP do qual a atividade foi executada.

- Origem — pesquise pela origem na qual a atividade foi detectada. A origem pode ser um dos seguintes:
  - Conector de aplicativo — logs provenientes diretamente do conector de API do aplicativo.
  - Análise de conector de aplicativo — melhorias de segurança do Cloud App Security com base na verificação de informação do conector de API.

- Usuário – o usuário que realizou a atividade, que pode ser filtrado em domínio, grupo, nome ou organização. Para filtrar atividades sem nenhum usuário específico, você pode usar o operador 'não está definido'.
  - Domínio do usuário — pesquise um domínio de usuário específico.
  - Organização do usuário – A unidade organizacional do usuário que executou a atividade, por exemplo, todas as atividades realizadas pelos usuários de EMEA_marketing. Isso só é relevante para instâncias conectadas do G Suite usando unidades organizacionais.
  - Grupo de usuários – Grupos de usuários específicos que você pode importar de aplicativos conectados, por exemplo, administradores do Office 365.
  - Nome de usuário — pesquise por um nome de usuário específico. Para ver uma lista de usuários em um grupo de usuários específico, clique no nome do grupo de usuários na **Gaveta de atividade**. Ao clicar, você será levado para a página contas que lista todos os usuários no grupo. A partir daí, você pode fazer uma busca detalhada dos detalhes das contas de usuários específicos no grupo.
  - Os filtros **Grupo de usuários** e **Nome de usuário** podem passar por filtragem adicional, usando o filtro **Como** e selecionando a função do usuário, que pode ser qualquer uma das seguintes:
    - Somente objeto de atividade-o que significa que o usuário ou grupo de usuários selecionado não executou a atividade em questão, ele era o objeto da atividade.
    - Somente ator-significando que o usuário ou grupo de usuários realizou a atividade.
    - Qualquer função – que significa que o usuário ou grupo de usuários estava envolvido na atividade, seja como a pessoa que realizou a atividade ou como o objeto da atividade.

- Agente do usuário – o agente do usuário do qual a atividade foi realizada.

- Marca de agente do usuário — marca de agente do usuário interna, por exemplo, todas as atividades de sistemas operacionais desatualizados ou navegador desatualizado.

<!--
>[!NOTE]
> If at any point you want to clear the filters, you can do so by clicking the clear filters icon ![clear filters icon](media/clear-filters.png). -->

## <a name="activity-queries"></a>Consultas de atividade

Para tornar a investigação ainda mais simples, agora você pode criar consultas personalizadas e salvá-las para uso posterior.

1. Na página **log de atividades** , use os filtros conforme descrito acima para fazer uma busca detalhada em seus aplicativos, conforme necessário.

2. Depois de concluir a criação da consulta, clique no botão **salvar como** no canto superior direito dos filtros.

3. No pop-up **Salvar consulta** , nomeie sua consulta.

   ![nova consulta](media/new-activity-query.png)

4. Para usar essa consulta novamente no futuro, em **consultas**, role para baixo até **consultas salvas** e selecione sua consulta.

   ![Abrir consulta](media/select-activity-query.png)

Cloud App Security também fornece **consultas sugeridas**. As consultas sugeridas fornecem a você as avenidas recomendadas de investigação que filtram suas atividades. Você pode editar essas consultas e salvar as consultas do as personalizadas. Veja a seguir as consultas sugeridas opcionais:

- Atividades de administração – filtra todas as suas atividades para exibir somente as atividades que envolveram administradores.

- Baixar atividades – filtra todas as suas atividades para exibir somente as atividades que foram baixadas, incluindo baixar a lista de usuários como um. csv Vile, baixando o conteúdo compartilhado e baixando uma pasta.

- Logon com falha – filtra todas as suas atividades para exibir apenas os logons com falha e entrar com falha via SSO

- Atividades de arquivo e pasta – filtra todas as suas atividades para exibir somente as atividades que envolvem arquivos e pastas. O filtro inclui carregar, baixar e acessar pastas, juntamente com a criação, a exclusão, o carregamento, o download, a quarentena e o acesso a arquivos e a transferência de conteúdo.

- Atividades de representação – filtra todas as suas atividades para exibir apenas as atividades de representação.

- Atividades da caixa de correio – filtra todas as suas atividades para exibir somente atividades do Microsoft Exchange Online, como criar item, limpar mensagens da caixa de correio, atualizar mensagem e enviar mensagem usando as permissões Enviar como (representação).

- Solicitações de alteração e redefinição de senha – filtra todas as suas atividades para exibir somente as atividades que envolvem a redefinição de senha, alterar senha e forçar o usuário a alterar a senha na próxima entrada.

- Riscos de segurança – filtra todas as suas atividades para exibir somente as atividades que correspondem às políticas de DLP.

- Compartilhando atividades – filtra todas as suas atividades para exibir somente as atividades que envolvem o compartilhamento de pastas e arquivos, incluindo a criação de um link da empresa, a criação de um link anônimo e a concessão de permissões de leitura/gravação.

- Logon bem-sucedido – filtra todas as suas atividades para exibir somente as atividades que envolvem logons bem-sucedidos, incluindo a ação de representar, representar o logon, o logon único e o logon do novo dispositivo.

![atividades de consulta](media/queries-activity.png)

Além disso, você pode usar as consultas sugeridas como um ponto de partida para uma nova consulta. Primeiro, selecione uma das consultas sugeridas. Em seguida, faça as alterações conforme necessário e, por fim, clique em **salvar como** para criar uma nova **consulta salva**.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)

---
title: Visibilidade das atividades dos aplicativos de nuvem | Microsoft Docs
description: "Este tópico fornece uma lista de atividades, filtros e parâmetros de correspondência que podem ser aplicados às políticas de atividade."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 9/24/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: f3af2d25-9286-4e9b-b2ad-35653bec72ff
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 835ffc05fb84117bf9bbf848d5718de4557e5e15
ms.sourcegitcommit: 8759541301241e03784c5ac87b56986f22bd0561
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/28/2017
---
# <a name="activities"></a>Atividades
O Cloud App Security proporciona visibilidade de todas as atividades de seus aplicativos conectados. Depois de conectar o Cloud App Security a um aplicativo usando o Conector de aplicativos, o Cloud App Security examina todas as atividades que ocorreram – o período de tempo de verificação retroativo é diferente de acordo com o aplicativo – e, em seguida, ele é constantemente atualizado com novas atividades. 

> [!NOTE] 
> Para obter uma lista completa de atividades do Office 365 monitoradas pelo Cloud App Security, veja [Pesquisar o log de auditoria no Centro de Conformidade e Segurança do Office 365](https://support.office.com/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c?ui=en-US&rs=en-US&ad=US#ID0EABAAA=Audited_activities)

O **Log de atividades** pode ser filtrado para permitir que você encontre atividades específicas. É possível criar políticas com base nas atividades e, em seguida, definir sobre o que você deseja ser alertado e agir. Também é possível pesquisar atividades executadas em determinados arquivos. O tipo de atividades e as informações que recebemos para cada atividade dependem do aplicativo e do tipo de dados que ele pode fornecer. 

Por exemplo, é possível usar o **Log de atividades** para encontrar usuários na sua organização que estejam usando sistemas operacionais ou navegadores desatualizados da seguinte maneira: depois de conectar um aplicativo ao Cloud App Security, na página **Log de atividades**, use o filtro avançado e selecione **Marcação do agente do usuário**. Em seguida, selecione **Navegador desatualizado** ou **Sistema operacional desatualizado**.

 ![Exemplo de navegador desatualizado de atividade](media/activity-example-outdated.png)

Se desejar verificar se existem arquivos **confidenciais** acessados fora da sua organização, defina o filtro **Objeto de atividade** para pesquisar **Rótulo de classificação** e selecione o rótulo **confidencial**. Defina o filtro **Endereço IP** para pesquisar a **Categoria** e exclua os endereços IP do Office (as categorias IP podem ser configuradas no menu **Configurações**). Você pode clicar em **Nova política de pesquisa** para criar uma política de atividade com base nos filtros definidos e notificar automaticamente os usuários.

 ![Exemplo externo de arquivos confidenciais de atividade](media/activity-example-ip.png)

 
O filtro básico fornece excelentes ferramentas para começar a usar a filtragem de suas atividades.

 ![filtro básico do log de atividades](media/activity-log-filter-basic.png)

Para analisar atividades mais específicas, você pode expandir o filtro básico clicando em Avançado.

 ![filtro avançado do log de atividades](media/activity-log-filter-advanced.png)

## <a name="activity-filters"></a>Filtros de atividade
Veja a seguir uma lista de filtros de atividades que podem ser aplicados. A maioria dos filtros dá suporte a vários valores, bem como NOT, para fornecer uma ferramenta poderosa para a criação de políticas.  
  
-   ID da Atividade ‑ Pesquisa apenas atividades específicas por sua ID. Esse filtro é útil quando você conecta o Cloud App Security ao SIEM (usando o agente SIEM) e deseja investigar ainda mais os alertas no portal do Cloud App Security.  
  
-   Objetos de atividade – pesquise os objetos nos quais a atividade foi executada. Este filtro se aplica ao arquivo, à pasta, ao usuário ou aos objetos do aplicativo. 
    - ID de objeto de atividade – a ID do objeto (arquivo, pasta, usuário ou ID do aplicativo).
    - Arquivo, pasta ou URL de site — permite que você selecione arquivos, pastas e URLs que começam com uma cadeia de caracteres específica.
    - Objeto de destino (arquivo/pasta) — permite que você selecione uma pasta ou um arquivo específico. 
    - Item – permite que você pesquise pelo nome ou ID de qualquer objeto de atividade (por exemplo: nomes de usuário, arquivos, parâmetros, sites). Para o filtro **Item do objeto da atividade**, você pode selecionar se deseja filtrar os itens por **Contém**, **Igual** ou **Começa com** o item específico.
    
-   Tipo de atividade — pesquise a atividade do aplicativo.

-   Atividade administrativa – pesquisa apenas atividades administrativas.  
  
-   ID do alerta — pesquise por ID do alerta.

-   Aplicativo – pesquisa apenas atividades em aplicativos específicos.  
  
-   Ação aplicada — pesquise pela ação de governança aplicada: Bloqueado, Ignorar proxy, Descriptografado, Criptografado, Falha de criptografia, Sem ação.

-   Data – a data em que a atividade ocorreu. O filtro dá suporte a datas antes/depois, bem como a intervalo de datas.  
  
-   Descrição – palavra-chave específica na descrição da atividade, por exemplo, todas as atividades que incluem a cadeia de caracteres **usuário** em sua descrição.  
  
-   Marca do dispositivo — pesquise por dispositivo compatível, gerenciado ou verificado.

-   Tipo de dispositivo — pesquise apenas as atividades executadas usando um tipo de dispositivo específico, por exemplo, todas as atividades de dispositivos móveis, PCs ou tablets.  
  
-   Endereço IP – o endereço IP bruto, a categoria ou a marca do(a) qual a atividade foi executada.  
    - Endereço IP bruto — permite que você pesquise as atividades que foram realizadas nos endereços IP brutos, ou por eles, que sejam iguais, diferentes, comecem com ou não comecem com uma sequência específica, ou endereços IP brutos que estão ou não estão definidos. 
    - Categoria de IP – a categoria do endereço IP em que a atividade foi executada, por exemplo, todas as atividades do intervalo de endereços IP administrativo. As categorias precisam ser configuradas para incluir os endereços IP relevantes, exceto para a categoria "Arriscado", que é pré-configurada e inclui duas marcações de IP: proxy anônimo e Tor. Para saber como configurar as categorias de IP, consulte [Organizar os dados de acordo com suas necessidades](ip-tags.md).  
    - Marca de IP ‑ A marca do endereço IP em que a atividade foi executada, por exemplo, todas as atividades de endereços IP de proxy anônimos. O Cloud App Security cria um conjunto de marcações internas de IP que não são configuráveis. Além disso, você pode configurar suas próprias marcações de IP. Para obter mais informações sobre como configurar as suas próprias marcações de IP, consulte [Organizar os dados de acordo com as suas necessidades](ip-tags.md).
   As marcações internas de IP incluem:
    - Aplicativos Microsoft (14 deles)
    - Proxy anônimo
    - Botnet (você vê que a atividade foi executada por um botnet com um link para saber mais sobre o botnet específico)
    - IP de verificação de Darknet
    - Servidor C&C de malware
    - Analisador de conectividade remota
    - Provedores satélite
    - Proxy inteligente e de acesso (deixados de fora de propósito)
    - Nós de saída do Tor
    - Zscaler


-   Atividade representada – pesquisa somente atividades que foram realizadas no nome de outro usuário.  

-   Local – o país do qual a atividade foi executada.  

-   Política correspondente – pesquisa atividades que corresponderam a uma política específica que foi definida no portal.  

-   ISP Registrado – o ISP do qual a atividade foi executada.   

-  Origem — pesquise pela origem na qual a atividade foi detectada. Pode ter uma das seguintes origens:
  - Conector de aplicativo — logs provenientes diretamente do conector de API do aplicativo.
  - Análise de conector de aplicativo — melhorias de segurança do Cloud App Security com base na verificação de informação do conector de API.
  

-   Usuário — o usuário que executou a atividade, que pode ser filtrado no domínio, grupo, nome ou na organização. Para filtrar atividades sem nenhum usuário específico, você pode usar o operador 'não está definido'.  
    -   Domínio do usuário — pesquise um domínio de usuário específico.
    -   Organização do usuário – A unidade organizacional do usuário que executou a atividade, por exemplo, todas as atividades realizadas pelos usuários de EMEA_marketing.  
    -   Grupo de usuários – Grupos de usuários específicos que você pode importar de aplicativos conectados, por exemplo, administradores do Office 365.  
    -   Nome de usuário — pesquise por um nome de usuário específico. Para ver uma lista de usuários em um grupo de usuários específico, clique no nome do grupo de usuários na **Gaveta de atividade**. Isso leva você até a página de Contas, que lista todos os usuários no grupo. Dali você pode analisar os detalhes das contas de usuários específicos do grupo.
       -  Os filtros **Grupo de usuários** e **Nome de usuário** podem passar por filtragem adicional, usando o filtro **Como** e selecionando a função do usuário, que pode ser qualquer uma das seguintes:
            - Apenas objeto de atividade – isso significa que o usuário ou o grupo de usuários selecionado não executou a atividade em questão, eles eram o objeto da atividade
            - Apenas ator – isso significa que o usuário ou o grupo de usuários realizou a atividade
            - Qualquer função – isso significa que o usuário ou o grupo de usuários foi envolvido na atividade, seja como a pessoa que realizou a atividade ou como o objeto da atividade

-   Agente do usuário – o agente do usuário do qual a atividade foi realizada.  
  
-   Marca de agente do usuário — marca de agente do usuário interna, por exemplo, todas as atividades de sistemas operacionais desatualizados ou navegador desatualizado.  
    
>[!NOTE]
> Se em algum momento você desejar limpar os filtros, poderá fazê-lo ao clicar no ícone ![Limpar filtros](./media/clear-filters.png).

## <a name="the-activity-drawer"></a>A gaveta de atividades

### <a name="working-with-the-activity-drawer"></a>Trabalhando com a gaveta Atividade

Você pode exibir mais informações sobre cada atividade clicando na própria atividade no log de atividades. Isso abre a Gaveta de atividades, que fornece as seguintes ações adicionais e informações para cada atividade:
    - Políticas correspondentes: clique no link Políticas correspondentes para ver uma lista de políticas nessa atividade correspondente.
    - Exibir dados brutos: clique em Exibir dados brutos para ver os dados reais que foram recebidos do aplicativo.
    - Usuário: clique no usuário para exibir a página do usuário que executou a atividade. 
    - Tipo de dispositivo: clique no tipo de dispositivo para exibir os dados brutos do agente do usuário. 
    - Local: clique no local para exibir o local no Bing Mapas.
    - Marcas e categoria de endereço IP: clique na marca de IP para exibir a lista de marcas de IP encontradas nessa atividade. Em seguida, você pode filtrar por todas as atividades correspondentes nessa marca.    

 Os campos na gaveta Atividade fornecem links contextuais para atividades adicionais e análises detalhadas que você talvez queira executar diretamente na gaveta. Por exemplo, se você mover o cursor para próximo da categoria de endereço IP, pode usar o ícone para adicionar filtro ![adicionar filtro](./media/add-to-filter-icon.png) para adicionar o endereço IP imediatamente ao filtro da página atual. Você também pode usar o ícone de engrenagem de configurações ![ícone de configurações](./media/contextual-settings-icon.png) que aparece diretamente na página de configurações necessária para alterar a configuração de um dos campos, tais como **Grupos de usuários**.


![gaveta de atividades](./media/activity-drawer.png "gaveta de atividades")  
  
Para obter uma lista das ações de governança disponíveis, consulte [Ações de governança de atividade](governance-actions.md#activity-governance-actions).

#### <a name="user-insights"></a>Informações de usuário

A experiência de investigação inclui informações prontas sobre o usuário em ação. Com um único clique, você pode obter uma visão abrangente do usuário, incluindo por meio de qual local ele se conectou, com quantos alertas em aberto ele está envolvido e suas informações de metadados.

Para exibir informações de usuário:

1. Clique na atividade em si no **Log de atividades**.

2. Em seguida, clique na guia **Usuário**. <br></br> Isso abre a Gaveta de atividades. A guia **Usuário** fornece as seguintes informações sobre o usuário:
    - **Abrir alertas**: o número de alertas abertos envolvendo o usuário.
    - **Violação de arquivo**: o número de violações de arquivo para arquivos pertencentes ao usuário.
    - **Atividades**: o número de atividades executadas pelo usuário nos últimos 30 dias.
    - **Países**: o número de países dos quais o usuário se conectou nos últimos 30 dias.
    - **ISPs**: o número de ISPs dos quais o usuário se conectou nos últimos 30 dias.
    - **Endereços IP**: o número de endereços IP dos quais o usuário se conectou nos últimos 30 dias.

![informações do usuário no Cloud App Security](./media/user-insights.png)

#### <a name="ip-address-insights"></a>Informações sobre endereço IP

Como as informações de endereço IP são cruciais para quase todas as investigações, você pode exibir informações detalhadas sobre endereços IP na Gaveta de atividades. De dentro de uma atividade específica, você pode clicar na guia de endereço IP para exibir os dados consolidados sobre o endereço IP, incluindo o número de alertas abertos para o endereço IP específico, um gráfico de tendência de atividade recente e um mapa do local. Isso permite o fácil detalhamento, por exemplo, quando estiver investigando alertas de viagem impossíveis, você pode compreender facilmente onde o endereço IP foi usado e se ele foi envolvido em atividades suspeitas ou não. Você também pode executar ações diretamente na gaveta do endereço IP que permite que você marque um endereço IP como arriscado, VPN ou corporativo para facilitar a criação de políticas e a futura investigação.

Para exibir as informações sobre endereço IP:

1. Clique na atividade em si no **Log de atividades**.

2. Em seguida, clique na guia **Endereço IP**. <br></br> Isso abre a guia **Endereço IP** da Gaveta de atividades e fornece as seguintes informações sobre o endereço IP:
    - **Abrir alertas**: o número de alertas abertos envolvendo o endereço IP.
    - **Atividades**: o número de atividades executadas pelo endereço IP nos últimos 30 dias.
    - **Localização do IP**: as localizações geográficas a partir das quais o endereço IP foi conectado nos últimos 30 dias.
    - **Atividades**: o número de atividades executadas a partir do endereço IP nos últimos 30 dias.
    - **Atividades administrativas**: o número de atividades administrativas executadas a partir do endereço IP nos últimos 30 dias.
    - Você pode executar as seguintes ações de endereço IP:
        - Marcar como arriscado 
        - Marcar como endereço IP de VPN
        - Marcar como IP arriscado e adicionar ao grupo bloqueado

![Informações do endereço IP no Cloud App Security](./media/ip-address-insights.png)


## <a name="see-also"></a>Veja também  
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
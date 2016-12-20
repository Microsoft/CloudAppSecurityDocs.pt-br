---
title: Atividades | Microsoft Docs
description: "Este tópico fornece uma lista de atividades, filtros e parâmetros de correspondência que podem ser aplicados às políticas de atividade."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/26/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: f3af2d25-9286-4e9b-b2ad-35653bec72ff
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 52f2245779568abbf41d47c4b45cdcced302529b
ms.openlocfilehash: 40fd28f568aa9af32f9e2399435f48372ea62413


---
# <a name="activities"></a>Atividades
O log de atividades pode ser filtrado para permitir que você encontre atividades específicas. O filtro básico fornece excelentes ferramentas para começar a usar a filtragem de suas atividades.

 ![filtro básico do log de atividades](media/activity-log-filter-basic.png)

Para analisar atividades mais específicas, você pode expandir o filtro básico clicando em Avançado.

 ![filtro avançado do log de atividades](media/activity-log-filter-advanced.png)

## <a name="activity-filters"></a>Filtros de atividade
Abaixo está uma lista de filtros de atividades que podem ser aplicados. A maioria dos filtros dá suporte a vários valores, bem como NOT, para fornecer uma ferramenta muito poderosa para a criação de políticas.  
  
-   ID da Atividade ‑ Pesquisa apenas atividades específicas por sua ID. Esse filtro é muito útil quando você conecta MCAS ao seu SIEM (usando o agente SIEM) e deseja investigar ainda mais os alertas no portal do MCAS.  
  
-   Objetos de atividade — procure arquivos, pastas ou URLs de site, ou objetos de destino (arquivo/pasta).
    - Arquivo, pasta ou URL de site — permite que você selecione arquivos, pastas e URLs que começam com uma cadeia de caracteres específica.
    - Objeto de destino (arquivo/pasta) — permite que você selecione uma pasta ou um arquivo específico. 
    
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
    - Categoria de IP – a categoria do endereço IP em que a atividade foi executada, por exemplo, todas as atividades do intervalo de endereços IP administrativo. Para obter mais informações sobre categorias de IP, consulte [Organizar os dados de acordo com suas necessidades](general-setup.md#IPtagsandRanges).  
    - Marca de IP ‑ A marca do endereço IP em que a atividade foi executada, por exemplo, todas as atividades de endereços IP de proxy anônimos. Para obter mais informações sobre marcas de IP, consulte [Organizar os dados de acordo com suas necessidades](general-setup.md#IPtagsandRanges).
  
-   Atividade representada – pesquisa somente atividades que foram realizadas no nome de outro usuário.  

-   Local – o país do qual a atividade foi executada.  

-   Política correspondente – pesquisa atividades que corresponderam a uma política específica que foi definida no portal.  

-   ISP Registrado – o ISP do qual a atividade foi executada.   

-  Origem — pesquise pela origem na qual a atividade foi detectada. A origem pode ser um dos seguintes:
  - Conector de aplicativo — logs provenientes diretamente do conector de API do aplicativo.
  - Análise de conector de aplicativo — melhorias de segurança do Cloud App Security com base na verificação de informação do conector de API.
  

-   Usuário — o usuário que executou a atividade, que pode ser filtrado no domínio, grupo, nome ou na organização. Para filtrar atividades sem nenhum usuário específico, você pode usar o operador 'não está definido'.  
    -   Domínio do usuário — pesquise um domínio de usuário específico.
    -   Grupo de usuários — grupos de usuários específicos que são importados automaticamente pelo Cloud App Security do aplicativo de nuvem, por exemplo, todas as atividades realizadas por administradores do Office 365.
    -   Nome de usuário — pesquise por um nome de usuário específico.
    -   Organização do usuário – A unidade organizacional do usuário que executou a atividade, por exemplo, todas as atividades realizadas pelos usuários de EMEA_marketing.  

-   Agente do usuário – o agente do usuário do qual a atividade foi realizada.  
  
-   Marca de agente do usuário — marca de agente do usuário interna, por exemplo, todas as atividades de sistemas operacionais desatualizados ou navegador desatualizado.  
    
  
## <a name="working-with-the-activity-drawer"></a>Trabalhando com a gaveta Atividade

Você pode exibir mais informações sobre cada atividade clicando na própria atividade no log de atividades. Isso abre a gaveta Atividade, que fornece as seguintes ações adicionais que você pode executar no arquivo:

- Políticas correspondentes: clique no link Políticas correspondentes para ver uma lista de políticas nessa atividade correspondente.
- Exibir dados brutos: clique em Exibir dados brutos para ver os dados reais que foram recebidos do aplicativo.
- Usuário: clique no usuário para exibir a página do usuário que executou a atividade. 
- Tipo de dispositivo: clique no tipo de dispositivo para exibir os dados brutos do agente do usuário. 
- Local: clique no local para exibir o local no Bing Mapas.
- Marcas e categoria de endereço IP: clique na marca de IP para exibir a lista de marcas de IP encontradas nessa atividade. Em seguida, você pode filtrar por todas as atividades correspondentes nessa marca.    

![gaveta atividade](./media/activity-drawer.png "activity drawer")  
  
Para obter uma lista de ações de governança disponíveis, consulte [Parâmetros de correspondência de atividade](governance-actions.md#activity-match-parameters).


## <a name="see-also"></a>Veja também  
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Dec16_HO1-->



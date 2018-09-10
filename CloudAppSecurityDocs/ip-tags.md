---
title: Definir intervalos de IP e marcas | Microsoft Docs
description: Este tópico fornece instruções sobre como trabalhar com marcas IP e categorias IP.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/22/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: bbf54f66-4ce2-428c-afc8-b5a64277014f
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: a25a8aff6a945e8500405a23fca4e55150c114af
ms.sourcegitcommit: 0ac08ca7b3140b79f1d36ff7152476c188fa12b3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44144356"
---
*Aplica-se ao: Microsoft Cloud App Security*
 
 
#  <a name="IPtagsandRanges"></a> Trabalhando com marcações e intervalos de IP

Para identificar facilmente endereços IP conhecidos, como os endereços IP do escritório físico, é necessário definir intervalos de endereço IP, o que permite que você marque e categorize apropriadamente e personalize a forma como os logs e alertas são exibidos e investigados. <br></br>  
Cada grupo de intervalos de IP pode ser categorizado com base em uma lista predefinida de categorias de IP ou marcado com suas próprias marcas de IP criadas. Além disso, essa configuração permite que você substitua as informações de geolocalização com base no seu conhecimento de rede interno.  
  
Há suporte para IPv4 e IPv6.  
  
O Cloud App Security é pré-configurado com intervalos de IP internos de provedores de nuvem populares, como o Azure e o Office 365. Além disso, temos marcação interna baseada na inteligência contra ameaças da Microsoft, que inclui proxy anônimo, Botnet e Tor. É possível ver a lista suspensa completa na página de intervalos de endereços IP.

Para usar essas marcações internas como parte de uma pesquisa, consulte a ID na documentação da API do Cloud App Security. 

> [!NOTE]
> Você pode adicionar intervalos IP em massa por meio da criação de um script com a **API de intervalos de endereços IP**, que está localizada na barra de menus do portal do Cloud App Security. Para isso, basta clicar no ponto de interrogação e em **Documentação da API**.


Marcas de endereço IP internas e marcas de IP personalizadas são consideradas hierarquicamente, com marcas de IP personalizadas, tendo precedência sobre as marcas de IP internas. Por exemplo, se um endereço IP estiver marcado como **Arriscado** com base na inteligência de ameaças, mas houver uma marca IP personalizada que o identifica como **Corporativo**, as marcas e a categoria personalizada terão precedência.

Na barra de menus, clique no ícone de configurações ![ícone de configurações](./media/settings-icon.png "ícone de configurações") e selecione **Intervalos de Endereços IP**. Clique no sinal de adição para adicionar intervalos de endereços IP e defina os seguintes campos:  
  
> [!NOTE]  
> - O local e o ISP registrado substituem os padrões.   
> - No entanto, as marcas de IP são adicionadas à atividade sem substituir os dados.  
  
1.  Atribua um **Nome** ao seu intervalo de IP. O nome não aparece no log de atividades, ele é usado apenas para gerenciar o intervalo de IP.  
  
     Para incluir o intervalo de IP em uma categoria de IP, selecione uma categoria no menu suspenso.  
  
2.  Insira o **Intervalo de endereços IP** que você deseja configurar e clique no botão "+". Você pode adicionar quantos endereços IP e sub-redes desejar usando a notação de prefixo de rede (também conhecida como notação CIDR), por exemplo, 192.168.1.0/32.  
  
3.  Use as **Categorias** para reconhecer facilmente as atividades de endereços IP interessantes. As categorias estão disponíveis no portal, embora precisem de configuração do usuário para determinar quais endereços IP estão incluídos em cada categoria, exceto para a categoria “Arriscados”, que inclui duas marcas de IP: proxy anônimo e Tor.  
  
     As seguintes categorias IP estão disponíveis:  
  
    -   **Administrativos**: esses devem ser todos os endereços IP dos seus administradores.  
  
    -  **Provedor de nuvem**: estes devem ser os endereços IP usados por seu provedor de nuvem.
  
    -   **Corporativos**: devem ser todos os endereços IP de sua rede interna, suas filiais e seus endereços de roaming de Wi-Fi.  
  
    -   **Arriscados**: esses devem ser quaisquer endereços IP que considerar arriscados. Eles podem incluir endereços IP suspeitos que você viu no passado, endereços IP em redes de seus concorrentes etc.  
  
    -   **VPN**: esses devem ser quaisquer endereços IP usados para funcionários remotos.  
4.  Para **Marcar** as atividades desses endereços IP, insira uma marca. Inserir uma palavra na caixa cria a marca. Depois que já tiver uma marca configurada, você poderá adicioná-la facilmente a intervalos de IP adicionais selecionando-a na lista. Você pode adicionar quantas marcas de IP desejar para cada intervalo. As marcas de IP podem ser usadas ao criar políticas.  Além das marcações de IP que você configura, o Cloud App Security tem marcações internas que não são configuráveis. Você pode ver a lista de marcações em [Filtro de marcações de IP](activity-filters.md).  
  
5.  Para os campos **Substituir o local** ou Organização (ISP) para esses endereços, insira um novo valor. Por exemplo, se você tiver um endereço IP que é considerado publicamente como sendo da Irlanda, mas você sabe que é dos Estados Unidos, você poderá substituir essa configuração.  
  
6.  Insira um **ISP Registrado**. Isso substitui os dados em suas atividades  
 
7.   Quando terminar, clique em **Criar**.  
  
     ![intervalo de newipaddress](./media/newipaddress-range.png "intervalo de newipaddress")  
  
  
    
## <a name="see-also"></a>Consulte Também  
[Configurar o Cloud Discovery](set-up-cloud-discovery.md)   

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
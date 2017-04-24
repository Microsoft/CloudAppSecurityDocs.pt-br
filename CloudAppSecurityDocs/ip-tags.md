---
title: Definir intervalos de IP e marcas | Microsoft Docs
description: "Este tópico fornece instruções sobre como trabalhar com marcas IP e categorias IP."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/29/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: bbf54f66-4ce2-428c-afc8-b5a64277014f
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: b3c8c8917606f3c34055eef0334f010d8aab7998
ms.sourcegitcommit: 661f4ce41262e8462c90fd2a4f1232e2154d5113
translationtype: HT
---
#  <a name="IPtagsandRanges"></a> Trabalhando com marcações e intervalos de IP

Para identificar facilmente os endereços IP conhecidos, como seus endereços IP do escritório físico, é necessário definir intervalos de endereço IP, o que permite que você marque e categorize apropriadamente e personalize a forma como os logs e alertas são exibidos e investigados.   
Cada grupo de intervalos de IP pode ser categorizado com base em uma lista predefinida de categorias de IP ou marcado com suas próprias marcas de IP criadas. Além disso, essa configuração permite que você substitua as informações de geolocalização com base no seu conhecimento de rede interno.  
  
Há suporte para IPv4 e IPv6.  
  
O Cloud App Security é fornecido pré-configurado com marcações internas para os seguintes endereços IP: 
- Cliente nativo
- Sistema operacional desatualizado
- Dispositivos gerenciados
- Proxy anônimo
- Botnet
- Tor
- Dispositivo em conformidade
- Dispositivo verificado
- Representar

Para usar essas marcações internas como parte de uma pesquisa, consulte a ID na documentação da API do Cloud App Security. 



Na barra de menus, clique no ícone de configurações ![ícone de configurações](./media/settings-icon.png "ícone de configurações") e selecione **Intervalos de Endereços IP**. Clique em **+Adicionar Intervalo de Endereços IP** e defina o seguinte:  
  
> [!NOTE]  
>  O local e o ISP registrado substituirão os padrões.   
> No entanto, as marcas de IP são adicionadas à atividade sem substituir os dados.  
  
1.  Atribua um **Nome** ao seu intervalo de IP. O nome não aparecerá no log de atividades, ele é usado apenas para gerenciar o intervalo de IP.  
  
     Para incluir o intervalo de IP em uma categoria de IP, selecione uma categoria no menu suspenso.  
  
2.  Insira o **Intervalo de endereços IP** que você deseja configurar e clique no botão "+". Você pode adicionar quantos endereços IP e sub-redes desejar usando a notação de prefixo de rede (também conhecida como notação CIDR), por exemplo, 192.168.1.0/32.  
  
3.  Para os campos **Substituir o local** ou Organização (ISP) para esses endereços, insira um novo valor. Por exemplo, se você tiver um endereço IP que é considerado publicamente como sendo da Irlanda, mas você sabe que é dos Estados Unidos, você poderá substituir essa configuração.  
  
4.  Insira um **ISP Registrado**. Isso substituirá os dados em suas atividades  
  
5.  Para **Marcar** as atividades desses endereços IP, insira uma marca. Inserir uma palavra na caixa cria a marca. Depois que você já tiver uma marca configurada, poderá adicioná-la facilmente a intervalos de IP adicionais selecionando-a na lista. Você pode adicionar quantas marcas de IP desejar para cada intervalo. As marcas de IP podem ser usadas ao criar políticas.  Além das marcações de IP que você configura, o Cloud App Security tem marcações internas que não são configuráveis. Você pode ver a lista de marcações em [Filtro de marcações de IP](activity-filters.md).  
  
6.  As **Categorias de IP** são usadas para reconhecer facilmente atividades de endereços IP interessantes. As categorias estão disponíveis no portal embora precisem de configuração do usuário para determinar quais endereços IP estão incluídos em cada categoria, exceto para a categoria “Arriscados”, que inclui duas marcas de IP: proxy anônimo e Tor.  
  
     As seguintes categorias IP estão disponíveis:  
  
    -   **Administrativos**: esses devem ser todos os endereços IP dos seus administradores.  
  
    -   **Internos**: esses devem ser todos os endereços IP da sua rede interna, suas filiais e seus endereços de roaming de Wi-Fi.  
  
    -   **Arriscados**: esses devem ser quaisquer endereços IP que considerar arriscados. Eles podem incluir endereços IP suspeitos que você viu no passado, endereços IP em redes de seus concorrentes etc.  
  
    -   **VPN**: esses devem ser quaisquer endereços IP usados para funcionários remotos.  
  
    -   **Proxy de nuvem**: esse deve ser o endereço IP do seu proxy a nuvem.  
  
7.  Quando terminar, clique em **Criar**.  
  
     ![intervalo de newipaddress](./media/newipaddress-range.png "intervalo de newipaddress")  
  
  
    
## <a name="see-also"></a>Veja também  
[Configurar o Cloud Discovery](set-up-cloud-discovery.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
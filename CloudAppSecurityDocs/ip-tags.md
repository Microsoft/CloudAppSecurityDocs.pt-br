---
title: Definir intervalos de IP e marcas
description: Este artigo fornece instruções sobre como trabalhar com marcas de IP e categorias de IP.
ms.date: 11/09/2020
ms.topic: how-to
ms.openlocfilehash: 295b4b812679600254cb2a82b8efef57aa71757b
ms.sourcegitcommit: 16a65ab2c8ca778d0b3cfa97b847af4c812363b2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/03/2021
ms.locfileid: "97855737"
---
# <a name="working-with-ip-ranges-and-tags"></a><a name="IPtagsandRanges"></a>Trabalhando com intervalos de IP e marcas

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Para identificar com facilidade endereços IP conhecidos, como os endereços IP de seu escritório físico, você precisa definir intervalos de endereços IP. Os intervalos de endereços IP permitem que você marque, categorize e personalize a maneira como os logs e os alertas são exibidos e investigados. Cada grupo de intervalos de IP pode ser categorizado com base em uma lista predefinida de categorias de IP. Você também pode criar marcas de IP personalizadas para seus intervalos de IP. Além disso, você pode substituir as informações de localização geográfica pública com base no seu conhecimento de rede interno. Há suporte para IPv4 e IPv6.

O Cloud App Security é pré-configurado com intervalos de IP internos de provedores de nuvem populares, como o Azure e o Office 365. Além disso, temos marcação interna baseada na inteligência contra ameaças da Microsoft, incluindo proxy anônimo, Botnet e Tor. Veja a lista completa no menu suspenso na página de intervalos de endereços IP.

> [!NOTE]
>
> - Para usar essas marcações internas como parte de uma pesquisa, consulte a ID na documentação da API do Cloud App Security.
> - Você pode adicionar intervalos de IP em massa criando um script usando a **API de intervalos de endereços IP**.
> - Você não pode adicionar intervalos de IP com endereços IP sobrepostos.
> - Para exibir a documentação da API, na barra de menus do portal do Cloud App Security, clique no ponto de interrogação e, em seguida, em **Documentação da API**.

As marcas de endereço IP internas e as marcas de IP personalizadas são consideradas de maneira hierárquica. As marcas de IP personalizadas têm precedência sobre as marcas de IP internas. Por exemplo, se um endereço IP estiver marcado como **De risco** com base na inteligência contra ameaças, mas houver uma marca de IP personalizada que o identifica como **Corporativo**, as marcas e a categoria personalizadas terão precedência.

>[!NOTE]
> Quando um endereço IP é marcado como corporativo, ele é refletido no portal e os endereços IP são excluídos do disparo de detecções específicas (por exemplo, [viagem impossível](anomaly-detection-policy.md#impossible-travel)) porque esses endereços IP são considerados confiáveis.

## <a name="create-an-ip-address-range"></a>Criar um intervalo de endereços IP

Na barra de menus, clique no ícone de configurações. Selecione **Intervalos de endereços IP**. Clique no sinal de adição ( **+** ) para adicionar intervalos de endereços IP e defina os seguintes campos:

1. Atribua um **Nome** ao seu intervalo de IP. O nome não é exibido no log de atividades; ele é usado apenas para gerenciar o intervalo de IP.

    Para incluir o intervalo de IP em uma categoria de IP, selecione uma categoria no menu suspenso.

2. Insira o **Intervalo de endereços IP** que você deseja configurar e clique no botão "+". Você pode adicionar quantos endereços IP e sub-redes desejar usando a notação de prefixo de rede (também conhecida como notação CIDR), por exemplo, 192.168.1.0/32.

3. Use as **Categorias** para reconhecer facilmente as atividades de endereços IP interessantes. As categorias estão disponíveis no portal. No entanto, elas geralmente exigem a configuração de usuário para determinar quais endereços IP estão incluídos em cada categoria. A exceção a essa configuração é a categoria "De risco", que inclui duas marcas de IP – Proxy anônimo e Tor.

    As seguintes categorias IP estão disponíveis:

    - **Administrativos**: esses IPs devem ser todos os endereços IP dos administradores.

    - **Provedor de nuvem**: esses IPs devem ser os endereços IP usados por seu provedor de nuvem.

    - **Corporativo**: esses IPS devem ser todos os endereços IP públicos de sua rede interna, suas filiais e seus endereços de roaming de Wi-Fi.

    - **De risco**: esses IPs devem ser todos os endereços IP que você considere apresentar riscos. Eles podem incluir endereços IP suspeitos vistos no passado, endereços IP em redes de seus concorrentes, etc.

    - **VPN**: esses IPs devem ser todos os endereços IP usados para funcionários remotos.

4. Para **Marcar** as atividades desses endereços IP, insira uma marca. Inserir uma palavra na caixa cria a marca. Depois que já tiver uma marca configurada, você poderá adicioná-la facilmente a intervalos de IP adicionais selecionando-a na lista. Você pode adicionar quantas marcas de IP desejar para cada intervalo. As marcas de IP podem ser usadas ao criar políticas.  Junto com as marcas de IP que você configura, o Cloud App Security tem marcas internas que não são configuráveis. Você pode ver a lista de marcações em [Filtro de marcações de IP](activity-filters.md).
    > [!NOTE]
    > - O local e o ISP registrado substituem os padrões.
    > - As marcas de IP são adicionadas à atividade sem substituir os dados.

5. Para os campos **Substituir o local** ou Organização (ISP) para esses endereços, insira um novo valor. Por exemplo, digamos que você tenha um endereço IP que seja considerado publicamente como pertencente à Irlanda. No entanto, você sabe que o IP está nos Estados Unidos. Você substituirá a localização para esse intervalo de endereços IP.

6. Insira um **ISP Registrado**. Essa configuração substitui os dados em suas atividades.

7. Quando tiver concluído, clique em **Criar**.

    ![intervalo de newipaddress](media/newipaddress-range.png "intervalo de newipaddress")

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Configurar Cloud Discovery](set-up-cloud-discovery.md)

[!INCLUDE [Open support ticket](includes/support.md)]

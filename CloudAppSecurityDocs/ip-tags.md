---
title: Definir intervalos de IP e marcas-Cloud App Security | Microsoft Docs
description: Este artigo fornece instruções para trabalhar com marcas de IP e categorias de IP.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/16/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: c26c5cea5a366220c5f8fdff030db1240a7e1a73
ms.sourcegitcommit: 9fe879ce7f07933866191724de5f108f43e3f923
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/24/2020
ms.locfileid: "77566939"
---
#  <a name="IPtagsandRanges"></a>Trabalhando com intervalos de IP e marcas

*Aplica-se a: Microsoft Cloud App Security*

Para identificar facilmente endereços IP conhecidos, como seus endereços IP físicos do Office, você precisa definir intervalos de endereços IP. Os intervalos de endereços IP permitem marcar, categorizar e personalizar a maneira como os logs e alertas são exibidos e investigados. Cada grupo de intervalos de IP pode ser categorizado com base em uma lista predefinida de categorias de IP. Você também pode criar marcas de IP personalizadas para seus intervalos de IP. Além disso, você pode substituir as informações públicas de localização geográfica com base no seu conhecimento de rede interno. Há suporte para IPv4 e IPv6.

Cloud App Security vem pré-configurado com intervalos de IP internos para provedores de nuvem populares, como o Azure e o Office 365. Além disso, temos uma marcação interna baseada em inteligência contra ameaças da Microsoft, incluindo proxy anônimo, botnet e Tor. Você pode ver a lista completa no menu suspenso na página intervalos de endereços IP.

> [!NOTE]
>
> - Para usar essas marcas internas como parte de uma pesquisa, consulte sua ID na documentação da API Cloud App Security.
> - Você pode adicionar intervalos de IP em massa criando um script usando a **API de intervalos de endereços IP**.
> - Você não pode adicionar intervalos de IP com endereços IP sobrepostos.
> - Para exibir a documentação da API, na barra de menus do Cloud App Security portal, clique no ponto de interrogação e na **documentação da API**.

Marcas de endereço IP interno e marcas de IP personalizadas são consideradas hierarquicamente. Marcas de IP personalizadas têm precedência sobre marcas de IP internas. Por exemplo, se um endereço IP estiver marcado como **arriscado** com base na inteligência contra ameaças, mas houver uma marca de IP personalizada que a identifique como **corporativa**, a categoria e as marcas personalizadas têm precedência.

>[!NOTE]
> Quando um endereço IP é marcado como corporativo, ele é refletido no portal e os endereços IP são excluídos do disparo de detecções específicas (por exemplo, [viagem impossível](anomaly-detection-policy.md#impossible-travel)) porque esses endereços IP são considerados confiáveis.

## <a name="create-an-ip-address-range"></a>Criar um intervalo de endereços IP

Na barra de menus, clique no ícone configurações. Selecione **intervalos de endereços IP**. Clique no sinal de adição para adicionar intervalos de endereços IP e defina os seguintes campos:

1. **Nomeie** seu intervalo de IP. O nome não aparece no log de atividades, mas só é usado para gerenciar seu intervalo de IPS.

    Para incluir o intervalo de IP em uma categoria de IP, selecione uma categoria no menu suspenso.

2. Insira o **intervalo de endereços IP** que você deseja configurar e, em seguida, clique no botão "+". Você pode adicionar quantos endereços IP e sub-redes desejar usando a notação de prefixo de rede (também conhecida como notação CIDR), por exemplo 192.168.1.0/32.

3. As **categorias** são usadas para reconhecer facilmente as atividades de endereços IP interessantes. As categorias estão disponíveis no Portal. No entanto, normalmente exigem a configuração do usuário para determinar quais endereços IP estão incluídos em cada categoria. A exceção a essa configuração é a categoria "arriscada", que inclui duas marcas de IP – proxy anônimo e Tor.

    As seguintes categorias de IP estão disponíveis:

    - **Administrativo**: esses IPS devem ser todos os endereços IP de seus administradores.

    - **Provedor de nuvem**: esses IPS devem ser os endereços IP usados pelo seu provedor de nuvem.

    - **Corporativo**: esses IPS devem ser todos os endereços IP de sua rede interna, suas filiais e seus endereços de roaming de Wi-Fi.

    - **Arriscado**: esses IPS devem ser qualquer endereço IP que você considere arriscado. Eles podem incluir endereços IP suspeitos que você viu no passado, endereços IP nas redes de seus concorrentes e assim por diante.

    - **VPN**: esses IPS devem ser quaisquer endereços IP que você usar para trabalhadores remotos.

4. Para **Marcar** as atividades desses endereços IP, insira uma marca. A inserção de uma palavra na caixa cria a marca. Depois que você já tiver uma marca configurada, poderá adicioná-la facilmente a intervalos IP adicionais, escolhendo-a na lista. Você pode adicionar quantas marcas de IP desejar para cada intervalo. Marcas de IP podem ser usadas ao criar políticas.  Juntamente com as marcas de IP que você configura, Cloud App Security tem marcas internas que não são configuráveis. Você pode ver a lista de marcas no [filtro marcas de IP](activity-filters.md).
    > [!NOTE]
    > - O local e os padrões de substituição do ISP registrados.
    > - As marcas de IP são adicionadas à atividade sem substituir dados.

5. Para **substituir os** campos de local ou organização (ISP) para esses endereços, insira novo valor. Por exemplo, digamos que você tenha um endereço IP que é considerado publicamente como na Irlanda. No entanto, você sabe que o IP está nos EUA. Você substituirá o local desse intervalo de endereços IP.

6. Insira um **ISP registrado**. Essa configuração substitui os dados em suas atividades.

7. Quando terminar, clique em **criar**.

    ![intervalo de newipaddress](media/newipaddress-range.png "intervalo de newipaddress")

## <a name="next-steps"></a>{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}

> [!div class="nextstepaction"]
> [Configurar Cloud Discovery](set-up-cloud-discovery.md)

[!INCLUDE [Open support ticket](includes/support.md)]

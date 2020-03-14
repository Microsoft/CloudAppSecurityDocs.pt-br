---
title: Visibilidade das atividades do aplicativo de nuvem-Cloud App Security | Microsoft Docs
description: Este artigo fornece uma lista de atividades, filtros e parâmetros de correspondência que podem ser aplicados às políticas de atividade.
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
ms.openlocfilehash: 33837f543282dbc7d40dc7c1961e687b4334794e
ms.sourcegitcommit: 4f3883a9e85d0aaf2802b10433b221c3f1838d88
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79285290"
---
# <a name="activities"></a>Atividades

*Aplica-se a: Microsoft Cloud App Security*

Microsoft Cloud App Security fornece visibilidade de todas as atividades de seus aplicativos conectados. Depois de conectar Cloud App Security a um aplicativo usando o conector de aplicativos, Cloud App Security examina todas as atividades ocorridas – o período de tempo de varredura retroativa difere por aplicativo e, em seguida, é atualizado constantemente com novas atividades.

> [!NOTE]
> Para obter uma lista completa de atividades do Office 365 monitoradas pelo Cloud App Security, veja [Pesquisar o log de auditoria no Centro de Conformidade e Segurança do Office 365](https://support.office.com/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c?ui=en-US&rs=en-US&ad=US#ID0EABAAA=Audited_activities)

O **Log de atividades** pode ser filtrado para permitir que você encontre atividades específicas. Você cria políticas com base nas atividades e, em seguida, define o que deseja ser alertado e atua. Você pode pesquisar atividades executadas em determinados arquivos. O tipo de atividades e as informações que recebemos para cada atividade dependem do aplicativo e do tipo de dados que ele pode fornecer.

Por exemplo, é possível usar o **Log de atividades** para encontrar usuários na sua organização que estejam usando sistemas operacionais ou navegadores desatualizados da seguinte maneira: depois de conectar um aplicativo ao Cloud App Security, na página **Log de atividades**, use o filtro avançado e selecione **Marcação do agente do usuário**. Em seguida, selecione **Navegador desatualizado** ou **Sistema operacional desatualizado**.

![Exemplo de navegador desatualizado de atividade](media/activity-example-outdated.png)

O filtro básico fornece excelentes ferramentas para começar a usar a filtragem de suas atividades.

![filtro básico do log de atividades](media/activity-log-filter-basic.png)

Para fazer uma busca detalhada em atividades mais específicas, você pode expandir o filtro básico clicando em **avançado**.

![filtro avançado do log de atividades](media/activity-log-filter-advanced.png)

> [!NOTE]
> A marca herdada é adicionada a qualquer política de atividade que use o filtro "usuário" mais antigo. Esse filtro continuará funcionando normalmente. Se você quiser remover a marca herdada, poderá remover o filtro e adicionar o filtro novamente usando o novo filtro de **nome de usuário** .

## <a name="the-activity-drawer"></a>A gaveta de atividades

### <a name="working-with-the-activity-drawer"></a>Trabalhando com a gaveta Atividade

Você pode exibir mais informações sobre cada atividade clicando na própria atividade no log de atividades. Isso abre a gaveta de atividade que fornece as seguintes ações e informações adicionais para cada atividade:
- Políticas correspondentes: clique no link Políticas correspondentes para ver uma lista de políticas nessa atividade correspondente.

- Exibir dados brutos: clique em Exibir dados brutos para ver os dados reais que foram recebidos do aplicativo.

- Usuário: clique no usuário para exibir a página do usuário que executou a atividade.

- Tipo de dispositivo: clique no tipo de dispositivo para exibir os dados brutos do agente do usuário.

- Local: clique no local para exibir o local no Bing Mapas.

- Marcas e categoria de endereço IP: clique na marca de IP para exibir a lista de marcas de IP encontradas nessa atividade. Em seguida, você pode filtrar por todas as atividades correspondentes nessa marca.

Os campos na gaveta Atividade fornecem links contextuais para atividades adicionais e análises detalhadas que você talvez queira executar diretamente na gaveta. Por exemplo, se você mover o cursor para próximo da categoria de endereço IP, pode usar o ícone para adicionar filtro ![adicionar filtro](media/add-to-filter-icon.png) para adicionar o endereço IP imediatamente ao filtro da página atual. Você também pode usar o ícone de engrenagem de configurações ![ícone de configurações](media/contextual-settings-icon.png) que aparece diretamente na página de configurações necessária para alterar a configuração de um dos campos, tais como **Grupos de usuários**.

Você também pode usar os ícones na parte superior da guia para:
- Exibir atividades do mesmo tipo
- Exibir todas as atividades do mesmo usuário
- Exibir atividades do mesmo endereço IP
- Exibir atividades da mesma localização geográfica
- Exibir atividades do mesmo período de tempo (48 horas)

![gaveta de atividade](media/activity-drawer.png "gaveta de atividade")

Para obter uma lista das ações de governança disponíveis, consulte [Ações de governança de atividade](governance-actions.md#activity-governance-actions).

#### <a name="user-insights"></a>Informações de usuário

A experiência de investigação inclui informações sobre o usuário que está agindo. Com um único clique, você pode obter uma visão geral abrangente do usuário, incluindo em qual local eles se conectaram, quantos alertas abertos estão envolvidos e suas informações de metadados.

Para exibir informações de usuário:

1. Clique na atividade em si no **Log de atividades**.

2. Em seguida, clique na guia **Usuário**.  
Clicar em abre a guia **usuário** da gaveta de atividade fornece as seguintes informações sobre o usuário:
    - **Abrir alertas**: o número de alertas abertos envolvendo o usuário.
    - **Corresponde**: o número de correspondências de política para arquivos pertencentes ao usuário.
    - **Atividades**: o número de atividades executadas pelo usuário nos últimos 30 dias.
    - **Países**: o número de países dos quais o usuário se conectou nos últimos 30 dias.
    - **ISPs**: o número de ISPs dos quais o usuário se conectou nos últimos 30 dias.
    - **Endereços IP**: o número de endereços IP dos quais o usuário se conectou nos últimos 30 dias.

![Informações do usuário no Microsoft Cloud App Security](media/user-insights.png)

#### <a name="ip-address-insights"></a>Informações de endereço IP

Como as informações de endereço IP são cruciais para quase todas as investigações, você pode exibir informações detalhadas sobre endereços IP na gaveta de atividades. De dentro de uma atividade específica, você pode clicar na guia endereço IP para exibir dados consolidados sobre o endereço IP, incluindo o número de alertas abertos para o endereço IP específico, um grafo de tendência de atividade recente e um mapa de local. Isso permite uma busca detalhada fácil ao investigar alertas de viagem impossíveis, por exemplo. Você pode entender facilmente onde o endereço IP foi usado e se ele estava envolvido em atividades suspeitas ou não. Você também pode executar ações diretamente na gaveta de endereço IP que permitem marcar um endereço IP como arriscado, VPN ou corporativo para facilitar a investigação futura e a criação de políticas.

Para exibir informações de endereço IP:

1. Clique na atividade em si no **Log de atividades**.

2. Em seguida, clique na guia **endereço IP** .  
Isso abre a guia **endereço IP** da gaveta de atividades, que fornece as seguintes informações sobre o endereço IP:
    - **Abrir alertas**: o número de alertas abertos que envolveram o endereço IP.
    - **Atividades**: o número de atividades executadas pelo endereço IP nos últimos 30 dias.
    - **Local do IP**: os locais geográficos dos quais o endereço IP se conectou nos últimos 30 dias.
    - **Atividades**: o número de atividades executadas a partir deste endereço IP nos últimos 30 dias.
    - **Atividades de administração**: o número de atividades administrativas executadas a partir desse endereço IP nos últimos 30 dias.
    - Você pode executar as seguintes ações de endereço IP:
        - Marcar como IP corporativo e adicionar à lista de permissões
        - Marcar como endereço IP VPN e adicionar à lista de permissões
        - Marcar como IP arriscado e adicionar à lista bloqueada

   >[!NOTE]
   > Quando um endereço IP é marcado como corporativo, ele é refletido no portal e os endereços IP são excluídos do disparo de detecções específicas (por exemplo, viagem impossível) porque esses endereços IP são considerados confiáveis.

![Informações de endereço IP no Cloud App Security](media/ip-address-insights.png)

## Exportar atividades<a name="export"></a>

Você pode exportar todas as atividades do usuário para um arquivo CSV.

No **log de atividades**, no canto superior direito, clique no botão **Exportar** .

![botão Exportar](media/export-button.png)

[!INCLUDE [Handle personal data](../includes/gdpr-intro-sentence.md)]

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]

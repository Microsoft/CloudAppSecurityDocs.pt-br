---
title: Trabalhando com aplicativos descobertos no Cloud App Security
description: Este artigo descreve o processo para identificar e corrigir aplicativos de descoberta de nuvem arriscados no Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 09/25/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: a63546a3404cdf4c48a56b800f5d80d09ee5971e
ms.sourcegitcommit: 4f3883a9e85d0aaf2802b10433b221c3f1838d88
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79285470"
---
# <a name="working-with-discovered-apps"></a>Trabalhando com aplicativos descobertos

*Aplica-se a: Microsoft Cloud App Security*

O painel do Cloud Discovery foi projetado para fornecer mais informações sobre como os aplicativos de nuvem estão sendo usados na sua organização. Ele fornece uma visão geral rápida de quais tipos de aplicativos estão sendo usados, seus alertas abertos e os níveis de risco dos aplicativos em sua organização. Ele também mostra quem são os principais usuários do aplicativo e fornece um mapa do local da Matriz de Aplicativo. O painel de Cloud Discovery tem muitas opções para filtrar os dados. A filtragem permite que você gere exibições específicas dependendo do que você está mais interessado em usar gráficos fáceis de entender para lhe dar um panorama completo.

![painel do Cloud Discovery](media/cloud-discovery-dashboard.png)

## <a name="review-the-cloud-discovery-dashboard"></a>Examinar o Painel do Cloud Discovery

A primeira coisa que você deve fazer para obter uma visão geral de seus aplicativos Cloud Discovery é examinar as seguintes informações no painel do Cloud Discovery:

1. Primeiro, veja o uso geral do aplicativo de nuvem em sua organização na **visão geral de uso de alto nível**.

1. Em seguida, aprofunde um nível mais profundo para ver quais são as **principais categorias** usadas em sua organização para cada um dos diferentes parâmetros de uso. Você pode ver quanto desse uso é por aplicativos de sanções.

1. Aprofunde-se ainda mais e veja todos os aplicativos em uma categoria específica na guia **aplicativos descobertos** .

1. Você pode ver os **principais usuários e endereços IP** de origem para identificar quais usuários são os mais dominantes nos aplicativos de nuvem na sua organização.
1. Verifique como os aplicativos descobertos se espalham acordo com a localização geográfica (segundo a Matriz) no **mapa de Matriz de Aplicativos**.

1. Por fim, não se esqueça de revisar a pontuação de risco do aplicativo descoberto na **visão geral de risco do aplicativo**. Verifique o **status dos alertas de descoberta** para ver quantos alertas abertos você deve investigar.

## <a name="deep-dive-into-discovered-apps"></a>Aprofundar-se nos aplicativos Descobertos

Se você quiser aprofundar-se nos dados fornecidos pelo Cloud Discovery, use os filtros para examinar quais aplicativos são arriscados e que são comumente usados.

Por exemplo, se você quiser identificar aplicativos de colaboração e de armazenamento de nuvem arriscados usados com frequência, poderá usar a página de aplicativos Descobertos para os aplicativos que você deseja filtrar. Em seguida, você pode [desaprovar ou bloqueá](governance-discovery.md) -los da seguinte maneira:

1. Na página **Aplicativos descobertos**, em **Procurar por categoria**, selecione **Armazenamento em nuvem** e **Colaboração**.

1. Em seguida, use os filtros avançados e defina o **fator de risco de conformidade** para **SOC 2** igual a **falso**

1. Para **uso**, defina **os usuários** com mais de 50 usuários e **uso** de **Transações** para maior que 100.

1. **Não há suporte**para definir o **fator de risco de segurança** para **dados em uma criptografia em repouso** . Em seguida, defina a **Pontuação de risco** igual a 6 ou inferior.

![Filtros dos aplicativos descobertos](media/discovered-app-filters.png)

Depois que os resultados são filtrados, você pode [cancelar a sanção e bloqueá-los](governance-discovery.md) usando a caixa de seleção de ação em massa para cancelar a sanção de todos eles em uma ação só. Depois que eles não forem aprovados, você poderá usar um script de bloqueio para bloqueá-los de serem usados em seu ambiente.

A descoberta de nuvem permite que você se aprofunde ainda mais no uso da nuvem da sua organização. Você pode identificar instâncias específicas que estão em uso investigando os subdomínios descobertos.

Por exemplo, você pode diferenciar entre diferentes sites do SharePoint.

Isso tem suporte apenas em firewalls e proxies que contêm dados de URL de destino. Para obter mais informações, consulte a lista de dispositivos com suporte em [firewalls e proxies com suporte](set-up-cloud-discovery.md#supported-firewalls-and-proxies).

![informações de subdomínio](media/discovery-domains.png)

## <a name="discover-resources-and-custom-apps"></a>Descubra recursos e aplicativos personalizados

O Cloud Discovery também permite que você aprofunde-se em seus recursos de IaaS e PaaS. Você pode descobrir atividades em suas plataformas de hospedagem de recursos, exibindo o acesso aos dados em seus recursos e aplicativos auto-hospedados, incluindo contas de armazenamento, infraestrutura e aplicativos personalizados hospedados no Azure, Google Cloud Platform e AWS. Não apenas você pode ver o uso geral em suas soluções de IaaS, mas você pode obter visibilidade dos recursos específicos que são hospedados em cada uma delas e também do uso geral dos recursos, a fim de ajudar a atenuar o risco de acordo com o recurso.

Por exemplo, do Cloud App Security, você pode monitorar a atividade de modo que, se um volume grande de dados for carregado, você poderá descobrir para qual recurso esses dados são carregados e fazer drill down para ver quem executou a atividade.

> [!NOTE]
> Isso tem suporte apenas em firewalls e proxies que contêm dados de URL de destino. Para obter mais informações, consulte a lista de dispositivos com suporte em [firewalls e proxies com suporte](set-up-cloud-discovery.md#supported-firewalls-and-proxies).

Para exibir os recursos descobertos:

1. No portal do Cloud App Security, selecione **Descobrir** e **Recursos descobertos**.

    ![Menu Recursos descobertos](media/discovered-resources-menu.png)

1. Na página de recursos descobertos, você pode fazer drill down em cada recurso para ver quais tipos de transações ocorreram, quem as acessou e, em seguida, fazer drill down para investigar ainda mais os usuários.

   ![Recursos de descoberta](media/discovery-resources.png)

1. Para aplicativos personalizados, clique em três botões no fim da linha e selecione **Adicionar aplicativo personalizado**. Isso abrirá a janela **Adicionar aplicativo personalizado** que permite que você nomeie e identifique o aplicativo para que ele possa ser incluído no painel do Cloud Discovery.

## <a name="generate-cloud-discovery-executive-report"></a>Gerar relatório executivo de Cloud Discovery

A melhor maneira de obter uma visão geral do uso de sombra de ti em sua organização é gerando um relatório executivo Cloud Discovery. Este relatório identifica os principais riscos potenciais e ajuda a planejar um fluxo de trabalho para reduzir e gerenciar riscos até que eles sejam resolvidos.

Para gerar um relatório executivo de Cloud Discovery:

1. No **painel Cloud Discovery**, clique nos três pontos no canto superior direito do painel e, em seguida, selecione **gerar relatório executivo Cloud Discovery**.
1. Opcionalmente, altere o nome do relatório.
1. Clique em **Gerar**.

## <a name="exclude-entities"></a>Excluir entidades

Se você tiver usuários do sistema, endereços IP ou computadores com ruídos, mas não interessantes ou aplicativos que não são relevantes, talvez você queira excluir seus dados dos dados de Cloud Discovery que são analisados. Por exemplo, você talvez queira excluir todas as informações provenientes de 127.0.0.1 ou do host local.

Para criar uma exclusão:

1. No portal, no ícone de configurações, selecione **Configurações de Cloud Discovery**.

1. Clique na guia **Excluir entidades**.

1. Escolha a guia **usuários excluídos**, **endereços IP excluídos**ou **computadores excluídos** e clique no botão + para adicionar sua exclusão.

1. Adicione um alias de usuário, um endereço IP ou um nome de computador. É recomendável adicionar informações sobre por que a exclusão foi feita.

    ![excluir usuário](media/exclude-user.png "excluir usuário")

## <a name="manage-continuous-reports"></a>Gerenciar relatórios contínuos

Relatórios contínuos personalizados fornecem maior granularidade ao monitorar os dados de log do Cloud Discovery da sua organização. Ao criar relatórios personalizados, é possível filtrar em locais geográficos específicos, redes e sites ou unidades organizacionais. Por padrão, somente os relatórios a seguir aparecem no seu seletor de relatório do Cloud Discovery:

- O **Relatório global** consolida todas as informações no portal de todas as fontes de dados incluídas em seus logs.  O relatório global não inclui dados do Microsoft Defender ATP.

- O **Relatório específico de fonte de dados** mostra apenas informações para uma fonte de dados específica.

Para criar um novo relatório contínuo:

1. No portal, no ícone de configurações, selecione **Configurações de Cloud Discovery**.

1. Clique na guia **relatório contínuo** .

1. Clique no botão **Criar relatório**.

1. Insira um nome de relatório.

1. Selecione as fontes de dados que você deseja incluir.

1. Defina os filtros desejados nos dados. Esses filtros podem ser **grupos de usuários**, **marcas de endereço IP**ou **intervalos de endereços IP**. Para obter mais informações sobre como trabalhar com marcas de endereço IP e intervalos de endereço IP, consulte [Organizar os dados de acordo com suas necessidades](ip-tags.md).

    ![criar relatório contínuo personalizado](media/create-custom-continuous-report.png)

> [!NOTE]
> Todos os relatórios personalizados são limitados a um máximo de 1 GB de dados não compactados. Se houver mais de 1 GB de dados, os primeiros 1 GB de dados serão exportados para o relatório.

## <a name="deleting-cloud-discovery-data"></a>Excluindo dados do Cloud Discovery

Há uma série de motivos pelos quais você pode desejar excluir seus dados do Cloud Discovery. É recomendável exclui-los nos seguintes casos:

- Se você carregou os arquivos de log manualmente e passou muito tempo antes de atualizar o sistema com novos arquivos de log e você não deseja dados antigos afetando os resultados.

- Quando você definir uma nova exibição de dados personalizada, ela será aplicada somente aos novos dados desse ponto em diante. Portanto, talvez você queira apagar dados antigos e, em seguida, carregar os arquivos de log novamente para permitir que a exibição de dados personalizada pegue eventos nos dados do arquivo de log.

- Se muitos usuários ou endereços IP começaram a funcionar novamente depois de ficar offline por algum tempo, sua atividade será identificada como anômala e poderá dar a você falsas violações positivas.

Para excluir os dados do Cloud Discovery:

1. No portal, no ícone de configurações, selecione **Configurações de Cloud Discovery**.

1. Clique na guia **Excluir dados**.

    É importante ter certeza de que deseja excluir os dados antes de continuar-ele não pode ser desfeito e exclui **todos os** Cloud Discovery dados no sistema.

1. Clique no botão **Excluir**.

    ![excluir dados](media/delete-data.png "excluir dados")

    > [!NOTE]
    > O processo de exclusão leva alguns minutos e não é imediato.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Criar instantâneo de relatórios do Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

> [!div class="nextstepaction"]
> [Configurar upload de log automático para relatórios contínuos](configure-automatic-log-upload-for-continuous-reports.md)

> [!div class="nextstepaction"]
> [Trabalhando com os dados do Cloud Discovery](working-with-cloud-discovery-data.md)

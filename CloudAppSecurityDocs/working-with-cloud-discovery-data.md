---
title: Usar dados de Cloud Discovery para detectar comportamento arriscado – Cloud App Security
description: Este tópico fornece instruções sobre como trabalhar com os dados do Cloud Discovery, incluindo trabalhar com a pontuação de risco do aplicativo.
keywords: ''
author: shsagir
ms.author: shsagir
manager: angrobe
ms.date: 05/06/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 1406212b95a790aea489f4580fa821206139d5ae
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90878112"
---
# <a name="working-with-discovery-data"></a>Trabalhando com os dados de descoberta

[!INCLUDE [Banner for top of topics](includes/banner.md)]

O painel do Cloud Discovery foi projetado para fornecer mais informações sobre como os aplicativos de nuvem estão sendo usados na sua organização. Ele fornece uma visão geral rápida de quais tipos de aplicativos estão sendo usados, os alertas abertos e os níveis de risco dos aplicativos na sua organização. Ele também mostra quem são os principais usuários do aplicativo e fornece um mapa do local da Matriz de Aplicativo. O Painel do Cloud Discovery tem muitas opções para filtrar os dados. A filtragem permite que você gere exibições específicas dependendo do que você está mais interessado usando gráficos de fácil compreensão para apresentar o panorama completo em uma visão geral.

![painel do Cloud Discovery](media/cloud-discovery-dashboard.png)

## <a name="review-the-cloud-discovery-dashboard"></a>Examinar o Painel do Cloud Discovery

A primeira coisa que você deve fazer para obter uma visão geral de seus aplicativos do Cloud Discovery é examinar as seguintes informações no Painel do Cloud Discovery:

1. Primeiro, examine o uso geral de aplicativos de nuvem em sua organização na **visão geral de alto nível de uso**.

2. Em seguida, aprofunde-se um nível para ver quais são as **principais categorias** usadas na sua organização para cada um dos diferentes parâmetros de uso. Você pode ver quanto dessa utilização é de aplicativos de Sanção.

3. Vá ainda mais fundo e veja todos os aplicativos em uma categoria específica na guia **Aplicativos descobertos**.

4. Você pode ver os **principais usuários e endereços IP** de origem para identificar quais usuários são os mais dominantes nos aplicativos de nuvem na sua organização.
5. Verifique como os aplicativos descobertos se espalham acordo com a localização geográfica (segundo a Matriz) no **mapa de Matriz de Aplicativos**.

6. Por fim, não se esqueça de examinar a pontuação de risco do aplicativo descoberto na **Visão geral de risco do aplicativo**. Verifique o **status de alertas de descoberta** para ver quantos alertas abertos você deve investigar.

## <a name="exclude-entities"></a>Excluir entidades

Se você tem usuários do sistema, endereços IP ou computadores ruidosos, mas desinteressantes, ou aplicativos que não são relevantes, talvez queira excluir os dados deles dos dados do Cloud Discovery que são analisados. Por exemplo, você talvez queira excluir todas as informações provenientes de 127.0.0.1 ou do host local.

Para criar uma exclusão:

1. No portal, no ícone de configurações, selecione **Configurações de Cloud Discovery**.
2. Clique na guia **Excluir entidades**.
3. Escolha a guia **Usuários excluídos**, **Endereços IP excluídos** ou **Computadores excluídos** e clique no botão + para adicionar sua exclusão.
4. Adicione um alias do usuário, um endereço IP ou um nome do computador. É recomendável adicionar informações sobre por que a exclusão foi feita.

    ![excluir usuário](media/exclude-user.png "excluir usuário")

## <a name="manage-continuous-reports"></a>Gerenciar relatórios contínuos

Relatórios contínuos personalizados fornecem maior granularidade ao monitorar os dados de log do Cloud Discovery da sua organização. Ao criar relatórios personalizados, é possível filtrar por localizações geográficas, redes, sites ou unidades organizacionais específicas. Por padrão, somente os relatórios a seguir aparecem no seu seletor de relatório do Cloud Discovery:

- O **Relatório global** consolida todas as informações no portal de todas as fontes de dados incluídas em seus logs.  O relatório global não inclui dados do Microsoft Defender ATP.

- O **Relatório específico de fonte de dados** mostra apenas informações para uma fonte de dados específica.

Para criar um novo relatório contínuo:

1. No portal, no ícone de configurações, selecione **Configurações de Cloud Discovery**.

2. Clique na guia **Relatório contínuo**.

3. Clique no botão **Criar relatório**.

4. Insira um nome de relatório.

5. Selecione as fontes de dados que você deseja incluir.

6. Defina os filtros que você deseja nos dados. Esses filtros podem ser **grupos de usuários**, **marcas de endereço IP**ou **intervalos de endereços IP**. Para obter mais informações sobre como trabalhar com marcas de endereço IP e intervalos de endereço IP, consulte [Organizar os dados de acordo com suas necessidades](ip-tags.md).

    ![criar relatório contínuo personalizado](media/create-custom-continuous-report.png)

> [!NOTE]
> Todos os relatórios personalizados são limitados a no máximo 1 GB de dados não compactados. Se houver mais de 1 GB de dados, o primeiro GB de dados será exportado para o relatório.

## <a name="deleting-cloud-discovery-data"></a>Excluindo dados do Cloud Discovery

Há uma série de motivos pelos quais você pode desejar excluir seus dados do Cloud Discovery. É recomendável exclui-los nos seguintes casos:

- Se você carregou os arquivos de log manualmente e passou muito tempo antes de atualizar o sistema com novos arquivos de log e você não deseja dados antigos afetando os resultados.

- Quando você define uma nova exibição de dados personalizada, ela será aplicada somente aos novos dados desse ponto em diante. Portanto, você talvez queira apagar os dados antigos e, em seguida, carregar seus arquivos de log novamente para habilitar a exibição de dados personalizada para escolher eventos nos dados do arquivo de log.

- Se vários usuários ou endereços IP tiverem começado a funcionar de novo recentemente após ficarem um período offline, sua atividade será identificada como anômala e poderá gerar violações falso-positivas.

Para excluir os dados do Cloud Discovery:

1. No portal, no ícone de configurações, selecione **Configurações de Cloud Discovery**.

2. Clique na guia **Excluir dados**.

    É importante ter certeza de que deseja excluir os dados antes de continuar. Isso não poderá ser desfeito e excluirá **todos** os dados do Cloud Discovery no sistema.

3. Clique no botão **Excluir**.

    ![excluir dados](media/delete-data.png "excluir dados")

    > [!NOTE]
    >  O processo de exclusão leva alguns minutos e não é imediato.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]

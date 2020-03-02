---
title: Criar políticas para controlar atividades no Cloud App Security
description: Este artigo fornece instruções para criar e trabalhar com políticas de atividade.
author: shsagir
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: conceptual
ms.date: 03/01/2020
ms.collection: M365-security-compliance
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 87e25ce39cf7c3858db00af9dbe9d9141de2a48d
ms.sourcegitcommit: 828bbe923713b358fbd32f14e007bf7e5bccedbe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/01/2020
ms.locfileid: "78207895"
---
# <a name="activity-policies"></a>Políticas de atividade

*Aplica-se a: Microsoft Cloud App Security*

As políticas de atividade permitem impor uma ampla variedade de processos automatizados usando as APIs do provedor de aplicativos. Essas políticas permitem que você monitore atividades específicas executadas por vários usuários ou siga taxas altas inesperadamente de um determinado tipo de atividade.

Depois de definir uma política de detecção de atividade, ele começa a gerar alertas-os alertas são gerados somente em atividades que ocorrem após a criação da política.

> [!NOTE]
> As políticas que disparam mais de 50.000 correspondências por dia, para três dos últimos 7 dias, são automaticamente desabilitadas. Você pode tentar refinar as políticas adicionando filtros adicionais ou, se estiver usando políticas para fins de relatório, considere [salvá-las como consultas](activity-filters-queries.md#activity-queries) em vez disso.

## <a name="custom-alerts"></a>Alertas personalizados

As políticas de atividade permitem que alertas personalizados sejam enviados ou ações tomadas quando a atividade do usuário é detectada. Por exemplo, você deseja saber todas as vezes:

- Um usuário tenta entrar e falha 70 vezes em um minuto
- Um usuário baixa 7.000 arquivos
- Um usuário está conectado do Afeganistão

Você pode definir alertas de atividade a serem enviados para você mesmo ou para o usuário quando esses eventos ocorrerem. Você pode até mesmo suspender o usuário até concluir a investigação do que aconteceu.

Para criar uma nova política de atividade, siga este procedimento:

1. No console do, clique em **controle** seguido por **políticas**.

2. Clique em **criar política** e selecione **política de atividade**.

     ![menu de política de atividade](media/activity-policy-menu.png)

3. Dê um nome e uma descrição à sua política, se você quiser que possa baseá-la em um modelo, para obter mais informações sobre modelos de política, consulte [controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md).

4. Para definir quais ações ou outras métricas irão disparar essa política, trabalhe com os **filtros de atividade**.
    > [!NOTE]
    > Para garantir que você inclua apenas os resultados em que o campo de filtro especificado tenha um valor, é recomendável adicionar o mesmo campo novamente usando o teste de **configuração** . Por exemplo, quando a filtragem por **local** *não é igual* a uma lista especificada de países, também *é*possível adicionar um filtro para **localização** . Você também pode visualizar os resultados do filtro selecionando **Editar e Visualizar resultados**.
    >
    > ![Captura de tela das configurações de filtro, a exibição do campo de localização é definida](media/activity-example-location-isset.png)

5. Em **parâmetros de correspondência de atividade**, selecione quando uma violação de política será disparada. Escolha disparar quando uma única atividade corresponder aos filtros ou somente quando um número especificado de **atividades repetidas** for detectado.
    - Se você escolher uma **atividade repetida**, poderá definir **em um único aplicativo**. Essa configuração irá disparar uma correspondência de política somente quando as atividades repetidas ocorrerem no mesmo aplicativo. Por exemplo, cinco downloads em 30 minutos do box disparam uma correspondência de política.

6. Configure as **ações** que devem ser executadas quando uma correspondência for encontrada.

Veja estes exemplos:

- Vários logons com falha

    Você pode definir a política para que receba um alerta quando ocorrer um grande número de logons com falha dentro de um curto período de tempo. Para configurar esse tipo de política, escolha o filtro de atividade apropriado na página **nova política de atividade** .

    Abaixo do campo **filtros de atividade** , configure os parâmetros para os quais o alerta será disparado.

    ![Exemplo de política para várias tentativas de entrada com falha](media/multiple-failed-log-on-attempts-policy-example.png "exemplo de política de várias tentativas de logon com falha")

- Alta taxa de download

    Você pode definir sua política para que receba um alerta quando houver um nível inesperado ou não-caracterizado de download da atividade. Para configurar esse tipo de política, em parâmetros de **taxa** , escolha os parâmetros para disparar o alerta.

    ![exemplo de alta taxa de download](media/high-download-rate-example.png "exemplo de alta taxa de download")

## <a name="activity-policy-reference"></a>Referência de política de atividade

Esta seção tem detalhes de referência sobre políticas, explicações para cada tipo de política e os campos que podem ser configurados para cada política.

Uma **política de atividade** é uma política baseada em API que permite monitorar as atividades da sua organização na nuvem. A política leva em conta mais de 20 filtros de metadados de arquivo, incluindo o tipo de dispositivo e o local. Com base nos resultados da política, as notificações podem ser geradas e os usuários podem ser suspensos do aplicativo de nuvem.
Cada política é composta pelas seguintes partes:

- Filtros de atividade – permita que você crie condições granulares com base em metadados.

- Parâmetros de correspondência de atividade – permite que você defina um limite para o número de vezes que uma atividade se repete para corresponder à política.  Especifique o número de atividades repetidas necessárias para corresponder à política. Por exemplo, defina uma política para alertar quando um usuário tiver 10 tentativas de logon malsucedidas em um período de 2 minutos. Por padrão, o parâmetro de correspondência de atividade * * gera uma correspondência para cada atividade única que atende a todos os filtros de atividade.

  - Usando a **atividade repetida** , você pode definir o número de atividades repetidas, a duração do intervalo de tempo no qual as atividades são contadas. Você também pode especificar que todas as atividades devem ser executadas pelo mesmo usuário e no mesmo aplicativo de nuvem.

- Ações – a política fornece um conjunto de ações de governança que podem ser aplicadas automaticamente quando violações são detectadas.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Políticas de proteção de dados](data-protection-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]

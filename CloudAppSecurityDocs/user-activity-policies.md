---
title: Criar políticas para controlar atividades no Cloud App Security
description: Este artigo fornece instruções para criar e trabalhar com políticas de atividade.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: barbkess
ms.date: 12/14/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 99d5fd37-d922-4269-b557-86d7f84180eb
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: b1ab9549e4bb4587137f8560b2ef997c7ee1218a
ms.sourcegitcommit: 8ef0438fa35916c48625ff750cb85e9628d202f2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56281892"
---
# <a name="activity-policies"></a>Políticas de atividade

*Aplica-se a: Microsoft Cloud App Security*

As políticas de atividade permitem que você aplique uma ampla gama de processos automatizados usando as APIs do provedor de aplicativo. Essas políticas permitem que você monitore atividades específicas realizadas por vários usuários ou siga altas taxas inesperadas de um determinado tipo de atividade.  
  
Depois de definir uma política de detecção de atividades, ele começará a gerar alertas, os quais são gerados apenas em atividades que ocorrem depois da criação da política.
  
  
## <a name="custom-alerts"></a>Alertas personalizados  

As políticas de atividade permitem o envio de alertas personalizados ou a execução de ações quando a atividade do usuário é detectada. Por exemplo, você deseja ser informado sempre que:

- Um usuário tenta entrar e falha 70 vezes em um minuto
- Um usuário baixa 7.000 arquivos
- Um usuário se conecta do Afeganistão

Você pode definir alertas de atividade a serem enviados para você mesmo ou para o usuário quando esses eventos ocorrerem. Você pode até mesmo suspender o usuário até concluir a investigação do que ocorreu.  
  
Para criar uma nova política de atividade, siga este procedimento:  
  
1. No console, clique em **Controlar** seguido por **Políticas**.  
  
2. Clique em **Criar política** e selecione **Política de atividade**.  
  
     ![menu de política de atividade](./media/activity-policy-menu.png "menu de política de atividade")  
  
3. Atribua um nome e uma descrição à sua política. Se desejar, poderá baseá-la em um modelo. Para obter mais informações sobre modelos de política, consulte [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md).  
  
4. Para definir quais ações ou outras métricas vão disparar essa política, trabalhe com os **filtros de atividade**.  
  
5. Em **Parâmetros de correspondência de atividade**, selecione quando uma violação de política será disparada. Escolha disparar quando uma única atividade corresponde aos filtros ou somente quando um número especificado de **Atividades repetidas** é detectado.  
    - Se você escolher **Atividade repetida**, poderá definir **Em um único aplicativo**. Essa configuração disparará uma correspondência de política somente quando as atividades repetidas ocorrerem no mesmo aplicativo. Por exemplo, cinco downloads em 30 minutos no Box disparam uma correspondência de política.  
  
6. Configure as **Ações** que devem ser executadas quando uma correspondência for encontrada.  
  
Veja esses exemplos:  
  
- Vários logons com falha  
  
     Você pode definir uma política para receber um alerta quando ocorrer um grande número de logons com falha em um curto período. Para configurar esse tipo de política, escolha o filtro de atividade apropriado na página **Nova Política de Atividade**.  
  
     No campo **Filtros de atividade**, configure os parâmetros para os quais o alerta será disparado.  
  
     ![Exemplo de política de várias tentativas de credenciais com falha](./media/multiple-failed-log-on-attempts-policy-example.png "exemplo de política de várias tentativas de logon com falha")  
  
- Alta taxa de downloads  
  
     Você pode definir a política para que você receba um alerta quando houve um nível inesperado ou não característico de atividade de download. Para configurar esse tipo de política, nos parâmetros de **Taxa**, escolha os parâmetros para disparar o alerta.  
  
     ![exemplo de alta taxa de downloads](./media/high-download-rate-example.png "exemplo de alta taxa de downloads")  
  
  
## <a name="activity-policy-reference"></a>Referência de política de atividade  

Esta seção apresenta detalhes de referência sobre as políticas, explicações sobre cada tipo de política e os campos que podem ser configurados para cada política.  
  
Uma **Política de atividade** é uma política baseada em API que permite monitorar as atividades de sua organização na nuvem. A política leva em conta mais de 20 filtros de metadados de arquivo, incluindo a localização e o tipo de dispositivo. Com base nos resultados de política, as notificações podem ser geradas e os usuários podem ser suspensos do aplicativo de nuvem.
Cada política é composta pelas seguintes partes:  
  
- Filtros de atividade – permite criar condições granulares com base nos metadados.  
  
- Parâmetros de correspondência de atividade – permitem que você defina um limite para o número de vezes que uma atividade se repete para ser considerada como correspondente à política.  Especifique o número de atividades repetidas necessário para corresponder à política. Por exemplo, defina uma política para alertar quando um usuário tiver 10 tentativas de logon sem êxito em um período de 2 minutos. Por padrão, o parâmetro **Correspondência de atividade aciona uma correspondência para cada atividade que atende a todos os filtros de atividade.

  - Usando a **Atividade repetida**, você pode definir o número de atividades repetidas e a duração do período em que as atividades são contadas. Você também pode especificar que todas as atividades devem ser executadas pelo mesmo usuário e no mesmo aplicativo na nuvem.  
  
  
- Ações – a política fornece a um conjunto de ações de governança que podem ser aplicadas automaticamente quando violações são detectadas.  
  
## <a name="next-steps"></a>Próximas etapas
  
[Políticas de proteção de dados](data-protection-policies.md)

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/)  
  

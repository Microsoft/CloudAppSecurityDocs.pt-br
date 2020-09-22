---
title: Monitorar alertas acionados no Cloud App Security
description: Este artigo fornece uma lista e uma descrição de todos os alertas.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/10/2018
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 6bb43764f9a8e200b79a81dfe0dc97db557b6fe0
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90878010"
---
# <a name="monitor-alerts-in-cloud-app-security"></a>Monitorar alertas no Cloud App Security

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Os alertas são os pontos de entrada para compreender seu ambiente de nuvem mais profundamente. Este artigo fornece uma lista e uma descrição de todos os alertas.

## <a name="monitoring-your-alerts"></a>Monitorando os alertas

É uma boa ideia examinar todos os seus alertas. Entender o motivo pelo qual um alerta está ocorrendo permite que você o use como uma ferramenta para modificar as políticas.

**Para exibir alertas:** No portal de Microsoft Cloud App Security, clique em **alertas**.

![Menu Alerta](media/alert-menu.png)

- **Ignore** um alerta depois de vê-lo e determinar que ele não é de interesse.
  - Insira um **comentário** para explicar o motivo pelo qual você ignorou o alerta
  - **Envie-nos comentários sobre este alerta** a serem examinados por nossa equipe de pesquisa de segurança para melhoria dos alertas.

- **Resolva** o alerta se você investigá-lo e atenue o risco.

  - O alerta não será mais exibido na tabela de alertas.
  - **Marque-o como não lido** se você começou a investigar um problema, mas deseja garantir que se lembrará de continuar.
  - **Ajuste a política** que correspondeu ao alerta para melhorar as correspondências futuras de alerta.
  - Resolver um alerta oferece a opção de inserir um comentário e **Enviar comentários para a equipe do Cloud App Security**.

## <a name="built-in-alerts"></a>Alertas internos

Os seguintes tipos de alertas serão exibidos.

|Nome do alerta|AlertID|Descrição|
|----|----|----|
|Novo local|ALERT_GEOLOCATION_NEW_COUNTRY|Um novo local foi detectado desde o início da verificação (até seis meses). Esse alerta só aparece uma vez para cada país/região de toda a organização. |
|Novo usuário administrador|ALERT_ADMIN_USER|Um novo administrador foi detectado para um aplicativo específico. Esse administrador pode ser alguém que é administrador em um aplicativo e agora é administrador em outro. Este alerta relaciona-se ao tipo de administrador específico, por isso ele aparecerá sempre que o tipo de administrador for alterado. Se um usuário perder os privilégios de administrador e obtê-los novamente, esse alerta será exibido.|
|Conta inativa|ALERT_ZOMBIE_USER|Quando um usuário fica inativo por 60 dias por aplicativo (por exemplo, se alguém está ativo no Box, mas não usa o G Suite por 60 dias) o usuário é considerado inativo no G Suite. Uma marca é adicionada a esses usuários para que você possa pequisar contas inativas.|
|Local de administrador inesperado|ALERT_NEW_ADMIN_LOCATION|Um novo local foi detectado para os administradores desde o início da verificação (até seis meses). Esse alerta aparece apenas uma vez para cada país/região para qualquer administrador em sua organização. |
|Conta comprometida|ALERT_COMPROMISED_ACCOUNT|Se ocorreu uma violação em um aplicativo e a lista de contas violadas é publicada, o Cloud App Security baixa a lista e a compara com sua lista de usuários. A lista de usuários inclui usuários internos, usuários externos e contas pessoais. |

## <a name="custom-alerts"></a>Alertas Personalizados

Os seguintes tipos de alertas serão exibidos.

|Nome do alerta|AlertID|Descrição|
|----|----|----|
|Alerta de atividade suspeita|ALERT_SUSPICIOUS_ACTIVITY|Atividades suspeitas são pontuadas de acordo com o nível de suspeita da atividade anormal (há uma conta inativa envolvida? Ele é de um novo local?) Esses critérios são todos calculados juntos para fornecer uma pontuação de risco com base nos seguintes fatores de risco: <br />O usuário é administrador <br />Usuário estritamente remoto<br />Proxy anônimo<br /> A sessão inteira é composta por logons com falha<br />Vários logons com falha<br />Novo (administrador)<br />IP/ISP/país/agente de usuário para usuário/locatário<br /> IP/ISP/país/agente de usuário usado somente pelo usuário (administrador)<br />Primeira atividade de usuário (administrador) em muito tempo<br />Primeira vez que essa atividade administrativa específica é executada em muito tempo<br />Essa atividade administrativa específica não é comum/nunca foi executada antes<br />Esse IP tinha apenas logons com falha no passado<br />Viagem impossível|
|Alerta de uso de nuvem suspeito|ALERT_DISCOVERY_ANOMALY_DETECTION|A detecção de anomalias do Cloud Discovery verifica o padrão de comportamento normal e procura por usuários ou aplicativos que são usados de maneira incomum. |
|Violação de política de atividade|ALERT_CABINET_EVENT_MATCH_AUDIT|Esse alerta informa quando uma correspondência de política foi detectada.|
|Violação de política de arquivos|ALERT_CABINET_EVENT_MATCH_FILE|Esse alerta informa quando uma correspondência de política foi detectada.|
|Violação de política de proxy|ALERT_CABINET_INLINE_EVENT_MATCH|Esse alerta informa quando uma correspondência de política foi detectada.|
|Violação de política de campo|ALERT_CABINET_EVENT_MATCH_OBJECT|Esse alerta informa quando uma correspondência de política foi detectada.|
|Novo serviço descoberto|ALERT_CABINET_DISCOVERY_NEW_SERVICE|Um novo aplicativo foi descoberto.|
|Uso de conta pessoal|ALERT_PERSONAL_USER_SAGE|Com base em nomes de usuário, o mecanismo de detecção procura contas pessoais e compartilhamentos de arquivos. |

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]

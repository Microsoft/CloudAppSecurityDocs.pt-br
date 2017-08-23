---
title: Trabalhando com alertas no Cloud App Security | Microsoft Docs
description: "Este tópico fornece uma lista e descrição de todos os alertas."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 8/18/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: f118a3bf-1663-46ba-884f-b1b03a84ab66
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: b5027699862a6cfe4b8dd8037f26d569b788a412
ms.sourcegitcommit: 27170447acfaeded585c264e425a46a485e7fb19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/20/2017
---
# <a name="alerts"></a>Alertas
Para exibir alertas:

No portal do Cloud App Security, clique em Alertas.


![Menu Alerta](./media/alert-menu.png)

Para lidar com cada alerta, clique no alerta na tabela e selecione uma destas opções:
- **Resolver alerta**: depois de investigar e realizar ações para mitigar o alerta, clique em **Resolver alerta**. Você pode inserir um comentário para salvar as informações sobre quais ações foram executadas e pode optar por **Enviar comentários à equipe do Cloud App Security** sobre o alerta. Depois de resolver um alerta, ele não será mais exibido na tabela de alertas.
- Resolver um alerta e **Marcar como lido**: você pode deixar o alerta aberto, mas pode marcá-lo como lido.
- Resolver alerta e **Ajustar a política**: você pode modificar a política correspondente ao alerta em resposta ao alerta.
- **Ignorar**: você pode ignorar o alerta, o que fará com que ele deixe de ser exibido na tabela, mas não o mostrará como resolvido. Isso é mais usado quando o alerta é benigno ou um falso positivo.

Os seguintes tipos de alertas serão exibidos. 

## <a name="built-in-alerts"></a>Alertas internos

|Nome do alerta|AlertID|Descrição|
|----|----|----|
|Novo local|ALERT_GEOLOCATION_NEW_COUNTRY|Um novo local foi detectado desde o início da verificação (até seis meses). Isso é mostrado apenas uma vez para cada país para toda a sua organização. |
|Novo usuário administrador|ALERT_ADMIN_USER|Foi detectado um novo administrador para um aplicativo específico; isso pode ser alguém que é um administrador em um aplicativo e agora é um administrador em outro. Este alerta relaciona-se ao tipo de administrador específico, por isso ele aparecerá sempre que o tipo de administrador for alterado. Se um usuário perder os privilégios de administrador e obtê-los novamente, esse alerta será exibido.|
|Conta inativa|ALERT_ZOMBIE_USER|Quando um usuário fica inativo por 60 dias por aplicativo (por exemplo, se alguém está ativo no Box, mas não usa o G Suite por 60 dias) o usuário é considerado inativo no G Suite. Uma marca é adicionada a esses usuários para que você possa pequisar contas inativas.|
|Local de administrador inesperado|ALERT_NEW_ADMIN_LOCATION|Um novo local foi detectado para os administradores desde o início da verificação (até seis meses). Isso é mostrado apenas uma vez para cada país para um administrador para toda a sua organização. |
|Conta comprometida|ALERT_COMPROMISED_ACCOUNT|Se ocorrer uma violação em um aplicativo e a lista de contas violadas for publicada, o Cloud App Security baixa a lista e a compara à sua lista de usuários, incluindo usuários internos, usuários externos e contas pessoais. |

## <a name="custom-alerts"></a>Alertas Personalizados

|Nome do alerta|AlertID|Descrição|
|----|----|----|
|Alerta de atividade suspeita|ALERT_SUSPICIOUS_ACTIVITY|Atividades suspeitas são pontuadas de acordo com o nível de suspeita da atividade anormal (há uma conta inativa envolvida? Trata-se de um novo local?) Esses critérios são calculados juntos para fornecer uma pontuação de risco com base nos seguintes fatores de risco: <br>O usuário é administrador <br>Usuário estritamente remoto<br>Proxy anônimo<br> A sessão inteira é composta por logons com falha<br>Várias falhas de logon<br>Novo (administrador)<br>IP/ISP/país/agente de usuário para usuário/locatário<br> IP/ISP/país/agente de usuário usado somente pelo usuário (administrador)<br>Primeira atividade de usuário (administrador) em muito tempo<br>Primeira vez que essa atividade administrativa específica é executada em muito tempo<br>Essa atividade administrativa específica não é comum / nunca foi executada antes<br>Esse IP tinha apenas logons com falha no passado<br>Viagem impossível|
|Alerta de uso de nuvem suspeito|ALERT_DISCOVERY_ANOMALY_DETECTION|A detecção de anomalias do Cloud Discovery verifica o padrão de comportamento normal e procura por usuários ou aplicativos que são usados de maneira incomum. |
|Violação de política de atividade|ALERT_CABINET_EVENT_MATCH_AUDIT|Esse alerta informa quando uma correspondência de política foi detectada.|
|Violação de política de arquivos|ALERT_CABINET_EVENT_MATCH_FILE|Esse alerta informa quando uma correspondência de política foi detectada.|
|Violação de política de proxy|ALERT_CABINET_INLINE_EVENT_MATCH|Esse alerta informa quando uma correspondência de política foi detectada.|
|Violação de política de campo|ALERT_CABINET_EVENT_MATCH_OBJECT|Esse alerta informa quando uma correspondência de política foi detectada.|
|Novo serviço descoberto|ALERT_CABINET_DISCOVERY_NEW_SERVICE|Um novo aplicativo foi descoberto.|
|Uso de conta pessoal|ALERT_PERSONAL_USER_SAGE|Com base em nomes de usuário, o mecanismo de detecção procura contas pessoais e compartilhamentos de arquivos. |

## <a name="see-also"></a>Veja também  
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
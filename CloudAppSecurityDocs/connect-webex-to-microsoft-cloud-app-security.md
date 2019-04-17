---
title: Conectar-se WebEx ao Cloud App Security
description: Este artigo fornece informações sobre como conectar seu aplicativo WebEx ao Cloud App Security usando o conector de API para obter visibilidade e controle de uso.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: barbkess
ms.date: 04/16/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: c43271fd-9a61-4727-9945-de1c6ea5422c
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 764ca55b076c837b784ddc82ef3b4337bc9a8fcd
ms.sourcegitcommit: ec7ae3cd7648fa62d7a7925f8693dcb99b0b0d26
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2019
ms.locfileid: "59622347"
---
# <a name="connect-cisco-webex-to-microsoft-cloud-app-security"></a>Conectar o Cisco WebEx ao Microsoft Cloud App Security

*Aplica-se a: Microsoft Cloud App Security*

Este artigo fornece instruções para conectar o Microsoft Cloud App Security à sua conta existente do Cisco WebEx usando as APIs do conector. Essa conexão dá a você visibilidade e controle sobre os usuários, atividades e arquivos WebEx. 
 
## <a name="prerequisites"></a>Pré-requisitos

- Sugerimos que você crie uma conta de serviço dedicada para a conexão. Isso permite que você veja o que as ações de governança realizadas no WebEx como sendo executada nessa conta, como excluem mensagens enviadas em WebEx. Caso contrário, o nome do administrador que conector o Cloud App Security WebEx será exibido como o usuário que realizou as ações.  
- Você deve ter o administrador completo **e** permissões de administrador de conformidade no WebEx.


## <a name="how-to-connect-webex-to-cloud-app-security"></a>Como conectar WebEx ao Cloud App Security  
  
1.  No console do Cloud App Security, clique em **Investigar** e em **Aplicativos conectados**.  
  
2.  No **conectores de aplicativos** , clique no botão de adição seguido **Cisco WebEx**.  
  
     ![conectar-se WebEx](./media/cisco-webex.png "conectar WebEx")  
  
3.  No pop-up, insira o nome da instância deste conector.  
  
4.  Clique em **conectar-se o Cisco Webex**. Abre a página de entrada WebEx. Insira suas credenciais para permitir que Cloud App Security acesse a instância do WebEx da sua equipe.  
  
6.  WebEx perguntará se deseja permitir que Cloud App Security acesse suas informações de equipe, o log de atividades e realize atividades como um membro da equipe. Para continuar, clique em **Permitir**.  
  
7.  Novamente no console do Cloud App Security, você deve receber uma mensagem WebEx foi conectado com êxito.  
  
8.  Certifique-se de que a conexão foi bem-sucedida clicando em **Testar API**.  
  
     O teste pode levar alguns minutos. Depois de receber uma notificação de êxito, clique em **Fechar**.  
  
Depois de conectar WebEx, você receberá eventos por 7 dias antes da conexão. Cloud App Security examina os eventos nos últimos três meses. Para aumentar a isso, você deve ter uma licença pro do Cisco WebEx e abra um tíquete com suporte do Cloud App Security.

 
## <a name="next-steps"></a>Próximas etapas 
[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)   

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  

---
title: "Proteger sua organização contra ameaças | Microsoft Docs"
description: "Este tópico descreve o cenário para proteger sua organização contra ameaças em seu ambiente de nuvem."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 6/27/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 0017be99-29c3-468e-a181-255e343ed4f5
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 7bad1e1ae6196b684ac35d063558fad22bc3689f
ms.sourcegitcommit: 2f4474084c7e07ac4853945ab5aa1ea78950675d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/28/2017
---
# <a name="protecting-your-organization-against-threats"></a>Proteger sua organização contra ameaças  

Identifique problemas de segurança de nuvem e de uso de alto risco, detecte comportamentos anormais de usuários e evite ameaças em seus aplicativos de nuvem conectados. Obtenha visibilidade em atividades administrativas e de usuário e defina políticas para alertar um comportamento suspeito automaticamente ou quando ocorrerem atividades específicas que você considere arriscadas em seus ambientes de sanção. Aproveite a vasta quantidade de dados de pesquisa de segurança e de inteligência contra ameaças da Microsoft. As políticas de detecção de ameaças ajudam você a garantir que os aplicativos sancionados tenham todos os controles de segurança necessários e ajudem a manter o controle sobre eles.
 
## <a name="mass-download-by-a-single-user-data-exfiltration-by-an-insider"></a>Download em massa de um único usuário (remoção de dados por um usuário interno)

Esse caso de uso aplica-se ao Office 365, G Suite, Box, Dropbox e Salesforce.

### <a name="the-threat"></a>A AMEAÇA
Um usuário interno mal-intencionado pode e invasor com uma conta comprometida pode remover dados do Office 365 ou de outros aplicativos de nuvem ao baixar ou acessar vários arquivos em um curto período de tempo.

### <a name="the-solution"></a>A SOLUÇÃO
Detecte quando um usuário baixa ou acessa um grande número de arquivos em um curto período.

#### <a name="prerequisites"></a>Pré-requisitos

[Conectar](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) ao menos um aplicativo de nuvem ao Cloud App Security.

#### <a name="setting-up-monitoring"></a>Configurar o monitoramento

1.  Por padrão, o Cloud App Security examina sua rede para estabelecer uma linha de base, na qual aprende padrões sobre o que seus usuários costumam fazer na nuvem, quando o fazem e o que fazem normalmente. 

2. Defina uma política que observará seus aplicativos de nuvem para downloads em massa e alertará você se algo fora do comum acontecer:

    1. Na página **Políticas**, clique em [**Criar política de atividade**](user-activity-policies.md). 
   

    2. No campo [**Modelo de política**](policy-template-reference.md), escolha **Download em massa por um único usuário**.
    
    3. Como alternativa, você pode ajustar o filtro de atividades repetidas.
    
    4. Clique em **Criar**. 
   
     
2. Investigar suas correspondências
    
    1. Na página **Políticas**, clique no nome da política para ir para **Relatório de Políticas** e analise as correspondências que foram criadas para a política.

    2. Você pode investigar a correspondência clicando em uma correspondência específica para abrir a gaveta de atividades. Na gaveta, você pode ver as outras políticas com as quais essa atividade correspondente. 
    
    3. Você pode verificar os arquivos que foram baixados pelo usuário clicando nos objetos da atividade na **Gaveta de atividades** e, em seguida, no nome do arquivo, isso levará você para o arquivo na tabela de arquivos. Ali, você pode ver se os arquivos pertencem ao usuário, com quem eles são compartilhados e permitirá que você determine se estes são arquivos nos quais eles costumam funcionar ou se eles têm IP interno que não deve ser baixado.
     


#### <a name="validating-your-policy"></a>Validar a política

1. Para simular um alerta, baixe um número de documentos maior que o limite definido dos aplicativos de nuvem conectados em um curto período de tempo, dependendo do período de tempo definido na política (por exemplo, 30 downloads em menos de 5 minutos).
3. Vá para o relatório de políticas. Uma atividade de política do arquivo deve aparecer em breve. 
4. Você pode clicar na correspondência para ver quais arquivos foram baixados.  

#### <a name="removing-the-risk"></a>Remover o risco

Depois de validar e ajustar a política, remova possíveis falsos positivos que podem ter correspondido à sua política, como contas de serviço que são arquivos de sincronização, pastas de imagens de eventos da empresa etc. Em seguida, faça o seguinte: 
  1. Você pode tomar [ações de governança](governance-actions.md) abrindo a atividade na gaveta de atividades e clicando no nome do arquivo em **Objetos da atividade**.

  2. Entre em contato com os usuários para ver por que eles precisam de cópias de muitos arquivos corporativos em seus computadores.

 
## <a name="admin-activity-from-outside-your-organizations-network"></a>Atividade do administrador de fora da rede da sua organização

Esse caso de uso aplica-se ao Office 365, G Suite, Box, Dropbox, Salesforce e Okta.

### <a name="the-threat"></a>A AMEAÇA
Uma conta do administrador foi comprometida por um invasor externo. Contas de administrador são as contas mais importantes em sua organização, pois elas têm os maiores privilégios e acesso a todas as informações na sua organização. Geralmente, a atividade administrativa deve ser executada no escritório como parte do trabalho do administrador e não em locais remotos ou por dispositivos não reconhecidos.

### <a name="the-solution"></a>A SOLUÇÃO
Detecte quando as pessoas apresentando-se como administradores se conectam ao seu aplicativo de nuvem por meio de endereços IP externos e executando atividades de administrador.

#### <a name="prerequisites"></a>Pré-requisitos

- [Conectar](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) ao menos um aplicativo de nuvem ao Cloud App Security.

- Vá para **Configurações** > **Intervalos de endereços IP** e adicione intervalos de endereços IP para ambas as sub-redes internas e seus IPs públicos de saída e marque-os como **Corporativo**.

#### <a name="setting-up-monitoring"></a>Configurar o monitoramento

1.  Comece a monitorar seus aplicativos na nuvem ao configurar uma política que observará seus aplicativos na nuvem para atividade de administrador fora de sua rede e alertará caso algo fora do comum aconteça:

    1. Na página **Políticas**, clique em [**Criar política de atividade**](user-activity-policies.md). 
   

    2. No campo [**Modelo de política**](policy-template-reference.md), escolha **Atividade administrativa de um endereço IP não corporativo** e também defina o **Tipo de atividade** para **Logon** e selecione **Usuário**. Em seguida, em **Do grupo**, selecione o grupo ao qual seus administradores pertencem.
    
    3. Você pode ajustar a política para definir o número de atividades repetidas que você queira considerar como suspeitas.
    
    4. Clique em **Criar**. 
   
     
2. Investigar suas correspondências
    
    1. Na página **Políticas**, clique no nome da política para ir para **Relatório de Políticas** e analise as correspondências que foram criadas para a política.

    2. Você pode investigar a correspondência clicando em uma correspondência específica para abrir a gaveta de atividades. Na gaveta, você pode ver as outras políticas com as quais essa atividade correspondente. 
     
#### <a name="validating-your-policy"></a>Validar a política

1. Para simular um alerta, de um computador com um endereço IP que não faz parte da sua rede corporativa, execute atividades de administração, certificando-se de que o número de atividades que você executará seja maior que o limite definido, em um curto período, dependendo do período de tempo definido na política (por exemplo, 1 atividade em menos de 5 minutos).
3. Vá para o relatório de políticas. Uma atividade de política do arquivo deve aparecer em breve. 
4. Você pode clicar na correspondência para ver quais atividades foram executadas. 

#### <a name="removing-the-risk"></a>Remover o risco

Após você ter validado e ajustado a política, remova eventuais falsos positivos que possam ter correspondido à sua política. Em seguida, faça o seguinte: 
  1. Você pode tomar [ações de governança](governance-actions.md) abrindo a atividade na gaveta de atividades e clicando no nome do **Usuário**.

  2. Na página do usuário que é aberta, você pode ver um gráfico de atividade do usuário no último mês e locais em que o usuário foi visto como ativo, também no último mês, além de associações de grupo, atividade do aplicativo e contas. 
  
  3. Se necessário, você poderá clicar em **Contatar** para enviar uma mensagem de email para o usuário para alertá-lo de que sua conta foi violada.

 ![governança automática externa](./media/auto-gov-external.png)

   2. Depois que for totalmente validada, você pode defini-la para executar ações de governança automáticas. Por exemplo, você pode **Suspender usuário** ou **Remover colaborações do usuário**.


## <a name="see-also"></a>Veja também  
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
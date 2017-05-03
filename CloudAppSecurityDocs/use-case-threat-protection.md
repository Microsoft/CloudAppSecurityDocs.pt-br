---
title: "Visão geral do cenário de proteção contra ameaças | Microsoft Docs"
description: "Este tópico descreve o cenário para proteger sua organização contra ameaças em seu ambiente de nuvem."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/30/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 0017be99-29c3-468e-a181-255e343ed4f5
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: fcc793f0fea71ef0666a7c99034185c5cd5fd894
ms.sourcegitcommit: 7e9ae94cb4f90fbccaa84f19bdebb4652a425e45
translationtype: HT
---
# <a name="controlling-and-protecting-your-files"></a>Controlar e proteger seus arquivos  

Identifique problemas de segurança de nuvem e do uso de alto risco, detecte comportamentos anormais de usuários e evite ameaças em seus aplicativos de nuvem sancionados. Obtenha visibilidade em atividades administrativas e de usuário e defina políticas para alertar um comportamento suspeito automaticamente ou quando ocorrerem atividades específicas que você considere arriscadas em seus ambientes de sanção. Aproveite a vasta quantidade de dados de pesquisa de segurança e de inteligência contra ameaças da Microsoft. As políticas de detecção de ameaças ajudam você a garantir que os aplicativos sancionados tenham todos os controles de segurança necessários e ajudem a manter o controle sobre eles.
 
## <a name="massive-quantities-of-files-are-being-downloaded-insider-data-exfiltration"></a>Grandes quantidades de arquivos estão sendo baixadas (exfiltração de dados privilegiados)

Esse caso de uso se aplica aos aplicativos Office 365, Google Apps, Box, Dropbox e Salesforce.

### <a name="the-threat"></a>A AMEAÇA
Um invasor com uma conta comprometida pode exfiltrar dados do Office 365 ou de outros aplicativos de nuvem ao baixar ou acessar vários arquivos.

### <a name="the-solution"></a>A SOLUÇÃO
Detecte quando um usuário baixa ou acessa um grande número de arquivos em um curto período.

#### <a name="prerequisites"></a>Pré-requisitos

[Conectar](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) ao menos um aplicativo de nuvem ao Cloud App Security.

#### <a name="setting-up-monitoring"></a>Configurar o monitoramento

1.    Por padrão, o Cloud App Security examina sua rede para estabelecer uma linha de base, na qual aprende padrões sobre o que seus usuários costumam fazer na nuvem, quando o fazem e o que fazem normalmente. 

2. Além disso, é importante começar a monitorar seus aplicativos em nuvem, configurando uma política que inspecionará seus aplicativos em nuvem para downloads em massa e alertará você se algo fora do comum acontecer:

    1. Na página **Políticas**, clique em [**Criar política de atividade**](user-activity-policies.md). 
    ![criar política de atividade](./media/create-activity-policy.png)

    2. No campo [**Modelo de política**](policy-template-reference.md), escolha **Download em massa por um único usuário**.
    
    3. Como alternativa, você pode ajustar o filtro de atividades repetidas.
    
    4. Clique em **Aplicar modelo**. 
    ![modelo de atividade de política](./media/activity-policy-template.png)
     
2. Investigar suas correspondências
    
    1. Na página **Políticas**, clique no nome da política para ir para **Relatório de Políticas** e analise as correspondências que foram criadas para a política.

    2. Você pode investigar a correspondência clicando em uma correspondência específica para abrir a gaveta de atividades. Na gaveta, você pode ver as outras políticas com as quais essa atividade correspondente. 
     


#### <a name="validating-your-policy"></a>Validar a política

1. Para simular um alerta, baixe vários documentos de seus aplicativos de nuvem conectados várias vezes em um curto período, conforme definido na configuração de política (por exemplo, 10 vezes em menos de 30 minutos).
3. Vá para o relatório de políticas. Uma atividade de política do arquivo deve aparecer em breve. 
4. Você pode clicar na correspondência para ver quais arquivos foram baixados. A correspondência em si será mascarada para proteger os dados confidenciais. 

#### <a name="removing-the-risk"></a>Remover o risco

Após você ter validado e ajustado a política, remova eventuais falsos positivos que possam ter correspondido à sua política. Em seguida, faça o seguinte: 
  1. Você pode executar [ações de governança](governance-actions.md) imediatas clicando nos três pontos no final da linha e selecionando a ação de governança relevante; por exemplo, **Colocar em quarentena de usuário**.

 ![governança automática externa](./media/auto-gov-external.png)

   2. Depois que for totalmente validada, você pode defini-la para executar ações de governança automáticas. Por exemplo, no SharePoint e no OneDrive é possível **Remover usuários externos** ou **Colocar em quarentena de usuário** e, para o G Suite e o Box, é possível **Remover usuários externos** e **Remover acesso público**.

  ![aplicar ações de governança automáticas](./media/apply-automatic-gov-actions.png)



## <a name="see-also"></a>Veja também  
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
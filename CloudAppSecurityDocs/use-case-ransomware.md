---
title: "Visão geral do cenário de proteção contra ameaças | Microsoft Docs"
description: "Este tópico descreve o cenário para proteger sua organização contra ameaças em seu ambiente de nuvem."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/15/2018
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 7a06a243-9ec2-4a11-8db2-bc065cdfef64
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 4bb90d94fdab3725c853a772df1c484260a6c5ec
ms.sourcegitcommit: 458e936e1ac548eda37e9bf955b439199bbdd018
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2018
---
# <a name="protecting-your-organization-from-ransomware"></a>Protegendo sua organização contra ransonware

No último grande ataque de ransomware, WannaCry atingiu o mundo cibernético com grande força, infectando uma estimativa de 200 mil computadores em 150 países. Com o aumento de ataques de ransomware nos últimos anos, uma média de 25 mil ataques por mês em 2015 e 56 mil em 2016, ser proativo em relação à garantia de que sua rede não esteja em risco está se tornando uma necessidade de segurança cibernética. Este artigo explica como você pode usar o Cloud App Security para monitorar sua nuvem, detectar e reduzir as ameaças e aplicar as práticas recomendadas para proteger seu ambiente contra ransomware.

## <a name="what-is-ransomware"></a>O que é o ransomware?
O ransomware é um ataque cibernéticos em que o invasor envia um arquivo que pode impedir o acesso a seu computador e criptografar seus próprios arquivos. Os arquivos, às vezes, são mantidos para resgate e não são descriptografados até que você pague o invasor para recuperar acesso ao seu computador, a arquivos ou a aplicativos LOB críticos. Ataques ransomware podem afetar qualquer computador, casa, escritório, rede ou servidor. Na verdade, como grandes organizações são compostas de vários usuários que inadvertidamente podem abrir um arquivo que libera o ransomware em sua rede, as organizações são sob um risco ainda maior de serem forçadas a pagar o invasor para interromper o ransomware e restaurar o acesso aos arquivos ou computadores.

>[!NOTE]
> Esse caso de uso aplica-se ao Office 365, G Suite, Box e Dropbox.

## <a name="the-threat"></a>A AMEAÇA
Um usuário em sua organização é o alvo de um ataque ransomware. O usuário pode abrir inadvertidamente um email infectado e executar o ransomware que infecta todos os seus arquivos, incluindo os arquivos sincronizados na nuvem.

## <a name="the-solution"></a>A SOLUÇÃO
Detecte potencial ransomware em seu ambiente de nuvem ao criar uma política para atualizar quando atividade suspeita é detectada e configure ações automatizadas para impedir que arquivos ransomware sejam salvos em sua nuvem.

## <a name="prerequisites"></a>Pré-requisitos

[Conecte](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) pelo menos um aplicativo de nuvem (Office 365, G Suite, Box e Dropbox) ao Cloud App Security.

## <a name="setting-up-monitoring"></a>Configurar o monitoramento

1.  Por padrão, o Cloud App Security examina sua rede para estabelecer uma linha de base, na qual aprende padrões sobre o que seus usuários costumam fazer na nuvem, quando o fazem e o que fazem normalmente. 

2. Além disso, é importante começar a monitorar seus aplicativos em nuvem, configurando uma política que inspecionará seus aplicativos em nuvem para downloads em massa e alertará você se algo fora do comum acontecer:

    1. Na guia **Controle**, clique em [**Modelos**](policy-template-reference.md). 
   
    2. Na lista [**Modelo de política**](policy-template-reference.md), escolha **Atividade potencial de ransomware**. 
       ![modelo de ransomware](./media/ransomware-template.png)
    3. Este modelo é criado pronto para pesquisar atividade comum de ataques ransomware e arquivos e pastas associadas ao ransomware conhecido. Opcionalmente, você pode definir o tipo de alerta recebido (email e mensagem de texto) quando a política for correspondida.
        ![modelo de ransomware](./media/ransomware-template-fields.png)
    4. Clique em **Criar**. 
   
     
2. Investigar suas correspondências
    
    1. Na página **Políticas**, clique no nome da política para ir para **Relatório de Políticas** e analise as correspondências que foram criadas para a política.

    2. Você pode investigar a correspondência clicando em uma correspondência específica para abrir a gaveta de atividades. Na gaveta, você pode ver as outras políticas com as quais essa atividade correspondente. 
     
## <a name="validating-your-policy"></a>Validar a política

1. Para simular um alerta, altere a extensão de 30 arquivos para .wncry e carregue-os em seu site do SharePoint.
3. Vá para o relatório de políticas. Uma atividade de política do arquivo deve aparecer em breve. 
4. Você pode clicar na correspondência para ver quais arquivos foram baixados. A correspondência em si será mascarada para proteger os dados confidenciais. 

## <a name="remediating-attacks-and-preventing-risk"></a>Corrigindo ataques e evitando riscos

Após você ter validado e ajustado a política, remova eventuais falsos positivos que possam ter correspondido à sua política. Em seguida, faça o seguinte: 
1. Quando uma política de ransomware for atendida, você pode corrigi-lo definindo [ações de governança](governance-actions.md) automatizadas.

2. Para evitar ataques futuros, configure a política para executar ações de governança automáticas. Por exemplo, no SharePoint e no OneDrive você pode definir a política para automaticamente **Suspender usuário**.

 ## <a name="see-also"></a>Consulte Também  
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
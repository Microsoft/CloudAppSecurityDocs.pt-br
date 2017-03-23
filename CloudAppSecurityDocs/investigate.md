---
title: Investigar riscos e atividades suspeitas na nuvem com o Cloud App Security | Microsoft Docs
description: "Este tópico fornece uma descrição do processo para investigar alertas, problemas e atividades suspeitas usando o Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/19/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: a9b00c2a-2f71-499e-8f57-67e560daedc1
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 8e552aea95318288d329597ec2a0749535e06a52
ms.sourcegitcommit: 0d4748ea2a71e6ee2b0fa1c0498d9219bfbda29a
translationtype: HT
---
# <a name="investigate"></a>Investigar
Depois de o Cloud App Security ser executado em seu ambiente de nuvem, você precisará de um estágio de aprendizado e investigação sobre como usa as ferramentas do Cloud App Security para obter uma compreensão mais profunda do que está acontecendo no seu ambiente de nuvem. Em seguida, com base em seu ambiente específico e como ele está sendo usado, você pode identificar os requisitos para proteger sua organização contra riscos.

Este tópico descreve como executar uma investigação profunda para obter uma compreensão melhor sobre seu ambiente de nuvem.  

## <a name="dashboards"></a>Painéis  
Os painéis a seguir estão disponíveis para ajudá-lo a investigar aplicativos no seu ambiente de nuvem:  

|Painel|Descrição|  
|---------------|-----------------|  
|Painel principal|Visão geral do status da nuvem (usuários, arquivos e atividades) e ações necessárias (alertas, violações de atividade e violações de conteúdo)|  
|Painel do aplicativo: geral|Visão geral do uso do aplicativo por local, gráficos de uso por número de usuários|  
|Painel do aplicativo: insights|Análise de dados armazenados no aplicativo, divididos por tipo de arquivo e nível de compartilhamento de arquivos|  
|Painel do aplicativo: arquivos|Analise detalhadamente arquivos, a capacidade de filtrar de acordo com o proprietário, o nível de compartilhamento etc. e execute ações de governança (como quarentena)|  
|Painel do aplicativo: aplicativos de terceiros|Faz uma busca detalhada nos aplicativos de terceiros atualmente implantados, como o G Suite, e suas políticas definidas|  
|Painel do usuário|Uma visão geral completa do perfil do usuário na nuvem, incluindo grupos, locais, atividades recentes, alertas relacionados e navegadores usados|  

##  <a name="sanctionapp"></a> Marcar aplicativos como sancionados ou não sancionados  
Uma etapa importante para entender sua nuvem é marcar os aplicativos como sancionados ou não sancionados. Depois de sancionar um aplicativo, você poderá filtrar pelos aplicativos que não estão sancionados e iniciar a migração para aplicativos sancionadas do mesmo tipo.  

-   No console do Cloud App Security, acesse o Catálogo de aplicativos ou Aplicativos descobertos.  

-   Na lista de aplicativos, na linha do aplicativo que você deseja marcar como sancionado, selecione os três pontos no final da linha ![pontos para Marcar como sancionado](./media/sanction-three-dots.png "pontos para Marcar como sancionado") e selecione **Marcar como sancionado**.  

     ![Marcar como sancionado](./media/mark-as-sanctioned.png "marcar como sancionado")  


## <a name="use-the-investigation-tools"></a>Usar as ferramentas de investigação  

1.  No portal do Cloud App Security, vá para **Investigar**, examine o **Log de atividades** e filtre por um aplicativo específico. Verifique o seguinte:  

    -   Quem está acessando o seu ambiente de nuvem?  

    -   De quais intervalos de IP?  

    -   O que é a atividade do administrador?  

    -   De quais locais os administradores estão se conectando?  

    -   Existem quaisquer dispositivos desatualizados se conectando ao seu ambiente de nuvem?  

    -   Logons com falha estão partindo de endereços IP esperados?  

2.  Vá para **Investigar** e **Arquivos** e verifique o seguinte:  

    -   Quantos arquivos são compartilhados publicamente para que qualquer pessoa possa acessá-los sem um link?  

    -   Com quais parceiros você está compartilhando arquivos (compartilhamento de saída)?  

    -   Algum arquivo tem um nome sigiloso?  

    -   Qualquer um dos arquivos está sendo compartilhado com a conta pessoal de outra pessoa?  

3.  Vá para **Investigar** e **Contas** e verifique o seguinte:  

    -   Alguma conta esteve inativa em um determinado serviço por muito tempo? (Talvez você deva revogar a licença para esse usuário para esse serviço?)  

    -   Você deseja saber quais usuários têm uma função específica?  

    -   Alguém foi demitido, mas ainda tem acesso a um aplicativo e pode usar esse acesso para roubar informações?  

    -   Você deseja revogar a permissão do usuário para um aplicativo específico ou exigir que um usuário específico execute a autenticação multifator?  
    
    -   Você também pode analisar a conta do usuário clicando na engrenagem no final da linha da conta do usuário e selecionando uma ação a ser executada, como **Suspender o usuário** ou **Remover as colaborações do usuário**. Se o usuário foi importado do Azure Active Directory, você também pode clicar nas **Configurações da conta do Azure AD** para ter acesso fácil a recursos de gerenciamento de usuários avançados, como gerenciamento de grupo, MFA, detalhes sobre as entradas do usuário e a possibilidade de bloquear a entrada.

4.  Vá para **Investigar** e, em seguida, selecione um aplicativo. O painel do aplicativo se abre e fornece informações e insights. Você pode usar as guias na parte superior para verificar o seguinte:  

     ![Painel de aplicativos](./media/investigate-app.png "investigar aplicativo")  

    -   Que tipo de dispositivos seus usuários estão usando para se conectar ao aplicativo?  

    -   Quais tipos de arquivos eles estão salvando na nuvem?  

    -   Que atividade está acontecendo no aplicativo agora?  

    -   Há algum aplicativo de terceiros conectado ao seu ambiente?  

    -   Você estiver familiarizado com esses aplicativos?  

    -   Eles estão autorizados para o nível de acesso para o qual têm permissão?  

    -   Quantos usuários o implantaram? Quão comuns são esses aplicativos em geral?  

5.  Vá para o **Cloud Discovery Dashboard (Painel do Cloud Discovery)** e verifique o seguinte:  

    -   Quais aplicativos de nuvem estão sendo usados, até que ponto e por quem?  

    -   Para quais fins eles estão sendo usados?  

    -   Quantos dados estão sendo carregados nesses aplicativos de nuvem?  

    -   Em quais categorias você tem aplicativos de nuvem sancionados e, ainda assim, os usuários estão usando soluções alternativas?  

    -   Para a solução alternativa, deseja cancelar a sanção para algum aplicativo de nuvem na sua organização?  

    -   Há aplicativos de nuvem que são usados, mas não estão em conformidade com a política da sua organização?  

## <a name="use-reports-to-investigate-risk"></a>Usar relatórios para investigar riscos  
Ao começar a tentar obter controle sobre seu ambiente de nuvem, determinadas suposições são feitas com base no que se espera encontrar ou seja, você ainda não conhece realmente a nuvem. Com base nessas suposições, você cria políticas.

Após o Cloud App Security ser executado em seu ambiente de nuvem, use os relatórios internos (e relatórios personalizados) para ver o que está acontecendo em sua nuvem. Com base nisso, ajuste as políticas novamente para incluir exceções para que, eventualmente, sua política capture pouquíssimos falsos positivos.  

Os relatórios internos oferecem exibições agregadas para investigação. Para trabalhar com relatórios internos, vá para **Investigar** e para **Relatórios internos**. Para obter mais informações sobre os diferentes relatórios internos, consulte a [Referência do relatório interno](built-in-report-reference.md).  

## <a name="sample-investigation"></a>Investigação de amostra  
Digamos que você supõe que não há nenhum acesso ao seu ambiente de nuvem por endereços IP arriscados (por exemplo, proxies anônimos e Tor). Mas você cria uma política de IP arriscado para garantir:  

1.  No portal, vá até **Controlar** e selecione **Políticas**.  

2.  No **Centro de políticas**, selecione a guia **Modelos**.  

3.  No final da linha **Logon do usuário usando um endereço IP não categorizado**, selecione o sinal de mais (**+**) para criar uma nova política.  

4.  Altere o nome da política para que você seja capaz de identificar essa política.  

5.  Em **Filtros de atividade**, selecione **+** para adicionar um filtro. Role para baixo até **Marca de IP** e, em seguida, selecione **Anônimo** e **Tor**.  

     ![Exemplo de política para IPs arriscados](./media/example-policy-risky-ips.png "Exemplo de política para IPs arriscados")  

Agora que você tem a política em vigor, está surpreso ao ver que recebe um alerta de que a política foi violada.  

1.  Vá para a página **Alertas** e exiba o alerta sobre a violação da política.  

2.  Se você notar que parece uma violação real, desejará conter o risco ou corrigir.  

     Para conter o risco, você pode enviar uma notificação para o usuário para perguntar se a violação foi intencional e se o usuário estava ciente dela.  

     Você também pode detalhar o alerta e suspender o usuário até que possa descobrir o que precisa ser feito.  

3.  Se for um evento permitido que provavelmente não ocorrerá novamente, você poderá ignorar o alerta.  

     Se for permitido e esperar-se que ocorra novamente, você poderá modificar a política para evitar que esse tipo de evento seja considerado uma violação no futuro.  

## <a name="see-also"></a>Veja também  
Para saber como controlar o aplicativo de nuvem da sua organização, consulte [Controlar](control.md).   
Para obter suporte técnico, vá para a página de [suporte assistido do Cloud App Security](http://support.microsoft.com/oas/default.aspx?prid=16031).  
Os clientes Premier também podem escolher o Cloud App Security diretamente no [Portal Premier](https://premier.microsoft.com/).  

---
title: Investigar | Microsoft Docs
description: "Este tópico fornece uma descrição do processo para investigar alertas, problemas e atividades suspeitas usando o Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: a9b00c2a-2f71-499e-8f57-67e560daedc1
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed4ea71b24767d3602d40894d1cbac7447bcd8a2
ms.openlocfilehash: 186643ab8efa7391b06a09dd2cddbb22ba583e71


---

# <a name="investigate"></a>Investigar
Depois do Cloud App Security ser executado em seu ambiente de nuvem, você precisará de um estágio de aprendizado e investigação usando as ferramentas do Cloud App Security para alcançar uma compreensão mais profunda do que está acontecendo no seu ambiente de nuvem. Em seguida, com base em seu ambiente específico e como ele está sendo usado, você pode identificar os requisitos necessários para proteger sua organização contra riscos.  
  
Esta seção descreve como executar uma investigação profunda para obter uma compreensão melhor sobre o que está acontecendo em seu ambiente de nuvem.  
  
## <a name="dashboards"></a>Painéis  
Os painéis a seguir estão disponíveis para ajudá-lo a investigar o que está acontecendo com os aplicativos no seu ambiente de nuvem:  
  
|Painel|Descrição|  
|---------------|-----------------|  
|Painel principal|Visão geral do status da nuvem (usuários, arquivos e atividades), bem como as ações necessárias (alertas, violações de atividade e violações de conteúdo)|  
|Painel Aplicativo ‑ geral|Visão geral do uso do aplicativo por local, gráficos de uso por número de usuários|  
|Painel do aplicativo – insights|Análise de dados armazenados no aplicativo, divididos por tipo de arquivos e nível de compartilhamento de arquivos|  
|Painel do aplicativo – arquivos|Analise detalhadamente arquivos, a capacidade de filtrar de acordo com o proprietário, o nível de compartilhamento, etc., além de executar ações de governança (como quarentena)|  
|Painel do aplicativo – aplicativos de terceiros|Analise aplicativos de terceiros atualmente implantados, como Google Apps e defina políticas para eles|  
|Painel do usuário|Uma visão geral completa do perfil do usuário na nuvem, incluindo grupos, locais, atividades recentes, alertas relacionados e navegadores usados|  
  
##  <a name="a-namesanctionappa-sanction-or-unsanction-apps"></a> Sancionar ou cancelar a sanção de aplicativos  
A primeira etapa para entender sua nuvem é sancionar aplicativos. Depois de sancionar um aplicativo, você poderá filtrar pelos aplicativos que não estão sancionados e iniciar a migração para aplicativos sancionadas do mesmo tipo.  
  
-   No console do Cloud App Security, clique em **Descobrir** e em **Painel Descoberta**.  
  
-   Na lista de aplicativos descobertos, na linha em que o aplicativo que você deseja sancionar é exibido, clique nos três pontos no final da linha ![Sancionar três pontos](./media/sanction-three-dots.png "Sanction three dots") e selecione **Marcar como sancionado**.  
  
     ![marcar como aprovado](./media/mark-as-sanctioned.png "mark as sanctioned")  
  
> [!NOTE]  
>  Para cada aplicativo que você deseja monitorar com a integração da API do Cloud App Security, é recomendável criar uma conta de serviço de administrador dedicada para o Cloud App Security.  
  
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
  
    -   Com a quais parceiros você está compartilhando arquivos? (compartilhamento de saída)  
  
    -   Há quaisquer arquivos que contenham um nome confidencial?  
  
    -   Qualquer um dos arquivos está sendo compartilhado com a conta pessoal de outra pessoa?  
  
3.  Vá para **Investigar** e **Contas** e verifique o seguinte:  
  
    -   Existe alguma conta que não esteve ativa em um serviço específico por um longo período e talvez você possa revogar a licença desse usuário para esse serviço?  
  
    -   Você deseja saber quais usuários têm uma função específica?  
  
    -   Alguém foi demitido, mas ainda tem acesso a um aplicativo e pode usar esse acesso para roubar informações?  
  
    -   Você deseja revogar a permissão do usuário para um aplicativo específico ou exigir que um usuário específico execute a autenticação multifator?  
  
4.  Vá para **Investigar** e, em seguida, selecione um aplicativo. Você chegará ao painel do aplicativo, que fornece informações e insights para que possa usar as guias na parte superior para verificar o seguinte:  
  
     ![investigar aplicativo](./media/investigate-app.png "investigate app")  
  
    -   Que tipo de dispositivos seus usuários estão usando para se conectar ao aplicativo?  
  
    -   Quais tipos de arquivos eles estão salvando na nuvem?  
  
    -   Que atividade está acontecendo no aplicativo agora?  
  
    -   Há que quaisquer aplicativos de terceiros conectados ao seu ambiente?  
  
    -   Você estiver familiarizado com esses aplicativos?  
  
    -   Eles estão autorizados para o nível de acesso para o qual têm permissão?  
  
    -   Quantos usuários o implantaram? Quão comuns são esses aplicativos em geral?  
  
5.  Vá para o **Cloud Discovery Dashboard (Painel do Cloud Discovery)** e verifique o seguinte:  
  
    -   Quais aplicativos de nuvem estão sendo usados, até que ponto e por quem?  
  
    -   Para quais fins eles estão sendo usados?  
  
    -   Quantos dados estão sendo carregados nesses aplicativos de nuvem?  
  
    -   Em quais categorias você tem aplicativos de nuvem sancionados e, ainda assim, os usuários estão usando soluções alternativas?  
  
    -   Para a solução alternativa, há aplicativos de nuvem para os quais você deseja cancelar a sanção na sua organização?  
  
    -   Há aplicativos de nuvem que são usados, mas não estão em conformidade com a política da sua organização?  
  
## <a name="how-to-use-reports-to-investigate-risk"></a>Como usar relatórios para investigar os riscos  
Ao começar a tentar obter controle sobre seu ambiente de nuvem, determinadas suposições são feitas com base no que se espera encontrar, ou seja, você ainda não conhece realmente a nuvem. E, com base nessas suposições, cria políticas. Após o Cloud App Security ser executado em seu ambiente de nuvem, você pode usar os relatórios internos (bem como relatórios personalizados) para ver o que realmente está acontecendo na nuvem e, com base nisso, ajustar as políticas novamente para incluir exceções para que, por fim, sua política capture pouquíssimos falsos positivos.  
  
Os relatórios internos oferecem exibições agregadas para investigação.  
  
Para trabalhar com relatórios internos, vá para **Investigar** e para **Relatórios internos**. Para obter mais informações sobre os vários relatórios internos, consulte a [Referência do relatório interno](built-in-report-reference.md).  
  
## <a name="sample-investigation"></a>Investigação de amostra  
Digamos que você supõe que não há nenhum acesso ao seu ambiente de nuvem por endereços IP arriscados (por exemplo, proxies anônimos e Tor). Mas você cria uma política de IP arriscado para garantir:  
  
1.  No portal, vá até **Controlar** e selecione **Políticas**.  
  
2.  No **Centro de políticas**, clique na guia **Modelos**.  
  
3.  No final da linha **Logon do usuário usando um endereço IP não categorizado**, clique no **+** para criar uma nova política.  
  
4.  Altere o nome da política para que você seja capaz de identificar essa política.  
  
5.  Em **Filtros de atividade**, clique no **+** para adicionar um filtro. Role para baixo até **Marca de IP** e, em seguida, selecione **Anônimo** e **Tor**.  
  
     ![exemplo de ips arriscados de política](./media/example-policy-risky-ips.png "example policy risky ips")  
  
Agora que você tem a política em vigor, está surpreso ao ver que recebe um alerta de que a política foi violada.  
  
1.  Vá para a página **Alertas** e exiba o alerta sobre a violação da política.  
  
2.  Se você notar que parece uma violação real, desejará conter o risco ou corrigir.  
  
     Para conter o risco, você pode enviar uma notificação para o usuário para perguntar se a violação foi intencional e se o usuário estava ciente dela.  
  
     Você também pode detalhar o alerta e suspender o usuário até que possa descobrir o que precisa ser feito.  
  
3.  Se for um evento permitido que provavelmente não ocorrerá novamente, você poderá ignorar o alerta.  
  
     Se for permitido e espera-se que ocorra novamente, você poderá modificar a política para evitar que esse tipo de evento seja considerado uma violação no futuro.  
  
## <a name="see-also"></a>Veja também  
[Controle](control.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Oct16_HO4-->



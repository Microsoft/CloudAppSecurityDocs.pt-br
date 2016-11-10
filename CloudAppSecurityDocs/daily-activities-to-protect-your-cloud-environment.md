---
title: "Atividades diárias para proteger seu ambiente de nuvem | Microsoft Docs"
description: "Este artigo fornece uma base para o que você deve fazer no Cloud App Security regularmente para usá-lo para monitorar o uso de aplicativos de nuvem em sua organização."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: a835fa24-15c5-4bbb-a25a-688444040f1f
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed4ea71b24767d3602d40894d1cbac7447bcd8a2
ms.openlocfilehash: cc6a6e4b41b6660462c9c873469a1e8c9af97c4e


---

# <a name="daily-activities-to-protect-your-cloud-environment"></a>Atividades diárias para proteger seu ambiente de nuvem
Depois de colocar o Cloud App Security em funcionamento e configurar fluxos de dados, sancionar todos os aplicativos que deseja que as pessoas usem e definir políticas para monitorar seu ambiente de rede, é hora de usá-lo para controlar e proteger sua nuvem e gerenciar o risco.  
  
Este tópico descreve o que você deve fazer diariamente.  
  
## <a name="check-the-dashboard"></a>Verificar o painel  
Quando você abre o portal do Cloud App Security, é fornecida uma visão geral dos alertas abertos, das violações de atividade, das violações de conteúdo, um mapa de atividades que fornece um mapa que plota de onde, geograficamente, a atividade do usuário é originada e as tendências de uso do aplicativo conectado no seu ambiente de rede.  
  
É recomendável que você verifique o painel diariamente para ver quais novos alertas foram disparados e tratá-los. Também é bom ficar atento à integridade do seu ambiente de nuvem para ter uma ideia do que está acontecendo, em um alto nível, em seu ambiente de nuvem.  
  
![painel](./media/dashboard.png "dashboard")  
  
## <a name="handle-your-alerts"></a>Tratar os alertas  
Os alertas são o ponto de entrada para compreender seu ambiente de nuvem mais profundamente. Você talvez queira criar novas políticas com base no que encontrar. Por exemplo, você pode ver um administrador fazendo logon da Groenlândia e decidir que no futuro deseja criar uma política que suspende automaticamente uma conta de administrador quando ela é usada para fazer logon da Groenlândia.  
  
É uma boa ideia examinar todos os alertas e usá-los como uma ferramenta para modificar suas políticas. Se eventos inofensivos estiverem sendo considerados violações das políticas existentes, você deverá refinar suas políticas para receber menos alertas desnecessários.  
  
-   Em **Alertas abertos**, clique em **Exibir todos os alertas**.  
  
     Isso oferece visibilidade completa de qualquer atividade suspeita ou violação de suas políticas estabelecidas e ajuda a proteger a postura de segurança que você definiu para o seu ambiente de nuvem.  
  
     ![alertas](./media/alerts.png "alerts")  
  
-   Para cada alerta, você precisa investigar e determinar a natureza da violação e a resposta necessária.  
  
     Você pode filtrar os alertas por **Tipo de alerta** ou **Gravidade** para processar os mais importantes primeiro.  
  
     Clique em um alerta específico. Dependendo do tipo de alerta, você receberá várias ações que podem ser executadas antes de resolver o alerta.  
  
     Há três tipos de violações com os quais você precisará lidar ao investigar os alertas:  
  
    -   **Violações graves** que exigem resposta imediata  
  
         Exemplos:  
  
         Para um alerta de atividade suspeita, talvez você deseje suspender a conta até que o usuário altere sua senha.  
  
         Para um vazamento de dados, talvez você deseje restringir as permissões ou colocar o arquivo em quarentena.  
  
         Se um novo serviço não sancionado for descoberto, talvez você deseje bloquear o acesso ao serviço no proxy ou firewall.  
  
    -   **Violações questionáveis** que exigem mais investigação  
  
         Você pode contatar o usuário ou o gerente do usuário sobre a natureza da atividade.  
  
         Deixe a atividade aberta até ter mais informações.  
  
    -   **Violações autorizadas ou comportamento anômalo** que resultaram de uso legítimo.  
  
         Ignore o alerta.  
  
-   Ao concluir esse processo, marque o alerta como resolvido.  
  
A tabela a seguir fornece uma lista dos tipos de alertas que podem ser disparados e as maneiras recomendadas pelas quais você pode resolvê-los.  
  
|Tipo de alerta|Descrição|Resolução recomendada|  
|----------------|-----------------|----------------------------|  
|Violação de política de atividade|Este tipo de alerta é o resultado de uma política que você criou.|- Para trabalhar com esse tipo de alerta em massa, é recomendável trabalhar diretamente de dentro do Centro de políticas para mitigá-los.<br />-   Ajuste a política para excluir entidades ruidosas adicionando mais filtros e mais controles granulares.<br />- Se a política for muito precisa e o alerta foi garantido e for uma violação que você deseja parar imediatamente, considere mudar para uma resposta automatizada adicionando a correção automática à política.|  
|Violação de política de arquivos|Este tipo de alerta é o resultado de uma política que você criou.|- Para trabalhar com esse tipo de alerta em massa, é recomendável trabalhar diretamente de dentro do Centro de políticas para mitigá-los.<br />-   Ajuste a política para excluir entidades ruidosas adicionando mais filtros e mais controles granulares.<br />- Se a política for muito precisa e o alerta foi garantido e for uma violação que você deseja parar imediatamente, considere mudar para uma resposta automatizada adicionando a correção automática à política.|  
|Conta comprometida|Este tipo de alerta é disparado quando o Cloud App Security identifica uma conta que foi comprometida (probabilidade muito alta de a conta ter sido usada de uma forma não autorizada).|É recomendável que você suspenda a conta até entrar em contato com o usuário e garantir que ele altere a senha.|  
|Conta inativa|Este alerta é disparado quando uma conta não é mais usada em um dos seus aplicativos de nuvem conectados.|Entre em contato com o usuário e o gerente do usuário para determinar se a conta ainda está ativa. Caso contrário, suspenda o usuário e encerre a licença para o aplicativo.|  
|Novo usuário administrador|Isso alerta você para as alterações em suas contas com privilégios para aplicativos conectados.|Confirme se as novas permissões de administrador são realmente necessárias para o usuário e, se não, é recomendável revogar os privilégios de administrador para reduzir a exposição.|  
|Novo local de administração|Isso alerta você para as alterações em suas contas com privilégios para aplicativos conectados.|Confirme se o logon deste local anômalo foi legítimo e, se não, é recomendável revogar as permissões de administrador ou suspender a conta para reduzir a exposição.|  
|Novo local|Este é um alerta informativo sobre o acesso a um aplicativo conectado de um novo local e é disparado apenas uma vez por país.|Investigue a atividade do usuário específico.|  
|Novo serviço descoberto|Este é um alerta sobre a TI sombra, um novo aplicativo foi detectado pelo Cloud Discovery.|<ul><li>Avalie o risco do serviço com base no catálogo de aplicativos.</li><li>Analise a atividade para entender a predominância e os padrões de uso.</li><li>Decida se deseja sancionar ou cancelar a sanção do aplicativo.<br /><br />     Para aplicativos não sancionados:<br /><br /> <ul><li>Talvez você queira bloquear uso no seu proxy ou firewall.</li><li>Se ele não for sancionado e você tiver um aplicativo sancionado na mesma categoria, poderá analisar detalhadamente e exportar uma lista de usuários do aplicativo não sancionado e entrar em contato com eles para migrá-los para o aplicativo sancionado.</li></ul></li></ul>|  
|Atividade suspeita|Esse alerta permite que você saiba que foi detectada uma atividade anômala que não está alinhada com atividades esperadas ou usuários em sua organização.|Investigue o comportamento e confirme-o com o usuário.<br /><br /> Este tipo de alerta é um ótimo lugar para começar a aprender mais sobre seu ambiente e o uso desses alertas para criar novas políticas. Por exemplo, se alguém repentinamente carrega uma grande quantidade de dados para um dos seus aplicativos conectados, você pode definir uma regra para controlar esse tipo de comportamento anômalo.|  
|Uso de nuvem suspeito|Esse alerta permite que você saiba que foi detectada uma atividade anômala que não está alinhada com atividades esperadas ou usuários em sua organização.|Investigue o comportamento e confirme-o com o usuário.<br /><br /> Este tipo de alerta é um ótimo lugar para começar a aprender mais sobre seu ambiente e o uso desses alertas para criar novas políticas. Por exemplo, se alguém repentinamente carrega uma grande quantidade de dados para um dos seus aplicativos conectados, você pode definir uma regra para controlar esse tipo de comportamento anômalo.|  
|Uso de conta pessoal|Esse alerta informa que uma nova conta pessoal tem acesso a recursos em seus aplicativos conectados.|Na conta externa, remova as colaborações do usuário.|  
  
## <a name="use-policies-to-assess-risk"></a>Usar políticas para avaliar os riscos  
Depois que você examinar os alertas abertos, vá para o **Centro de políticas** para examinar as violações de política que não dispararam alertas.  
  
-   No portal do Cloud App Security, clique em **Controle** e em **Políticas**.  
  
-   Clique em uma política específica para ver a lista **Violating now (Em violação agora)** das correspondências de política que não dispararam alertas.  
  
-   Clique nas violações, uma de cada vez, e decida o que fazer para cada uma. Para obter mais informações sobre as ações de governança, veja abaixo.  
  
     Por exemplo, se a política estiver definida para encontrar violações de conformidade e alguém salvar os números de cartão de crédito em arquivos no OneDrive, você terá uma correspondência na política.  
  
     ![correspondências de pci](./media/pci-matches.png "pci matches")  
  
-   Clique na correspondência para ver os arquivos reais que violaram a política.  
  
     ![correspondências de conteúdo de pci](./media/pci-content-matches.png "pci content matches")  
  
     Você pode clicar no próprio arquivo para obter informações sobre os arquivos.  
  
     Você pode clicar em **Colaboradores** para ver quem tem acesso a esse arquivo.  
  
     Você pode clicar nas **Correspondências** para ver os números de cartão de crédito reais.  
  
     ![ccn de correspondências de conteúdo](./media/content-matches-ccn.png "content matches ccn")  
  
## <a name="see-also"></a>Veja também  
[Investigar](investigate.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Oct16_HO4-->



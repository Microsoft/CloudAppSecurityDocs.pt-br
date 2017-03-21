---
title: "Atividades diárias para proteger seu ambiente de nuvem | Microsoft Docs"
description: "Este artigo fornece uma base para o que você deve fazer no Cloud App Security regularmente para usá-lo para monitorar o uso de aplicativos de nuvem em sua organização."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/23/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: a835fa24-15c5-4bbb-a25a-688444040f1f
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 28068d41d44aa0b2f7a5e5950546a5e185d77eba
ms.sourcegitcommit: 355226ee21981563066d637e7db0bff0d53c2da6
translationtype: HT
---
# <a name="daily-activities-to-protect-your-cloud-environment"></a>Atividades diárias para proteger seu ambiente de nuvem
Depois de colocar o Cloud App Security em funcionamento, será necessário configurar fluxos de dados, sancionar os aplicativos que deseja permitir que as pessoas usem e definir políticas para monitorar seu ambiente de nuvem. Em seguida, você pode usar o Cloud App Security para controlar e proteger sua nuvem e gerenciar os riscos.  

Este tópico descreve o que você deve fazer com o Cloud App Security diariamente.  

## <a name="check-the-dashboard"></a>Verificar o painel  
O painel do Cloud App Security fornece uma visão geral das atividades e recursos, incluindo:

- Alertas abertos.
- Violações de atividade.
- Violações de conteúdo.
- Um mapa de atividades que rastreia de onde a atividade do usuário foi originada.
- Tendências de uso do aplicativo conectado em seu ambiente de nuvem.  

É recomendável verificar o painel diariamente para ver quais novos alertas foram acionados. Também é bom ficar atento à integridade do seu ambiente de nuvem para ter uma ideia do que está acontecendo em seu ambiente de nuvem.  

![Painel do Cloud App Security](./media/dashboard.png "painel")  

## <a name="handle-your-alerts"></a>Tratar os alertas  
Os alertas são os pontos de entrada para compreender seu ambiente de nuvem mais profundamente. Você talvez queira criar novas políticas com base no que encontrar. Por exemplo, talvez você veja um administrador se conectando da Groenlândia e ninguém na sua empresa nunca se conectou da Groenlândia antes. Você pode criar uma política que suspende automaticamente uma conta de administrador quando ela é usada para entrar nesse local.  

É uma boa ideia examinar todos os alertas e usá-los como ferramentas para modificar suas políticas. Se eventos inofensivos estiverem sendo considerados violações das políticas existentes, refine suas políticas para receber menos alertas desnecessários.  

1.   Em **Alertas abertos**, clique em **Exibir todos os alertas**.  

     Esta seção do painel fornece uma visibilidade completa de qualquer atividade suspeita ou violação de suas políticas estabelecidas. Ela ajuda a proteger a postura de segurança que você definiu para o seu ambiente de nuvem.  

     ![Alertas](./media/alerts.png "alertas")  

2.   Para cada alerta, você precisa investigar e determinar a natureza da violação e a resposta necessária.  

     Você pode filtrar os alertas por Tipo de alerta ou Gravidade para processar os mais importantes primeiro.  

     Selecione um alerta específico. Dependendo do tipo de alerta, você receberá várias ações que podem ser executadas antes de resolver o alerta.  

     Há três tipos de violações com os quais você precisará lidar ao investigar os alertas:  

    #### <a name="serious-violations"></a>Violações graves
     Violações graves exigem resposta imediata.

         Examples:  

         For a suspicious activity alert, you might want to suspend the account until the user changes their password.  

         For a data leak you might want to restrict permissions or quarantine the file.  

         If a new app is discovered, you might want to block access to the service on your proxy or firewall.  

    #### <a name="questionable-violations"></a>Violações questionáveis
    Violações questionáveis exigem mais investigação.  

         You can contact the  user or the user's manager about the nature of the activity.  

         Leave the activity open until you have more information.  

 #### <a name="authorized-violations-or-anomalous-behavior"></a>Violações autorizadas ou comportamento anormal
 Violações autorizadas ou comportamento anormal podem resultar de uso legítimo.  

         Dismiss the alert.  

3.   Ao concluir esse processo, marque o alerta como resolvido.  

A tabela a seguir fornece uma lista dos tipos de alertas que podem ser disparados e recomenda maneiras pelas quais você pode resolvê-los.  

|Tipo de alerta|Descrição|Resolução recomendada|  
|----------------|-----------------|----------------------------|  
|Violação de política de atividade|Este tipo de alerta é o resultado de uma política que você criou.|Para trabalhar com esse tipo de alerta em massa, é recomendável trabalhar no Centro de políticas para mitigá-los.<br /><br /> Ajuste a política para excluir entidades ruidosas adicionando mais filtros e mais controles granulares.<br /><br /> Se a política for precisa, o alerta for garantido e for uma violação que você deseja parar imediatamente, considere adicionar a correção automática à política.|  
|Violação de política de arquivos|Este tipo de alerta é o resultado de uma política que você criou.| Para trabalhar com esse tipo de alerta em massa, é recomendável trabalhar no Centro de políticas para mitigá-los.<br /><br /> Ajuste a política para excluir entidades ruidosas adicionando mais filtros e mais controles granulares.<br /><br /> Se a política for precisa, o alerta for garantido e for uma violação que você deseja parar imediatamente, considere adicionar a correção automática à política.|  
|Conta comprometida|Este tipo de alerta é disparado quando o Cloud App Security identifica uma conta que foi comprometida, o que significa uma probabilidade muito alta de a conta ter sido usada de uma forma não autorizada.|Recomendamos que você suspenda a conta até entrar em contato com o usuário e garantir que ele altere a senha.|  
|Conta inativa|Este alerta é disparado quando uma conta não é usada durante 60 dias em um dos seus aplicativos de nuvem conectados.|Entre em contato com o usuário e o gerente do usuário para determinar se a conta ainda está ativa. Caso contrário, suspenda o usuário e encerre a licença para o aplicativo.|  
|Novo usuário administrador|Isso alerta você para as alterações em suas contas com privilégios para aplicativos conectados.|Confirme se as novas permissões de administrador na verdade são necessárias para o usuário. Se não forem, recomendamos revogar privilégios de administrador para reduzir a exposição.|  
|Novo local de administração|Isso alerta você para as alterações em suas contas com privilégios para aplicativos conectados.|Confirme se a entrada desse local anormal foi legítima. Se não for, recomendamos revogar as permissões de administrador ou suspender a conta para reduzir a exposição.|  
|Novo local|Este é um alerta informativo sobre o acesso a um aplicativo conectado de um novo local e é disparado apenas uma vez por país.|Investigue a atividade do usuário específico.|  
|Novo serviço descoberto|Este é um alerta sobre a TI invisível, um novo aplicativo foi detectado pelo Cloud Discovery.|<ul><li>Avalie o risco do serviço com base no catálogo de aplicativos.</li><li>Analise a atividade para entender a predominância e os padrões de uso.</li><li>Decida se deseja sancionar ou cancelar a sanção do aplicativo.</li><br /></ul>Para aplicativos não sancionados:<br /><br /><ul><li>Talvez você queira bloquear uso no seu proxy ou firewall.</li><li>Se você tiver um aplicativo não sancionado e um aplicativo sancionado na mesma categoria, poderá exportar uma lista de usuários do aplicativo não sancionado e entrar em contato com eles para migrá-los para o aplicativo sancionado.</li></ul></li>|  
|Atividade suspeita|Esse alerta permite que você saiba que foi detectada uma atividade anômala que não está alinhada com atividades esperadas ou usuários em sua organização.|Investigue o comportamento e confirme-o com o usuário.<br /><br /> Este tipo de alerta é um ótimo lugar para começar a aprender mais sobre seu ambiente e criar novas políticas com esses alertas. Por exemplo, se alguém repentinamente carrega uma grande quantidade de dados para um dos seus aplicativos conectados, você pode definir uma regra para controlar esse tipo de comportamento anômalo.|  
|Uso de nuvem suspeito|Esse alerta permite que você saiba que foi detectada uma atividade anômala que não está alinhada com atividades esperadas ou usuários em sua organização.|Investigue o comportamento e confirme-o com o usuário.<br /><br /> Este tipo de alerta é um ótimo lugar para começar a aprender mais sobre seu ambiente e criar novas políticas com esses alertas. Por exemplo, se alguém repentinamente carrega uma grande quantidade de dados para um dos seus aplicativos conectados, você pode definir uma regra para controlar esse tipo de comportamento anômalo.|  
|Uso de conta pessoal|Esse alerta informa que uma nova conta pessoal tem acesso a recursos em seus aplicativos conectados.|Remover as colaborações do usuário na conta externa.|  

## <a name="use-policies-to-assess-risk"></a>Usar políticas para avaliar os riscos  
Depois que você examinar os alertas abertos, vá para o Centro de políticas para examinar as violações de política que não dispararam alertas.  

-   No painel do Cloud App Security, clique em **Controle** e em **Políticas**.  

-   Selecione uma política específica para ver a lista **Em violação agora** das correspondências de política que não dispararam alertas.  

-   Clique nas violações, uma de cada vez, e decida o que fazer para cada uma. Consulte as seguintes figuras, para obter mais informações sobre as ações de governança.  

     Se a política estiver definida para encontrar violações de conformidade e alguém salvar os números de cartão de crédito em arquivos no OneDrive, você terá uma correspondência na política.  

     ![Correspondências de PCI](./media/pci-matches.png "correspondências de pci")  

-   Selecione a correspondência para ver os arquivos reais que violaram a política.  

     ![Correspondências de conteúdo de PCI](./media/pci-content-matches.png "correspondências de conteúdo de pci")  

     Você pode selecionar o próprio arquivo para obter informações sobre os arquivos.  

     Você pode clicar em **Colaboradores** para ver quem tem acesso a esse arquivo.  

     Você pode clicar nas **Correspondências** para ver os números de cartão de crédito reais.  

     ![Ccn de correspondências de conteúdo](./media/content-matches-ccn.png "ccn de correspondências de conteúdo")  

## <a name="next-steps"></a>Próximas etapas  
Para obter mais informações sobre como investigar alertas, consulte [Investigar](investigate.md).  
Para obter suporte técnico, visite a página de [suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
Os clientes Premier também podem escolher o Cloud App Security diretamente no [Portal Premier.](https://premier.microsoft.com/)  

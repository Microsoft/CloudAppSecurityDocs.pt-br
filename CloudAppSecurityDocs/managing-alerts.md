---
title: Gerenciar alertas acionados no Cloud App Security
description: Este artigo explica como trabalhar com alertas gerados no portal do Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/10/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 1b1dbcc6-472f-43ea-af59-2aa926e3e5a9
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 34fe83d4d6300037d31f577029f0b4887c7108e2
ms.sourcegitcommit: b86c3afd1093fbc825fec5ba4103e3a95f65758e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53176807"
---
# <a name="manage-alerts"></a>Gerenciar alertas

*Aplica-se a: Microsoft Cloud App Security*

Este artigo explica como trabalhar com alertas gerados no portal do Cloud App Security.

## <a name="manage-your-alerts"></a>Gerenciar os alertas

Os alertas são os pontos de entrada para compreender seu ambiente de nuvem mais profundamente. Você talvez queira criar novas políticas com base no que encontrar. Por exemplo, talvez você veja um administrador se conectando da Groenlândia e ninguém na sua empresa nunca se conectou da Groenlândia antes. Você pode criar uma política que suspende automaticamente uma conta do administrador quando ela é usada para entrar nessa localização.  

É uma boa ideia examinar todos os alertas e usá-los como ferramentas para modificar suas políticas. Se eventos inofensivos estiverem sendo considerados violações das políticas existentes, refine suas políticas para receber menos alertas desnecessários.  

1. Na página **Alertas**, selecione **Abrir** para o **Status de resolução**.  

   Esta seção do painel fornece uma visibilidade completa de qualquer atividade suspeita ou violação de suas políticas estabelecidas. Pode ajudá-lo a proteger a postura de segurança que você definiu para o seu ambiente de nuvem.  

   ![Alertas](./media/alerts.png "alertas")  

2. Para cada alerta, você precisa investigar e determinar a natureza da violação e a resposta necessária.  

   - Você pode filtrar os alertas por Tipo de alerta ou Gravidade para processar os mais importantes primeiro.  

   - Selecione um alerta específico. Dependendo do tipo de alerta, você receberá várias ações que podem ser executadas antes de resolver o alerta.  
   
   - É possível filtrar com base no aplicativo. Os aplicativos listados são aqueles nos quais foram detectadas atividades pelo Cloud App Security.

   - Há três tipos de violações com os quais você precisará lidar ao investigar os alertas:  

       - **Violações graves** – violações graves exigem resposta imediata. <br>
     *Exemplos:*
         - Para um alerta de atividade suspeita, talvez seja necessário suspender a conta até que o usuário altere sua senha.  
         - Em caso de perda de dados, talvez você deseje restringir as permissões ou colocar o arquivo em quarentena.  
         - Se um novo aplicativo for descoberto, talvez você queira bloquear o acesso ao serviço em seu proxy ou firewall.  

       - **Violações questionáveis** – violações questionáveis exigem mais investigação.  <br>
         - Você pode contatar o usuário ou o gerente do usuário sobre a natureza da atividade.
         - Deixe a atividade aberta até ter mais informações.  

       - **Violações autorizadas ou comportamento anômalo** – violações autorizadas ou comportamento anômalo pode resultar de uso legítimo. <br>
         - Você pode ignorar o alerta.


3. Sempre que você ignora um alerta, é importante enviar comentários sobre o motivo pelo qual você o está ignorando. A equipe do Cloud App Security usa esses comentários como uma indicação da precisão do alerta. Em seguida, essas informações são usadas para ajustar nossos modelos de machine learning para alertas futuros. Você pode seguir estas diretrizes para decidir como categorizar o alerta:
   - Se o uso legítimo disparou o alerta e esse não é um problema de segurança, ele pode ser um destes tipos: 

     - Benigno positivo: O alerta é preciso, mas a atividade é legítima. Você deve ignorar o alerta e definir o motivo como **A gravidade real é menor** ou **Não interessante**.
     -  Falso positivo: O alerta é impreciso. Ignore o alerta e defina o motivo pelo qual o **Alerta não é preciso**.
   - Se houver muito ruído para determinar a legitimidade e a precisão de um alerta, ignore-o e defina o motivo como **Excesso de alertas semelhantes**.
   - Verdadeiro positivo: Se o alerta estiver relacionado a um evento de risco real que foi confirmado de modo mal-intencionado ou inadvertidamente por alguém de dentro ou fora da organização, defina o evento como **Resolver** depois de terem sido tomadas todas as devidas providências para corrigir o evento.

## <a name="alert-types"></a>Tipos de alerta

A tabela a seguir fornece uma lista dos tipos de alertas que podem ser disparados e recomenda maneiras pelas quais você pode resolvê-los.  

|Tipo de alerta|Descrição|Resolução recomendada|  
|----------------|-----------------|----------------------------|  
|Violação de política de atividade|Este tipo de alerta é o resultado de uma política que você criou.|Para trabalhar com esse tipo de alerta em massa, é recomendável trabalhar no Centro de políticas para mitigá-los.<br /><br /> Ajuste a política para excluir entidades ruidosas adicionando mais filtros e mais controles granulares.<br /><br /> Se a política for precisa, o alerta for garantido e for uma violação que você deseja parar imediatamente, considere adicionar a correção automática à política.|  
|Violação de política de arquivos|Este tipo de alerta é o resultado de uma política que você criou.| Para trabalhar com esse tipo de alerta em massa, é recomendável trabalhar no Centro de políticas para mitigá-los.<br /><br /> Ajuste a política para excluir entidades ruidosas adicionando mais filtros e mais controles granulares.<br /><br /> Se a política for precisa, o alerta for garantido e for uma violação que você deseja parar imediatamente, considere adicionar a correção automática à política.|  
|Conta comprometida|Este tipo de alerta é disparado quando o Cloud App Security identifica uma conta que foi comprometida. Isso significa que há uma probabilidade muito alta de que a conta ter sido usada de maneira não autorizada.|Recomendamos que você suspenda a conta até entrar em contato com o usuário e garantir que ele altere a senha.|  
|Conta inativa|Este alerta é disparado quando uma conta não é usada durante 60 dias em um dos seus aplicativos de nuvem conectados.|Entre em contato com o usuário e o gerente do usuário para determinar se a conta ainda está ativa. Caso contrário, suspenda o usuário e encerre a licença para o aplicativo.|  
|Novo usuário administrador|Alerta você para as alterações em suas contas com privilégios para aplicativos conectados.|Confirme se as novas permissões de administrador na verdade são necessárias para o usuário. Se não forem, recomendamos revogar privilégios de administrador para reduzir a exposição.|  
|Novo local de administração|Alerta você para as alterações em suas contas com privilégios para aplicativos conectados.|Confirme se a entrada dessa localização anormal foi legítima. Se não for, recomendamos revogar as permissões de administrador ou suspender a conta para reduzir a exposição.|  
|Novo local|Um alerta informativo sobre o acesso a um aplicativo conectado de uma nova localização e é disparado apenas uma vez por país.|Investigue a atividade do usuário específico.|  
|Novo serviço descoberto|Este alerta é um alerta sobre TI sombra. Um novo aplicativo foi detectado pelo Cloud Discovery.|<ul><li>Avalie o risco do serviço com base no catálogo de aplicativos.</li><li>Analise a atividade para entender a predominância e os padrões de uso.</li><li>Decida se deseja sancionar ou cancelar a sanção do aplicativo.</li><br /></ul>Para aplicativos não sancionados:<br /><br /><ul><li>Talvez você queira bloquear uso no seu proxy ou firewall.</li><li>Se você tiver um aplicativo não sancionado e um aplicativo sancionado na mesma categoria, poderá exportar uma lista de usuários do aplicativo não sancionado. Em seguida, entre em contato com eles para migrá-los para o aplicativo sancionado.</li></ul></li>|  
|Atividade suspeita|Esse alerta permite que você saiba que foi detectada uma atividade anômala que não está alinhada com atividades esperadas ou usuários em sua organização.|Investigue o comportamento e confirme-o com o usuário.<br /><br /> Este tipo de alerta é um ótimo lugar para começar a aprender mais sobre seu ambiente e criar novas políticas com esses alertas. Por exemplo, se alguém repentinamente carrega uma grande quantidade de dados para um dos seus aplicativos conectados, você pode definir uma regra para controlar esse tipo de comportamento anômalo.|  
|Uso de nuvem suspeito|Esse alerta permite que você saiba que foi detectada uma atividade anômala que não está alinhada com atividades esperadas ou usuários em sua organização.|Investigue o comportamento e confirme-o com o usuário.<br /><br /> Este tipo de alerta é um ótimo lugar para começar a aprender mais sobre seu ambiente e criar novas políticas com esses alertas. Por exemplo, se alguém repentinamente carrega uma grande quantidade de dados para um dos seus aplicativos conectados, você pode definir uma regra para controlar esse tipo de comportamento anômalo.|  
|Uso de conta pessoal|Esse alerta informa que uma nova conta pessoal tem acesso a recursos em seus aplicativos conectados.|Remover as colaborações do usuário na conta externa.|  


## <a name="next-steps"></a>Próximas etapas  
Para obter mais informações sobre como investigar alertas, consulte [Investigar](investigate.md).  

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/)  

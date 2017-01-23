---
title: "Políticas de atividade | Microsoft Docs"
description: "Este tópico fornece instruções para criar e trabalhar com políticas de atividade."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/19/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 99d5fd37-d922-4269-b557-86d7f84180eb
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2997a79f2e0fd730302be2602b6aee6ec56999db
ms.openlocfilehash: 46ab0f13a8d0839f77525c334e75c840c9bfc73f


---

# <a name="activity-policies"></a>Políticas de atividade
As políticas de atividade permitem que você aplique uma ampla gama de processos automatizados, utilizando as APIs do provedor de aplicativo. Essas políticas permitem que você monitore atividades específicas realizadas por vários usuários ou siga altas taxas inesperadas de um determinado tipo de atividade.  
  
Depois de definir uma política de detecção de atividades, ele começará a gerar alertas, os quais são gerados apenas em atividades que ocorrem depois da criação da política.
  
  
## <a name="custom-alerts"></a>Alertas personalizados  
As políticas de atividade permitem que você defina alertas personalizados para serem enviados ou ações para serem realizadas quando a atividade do usuário é detectada. Por exemplo, se você quiser saber sempre que um usuário tenta fazer logon e falha 70 vezes em um minuto ou se um usuário baixa 7.000 arquivos ou se conecta do Afeganistão, você poderá definir alertas de atividade a serem enviados para você ou para o usuário quando esses eventos ocorrerem. Você pode até mesmo suspender o usuário até ter tempo de investigar o que ocorreu.  
  
Para criar uma nova política de atividade, siga este procedimento:  
  
1.  No console, clique em **Controlar** seguido por **Políticas**.  
  
2.  Clique em **Criar política** e selecione **Política de atividade**.  
  
     ![menu de política de atividade](./media/activity-policy-menu.png "menu de política de atividade")  
  
3.  Atribua um nome e uma descrição à sua política. Se desejar, poderá baseá-la em um modelo. Para obter mais informações sobre modelos de política, consulte [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md).  
  
4.  Para definir quais ações ou outras métricas vão disparar essa política, trabalhe com os **filtros de atividade**.  
  
5.  Em **Parâmetros de correspondência de atividade**, selecione se a violação da política será disparada quando uma única atividade corresponder aos filtros ou se uma violação será detectada apenas quando um número especificado de **Atividades repetidas** for detectado.  
    Se você escolher **Atividade repetida**, será possível definir **Agrupar atividades correspondentes por aplicativo**. Isso vai disparar uma correspondência de política apenas quando as atividades repetidas ocorrerem no mesmo aplicativo (por exemplo, cinco downloads do Box).  
  
6.  Configure as **Ações** que devem ser executadas quando uma correspondência for encontrada.  
  
Veja esses exemplos:  
  
-   Vários logons com falha  
  
     Você pode definir sua política para que receba um alerta quando houve um grande número de tentativas de logon com falha dentro de um determinado período relativamente curto. Para configurar uma política assim, escolha o filtro de atividade apropriado na página **Nova Política de Atividade**.  
  
     No campo **Filtros de atividade**, configure os parâmetros para os quais o alerta será disparado.  
  
     ![exemplo de política de falha no logon após várias tentativas](./media/multiple-failed-log-on-attempts-policy-example.png "exemplo de política de falha no logon após várias tentativas")  
  
-   Alta taxa de downloads  
  
     Você pode definir a política para que você receba um alerta quando houve um nível inesperado ou não característico de atividade de download. Para configurar uma política assim, nos parâmetros **Taxa**, escolha os parâmetros para disparar o alerta.  
  
     ![exemplo de alta taxa de downloads](./media/high-download-rate-example.png "exemplo de alta taxa de downloads")  
  
## <a name="anomaly-detection"></a>Detecção de anomalias  
Depois que sua organização estiver protegida pelo Cloud App Security, todas as atividades de nuvem serão pontuadas de acordo com vários fatores de risco predefinidos. O Cloud App Security examina cada sessão do usuário na nuvem e, em seguida, considera os fatores de risco definidos aqui para alertar você quando acontecer algo que seja diferente da linha de base da sua organização ou da atividade regular do usuário. A página de política de detecção de anomalias permite configurar e personalizar quais famílias de fatores de risco serão consideradas no processo de pontuação de risco. As políticas podem ser aplicadas de forma diferente para diferentes usuários, locais e setores organizacionais. Por exemplo, você pode criar uma política que o alerta quando os membros da sua equipe de TI estão ativos de fora do escritório.  
  
Para configurar uma política de detecção de anomalias:  
  
1.  No console, clique em **Controlar** seguido por **Políticas**.  
  
2.  Clique em **Criar política** e selecione a política de **Detecção de anomalias**.  
  
     ![Menu de política de detecção de anomalias](./media/anomaly-detection-policy-menu.png "Menu de política de detecção de anomalias")  
  
3.  Preencha o nome e a descrição da política e continue para o campo **Filtros de atividade**, no qual é possível escolher a atividade à qual deseja aplicar a política.  
  
4.  Atribua um nome e uma descrição à sua política. Se desejar, poderá baseá-la em um modelo. Para obter mais informações sobre modelos de política, consulte [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md).  
  
5.  Para aplicar a política a todas as atividades em seu ambiente de nuvem, selecione **Todas as atividades monitoradas**. Para limitar a política a tipos específicos de atividades, escolha **Atividade selecionada**. Clique em **Adicionar filtros** e defina os parâmetros apropriados pelos quais filtrar a atividade. Por exemplo, para impor a política somente em atividades realizadas por administradores do Salesforce, selecione essa marca.  
  
6.  Sob esse campo, defina os **Fatores de risco**. Você pode escolher quais famílias de risco deseja considerar ao calcular a pontuação de risco. À direita da linha, você pode usar o botão Ativar/Desativar para habilitar e desabilitar os vários riscos. Além disso, para maior granularidade, você pode escolher a atividade na qual habilitar cada família de risco específica.  
  
     Os fatores de risco são os seguintes:  
  
    -   **Falhas de logon**: os usuários estão tentando fazer logon e falhando várias vezes em um curto período?  
  
    -   **Atividade do administrador**: os administradores estão usando suas contas com privilégios para fazer logon de locais incomuns ou em horários estranhos?  
  
    -   **Contas inativas**: repentinamente há atividade em uma conta que não estava sendo usada há algum tempo?  
  
    -   **Local**: há atividade em um local novo, incomuns ou suspeito?  
  
    -   **Viagem impossível**: um usuário está fazendo logon de Denver e dez minutos depois de Paris?  
  
    -   **Agente de dispositivo e usuário**: há atividade de um dispositivo não reconhecido ou não gerenciado?  
  
     Você pode usar esses parâmetros para definir cenários complexos, por exemplo, para excluir o intervalo IP do seu escritório dos fatores de risco considerados para a detecção de anomalias, criar uma marca de “IP do escritório” específica e filtrar o intervalo sem os parâmetros considerados. Para então excluir o intervalo que você criou da detecção de anomalias da atividade do administrador:  
  
    -   Em **Tipo de risco**, localize **Atividade do Administrador**.  
  
    -   Altere **Aplicar a** para **Atividade Selecionada**.  
  
    -   Em **Filtros de atividade**, defina **Aplicar a** como **Atividade selecionada** e em **Activities matching all of the following (Atividades que correspondem a todas as a seguir)**, escolha **Atividade administrativa** é **True**.  
  
    -   Clique no ícone **+** e selecione **IP tag does not equal (Marca do IP diferente de)** e selecione a marca de IP do escritório.  
  
7.  Em **Sensibilidade**, selecione com que frequência você deseja receber alertas.  
  
     O valor de sensibilidade determinará quantos alertas semanais serão disparados em média para cada 1.000 usuários.  
  
     ![IPs de detecção de anomalias](./media/anomaly-detection-ips.png "IPs de detecção de anomalias")  
  
8.  Clique em **Criar**.  
 
  
## <a name="activity-policy-reference"></a>Referência de política de atividade  
Esta seção fornece detalhes de referência sobre as políticas, fornecendo explicações sobre cada tipo de política e os campos que podem ser configurados para cada política.  
  
Uma **Política de atividade** é uma política baseada em API que permite que você monitore as atividades da sua organização na nuvem, considerando mais de 20 filtros de metadados de arquivo (incluindo o tipo de dispositivo e o local). Com base nos resultados de política, as notificações podem ser geradas e os usuários podem ser suspensos do aplicativo de nuvem.   
Cada política é composta pelas seguintes partes:  
  
-   Filtros de atividade – permitem criar condições muito granulares com base nos metadados.  
  
-   Parâmetros de correspondência de atividade – permitem que você defina um limite para o número de vezes que uma atividade se repete para ser considerada como correspondente à política.  Especifique o número de atividades repetidas necessário para corresponder à política, por exemplo, definindo uma política para alertar quando um usuário executa dez tentativas de logon sem êxito em um período de dois minutos.  Por padrão, a configuração **Parâmetros de correspondência de atividade** gera uma correspondência para cada atividade que atende a todos os filtros de atividade.   
Usando **Atividade repetida**, você pode definir o número de atividades repetidas, a duração do período em que as atividades são contadas e até mesmo especificar que todas as atividades devem ser executadas pelo mesmo usuário e no mesmo aplicativo de nuvem.  
  
  
-   Ações – a política fornece a um conjunto de ações de governança que podem ser aplicadas automaticamente quando violações são detectadas.  
## <a name="see-also"></a>Veja também  
[Políticas de proteção de dados](data-protection-policies.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Dec16_HO3-->



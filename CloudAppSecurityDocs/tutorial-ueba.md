---
title: Investigar usuários arriscados | Microsoft Docs
description: Este tutorial descreve o processo para investigar usuários arriscados no Microsoft Cloud App Security em ambientes híbridos, integrando-o com o ATP do Azure.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: rkarlin
ms.date: 06/11/2019
ms.topic: tutorial
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: eac0b192-98d7-4939-9a07-1d4a7f8c39c3
ms.reviewer: dannyk
ms.suite: ems
ms.openlocfilehash: 80ef10622093523c92547de4bb52538b705ce168
ms.sourcegitcommit: 62778bfbc010b95cdef4c8aed23b0f195f382242
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/18/2019
ms.locfileid: "67171548"
---
# <a name="tutorial-investigate-risky-users"></a>Tutorial: Investigar usuários arriscados

*Aplica-se a: Microsoft Cloud App Security*

Integramos o Microsoft Cloud App Security à Proteção Avançada contra Ameaças do Azure para fornecer o recurso de UEBA (análise comportamental de usuários e entidades), a fim de viabilizar uma investigação detalhada no ambiente híbrido, tanto das atividades locais como do aplicativo de nuvem. 

Agora, o Cloud App Security fornece em um único portal todas as informações de que você precisa para tomar melhores decisões sobre riscos na organização, bem como para corrigir ativamente as ameaças. Use o Cloud App Security para iniciar a investigação de usuários em primeira mão, combinando alertas e analisando dados nesses sistemas, a fim de obter informações com baseadas em identidade, em um ambiente híbrido:
- O Microsoft Cloud App Security, que identifica ataques em uma sessão de nuvem, abrangendo produtos da Microsoft e aplicativos de terceiros
- A Proteção Avançada contra Ameaças do Azure, que usa análise comportamental para identificar ataques na rede local
- O Azure Active Directory Identity Protection, que detecta e impede proativamente os riscos de usuário e de entrada para identidades na nuvem

Comece a usar o painel do Cloud App Security para analisar detalhadamente os usuários arriscados, seja para iniciar a investigação sobre algo arriscado relacionado a um usuário que você detectou no painel do Cloud App Security ou para investigar um usuário que talvez tenha uma motivação que o sistema desconhece.  



Este tutorial fornece instruções sobre como usar o Cloud Discovery para investigar usuários arriscados.

> [!div class="checklist"]
> * Pré-requisitos
> * Identificar os principais usuários arriscados
> * investigar um usuário
> * Entender os usuários arriscados
> * Proteger a organização


## <a name="prerequisites"></a>Pré-requisitos

Para fazer uma investigação completa em um ambiente híbrido, é necessário:

- Uma licença válida do Microsoft Cloud App Security
- Uma licença válida do ATP do Azure vinculada à instância do Azure Active Directory
- Habilitar o Cloud App Security para [integrá-lo ao ambiente do ATP do Azure](aatp-integration.md) 

>[!NOTE]
>Mesmo que não tenha uma assinatura do ATP do Azure, você ainda poderá usar o portal do Cloud App Security para investigar usuários, mas não receberá informações do ambiente local. Você pode também exibir informações do ATP do Azure no portal do Cloud App Security, caso tenha uma licença do ATP do Azure, mas não do Microsoft Cloud App Security.


## <a name="identify-top-risky-users"></a>Identificar os principais usuários arriscados

Para identificar quem são os usuários mais arriscados no Cloud App Security:

1. Vá até o painel do Cloud App Security e procure as pessoas identificadas no bloco como **Principais usuários por prioridade de investigação**. Em seguida, acesse a página de usuário de cada uma delas para investigá-las. <br>O **número de prioridade de investigação**, exibido ao lado do nome de usuário, representa a soma de todas as atividades arriscadas do usuário ao longo da semana anterior. 

   ![Painel de principais usuários](./media/dashboard-top-users.png) 

2. Clique em um determinado usuário para acessar a página de **Usuário**. 
   ![Página de Usuário](./media/user-page.png) 

3. Clique na **Pontuação de prioridade de investigação** para exibir uma lista de todas as atividades arriscadas que ocorreram na semana anterior, a fim de combiná-las e atribuir uma determinada pontuação ao usuário. 
4. Revise as informações na página de **Usuário** para obter uma visão geral do usuário e ver se há pontos em que ele realizou atividades incomuns ou que foram realizadas em horários incomuns. A **Pontuação do usuário em comparação com a organização** representa o percentil em que ele está com base na classificação dele em sua organização. Ou seja, você deve investigar o nível em que ele está na lista de usuários, em relação a outros usuários da organização. O número será vermelho se o usuário estiver dentro ou acima do 90º percentil de usuários em risco na organização.<br>A página de **Usuário** permite responder às seguintes questões:
    1. Quem é o usuário?<br>Confira o painel esquerdo para obter informações sobre quem é o usuário e fatos relacionados a ele. Este painel fornece informações sobre a função do usuário na empresa e no respectivo departamento. O usuário é um engenheiro do DevOps que realiza frequentemente atividades incomuns como parte da função dele? O usuário é um funcionário insatisfeito que acaba de ser preterido para uma promoção?
    2. O usuário é arriscado?<br>Confira a parte superior do painel direito para ver se vale a pena investigar o usuário. Qual é a [pontuação de risco](#risk-score) do funcionário?
    3. Que risco o usuário representa para a organização?<br>Observe a lista no painel inferior, que fornece as atividades e os alertas relacionados ao usuário, para ajudá-lo a compreender que tipo de risco ele representa, de modo que você possa iniciar uma investigação mais detalhada.

  >[!NOTE]
  >É importante lembrar que, embora a página de **Usuário** forneça informações de todas as atividades sobre dispositivos, recursos e contas, a pontuação da prioridade de investigação é a soma de todos os alertas e atividades arriscadas dos últimos sete dias.
 
 
## <a name="investigate-a-user"></a>investigar um usuário
Quando algo parece fora do normal ou há um usuário que você deseja investigar, faça uma busca detalhada nos alertas desse usuário. Pode haver pequenas atividades isoladas que não parecem ser motivo de alarme, mas quando o Cloud App Security as agrega junto com outras atividades pouco preocupantes, fica mais fácil determinar a necessidade de uma investigação.
 
Quando investiga um usuário, você quer fazer as seguintes perguntas sobre as atividades e os alertas exibidos:
- As atividades estão relacionadas com a função dele?
- As atividades foram realizadas em momentos que fazem sentido de acordo com a linha do tempo?
- Faça uma busca detalhada em cada atividade para a qual você respondeu "não". Em seguida, no **log de atividades**, faça uma verificação cruzada desta atividade com outras atividades do mesmo usuário. Nesse local, você pode ver se havia outras atividades arriscadas de onde o usuário se conectou. Além disso, você pode facilmente dinamizar para outras quedas de análise, como atividades de nuvem não anômalas ou atividades locais, para continuar a investigação.


## Entender os usuários arriscados <a name ="risk-score"></a>
    
Para decidir quais usuários você investigará primeiro, use a **Pontuação de prioridade de investigação**. O Cloud App Security cria perfis de usuário para cada usuário com base em análises prolongadas, grupos de colegas e atividades relevantes esperadas do usuário. A atividade considerada anômala na linha de base do usuário é avaliada e pontuada. Após concluir a pontuação, o aprendizado de máquina e os cálculos de pares dinâmicos proprietários da Microsoft são executados em relação às atividades do usuário para calcular a prioridade de investigação de cada usuário. 

A **Pontuação de prioridade de investigação** fornece a capacidade de detectar invasores externos e internos mal-intencionados que se movem lateralmente na organização, sem depender de detecções determinísticas padrão.

Avaliando a urgência de investigação de cada usuário específico, a pontuação de prioridade de investigação se baseia em alertas de segurança, atividades anormais, negócios em potencial e impacto do ativo relacionados a cada usuário. 

Quando clica no valor da pontuação de um alerta ou de uma atividade, você exibe a evidência que explica como o Cloud App Security pontuou a atividade.

Todos os usuários do Microsoft Azure AD têm uma Pontuação de prioridade de investigação, que é constantemente atualizada com base em impacto e comportamento recentes, gerada sobre dados avaliados nos serviços ATP do Azure, Microsoft Cloud App Security e Azure AD Identity Protection. Agora, você pode compreender de imediato as ameaças reais dos principais usuários por **Pontuação de prioridade de investigação** e, em seguida, verificar o impacto sobre os negócios e investigar todas as atividades relacionadas, independentemente de estarem comprometidas, removendo dados ou atuando como ameaças internas.

O Cloud App Security usa os seguintes critérios para avaliar riscos: 

- **Pontuação de alerta**<br>A pontuação de alerta representa o impacto potencial de um alerta específico sobre cada usuário. A pontuação de alerta se baseia em severidade, impacto do usuário, popularidade do alerta entre os usuários e todas as entidades da organização.

- **Pontuação de atividade**<br> A pontuação de atividade determina a probabilidade de um usuário específico realizar uma determinada atividade, com base no aprendizado comportamental desse usuário e dos colegas dele. As atividades identificadas como mais anormais recebem as pontuações mais altas. 


## <a name="protect-your-organization"></a>Proteger a organização

Se você observar que um usuário está comprometido ou suspeitar que há um problema, é hora de tomar medidas.
- Diretamente do portal do Cloud App Security, é possível clicar no controle de **Ações do usuário** e definir o usuário como sendo de alto risco ou até mesmo suspendê-lo.
- Como alternativa, você pode redefinir a senha do usuário para bloquear o acesso dele.
- Se fizer uma busca detalhada em um alerta e determinar que a atividade não o acionou, na [Gaveta de atividades](activity-filters.md), clique no link **Enviar comentários** para que possamos refinar nosso sistema de alertas especialmente para sua organização.
- Depois de corrigir o problema, feche o alerta.


## <a name="see-also"></a>Consulte Também  
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  

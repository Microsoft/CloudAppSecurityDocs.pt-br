---
title: Investigar usuários arriscados | Microsoft Docs
description: Este tutorial descreve o processo para investigar usuários arriscados no Microsoft Cloud App Security em ambientes híbridos, integrando-o com o ATP do Azure.
keywords: ''
author: shsagir
ms.author: shsagir
ms.date: 07/02/2019
ms.topic: tutorial
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.reviewer: dannyk
ms.suite: ems
ms.openlocfilehash: d7373fb53984b84095fb08522f2f1922c9a0b947
ms.sourcegitcommit: c342abeec95359ddabdabcc3a081a0f91d52407c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72336136"
---
# <a name="tutorial-investigate-risky-users"></a>Tutorial: Investigar usuários arriscados

*Aplica-se a: Microsoft Cloud App Security*

As equipes de operações de segurança enfrentam o desafio de monitorar atividades de usuários, suspeitas ou não, em todas as dimensões da superfície de ataque de identidade, usando diversas soluções de segurança que geralmente não estão conectadas. Embora muitas empresas agora tenham equipes de caça para identificar proativamente as ameaças em seus ambientes, pode ser um desafio saber o que procurar na grande quantidade de dados. Agora, o Microsoft Cloud App Security simplifica isso ao eliminar a necessidade de criar regras de correlação complexas e permitir que você procure por ataques que se estendam por toda a nuvem e pela rede local.

Para ajudar você a se concentrar na identidade do usuário, o Microsoft Cloud App Security oferece a UEBA (análise comportamental da entidade do usuário) na nuvem. Isso pode ser estendido para seu ambiente local por meio da integração da ATP (Proteção Avançada contra Ameaças do Azure). Após integrar o ATP do Azure, você também obterá contexto em torno da identidade do usuário com base em sua integração nativa com o Active Directory.


Independentemente de o gatilho ser um alerta que você vê no painel do Cloud App Security ou de você ter informações de um serviço de segurança de terceiros, comece sua investigação no painel do Cloud App Security para se aprofundar nos usuários arriscados.  

Este tutorial fornece instruções sobre como usar o Cloud App Security para investigar usuários arriscados.

> [!div class="checklist"]
> * 1: [Conectar-se aos aplicativos que você deseja proteger](#connect-apps-protect)
> * 2: [Identificar os principais usuários arriscados](#identify)
> * 3: [Investigar mais os usuários](#investigate)
> * 4: [Proteger a organização](#protect)

## Entender a pontuação de prioridade de investigação<a name="risk-score"></a>

A pontuação de prioridade de investigação é uma pontuação que o Cloud App Security fornece a cada usuário para que você saiba o nível de risco de um usuário em relação aos outros usuários da sua organização.
    
Para decidir quais usuários você investigará primeiro, use a **Pontuação de prioridade de investigação**. O Cloud App Security cria perfis de usuário para cada usuário com base em análises prolongadas, grupos de colegas e atividades relevantes esperadas do usuário. A atividade considerada anômala na linha de base do usuário é avaliada e pontuada. Após concluir a pontuação, o aprendizado de máquina e os cálculos de pares dinâmicos proprietários da Microsoft são executados em relação às atividades do usuário para calcular a prioridade de investigação de cada usuário. 

A **Pontuação de prioridade de investigação** fornece a capacidade de detectar invasores externos e internos mal-intencionados que se movem lateralmente na organização, sem depender de detecções determinísticas padrão.

A pontuação de prioridade de investigação se baseia em alertas de segurança, atividades anormais, negócios em potencial e impacto do ativo relacionados a cada usuário para ajudar você a avaliar a urgência da investigação de cada usuário específico. 

Quando clica no valor da pontuação de um alerta ou de uma atividade, você exibe a evidência que explica como o Cloud App Security pontuou a atividade.

Todos os usuários do Microsoft Azure AD têm uma pontuação de prioridade de investigação, que é constantemente atualizada com base em impacto e comportamento recentes, gerada sobre dados avaliados nos serviços ATP do Azure, Microsoft Cloud App Security e Azure AD Identity Protection. Agora você pode compreender de imediato quem são os usuários de maior risco filtrando de acordo com a **Pontuação de prioridade de investigação**, verificar diretamente o impacto sobre os negócios e investigar todas as atividades relacionadas, independentemente de estarem comprometidas, apropriando dados ou atuando como ameaças internas.

O Cloud App Security usa os seguintes critérios para avaliar riscos: 

- **Pontuação de alerta**<br>A pontuação de alerta representa o impacto potencial de um alerta específico sobre cada usuário. A pontuação de alerta se baseia em severidade, impacto do usuário, popularidade do alerta entre os usuários e todas as entidades da organização.

- **Pontuação de atividade**<br> A pontuação de atividade determina a probabilidade de um usuário específico realizar uma determinada atividade, com base no aprendizado comportamental desse usuário e dos colegas dele. As atividades identificadas como mais anormais recebem as pontuações mais altas. 

## Fase 1: Conectar-se aos aplicativos que você deseja proteger<a name="connect-apps-protect"></a>

1. Conecte pelo menos um aplicativo ao Microsoft Cloud App Security usando os [conectores de API](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md). É recomendável que você comece conectando o [Office 365](connect-office-365-to-microsoft-cloud-app-security.md). 
1. Conecte outros aplicativos usando o [proxy para obter controle de aplicativos de acesso condicional](proxy-deployment-aad.md).
1. Para habilitar insights em seu ambiente local, configure o Cloud App Security para [integrar-se ao seu ambiente do ATP do Azure](aatp-integration.md).

## Fase 2: Identificar os principais usuários arriscados<a name="identify"></a>

Para identificar quem são os usuários mais arriscados no Cloud App Security:

1. Vá até o painel do Cloud App Security e procure as pessoas identificadas no bloco como **Principais usuários por prioridade de investigação**. Em seguida, acesse a página de usuário de cada uma delas para investigá-las. <br>O **número de prioridade de investigação**, exibido ao lado do nome de usuário, representa a soma de todas as atividades arriscadas do usuário ao longo da semana anterior. 

   ![Painel de principais usuários](./media/dashboard-top-users.png) 

2. Clique em um determinado usuário para acessar a página de **Usuário**. 
   ![Página de Usuário](./media/user-page.png) 

4. Examine as informações na página Usuário para obter uma visão geral do usuário e ver se há pontos em que ele realizou atividades incomuns ou que foram realizadas em horários incomuns. A **Pontuação do usuário em comparação com a organização** representa o percentil em que ele está com base na classificação dele em sua organização. Ou seja, você deve investigar o nível em que ele está na lista de usuários, em relação a outros usuários da organização. O número será vermelho se o usuário estiver dentro ou acima do 90º percentil de usuários em risco na organização.<br>A página Usuário permite responder às seguintes questões:
    - Quem é o usuário?<br>Confira o painel esquerdo para obter informações sobre quem é o usuário e fatos relacionados a ele. Este painel fornece informações sobre a função do usuário na empresa e no respectivo departamento. O usuário é um engenheiro do DevOps que realiza frequentemente atividades incomuns como parte da função dele? O usuário é um funcionário insatisfeito que acaba de ser preterido para uma promoção?
      
   - O usuário é arriscado?<br>Confira a parte superior do painel direito para ver se vale a pena investigar o usuário. Qual é a [pontuação de risco](#risk-score) do funcionário?
    
   - Que risco o usuário representa para a organização?<br>Observe a lista no painel inferior, que fornece as atividades e os alertas relacionados ao usuário para ajudá-lo a compreender que tipo de risco ele representa. Na linha do tempo, clique em cada linha para analisar detalhadamente a atividade ou o alerta em si. Você também pode clicar no número ao lado da atividade para entender as evidências que influenciaram a pontuação.

  >[!NOTE]
  >É importante lembrar que, embora a página Usuário forneça informações de todas as atividades sobre dispositivos, recursos e contas, a pontuação da prioridade de investigação é a soma de todos os alertas e as atividades arriscadas dos últimos sete dias.
 
 
## Fase 3: Investigar mais os usuários<a name="investigate"></a>

Ao investigar um usuário com base em um alerta ou se você notou um alerta em um sistema externo, pode haver atividades que, sozinhas, talvez não sejam motivo de alarme, mas quando o Cloud App Security as agrega junto a outras atividades, o alerta pode ser uma indicação de um evento suspeito.
 
Quando investiga um usuário, você quer fazer as seguintes perguntas sobre as atividades e os alertas exibidos:
- Há uma justificativa comercial para esse funcionário executar essas atividades? Por exemplo, se alguém da equipe de Marketing está acessando a base de código ou se alguém do desenvolvimento acessa o banco de dados de finanças, você deve se comunicar com o funcionário para certificar-se de que essa era uma atividade intencional e justificada.

- Acesse o **Log de atividades** para entender por que esta atividade recebeu uma classificação alta, enquanto outras não. Você pode definir a **Prioridade de investigação** para **Está definida** para entender quais atividades são suspeitas. Por exemplo, você pode filtrar com base na Prioridade de investigação por todas as atividades que ocorreram na Ucrânia. Então você pode ver se havia outras atividades arriscadas de onde o usuário se conectou. Além disso, você pode facilmente dinamizar para outras quedas de análise, como atividades de nuvem não anômalas ou atividades locais, para continuar a investigação.




## Fase 4: Proteger a organização<a name="protect"></a>

Se, por meio da sua investigação, você concluir que um usuário está comprometido, siga estas etapas para atenuar o risco.

- Contate o usuário – Usando as informações de contato do usuário integradas ao Cloud App Security do Active Directory, é possível fazer uma busca detalhada de cada alerta e atividade para resolver a identidade do usuário. Verifique se que o usuário está familiarizado com as atividades.

- Diretamente do portal do Cloud App Security, clique no controle de **Ações do usuário** e defina o usuário como sendo de alto risco ou suspenda-o.
- No caso de uma identidade comprometida, é possível pedir ao usuário para redefinir a senha, verificando se ela atende às diretrizes de melhor prática quanto ao tamanho e à complexidade.
- Se fizer uma busca detalhada em um alerta e determinar que a atividade não o acionou, na [Gaveta de atividades](activity-filters.md), clique no link **Enviar comentários** para que possamos refinar nosso sistema de alertas especialmente para sua organização.
- Depois de corrigir o problema, feche o alerta.


## <a name="see-also"></a>Consulte Também  
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  

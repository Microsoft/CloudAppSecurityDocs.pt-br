---
title: Criar políticas de detecção de anomalias no Cloud App Security | Microsoft Docs
description: Este tópico fornece uma descrição das Políticas de detecção de anomalias, bem como informações de referência sobre os blocos de construção de uma política de detecção de anomalias.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 6/18/2018
ms.topic: article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: ab9bc377-d2f5-4f4c-a419-f1728a15d1c7
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: c182ea9cfebd7161e637cbd1460ac6b56b17362d
ms.sourcegitcommit: 49a06f2169af74304eef0288e31783c06ccd3b74
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/24/2018
ms.locfileid: "36746993"
---
*Aplica-se ao: Microsoft Cloud App Security*

 
# <a name="get-instantaneous-behavioral-analytics-and-anomaly-detection"></a>Obter análise comportamental e detecção de anomalias instantaneamente

As políticas de detecção de anomalias do Microsoft Cloud App Security fornecem análises comportamentais de entidades e de usuários (UEBA) e aprendizado de máquina (ML) inovadores para que você execute imediatamente uma detecção avançada a ameaças em seu ambiente de nuvem. Por serem habilitadas automaticamente, as novas políticas de detecção de anomalias geram resultados imediatos ao fornecer detecções imediatas, visando inúmeras anomalias comportamentais nos usuários, máquinas e dispositivos conectados à sua rede.  Além disso, as novas políticas expõem mais dados do mecanismo de detecção do Cloud App Security para ajudar a acelerar o processo de investigação e conter as ameaças em andamento. 

As políticas de detecção de anomalias são habilitadas automaticamente, mas o Cloud App Security tem um período inicial de aprendizagem de sete dias, durante os quais nem todos os alertas de detecção de anomalias são disparados. Depois disso, cada sessão é comparada à atividade, quando os usuários estavam ativos, endereços IP, dispositivos, etc. detectados ao longo do mês anterior e à pontuação de risco dessas atividades.  Essas detecções fazem parte do mecanismo heurístico de detecção de anomalias que analisa seu ambiente e dispara alertas em relação a uma linha de base obtida quanto à atividade de sua organização. As detecções também impulsionam os algoritmos de aprendizado de máquina , desenvolvidos para analisar os usuários e o padrão de login para reduzir o número de falsos positivos.

As anomalias são detectadas pela verificação da atividade do usuário. O risco é avaliado observando-se mais de 30 indicadores de risco diferentes, agrupados em múltiplos fatores de risco, como: 
          
 -   Endereço IP arriscado
 -   Falhas de logon
 -   Atividade do administrador
 -   Contas inativas
 -   Local  
 -   Viagem impossível
 -   Agente de dispositivo e usuário
 -   Taxa de atividade

Com base nos resultados da política, os alertas de segurança são disparados. O Cloud App Security examina cada sessão do usuário na nuvem e alerta você quando acontece algo diferente da linha de base da sua organização ou da atividade regular do usuário. 


Você pode ver as políticas de detecção de anomalias no portal clicando em **Controle** e em **Políticas**.

 ![novas políticas de detecção de anomalias](./media/new-anomaly-detection-policies.png)

As seguintes políticas de detecção de anomalias estão disponíveis:

**Viagem impossível**
-  Essa detecção identifica duas atividades do usuário (em uma ou em várias sessões) provenientes de locais geograficamente distantes em um período menor que o tempo necessário para o usuário se deslocar do primeiro local para o segundo, indicando que outro usuário está usando as mesmas credenciais. Essa detecção usa um algoritmo de aprendizado de máquina que ignora "falsos positivos" óbvios que contribuem para a condição de viagem impossível, como VPNs e locais usados regularmente por outros usuários da organização. A detecção tem um período inicial de aprendizado de sete dias, durante o qual aprende o padrão de atividade do novo usuário.


**Atividade de país não frequente**
- Essa detecção considera locais de atividades anteriores para determinar locais novos e pouco frequentes. O mecanismo de detecção de anomalias armazena informações sobre locais anteriores usados por usuários da organização. Um alerta é acionado quando uma atividade ocorre em um local que o usuário ou alguém da organização nunca visitou ou que não visitou recentemente. 

**Detecção de malware**
- Essa detecção identifica arquivos mal-intencionados no armazenamento em nuvem, sejam de aplicativos da Microsoft ou de aplicativos de terceiros. O Microsoft Cloud App Security usa a Inteligência Contra Ameaças da Microsoft para reconhecer se determinados arquivos estão associados a ataques de malware conhecidos e são possivelmente mal-intencionados. Essa política interna é desabilitada por padrão. Nem todo arquivo é examinado, mas é usada heurística para procurar arquivos que possam estar em risco. Depois que os arquivos são detectados, é exibida uma lista de **Arquivos infectados**. Clique no nome do arquivo de malware na gaveta de arquivo para abrir um relatório de malware que oferece informações sobre o tipo de malware que infectou o arquivo.
    
**Atividade de endereços IP anônimos**
- Essa detecção identifica que os usuários estavam ativos com base em um endereço IP que foi identificado como um endereço IP de proxy anônimo. Esses proxies são usados por pessoas que desejam ocultar o endereço IP de seu dispositivo e podem ser usados de forma mal-intencionada. Essa detecção usa um algoritmo de aprendizado de máquina que reduz "falsos positivos", como endereços IP marcados incorretamente que são usados amplamente por usuários da organização.

**Atividade de ransomware**
-  O Cloud App Security estendeu seus recursos de detecção de ransomware com a detecção de anomalias para garantir uma cobertura mais ampla contra ataques de Ransomware sofisticados. Usando nossa experiência com pesquisa de segurança para identificar padrões de comportamentos que refletem a atividade de ransomware, o Cloud App Security garante a proteção holística e robusta. Por exemplo, se o Cloud App Security identificar uma taxa alta de uploads de arquivos ou atividades de exclusão de arquivo, isso poderá representar um processo de criptografia adverso. Esses dados são coletados nos logs recebidos de APIs conectadas e são combinados com padrões comportamentais aprendidos e inteligência contra ameaças, por exemplo, extensões de ransomware conhecidas. Para obter mais informações sobre como o Cloud App Security detecta ransomware, confira [Proteger sua organização contra ransomware](use-case-ransomware.md).

**Atividade de usuário encerrada**

- Essa detecção habilita você a identificar quando um funcionário demitido continua a executar ações em seus aplicativos SaaS. Como os dados mostram que o maior risco de ameaça interna vem de funcionários que deixaram a empresa descontentes, é importante ficar atento à atividade em contas de funcionários demitidos. Às vezes, quando funcionários deixam a empresa, suas contas são desprovisionadas de aplicativos corporativos, mas, em muitos casos, eles ainda mantêm o acesso a determinados recursos corporativos. Isso é ainda mais importante ao considerar as contas privilegiadas, pois os danos potenciais que um administrador anterior pode causar são inerentemente maiores.
Essa detecção se beneficia da capacidade do Cloud App Security de monitorar o comportamento do usuário entre aplicativos, permitindo a identificação da atividade regular do usuário, o fato de que a conta foi encerrada e atividade real em outros aplicativos. Por exemplo, um funcionário cuja conta do Azure AD foi encerrada, mas que ainda tem acesso à infraestrutura corporativa do AWS, tem o potencial de causar danos em grande escala.  

**Atividade de endereços IP suspeitos**
- A detecção identifica que os usuários estavam ativos com base em um endereço IP que foi identificado como arriscado pela Microsoft Threat Intelligence. Esses endereços IP estão envolvidos em atividades mal-intencionadas, como Botnet C&C, e podem indicar uma conta comprometida. Essa detecção usa um algoritmo de aprendizado de máquina que reduz "falsos positivos", como endereços IP marcados incorretamente que são usados amplamente por usuários da organização.


**Atividades incomuns (por usuário)**

Essas detecções identificam os usuários que executam:

 - Atividades incomuns de vários downloads de arquivos
 - Atividades incomuns de compartilhamento de arquivos
 - Atividades incomuns de exclusão de arquivos
 - Atividades representadas incomuns
 - Atividades administrativas incomuns
 
Essas políticas buscam atividades em uma única sessão em relação à linha de base aprendida, que pode indicar uma tentativa de violação. As detecções se beneficiam de um algoritmo de aprendizado de máquina que analisa o padrão de logon dos usuários e reduz falsos positivos. Essas detecções fazem parte do mecanismo heurístico de detecção de anomalias que analisa seu ambiente e dispara alertas em relação a uma linha de base obtida quanto à atividade de sua organização.

**Várias tentativas de logon com falha**
- A detecção identifica usuários que realizaram várias tentativas de logon com falha em uma única sessão em relação à linha de base aprendida, o que poderia indicar uma tentativa de violação. 

## Habilitar governança automatizada<a name="adp-automated-gov"></a>

É possível habilitar ações de correção automatizadas em alertas gerados por políticas de detecção de anomalias. 

1. Clique no nome da política de detecção na página **Política**.
2. Na janela **Editar política de detecção de anomalias** que é aberta, em **Governança** defina as ações de correção que deseja para cada aplicativo conectado ou para todos os aplicativos. 
3. Clique em **Atualizar**.

 
## <a name="scope-anomaly-detection-policies"></a>Definir políticas de detecção de anomalias

Cada política de detecção de anomalias pode ter um escopo independente, de modo que se aplique apenas aos usuários e grupos que você deseja incluir e excluir na política.
Por exemplo, você pode definir a Atividade de detecção de regiões pouco frequentes para ignorar um usuário específico que viaja com frequência. 

Para definir uma política de detecção de anomalias:
1. Clique em **Políticas de**  > **Controle** e configure o filtro **Tipo** como **Política de detecção de anomalias**.
2. Clique na política que você deseja definir.
3. Em **Escopo**, altere o menu suspenso da configuração padrão de **Todos os usuários e grupos** para **Usuários e grupos específicos**.
4. Selecione **Incluir** para especificar os usuários e grupos para os quais essa política será aplicada. Qualquer usuário ou grupo não selecionado aqui não será considerado uma ameaça e não gerará um alerta.
5. Selecione **Excluir** para especificar usuários para os quais essa política não será aplicada. Qualquer usuário selecionado aqui não será considerado uma ameaça e não gerará um alerta, mesmo se eles forem membros de grupos selecionados em **Incluir**.

 ![escopo de detecção de anomalias](./media/anomaly-detection-scoping.png)
## <a name="triage-anomaly-detection-alerts"></a>Triagem de alertas de detecção de anomalias

Você pode triar rapidamente os vários alertas disparados pelas novas políticas de detecção de anomalias e decidir quais precisam ser tratados primeiro. Para isso, é necessário o contexto do alerta para ver o panorama geral e entender se algo mal-intencionado realmente está acontecendo.  

1. No **Log de atividades**, você pode abrir uma atividade para exibir a gaveta Atividades. Clique em **Usuário** para exibir a guia de informações do usuário. Isso inclui informações como o número de alertas, as atividades e de onde o usuário se conectou, que são importantes em uma investigação. 

   ![alerta1 de detecção de anomalias](./media/anomaly-alert-user1.png)
   ![alerta1 de detecção de anomalias](./media/anomaly-alert-user2.png)
 
2. Isso permite que você entenda quais são as atividades suspeitas que o usuário executou e ter maior confiança sobre o comprometimento da conta. Por exemplo, um alerta de vários logons com falha pode realmente ser suspeito e indicar um ataque de força bruta em potencial, mas também pode ser um erro de configuração do aplicativo, fazendo com que o alerta seja um verdadeiro positivo benigno. No entanto, se você vir um alerta de vários logons com falha com atividades suspeitas adicionais, então há uma grande probabilidade de que a conta foi comprometida. No exemplo a seguir, você pode ver que o alerta **Várias tentativas de logon com falha** foi seguido de uma **Atividade de um endereço IP TOR** e de uma **Atividade de viagem impossível**, ambas fortes indicadores de comprometimento (IOCs) por si próprias. Como se isso já não fosse suspeito, é possível ver que o mesmo usuário realizou uma **Atividade de download em massa**, que em geral indica que o invasor está executando uma extração de dados. 

   ![alerta1 de detecção de anomalias](./media/anomaly-alert-user3.png)
   ![alerta1 de detecção de anomalias](./media/anomaly-alert-user4.png)

3.  Para arquivos infectados por malware, depois que os arquivos forem detectados, será exibida uma lista de **Arquivos infectados**. Clique no nome do arquivo de malware na gaveta de arquivo para abrir um relatório de malware que oferece informações sobre o tipo de malware que infectou o arquivo. 


  

  
## <a name="see-also"></a>Consulte Também  
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  

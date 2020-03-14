---
title: Criar políticas de detecção de anomalias no Cloud App Security
description: Este artigo fornece uma descrição das políticas de detecção de anomalias e fornece informações de referência sobre os blocos de construção de uma política de detecção de anomalias.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 02/04/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: d2dce554b959c14ba32c92f27579d5525069b1f3
ms.sourcegitcommit: 4f3883a9e85d0aaf2802b10433b221c3f1838d88
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79285310"
---
# <a name="get-instantaneous-behavioral-analytics-and-anomaly-detection"></a>Obtenha análise comportamental e detecção de anomalias instantâneas

*Aplica-se a: Microsoft Cloud App Security*

As políticas de detecção de anomalias do Microsoft Cloud App Security fornecem UEBA (análise comportamental do usuário e entidade) e o ML (aprendizado de máquina) prontos para que você possa executar imediatamente a detecção avançada de ameaças em seu ambiente de nuvem. Como elas são habilitadas automaticamente, as novas políticas de detecção de anomalias fornecem resultados imediatos, fornecendo detecções imediatas, direcionando a várias anomalias comportamentais entre seus usuários e os computadores e dispositivos conectados à sua rede.  Além disso, as novas políticas expõem mais dados do mecanismo de detecção do Cloud App Security para ajudar a agilizar o processo de investigação e conter as ameaças em andamento.

As políticas de detecção de anomalias são habilitadas automaticamente, mas Cloud App Security tem um período de aprendizado inicial de sete dias durante o qual nem todos os alertas de detecção de anomalias são gerados. Depois disso, cada sessão é comparada à atividade, quando os usuários estavam ativos, os endereços IP, os dispositivos, entre outros itens detectados ao longo do mês anterior e a pontuação de risco dessas atividades.  Essas detecções fazem parte do mecanismo de detecção de anomalias heurística que cria o perfil de seu ambiente e dispara alertas em relação a uma linha de base que foi aprendida na atividade da sua organização. Essas detecções também usam algoritmos de aprendizado de máquina criados para criar o perfil dos usuários e o padrão de entrada para reduzir os falsos positivos.

As anomalias são detectadas por meio da verificação da atividade do usuário. O risco é avaliado examinando mais de 30 indicadores de risco diferentes, agrupados em fatores de risco, da seguinte maneira:

* Endereço IP arriscado
* Falhas de logon
* Atividade de administrador
* Contas inativas
* Local
* Viagem impossível
* Agente do usuário e do dispositivo
* Taxa de atividade

Com base nos resultados da política, os alertas de segurança são disparados. Cloud App Security examina cada sessão de usuário em sua nuvem e alerta quando algo acontece diferente da linha de base da sua organização ou da atividade regular do usuário.

Além dos alertas de Cloud App Security nativos, você também obterá os seguintes alertas de detecção com base nas informações recebidas da proteção de identidade do Azure Active Directory (AD):

* Credenciais vazadas: disparadas quando as credenciais válidas de um usuário tiverem sido vazadas. Para obter mais informações, consulte [detecção de credenciais vazadas do Azure ad](/azure/active-directory/identity-protection/concept-identity-protection-risks#user-risk).
* Entrada arriscada: combina várias detecções de entrada Azure AD Identity Protection em uma única detecção (desabilitada por padrão). Para obter mais informações, consulte [detecções de risco de entrada do Azure ad](/azure/active-directory/identity-protection/concept-identity-protection-risks#sign-in-risk).

Essas políticas serão exibidas na página políticas de Cloud App Security e poderão ser habilitadas ou desabilitadas, mas não editadas.

## <a name="anomaly-detection-policies"></a>Políticas de detecção de anomalias

Você pode ver as políticas de detecção de anomalias no portal clicando em **controle** e em **políticas**. Selecione **política de detecção de anomalias** para o tipo de política.

 ![novas políticas de detecção de anomalias](media/new-anomaly-detection-policies.png)

As seguintes políticas de detecção de anomalias estão disponíveis:

### <a name="impossible-travel"></a>Viagem impossível

* Essa detecção identifica duas atividades do usuário (é uma única ou várias sessões) provenientes de locais geograficamente distantes em um período de tempo menor que o tempo que teria levado para o usuário viajar do primeiro local para o segundo, indicando que um usuário diferente está usando as mesmas credenciais. Essa detecção usa um algoritmo de aprendizado de máquina que ignora "falsos positivos" claros que contribuem para a condição de viagem impossível, como VPNs e locais usados regularmente por outros usuários na organização. A detecção tem um período inicial de aprendizado de sete dias, durante o qual aprende o padrão de atividade de um novo usuário. A detecção de viagem impossível identifica atividades de usuário incomuns e impossíveis entre dois locais. A atividade deve ser incomum o suficiente para ser considerada um indicador de comprometimento e digno de um alerta. Para fazer isso funcionar, a lógica de detecção inclui diferentes níveis de supressão para tratar de cenários que podem disparar falsos positivos, como atividades de VPN. O controle deslizante sensibilidade permite que você afete o algoritmo e defina o quão estrito é a lógica de detecção. Quanto maior o nível de sensibilidade, menor será a supressão aplicada como parte da lógica de detecção. Dessa forma, você pode adaptar a detecção de acordo com suas necessidades de cobertura e seus destinos de SNR.

    > [!NOTE]
    > Quando os endereços IP em ambos os lados da viagem são [marcados como corporativos](ip-tags.md), a viagem é considerada confiável e excluída do disparo da detecção de viagem impossível. No entanto, se o endereço IP de apenas um dos lados da viagem for marcado como corporativo, a detecção será disparada como normal.

### <a name="activity-from-infrequent-country"></a>Atividade de um país infrequente

* Essa detecção considera os locais de atividades anteriores para determinar os locais novos e pouco frequentes. O mecanismo de detecção de anomalias armazena informações sobre locais anteriores usados por usuários na organização. Um alerta é disparado quando ocorre uma atividade de um local que não foi recentemente ou nunca foi visitado por nenhum usuário na organização.

### <a name="malware-detection"></a>Detecção de malware

* Essa detecção identifica arquivos mal-intencionados em seu armazenamento em nuvem, seja de seus aplicativos da Microsoft ou de aplicativos de terceiros. Microsoft Cloud App Security usa a inteligência contra ameaças da Microsoft para reconhecer se determinados arquivos estão associados a ataques de malware conhecidos e são potencialmente mal-intencionados. Essa política interna é desabilitada por padrão. Nem todo arquivo é verificado, mas a heurística é usada para procurar por arquivos potencialmente arriscados. Depois que os arquivos forem detectados, você poderá ver uma lista de **arquivos infectados**. Clique no nome do arquivo de malware na gaveta do arquivo para abrir um relatório de malware que fornece informações sobre esse tipo de malware com o qual o arquivo está infectado.

    > [!NOTE]
    > * Para detecção de malware do Office 365, você precisa de uma licença válida para a proteção de ameaças avançadas do Office 365 P1.
    > * O Cloud App Security dá suporte à detecção de malware dos seguintes aplicativos:
    >   * Caixa
    >   * Dropbox
    >   * G Suite
    >   * Office 365

### <a name="activity-from-anonymous-ip-addresses"></a>Atividade de endereços IP anônimos

* Essa detecção identifica que os usuários estavam ativos com base em um endereço IP que foi identificado como um endereço IP de proxy anônimo. Esses proxies geralmente são usados por usuários que desejam ocultar o endereço IP de seu dispositivo e podem ser usados com objetivos mal-intencionados. Essa detecção usa um algoritmo de aprendizado de máquina que reduz "falsos positivos", como endereços IP com marcas de tipo de mis que são amplamente usadas por usuários na organização.

### <a name="ransomware-activity"></a>Atividade de ransomware

* O Cloud App Security ampliou seus recursos de detecção de ransomware com a detecção de anomalias para garantir uma cobertura mais abrangente contra ataques sofisticados de ransomware. Usando nossa experiência de pesquisa de segurança para identificar os padrões comportamentais que refletem a atividade de ransomware, o Cloud App Security garante uma proteção holística e robusta. Se Cloud App Security identificar, por exemplo, uma alta taxa de carregamentos de arquivos ou atividades de exclusão de arquivos, ele poderá representar um processo de criptografia adverso. Esses dados são coletados nos logs recebidos de APIs conectadas e, em seguida, combinados com padrões de comportamento conhecidos e inteligência contra ameaças, por exemplo, extensões de ransomware conhecidas. Para obter mais informações sobre como Cloud App Security detecta ransomware, consulte [protegendo sua organização contra ransomware](use-case-ransomware.md).

### <a name="activity-performed-by-terminated-user"></a>Atividade executada por usuário encerrado

* Essa detecção permite que você identifique quando um funcionário encerrado continua executando ações em seus aplicativos SaaS. Como os dados mostram que o maior risco de ameaça interna provém de funcionários que deixaram de termos ruins, é importante ficar atento à atividade em contas de funcionários demitidos. Às vezes, quando os funcionários deixam uma empresa, suas contas são desprovisionadas dos aplicativos corporativos, mas em muitos casos eles ainda retêm o acesso a determinados recursos corporativos. Isso é ainda mais importante ao considerar contas privilegiadas, pois o dano potencial que um administrador anterior pode fazer é inerentemente maior.
Essa detecção aproveita a capacidade do Cloud App Security de monitorar o comportamento do usuário entre aplicativos, permitindo a identificação da atividade regular do usuário, o fato de que a conta foi encerrada e a atividade real em outros aplicativos. Por exemplo, um funcionário que é a conta do Azure AD foi encerrado, mas ainda tem acesso à infraestrutura AWS corporativa, tem o potencial de causar danos em larga escala.

A detecção procura por usuários cuja conta foi encerrada no Azure AD, mas ainda realiza atividades em outras plataformas, como AWS ou Salesforce. Isso é especialmente relevante para usuários que usam outra conta (não sua conta de logon único principal) para gerenciar recursos, já que essas contas geralmente não são encerradas quando um usuário sai da empresa.

### <a name="activity-from-suspicious-ip-addresses"></a>Atividade de endereços IP suspeitos

* Essa detecção identifica que os usuários estavam ativos de um endereço IP identificado como arriscado pela inteligência contra ameaças da Microsoft. Esses endereços IP estão envolvidos em atividades mal-intencionadas, como a botnet C & C, e podem indicar uma conta comprometida. Essa detecção usa um algoritmo de aprendizado de máquina que reduz "falsos positivos", como endereços IP com marcas de tipo de mis que são amplamente usadas por usuários na organização.

### <a name="suspicious-inbox-forwarding"></a>Encaminhamento de caixa de entrada suspeito

* Essa detecção procura regras de encaminhamento de email suspeitas, por exemplo, se um usuário criou uma regra de caixa de entrada que encaminha uma cópia de todos os emails para um endereço externo.

> [!NOTE]
> Cloud App Security apenas alerta você para cada regra de encaminhamento identificada como suspeita, com base no comportamento típico do usuário.

### <a name="suspicious-inbox-manipulation-rules"></a>Regras de manipulação de caixa de entrada suspeitas

* Essa detecção faz o perfil do seu ambiente e dispara alertas quando regras suspeitas que excluem ou movem mensagens ou pastas são definidas na caixa de entrada de um usuário. Pode indicar que a conta de usuário está comprometida, que as mensagens foram ocultadas de forma intencional e que a caixa de correio está sendo usada para enviar spam e malware em sua organização.

### <a name="suspicious-email-deletion-activity-preview"></a>Atividade de exclusão de email suspeito (versão prévia)

* Essa política faz o perfil do seu ambiente e dispara alertas quando um usuário executa atividades suspeitas de exclusão de email em uma única sessão. Essa política pode indicar que as caixas de correio de um usuário podem ser comprometidas por possíveis vetores de ataque, como a comunicação de comando e controle (C & C/C2) por email.

### <a name="unusual-activities-by-user"></a>Atividades incomuns (por usuário)

Essas detecções identificam os usuários que executam:

* Atividades de download de vários arquivos incomuns
* Atividades de compartilhamento de arquivos incomum
* Atividades de exclusão de arquivo incomum
* Atividades representadas incomuns
* Atividades administrativas incomuns
* Atividades de compartilhamento de relatório Power BI incomum (versão prévia)
* Várias atividades de criação de VM incomuns (versão prévia)
* Várias atividades de exclusão de armazenamento incomum (visualização)

Essas políticas procuram atividades em uma única sessão em relação à linha de base aprendida, o que pode indicar uma tentativa de violação. Essas detecções aproveitam um algoritmo de aprendizado de máquina que faz o perfil do padrão de logon dos usuários e reduz os falsos positivos. Essas detecções fazem parte do mecanismo de detecção de anomalias heurística que cria o perfil de seu ambiente e dispara alertas em relação a uma linha de base que foi aprendida na atividade da sua organização.

### <a name="multiple-failed-login-attempts"></a>Várias tentativas de logon com falha

* Essa detecção identifica os usuários que falharam várias tentativas de logon em uma única sessão em relação à linha de base aprendida, o que pode indicar uma tentativa de violação.

### <a name="data-exfiltration-to-unsanctioned-apps"></a>Vazamento de dados para aplicativos não aprovados

* Essa política é habilitada automaticamente para alertá-lo quando um usuário ou endereço IP usa um aplicativo que não é aprovado para executar uma atividade que se assemelha a uma tentativa de exfiltrar informações de sua organização.

### <a name="multiple-delete-vm-activities"></a>Várias atividades de exclusão de VM

* Essa política faz o perfil do seu ambiente e dispara alertas quando os usuários excluem várias VMs em uma única sessão, em relação à linha de base em sua organização. Isso pode indicar uma tentativa de violação.

## Habilitar governança automatizada<a name="adp-automated-gov"></a>

Você pode habilitar ações de correção automatizadas em alertas gerados por políticas de detecção de anomalias.

1. Clique no nome da política de detecção na página de **política** .
1. Na janela **Editar política de detecção de anomalias** que é aberta, em **governança** , defina as ações de correção desejadas para cada aplicativo conectado ou para todos os aplicativos.
1. Clique em **Atualizar**.

## <a name="tune-anomaly-detection-policies"></a>Ajustar políticas de detecção de anomalias

Para afetar o mecanismo de detecção de anomalias para suprimir ou Surface os alertas de acordo com suas preferências:

* Na política Viagem Impossível, você pode definir o controle deslizante de sensibilidade para determinar o nível de comportamento anormal necessário antes que um alerta seja disparado. Por exemplo, se você defini-lo como baixo, ele suprimirá os alertas de viagem impossíveis dos locais comuns de um usuário e, se você defini-lo como alto, ele causará a superfície desses alertas. Você pode escolher entre os seguintes níveis de sensibilidade:

  * **Baixo**: supressões de sistema, locatário e usuário
  * **Médio**: supressões do sistema e do usuário
  * **Alta**: somente supressões do sistema

    Sendo que:

    | Tipo de supressão | Descrição |
    | --- | --- |
    | **Sistema** | Detecções internas que são sempre suprimidas. |
    | **Locatário** | Atividades comuns com base na atividade anterior no locatário. Por exemplo, suprimir atividades de um ISP anteriormente alertado em sua organização. |
    | **Usuário** | Atividades comuns com base na atividade anterior do usuário específico. Por exemplo, suprimir atividades de um local que é comumente usado pelo usuário. |

* Você também pode configurar se os alertas de atividade de um país infrequente, endereços IP anônimos, endereços IP suspeitos e viagens impossíveis devem analisar logons com falha e com êxito ou apenas logons bem-sucedidos.

> [!NOTE]
> Por padrão, protocolos de entrada herdados, como aqueles que não usam a autenticação multifator (por exemplo, WS-Trust), não são monitorados pela política de viagem impossível. Se sua organização usa protocolos herdados, para evitar atividades relevantes ausentes, edite a política e, em **Configuração avançada**, defina **analisar as atividades de entrada** para **todas as**entradas.

## <a name="scope-anomaly-detection-policies"></a>Políticas de detecção de anomalias de escopo

Cada política de detecção de anomalias pode ter escopo independente para que se aplique somente aos usuários e grupos que você deseja incluir e excluir na política.
Por exemplo, você pode definir a detecção de Atividade de região pouco frequente para ignorar um usuário específico que viaja com frequência.

Para fazer o escopo de uma política de detecção de anomalias:

1. Clique em **controlar** > **políticas**e defina o filtro de **tipo** como política de **detecção de anomalias**.
1. Clique na política que você deseja escopo.
1. Em **escopo**, altere a lista suspensa da configuração padrão de todos os **usuários e grupos**para **usuários e grupos específicos**.
1. Selecione **incluir** para especificar os usuários e grupos aos quais essa política será aplicada. Qualquer usuário ou grupo não selecionado aqui não será considerado uma ameaça e não gerará um alerta.
1. Selecione **excluir** para especificar os usuários para os quais essa política não será aplicada. Qualquer usuário selecionado aqui não será considerado uma ameaça e não gerará um alerta, mesmo se eles forem membros de grupos selecionados em **incluir**.

    ![escopo de detecção de anomalias](media/anomaly-detection-scoping.png)

## <a name="triage-anomaly-detection-alerts"></a>Filtrar alertas de detecção de anomalias

Você pode fazer uma triagem dos vários alertas disparados pelas novas políticas de detecção de anomalias rapidamente e decidir quais delas precisam ser levadas em primeiro lugar. Para fazer isso, você precisa do contexto para o alerta, então você pode ver a imagem maior e entender se algo mal-intencionado está realmente acontecendo.

1. No **log de atividades**, você pode abrir uma atividade para exibir a gaveta de atividade. Clique em **usuário** para exibir a guia insights do usuário. Essa guia inclui informações como o número de alertas, atividades e o local em que eles se conectaram, o que é importante em uma investigação.

    ![detecção de anomalias alert1](media/anomaly-alert-user1.png) ![detecção de anomalias alert1](media/anomaly-alert-user2.png)

1. Isso permite que você entenda quais são as atividades suspeitas que o usuário realizou e se tem uma confiança mais profunda sobre se a conta foi comprometida. Por exemplo, um alerta em vários logons com falha pode realmente ser suspeito e pode indicar um ataque de força bruta potencial, mas também pode ser uma configuração incorreta do aplicativo, fazendo com que o alerta seja um verdadeiro positivo benigno. No entanto, se você vir um alerta de vários logons com falha com atividades suspeitas adicionais, haverá uma maior probabilidade de que a conta seja comprometida. No exemplo a seguir, você pode ver que o alerta **várias tentativas de logon com falha** foi seguido por **atividade de um endereço IP Tor** e **atividade de viagem impossível**, tantos indicadores fortes de comprometimento (IOCs) por si mesmos. Se isso não era suspeito, você pode ver que o mesmo usuário realizou uma **atividade de download em massa**, que é geralmente um indicador do invasor que executa vazamento de dados.

    ![alert1 de detecção de anomalias](media/anomaly-alert-user3.png)

1. Para arquivos infectados por malware, depois que os arquivos forem detectados, você poderá ver uma lista de **arquivos infectados**. Clique no nome do arquivo de malware na gaveta do arquivo para abrir um relatório de malware que fornece informações sobre esse tipo de malware com o qual o arquivo está infectado.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]

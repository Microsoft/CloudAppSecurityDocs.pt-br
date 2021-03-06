---
title: Criar políticas de detecção de anomalias no Cloud App Security
description: Este artigo fornece uma descrição das Políticas de detecção de anomalias, bem como informações de referência sobre os blocos de construção de uma política de detecção de anomalias.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 01/05/2021
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 0fce6bbf6e13b34c904d88a34fe858f1586d9d90
ms.sourcegitcommit: 7fc4d916a43d188b1aa4e3cee2e8bd1de230d135
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98206467"
---
# <a name="get-behavioral-analytics-and-anomaly-detection"></a>Obter análise comportamental e detecção de anomalias

[!INCLUDE [Banner for top of topics](includes/banner.md)]

As políticas de detecção de anomalias do Microsoft Cloud App Security fornecem UEBA (análise comportamental do usuário e entidade) e o ML (aprendizado de máquina) prontos para uso para que você esteja pronto desde o início para executar a detecção avançada de ameaças em seu ambiente de nuvem. Como elas são habilitadas automaticamente, as novas políticas de detecção de anomalias iniciam imediatamente o processo de detecção e agrupamento de resultados, direcionando várias anomalias comportamentais entre os usuários e os computadores e dispositivos conectados à sua rede. Além disso, as políticas expõem mais dados do mecanismo de detecção de Cloud App Security, para ajudá-lo a acelerar o processo de investigação e conter ameaças contínuas.

As políticas de detecção de anomalias são habilitadas automaticamente, mas o Cloud App Security tem um período inicial de aprendizagem de sete dias, durante os quais nem todos os alertas de detecção de anomalias são disparados. Depois disso, à medida que os dados são coletados de seus conectores de API configurados, cada sessão é comparada com a atividade, quando os usuários estavam ativos, endereços IP, dispositivos, etc. detectados no último mês e na pontuação de risco dessas atividades. Lembre-se de que pode levar várias horas para que os dados estejam disponíveis nos conectores de API. Essas detecções fazem parte do mecanismo de detecção de anomalias heurística que cria o perfil de seu ambiente e dispara alertas em relação a uma linha de base que foi aprendida na atividade da sua organização. As detecções também usam os algoritmos de aprendizado de máquina, desenvolvidos para analisar os usuários e o padrão de entrada para reduzir o número de falsos positivos.

As anomalias são detectadas pela verificação da atividade do usuário. O risco é avaliado observando-se mais de 30 indicadores de risco diferentes, agrupados em fatores de risco, como:

* Endereço IP arriscado
* Falhas de logon
* Atividade do administrador
* Contas inativas
* Location
* Viagem impossível
* Agente de dispositivo e usuário
* Taxa de atividade

Com base nos resultados da política, os alertas de segurança são disparados. O Cloud App Security examina cada sessão do usuário na nuvem e alerta você quando acontece algo diferente da linha de base da sua organização ou da atividade regular do usuário.

Além dos alertas de Cloud App Security nativos, você também obterá os seguintes alertas de detecção com base nas informações recebidas da proteção de identidade do Azure Active Directory (AD):

* Credenciais vazadas: disparadas quando as credenciais válidas de um usuário tiverem sido vazadas. Para obter mais informações, consulte [detecção de credenciais vazadas do Azure ad](/azure/active-directory/identity-protection/concept-identity-protection-risks#user-risk).
* Entrada arriscada: combina várias detecções de entrada Azure AD Identity Protection em uma única detecção. Para obter mais informações, consulte [detecções de risco de entrada do Azure ad](/azure/active-directory/identity-protection/concept-identity-protection-risks#sign-in-risk).

Essas políticas serão exibidas na página políticas de Cloud App Security e poderão ser habilitadas ou desabilitadas.

## <a name="anomaly-detection-policies"></a>Políticas de detecção de anomalias

É possível ver as políticas de detecção de anomalias no portal clicando em **Controle** e em **Políticas**. Selecione **Política de detecção de anomalias** para o tipo de política.

 ![novas políticas de detecção de anomalias](media/new-anomaly-detection-policies.png)

As seguintes políticas de detecção de anomalias estão disponíveis:

### <a name="impossible-travel"></a>Viagem impossível

* Essa detecção identifica duas atividades do usuário (é uma única ou várias sessões) provenientes de locais geograficamente distantes em um período de tempo menor que o tempo que teria levado para o usuário viajar do primeiro local para o segundo, indicando que um usuário diferente está usando as mesmas credenciais. Essa detecção usa um algoritmo de aprendizado de máquina que ignora "falsos positivos" óbvios que contribuem para a condição de viagem impossível, como VPNs e locais usados regularmente por outros usuários da organização. A detecção tem um período de aprendizado inicial de sete dias durante o qual ele aprende o padrão de atividade de um novo usuário. A detecção de viagem impossível identifica atividades incomuns e impossíveis do usuário entre dois locais. A atividade deve ser incomum o suficiente para ser considerada um indicador de comprometimento e emitir um alerta. Para fazer isso funcionar, a lógica de detecção inclui níveis diferentes de supressão para lidar com cenários que podem disparar falsos positivos, como atividades de VPN. O controle deslizante de confidencialidade permite impactar o algoritmo e definir quão estrita a lógica de detecção deve ser. Quanto maior o nível de confidencialidade, menor a supressão que é aplicada como parte da lógica de detecção. Dessa forma, você pode adaptar a detecção de acordo com suas necessidades de cobertura e seus destinos de SNR.

    > [!NOTE]
    > Quando os endereços IP em ambos os lados da viagem são considerados seguros, a viagem é confiável e excluída do disparo da detecção de viagem impossível. Por exemplo, ambos os lados são considerados seguros se estiverem [marcados como corporativos](ip-tags.md). No entanto, se o endereço IP de apenas um dos lados da viagem for considerado seguro, a detecção será disparada normalmente.

### <a name="activity-from-infrequent-country"></a>Atividade de país não frequente

* Essa detecção considera os locais de atividades anteriores para determinar os locais novos e pouco frequentes. O mecanismo de detecção de anomalias armazena informações sobre locais anteriores usados por usuários na organização. Um alerta é disparado quando uma atividade ocorre em um local que nunca foi visitado ou não foi visitado recentemente por nenhum usuário na organização.

### <a name="malware-detection"></a>Detecção de malware

* Essa detecção identifica arquivos mal-intencionados no armazenamento em nuvem, sejam de aplicativos da Microsoft ou de aplicativos de terceiros. O Microsoft Cloud App Security usa a Inteligência Contra Ameaças da Microsoft para reconhecer se determinados arquivos estão associados a ataques de malware conhecidos e são possivelmente mal-intencionados. Essa política interna é desabilitada por padrão. Nem todo arquivo é examinado, mas é usada heurística para procurar arquivos que possam estar em risco. Depois que os arquivos são detectados, é exibida uma lista de **Arquivos infectados**. Clique no nome do arquivo de malware na gaveta do arquivo para abrir um relatório de malware que fornece informações sobre o tipo de malware com o qual o arquivo está infectado.

    Você pode usar essa detecção em tempo real usando políticas de sessão para controlar uploads e downloads de arquivos.

    > [!NOTE]
    >
    > O Cloud App Security dá suporte à detecção de malware para os seguintes aplicativos:
    >
    > * Box
    > * Dropbox
    > * Google Workspace
    > * Office 365 (requer uma licença válida para o Microsoft defender para Office 365 P1)

### <a name="activity-from-anonymous-ip-addresses"></a>Atividade de endereços IP anônimos

* Essa detecção identifica que os usuários estavam ativos com base em um endereço IP que foi identificado como um endereço IP de proxy anônimo. Esses proxies são usados por pessoas que desejam ocultar o endereço IP do dispositivo e podem ser usados para uma intenção mal-intencionada. Essa detecção usa um algoritmo de aprendizado de máquina que reduz "falsos positivos", como endereços IP marcados incorretamente usados amplamente por usuários da organização.

### <a name="ransomware-activity"></a>Atividade de ransomware

* O Cloud App Security ampliou seus recursos de detecção de ransomware com a detecção de anomalias para garantir uma cobertura mais abrangente contra ataques sofisticados de ransomware. Usando nossa experiência de pesquisa de segurança para identificar os padrões comportamentais que refletem a atividade de ransomware, o Cloud App Security garante uma proteção holística e robusta. Por exemplo, se o Cloud App Security identificar uma taxa alta de uploads de arquivos ou atividades de exclusão de arquivo, isso poderá representar um processo de criptografia adverso. Esses dados são coletados nos logs recebidos de APIs conectadas e são combinados com padrões comportamentais aprendidos e inteligência contra ameaças, por exemplo, extensões de ransomware conhecidas. Para obter mais informações sobre como o Cloud App Security detecta ransomware, confira [Proteger sua organização contra ransomware](use-case-ransomware.md).

### <a name="activity-performed-by-terminated-user"></a>Atividade realizada por usuário encerrado

* Essa detecção habilita você a identificar quando um funcionário demitido continua a executar ações em seus aplicativos SaaS. Como os dados mostram que o maior risco de ameaça interna vem de funcionários que deixaram a empresa descontentes, é importante ficar atento à atividade em contas de funcionários demitidos. Às vezes, quando funcionários deixam a empresa, suas contas são desprovisionadas de aplicativos corporativos, mas, em muitos casos, eles ainda mantêm o acesso a determinados recursos corporativos. Isso é ainda mais importante ao considerar as contas privilegiadas, pois os danos potenciais que um administrador anterior pode causar são inerentemente maiores.
Essa detecção se beneficia da capacidade do Cloud App Security de monitorar o comportamento do usuário entre aplicativos, permitindo a identificação da atividade regular do usuário, o fato de que a conta foi encerrada e atividade real em outros aplicativos. Por exemplo, um funcionário que é a conta do Azure AD foi encerrado, mas ainda tem acesso à infraestrutura AWS corporativa, tem o potencial de causar danos em larga escala.

A detecção procura usuários cuja conta foi encerrada no Azure AD, mas ainda executam atividades em outras plataformas, como AWS ou Salesforce. Isso é relevante principalmente para usuários que usam outra conta (não a conta de logon único principal) para gerenciar recursos, já que essas contas geralmente não são encerradas quando o usuário sai da empresa.

### <a name="activity-from-suspicious-ip-addresses"></a>Atividade de endereços IP suspeitos

* A detecção identifica que os usuários estavam ativos com base em um endereço IP identificado como arriscado pela Microsoft Threat Intelligence. Esses endereços IP estão envolvidos em atividades mal-intencionadas, como Botnet C&C, e podem indicar uma conta comprometida. Essa detecção usa um algoritmo de aprendizado de máquina que reduz "falsos positivos", como endereços IP marcados incorretamente usados amplamente por usuários da organização.

### <a name="suspicious-inbox-forwarding"></a>Encaminhamento suspeito da caixa de entrada

* Essa detecção procura regras de encaminhamento de email suspeito, por exemplo, se um usuário criou uma regra de caixa de entrada que encaminha uma cópia de todos os emails para um endereço externo.

> [!NOTE]
> O Cloud App Security só alerta você para cada regra de encaminhamento identificada como suspeita com base no comportamento típico do usuário.

### <a name="suspicious-inbox-manipulation-rules"></a>Regras de manipulação de caixa de entrada suspeita

* Essa detecção analisa o ambiente e dispara alertas quando regras suspeitas que excluem ou movem mensagens ou pastas são definidas na caixa de entrada de um usuário. Isso pode indicar que a conta de usuário está comprometida, que as mensagens foram ocultadas de forma intencional e que a caixa de correio está sendo usada para enviar spam e malware em sua organização.

### <a name="suspicious-email-deletion-activity-preview"></a>Atividade de exclusão de email suspeito (versão prévia)

* Essa política faz o perfil do seu ambiente e dispara alertas quando um usuário executa atividades suspeitas de exclusão de email em uma única sessão. Essa política pode indicar que as caixas de correio de um usuário podem ser comprometidas por possíveis vetores de ataque, como a comunicação de comando e controle (C&C/C2) por email.

> [!NOTE]
> O Cloud App Security integra-se com o Microsoft defender para Office 365 para fornecer proteção para o Exchange Online, incluindo URL denotação, proteção contra malware e muito mais. Depois que o defender para Office 365 estiver habilitado, você começará a ver os alertas no log de atividades Cloud App Security.

### <a name="suspicious-oauth-app-file-download-activities"></a>Atividades suspeitas de download do arquivo de aplicativo OAuth

* Examina os aplicativos OAuth conectados ao seu ambiente e dispara um alerta quando um aplicativo baixa vários arquivos do Microsoft SharePoint ou do Microsoft OneDrive de maneira incomum para o usuário. Isso pode indicar que a conta de usuário está comprometida.

### <a name="unusual-activities-by-user"></a>Atividades incomuns (por usuário)

Essas detecções identificam os usuários que executam:

* Atividades incomuns de vários downloads de arquivos
* Atividades incomuns de compartilhamento de arquivos
* Atividades incomuns de exclusão de arquivos
* Atividades representadas incomuns
* Atividades administrativas incomuns
* Atividades de compartilhamento de relatório Power BI incomum (versão prévia)
* Várias atividades de criação de VM incomuns (versão prévia)
* Várias atividades de exclusão de armazenamento incomum (visualização)
* Região incomum para recurso de nuvem (visualização)

Essas políticas buscam atividades em uma única sessão em relação à linha de base aprendida, que pode indicar uma tentativa de violação. As detecções se beneficiam de um algoritmo de aprendizado de máquina que analisa o padrão de logon dos usuários e reduz falsos positivos. Essas detecções fazem parte do mecanismo de detecção de anomalias heurística que cria o perfil de seu ambiente e dispara alertas em relação a uma linha de base que foi aprendida na atividade da sua organização.

### <a name="multiple-failed-login-attempts"></a>Várias tentativas de logon com falha

* A detecção identifica usuários que realizaram várias tentativas de logon com falha em uma única sessão em relação à linha de base aprendida, o que poderia indicar uma tentativa de violação.

### <a name="data-exfiltration-to-unsanctioned-apps"></a>Extração de dados para aplicativos não sancionados

* Essa política é habilitada automaticamente para alertar quando um usuário ou endereço IP usa um aplicativo que não está aprovado para executar uma atividade parecida com uma tentativa de extrair informações de sua organização.

### <a name="multiple-delete-vm-activities"></a>Várias atividades de exclusão de VM

* Esta política identifica seu ambiente e dispara alertas quando os usuários excluem várias VMs em uma única sessão em relação à linha de base em sua organização. Isso pode indicar uma tentativa de violação.

## <a name="enable-automated-governance"></a>Habilitar governança automatizada<a name="adp-automated-gov"></a>

É possível habilitar ações de correção automatizadas em alertas gerados por políticas de detecção de anomalias.

1. Clique no nome da política de detecção na página **Política**.
1. Na janela **Editar política de detecção de anomalias** que é aberta, em **Governança** defina as ações de correção que deseja para cada aplicativo conectado ou para todos os aplicativos.
1. Clique em **Atualizar**.

## <a name="tune-anomaly-detection-policies"></a>Ajustar as políticas de detecção de anomalias

Para afetar o mecanismo de detecção de anomalias para suprimir ou mostrar alertas de acordo com suas preferências:

* Na política Viagem Impossível, você pode definir o controle deslizante de sensibilidade para determinar o nível de comportamento anormal necessário antes que um alerta seja disparado. Por exemplo, se você defini-lo como baixo, ele suprimirá os alertas de viagem impossíveis dos locais comuns de um usuário e, se você defini-lo como alto, ele causará a superfície desses alertas. Você pode escolher entre os seguintes níveis de sensibilidade:

  * **Baixo**: supressões de sistema, locatário e usuário
  * **Média**: supressões de sistema e usuário
  * **Alta**: apenas supressões de sistema

    Sendo que:

    | Tipo de supressão | Descrição |
    | --- | --- |
    | **System** | Detecções internas que são sempre suprimidas. |
    | **Locatário** | Atividades comuns com base nas atividades anteriores no locatário. Por exemplo, suprimir atividades de um ISP alertado anteriormente em sua organização. |
    | **Usuário** | Atividades comuns com base nas atividades anteriores do usuário específico. Por exemplo, suprimir atividades de um local que é normalmente usado pelo usuário. |

* Você também pode configurar se os alertas de atividade de um país/região não frequente, endereços IP anônimos, endereços IP suspeitos e viagens impossíveis devem analisar logons com falha e com êxito ou apenas logons bem-sucedidos.

> [!NOTE]
> Por padrão, protocolos de entrada herdados, como aqueles que não usam a autenticação multifator (por exemplo, WS-Trust), não são monitorados pela política de viagem impossível. Se sua organização usa protocolos herdados, para evitar atividades relevantes ausentes, edite a política e, em **Configuração avançada**, defina **analisar as atividades de entrada** para **todas as** entradas.

## <a name="scope-anomaly-detection-policies"></a>Definir políticas de detecção de anomalias

Cada política de detecção de anomalias pode ter um escopo independente, de modo que se aplique apenas aos usuários e grupos que você deseja incluir e excluir na política.
Por exemplo, você pode definir a detecção de Atividade de região pouco frequente para ignorar um usuário específico que viaja com frequência.

Para definir uma política de detecção de anomalias:

1. Clique em políticas de **controle**  >  e defina o filtro de **tipo** como **política de detecção de anomalias**.
1. Clique na política que você deseja definir.
1. Em **Escopo**, altere o menu suspenso da configuração padrão de **Todos os usuários e grupos** para **Usuários e grupos específicos**.
1. Selecione **Incluir** para especificar os usuários e grupos para os quais essa política será aplicada. Qualquer usuário ou grupo não selecionado aqui não será considerado uma ameaça e não gerará um alerta.
1. Selecione **Excluir** para especificar usuários para os quais essa política não será aplicada. Qualquer usuário selecionado aqui não será considerado uma ameaça e não gerará um alerta, mesmo se eles forem membros de grupos selecionados em **Incluir**.

    ![escopo de detecção de anomalias](media/anomaly-detection-scoping.png)

## <a name="triage-anomaly-detection-alerts"></a>Triagem de alertas de detecção de anomalias

Você pode triar rapidamente os vários alertas disparados pelas novas políticas de detecção de anomalias e decidir quais precisam ser tratados primeiro. Para isso, é necessário o contexto do alerta para ver o panorama geral e entender se algo mal-intencionado realmente está acontecendo.

1. No **Log de atividades**, você pode abrir uma atividade para exibir a gaveta Atividades. Clique em **usuário** para exibir a guia insights do usuário. Essa guia inclui informações como o número de alertas, atividades e o local em que eles se conectaram, o que é importante em uma investigação.

    ![detecção de anomalias alert1 ](media/anomaly-alert-user1.png) ![ detecção de anomalias alert2](media/anomaly-alert-user2.png)

1. Isso permite que você entenda quais são as atividades suspeitas que o usuário executou e ter maior confiança sobre o comprometimento da conta. Por exemplo, um alerta de vários logons com falha pode realmente ser suspeito e indicar um ataque de força bruta em potencial, mas também pode ser um erro de configuração do aplicativo, fazendo com que o alerta seja um verdadeiro positivo benigno. No entanto, se você vir um alerta de vários logons com falha com atividades suspeitas adicionais, então há uma grande probabilidade de que a conta foi comprometida. No exemplo a seguir, você pode ver que o alerta **Várias tentativas de logon com falha** foi seguido de uma **Atividade de um endereço IP TOR** e de uma **Atividade de viagem impossível**, ambas fortes indicadores de comprometimento (IOCs) por si próprias. Se isso não era suspeito, você pode ver que o mesmo usuário realizou uma **atividade de download em massa**, que é geralmente um indicador do invasor que executa vazamento de dados.

    ![alert3 de detecção de anomalias](media/anomaly-alert-user3.png)

1. Para arquivos infectados por malware, depois que os arquivos forem detectados, será exibida uma lista de **Arquivos infectados**. Clique no nome do arquivo de malware na gaveta de arquivo para abrir um relatório de malware que oferece informações sobre o tipo de malware que infectou o arquivo.

## <a name="related-videos"></a>Vídeos relacionados

> [!div class="nextstepaction"]
> [Webinar de proteção contra ameaças](webinars.md#on-demand-webinars)

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]

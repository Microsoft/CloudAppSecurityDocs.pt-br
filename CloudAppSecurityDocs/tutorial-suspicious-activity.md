---
title: Detectar atividade de usuário suspeita com análise comportamental (UEBA)
description: Este tutorial descreve o processo de ajuste das detecções de atividade do usuário no Microsoft Cloud App Security.
ms.date: 05/10/2020
ms.topic: tutorial
ms.openlocfilehash: b8b971af09a2ae245999ddcae5f503912aec4d9f
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96315779"
---
# <a name="tutorial-detect-suspicious-user-activity-with-ueba"></a>Tutorial: detectar atividade de usuário suspeita com UEBA

[!INCLUDE [Banner for top of topics](includes/banner.md)]

O Microsoft Cloud App Security fornece as melhores detecções do setor em toda a cadeia de encerramento de ataques para usuários comprometidos, ameaças internas, exfiltração, ransomware e muito mais. Nossa solução abrangente é obtida pela combinação de vários métodos de detecção, incluindo anomalias, análise comportamental (UEBA) e detecções de atividades baseadas em regras, para fornecer uma visão ampla de como os usuários usam aplicativos em seu ambiente.

Por que é importante detectar um comportamento suspeito? O impacto de um usuário capaz de alterar seu ambiente de nuvem pode ser significativo e afetar diretamente sua capacidade de realizar negócios. Por exemplo, os principais recursos corporativos, como os servidores que executam o serviço ou site público que você está fornecendo aos clientes, podem ser comprometidos.

O Cloud App Security analisa dados capturados de várias fontes para extrair as atividades do aplicativo e do usuário em sua organização, proporcionando aos analistas de segurança visibilidade quanto ao uso da nuvem. Os dados coletados são correlacionados, padronizados e aprimorados com inteligência contra ameaças, localização e muitos outros detalhes para fornecer uma visão precisa e consistente de atividades suspeitas.

Portanto, para aproveitar totalmente os benefícios dessas detecções, primeiro garanta a configuração das seguintes fontes:

* **[Log de atividades](activity-filters.md)**  
Atividades dos seus [aplicativos conectados à API](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).
* **[Log de descoberta](tutorial-shadow-it.md)**  
Atividades extraídas dos logs de firewall e de tráfego de proxy que são encaminhadas ao Cloud App Security. Os logs são analisados em relação ao [catálogo de aplicativos na nuvem](risk-score.md), classificados e pontuados com base em mais de 80 fatores de risco.
* **[Log de proxy](proxy-intro-aad.md)**  
Atividades dos [aplicativos do Controle de Aplicativos de Acesso Condicional](tutorial-proxy.md#phase-1-monitor-user-activities-for-anomalies).

Em seguida, ajuste suas políticas. As políticas a seguir podem ser ajustadas definindo filtros, limites dinâmicos (UEBA) para ajudar a treinar seus modelos de detecção e supressões para reduzir as detecções comuns de falsos positivos:

* Detecção de anomalias
* Detecção de anomalias do Cloud Discovery
* Detecção de atividades baseada em regras

Este tutorial fornece instruções para ajustar as detecções de atividade do usuário a fim de identificar comprometimentos verdadeiros e reduzir o excesso de alertas resultantes do manuseio de grandes volumes de detecções de falsos positivos.

> [!div class="checklist"]
>
> * Configurar intervalos de endereços IP
> * Ajustar as políticas de detecção de anomalias
> * Ajustar as políticas de detecção de anomalias do Cloud Discovery
> * Ajustar as políticas de detecção baseada em regras
> * Configurar alertas
> * Investigar e corrigir

## <a name="phase-1-configure-ip-address-ranges"></a>Fase 1: configurar intervalos de endereços IP

Antes de configurar as políticas individuais, é aconselhável configurar os intervalos de IP de modo que eles fiquem disponíveis para uso no ajuste de qualquer tipo de política de detecção de atividade de usuário suspeita.

Como as informações de endereço IP são cruciais para quase todas as investigações, a [configuração de endereços IP conhecidos](ip-tags.md) ajuda nossos algoritmos de aprendizado de máquina a identificar locais conhecidos e considerá-los como parte dos modelos de machine learning. Por exemplo, a adição do intervalo de endereços IP da sua VPN ajudará o modelo a classificar de forma correta esse intervalo de IP e o excluirá automaticamente das detecções de viagens impossíveis, pois o local da VPN não representa o local verdadeiro desse usuário.

Observação:  Os intervalos de IP configurados não estão limitados a detecções e são usados em todas as áreas do Cloud App Security, como atividades no log de atividades, acesso condicional etc. Lembre-se disso ao configurar os intervalos. Portanto, por exemplo, identificar os endereços IP físicos do escritório permite personalizar a maneira como os logs e alertas são exibidos e investigados.

### <a name="review-out-of-the-box-anomaly-detection-alerts"></a>Revisar alertas de detecção de anomalias prontos para uso

O Cloud App Security inclui um conjunto de alertas de detecção de anomalias para identificar diferentes cenários de segurança. Essas detecções são habilitadas automaticamente na instalação e começarão a criar o perfil da atividade do usuário e gerar alertas assim que os [conectores de aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) relevantes estiverem conectados.

Comece familiarizando-se com as [diferentes políticas de detecção](control-cloud-apps-with-policies.md), priorize os principais cenários que você considera mais relevantes para sua organização e ajuste as políticas adequadamente.

## <a name="phase-2-tune-anomaly-detection-policies"></a>Fase 2: ajustar as políticas de detecção de anomalias

Várias políticas de detecção de anomalias internas estão disponíveis no Cloud App Security, pré-configuradas para casos de uso de segurança comuns. Deve levar algum tempo para você se familiarizar com as detecções mais populares, como:

* **Viagem impossível**  
Atividades do mesmo usuário em locais diferentes em um período menor do que o tempo de viagem esperado entre os dois locais.
* **Atividade de país não frequente**  
Atividade de um local que não foi visitado recentemente ou nunca foi visitado pelo usuário ou por qualquer usuário na organização.
* **Detecção de malware**  
Verifica os arquivos em seus aplicativos de nuvem e executa arquivos suspeitos por meio do mecanismo de inteligência contra ameaças da Microsoft para determinar se eles estão associados a um malware conhecido.
* **Atividade de ransomware**  
Carrega arquivos para a nuvem que podem estar infectados com ransomware.
* **Atividade de endereços IP suspeitos**  
Atividade de um endereço IP que foi identificado como suspeito pela Inteligência contra Ameaças da Microsoft.
* **Encaminhamento suspeito da caixa de entrada**  
Detecta regras de encaminhamento de caixa de entrada suspeitas definidas na caixa de entrada de um usuário.
* **Atividades incomuns de download de vários arquivos**  
Detecta várias atividades de download de arquivos em uma única sessão em relação à linha de base aprendida, o que poderá indicar uma tentativa de violação.
* **Atividade administrativas incomuns**  
Detecta várias atividades administrativas em uma única sessão em relação à linha de base aprendida, o que poderá indicar uma tentativa de violação.

Para obter uma lista completa de detecções e o que elas fazem, confira [Políticas de detecção de anomalias](anomaly-detection-policy.md#anomaly-detection-policies).

Quando estiver familiarizado com as políticas, você deverá considerar como deseja ajustá-las aos requisitos específicos de sua organização para direcionar melhor as atividades que deseje investigar ainda mais.

1. **Políticas de escopo para usuários ou grupos específicos**

    As políticas de escopo para usuários específicos podem ajudar a reduzir o ruído de alertas que não são relevantes para sua organização. Cada política pode ser [configurada para incluir ou excluir usuários e grupos específicos](anomaly-detection-policy.md#scope-anomaly-detection-policies), como nos seguintes exemplos:

    * **Simulações de ataque**  
    Muitas organizações usam um usuário ou um grupo para simular ataques com frequência. Obviamente, não faz sentido receber alertas constantes das atividades desses usuários. Portanto, você pode configurar suas políticas para excluir esses usuários ou grupos. Isso também ajuda os modelos de machine learning a identificar esses usuários e ajustar seus limites dinâmicos adequadamente.
    * **Detecções de destino**  
    Sua organização pode estar interessada em investigar um grupo específico de usuários VIP, como membros de um grupo de administradores ou de CXO. Nesse cenário, você pode criar uma política para as atividades que deseja detectar e optar por incluir apenas o conjunto de usuários ou grupos nos quais está interessado.

2. **Ajustar as detecções de entradas anômalas**

    Algumas organizações desejam ver os alertas resultantes de [atividades de entrada com falha](anomaly-detection-policy.md#multiple-failed-login-attempts), pois elas podem indicar que alguém está tentando violar uma ou mais contas de usuário. Por outro lado, ataques de força bruta em contas de usuário ocorrem o tempo todo na nuvem, e as organizações não têm como evitá-los. Portanto, as organizações maiores geralmente decidem receber somente os alertas de atividades de entrada suspeitas que resultam em entradas bem-sucedidas, pois podem representar comprometimentos verdadeiros.

    O roubo de identidade é uma das principais fontes de comprometimento e representa um grande vetor de ameaça para sua organização. Nossos alertas de detecções de [viagem impossível](anomaly-detection-policy.md#impossible-travel), [endereços IP anônimos](anomaly-detection-policy.md#activity-from-anonymous-ip-addresses) e [país não frequente](anomaly-detection-policy.md#activity-from-infrequent-country) ajudam a descobrir atividades que sugerem que uma conta está potencialmente comprometida. Convém personalizar essas políticas para se concentrarem apenas nas entradas bem-sucedidas que indicam uma ameaça iminente acionável e tomar medidas quanto a elas com rapidez. Por exemplo, você pode personalizar a política de país não frequente para alertar apenas sobre as entradas bem-sucedidas de locais que não foram visitados recentemente por nenhum usuário em sua organização. Para isso, [edite a política](anomaly-detection-policy.md#tune-anomaly-detection-policies) e, em Configuração avançada, defina Analisar as atividades de entrada para uma das opções de entrada bem-sucedidas.

3. **Ajuste a sensibilidade de [viagem impossível](anomaly-detection-policy.md#impossible-travel)** [Configure o controle deslizante de sensibilidade](anomaly-detection-policy.md#tune-anomaly-detection-policies) que determina o nível de supressões aplicado ao comportamento anormal antes de disparar um alerta de viagem impossível. Por exemplo, as organizações interessadas em alta fidelidade devem considerar o aumento do nível de sensibilidade. Por outro lado, caso sua organização tenha muitos usuários que viajam, considere reduzir o nível de sensibilidade para suprimir as atividades dos locais comuns de um usuário aprendidos com as atividades anteriores. Você pode escolher entre os seguintes níveis de sensibilidade:

    * **Baixa**: supressões de sistema, locatário e usuário
    * **Média**: supressões de sistema e usuário
    * **Alta**: apenas supressões de sistema

    Sendo que:

    | Tipo de supressão | Descrição |
    | --- | --- |
    | **System** | Detecções internas que são sempre suprimidas. |
    | **Locatário** | Atividades comuns com base nas atividades anteriores no locatário. Por exemplo, suprimir atividades de um ISP alertado anteriormente em sua organização. |
    | **Usuário** | Atividades comuns com base nas atividades anteriores do usuário específico. Por exemplo, suprimir atividades de um local que é normalmente usado pelo usuário. |

## <a name="phase-3-tune-cloud-discovery-anomaly-detection-policies"></a>Fase 3: Ajustar as políticas de detecção de anomalias do Cloud Discovery

Assim como as políticas de detecção de anomalias, há várias [políticas internas de detecção de anomalias do Cloud Discovery](cloud-discovery-anomaly-detection-policy.md) que você pode ajustar. Por exemplo, a política de exfiltração de dados para aplicativos não sancionados alerta quando os dados estão sendo vazados para um aplicativo não sancionado e vem pré-configurada com as definições baseadas na experiência da Microsoft no campo de segurança.

No entanto, você pode ajustar as políticas internas ou criar políticas próprias para ajudá-lo a identificar outros cenários que você está interessado em investigar. Como essas políticas se baseiam nos logs do Cloud Discovery, elas têm [recursos de ajuste](cloud-discovery-anomaly-detection-policy.md#cloud-discovery-anomaly-detection-policy-reference) diferentes, mais focados no comportamento anormal do aplicativo e na exfiltração de dados.

1. **Ajustar o monitoramento de uso**  
Defina os filtros de uso para controlar a linha de base, o escopo e o período de atividade para detectar o comportamento anormal. Por exemplo, talvez você queira receber alertas de atividades anormais relacionadas aos funcionários do nível executivo.

2. **Ajustar a sensibilidade de alerta**  
Para evitar o excesso de alertas, configure a sensibilidade deles. Você pode usar o controle deslizante de sensibilidade para controlar o número de alertas de alto risco enviados por 1.000 usuários por semana. As sensibilidades mais altas exigem menor variação para algo ser considerado uma anomalia e geram mais alertas. Em geral, defina uma sensibilidade baixa para os usuários que não têm acesso a dados confidenciais.

## <a name="phase-4-tune-rule-based-detection-activity-policies"></a>Fase 4: ajustar as políticas (atividade) de detecção baseada em regras

As [políticas de detecção baseada em regras](user-activity-policies.md) oferecem a capacidade de complementar as políticas de detecção de anomalias com requisitos específicos da organização. Recomendamos a criação de políticas baseadas em regras usando um dos nossos Modelos de política de atividade (acesse **Controle** > **Modelos** e defina o **Tipo** de filtro para **Política de atividade**) e, em seguida, [configure-os](activity-filters-queries.md) para detectar comportamentos que não são normais para seu ambiente. Por exemplo, para uma organização que não tem nenhuma presença em um país/região específico, faz sentido criar uma política que detecte as atividades anormais naquele país e alertá-la sobre elas. Para outras, que têm grandes filiais naquele país, as atividades realizadas nele seriam normais e não faria sentido detectá-las.

1. **Ajustar o volume de atividades**  
Escolha o volume de atividades necessário antes que a detecção gere um alerta. Usando nosso exemplo de país, se você não tiver nenhuma presença em um país/região, até mesmo uma única atividade será significativa e garantirá um alerta. No entanto, uma única falha de logon pode ser um erro humano e apenas interessará se houver muitas falhas em um curto período.
2. **Ajustar os [filtros de atividade](activity-filters-queries.md)**  
Defina os filtros necessários para detectar o tipo de atividade no qual você deseja alertas. Por exemplo, para detectar a atividade de um país, use o parâmetro **Local**.
3. **Ajustar alertas**  
Para evitar o excesso de alertas, defina o **limite diário de alertas**.

## <a name="phase-5-configure-alerts"></a>Fase 5: configurar alertas

Você pode optar por receber alertas no formato e meio que atenda melhor às suas necessidades. Para receber alertas imediatos a qualquer momento do dia, você pode preferir recebê-los por email ou mensagem de texto.

Você também pode querer analisar os alertas no contexto de outros alertas disparados por outros produtos em sua organização para ter uma visão holística de uma ameaça em potencial. Por exemplo, talvez você queira correlacionar eventos locais e baseados em nuvem para ver se há alguma outra evidência atenuante que possa confirmar um ataque.

Além disso, você também pode disparar a automação de alerta personalizada usando nossa integração com o [Microsoft Power Automate](flow-integration.md). Por exemplo, você pode configurar um guia estratégico automaticamente para criar um problema no [ServiceNow](/connectors/service-now/) ou enviar um email de aprovação para executar uma ação de governança personalizada quando um alerta for disparado.

Use as seguintes diretrizes para configurar seus alertas:

1. **Email/SMS**  
Escolha a preferência de entrega para receber alertas. Você pode recebê-los por email, mensagem de texto ou ambos.
2. **SIEM**  
Há várias opções de integração do SIEM, incluindo o [Azure Sentinel](siem-sentinel.md), a [API de Segurança do Microsoft Graph](/graph/security-integration#list-of-connectors-from-microsoft) e outros [SIEMs genéricos](siem.md). Escolha a integração que melhor atende às suas necessidades.
3. **Automação do Power Automate**  
Crie os guias estratégicos de automação de que você precisa e defina-os como o alerta da política para a ação do Power Automate.

## <a name="phase-6-investigate-and-remediate"></a>Fase 6: investigar e corrigir

Ótimo, você configurou suas políticas e começou a receber alertas de atividades suspeitas. O que você deve fazer sobre elas? Para começar, você deve executar as etapas para investigar a atividade. Por exemplo, convém examinar as atividades que indicam que um [usuário está comprometido](tutorial-ueba.md#identify).

Para otimizar sua proteção, considere configurar ações de correção automática a fim de minimizar o risco para sua organização. Nossas políticas permitem que você aplique [ações de governança](control.md) em conjunto com os alertas, de modo que o risco para sua organização seja reduzido mesmo antes de você começar a investigação. As ações disponíveis são determinadas pelo tipo de política, incluindo ações como suspender um usuário ou bloquear o acesso ao recurso solicitado.

[!INCLUDE [Open support ticket](includes/support.md)]

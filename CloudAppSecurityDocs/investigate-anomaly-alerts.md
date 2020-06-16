---
title: Guia de investigação de alertas de detecção de anomalias Cloud App Security
description: Este artigo explica como investigar os Cloud App Security alertas de detecção de anomalias emitidos quando são detectados ataques em sua organização.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 06/08/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: itfalcon
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 08eec9c9a8e684d53b0947ce186d661bf5e7d961
ms.sourcegitcommit: 826d2ec022647bce6c3135c115a41ee894ff8ecd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/16/2020
ms.locfileid: "84800802"
---
# <a name="how-to-investigate-anomaly-detection-alerts"></a>Como investigar alertas de detecção de anomalias

*Aplica-se a: Microsoft Cloud App Security*

Microsoft Cloud App Security fornece detecções de segurança e alertas para atividades mal-intencionadas. A finalidade deste guia é fornecer informações gerais e práticas sobre cada alerta, para ajudar com suas tarefas de investigação e correção. Neste guia, estão incluídas informações gerais sobre as condições para disparar alertas. No entanto, é importante observar que, como as detecções de anomalias são não determinísticas por natureza, elas são disparadas apenas quando há um comportamento que se desvia da norma. Por fim, alguns alertas podem estar em versão prévia, portanto, examine regularmente a documentação oficial para obter o status de alerta atualizado.

## <a name="mitre-attck"></a>MITRE ATT \& CK

Para explicar e tornar mais fácil mapear a relação entre Cloud App Security alertas e a conhecida matriz MITRE ATT \& CK, nós categorizamos os alertas por sua tática Mitre ATT \& CK correspondente. Essa referência adicional torna mais fácil entender a técnica de ataques suspeitos potencialmente em uso quando um alerta de Cloud App Security é disparado.

Este guia fornece informações sobre a investigação e correção de Cloud App Security alertas nas categorias a seguir.

> [!div class="checklist"]
>
> - [Acesso inicial](#initial-access-alerts)
> - [Execução](#execution-alerts)
> - [Persistência](#persistence-alerts)
> - [Elevação de privilégio](#privilege-escalation-alerts)
> - [Acesso à credencial](#credential-access-alerts)
> - [Coleção](#collection-alerts)
> - [Exportação](#exfiltration-alerts)
> - [Impacto](#impact-alerts)

## <a name="security-alert-classifications"></a>Classificações de alerta de segurança

Seguindo a investigação correta, todos os Cloud App Security alertas podem ser classificados como um dos seguintes tipos de atividade:

- **Verdadeiro positivo (TP)**: um alerta sobre uma atividade mal-intencionada confirmada.
- **Verdadeiro positivo benigno (B-TP)**: um alerta sobre atividades suspeitas, mas não mal-intencionadas, como um teste de penetração ou outra ação suspeita autorizada.
- **Falso positivo (FP)**: um alerta em uma atividade não mal-intencionada.

## <a name="general-investigation-steps"></a>Etapas de investigação geral

Você deve usar as seguintes diretrizes gerais ao investigar qualquer tipo de alerta para obter uma compreensão mais clara da ameaça potencial antes de aplicar a ação recomendada.

- Examine a pontuação de [prioridade de investigação](tutorial-ueba.md#understand-the-investigation-priority-score) do usuário e compare com o restante da organização. Isso ajudará a identificar quais usuários em sua organização representam o maior risco.
- Se você identificar uma **TP**, examine todas as atividades do usuário para entender o impacto.
- Examine todas as atividades do usuário para outros indicadores de comprometimento e explore a origem e o escopo do impacto. Por exemplo, examine as seguintes informações de dispositivo do usuário e compare com informações conhecidas do dispositivo:
  - Sistema operacional e versão
  - Navegador e versão
  - Endereço IP e local

## <a name="initial-access-alerts"></a>Alertas de acesso inicial

Esta seção descreve os alertas que indicam que um ator mal-intencionado pode estar tentando obter um destaque inicial em sua organização.

### <a name="activity-from-anonymous-ip-address"></a>Atividade de endereço IP anônimo

**Descrição**

Atividade de um endereço IP que foi identificado como um endereço IP de proxy anônimo pela inteligência contra ameaças da Microsoft ou pela sua organização. Esses proxies podem ser usados para ocultar o endereço IP de um dispositivo e podem ser usados para atividades mal-intencionadas.

**TP**, **B-TP**ou **FP**?

Essa detecção usa um algoritmo de aprendizado de máquina que reduz incidentes **B-TP** , como endereços IP com marcas de tipo de mis que são amplamente usadas por usuários na organização.

1. **TP**: se você conseguir confirmar que a atividade foi executada a partir de um endereço IP anônimo ou Tor.

    **Ação recomendada**: suspenda o usuário, marque o usuário como comprometido e Redefina sua senha.
1. **B-TP**: se um usuário for conhecido a usar endereços IP anônimos no escopo de suas tarefas. Por exemplo, quando um analista de segurança realiza testes de segurança ou de penetração em nome da organização.

    **Ação recomendada**: ignorar o alerta.

**Entender o escopo da violação**

- Revise todos os alertas e a atividade do usuário para indicadores adicionais de comprometimento. Por exemplo, se o alerta foi seguido por outro alerta suspeito, como um [download de arquivo incomum (por usuário)](#unusual-file-download-by-user) ou um alerta de [encaminhamento de caixa de entrada suspeito](#suspicious-inbox-forwarding) , isso geralmente indica que um invasor está tentando exfiltrar dados.

### <a name="activity-from-infrequent-country"></a>Atividade de país não frequente

Atividade de um país que pode indicar atividades mal-intencionadas. Essa política faz o perfil do seu ambiente e dispara alertas quando a atividade é detectada de um local que não foi recentemente ou que nunca foi visitada por nenhum usuário na organização.

Por padrão, a política está configurada para incluir apenas atividades de entrada bem-sucedidas, mas pode ser configurada para incluir qualquer atividade de entrada. A política pode ser ainda mais delimitada para um subconjunto de usuários ou pode excluir usuários conhecidos por viajar para locais remotos.

**Período de aprendizado**

Detectar locais anormais requer um período de aprendizado inicial de sete dias durante o qual os alertas não são disparados para novos locais.

**TP**, **B-TP**ou **FP**?

1. **TP**: se for possível confirmar se a atividade não foi executada por um usuário legítimo.

    **Ação recomendada**:
    1. Suspenda o usuário, redefina sua senha e identifique a hora certa para reabilitar a conta com segurança.
    1. Opcional: Crie um guia estratégico usando a automatização de energia para contatar os usuários detectados como conexão de locais infrequentes e seus gerentes, para verificar sua atividade.
1. **B-TP**: se for conhecido um usuário nesse local. Por exemplo, quando um usuário viaja com frequência e está atualmente no local especificado.

    **Ação recomendada**:
    1. Ignore o alerta e modifique a política para excluir o usuário.
    1. Criar um grupo de usuários para viajantes frequentes, importar o grupo para Cloud App Security e excluir os usuários desse alerta
    1. Opcional: Crie um guia estratégico usando a automatização de energia para contatar os usuários detectados como conexão de locais infrequentes e seus gerentes, para verificar sua atividade.

**Entender o escopo da violação**

- Examine qual recurso pode ter sido comprometido, como possíveis downloads de dados.

### <a name="activity-from-suspicious-ip-addresses"></a>Atividade de endereços IP suspeitos

Atividade de um endereço IP que foi identificado como arriscado pela inteligência contra ameaças da Microsoft ou pela sua organização. Esses endereços IP foram identificados como envolvidos em atividades mal-intencionadas, como comando de botnet e controle (C&C) e podem indicar uma conta comprometida.

**TP**, **B-TP**ou **FP**?

1. **TP**: se for possível confirmar se a atividade não foi executada por um usuário legítimo.

    **Ação recomendada**: suspenda o usuário, marque o usuário como comprometido e Redefina sua senha.
1. **B-TP**: se um usuário for conhecido a usar o endereço IP no escopo de suas tarefas. Por exemplo, quando um analista de segurança realiza testes de segurança ou de penetração em nome da organização.

    **Ação recomendada**: ignorar o alerta.

**Entender o escopo da violação**

1. Examine o log de atividades e pesquise por atividades do mesmo endereço IP.
1. Examine qual recurso pode ter sido comprometido, como downloads de dados potenciais ou modificações administrativas.
1. Crie um grupo para analistas de segurança que disparem voluntariamente esses alertas e exclua-os da política.

### <a name="impossible-travel"></a>Viagem impossível

Atividade do mesmo usuário em locais diferentes dentro de um período de tempo menor do que o tempo de viagem esperado entre os dois locais. Isso pode indicar uma violação de credencial, no entanto, também é possível que o local real do usuário seja mascarado, por exemplo, usando uma VPN.

Para melhorar a precisão e o alerta apenas quando há uma indicação forte de uma violação, Cloud App Security estabelece uma linha de base em cada usuário na organização e alertará somente quando o comportamento incomum for detectado. A política de viagem impossível pode ser ajustada aos seus requisitos.

**Período de aprendizado**

O estabelecimento do padrão de atividade de um novo usuário requer um período de aprendizado inicial de sete dias durante o qual os alertas não são disparados para novos locais.

**TP**, **B-TP**ou **FP**?

Essa detecção usa um algoritmo de aprendizado de máquina que ignora as condições de **B-TP** óbvias, como quando os endereços IP em ambos os lados da viagem são considerados seguros, a viagem é confiável e excluída do disparo da detecção de viagem impossível. Por exemplo, ambos os lados são considerados seguros se estiverem [marcados como corporativos](ip-tags.md). No entanto, se o endereço IP de apenas um dos lados da viagem for considerado seguro, a detecção será disparada normalmente.

1. **TP**: se for possível confirmar se o local no alerta de viagem impossível é improvável para o usuário.

    **Ação recomendada**: suspenda o usuário, marque o usuário como comprometido e Redefina sua senha.
1. **FP** (viagem de usuário não detectada): se você conseguir confirmar se o usuário viajau recentemente para o destino mencionado detalhado no alerta. Por exemplo, se o telefone de um usuário que está no modo avião permanece conectado a serviços como o Exchange Online em sua rede corporativa enquanto viaja para um local diferente. Quando o usuário chega ao novo local, o telefone se conecta ao Exchange Online disparando o alerta de viagem impossível.

    **Ação recomendada**: ignorar o alerta.
1. **FP** (VPN não marcada): se você for capaz de confirmar se o intervalo de endereços IP é de uma VPN emissora.

    **Ação recomendada**: ignore o alerta e [adicione o intervalo de endereços IP da VPN](ip-tags.md#create-an-ip-address-range) a Cloud app Security e, em seguida, use-o para marcar o intervalo de endereços IP da VPN.

**Entender o escopo da violação**

1. Examine o log de atividades para obter uma compreensão das atividades semelhantes no mesmo local e endereço IP.
1. Se você vir que o usuário realizou outras atividades arriscadas, como baixar um grande volume de arquivos de um novo local, isso seria uma indicação forte de um possível comprometimento.
1. Adicione os intervalos de endereços IP e VPN corporativos.
1. Crie um guia estratégico usando a automatização de energia e entre em contato com o gerente do usuário para ver se o usuário está viajando de forma legítima.
1. Considere criar um banco de dados de viagem conhecido para até o minuto relatório de viagem organizacional e usá-lo para fazer referência cruzada da atividade de viagem.

### <a name="misleading-oauth-app-name"></a>Nome do aplicativo OAuth enganoso

O nome do aplicativo OAuth enganoso identifica aplicativos com caracteres, como cartas estrangeiras, que se assemelham a letras latinas. Isso pode indicar uma tentativa de disfarçar um aplicativo mal-intencionado como um aplicativo conhecido e confiável para que os invasores possam induzir os usuários a baixarem seus aplicativos mal-intencionados.

**TP**, **B-TP**ou **FP**?

1. **TP**: se for possível confirmar se o aplicativo tem um nome enganoso.

    **Ação recomendada**: revise o nível de permissão solicitado por este aplicativo e quais usuários concederam acesso. Com base em sua investigação, você pode optar por proibir o acesso a esse aplicativo.

Para proibir o acesso ao aplicativo, na página **aplicativos OAuth** , na linha na qual o aplicativo que você deseja proibir é exibido, clique no ícone de Ban.
    - Você pode escolher se deseja informar os usuários de que o aplicativo instalado e autorizado foi vetado. A notificação permite que os usuários saibam que o aplicativo será desabilitado e eles não terão acesso ao aplicativo conectado. Se não quiser que eles saibam, cancele a seleção de **Notificar os usuários que concederam acesso a esse aplicativo vetado** na caixa de diálogo.
    - Recomendamos informar os usuários do aplicativo de que ele está prestes a ter o uso vetado.

1. **FP**: se você for confirmar que o aplicativo tem um nome enganoso, mas que tem um uso comercial legítimo na organização.

    **Ação recomendada**: ignorar o alerta.

**Entender o escopo da violação**

- Siga o tutorial sobre como [investigar aplicativos de OAuth arriscados](investigate-risky-oauth.md).

### <a name="misleading-publisher-name-for-an-oauth-app"></a>Nome do editor enganoso para um aplicativo OAuth

O nome do editor OAuth enganoso para um aplicativo OAuth identifica aplicativos com caracteres, como cartas estrangeiras, que se assemelham a letras latinas. Isso pode indicar uma tentativa de disfarçar um aplicativo mal-intencionado como um aplicativo conhecido e confiável para que os invasores possam induzir os usuários a baixarem seus aplicativos mal-intencionados.

**TP**, **B-TP**ou **FP**?

1. **TP**: se for possível confirmar se o aplicativo tem um nome de editor enganoso.

    **Ação recomendada**: revise o nível de permissão solicitado por este aplicativo e quais usuários concederam acesso. Com base em sua investigação, você pode optar por proibir o acesso a esse aplicativo.
1. **FP**: se você for confirmar que o aplicativo tem um nome de editor enganoso, mas é um Publicador legítimo.

    **Ação recomendada**: ignorar o alerta.

**Entender o escopo da violação**

1. Na página **aplicativos OAuth** , clique no aplicativo para abrir a gaveta do **aplicativo**e clique em **atividade relacionada**. Isso abre a página **log de atividades** filtrada para atividades executadas pelo aplicativo. Lembre-se de que alguns aplicativos realizam atividades que foram registradas como executadas por um usuário. Essas atividades são automaticamente filtradas dos resultados no log de atividades. Para uma investigação adicional usando o log de atividades, confira [Log de atividades](activity-filters.md).
1. Se você suspeitar de que um aplicativo é suspeito, recomendamos que investigue o nome do aplicativo e o Publicador em lojas de aplicativos diferentes. Ao verificar as lojas de aplicativos, concentre-se nos seguintes tipos de aplicativos:
    - Aplicativos com um número baixo de downloads.
    - Aplicativos com uma classificação ou pontuação baixas ou comentários negativos.
    - Aplicativos com um editor ou website suspeito.
    - Aplicativos que não foram atualizados recentemente. Isso pode indicar um aplicativo que não tem mais suporte.
    - Aplicativos com permissões irrelevantes. Isso pode indicar que um aplicativo é arriscado.
1. Se você ainda suspeitar que um aplicativo é suspeito, poderá pesquisar o nome do aplicativo, o editor e a URL online.

## <a name="execution-alerts"></a>Alertas de execução

Esta seção descreve os alertas que indicam que um ator mal-intencionado pode estar tentando executar código mal-intencionado em sua organização.

### <a name="multiple-storage-deletion-activities"></a>Várias atividades de exclusão de armazenamento

Atividades em uma única sessão que indicam que um usuário realizou um número incomum de armazenamento em nuvem ou exclusões de bancos de dados de recursos como BLOBs do Azure, Buckets AWS S3 ou Cosmos DB em comparação com a linha de base aprendida. Isso pode indicar uma tentativa de violação da sua organização.

**Período de aprendizado**

O estabelecimento do padrão de atividade de um novo usuário requer um período de aprendizado inicial de sete dias durante o qual os alertas não são disparados para novos locais.

**TP**, **B-TP**ou **FP**?

1. **TP**: se você for confirmar que as exclusões não foram autorizadas.

    **Ação recomendada**: suspenda o usuário, redefina sua senha e verifique todos os dispositivos em busca de ameaças mal-intencionadas. Examine todas as atividades do usuário para outros indicadores de comprometimento e explore o escopo do impacto.
1. **FP**: se depois de sua investigação, você poderá confirmar se o administrador foi autorizado a executar essas atividades de exclusão.

    **Ação recomendada**: ignorar o alerta.

**Entender o escopo da violação**

1. Contate o usuário e confirme a atividade.
1. Examine o log de atividades para ver outros indicadores de comprometimento e veja quem fez a alteração.
1. Examine as atividades do usuário em busca de alterações em outros serviços.

### <a name="multiple-vm-creation-activities"></a>Várias atividades de criação de VM

Atividades em uma única sessão que indica que um usuário realizou um número incomum de ações de criação de VM em comparação com a linha de base aprendida. Várias criações de VM em uma infraestrutura de nuvem violada podem indicar uma tentativa de executar operações de mineração de criptografia de dentro de sua organização.

**Período de aprendizado**

O estabelecimento do padrão de atividade de um novo usuário requer um período de aprendizado inicial de sete dias durante o qual os alertas não são disparados para novos locais.

**TP**, **B-TP**ou **FP**?

Para melhorar a precisão e o alerta apenas quando há uma indicação forte de uma violação, essa detecção estabelece uma linha de base em cada ambiente na organização para reduzir os incidentes **de B-TP** , como um administrador, legitimamente, criava mais VMs do que a linha de base estabelecida e apenas alerta quando o comportamento incomum é detectado.

- **TP**: se for possível confirmar se as atividades de criação não foram executadas por um usuário legítimo.

    **Ação recomendada**: suspenda o usuário, redefina sua senha e verifique todos os dispositivos em busca de ameaças mal-intencionadas. Examine todas as atividades do usuário para outros indicadores de comprometimento e explore o escopo do impacto. Além disso, contate o usuário, confirme suas ações legítimas e certifique-se de desabilitar ou excluir quaisquer VMs comprometidas.
- **B-TP**: se depois de sua investigação, você poderá confirmar se o administrador foi autorizado a executar essas atividades de criação.

    **Ação recomendada**: ignorar o alerta.

**Entender o escopo da violação**

1. Examine todas as atividades do usuário para outros indicadores de comprometimento.
1. Examine os recursos criados ou modificados pelo usuário e verifique se eles estão em conformidade com as políticas da sua organização.

### <a name="suspicious-creation-activityfor-cloudregion-preview"></a>Atividade de criação suspeita para a região de nuvem (versão prévia)

Atividades que indicam que um usuário realizou uma ação de criação de recurso incomum em uma região AWS não comum quando comparado à linha de base aprendida. A criação de recursos em regiões de nuvem incomuns pode indicar uma tentativa de executar uma atividade mal-intencionada, como operações de mineração de criptografia de dentro da sua organização.

**Período de aprendizado**

O estabelecimento do padrão de atividade de um novo usuário requer um período de aprendizado inicial de sete dias durante o qual os alertas não são disparados para novos locais.

**TP**, **B-TP**ou **FP**?

Para melhorar a precisão e o alerta apenas quando há uma indicação forte de uma violação, essa detecção estabelece uma linha de base em cada ambiente na organização para reduzir os incidentes **de B-TP** .

- **TP**: se for possível confirmar se as atividades de criação não foram executadas por um usuário legítimo.

    **Ação recomendada**: suspenda o usuário, redefina sua senha e verifique todos os dispositivos em busca de ameaças mal-intencionadas. Examine todas as atividades do usuário para outros indicadores de comprometimento e explore o escopo do impacto. Além disso, contate o usuário, confirme suas ações legítimas e certifique-se de desabilitar ou excluir todos os recursos comprometidos de nuvem.
- **B-TP**: se depois de sua investigação, você poderá confirmar se o administrador foi autorizado a executar essas atividades de criação.

    **Ação recomendada**: ignorar o alerta.

**Entender o escopo da violação**

1. Examine todas as atividades do usuário para outros indicadores de comprometimento.
1. Examine os recursos criados e verifique se eles estão em conformidade com as políticas da sua organização.

## <a name="persistence-alerts"></a>Alertas de persistência

Esta seção descreve os alertas que indicam que um ator mal-intencionado pode estar tentando manter seu destaque em sua organização.

### <a name="activity-performed-by-terminated-user"></a>Atividade realizada por usuário encerrado

A atividade executada por um usuário encerrado pode indicar que um funcionário encerrado que ainda tem acesso aos recursos corporativos está tentando executar uma atividade mal-intencionada. Cloud App Security cria perfis de usuários na organização e dispara um alerta quando um usuário encerrado executa uma atividade.

**TP**, **B-TP**ou **FP**?

1. **TP**: se você conseguir confirmar se o usuário encerrado ainda tem acesso a determinados recursos corporativos e está executando atividades.

    **Ação recomendada**: desabilite o usuário.
1. **B-TP**: se for possível determinar se o usuário foi desabilitado temporariamente ou se foi excluído e registrado novamente.

    **Ação recomendada**: ignorar o alerta.

**Entender o escopo da violação**

1. Registros de RH de referência cruzada para confirmar que o usuário foi encerrado.
1. Valide a existência da conta de usuário do Azure Active Directory (AD do Azure).
    > [!NOTE]
    > Se estiver usando Azure AD Connect, valide o objeto Active Directory local e confirme um ciclo de sincronização bem-sucedido.
1. Identifique todos os aplicativos para os quais o usuário final tinha acesso e encerre as contas.
1. Atualize os procedimentos de encerramento.

### <a name="suspicious-change-of-cloudtrail-logging-service"></a>Alteração suspeita do serviço de log CloudTrail

As atividades em uma única sessão que indicam que, um usuário realizou alterações suspeitas no serviço de log do AWS CloudTrail. Isso pode indicar uma tentativa de violação da sua organização. Ao desabilitar o CloudTrail, as alterações operacionais não são mais registradas. Um invasor pode executar atividades mal-intencionadas e, ao mesmo tempo, evitar um evento de auditoria CloudTrail, como modificar um Bucket S3 de privado para público.

**TP**, **B-TP**ou **FP**?

1. **TP**: se for possível confirmar se a atividade não foi executada por um usuário legítimo.

    **Ação recomendada**: suspenda o usuário, redefina sua senha e inverta a atividade CloudTrail.
1. **FP**: se for possível confirmar se o usuário desabilitou legitimamente o serviço CloudTrail.

    **Ação recomendada**: ignorar o alerta.

**Entender o escopo da violação**

1. Examine o log de atividades para ver outros indicadores de comprometimento e veja quem fez a alteração no serviço CloudTrail.
1. Opcional: Crie um guia estratégico usando a automatização de energia para contatar os usuários e seus gerentes para verificar sua atividade.

### <a name="suspicious-email-deletion-activity-by-user"></a>Atividade de exclusão de email suspeito (por usuário)

Atividades em uma única sessão que indica que um usuário realizou exclusões de email suspeitas. Isso pode indicar uma tentativa de violação da sua organização, como invasores tentando mascarar operações excluindo emails relacionados a atividades de spam.

**TP**, **B-TP**ou **FP**?

1. **TP**: se for possível confirmar se a atividade não foi executada por um usuário legítimo.

    **Ação recomendada**: suspenda o usuário, marque o usuário como comprometido e Redefina sua senha.
1. **FP**: se você conseguir confirmar que o usuário criou legitimamente uma regra para excluir mensagens.

    **Ação recomendada**: ignorar o alerta.

**Entender o escopo da violação**

- Examine todas as atividades do usuário para ver indicadores adicionais de comprometimento, como o alerta de [encaminhamento de caixa de entrada suspeito](#suspicious-inbox-forwarding) seguido por um alerta de [viagem impossível](#impossible-travel) . Procurar:

    1. Novas regras de encaminhamento de SMTP, da seguinte maneira:
        - Verifique se há nomes de regra de encaminhamento mal-intencionado. Os nomes de regra podem variar de nomes simples, como "encaminhar todos os emails" e "encaminhamento automático" ou nomes enganosos, como um "." mal visível. Os nomes de regra de encaminhamento podem até estar vazios e o destinatário de encaminhamento pode ser uma única conta de email ou uma lista inteira. As regras mal-intencionadas também podem ser ocultadas da interface do usuário. Depois de detectado, você pode usar esta [postagem de blog](https://blogs.msdn.microsoft.com/hkong/2015/02/27/how-to-delete-corrupted-hidden-inbox-rules-from-a-mailbox-using-mfcmapi/) útil sobre como excluir regras ocultas de caixas de correio.
        - Se você detectar uma regra de encaminhamento não reconhecida para um endereço de email interno ou externo desconhecido, poderá assumir que a conta da caixa de entrada foi comprometida.
    1. Novas regras de caixa de entrada, como "excluir tudo", "mover mensagens para outra pasta" ou aquelas com convenções de nomenclatura obscuras, por exemplo, "...".
    1. Um aumento nos emails enviados.

### <a name="suspicious-inbox-manipulation-rule"></a>Regra de manipulação de caixa de entrada suspeita

Atividades que indicam que um invasor obteve acesso à caixa de entrada de um usuário e criou uma regra suspeita. As regras de manipulação, como excluir ou mover mensagens, ou pastas, da caixa de entrada de um usuário podem ser uma tentativa de exfiltrar informações de sua organização. Da mesma forma, eles podem indicar uma tentativa de manipular informações que um usuário vê ou usar sua caixa de entrada para distribuir spam, emails de phishing ou malware. Cloud App Security perfis seu ambiente e dispara alertas quando regras de manipulação de caixa de entrada suspeitas são detectadas na caixa de entrada de um usuário. Isso pode indicar que a conta do usuário está comprometida.

**TP**, **B-TP**ou **FP**?

1. **TP**: se for possível confirmar se uma regra de caixa de entrada mal-intencionada foi criada e se a conta foi comprometida.

    **Ação recomendada**: suspenda o usuário, redefina sua senha e remova a regra de encaminhamento.
1. **FP**: se você conseguir confirmar que um usuário criou a regra de forma legítima.

    **Ação recomendada**: ignorar o alerta.

**Entender o escopo da violação**

1. Examine todas as atividades do usuário para ver indicadores adicionais de comprometimento, como o alerta de [encaminhamento de caixa de entrada suspeito](#suspicious-inbox-forwarding) seguido por um alerta de [viagem impossível](#impossible-travel) . Procurar:
    - Novas regras de encaminhamento de SMTP.
    - Novas regras de caixa de entrada, como "excluir tudo", "mover mensagens para outra pasta" ou aquelas com convenções de nomenclatura obscuras, por exemplo, "...".
1. Colete informações de endereço IP e local para a ação.
1. Examine as atividades executadas do endereço IP usado para criar a regra para detectar outros usuários comprometidos.

## <a name="privilege-escalation-alerts"></a>Alertas de escalonamento de privilégios

Esta seção descreve os alertas que indicam que um ator mal-intencionado pode estar tentando obter permissões de nível superior em sua organização.

### <a name="unusual-administrative-activity-by-user"></a>Atividade administrativa incomum (por usuário)

Atividades que indicam que um invasor comprometeu uma conta de usuário e executou ações administrativas que não são comuns para esse usuário. Por exemplo, um invasor pode tentar alterar uma configuração de segurança para um usuário, uma operação relativamente rara para um usuário comum. Cloud App Security cria uma linha de base com base no comportamento do usuário e dispara um alerta quando o comportamento incomum é detectado.

**Período de aprendizado**

O estabelecimento do padrão de atividade de um novo usuário requer um período de aprendizado inicial de sete dias durante o qual os alertas não são disparados para novos locais.

**TP**, **B-TP**ou **FP**?

1. **TP**: se for possível confirmar se a atividade não foi executada por um administrador legítimo.

    **Ação recomendada**: suspenda o usuário, marque o usuário como comprometido e Redefina sua senha.
1. **FP**: se você conseguir confirmar que um administrador executou legitimamente o volume incomum de atividades administrativas.

    **Ação recomendada**: ignorar o alerta.

**Entender o escopo da violação**

1. Examine todas as atividades do usuário para indicadores adicionais de comprometimento, como [encaminhamento de caixa de entrada suspeito](#suspicious-inbox-forwarding) ou [viagem impossível](#impossible-travel).
1. Revise outras alterações de configuração, como a criação de uma conta de usuário que pode ser usada para persistência.

## <a name="credential-access-alerts"></a>Alertas de acesso à credencial

Esta seção descreve os alertas que indicam que um ator mal-intencionado pode estar tentando roubar nomes de conta e senhas de sua organização.

### <a name="multiple-failed-login-attempts"></a>Várias tentativas de logon com falha

Tentativas de logon com falha podem indicar uma tentativa de violar uma conta. No entanto, os logons com falha também podem ser um comportamento normal. Por exemplo, quando um usuário inseriu uma senha incorreta por engano. Para obter precisão e alertar apenas quando há uma indicação forte de uma tentativa de violação, Cloud App Security estabelece uma linha de base de hábitos de logon para cada usuário na organização e só alertará quando o comportamento incomum for detectado.

**Período de aprendizado**

O estabelecimento do padrão de atividade de um novo usuário requer um período de aprendizado inicial de sete dias durante o qual os alertas não são disparados para novos locais.

**TP**, **B-TP**ou **FP**?

Essa política se baseia em aprender o comportamento de logon normal de um usuário. Quando um desvio da norma é detectado, um alerta é disparado. Se a detecção começar a ver que o mesmo comportamento continua, o alerta será gerado apenas uma vez.

1. **TP** (falha de MFA): se você conseguir confirmar que a MFA está funcionando corretamente, isso pode ser um sinal de uma tentativa de ataque de força bruta.

    **Ações recomendadas**:
    1. Suspenda o usuário, marque o usuário como comprometido e Redefina sua senha.
    1. Localize o aplicativo que realizou as autenticações com falha e reconfigure-o.
    1. Procure outros usuários conectados em todo o tempo da atividade, pois eles também podem ser comprometidos. Suspenda o usuário, marque o usuário como comprometido e Redefina sua senha.
1. **B-TP** (falha de MFA): se você conseguir confirmar se o alerta é causado por um problema com a MFA.

    **Ação recomendada**: Crie um guia estratégico usando a automatização de energia para entrar em contato com o usuário e verificar se eles estão tendo problemas com a MFA.
1. **B-TP** (aplicativo configurado incorretamente): se você for capaz de confirmar se um aplicativo mal configurado está tentando se conectar a um serviço várias vezes com credenciais expiradas.

    **Ação recomendada**: ignorar o alerta.
1. **B-TP** (senha alterada): se você for capaz de confirmar que um usuário alterou recentemente sua senha, mas não afetou as credenciais entre compartilhamentos de rede.

    **Ação recomendada**: ignorar o alerta.
1. **B-TP** (teste de segurança): se você for capaz de confirmar se um teste de segurança ou de penetração está sendo conduzido por analistas de segurança em nome da organização.

    **Ação recomendada**: ignorar o alerta.

**Entender o escopo da violação**

1. Examine todas as atividades do usuário para ver indicadores adicionais de comprometimento, como o alerta, seguido de um dos seguintes alertas: [viagem impossível](#impossible-travel), [atividade de endereço IP anônimo](#activity-from-anonymous-ip-address)ou [atividade de um país infrequente](#activity-from-infrequent-country).
1. Examine as seguintes informações de dispositivo do usuário e compare com as informações conhecidas do dispositivo:
    - Sistema operacional e versão
    - Navegador e versão
    - Endereço IP e local
1. Identifique o endereço IP de origem ou o local em que ocorreu a tentativa de autenticação.
1. Identifique se o usuário alterou recentemente sua senha e se todos os aplicativos e dispositivos têm a senha atualizada.

## <a name="collection-alerts"></a>Alertas de coleta

Esta seção descreve os alertas que indicam que um ator mal-intencionado pode estar tentando reunir dados de interesse para sua meta de sua organização.

### <a name="multiple-power-bi-report-sharing-activities"></a>Várias atividades de compartilhamento de relatório Power BI

Atividades em uma única sessão que indica que um usuário realizou um número incomum de atividades de relatório de compartilhamento em Power BI em comparação com a linha de base aprendida. Isso pode indicar uma tentativa de violação da sua organização.

**Período de aprendizado**

O estabelecimento do padrão de atividade de um novo usuário requer um período de aprendizado inicial de sete dias durante o qual os alertas não são disparados para novos locais.

**TP**, **B-TP**ou **FP**?

1. **TP**: se for possível confirmar se a atividade não foi executada por um usuário legítimo.

    **Ação recomendada**: remover acesso de compartilhamento de Power bi. Se você conseguir confirmar que a conta está comprometida, suspenda o usuário, marque o usuário como comprometido e Redefina sua senha.
1. **FP**: se você for capaz de confirmar se o usuário teve uma justificativa de negócios para compartilhar esses relatórios.

    **Ação recomendada**: ignorar o alerta.

**Entender o escopo da violação**

1. Examine o log de atividades para obter uma compreensão melhor de outras atividades executadas pelo usuário. Examine o endereço IP no qual eles estão conectados e os detalhes do dispositivo.
1. Contate a equipe de Power BI ou a equipe de proteção de informações para entender as diretrizes para compartilhar relatórios interna e externamente.

### <a name="suspicious-power-bi-report-sharing"></a>Compartilhamento suspeito de relatório do Power BI

Atividades que indicam que um usuário compartilhou um relatório de Power BI que pode conter informações confidenciais identificadas usando NLP para analisar os metadados do relatório. O relatório foi compartilhado com um endereço de email externo, publicado na Web ou um instantâneo foi entregue a um endereço de email assinado externamente. Isso pode indicar uma tentativa de violação da sua organização.

**TP**, **B-TP**ou **FP**?

1. **TP**: se for possível confirmar se a atividade não foi executada por um usuário legítimo.

    **Ação recomendada**: remover acesso de compartilhamento de Power bi. Se você conseguir confirmar que a conta está comprometida, suspenda o usuário, marque o usuário como comprometido e Redefina sua senha.
1. **FP**: se você conseguir confirmar que o usuário teve uma justificativa de negócios para compartilhar esses relatórios.

    **Ação recomendada**: ignorar o alerta.

**Entender o escopo da violação**

1. Examine o log de atividades para obter uma compreensão melhor de outras atividades executadas pelo usuário. Examine o endereço IP no qual eles estão conectados e os detalhes do dispositivo.
1. Contate a equipe de Power BI ou a equipe de proteção de informações para entender as diretrizes para compartilhar relatórios interna e externamente.

### <a name="unusual-impersonated-activity-by-user"></a>Atividade representada incomum (por usuário)

Em alguns softwares, há opções para permitir que outros usuários representem outros usuários. Por exemplo, os serviços de email permitem que os usuários autorizem outros usuários a enviar emails em seu nome. Essa atividade é comumente usada por invasores para criar emails de phishing em uma tentativa de extrair informações sobre sua organização. Cloud App Security cria uma linha de base com base no comportamento do usuário e cria uma atividade quando uma atividade de representação incomum é detectada.

**Período de aprendizado**

O estabelecimento do padrão de atividade de um novo usuário requer um período de aprendizado inicial de sete dias durante o qual os alertas não são disparados para novos locais.

**TP**, **B-TP**ou **FP**?

1. **TP**: se for possível confirmar se a atividade não foi executada por um usuário legítimo.

    **Ação recomendada**: suspenda o usuário, marque o usuário como comprometido e Redefina sua senha.
1. **FP** (comportamento incomum): se for possível confirmar se o usuário executou legitimamente as atividades incomuns ou mais atividades do que a linha de base estabelecida.

    **Ação recomendada**: ignorar o alerta.
1. **FP**: se você conseguir confirmar se os aplicativos, como as equipes, foram representados legitimamente o usuário.

    **Ação recomendada**: revise as ações e ignore o alerta, se necessário.

**Entender o escopo da violação**

1. Revise todos os alertas e a atividade do usuário para indicadores adicionais de comprometimento.
1. Examine as atividades de representação para identificar possíveis atividades mal-intencionadas.
1. Examine a configuração de acesso delegado.

## <a name="exfiltration-alerts"></a>Alertas de exfiltração

Esta seção descreve os alertas que indicam que um ator mal-intencionado pode estar tentando roubar dados de sua organização.

### <a name="suspicious-inbox-forwarding"></a>Encaminhamento suspeito da caixa de entrada

Atividades que indicam que um invasor obteve acesso à caixa de entrada de um usuário e criou uma regra suspeita. Regras de manipulação, como encaminhar todos ou emails específicos para outra conta de email, podem ser uma tentativa de exfiltrar informações de sua organização. Cloud App Security perfis seu ambiente e dispara alertas quando regras de manipulação de caixa de entrada suspeitas são detectadas na caixa de entrada de um usuário. Isso pode indicar que a conta do usuário está comprometida.

**TP**, **B-TP**ou **FP**?

1. **TP**: se for possível confirmar que uma regra de encaminhamento de caixa de entrada mal-intencionada foi criada e a conta foi comprometida.

    **Ação recomendada**: suspenda o usuário, redefina sua senha e remova a regra de encaminhamento.
1. **FP**: se você conseguir confirmar que o usuário criou uma regra de encaminhamento para uma conta de email externa nova ou pessoal por motivos legítimos.

    **Ação recomendada**: ignorar o alerta.

**Entender o escopo da violação**

1. Examine todas as atividades do usuário para ver indicadores adicionais de comprometimento, como o alerta, seguido por um alerta de [viagem impossível](#impossible-travel) . Procurar:

    1. Novas regras de encaminhamento de SMTP, da seguinte maneira:
        - Verifique se há nomes de regra de encaminhamento mal-intencionado. Os nomes de regra podem variar de nomes simples, como "encaminhar todos os emails" e "encaminhamento automático" ou nomes enganosos, como um "." mal visível. Os nomes de regra de encaminhamento podem até estar vazios e o destinatário de encaminhamento pode ser uma única conta de email ou uma lista inteira. As regras mal-intencionadas também podem ser ocultadas da interface do usuário. Depois de detectado, você pode usar esta [postagem de blog](https://blogs.msdn.microsoft.com/hkong/2015/02/27/how-to-delete-corrupted-hidden-inbox-rules-from-a-mailbox-using-mfcmapi/) útil sobre como excluir regras ocultas de caixas de correio.
        - Se você detectar uma regra de encaminhamento não reconhecida para um endereço de email interno ou externo desconhecido, poderá assumir que a conta da caixa de entrada foi comprometida.
    1. Novas regras de caixa de entrada, como "excluir tudo", "mover mensagens para outra pasta" ou aquelas com convenções de nomenclatura obscuras, por exemplo, "...".
1. Examine as atividades executadas do endereço IP usado para criar a regra para detectar outros usuários comprometidos.
1. Examine a lista de mensagens encaminhadas usando o rastreamento de mensagens do Exchange Online.

### <a name="unusual-file-download-by-user"></a>Download de arquivo incomum (por usuário)

Atividades que indicam que um usuário realizou um número incomum de downloads de arquivos de uma plataforma de armazenamento em nuvem em comparação com a linha de base aprendida. Isso pode indicar uma tentativa de obter informações sobre a organização. Cloud App Security cria uma linha de base com base no comportamento do usuário e dispara um alerta quando o comportamento incomum é detectado.

**Período de aprendizado**

O estabelecimento do padrão de atividade de um novo usuário requer um período de aprendizado inicial de sete dias durante o qual os alertas não são disparados para novos locais.

**TP**, **B-TP**ou **FP**?

1. **TP**: se for possível confirmar se a atividade não foi executada por um usuário legítimo.

    **Ação recomendada**: suspenda o usuário, marque o usuário como comprometido e Redefina sua senha.
1. **FP** (comportamento incomum): se você puder confirmar que o usuário executou legitimamente mais atividades de download de arquivo do que a linha de base estabelecida.

    **Ação recomendada**: ignorar o alerta.
1. **FP** (sincronização de software): se você for capaz de confirmar se o software, como o onedrive, foi sincronizado com um backup externo que causou o alerta.

    **Ação recomendada**: ignorar o alerta.

**Entender o escopo da violação**

1. Examine as atividades de download e crie uma lista de arquivos baixados.
1. Examine a sensibilidade dos arquivos baixados com o proprietário do recurso e valide o nível de acesso.

### <a name="unusual-file-share-activity-by-user"></a>Atividade de compartilhamento de arquivo incomum (por usuário)

Atividades que indicam que um usuário realizou um número incomum de ações de compartilhamento de arquivos de uma plataforma de armazenamento em nuvem em comparação com a linha de base aprendida. Isso pode indicar uma tentativa de obter informações sobre a organização. Cloud App Security cria uma linha de base com base no comportamento do usuário e dispara um alerta quando o comportamento incomum é detectado.

**Período de aprendizado**

O estabelecimento do padrão de atividade de um novo usuário requer um período de aprendizado inicial de sete dias durante o qual os alertas não são disparados para novos locais.

**TP**, **B-TP**ou **FP**?

1. **TP**: se for possível confirmar se a atividade não foi executada por um usuário legítimo.

    **Ação recomendada**: suspenda o usuário, marque o usuário como comprometido e Redefina sua senha.
1. **FP** (comportamento incomum): se você for capaz de confirmar se o usuário executou legitimamente mais atividades de compartilhamento de arquivos do que a linha de base estabelecida.

    **Ação recomendada**: ignorar o alerta.

**Entender o escopo da violação**

1. Examine as atividades de compartilhamento e crie uma lista de arquivos compartilhados.
1. Examine a sensibilidade dos arquivos compartilhados com o proprietário do recurso e valide o nível de acesso.
1. Crie uma política de arquivo para documentos semelhantes para detectar o compartilhamento futuro de arquivos confidenciais.

## <a name="impact-alerts"></a>Alertas de impacto

Esta seção descreve os alertas que indicam que um ator mal-intencionado pode estar tentando manipular, interromper ou destruir seus sistemas e dados em sua organização.

### <a name="multiple-delete-vm-activities"></a>Várias atividades de exclusão de VM

Atividades em uma única sessão que indica que um usuário realizou um número incomum de exclusões de VM em comparação com a linha de base aprendida. Várias exclusões de VM podem indicar uma tentativa de interromper ou destruir um ambiente. No entanto, há muitos cenários normais em que as VMs são excluídas.

**TP**, **B-TP**ou **FP**?

Para melhorar a precisão e o alerta somente quando houver uma indicação forte de uma violação, essa detecção estabelecerá uma linha de base em cada ambiente na organização para reduzir os incidentes **de B-TP** e somente alertará quando o comportamento incomum for detectado.

**Período de aprendizado**

O estabelecimento do padrão de atividade de um novo usuário requer um período de aprendizado inicial de sete dias durante o qual os alertas não são disparados para novos locais.

- **TP**: se for possível confirmar se as exclusões não foram autorizadas.

    **Ação recomendada**: suspenda o usuário, redefina sua senha e verifique todos os dispositivos em busca de ameaças mal-intencionadas. Examine todas as atividades do usuário para outros indicadores de comprometimento e explore o escopo do impacto.
- **B-TP**: se depois de sua investigação, você poderá confirmar se o administrador foi autorizado a executar essas atividades de exclusão.

    **Ação recomendada**: ignorar o alerta.

**Entender o escopo da violação**

1. Contate o usuário e confirme a atividade.
1. Examine todas as atividades do usuário para ver indicadores adicionais de comprometimento, como o alerta, seguido de um dos seguintes alertas: [viagem impossível](#impossible-travel), [atividade de endereço IP anônimo](#activity-from-anonymous-ip-address)ou [atividade de um país infrequente](#activity-from-infrequent-country).

### <a name="ransomware-activity"></a>Atividade de ransomware

O ransomware é um cyberattack no qual um invasor bloqueia as vítimas de seus dispositivos ou impede que eles acessem seus arquivos até que a vítima pague um resgate. O ransomware pode ser distribuído por um arquivo compartilhado mal-intencionado ou pela rede comprometida. Cloud App Security usa conhecimento de pesquisa de segurança, inteligência contra ameaças e padrões de comportamento conhecidos para identificar a atividade de ransomware. Por exemplo, uma alta taxa de carregamentos de arquivo ou exclusões de arquivos pode representar um processo de criptografia comum entre operações de ransomware.

Essa detecção estabelece uma linha de base dos padrões de trabalho normais de cada usuário em sua organização, como quando o usuário acessa a nuvem e o que normalmente faz na nuvem.

As políticas de detecção de ameaças automatizadas do Cloud App Security começam a ser executadas em segundo plano a partir do momento em que você se conecta. Usando nossa experiência de pesquisa de segurança para identificar os padrões comportamentais que refletem a atividade de ransomware em nossa organização, Cloud App Security fornece cobertura abrangente contra ataques sofisticados de ransomware.

**Período de aprendizado**

O estabelecimento do padrão de atividade de um novo usuário requer um período de aprendizado inicial de sete dias durante o qual os alertas não são disparados para novos locais.

**TP**, **B-TP**ou **FP**?

1. **TP**: se for possível confirmar se a atividade não foi executada pelo usuário.

    **Ação recomendada**: suspenda o usuário, marque o usuário como comprometido e Redefina sua senha.
1. **FP** (comportamento incomum): o usuário executou legitimamente várias atividades de exclusão e carregamento de arquivos semelhantes em um curto período de tempo.

    **Ação recomendada**: depois de examinar o log de atividades e confirmar que as extensões de arquivo não são suspeitas, ignore o alerta.
1. **FP** (extensão de arquivo de ransomware comum): se for possível confirmar se as extensões dos arquivos afetados são uma correspondência para uma extensão de ransomware conhecida.

    **Ação recomendada**: contate o usuário e confirme se os arquivos estão seguros e, em seguida, ignore o alerta.

**Entender o escopo da violação**

1. Examine o log de atividades para obter outros indicadores de comprometimento, como o download em massa ou exclusão em massa de arquivos.
1. Se você estiver usando a proteção avançada contra ameaças do Microsoft defender, examine os alertas do computador do usuário para ver se arquivos mal-intencionados foram detectados.
1. Pesquise o log de atividades para atividades de compartilhamento e carregamento de arquivos mal-intencionados.

### <a name="unusual-file-deletion-activity-by-user"></a>Atividade de exclusão de arquivo incomum (por usuário)

Atividades que indicam que um usuário realizou uma atividade de exclusão de arquivo incomum em comparação com a linha de base aprendida. Isso pode indicar o ataque de ransomware. Por exemplo, um invasor pode criptografar os arquivos de um usuário e excluir todos os originais, deixando apenas as versões criptografadas que podem ser usadas para forçar a vítima de pagar um resgate. Cloud App Security cria uma linha de base com base no comportamento normal do usuário e dispara um alerta quando o comportamento incomum é detectado.

**Período de aprendizado**

O estabelecimento do padrão de atividade de um novo usuário requer um período de aprendizado inicial de sete dias durante o qual os alertas não são disparados para novos locais.

**TP**, **B-TP**ou **FP**?

1. **TP**: se for possível confirmar se a atividade não foi executada por um usuário legítimo.

    **Ação recomendada**: suspenda o usuário, marque o usuário como comprometido e Redefina sua senha.
1. **FP**: se você conseguir confirmar que o usuário executou legitimamente mais atividades de exclusão de arquivos do que a linha de base estabelecida.

    **Ação recomendada**: ignorar o alerta.

**Entender o escopo da violação**

1. Examine as atividades de exclusão e crie uma lista de arquivos excluídos. Se necessário, recupere os arquivos excluídos.
1. Opcionalmente, crie um guia estratégico usando a automatização de energia para contatar os usuários e seus gerentes para verificar a atividade.

## <a name="see-also"></a>Veja também

> [!div class="nextstepaction"]
> [Investigar usuários arriscados](tutorial-ueba.md)

---
title: Controlar o uso do aplicativo de nuvem criando políticas-Cloud App Security | Microsoft Docs
description: Este artigo fornece informações sobre como as políticas são usadas e configuradas para controlar o uso do aplicativo de nuvem.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 09/26/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: e4675430b45e92579cd4c692247c5a481bad233e
ms.sourcegitcommit: 4f3883a9e85d0aaf2802b10433b221c3f1838d88
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79285610"
---
# <a name="control-cloud-apps-with-policies"></a>Controlar aplicativos de nuvem com políticas

*Aplica-se a: Microsoft Cloud App Security*

As políticas permitem que você defina como deseja que os usuários se comportem na nuvem. Eles permitem que você detecte comportamentos arriscados, violações ou pontos de dados suspeitos e atividades em seu ambiente de nuvem. Se necessário, você pode integrar fluxos de trabalho de correção para obter uma mitigação de risco completa. Há vários tipos de políticas que se correlacionam aos diferentes tipos de informações que você deseja reunir sobre seu ambiente de nuvem e os tipos de ações de correção que talvez você queira executar.

Por exemplo, se houver uma ameaça de violação de dados que você deseja colocar em quarentena, você precisará de um tipo diferente de política em vigor do que se quiser impedir que um aplicativo de nuvem arriscado seja usado pela sua organização.

## <a name="policy-types"></a>Tipos de política

Ao examinar a página de **política** , as várias políticas e modelos podem ser diferenciados pelo tipo e ícone para ver quais políticas estão disponíveis. As políticas disponíveis dependem da fonte de dados e do que você habilitou em Cloud App Security para sua organização. Por exemplo, se você carregou Cloud Discovery logs, as políticas relacionadas a Cloud Discovery são exibidas.

Os seguintes tipos de políticas podem ser criados:

|Ícone de tipo de política|Tipo de política|Use objetos de|
|-----|-----------------|---------|
|![ícone de política de acesso](media/proxy-policy.png)|Política de acesso|As políticas de acesso fornecem monitoramento em tempo real e controle sobre os logons de usuário para seus aplicativos de nuvem.|
|![ícone de política de atividade](media/activity_policy.png)|Política de atividade|As políticas de atividade permitem impor uma ampla variedade de processos automatizados usando as APIs do provedor de aplicativos. Essas políticas permitem que você monitore atividades específicas executadas por vários usuários ou siga taxas altas inesperadamente de um determinado tipo de atividade.|
|![ícone da política de detecção de anomalias](media/anomaly_detection_policy.png)|Política de detecção de anomalias|As políticas de detecção de anomalias permitem que você procure atividades incomuns em sua nuvem. A detecção é baseada nos fatores de risco definidos para alertá-lo quando algo acontecer diferente da linha de base da sua organização ou da atividade regular do usuário.|
|![ícone de política de descoberta de nuvem](media/discovery_policy.png)|Política de descoberta de aplicativo|As políticas de descoberta de aplicativo permitem que você defina alertas que o notificam quando novos aplicativos são detectados em sua organização.|
|![ícone da política de detecção de anomalias](media/anomaly_detection_policy.png)|Política de detecção de anomalias do Cloud Discovery|Cloud Discovery as políticas de detecção de anomalias examinam os logs que você usa para descobrir aplicativos de nuvem e Pesquisar ocorrências incomuns. Por exemplo, quando um usuário que nunca usou o Dropbox antes de repentinamente carrega 600 GB para o Dropbox ou quando há muito mais transações do que o normal em um aplicativo específico.|
|![ícone de política de arquivo](media/file_policy.png)|Política de arquivos|As políticas de arquivo permitem que você examine seus aplicativos de nuvem em busca de arquivos ou tipos de arquivos especificados (compartilhados, compartilhados com domínios externos), dados (informações proprietárias, dados pessoais, informações de cartão de crédito e outros tipos de dados) e aplique ações de governança aos arquivos ( as ações de governança são específicas do aplicativo de nuvem).|
|![ícone de política de sessão](media/proxy-policy.png)|Política de sessão|As políticas de sessão fornecem monitoramento em tempo real e controle sobre a atividade do usuário em seus aplicativos de nuvem.|

## <a name="identifying-risk"></a>Identificação de risco

Cloud App Security ajuda a reduzir diferentes riscos na nuvem. Você pode configurar qualquer política e alerta a ser associado a um dos seguintes riscos:

- **Controle de acesso:** Quem acessa o quê?

    Monitore continuamente o comportamento e detecte atividades anormais, incluindo ataques internos e insider de alto risco e aplique uma política para alertar, bloquear ou exigir verificação de identidade para qualquer aplicativo ou ação específica em um aplicativo. Habilita políticas de controle de acesso móvel e locais com base em usuário, dispositivo e geografia com bloqueio e exibição granular, editar e bloquear. Detectar eventos de logon suspeitos, incluindo falhas de autenticação multifator, falhas de logon de conta desabilitadas e eventos de representação.

- **Conformidade:** Seus requisitos de conformidade foram violados?

    Catalogar e identificar dados confidenciais ou regulamentados, incluindo permissões de compartilhamento para cada arquivo, armazenados em serviços de sincronização de arquivos para garantir a conformidade com regulamentos como PCI, SOX e HIPAA

- **Controle de configuração:** As alterações não autorizadas estão sendo feitas à sua configuração?

    Monitore as alterações de configuração, incluindo a manipulação de configuração remota.

- **Cloud Discovery:** Novos aplicativos estão sendo usados em sua organização? Você tem um problema em que os aplicativos de ti de sombra estão sendo usados que você não conhece?

    Classifique o risco geral de cada aplicativo em nuvem com base em certificações regulatórias e do setor e práticas recomendadas. Permite monitorar o número de usuários, atividades, volume de tráfego e horas de uso típicas para cada aplicativo em nuvem.

- **DLP:** Os arquivos proprietários são compartilhados publicamente? Você precisa colocar arquivos em quarentena?

    A integração de DLP local fornece a integração e a correção de loop fechado com soluções de DLP locais existentes.

- **Contas com privilégios:** Você precisa monitorar contas de administrador?

    Monitoramento de atividades em tempo real e relatórios de usuários e administradores com privilégios.

- **Controle de compartilhamento:** Como os dados são compartilhados em seu ambiente de nuvem?

    Inspecione o conteúdo de arquivos e conteúdo na nuvem e imponha políticas de compartilhamento internas e externas. Monitore a colaboração e imponha políticas de compartilhamento, como impedir que arquivos sejam compartilhados fora da sua organização.

- **Detecção de ameaças:** Há atividades suspeitas ameaçando seu ambiente de nuvem?

    Receba notificações em tempo real para qualquer violação de política ou limite de atividade por email ou mensagem de texto. Aplicando algoritmos de aprendizado de máquina, o Cloud App Security permite detectar um comportamento que pode indicar que um usuário está usando dados indesejadamente.

## <a name="how-to-control-risk"></a>Como controlar o risco

Siga este processo para controlar o risco com as políticas:

1. Crie uma política a partir de um modelo ou de uma consulta.

1. Ajuste a política para obter os resultados esperados.

1. Adicione ações automatizadas para responder e corrigir riscos automaticamente.

### <a name="create-a-policy"></a>Criar uma política

Você pode usar os modelos de política do Cloud App Security como uma base para todas as suas políticas ou criar políticas de uma consulta.

Os modelos de política ajudam a definir os filtros e as configurações corretas necessárias para detectar eventos específicos de interesse em seu ambiente. Os modelos incluem políticas de todos os tipos e podem ser aplicados a vários serviços.

Para criar uma política de **modelos de política**, execute as seguintes etapas:

1. No console do, clique em **controle** seguido por **modelos**.

    ![Criar a política a partir de um modelo](media/create-policy-from-template.png)

1. Clique na **+** na extrema direita da linha do modelo que você deseja usar. Uma página Criar política é aberta, com a configuração predefinida do modelo.

1. Modifique o modelo conforme necessário para sua política personalizada. Cada propriedade e campo dessa nova política baseada em modelo podem ser modificados de acordo com suas necessidades.
   > [!NOTE]
   > Ao usar os filtros de política, o **contém** pesquisas somente por palavras completas – separadas por comas, pontos, espaços ou sublinhados. Por exemplo, se você Pesquisar **malware** ou **vírus**, ele encontrará virus_malware_file. exe, mas não encontrará o malwarevirusfile. exe. Se você Pesquisar *malware. exe*, encontrará todos os arquivos com malware ou exe em seu nome de arquivo, enquanto se você procurar por **"malware. exe"** (com as aspas), encontrará apenas os arquivos que contêm exatamente "malware. exe".  
**Equals** pesquisa apenas a cadeia de caracteres completa, por exemplo, se você pesquisar por *malware. exe* , ele encontra malware. exe, mas não malware. exe. txt.

1. Depois de criar a nova política baseada em modelo, um link para a nova política aparecerá na coluna **políticas vinculadas** na tabela modelo de política ao lado do modelo do qual a política foi criada.
    Você pode criar quantas políticas desejar de cada modelo e todas elas serão vinculadas ao modelo original. A vinculação permite que você acompanhe todas as políticas criadas usando o mesmo modelo.

Como alternativa, você pode **criar uma política durante a investigação**. Se você estiver investigando o **log de atividades**, os **arquivos** ou **as contas**, e fizer uma busca detalhada para pesquisar algo específico, a qualquer momento, você poderá criar uma nova política com base nos resultados de sua investigação.

Por exemplo, se você estiver olhando para o **log de atividades**e vir uma atividade de administrador fora dos endereços IP do seu escritório.

Para criar uma política com base nos resultados da investigação, execute as seguintes etapas:

1. No console do, clique em **investigar** seguido por **log de atividades**, **arquivos**ou **contas**.

1. Use os filtros na parte superior da página para limitar os resultados da pesquisa à área suspeita. Por exemplo, na página log de atividades, clique em **tipo de atividade** e selecione **gravar administradores** em operação do Azure. Em seguida, em **endereço IP**, selecione **categoria** e defina o valor como não incluir as categorias de endereço IP que você criou para seus domínios reconhecidos, como seus endereços IP de administrador, corporativo e VPN.

    ![Criar arquivo de investigação](media/create-file-from-investigation.png)

1. No canto superior direito do console, clique em **nova política da pesquisa**.

    ![Nova política do botão Pesquisar](media/new-policy-from-search-button.png)

1. Uma página Criar política é aberta, contendo os filtros que você usou em sua investigação.

1. Modifique o modelo conforme necessário para sua política personalizada. Cada propriedade e campo dessa nova política baseada em investigação pode ser modificado de acordo com suas necessidades.

    > [!NOTE]
    > Ao usar os filtros de política, o **contém** pesquisas somente por palavras completas – separadas por comas, pontos, espaços ou sublinhados. Por exemplo, se você Pesquisar **malware** ou **vírus**, ele encontrará virus_malware_file. exe, mas não encontrará o malwarevirusfile. exe.  
**Equals** pesquisa apenas a cadeia de caracteres completa, por exemplo, se você pesquisar por **malware. exe** , ele encontra malware. exe, mas não malware. exe. txt.

    ![criar política de atividade de investigação](media/create-activity-policy-from-investigation.png)

    > [!NOTE]
    > Para obter mais informações sobre como definir os campos de política, consulte a documentação da política correspondente:
    >
    > [Políticas de atividade do usuário](user-activity-policies.md)
    >
    > [Políticas de proteção de dados](data-protection-policies.md)
    >
    > [Políticas do Cloud Discovery](cloud-discovery-policies.md)

### <a name="add-automated-actions-to-respond-and-remediate-risks-automatically"></a>Adicionar ações automatizadas para responder e corrigir riscos automaticamente

Para obter uma lista de ações de governança disponíveis por aplicativo, consulte os [aplicativos que regem a conexão](governance-actions.md).

Você também pode definir a política para enviar um alerta por email ou mensagem de texto quando as correspondências forem detectadas.

Para definir suas preferências de notificação, é necessário [Personalizar o portal](general-setup.md)

> [!NOTE]
> O número máximo de alertas enviados por mensagem de texto é 10 por número de telefone por dia. O dia é calculado de acordo com o fuso horário UTC.

## <a name="enable-and-disable-policies"></a>Habilitar e desabilitar políticas

Depois de criar uma política, você pode habilitá-la ou desabilitá-la. Desabilitar evita a necessidade de excluir uma política depois de criá-la para interrompê-la. Em vez disso, se por algum motivo você quiser interromper a política, desabilite-a até optar por habilitá-la novamente.

- Para habilitar uma política, na página **política** , clique nos três pontos no final da linha da política que você deseja habilitar. Selecione **habilitar**.

    ![Habilitar política](media/enable-policy.png)

- Para desabilitar uma política, na página **política** , clique nos três pontos no final da linha da política que você deseja desabilitar. Selecione **desabilitar**.

    ![Desabilitar política](media/disable-policy.png)

Por padrão, depois de criar uma nova política, ela é habilitada.

## <a name="policies-overview-report"></a>Relatório de visão geral de políticas

Cloud App Security permite exportar um relatório de visão geral de políticas mostrando métricas de alerta agregadas por política para ajudá-lo a monitorar, compreender e personalizar suas políticas para proteger melhor sua organização.

Para exportar um log, execute as seguintes etapas:

1. Na página **políticas** , clique no botão **Exportar** .

1. Especifique o intervalo de tempo necessário.

1. Clique em **Exportar**. Esse processo pode levar algum tempo.

Para baixar o relatório exportado:

1. Depois que o relatório estiver pronto, vá para **configurações** e, em seguida, **relatórios exportados**.

1. Na tabela, selecione o relatório relevante no **relatório visão geral** da lista de políticas e clique em baixar.

    ![botão baixar](media/download-button.png)

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]

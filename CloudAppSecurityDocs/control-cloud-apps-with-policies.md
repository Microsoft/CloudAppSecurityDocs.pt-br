---
title: Controlar o uso do aplicativo de nuvem criando políticas
description: Este artigo fornece informações sobre como as políticas são usadas e configuradas para controlar o uso de aplicativos na nuvem.
ms.date: 09/26/2019
ms.topic: how-to
ms.openlocfilehash: 695737038f0c45e366581c0262550b4c769039a5
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96312284"
---
# <a name="control-cloud-apps-with-policies"></a>Controlar aplicativos de nuvem com políticas

[!INCLUDE [Banner for top of topics](includes/banner.md)]

As políticas permitem que você defina a maneira como deseja que os usuários se comportem na nuvem. Elas permitem que você detecte comportamento arriscado, violações ou atividades e pontos de dados suspeitos em seu ambiente de nuvem. Se necessário, é possível integrar fluxos de trabalho de correção para atingir a mitigação de risco completa. Existem vários tipos de políticas que se correlacionam com diferentes tipos de informações que você deseja reunir sobre seu ambiente de nuvem e os tipos de ações de correção que deseja executar.

Por exemplo, se você quiser colocar uma ameaça de violação de dados em quarentena, precisará ter um tipo de política em vigor diferente da necessária para bloquear o uso de um aplicativo de nuvem arriscado por sua organização.

## <a name="policy-types"></a>Tipos de política

Quando você observa a página **Política**, as várias políticas e modelos podem ser diferenciados pelo tipo e ícone para ver quais políticas estão disponíveis. As políticas disponíveis dependem da fonte de dados e o que você tiver habilitado no Cloud App Security para sua organização. Por exemplo, se você carregar os logs do Cloud Discovery, as políticas relacionadas ao Cloud Discovery serão exibidas.

Os seguintes tipos de políticas podem ser criados:

|Ícone Tipo de política|Tipo de política|Usar|
|-----|-----------------|---------|
|![ícone de política de acesso](media/proxy-policy.png)|Política de acesso|Políticas de acesso fornecem monitoramento em tempo real e controle sobre logons de usuário para seus aplicativos de nuvem.|
|![ícone de política de atividade](media/activity_policy.png)|Política de atividade|As políticas de atividade permitem impor uma ampla variedade de processos automatizados usando as APIs do provedor de aplicativos. Essas políticas permitem que você monitore atividades específicas realizadas por vários usuários ou siga altas taxas inesperadas de um determinado tipo de atividade.|
|![ícone de política de detecção de anomalias](media/anomaly_detection_policy.png)|Política de detecção de anomalias|As políticas de detecção de anomalias permitem que você procure atividades incomuns na sua nuvem. A detecção baseia-se nos fatores de risco que você define para alertá-lo quando algo diferente da linha de base de sua organização ou da atividade regular do usuário acontece.|
|![ícone de política do cloud discovery](media/discovery_policy.png)|Política de descoberta de aplicativo|As políticas de descoberta de aplicativo permitem que você defina alertas que notificam quando novos aplicativos são detectados na sua organização.|
|![ícone de política de detecção de anomalias](media/anomaly_detection_policy.png)|Política de detecção de anomalias do Cloud Discovery|As políticas de detecção de anomalias do Cloud Discovery analisam os logs usados para descobrir aplicativos de nuvem e pesquisa ocorrências incomuns. Por exemplo, quando um usuário que nunca usou o Dropbox antes de repente carrega 600 GB para o Dropbox ou quando há muito mais transações que o normal em um aplicativo específico.|
|![ícone de política de arquivos](media/file_policy.png)|Política de arquivo|As políticas de arquivos permitem que você examine seus aplicativos de nuvem quanto a tipos de arquivo ou arquivos especificados (compartilhados, compartilhados com domínios externos), dados (informações proprietárias, dados pessoais, informações de cartão de crédito e outros tipos de dados) e aplique ações de governança aos arquivos (as ações de governança são específicas do aplicativo de nuvem).|
|![Ícone de política de sessão](media/proxy-policy.png)|Política de sessão|As políticas de sessão fornecem monitoramento em tempo real e controle sobre a atividade do usuário em seus aplicativos de nuvem.|

## <a name="identifying-risk"></a>Identificando o risco

O Cloud App Security ajuda a mitigar diferentes riscos na nuvem. Você pode configurar qualquer política e alerta a ser associado a um dos seguintes riscos:

- **Controle de acesso:** quem acessa o que de onde?

    Monitore continuamente o comportamento e detecte atividades anômalas, incluindo ataques internos e externos de alto risco e aplique uma política para alertar, bloquear ou exigir a verificação de identidade para qualquer aplicativo ou ação específica dentro de um aplicativo. Habilite políticas de controle de acesso móvel e local com base no usuário, dispositivo e geografia com bloqueio não refinado e exibição, edição e bloqueio granulares. Detecte eventos de logon suspeitos, incluindo falhas de autenticação multifator, falhas de logon de conta desabilitada e eventos de representação.

- **Conformidade:** seus requisitos de conformidade estão violados?

    Catalogue e identifique dados controlados ou confidenciais, incluindo permissões de compartilhamento para cada arquivo armazenado nos serviços de sincronização de arquivos para garantir a conformidade com regulamentações como PCI, SOX e HIPAA

- **Controle de configuração:** estão sendo feitas alterações não autorizadas nas suas configurações?

    Monitore alterações de configuração, incluindo manipulação de configuração remota.

- **Cloud Discovery:** aplicativos novos estão sendo usados em sua organização? Você tem um problema de aplicativos de TI Invisível sendo usados sobre os quais não tem conhecimento?

    Classifique o risco geral para cada aplicativo de nuvem com base nas normas e certificações do setor e melhores práticas. Permite que você monitore o número de usuários, as atividades, o volume de tráfego e as horas de uso típico para cada aplicativo na nuvem.

- **DLP:** arquivos proprietários estão sendo compartilhados publicamente? Você precisa colocar arquivos em quarentena?

    A integração de DLP local fornece a correção de loop fechado e a integração com as soluções de DLP locais existentes.

- **Contas com privilégios:** você precisa monitorar contas de administrador?

    Monitoramento e relatórios de atividades de administradores e usuários com privilégios em tempo real.

- **Controle de compartilhamento:** como os dados estão sendo compartilhados em seu ambiente de nuvem?

    Inspecione o conteúdo de arquivos e na nuvem e imponha políticas de compartilhamento internas e externas. Monitore a colaboração e imponha políticas de compartilhamento, como bloquear o compartilhamento de arquivos fora da sua organização.

- **Detecção de ameaças:** há atividades suspeitas ameaçando seu ambiente de nuvem?

    Receba notificações em tempo real para qualquer limite de atividade ou violação de política por email ou mensagem de texto. Ao aplicar algoritmos de aprendizado de máquina, o Cloud App Security permite que você detecte o comportamento que poderia indicar que um usuário está usando os dados de maneira indevida.

## <a name="how-to-control-risk"></a>Como controlar o risco

Siga este processo para controlar o risco com políticas:

1. Crie uma política de um modelo ou uma consulta.

1. Ajuste a política para obter os resultados esperados.

1. Adicione ações automatizadas para responder e corrigir riscos automaticamente.

### <a name="create-a-policy"></a>Criar uma política

Você pode usar os modelos de política do Cloud App Security como uma base para todas as suas políticas ou criar políticas de uma consulta.

Modelos de política ajudam você a definir os filtros corretos e as configurações necessárias para detectar eventos específicos de interesse em seu ambiente. Os modelos incluem políticas de todos os tipos e podem ser aplicados a vários serviços.

Para criar uma política de **Modelo de política**, execute estas etapas:

1. No console, clique em **Controlar** seguido por **Modelos**.

    ![Criar a política com base em um modelo](media/create-policy-from-template.png)

1. Clique na **+** extrema direita da linha do modelo que você deseja usar. Uma página de criação de política é aberta contendo a configuração predefinida do modelo.

1. Modifique o modelo conforme necessário para sua política personalizada. Todas as propriedades e campos dessa política baseada em modelo podem ser modificados de acordo com suas necessidades.
   > [!NOTE]
   > Ao usar os filtros de política, **contém** pesquisa somente palavras inteiras: separadas por vírgulas, pontos, espaços ou sublinhados. Por exemplo, se você pesquisar **malware** ou **vírus**, ele localizará virus_malware_file.exe, mas não localizará malwarevirusfile.exe. Se você Pesquisar *malware.exe*, encontrará todos os arquivos com malware ou exe em seu nome de arquivo, enquanto se procurar por **"malware.exe"** (com as aspas), você encontrará apenas os arquivos que contêm exatamente "malware.exe".  
**É igual a** pesquisa apenas a cadeia de caracteres completa, por exemplo, se você pesquisar *malware.exe*, ele localizará malware.exe, mas não malware.exe.txt.

1. Depois de criar a nova política baseada em modelo, um link para a nova política aparece na coluna **Políticas vinculadas** na tabela de modelos de política ao lado do modelo por meio do qual a política foi criada.
    É possível criar quantas políticas você desejar de cada modelo e todas elas estarão vinculadas ao modelo original. A vinculação permite que você acompanhe todas as políticas criadas usando o mesmo modelo.

Como alternativa, você pode **criar uma política durante a investigação**. Se você estiver investigando o **Log de atividades**, os **Arquivos** ou as **Contas** e fizer uma busca detalhada para pesquisar algo específico, a qualquer momento você poderá criar uma nova política com base nos resultados da sua investigação.

Por exemplo, se você estiver olhando para o **log de atividades** e vir uma atividade de administrador fora dos endereços IP do seu escritório.

Para criar uma política com base nos resultados da investigação, siga estas etapas:

1. No console, clique em **Investigar** seguido de **Log de atividades**, **Arquivos** ou **Contas**.

1. Use os filtros na parte superior da página para limitar os resultados da pesquisa à área suspeita. Por exemplo, na página do Log de atividades, clique em **Tipo de atividade** e selecione **Gravar administradores** na operação do Azure. Em seguida, em **Endereço IP**, selecione **Categoria** e defina o valor para não incluir as categorias de endereço IP que você criou para seus domínios reconhecidos, como os endereços IP de administração, corporativos e de VPN.

    ![Criar arquivo com base na investigação](media/create-file-from-investigation.png)

1. No canto superior direito do console, clique em **nova política da pesquisa**.

    ![Botão Nova política da pesquisa](media/new-policy-from-search-button.png)

1. Uma página de criação de política é aberta, contendo os filtros usados na sua investigação.

1. Modifique o modelo conforme necessário para sua política personalizada. Todas as propriedades e campos dessa política baseada em investigação podem ser modificados de acordo com suas necessidades.

    > [!NOTE]
    > Ao usar os filtros de política, **contém** pesquisa somente palavras inteiras: separadas por vírgulas, pontos, espaços ou sublinhados. Por exemplo, se você pesquisar **malware** ou **vírus**, ele localizará virus_malware_file.exe, mas não localizará malwarevirusfile.exe.  
**É igual a** pesquisa apenas a cadeia de caracteres completa, por exemplo, se você pesquisar **malware.exe**, ele localizará malware.exe, mas não malware.exe.txt.

    ![criar política de atividade com base na investigação](media/create-activity-policy-from-investigation.png)

    > [!NOTE]
    > Para obter mais informações sobre como definir campos de política, consulte a documentação da política correspondente:
    >
    > [Políticas de atividade de usuário](user-activity-policies.md)
    >
    > [Políticas de proteção de dados](data-protection-policies.md)
    >
    > [Políticas do Cloud Discovery](cloud-discovery-policies.md)

### <a name="add-automated-actions-to-respond-and-remediate-risks-automatically"></a>Adicionar ações automatizadas para responder e corrigir riscos automaticamente

Para obter uma lista de ações de governança disponíveis por aplicativo, consulte [Controlando aplicativos conectados](governance-actions.md).

Você também pode definir a política para enviar um alerta por email ou mensagem de texto quando correspondências são detectadas.

Para definir suas preferências de notificação, vá até [Personalizar o portal](general-setup.md)

> [!NOTE]
> O número máximo de alertas enviados por meio de mensagem de texto é 10 por número de telefone por dia. O dia é calculado de acordo com o fuso horário UTC.

## <a name="enable-and-disable-policies"></a>Habilitar e desabilitar políticas

Depois de criar uma política, é possível habilitá-la ou desabilitá-la. Desabilitar evita a necessidade de excluir uma política depois de você criá-la para interrompê-la. Em vez disso, se por alguma razão você desejar interromper a política, desabilite-a até que queira habilitá-la novamente.

- Para habilitar uma política, na página **Política**, clique nas reticências no final da linha da política que você deseja habilitar. Selecione **Habilitar**.

    ![Habilitar política](media/enable-policy.png)

- Para desabilitar uma política, na página **Política**, clique nas reticências no final da linha da política que você deseja desabilitar. Selecione **Desabilitar**.

    ![Desabilitar política](media/disable-policy.png)

Por padrão, depois de criar uma política, ela será habilitada.

## <a name="policies-overview-report"></a>Relatório de visão geral de políticas

Cloud App Security permite exportar um relatório de visão geral de políticas mostrando métricas de alerta agregadas por política para ajudá-lo a monitorar, compreender e personalizar suas políticas para proteger melhor sua organização.

Para exportar um log, execute as seguintes etapas:

1. Na página **políticas** , clique no botão **Exportar** .

1. Especifique o intervalo de tempo necessário.

1. Clique em **Exportar**. Esse processo pode demorar algum tempo.

Para baixar o relatório exportado:

1. Depois que o relatório estiver pronto, vá para **Configurações** e, em seguida **Relatórios exportados**.

1. Na tabela, selecione o relatório relevante no **relatório visão geral** da lista de políticas e clique em baixar.

    ![botão download](media/download-button.png)

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]

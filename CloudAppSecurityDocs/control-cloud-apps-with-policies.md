---
title: Controlar o uso do aplicativo de nuvem criando políticas – Cloud App Security | Microsoft Docs
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
ms.sourcegitcommit: 445a7c208455e6ce2c4e13b028c811f4c3486290
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78342093"
---
# <a name="control-cloud-apps-with-policies"></a>Controlar aplicativos de nuvem com políticas

*Aplica-se a: Microsoft Cloud App Security*

As políticas permitem que você defina como deseja que os usuários se comportem na nuvem. Elas permitem que você detecte um comportamento de risco, violações ou atividades e pontos de dados suspeitos em seu ambiente de nuvem. Se necessário, você pode integrar fluxos de trabalho de correção para obter uma mitigação de risco completa. Há vários tipos de políticas que se correlacionam aos diferentes tipos de informações que você deseja reunir sobre seu ambiente de nuvem e os tipos de ações de correção que talvez você queira executar.

Por exemplo, se houver uma ameaça de violação de dados que você desejar colocar em quarentena, você precisará implementar um tipo diferente de política do que se desejar impedir que um aplicativo de nuvem de risco seja usado pela sua organização.

## <a name="policy-types"></a>Tipos de política

Ao examinar a página **Política**, as várias políticas e modelos podem ser diferenciados por tipo e ícone para ver quais políticas estão disponíveis. As políticas disponíveis dependem da fonte de dados e do que você habilitou no Cloud App Security para sua organização. Por exemplo, se você carregou logs do Cloud Discovery, as políticas relacionadas ao Cloud Discovery são exibidas.

Os seguintes tipos de políticas podem ser criados:

|Ícone do tipo de política|Tipo de política|Uso|
|-----|-----------------|---------|
|![ícone da política de acesso](media/proxy-policy.png)|Política de acesso|As políticas de acesso fornecem monitoramento em tempo real e controle sobre logons do usuário para seus aplicativos de nuvem.|
|![ícone da política de atividade](media/activity_policy.png)|Política de atividade|As políticas de atividade permitem impor uma ampla variedade de processos automatizados usando as APIs do provedor de aplicativos. Essas políticas permitem monitorar atividades específicas executadas por vários usuários ou seguem taxas inesperadamente altas de um tipo determinado de atividade.|
|![Ícone da política de detecção de anomalias](media/anomaly_detection_policy.png)|Política de detecção de anomalias|As políticas de detecção de anomalias permitem que você procure atividades incomuns em sua nuvem. A detecção é baseada nos fatores de risco definidos para alertar você quando algo acontecer diferente da linha de base da sua organização ou da atividade regular do usuário.|
|![ícone da política do cloud discovery](media/discovery_policy.png)|Política de descoberta de aplicativos|As políticas de descoberta de aplicativo permitem que você defina alertas que notifiquem você quando novos aplicativos são detectados em sua organização.|
|![Ícone da política de detecção de anomalias](media/anomaly_detection_policy.png)|Política de detecção de anomalias do Cloud Discovery|As políticas de detecção de anomalias do Cloud Discovery examinam os logs que você usa para descobrir aplicativos de nuvem e pesquisar ocorrências incomuns. Por exemplo, quando um usuário que nunca usou o Dropbox antes carrega repentinamente 600 GB para o Dropbox ou quando há muito mais transações do que o normal em um aplicativo específico.|
|![ícone da política de arquivos](media/file_policy.png)|Política de arquivos|As políticas de arquivos permitem que você examine seus aplicativos de nuvem quanto a tipos de arquivo ou arquivos especificados (compartilhados, compartilhados com domínios externos), dados (informações proprietárias, dados pessoais, informações de cartão de crédito e outros tipos de dados) e aplique ações de governança aos arquivos (as ações de governança são específicas do aplicativo de nuvem).|
|![ícone da política de sessão](media/proxy-policy.png)|Política de sessão|As políticas de sessão fornecem monitoramento em tempo real e controle sobre a atividade do usuário em seus aplicativos de nuvem.|

## <a name="identifying-risk"></a>Identificar o risco

O Cloud App Security ajuda a migrar diferentes riscos na nuvem. Você pode configurar qualquer política e alerta para serem associados a um dos seguintes riscos:

- **Controle de acesso:** Quem acessa o que de onde?

    Monitore continuamente o comportamento e detecte atividades anômalas, incluindo ataques internos e externos de alto risco e aplique uma política para alertar, bloquear ou exigir a verificação de identidade para qualquer aplicativo ou ação específica dentro de um aplicativo. Habilita políticas de controle de acesso móvel e local com base no usuário, dispositivo e geografia com bloqueio não refinado e exibição, edição e bloqueio granulares. Detecte eventos de logon suspeitos, incluindo falhas de autenticação multifator, falhas de logon de conta desabilitada e eventos de representação.

- **Conformidade:** seus requisitos de conformidade foram violados?

    Catalogue e identifique dados controlados ou confidenciais, incluindo permissões de compartilhamento para cada arquivo armazenado nos serviços de sincronização de arquivos para garantir a conformidade com regulamentações como PCI, SOX e HIPAA

- **Controle de configuração:** alterações não autorizadas estão sendo feitas em sua configuração?

    Monitore alterações de configuração incluindo a manipulação de configuração remota.

- **Cloud Discovery:** novos aplicativos estão sendo usados em sua organização? Você tem um problema de que estão sendo usados aplicativos Shadow IT que você não conhece?

    Classifique o risco geral para cada aplicativo de nuvem com base em certificações regulatórias e do setor e melhores práticas. Permite monitorar o número de usuários, atividades, volume de tráfego e horas de uso típicas para cada aplicativo de nuvem.

- **DLP:** arquivos proprietários estão sendo compartilhados publicamente? Você precisa colocar arquivos em quarentena?

    A integração de DLP local fornece correção de loop fechado e integração com as soluções de DLP locais existentes.

- **Contas privilegiadas:** você precisa monitorar contas de administrador?

    Monitoramento e relatórios de atividades de administradores e usuários com privilégios em tempo real.

- **Controle de compartilhamento:** como os dados estão sendo compartilhados em seu ambiente de nuvem?

    Inspecione o conteúdo de arquivos e o conteúdo na nuvem e imponha políticas de compartilhamento internas e externas. Monitore a colaboração e imponha políticas de compartilhamento, como impedir que arquivos sejam compartilhados fora de sua organização.

- **Detecção de ameaças:** há atividades suspeitas ameaçando seu ambiente de nuvem?

    Receba notificações em tempo real para qualquer limite de atividade ou violação de política por email ou mensagem de texto. Aplicando algoritmos de aprendizado de máquina, o Cloud App Security permite que você detecte o comportamento que poderia indicar que um usuário está usando os dados de maneira indevida.

## <a name="how-to-control-risk"></a>Como controlar o risco

Siga este processo para controlar o risco com políticas:

1. Crie uma política com base em um modelo ou uma consulta.

1. Ajuste a política para obter os resultados esperados.

1. Adicione ações automatizadas para responder a riscos e remediá-los automaticamente.

### <a name="create-a-policy"></a>Criar uma política

Você pode usar os modelos de política do Cloud App Security como base para todas as suas políticas ou criar políticas com base em uma consulta.

Os modelos de política ajudam a definir os filtros e configurações corretos necessários para detectar eventos de interesse específicos dentro de seu ambiente. Os modelos incluem políticas de todos os tipos e podem ser aplicados a vários serviços.

Para criar uma política com base em **Modelos de política**, siga estas etapas:

1. No console, clique em **Controlar** e em **Modelos**.

    ![Criar a política com base em um modelo](media/create-policy-from-template.png)

1. Clique no **+** na extrema direita da linha do modelo que você deseja usar. Uma página de criação de política é aberta, com a configuração predefinida do modelo.

1. Modifique o modelo conforme necessário da sua política personalizada. Todas as propriedades e campos dessa nova política baseada em modelo podem ser modificados de acordo com suas necessidades.
   > [!NOTE]
   > Ao usar os filtros de política, **Contains** pesquisa apenas palavras completas – separadas por vírgulas, pontos, espaços ou sublinhados. Por exemplo, se você pesquisar **malware** ou **virus**, ela encontrará virus_malware_file.exe, mas não encontrará malwarevirusfile.exe. Se você pesquisar *malware.exe*, encontrará TODOS os arquivos com malware ou exe no nome de arquivo, ao passo que se pesquisar **“malware.exe”** (com aspas) você encontrará apenas arquivos que contenham exatamente “malware.exe”.  
**Equals** pesquisa somente a cadeia de caracteres completa; por exemplo, se você pesquisar *malware.exe*, ela encontrará malware.exe, mas não malware.exe.txt.

1. Depois de criar a política baseada em modelo, um link para a nova política será exibido na coluna **Políticas vinculadas** na tabela de modelos de política ao lado do modelo por meio do qual a política foi criada.
    Você pode criar quantas políticas quiser com base em cada modelo e elas todas serão vinculadas ao modelo original. A vinculação permite acompanhar todas as políticas criadas usando o mesmo modelo.

Ou você pode **criar uma política durante a investigação**. Se estiver investigando o **Log de atividades**, os **Arquivos** ou as **Contas** e fizer drill down para pesquisar algo específico, a qualquer momento você poderá criar uma política com base nos resultados de sua investigação.

Por exemplo, se estiver examinando o **Log de atividades** e vir uma atividade de administrador de fora dos endereços IP do seu escritório.

Para criar uma política com base nos resultados da investigação, siga estas etapas:

1. No console, clique em **Investigar** e em **Log de atividades**, **Arquivos** ou **Contas**.

1. Use os filtros na parte superior da página para limitar os resultados da pesquisa à área suspeita. Por exemplo, na página do Log de atividades, clique em **Tipo de atividade** e selecione **Gravar Administradores** na operação do Azure. Em seguida, em **Endereço IP**, selecione **Categoria** e defina o valor para não incluir as categorias de endereço IP criadas para seus domínios reconhecidos, como seus endereços IP de administrador, de VPN e corporativo.

    ![Criar o arquivo com base na investigação](media/create-file-from-investigation.png)

1. No canto superior direito do console, clique em **Nova política com base na pesquisa**.

    ![Botão Nova política com base na pesquisa](media/new-policy-from-search-button.png)

1. Uma página de criação de política é aberta, contendo os filtros usados em sua investigação.

1. Modifique o modelo conforme necessário da sua política personalizada. Todas as propriedades e campos dessa política baseada em investigação podem ser modificados de acordo com suas necessidades.

    > [!NOTE]
    > Ao usar os filtros de política, **Contains** pesquisa apenas palavras completas – separadas por vírgulas, pontos, espaços ou sublinhados. Por exemplo, se você pesquisar **malware** ou **virus**, ela encontrará virus_malware_file.exe, mas não encontrará malwarevirusfile.exe.  
**Equals** pesquisa somente a cadeia de caracteres completa; por exemplo, se você pesquisar **malware.exe**, ela encontrará malware.exe, mas não malware.exe.txt.

    ![criar política de atividade com base na investigação](media/create-activity-policy-from-investigation.png)

    > [!NOTE]
    > Para obter mais informações sobre como definir os campos de política, confira a documentação da política correspondente:
    >
    > [Políticas de atividade do usuário](user-activity-policies.md)
    >
    > [Políticas de proteção de dados](data-protection-policies.md)
    >
    > [Políticas do Cloud Discovery](cloud-discovery-policies.md)

### <a name="add-automated-actions-to-respond-and-remediate-risks-automatically"></a>Adicionar ações automatizadas para responder a riscos e remediá-los automaticamente

Para obter uma lista de ações de governança disponíveis por aplicativo, confira [Controlar aplicativos conectados](governance-actions.md).

Você também poderá definir a política para enviar um alerta por email ou mensagem de texto quando forem detectadas correspondências.

Para definir suas preferências de notificação, acesse [Personalizar o portal](general-setup.md)

> [!NOTE]
> O número máximo de alertas enviados por mensagem de texto é 10 por número de telefone por dia. O dia é calculado de acordo com o fuso horário UTC.

## <a name="enable-and-disable-policies"></a>Habilitar e desabilitar políticas

Após criar uma política, você poderá habilitá-la ou desabilitá-la. Desabilitar evita a necessidade de excluir uma política após a criação dela a fim de interrompê-la. Em vez disso, se, por algum motivo, você desejar interromper a política, desabilite-a até optar por habilitá-la novamente.

- Para habilitar uma política, na página **Política**, clique nas reticências ao fim da linha da política que você deseja habilitar. Selecione **Habilitar**.

    ![Habilitar política](media/enable-policy.png)

- Para desabilitar uma política, na página **Política**, clique nas reticências ao fim da linha da política que você deseja desabilitar. Selecione **Desabilitar**.

    ![Desabilitar política](media/disable-policy.png)

Por padrão, após criar uma política, ela será habilitada.

## <a name="policies-overview-report"></a>Relatório de visão geral de políticas

O Cloud App Security permite exportar um relatório de visão geral de políticas mostrando as métricas de alerta agregadas por política para ajudar você a monitorar, compreender e personalizar suas políticas para proteger melhor sua organização.

Para exportar um log, execute estas etapas:

1. Na página **Políticas**, clique no botão **Exportar**.

1. Especifique o intervalo de tempo necessário.

1. Clique em **Exportar**. Esse processo pode levar algum tempo.

Para baixar o relatório exportado:

1. Depois que o relatório estiver pronto, acesse **Configurações** e, em seguida, **Relatórios exportados**.

1. No tabela, selecione o relatório relevante na lista de **Relatório de visão geral de políticas** e clique em baixar.

    ![botão de download](media/download-button.png)

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]

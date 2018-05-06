---
title: Controlar o uso de aplicativos de nuvem criando políticas no Cloud App Security | Microsoft Docs
description: Este tópico fornece informações sobre como as políticas são usadas e configuradas para controlar o uso de aplicativos de nuvem.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/22/2018
ms.topic: article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 14d10238-0f61-43e9-ab96-71534a27d3d4
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 578cedd1f499f91ae2e740a7e0e0f1495d86f3cb
ms.sourcegitcommit: 45311f2cafef79483e40d971a4c61c7673834d96
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2018
---
*Aplica-se ao: Microsoft Cloud App Security*


# <a name="control-cloud-apps-with-policies"></a>Controlar aplicativos de nuvem com políticas

As políticas permitem que você defina a maneira como deseja que os usuários se comportem na nuvem. Elas permitem que você detecte comportamento de risco, violações ou pontos de dados e atividades suspeitos em seu ambiente de nuvem e, se necessário, integrar fluxos de trabalho de correção para obter a mitigação de risco completa. Existem vários tipos de políticas que se correlacionam com diferentes tipos de informações que você deseja reunir sobre seu ambiente de nuvem e os tipos de ações de correção que deseja executar.  
  
Por exemplo, se você quiser colocar uma ameaça de violação de dados em quarentena, precisará ter um tipo de política em vigor diferente da necessária para bloquear o uso de um aplicativo de nuvem arriscado por sua organização.  
  
## <a name="policy-types"></a>Tipos de política  
Quando você observa a página **Política**, as várias políticas e modelos podem ser diferenciados pelo tipo e ícone para ver quais políticas estão disponíveis. As políticas disponíveis dependem da fonte de dados e do que foi habilitado no Cloud App Security para sua organização, por exemplo, se você carregou logs do Cloud Discovery, as políticas relacionadas ao Cloud Discovery são exibidas.

Os seguintes tipos de políticas podem ser criados:  
  
|Ícone Tipo de política|Tipo de política|Uso|  
|-----|-----------------|---------|  
|![ícone de política de acesso](./media/proxy-policy.png)|Política de acesso|Políticas de acesso fornecem monitoramento em tempo real e controle sobre logons de usuário para seus aplicativos de nuvem.|
|![ícone de política de atividade](./media/activity_policy.png)|Política de atividade|As políticas de atividade permitem que você aplique uma ampla gama de processos automatizados, utilizando as APIs do provedor de aplicativo. Essas políticas permitem que você monitore atividades específicas realizadas por vários usuários ou siga altas taxas inesperadas de um determinado tipo de atividade.|  
|![ícone de política de detecção de anomalias](./media/anomaly_detection_policy.png)|Política de detecção de anomalias|As políticas de detecção de anomalias permitem que você procure atividades incomuns na sua nuvem com base nos fatores de risco definidos aqui para alertar você quando acontecer algo que seja diferente da linha de base da sua organização ou da atividade regular do usuário.|  
|![ícone de política do cloud discovery](./media/discovery_policy.png)|Política de descoberta de aplicativo|As políticas de descoberta de aplicativo permitem que você defina alertas que notificam quando novos aplicativos são detectados na sua organização.|  
|![ícone de política de detecção de anomalias](./media/anomaly_detection_policy.png)|Política de detecção de anomalias do Cloud Discovery|As políticas de detecção de anomalias do Cloud Discovery analisam os logs usados para descobrir aplicativos de nuvem e pesquisa ocorrências incomuns. Por exemplo, quando um usuário que nunca usou o Dropbox antes de repente carrega 600 GB para o Dropbox ou quando há muito mais transações que o normal em um aplicativo específico.|  
|![ícone de política de arquivos](./media/file_policy.png)|Política de arquivos|As políticas de arquivos permitem que você examine seus aplicativos de nuvem quanto a tipos de arquivo ou arquivos especificados (compartilhados, compartilhados com domínios externos), dados (informações proprietárias, PII, informações de cartão de crédito etc.) e aplique ações de governança aos arquivos (as ações de governança são específicas do aplicativo de nuvem).|  
|![Ícone de política de sessão](./media/proxy-policy.png)|Política de sessão|Políticas de sessão fornecem monitoramento em tempo real e controle sobre a atividade do usuário nos seus aplicativos de nuvem.|

  
## <a name="identifying-risk"></a>Identificando o risco  
O Cloud App Security ajuda a mitigar diferentes riscos na nuvem. Você pode configurar qualquer política e alerta a ser associado a um dos seguintes riscos:  
  
-   **Controle de acesso:** quem acessa o que de onde?  
  
     Monitore continuamente o comportamento e detecte atividades anômalas, incluindo ataques internos e externos de alto risco e aplique uma política para alertar, bloquear ou exigir a verificação de identidade para qualquer aplicativo ou ação específica dentro de um aplicativo. Habilite políticas de controle de acesso móvel e local com base no usuário, dispositivo e geografia com bloqueio não refinado e exibição, edição e bloqueio granulares. Detecte eventos de logon suspeitos, incluindo falhas de autenticação multifator, falhas de logon de conta desabilitada e eventos de representação.  
  
-   **Conformidade:** seus requisitos de conformidade estão violados?  
  
     Catalogue e identifique dados controlados ou confidenciais, incluindo permissões de compartilhamento para cada arquivo armazenado nos serviços de sincronização de arquivos para garantir a conformidade com regulamentações como PCI, SOX e HIPAA  
  
-   **Controle de configuração:** estão sendo feitas alterações não autorizadas nas suas configurações?  
  
     Monitore alterações de configuração, incluindo manipulação de configuração remota.  
  
-   **Cloud Discovery:** aplicativos novos estão sendo usados em sua organização? Você tem um problema de aplicativos de TI Invisível sendo usados sobre os quais não tem conhecimento?  
  
     Classifique o risco geral para cada aplicativo de nuvem com base em normas e certificações e práticas recomendadas do setor, que permite que você monitore o número de usuários, atividades, volume de tráfego e horas de uso típico para  
    cada aplicativo de nuvem.  
  
-   **DLP:** arquivos proprietários estão sendo compartilhados publicamente? Você precisa colocar arquivos em quarentena?  
  
     A integração de DLP local fornece a correção de loop fechado e a integração com as soluções de DLP locais existentes.  
  
-   **Contas com privilégios:** você precisa monitorar contas de administrador?  
  
     Monitoramento e relatórios de atividades de administradores e usuários com privilégios em tempo real.  
  
-   **Controle de compartilhamento:** como os dados estão sendo compartilhados em seu ambiente de nuvem?  
  
     Inspecione o conteúdo de arquivos e na nuvem e imponha políticas de compartilhamento internas e externas. Monitore a colaboração e imponha políticas de compartilhamento, como bloquear o compartilhamento de arquivos fora da sua organização.  
  
-   **Detecção de ameaças:** há atividades suspeitas ameaçando seu ambiente de nuvem?  
  
     Receba notificações em tempo real para qualquer limite de atividade ou violação de política por email ou mensagem de texto. Ao aplicar algoritmos de aprendizado de máquina, o Cloud App Security permite que você detecte o comportamento que poderia indicar que um usuário está usando os dados de maneira indevida.  
  
## <a name="how-to-control-risk"></a>Como controlar o risco  
Siga este processo para controlar o risco com políticas:  
  
1.  Crie uma política de um modelo ou uma consulta.  
  
2.  Ajuste a política para obter os resultados esperados.  
  
3.  Adicione ações automatizadas para responder e corrigir riscos automaticamente.  
  
### <a name="create-a-policy"></a>Criar uma política  
Você pode usar os modelos de política do Cloud App Security como base para todas as suas políticas ou criar políticas de uma consulta.  
  
Modelos de política ajudam você a definir os filtros corretos e as configurações necessárias para detectar eventos específicos de interesse em seu ambiente. Os modelos incluem políticas de todos os tipos e podem ser aplicados a vários serviços.  
  
Para criar uma política de **Modelo de política**, execute estas etapas:  
  
1. No console, clique em **Controlar** seguido por **Modelos**.  
  
    ![](./media/create-policy-from-template.png)  
  
2. Clique no **+** na extrema direita da linha do modelo que deseja usar. Uma página de criação de política é aberta contendo a configuração predefinida do modelo.  
  
3. Modifique o modelo conforme necessário para sua política personalizada. Todas as propriedades e campos dessa política baseada em modelo podem ser modificados de acordo com suas necessidades.  
   > [!NOTE] 
   >Ao usar os filtros de política, **contém** pesquisa somente palavras inteiras: separadas por vírgulas, pontos, espaços ou sublinhados. Por exemplo, se você pesquisar **malware** ou **vírus**, ele localizará virus_malware_file.exe, mas não localizará malwarevirusfile.exe. Se pesquisar *malware.exe*, você localizará TODOS os arquivos com malware ou exe em seu nome de arquivo, enquanto se pesquisar **"malware.exe"** (com aspas), localizará apenas arquivos que contêm exatamente "malware.exe". 
    **É igual a** pesquisa apenas a cadeia de caracteres completa, por exemplo, se você pesquisar *malware.exe*, ele localizará malware.exe, mas não malware.exe.txt.  
4. Depois de criar a nova política baseada em modelo, um link para a nova política aparece na coluna **Políticas vinculadas** na tabela de modelos de política ao lado do modelo por meio do qual a política foi criada.   
    Você pode criar quantas políticas desejar de cada modelo e elas serão vinculadas ao modelo original, permitindo que você acompanhe todas as políticas criadas usando o mesmo modelo.  
  
Como alternativa, você pode **criar uma política durante a investigação**. Se você estiver investigando **Log de atividades**, **Arquivos** ou **Contas** e analisar detalhadamente para pesquisar algo específico, a qualquer momento você poderá criar uma nova política com base nos resultados da sua investigação.  
  
Por exemplo, se você estiver consultando o **Log de atividades** e encontrar uma atividade de administrador que não pertença aos endereços IP de seu escritório.

  
Para criar uma política com base nos resultados da investigação, execute as seguintes etapas:  
  
1.  No console, clique em **Investigar** seguido de **Log de atividades**, **Arquivos** ou **Contas**.  
  
2.  Use os filtros na parte superior da página para limitar os resultados da pesquisa à área suspeita, por exemplo, na página Log de atividades, clique em **Atividade** e selecione **Logon de administrador**. Em seguida, em **Endereço IP**, selecione **Categoria** e defina o valor para não incluir as categorias de endereço IP que você criou para seus domínios reconhecidos, como os endereços IP de administração, corporativos e de VPN.  
  
     ![Criar arquivo com base na investigação](./media/create-file-from-investigation.png)  
  
3.  No canto superior direito do console, clique em **Nova política da pesquisa**![](./media/new-policy-from-search-button.png)  
  
4.  Uma página de criação de política é aberta, contendo os filtros usados na sua investigação.  
  
5.  Modifique o modelo conforme necessário para sua política personalizada. Todas as propriedades e campos dessa política baseada em investigação podem ser modificados de acordo com suas necessidades.  
   
> [!NOTE] 
> Ao usar os filtros de política, **contém** pesquisa somente palavras inteiras: separadas por vírgulas, pontos, espaços ou sublinhados. Por exemplo, se você pesquisar **malware** ou **vírus**, ele localizará virus_malware_file.exe, mas não localizará malwarevirusfile.exe.  
     **É igual a** pesquisa apenas a cadeia de caracteres completa, por exemplo, se você pesquisar **malware.exe**, ele localizará malware.exe, mas não malware.exe.txt.  
  
 
 
![criar política de atividade com base na investigação](./media/create-activity-policy-from-investigation.png)
 
 
  
> [!NOTE]  
>  Para obter mais informações sobre como definir campos de política, consulte a documentação da política correspondente:  
>   
>  [Políticas de atividade de usuário](user-activity-policies.md)  
>   
>  [Políticas de proteção de dados](data-protection-policies.md)  
>   
>  [Políticas do Cloud Discovery](cloud-discovery-policies.md)  

  
### <a name="add-automated-actions-to-respond-and-remediate-risks-automatically"></a>Adicionar ações automatizadas para responder e corrigir riscos automaticamente

Para obter uma lista de ações de governança disponíveis por aplicativo, consulte [Controlando aplicativos conectados](governance-actions.md).

Você também pode definir a política para enviar um alerta por email ou mensagem de texto quando correspondências são detectadas. 

Para definir suas preferências de notificação, vá até [Personalizar o portal](general-setup.md) 
  
> [!NOTE] 
> O número máximo de alertas enviados por meio de mensagem de texto é 10 por número de telefone por dia. O dia é calculado de acordo com o fuso horário UTC. 


## <a name="enable-and-disable-policies"></a>Habilitar e desabilitar políticas

Depois de criar uma política, é possível habilitá-la ou desabilitá-la. Isso evita a necessidade de excluir uma política após criá-la a fim de a interromper. Em vez disso, se por alguma razão você desejar interromper a política, desabilite-a até que queira habilitá-la novamente.

- Para habilitar uma política, na página **Política**, clique nos três pontos no final da linha da política que você deseja habilitar e selecione **Habilitar**. 

![Habilitar política](./media/enable-policy.png)

- Para desabilitar uma política, na página **Política**, clique nos três pontos no final da linha da política que você deseja desabilitar e selecione **Desabilitar**.

![Desabilitar política](./media/disable-policy.png)

Por padrão, depois de criar uma nova política, ela é habilitada.

## <a name="see-also"></a>Consulte Também  
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
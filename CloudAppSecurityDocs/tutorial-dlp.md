---
title: Descobrir e proteger informações confidenciais em sua organização
description: Este tutorial descreve o processo para descobrir e proteger informações confidenciais no Microsoft Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 05/26/2020
ms.topic: tutorial
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.suite: ems
ms.openlocfilehash: 4a75a256f8d4fa2e9483a153fce7ba1e1ab28376
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90880947"
---
# <a name="tutorial-discover-and-protect-sensitive-information-in-your-organization"></a>Tutorial: Descobrir e proteger informações confidenciais em sua organização

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Em um mundo perfeito, todos os seus funcionários entendem a importância da proteção de informações e do trabalho em relação às suas políticas. No mundo real, é provável que um parceiro ocupado que trabalha frequentemente com informações de contabilidade carregue por acidente um documento confidencial no repositório do Box com permissões incorretas. Uma semana depois, você percebe que as informações confidenciais da sua empresa foram vazadas para a concorrência.

Para ajudá-lo a evitar isso, o Microsoft Cloud App Security fornece um pacote amplo de recursos de DLP que abrangem os vários pontos de vazamento de dados existentes nas organizações.

Este tutorial fornece uma visão geral e instruções sobre como usar o Cloud App Security para descobrir dados confidenciais potencialmente expostos e aplicar controles para evitar sua exposição.

> [!div class="checklist"]
>
> * Descobrir seus dados
> * Classificar informações confidenciais
> * Proteja seus dados
> * Monitorar e relatar seus dados

## <a name="how-to-discover-and-protect-sensitive-information-in-your-organization"></a>Como descobrir e proteger informações confidenciais em sua organização

Nossa abordagem para a proteção de informações pode ser dividida nas fases a seguir, que permitem que você proteja seus dados ao longo de todo o ciclo de vida, em vários locais e dispositivos.

![ciclo de vida do Shadow IT](media/tutorial-dlp-solution.png)

### <a name="phase-1-discover-your-data"></a>Fase 1: Descobrir seus dados

1. **Conecte aplicativos**: A primeira etapa na descoberta de quais dados estão sendo usados em sua organização é conectar os aplicativos de nuvem usados em sua organização ao Cloud App Security. Uma vez conectado, o Cloud App Security pode verificar dados, adicionar classificações e impor políticas e controles. A forma como os aplicativos estão conectados afeta como e quando verificações e controles são aplicados. Você pode conectar seus aplicativos de uma das seguintes maneiras:

    * **Use um conector de aplicativo**: Nossos conectores de aplicativos usam as APIs fornecidas pelos provedores de aplicativos. Eles fornecem maior visibilidade e controle sobre os aplicativos usados em sua organização. As verificações são realizadas periodicamente (a cada 12 horas) e em tempo real (disparadas sempre que uma alteração é detectada). Para obter mais informações e instruções sobre como adicionar aplicativos, confira [Conectar aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).
    * **Use o Controle de Aplicativos de Acesso Condicional**: Nossa solução Controle de Aplicativos de Acesso Condicional usa uma arquitetura de proxy reverso que é integrada exclusivamente ao Acesso Condicional do Azure AD (Active Directory). Após a configuração no Azure AD, os usuários serão roteados para o Cloud App Security, onde as políticas de acesso e sessão são impostas para proteger os dados que os aplicativos tentam usar. Esse método de conexão permite aplicar controles a [qualquer aplicativo](proxy-deployment-any-app.md). Para obter mais informações, confira [Proteger aplicativos com o Controle de Aplicativos de Acesso Condicional do Cloud App Security](proxy-intro-aad.md).

1. **Investigue**: Depois de conectar um aplicativo ao Cloud App Security usando seu conector de API, o Cloud App Security examina todos os arquivos que ele usa. Em seguida, você pode ir até a página de investigação de arquivos (**Investigar** > **Arquivos**) para obter uma visão geral dos arquivos compartilhados por seus aplicativos de nuvem, bem como da acessibilidade e do status deles. Para obter mais informações, confira [Investigar arquivos](file-filters.md).

### <a name="phase-2-classify-sensitive-information"></a>Fase 2: Classificar informações confidenciais

1. **Defina quais informações são confidenciais**: Antes de procurar informações confidenciais em seus arquivos, primeiro você precisa definir o que é considerado confidencial para sua organização. Como parte do nosso [serviço de classificação de dados](dcs-inspection.md), oferecemos mais de 100 tipos de informações confidenciais prontas para uso, ou você pode [criar seu tipo](/microsoft-365/compliance/create-a-custom-sensitive-information-type) para se adequar à política da sua empresa. **O Cloud App Security é nativamente integrado à Proteção de Informações da Microsoft**, e os mesmos tipos e rótulos confidenciais estão disponíveis em ambos os serviços. Portanto, quando você quiser definir informações confidenciais, vá até o portal de Proteção de Informações da Microsoft para criá-las e, uma vez definidas, elas estarão disponíveis no Cloud App Security. Você também pode usar tipos de classificações avançadas, como a impressão digital ou a EDM (correspondência exata de dados).

    Se você já tiver feito o trabalho árduo de identificar as informações confidenciais e aplicar os rótulos de confidencialidade apropriados, poderá usar esses rótulos em suas políticas sem precisar verificar o conteúdo novamente.
1. **Habilitar a integração da Proteção de Informações do Azure**
    1. No Cloud App Security, na engrenagem de configurações, selecione a página **Configurações** no título **Sistema**.
    1. Em **Proteção de Informações do Azure**, selecione **Verificar automaticamente novos arquivos para os rótulos de classificação da Proteção de Informações do Azure**.

    Confira mais informações em [Integração da Proteção de Informações do Azure](azip-integration.md).
1. **Crie políticas para identificar informações confidenciais em arquivos**: Depois de conhecer os tipos de informações que você deseja proteger, é hora de criar políticas para detectá-las. Para começar, crie as seguintes políticas:

    **Política de arquivos**  
    Use esse tipo de política para verificar o conteúdo dos arquivos armazenados em seus aplicativos de nuvem conectados à API quase em tempo real e em dados em repouso. Os arquivos são verificados usando um dos nossos métodos de inspeção compatíveis, incluindo **conteúdo criptografado da Proteção de Informações do Azure**, graças à sua **integração nativa** com o Cloud App Security.

    1. Vá para **Controle** > **Políticas**, clique em **Criar Política** e, em seguida, selecione **Política de arquivos**.
    1. Em **Método de inspeção**, escolha e configure um dos seguintes serviços de classificação:

        * **[Serviço de Classificação de Dados](dcs-inspection.md)** : Usa as decisões de classificação que você tomou no Office 365, na Proteção de Informações do Azure e no Cloud App Security para fornecer uma experiência de rotulagem unificada. Esse é o método de inspeção de conteúdo preferencial, pois ele proporciona uma experiência consistente e unificada entre os produtos da Microsoft.
        * **[DLP interno](content-inspection-built-in.md)** : Inspeciona os arquivos para obter informações confidenciais usando nosso mecanismo interno de inspeção de conteúdo de DLP.
        * **[Integração de DLP externa](icap-stunnel.md)** : Para empresas que desejam usar soluções de DLP de terceiros, as políticas de arquivos do Cloud App Security podem direcionar com segurança os arquivos a serem inspecionados para sua solução de DLP externa por meio de um servidor ICAP.

    1. Para arquivos altamente confidenciais, selecione **Criar um alerta** e escolha os alertas de que você precisa, para ser informado quando houver arquivos com informações confidenciais desprotegidas em sua organização.
    1. Clique em **Criar**.

    **Política de sessão**  
    Use esse tipo de política para verificar e proteger arquivos em tempo real no acesso, para:

    * **Impedir o vazamento de dados**: bloqueie o download, o recorte, a cópia e a impressão de documentos confidenciais em, por exemplo, dispositivos não gerenciados.
    * **Proteger arquivos no download**: exigir que os documentos sejam rotulados e protegidos com a Proteção de Informações do Azure. Essa ação garante que o documento esteja protegido e o acesso do usuário seja restrito em uma sessão potencialmente arriscada.
    * **Impedir o upload de arquivos sem rótulo**: exija que um arquivo tenha o rótulo e a proteção corretos antes que um arquivo confidencial seja carregado, distribuído e usado por outras pessoas. Com essa ação, você pode garantir que arquivos sem rótulo com conteúdo confidencial sejam impedidos de serem carregados até que o usuário classifique o conteúdo.

    1. Vá para **Controle** > **Políticas**, clique em **Criar Política** e, em seguida, selecione **Política de sessão**.
    1. Em **Tipo de controle sessão**, escolha uma das opções com DLP.
    1. Em **Método de inspeção**, escolha e configure um dos seguintes serviços de classificação:

        * **[Serviço de Classificação de Dados](dcs-inspection.md)** : Usa as decisões de classificação que você tomou no Office 365, na Proteção de Informações do Azure e no Cloud App Security para fornecer uma experiência de rotulagem unificada. Esse é o método de inspeção de conteúdo preferencial, pois ele proporciona uma experiência consistente e unificada entre os produtos da Microsoft.
        * **[DLP interno](content-inspection-built-in.md)** : inspeciona os arquivos para obter informações confidenciais usando nosso mecanismo interno de inspeção de conteúdo de DLP.

    1. Para arquivos altamente confidenciais, selecione **Criar um alerta** e escolha os alertas de que você precisa, para ser informado quando houver arquivos com informações confidenciais desprotegidas em sua organização.
    1. Clique em **Criar**.

Você deve criar quantas políticas forem necessárias para detectar dados confidenciais de acordo com a política da sua empresa.

### <a name="phase-3-protect-your-data"></a>Fase 3: Proteja seus dados

Agora, você pode detectar arquivos com informações confidenciais, mas o que você realmente quer fazer é proteger essas informações contra possíveis ameaças. Quando estiver ciente de um incidente, você poderá corrigir a situação manualmente ou usar uma das ações de governança automáticas fornecidas pelo Cloud App Security para proteger seus arquivos. As ações incluem, entre outras, controles nativos da Proteção de Informações do Azure, ações fornecidas pela API e monitoramento em tempo real. O tipo de governança que você pode aplicar depende do tipo de política que está configurando, da seguinte maneira:

1. **[Ações de governança de política](governance-actions.md#file-governance-actions) de arquivos**: usa a API do provedor de aplicativo de nuvem e nossas integrações nativas para proteger arquivos, incluindo:
    * Disparar alertas e enviar notificações por email sobre o incidente
    * Gerenciar rótulos aplicados a um arquivo para impor controles nativos da Proteção de Informações do Azure
    * Alterar o acesso de compartilhamento a um arquivo
    * Colocar um arquivo em quarentena
    * Remover permissões específicas de um arquivo ou uma pasta no Office 365
    * Mover um arquivo para a pasta da lixeira

1. **Controles de política de sessão**: usa recursos de proxy reverso para proteger arquivos, incluindo:
    * Disparar alertas e enviar notificações por email sobre o incidente
    * [Monitorar todas as atividades](session-policy-aad.md#monitor-session): permite explicitamente o download ou o upload de arquivos e monitora todas as atividades relacionadas.
    * [Bloquear](session-policy-aad.md#block-download): bloqueia explicitamente o download ou o upload de arquivos. Use essa opção para proteger os arquivos confidenciais de sua organização contra vazamento ou invasão de qualquer dispositivo, incluindo dispositivos não gerenciados.
    * [Proteger](session-policy-aad.md#protect-download): aplica automaticamente um rótulo de classificação a arquivos que correspondem aos filtros de arquivo da política. Use essa opção para proteger o download de arquivos confidenciais.

### <a name="phase-4-monitor-and-report-on-your-data"></a>Fase 4: Monitorar e relatar seus dados

Suas políticas estão todas ativas para inspecionar e proteger seus dados. Agora, você quer [verificar seu painel](daily-activities-to-protect-your-cloud-environment.md#check-the-dashboard) diariamente para ver quais novos alertas foram disparados. Esse é um bom local para observar a integridade do seu ambiente de nuvem. Seu painel ajuda você a ter uma noção do que está acontecendo e, se necessário, iniciar uma [investigação](investigate.md).

Uma das maneiras mais eficientes de monitorar incidentes com arquivo confidenciais é acessar a página **Políticas** e examinar as correspondências para as políticas que você configurou. Além disso, se você configurou alertas, também deve considerar o monitoramento regular de alertas de arquivo por título acessando a página **Alertas**, especificando a categoria como **DLP** e verificando quais políticas relacionadas a arquivo estão sendo disparadas. A verificação desses incidentes pode ajudá-lo a ajustar suas políticas para focar em ameaças que são de interesse de sua organização.

Em conclusão: o gerenciamento de informações confidenciais dessa maneira garante que os dados salvos na nuvem tenham proteção máxima contra exfiltração e infiltração mal-intencionados. Além disso, caso um arquivo seja compartilhado ou perdido, ele só poderá ser acessado por usuários autorizados.

## <a name="see-also"></a>Consulte Também

> [!div class="nextstepaction"]
> [Noções básicas sobre filtros e dados de arquivo](file-filters.md)

> [!div class="nextstepaction"]
> [Políticas de arquivos](data-protection-policies.md)

> [!div class="nextstepaction"]
> [Inspeção de conteúdo](content-inspection.md)

> [!div class="nextstepaction"]
> [Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]  

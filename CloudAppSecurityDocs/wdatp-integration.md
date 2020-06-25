---
title: Integrar o Microsoft defender ATP com o Cloud App Security
description: Este artigo descreve como integrar a proteção avançada contra ameaças do Microsoft defender com o Cloud App Security para obter visibilidade aprimorada de ti em sombra e gerenciamento de riscos.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/24/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 0b2106faed750a2eba06ae505a6d7d9cf17ca1be
ms.sourcegitcommit: f8d170b0da8e8d7f723ddc9e845595f64dc79a02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85323766"
---
# <a name="microsoft-defender-advanced-threat-protection-integration-with-microsoft-cloud-app-security"></a>Integração da proteção avançada contra ameaças do Microsoft defender com o Microsoft Cloud App Security

*Aplica-se a: Microsoft Cloud App Security*

O Microsoft Cloud App Security integra-se com o Microsoft defender com a ATP (proteção avançada contra ameaças) nativamente. A integração simplifica a distribuição do Cloud Discovery, estende as funcionalidades do Cloud Discovery para além da rede corporativa e permite a investigação baseada em computador. [O Microsoft defender ATP](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection) é uma plataforma de segurança para proteção, detecção, investigação e resposta inteligentes. O Microsoft defender ATP protege pontos de extremidade contra ameaças cibernéticos, detecta ataques avançados e violações de dados, automatiza incidentes de segurança e melhora a postura de segurança.

Cloud App Security usa as informações de tráfego coletadas pelo Microsoft defender ATP sobre os aplicativos de nuvem e os serviços que estão sendo acessados por computadores Windows 10 gerenciados por ti. A integração nativa permite que você execute Cloud Discovery em qualquer computador na rede corporativa, usando Wi-Fi público, enquanto estiver em roaming e por meio de acesso remoto. Também permite a investigação baseada em computador.

A integração não exige nenhuma implantação adicional e funciona prontamente. Você não precisa rotear nem espelhar o tráfego dos pontos de extremidade, nem executar etapas de integração complexas. Os logs de seus pontos de extremidade enviados para Cloud App Security fornecem informações de usuário para atividades de tráfego. A atividade de rede do Microsoft defender ATP fornece o contexto do dispositivo. O contexto do dispositivo de emparelhamento com o nome de usuário fornece uma imagem completa em sua rede, permitindo que você determine qual usuário fez qual a atividade de qual computador.

Além disso, ao identificar um usuário arriscado, você pode verificar todos os computadores que o usuário acessou para detectar possíveis riscos. Se você identificar um computador arriscado, verifique todos os usuários que o usaram para detectar possíveis riscos potenciais.

Depois que as informações de tráfego forem coletadas, você estará pronto para se [aprofundar no uso do aplicativo de nuvem](discovered-apps.md#deep-dive-into-discovered-apps) em sua organização. Cloud App Security aproveita os recursos de proteção de rede do Microsoft defender ATP para bloquear o acesso de dispositivo de ponto de extremidade a aplicativos de nuvem. Você pode bloquear aplicativos [marcando-os como não **aprovados** ](governance-discovery.md#BKMK_SanctionApp) no Portal. Com base no uso abrangente e na avaliação de risco de cada aplicativo não aprovado, os domínios do aplicativo são usados para criar [indicadores de domínio](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/manage-indicators#create-indicators-for-ips-and-urlsdomains-preview) no portal do Microsoft defender ATP. O Microsoft defender antivírus, em execução em dispositivos de ponto de extremidade, usa os indicadores de domínio para bloquear o acesso a esses aplicativos.

> [!NOTE]
> Quer experimentar o Microsoft defender ATP? [Inscreva-se para uma avaliação gratuita](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-assignaccess-abovefoldlink).

## <a name="prerequisites"></a>Pré-requisitos

- Licença do Microsoft Cloud App Security
- Licença do Microsoft defender ATP
- Windows 10 versão 1709 (so Build 16299,1085 com KB4493441), Windows 10 versão 1803 (so Build 17134,704 com KB4493464), Windows 10 versão 1809 (so Build 17763,379 com KB4489899) ou versões posteriores do Windows 10
- Microsoft Defender Antivírus
  - [proteção em tempo real habilitada](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/configure-real-time-protection-windows-defender-antivirus)
  - [proteção fornecida pela nuvem habilitada](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/enable-cloud-protection-windows-defender-antivirus)
  - [Proteção de rede habilitada e configurada para o modo de bloqueio](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/enable-network-protection)

## <a name="how-it-works"></a>Como ele funciona

Por conta própria, o Cloud App Security coleta logs dos seus pontos de extremidade usando [logs carregados por você](create-snapshot-cloud-discovery-reports.md) ou [configurando o upload de log automático](discovery-docker.md). A integração nativa permite que você aproveite os logs que o agente do Microsoft defender ATP cria quando é executado no Windows e monitora as transações de rede. Use essas informações para a descoberta de TI de sombra nos computadores Windows de sua rede.

Para permitir que você execute Cloud Discovery em outras plataformas, é melhor usar o [coletor de logs](discovery-docker.md)do Cloud app Security, juntamente com a integração do Microsoft defender ATP para monitorar suas máquinas com Windows 10.

## <a name="how-to-integrate-microsoft-defender-atp-with-cloud-app-security"></a>Como integrar o Microsoft defender ATP com o Cloud App Security

Para habilitar a integração do Microsoft defender ATP com o Cloud App Security:

1. No portal do Microsoft defender ATP, no painel de navegação, selecione **configuração de preferências**.
2. No menu **Configurações**, em **Geral**, selecione **Recursos avançados**.
3. Alterne o **Microsoft Cloud App Security** para **Ativado**.
4. Clique em **Salvar preferências**.

>[!NOTE]
> Demora até duas horas para os dados serem exibidos no Cloud App Security após você habilitar a integração.
>

![Configurações do WD ATP](media/wdatp-settings.png)

## <a name="investigate-machines-in-cloud-app-security"></a>Investigar computadores no Cloud App Security

Depois de integrar o Microsoft defender ATP com o Cloud App Security, você pode investigar os dados do computador descoberto no painel do Cloud Discovery.

1. No portal do Cloud App Security, clique em **Cloud Discovery** e, em seguida, **Painel do Cloud Discovery**.
2. Na barra de navegação superior, em **Relatórios contínuos**, selecione **Usuários de ponto de extremidade do Win10**.
  ![Relatório do WD ATP](media/win10-dashboard-report.png)
3. Na parte superior, você verá o número de computadores descobertos adicionados após a integração.
4. Clique na guia **Computadores**.
5. Faça uma busca detalhada em cada computador listado e use as guias para exibir os dados de investigação. Encontre correlações entre os computadores, os usuários, os endereços IP e os aplicativos envolvidos em incidentes:

    - **Visão geral**
        - Transações: informações sobre o número de transações que ocorreram no computador durante o período de tempo selecionado.
        - Tráfego total: informações sobre a quantidade total de tráfego (em MB) durante o período de tempo selecionado.
        - Carregamentos: informações sobre a quantidade total de tráfego (em MB) carregados pelo computador durante o período de tempo selecionado.
        - Downloads: informações sobre a quantidade total de tráfego (em MB) baixados pelo computador durante o período de tempo selecionado.
    - **Aplicativos Descobertos**  
  Lista todos os aplicativos descobertos que foram acessados pelo computador.
    - **Histórico de usuários**  
    Lista todos os usuários que se conectaram ao computador.
    - **Histórico de endereços IP**  
    Lista todos os endereços IP que foram atribuídos ao computador.
 ![Visão geral de computadores](media/machines-overview.png)

Assim como acontece com qualquer outra fonte do Cloud Discovery, é possível exportar os dados do relatório de usuários de ponto de extremidade do Win10 para uma investigação adicional.

> [!NOTE]
>
> - O Microsoft defender ATP encaminha dados para Cloud App Security em partes de ~ 4 MB (~ 4000 transações de ponto de extremidade)
> - Se o limite de 4 MB não for atingido em 1 hora, o Microsoft defender ATP relatará todas as transações executadas na última hora.
> - Se o dispositivo de ponto de extremidade estiver protegido por um proxy de encaminhamento, os dados de tráfego não serão visíveis para o Microsoft defender ATP e, portanto, não serão incluídos nos relatórios do Cloud Discovery. Para obter mais informações, consulte [monitorando a conexão de rede por trás do proxy de encaminhamento](https://techcommunity.microsoft.com/t5/Microsoft-Defender-ATP/MDATP-Monitoring-network-connection-behind-forward-proxy-Public/ba-p/758274).

## <a name="block-access-to-unsanctioned-cloud-apps"></a>Bloquear o acesso a aplicativos de nuvem não aprovados

Cloud App Security usa a marca [**de aplicativo interna**](governance-discovery.md#BKMK_SanctionApp) não atestada para marcar os aplicativos de nuvem como proibidos para uso, disponíveis nas páginas Cloud Discovery e catálogo de aplicativos de nuvem. Ao habilitar a integração com o Microsoft defender ATP, você pode bloquear diretamente o acesso a aplicativos não aprovados com um único clique no portal de Cloud App Security.

### <a name="how-it-works"></a>Como ele funciona

Os aplicativos marcados como não **aprovados** no Cloud app Security são sincronizados automaticamente com o Microsoft defender ATP, geralmente em alguns minutos. Mais especificamente, os domínios usados por esses aplicativos não aprovados são propagados para dispositivos de ponto de extremidade a serem bloqueados pelo Microsoft defender antivírus dentro do SLA de proteção de rede.

### <a name="how-to-enable-cloud-app-blocking-with-microsoft-defender-atp"></a>Como habilitar o bloqueio de aplicativo de nuvem com o Microsoft defender ATP

Use as etapas a seguir para habilitar o controle de acesso para aplicativos de nuvem:

1. Em Cloud App Security, sob as configurações engrenagem, selecione **configurações**, em **Cloud Discovery** selecione **Microsoft defender ATP**e, em seguida, selecione **bloquear aplicativos não aprovados**.

    ![Captura de tela mostrando como habilitar o bloqueio com o Microsoft defender ATP](media/defender-atp-integration.png)

1. Na central de segurança do Microsoft defender, vá para **configurações**  >  **recursos avançados**e, em seguida, selecione **indicadores de rede personalizados**. Para obter informações sobre indicadores de rede, consulte [criar indicadores para IPS e URLs/domínios](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/manage-indicators#create-indicators-for-ips-and-urlsdomains-preview).

    Isso permite que você aproveite os recursos de proteção de rede do Microsoft defender antivírus para bloquear o acesso a um conjunto predefinido de URLs usando Cloud App Security, seja atribuindo manualmente [marcas de aplicativo](governance-discovery.md#BKMK_SanctionApp) a aplicativos específicos ou usando uma política de [descoberta de aplicativo](cloud-discovery-policies.md#creating-an-app-discovery-policy)automaticamente.

    ![Captura de tela mostrando como habilitar indicadores de rede personalizados no Microsoft defender ATP](media/defender-atp-custom-network-indicators.png)

## <a name="investigate-unsanctioned-apps-in-microsoft-defender-security-center"></a>Investigar aplicativos não aprovados na central de segurança do Microsoft defender

Cada tentativa de acessar um aplicativo não aprovado dispara um alerta na central de segurança do Microsoft defender com detalhes detalhados sobre toda a sessão. Isso permite que você execute investigações mais aprofundadas em tentativas de acessar aplicativos não aprovados, além de fornecer informações adicionais relevantes para uso na investigação de dispositivos de ponto de extremidade.

Às vezes, o acesso a um aplicativo não aprovado não é bloqueado, seja porque o dispositivo de ponto de extremidade não está configurado corretamente ou se a política de imposição ainda não foi propagada para o ponto de extremidade. Nesta instância, os administradores do Microsoft defender ATP receberão um alerta na central de segurança do Microsoft defender que o aplicativo não aprovado não foi bloqueado.

![Captura de tela mostrando o alerta de aplicativo não aprovado do Microsoft defender ATP](media/defender-atp-unsanctioned-app-alert.png)

> [!NOTE]
>
> - Leva até duas horas depois que você marca um aplicativo como não **aprovado** para que domínios de aplicativo se propaguem para dispositivos de ponto de extremidade.
> - Por padrão, os aplicativos e domínios marcados como não **aprovados** no Cloud app Security serão bloqueados para todos os dispositivos de ponto de extremidade na organização.
> - No momento, não há suporte para URLs completas em aplicativos não aprovados. Portanto, quando aplicativos sem sanções configurados com URLs completas, eles não são propagados para o Microsoft defender ATP e não serão bloqueados. Por exemplo, `google.com/drive` não tem suporte, enquanto tem `drive.google.com` suporte.
> - As notificações no navegador podem variar entre diferentes navegadores.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

## <a name="related-videos"></a>Vídeos relacionados

> [!div class="nextstepaction"]
> [Descoberta de TI sombra além da rede corporativa](https://www.youtube.com/watch?v=f8hbvbY1Hnc)

[!INCLUDE [Open support ticket](includes/support.md)]

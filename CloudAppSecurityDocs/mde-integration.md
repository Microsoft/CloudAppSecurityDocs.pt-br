---
title: Integre o Microsoft defender for Endpoint ao Cloud App Security
description: Este artigo descreve como integrar o Microsoft defender para ponto de extremidade com Cloud App Security para obter visibilidade aprimorada de ti em sombra e gerenciamento de riscos.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 10/29/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 95e8271a26828ad4e3adb73727e2692cac3a8d23
ms.sourcegitcommit: 5367d8fdf99d61719a395728f2ef4b014604e3bc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/08/2020
ms.locfileid: "94371240"
---
# <a name="microsoft-defender-for-endpoint-integration-with-microsoft-cloud-app-security"></a>Integração do Microsoft defender para EndPoint com o Microsoft Cloud App Security

[!INCLUDE [Banner for top of topics](includes/banner.md)]

O Microsoft Cloud App Security integra-se com o Microsoft defender para ponto de extremidade nativamente. A integração simplifica a distribuição de Cloud Discovery, amplia os recursos de Cloud Discovery além da rede corporativa e habilita a investigação baseada em dispositivo. [O Microsoft defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) é uma plataforma de segurança para proteção, detecção, investigação e resposta inteligentes. O defender for Endpoint protege pontos de extremidade de ameaças cibernéticos, detecta ataques avançados e violações de dados, automatiza incidentes de segurança e melhora a postura de segurança.

Cloud App Security usa as informações de tráfego coletadas pelo defender para o ponto de extremidade sobre os aplicativos e serviços de nuvem que estão sendo acessados por dispositivos Windows 10 gerenciados por ti. A integração nativa permite que você execute Cloud Discovery em qualquer dispositivo na rede corporativa, usando Wi-Fi público, enquanto estiver em roaming e por meio de acesso remoto. Ele também habilita a investigação baseada em dispositivo.

A integração não exige nenhuma implantação adicional e funciona prontamente. Você não precisa rotear nem espelhar o tráfego dos pontos de extremidade, nem executar etapas de integração complexas. Os logs de seus pontos de extremidade enviados para Cloud App Security fornecem informações de usuário para atividades de tráfego. A atividade de rede do defender for Endpoint fornece o contexto do dispositivo. O contexto do dispositivo de emparelhamento com o nome de usuário fornece uma imagem completa em sua rede, permitindo que você determine qual usuário fez qual atividade de qual dispositivo.

Além disso, ao identificar um usuário arriscado, você pode verificar todos os dispositivos que o usuário acessou para detectar possíveis riscos. Se você identificar um dispositivo arriscado, verifique todos os usuários que o usaram para detectar possíveis riscos potenciais.

Depois que as informações de tráfego forem coletadas, você estará pronto para se [aprofundar no uso do aplicativo de nuvem](discovered-apps.md#deep-dive-into-discovered-apps) em sua organização. Cloud App Security aproveita os recursos do defender para proteção de rede de ponto de extremidade para bloquear o acesso de dispositivo de ponto de extremidade a aplicativos de nuvem. Você pode bloquear aplicativos [marcando-os como não **aprovados**](governance-discovery.md#BKMK_SanctionApp) no Portal. Com base no uso abrangente e na avaliação de risco de cada aplicativo não aprovado, os domínios do aplicativo são usados para criar [indicadores de domínio](/windows/security/threat-protection/microsoft-defender-atp/manage-indicators#create-indicators-for-ips-and-urlsdomains-preview) no portal do defender for Endpoint. O Microsoft defender antivírus, em execução em dispositivos de ponto de extremidade, usa os indicadores de domínio para bloquear o acesso a esses aplicativos.

> [!NOTE]
> Deseja experimentar o Microsoft defender para ponto de extremidade? [Inscreva-se em uma avaliação gratuita](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-assignaccess-abovefoldlink).

## <a name="prerequisites"></a>Pré-requisitos

- Licença do Microsoft Cloud App Security
- Licença do Microsoft defender for Endpoint
- Windows 10 versão 1709 (so Build 16299,1085 com KB4493441), Windows 10 versão 1803 (so Build 17134,704 com KB4493464), Windows 10 versão 1809 (so Build 17763,379 com KB4489899) ou versões posteriores do Windows 10
- Microsoft Defender Antivírus
  - [proteção em tempo real habilitada](/windows/security/threat-protection/windows-defender-antivirus/configure-real-time-protection-windows-defender-antivirus)
  - [proteção fornecida pela nuvem habilitada](/windows/security/threat-protection/windows-defender-antivirus/enable-cloud-protection-windows-defender-antivirus)
  - [Proteção de rede habilitada e configurada para o modo de bloqueio](/windows/security/threat-protection/microsoft-defender-atp/enable-network-protection)

## <a name="how-it-works"></a>Como ele funciona

Por conta própria, o Cloud App Security coleta logs dos seus pontos de extremidade usando [logs carregados por você](create-snapshot-cloud-discovery-reports.md) ou [configurando o upload de log automático](discovery-docker.md). A integração nativa permite que você aproveite o agente dos logs defender for Endpoint cria quando ele é executado no Windows e monitora as transações de rede. Use essas informações para a descoberta de ti de sombra nos dispositivos Windows na sua rede.

Para permitir que você execute Cloud Discovery em outras plataformas, é melhor usar o [coletor de logs](discovery-docker.md)do Cloud app Security, juntamente com a integração do defender for Endpoint para monitorar seus dispositivos Windows 10.

[Assista a nossos vídeos](#related-videos) mostrando os benefícios de usar o defender for Endpoint com Cloud app Security.

## <a name="how-to-integrate-microsoft-defender-for-endpoint-with-cloud-app-security"></a>Como integrar o Microsoft defender for Endpoint ao Cloud App Security

Para habilitar o defender para a integração de ponto de extremidade com o Cloud App Security:

1. Na central de segurança do Microsoft defender, no painel de navegação, selecione **configurações**.
2. Em **geral** , selecione **recursos avançados**.
3. Alterne o **Microsoft Cloud App Security** para **Ativado**.
4. Clique em **Aplicar**.

>[!NOTE]
> Demora até duas horas para os dados serem exibidos no Cloud App Security após você habilitar a integração.
>

![Configurações do defender para ponto de extremidade](media/mde-settings.png)

Para configurar a severidade para alertas enviados ao Microsoft defender para ponto de extremidade:

1. Em Cloud App Security, clique no ícone **configurações** e, em seguida, selecione **Microsoft defender para ponto de extremidade**.
1. Em **alertas** , selecione o nível de severidade global para alertas.
1. Clique em **Salvar**.

![Configurações de alerta do defender for Endpoint](media/mde-alert-severity-settings.png)

## <a name="investigate-devices-in-cloud-app-security"></a>Investigar dispositivos no Cloud App Security

Depois de integrar o defender for Endpoint ao Cloud App Security, você pode investigar os dados de dispositivo descobertos no painel de Cloud Discovery.

1. Em Cloud App Security, clique em **Cloud Discovery** e, em seguida, **Cloud Discovery painel**.
2. Na barra de navegação superior, em **Relatórios contínuos** , selecione **Usuários de ponto de extremidade do Win10**.
  ![Relatório do defender for Endpoint](media/win10-dashboard-report.png)
3. Na parte superior, você verá o número de dispositivos descobertos adicionados após a integração.
4. Clique na guia **Dispositivos**.
5. Você pode fazer uma busca detalhada em cada dispositivo listado e usar as guias para exibir os dados de investigação. Encontre correlações entre os dispositivos, os usuários, os endereços IP e os aplicativos que estavam envolvidos em incidentes:

    - **Visão geral**
        - **Nível de risco do dispositivo** : mostra o quão arriscado o perfil do dispositivo é relativo a outros dispositivos em sua organização, conforme indicado pela severidade (alta, média, baixa, informativa). Cloud App Security usa perfis de dispositivo do defender for Endpoint para cada dispositivo baseado na análise avançada. A atividade que é anômala para a linha de base de um dispositivo é avaliada e determina o nível de risco do dispositivo. Use o nível de risco do dispositivo para determinar quais dispositivos investigar primeiro.
        - **Transações** : informações sobre o número de transações que ocorreram no dispositivo durante o período de tempo selecionado.
        - **Tráfego total** : informações sobre a quantidade total de tráfego (em MB) durante o período de tempo selecionado.
        - Carregamentos: informações sobre a quantidade total de tráfego (em MB) carregados pelo dispositivo durante o período de tempo selecionado.
        - **Downloads** : informações sobre a quantidade total de tráfego (em MB) baixada pelo dispositivo durante o período de tempo selecionado.
    - **Aplicativos Descobertos**  
    Lista todos os aplicativos descobertos que foram acessados pelo dispositivo.
    - **Histórico de usuários**  
    Lista todos os usuários que entraram no dispositivo.
    - **Histórico de endereços IP**  
    Lista todos os endereços IP que foram atribuídos ao dispositivo.
 ![Visão geral de dispositivos](media/devices-overview.png)

Assim como acontece com qualquer outra fonte do Cloud Discovery, é possível exportar os dados do relatório de usuários de ponto de extremidade do Win10 para uma investigação adicional.

> [!NOTE]
>
> - O defender for Endpoint encaminha dados para Cloud App Security em partes de ~ 4 MB (~ 4000 transações de ponto de extremidade)
> - Se o limite de 4 MB não for atingido em 1 hora, o defender for Endpoint relatará todas as transações executadas na última hora.
> - Se o dispositivo de ponto de extremidade estiver protegido por um proxy de encaminhamento, os dados de tráfego não serão visíveis para o defender para pontos de extremidade e, portanto, não serão incluídos em relatórios de Cloud Discovery. É recomendável rotear os logs do proxy de encaminhamento para Cloud App Security usando o **upload de log automatizado** para obter visibilidade completa. Para obter uma maneira alternativa de exibir esse tráfego e investigar URLs acessadas por dispositivos por trás do proxy de encaminhamento, consulte [monitorando a conexão de rede por trás do proxy de encaminhamento](https://techcommunity.microsoft.com/t5/Microsoft-Defender-ATP/MDATP-Monitoring-network-connection-behind-forward-proxy-Public/ba-p/758274).

## <a name="investigate-device-network-events-in-defender-for-endpoint"></a>Investigar eventos de rede do dispositivo no defender para ponto de extremidade

Use as etapas a seguir para obter visibilidade mais granular da atividade de rede do dispositivo no Microsoft defender para ponto de extremidade:

1. Em Cloud App Security, em **descoberta** e selecione **dispositivos**.
1. Selecione o computador que você deseja investigar e, na parte superior direita, clique em **Exibir no Microsoft defender para ponto de extremidade**.
1. Na central de segurança do Microsoft defender, em **dispositivos** > {dispositivo selecionado}, selecione **linha do tempo**.
1. Em **filtros** , selecione **eventos de rede**.
1. Investigue os eventos de rede do dispositivo, conforme necessário.

![Captura de tela mostrando o cronograma do dispositivo na central de segurança do Microsoft defender](media/mde-selected-device.png)

## <a name="investigate-app-usage-in-defender-for-endpoint-with-advanced-hunting"></a>Investigar o uso do aplicativo no defender para ponto de extremidade com busca avançada

Use as etapas a seguir para obter visibilidade mais granular sobre eventos de rede relacionados ao aplicativo no defender para ponto de extremidade:

1. Em Cloud App Security, em **descoberta** e, em seguida, selecione **descoberto**.
1. Clique no aplicativo que você deseja investigar para abrir sua gaveta.
1. Clique na lista de **domínios** do aplicativo e copie a lista de domínios.
1. Na central de segurança do Microsoft defender, em **dispositivos** , selecione **busca avançada**.
1. Cole a consulta a seguir e substitua `<DOMAIN_LIST>` pela lista de domínios que você copiou anteriormente.

    ```kusto
    DeviceNetworkEvents
    | where RemoteUrl in ("<DOMAIN_LIST>")
    | order by Timestamp desc
    ```

1. Execute a consulta e investigue os eventos de rede para este aplicativo.

![Captura de tela mostrando a busca avançada da central de segurança do Microsoft defender](media/mde-advanced-hunting.png)

## <a name="block-access-to-unsanctioned-cloud-apps"></a>Bloquear o acesso a aplicativos de nuvem não aprovados

Cloud App Security usa a marca [**de aplicativo interna**](governance-discovery.md#BKMK_SanctionApp) não atestada para marcar os aplicativos de nuvem como proibidos para uso, disponíveis nas páginas Cloud Discovery e catálogo de aplicativos de nuvem. Ao habilitar a integração com o defender for Endpoint, você pode bloquear diretamente o acesso a aplicativos não aprovados com um único clique no portal de Cloud App Security.

### <a name="how-blocking-works"></a>Como o bloqueio funciona

Os aplicativos marcados como não **aprovados** no Cloud app Security são sincronizados automaticamente com o defender para ponto de extremidade, geralmente em alguns minutos. Mais especificamente, os domínios usados por esses aplicativos não aprovados são propagados para dispositivos de ponto de extremidade a serem bloqueados pelo Microsoft defender antivírus dentro do SLA de proteção de rede.

### <a name="how-to-enable-cloud-app-blocking-with-defender-for-endpoint"></a>Como habilitar o bloqueio de aplicativo de nuvem com o defender para ponto de extremidade

Use as etapas a seguir para habilitar o controle de acesso para aplicativos de nuvem:

1. Em Cloud App Security, na engrenagem configurações, selecione **configurações** , em **Cloud Discovery** selecione **Microsoft defender para ponto de extremidade** e, em seguida, selecione **bloquear aplicativos não aprovados**.

    ![Captura de tela mostrando como habilitar o bloqueio com o defender para ponto de extremidade](media/mde-integration.png)

1. Na central de segurança do Microsoft defender, vá para **configurações**  >  **recursos avançados** e, em seguida, selecione **indicadores de rede personalizados**. Para obter informações sobre indicadores de rede, consulte [criar indicadores para IPS e URLs/domínios](/windows/security/threat-protection/microsoft-defender-atp/manage-indicators#create-indicators-for-ips-and-urlsdomains-preview).

    Isso permite que você aproveite os recursos de proteção de rede do Microsoft defender antivírus para bloquear o acesso a um conjunto predefinido de URLs usando Cloud App Security, seja atribuindo manualmente [marcas de aplicativo](governance-discovery.md#BKMK_SanctionApp) a aplicativos específicos ou usando uma política de [descoberta de aplicativo](cloud-discovery-policies.md#creating-an-app-discovery-policy)automaticamente.

    ![Captura de tela mostrando como habilitar indicadores de rede personalizados no defender para ponto de extremidade](media/mde-custom-network-indicators.png)

## <a name="investigate-unsanctioned-apps-in-microsoft-defender-security-center"></a>Investigar aplicativos não aprovados na central de segurança do Microsoft defender

Cada tentativa de acessar um aplicativo não aprovado dispara um alerta na central de segurança do Microsoft defender com detalhes detalhados sobre toda a sessão. Isso permite que você execute investigações mais aprofundadas em tentativas de acessar aplicativos não aprovados, além de fornecer informações adicionais relevantes para uso na investigação de dispositivos de ponto de extremidade.

Às vezes, o acesso a um aplicativo não aprovado não é bloqueado, seja porque o dispositivo de ponto de extremidade não está configurado corretamente ou se a política de imposição ainda não foi propagada para o ponto de extremidade. Nessa instância, os administradores do defender for Endpoint receberão um alerta na central de segurança do Microsoft defender que o aplicativo não aprovado não foi bloqueado.

![Captura de tela mostrando alerta do aplicativo defender para ponto de extremidade não aprovado](media/mde-unsanctioned-app-alert.png)

> [!NOTE]
>
> - Leva até duas horas depois que você marca um aplicativo como não **aprovado** para que domínios de aplicativo se propaguem para dispositivos de ponto de extremidade.
> - Por padrão, os aplicativos e domínios marcados como não **aprovados** no Cloud app Security serão bloqueados para todos os dispositivos de ponto de extremidade na organização.
> - No momento, não há suporte para URLs completas em aplicativos não aprovados. Portanto, quando aplicativos que não são aprovados configurados com URLs completas, eles não são propagados para o defender for Endpoint e não serão bloqueados. Por exemplo, `google.com/drive` não tem suporte, enquanto tem `drive.google.com` suporte.
> - As notificações no navegador podem variar entre diferentes navegadores.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

## <a name="related-videos"></a>Vídeos relacionados

> [!div class="nextstepaction"]
> [Descobrir e bloquear a ti sombra usando o defender para ponto de extremidade](https://www.youtube.com/watch?v=MsHkTOoqSQo)

> [!div class="nextstepaction"]
> [Descoberta de TI sombra além da rede corporativa](https://www.youtube.com/watch?v=f8hbvbY1Hnc)

[!INCLUDE [Open support ticket](includes/support.md)]

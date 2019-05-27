---
title: Integrar o Microsoft Defender ATP ao Cloud App Security
description: Este artigo descreve como integrar o Microsoft Defender Advanced Threat Protection com o Cloud App Security para visibilidade aprimorada de TI sombra e o gerenciamento de riscos.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: rkarlin
ms.date: 12/14/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: b35ca44c-da8e-49ec-89d1-c076d123c14f
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: b49ab77b33548d6fd188eadde97294ceb6c62ca5
ms.sourcegitcommit: 235b7d5f1f49075c199b154abc38e51326c0493e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66173522"
---
# <a name="microsoft-defender-advanced-threat-protection-integration-with-microsoft-cloud-app-security"></a>Integração do Microsoft Defender Advanced Threat Protection com o Microsoft Cloud App Security

*Aplica-se a: Microsoft Cloud App Security*

Microsoft Cloud App Security integra-se com o Microsoft Advanced Threat ATP (proteção Defender) nativamente. A integração simplifica a distribuição do Cloud Discovery, estende as funcionalidades do Cloud Discovery para além da rede corporativa e permite a investigação baseada em computador. [Proteção de ameaças avançadas (ATP) do Microsoft Defender](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection) é uma plataforma de segurança para proteção inteligente, detecção, investigação e resposta. Microsoft Defender ATP protege pontos de extremidade contra ameaças cibernéticas, detecta violações de dados e de ataques avançadas, automatiza a incidentes de segurança e melhora a postura de segurança.

Microsoft Cloud App Security usa as informações de tráfego coletadas pelo Microsoft Defender ATP sobre aplicativos de nuvem e serviços que está sendo acessados de computadores com Windows 10 gerenciado por TI. A integração permite que você execute o Cloud Discovery em qualquer computador na rede corporativa, usando Wi-Fi público, roaming e acesso remoto. Também permite a investigação baseada em computador.

Depois de identificar um usuário de risco, você poderá verificar todos os computadores acessados pelo usuário para detectar riscos potenciais. Caso identifique um computador de risco, verifique todos os usuários que o utilizaram para detectar riscos potenciais. Os logs dos seus pontos de extremidade roteados para o Cloud App Security fornecem informações de usuário para atividades de tráfego. Atividade de rede Microsoft Defender ATP fornece o contexto de dispositivo. Emparelhe o contexto de dispositivo com o nome de usuário para fornecer uma visão completa da rede na qual o usuário executou uma atividade específica de um computador específico.

Microsoft Cloud App Security usa a integração nativa com o Microsoft Defender ATP para explorar dados sobre o tráfego de aplicativo e serviço de nuvem de dispositivos gerenciados do Windows. A integração não exige nenhuma implantação adicional e funciona prontamente. Você não precisa rotear nem espelhar o tráfego dos pontos de extremidade, nem executar etapas de integração complexas.

> [!NOTE]
> Deseja experimentar o Microsoft Defender ATP? [Inscreva-se para uma avaliação gratuita](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-assignaccess-abovefoldlink).
>


## <a name="prerequisites"></a>Pré-requisitos

- Licença do Microsoft Cloud App Security
- Licença do Microsoft Defender ATP
- Computadores Windows 10 que executam a versão 1809 ou posterior
- Ative a **versão prévia dos recursos** para habilitar este recurso no Cloud App Security

## <a name="how-it-works"></a>Como funciona

Por conta própria, o Cloud App Security coleta logs dos seus pontos de extremidade usando [logs carregados por você](create-snapshot-cloud-discovery-reports.md) ou [configurando o upload de log automático](discovery-docker.md). Integração nativa permite tirar proveito dos logs de agente do Microsoft Defender ATP cria quando ele é executado no Windows e monitora as transações de rede. Use essas informações para a descoberta de TI de sombra nos computadores Windows de sua rede.

Para que você possa executar a descoberta de nuvem em outras plataformas, é melhor usar os dois o Cloud App Security [coletor de log](discovery-docker.md), juntamente com a integração do Microsoft Defender ATP para monitorar seus computadores com Windows 10.

## <a name="how-to-integrate-microsoft-defender-atp-with-cloud-app-security"></a>Como integrar o Microsoft Defender ATP com o Cloud App Security

Para habilitar a integração com o Cloud App Security no Microsoft Defender ATP:

1. No portal do Microsoft Defender ATP, no painel de navegação, selecione **instalação preferências**.
2. No menu **Configurações**, em **Geral**, selecione **Recursos avançados**.
3. Alterne o **Microsoft Cloud App Security** para **Ativado**.
4. Clique em **Salvar preferências**.

>[!NOTE]
> Demora até duas horas para os dados serem exibidos no Cloud App Security após você habilitar a integração.
>

   ![Configurações do WD ATP](./media/wdatp-settings.png)

## <a name="investigate-machines-in-cloud-app-security"></a>Investigar computadores no Cloud App Security

Após você integrar o Microsoft Defender ATP com o Cloud App Security, você pode investigar os dados de computador descobertos no painel do Cloud Discovery.

1. No portal do Cloud App Security, clique em **Cloud Discovery** e, em seguida, **Painel do Cloud Discovery**.
2. Na barra de navegação superior, em **Relatórios contínuos**, selecione **Usuários de ponto de extremidade do Win10**.
  ![Relatório do WD ATP](./media/win10-dashboard-report.png)
3. Na parte superior, você verá o número de computadores descobertos adicionados após a integração.
4. Clique na guia **Computadores**.
5. Faça uma busca detalhada em cada computador listado e use as guias para exibir os dados de investigação. Encontre correlações entre os computadores, os usuários, os endereços IP e os aplicativos envolvidos em incidentes:
   - **Visão geral**
      - Transações: Informações sobre o número de transações que ocorreram no computador durante o período selecionado.
      - Tráfego total: Informações sobre o volume total de tráfego (em MB) durante o período selecionado.
     - Uploads: Informações sobre o volume total de tráfego (em MB) carregado pelo computador durante o período selecionado.
     - Downloads: Informações sobre o volume total de tráfego (em MB) baixado pelo computador durante o período selecionado.
   - **Aplicativos descobertos**<br>
  Lista todos os aplicativos descobertos que foram acessados pelo computador.
   - **Histórico de usuários**<br>
    Lista todos os usuários que se conectaram ao computador.
   - **Histórico de endereços IP**<br>
    Lista todos os endereços IP que foram atribuídos ao computador.
 ![Visão geral de computadores](./media/machines-overview.png)
 
Assim como acontece com qualquer outra fonte do Cloud Discovery, é possível exportar os dados do relatório de usuários de ponto de extremidade do Win10 para uma investigação adicional. 

> [!NOTE]
> - Defender ATP encaminha os dados ao Cloud App Security em partes de ~ 4 MB (transações de ponto de extremidade de ~ 4000)
> - Se o limite de 4 MB não é atingido em 1 hora, relatórios de Defender ATP todas as transações executadas na última hora.

## <a name="related-videos"></a>Vídeos Relacionados

[Descoberta de TI de sombra estejam fora da rede corporativa com o Cloud App Security e o Microsoft Defender ATP](https://www.youtube.com/watch?v=f8hbvbY1Hnc)  

## <a name="next-steps"></a>Próximas etapas 
[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md) 

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/)  
  

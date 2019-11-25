---
title: Integrate Microsoft Defender ATP with Cloud App Security
description: This article describes how to integrate Microsoft Defender Advanced Threat Protection with Cloud App Security for enhanced visibility into Shadow IT and risk management.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 7/11/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: b35ca44c-da8e-49ec-89d1-c076d123c14f
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: aeddfb56542309b0ee6b1f0d4cdec85bb36a120e
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2019
ms.locfileid: "74459439"
---
# <a name="microsoft-defender-advanced-threat-protection-integration-with-microsoft-cloud-app-security"></a>Microsoft Defender Advanced Threat Protection integration with Microsoft Cloud App Security

*Aplica-se ao: Microsoft Cloud App Security*

Microsoft Cloud App Security integrates with Microsoft Defender Advanced Threat Protection (ATP) natively. A integração simplifica a distribuição do Cloud Discovery, estende as funcionalidades do Cloud Discovery para além da rede corporativa e permite a investigação baseada em computador. [Microsoft Defender Advanced Threat Protection (ATP)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection) is a security platform for intelligent protection, detection, investigation, and response. Microsoft Defender ATP protects endpoints from cyber threats, detects advanced attacks and data breaches, automates security incidents, and improves security posture.

Microsoft Cloud App Security uses the traffic information collected by Microsoft Defender ATP about the cloud apps and services being accessed from IT-managed Windows 10 machines. A integração permite que você execute o Cloud Discovery em qualquer computador na rede corporativa, usando Wi-Fi público, roaming e acesso remoto. Também permite a investigação baseada em computador.

Depois de identificar um usuário de risco, você poderá verificar todos os computadores acessados pelo usuário para detectar riscos potenciais. Caso identifique um computador de risco, verifique todos os usuários que o utilizaram para detectar riscos potenciais. Os logs dos seus pontos de extremidade roteados para o Cloud App Security fornecem informações de usuário para atividades de tráfego. Microsoft Defender ATP network activity provides device context. Emparelhe o contexto de dispositivo com o nome de usuário para fornecer uma visão completa da rede na qual o usuário executou uma atividade específica de um computador específico.

Microsoft Cloud App Security uses the native integration with Microsoft Defender ATP to tap into data about cloud app and service traffic from managed Windows devices. A integração não exige nenhuma implantação adicional e funciona prontamente. Você não precisa rotear nem espelhar o tráfego dos pontos de extremidade, nem executar etapas de integração complexas.

> [!NOTE]
> Want to experience Microsoft Defender ATP? [Inscreva-se para uma avaliação gratuita](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-assignaccess-abovefoldlink).
>


## <a name="prerequisites"></a>Pré-requisitos

- Licença do Microsoft Cloud App Security
- Microsoft Defender ATP license
- Windows 10 version 1709 (OS Build 16299.1085 with KB4493441), Windows 10 version 1803 (OS Build 17134.704 with KB4493464), Windows 10 version 1809 (OS Build 17763.379 with KB4489899) or later Windows 10 versions
- Ative a **versão prévia dos recursos** para habilitar este recurso no Cloud App Security

## <a name="how-it-works"></a>Como funciona

Por conta própria, o Cloud App Security coleta logs dos seus pontos de extremidade usando [logs carregados por você](create-snapshot-cloud-discovery-reports.md) ou [configurando o upload de log automático](discovery-docker.md). Native integration enables you to take advantage of the logs Microsoft Defender ATP's agent creates when it runs on Windows and monitors network transactions. Use essas informações para a descoberta de TI de sombra nos computadores Windows de sua rede.

To enable you to perform Cloud Discovery across other platforms, it's best to use both the Cloud App Security [log collector](discovery-docker.md), along with Microsoft Defender ATP integration to monitor your Windows 10 machines.

## <a name="how-to-integrate-microsoft-defender-atp-with-cloud-app-security"></a>How to integrate Microsoft Defender ATP with Cloud App Security

To enable integration with Cloud App Security from Microsoft Defender ATP:

1. In the Microsoft Defender ATP portal, from the navigation pane, select **Preferences setup**.
2. No menu **Configurações**, em **Geral**, selecione **Recursos avançados**.
3. Alterne o **Microsoft Cloud App Security** para **Ativado**.
4. Clique em **Salvar preferências**.

>[!NOTE]
> Demora até duas horas para os dados serem exibidos no Cloud App Security após você habilitar a integração.
>

   ![Configurações do WD ATP](./media/wdatp-settings.png)

## <a name="investigate-machines-in-cloud-app-security"></a>Investigar computadores no Cloud App Security

After you integrate Microsoft Defender ATP with Cloud App Security, you can investigate discovered machine data in the Cloud Discovery dashboard.

1. No portal do Cloud App Security, clique em **Cloud Discovery** e, em seguida, **Painel do Cloud Discovery**.
2. Na barra de navegação superior, em **Relatórios contínuos**, selecione **Usuários de ponto de extremidade do Win10**.
  ![Relatório do WD ATP](./media/win10-dashboard-report.png)
3. Na parte superior, você verá o número de computadores descobertos adicionados após a integração.
4. Clique na guia **Computadores**.
5. Faça uma busca detalhada em cada computador listado e use as guias para exibir os dados de investigação. Encontre correlações entre os computadores, os usuários, os endereços IP e os aplicativos envolvidos em incidentes:
   - **Visão geral**
      - Transactions: Information about the number of transactions that took place on the machine over the selected period of time.
      - Total traffic: Information about the total amount of traffic (in MB) over the selected period of time.
     - Uploads: Information about the total amount of traffic (in MB) uploaded by the machine over the selected period of time.
     - Downloads: Information about the total amount of traffic (in MB) downloaded by the machine over the selected period of time.
   - **Aplicativos descobertos**<br>
  Lista todos os aplicativos descobertos que foram acessados pelo computador.
   - **Histórico de usuários**<br>
    Lista todos os usuários que se conectaram ao computador.
   - **Histórico de endereços IP**<br>
    Lista todos os endereços IP que foram atribuídos ao computador.
 ![Visão geral de computadores](./media/machines-overview.png)
 
Assim como acontece com qualquer outra fonte do Cloud Discovery, é possível exportar os dados do relatório de usuários de ponto de extremidade do Win10 para uma investigação adicional. 

> [!NOTE]
> - Defender ATP forwards data to Cloud App Security in chunks of ~4 MB (~4000 endpoint transactions)
> - If the 4 MB limit isn't reached within 1 hour, Defender ATP reports all the transactions performed over the last hour.

## <a name="related-videos"></a>Vídeos Relacionados

[Shadow IT discovery beyond the corporate network with Microsoft Defender ATP and Cloud App Security](https://www.youtube.com/watch?v=f8hbvbY1Hnc)  

## <a name="next-steps"></a>Próximas etapas 
[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md) 

[!INCLUDE [Open support ticket](includes/support.md)]  
  

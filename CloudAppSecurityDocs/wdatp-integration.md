---
title: Integrar o Windows Defender ATP ao Cloud App Security
description: Este artigo descreve como integrar a Proteção Avançada contra Ameaças do Windows Defender ao Cloud App Security para melhor visibilidade da TI sombra e do gerenciamento de riscos.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: barbkess
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
ms.openlocfilehash: 2312ee7cdb7ab7f7e4f9a132442fac397614189b
ms.sourcegitcommit: 8ef0438fa35916c48625ff750cb85e9628d202f2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56281314"
---
# <a name="windows-defender-advanced-threat-protection-integration-with-microsoft-cloud-app-security"></a>Integração da Proteção Avançada contra Ameaças do Windows Defender ao Microsoft Cloud App Security | Microsoft Docs

*Aplica-se a: Microsoft Cloud App Security*

O Microsoft Cloud App Security é integrado nativamente ao Windows Defender ATP (Proteção Avançada contra Ameaças). A integração simplifica a distribuição do Cloud Discovery, estende as funcionalidades do Cloud Discovery para além da rede corporativa e permite a investigação baseada em computador. [Windows Defender ATP (Proteção Avançada contra Ameaças)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection) é uma plataforma de segurança para proteção, detecção, investigação e resposta inteligentes. O Windows Defender ATP protege pontos de extremidade contra ameaças cibernéticas, detecta violações de dados e ataques avançados, automatiza os incidentes de segurança e melhora a postura de segurança.

O Microsoft Cloud App Security usa as informações de tráfego coletadas pelo Windows Defender ATP sobre os serviços e os aplicativos na nuvem que estão sendo acessados em computadores Windows 10 gerenciados por TI. A integração permite que você execute o Cloud Discovery em qualquer computador na rede corporativa, usando Wi-Fi público, roaming e acesso remoto. Também permite a investigação baseada em computador.

Depois de identificar um usuário de risco, você poderá verificar todos os computadores acessados pelo usuário para detectar riscos potenciais. Caso identifique um computador de risco, verifique todos os usuários que o utilizaram para detectar riscos potenciais. Os logs dos seus pontos de extremidade roteados para o Cloud App Security fornecem informações de usuário para atividades de tráfego. A atividade de rede do Windows Defender ATP fornece o contexto de dispositivo. Emparelhe o contexto de dispositivo com o nome de usuário para fornecer uma visão completa da rede na qual o usuário executou uma atividade específica de um computador específico.

O Microsoft Cloud App Security usa a integração nativa com o Windows Defender ATP para acessar dados sobre o tráfego do serviço e do aplicativo na nuvem em dispositivos Windows gerenciados. A integração não exige nenhuma implantação adicional e funciona prontamente. Você não precisa rotear nem espelhar o tráfego dos pontos de extremidade, nem executar etapas de integração complexas.

> [!NOTE]
> Deseja experimentar o Windows Defender ATP? [Inscreva-se para uma avaliação gratuita](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-assignaccess-abovefoldlink).
>


## <a name="prerequisites"></a>Pré-requisitos

- Licença do Microsoft Cloud App Security
- Licença do Windows Defender ATP
- Computadores Windows 10 que executam a versão 1809 ou posterior


## <a name="how-it-works"></a>Como funciona

Por conta própria, o Cloud App Security coleta logs dos seus pontos de extremidade usando [logs carregados por você](create-snapshot-cloud-discovery-reports.md) ou [configurando o upload de log automático](discovery-docker.md). A integração nativa permite que você aproveite os logs criados pelo agente do Windows Defender ATP quando ele é executado no Windows e monitora as transações de rede. Use essas informações para a descoberta de TI de sombra nos computadores Windows de sua rede.

Para permitir que você execute o Cloud Discovery em outras plataformas, é melhor usar o [coletor de logs](discovery-docker.md) do Cloud App Security, juntamente com a integração com o Windows Defender ATP para monitorar os computadores Windows 10.

## <a name="how-to-integrate-windows-defender-atp-with-cloud-app-security"></a>Como integrar o Windows Defender ATP ao Cloud App Security

Para habilitar a integração com o Cloud App Security do Windows Defender ATP:

1. No portal do Windows Defender ATP, no painel de navegação, selecione **Configuração de preferências**.
2. No menu **Configurações**, em **Geral**, selecione **Recursos avançados**.
3. Alterne o **Microsoft Cloud App Security** para **Ativado**.
4. Clique em **Salvar preferências**.

>[!NOTE]
> Demora até duas horas para os dados serem exibidos no Cloud App Security após você habilitar a integração.
>

   ![Configurações do WD ATP](./media/wdatp-settings.png)

## <a name="investigate-machines-in-cloud-app-security"></a>Investigar computadores no Cloud App Security

Depois de integrar o Windows Defender ATP ao Cloud App Security, você poderá investigar os dados de computador descobertos no painel do Cloud Discovery.

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


## <a name="related-videos"></a>Vídeos Relacionados

[Descoberta de TI de sombra além da rede corporativa com o Windows Defender ATP e o Cloud App Security](https://www.youtube.com/watch?v=f8hbvbY1Hnc)  

## <a name="next-steps"></a>Próximas etapas 
[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md) 

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/)  
  

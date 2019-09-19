---
title: Integrar o Microsoft defender ATP com o Cloud App Security
description: Este artigo descreve como integrar a proteção avançada contra ameaças do Microsoft defender com o Cloud App Security para obter visibilidade aprimorada de ti em sombra e gerenciamento de riscos.
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
ms.openlocfilehash: 826e28b55471c3e07ebfeaa51b3fa65ee3debb03
ms.sourcegitcommit: 8a49c166424fea83853b0a6895212367526abe78
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71084840"
---
# <a name="microsoft-defender-advanced-threat-protection-integration-with-microsoft-cloud-app-security"></a>Integração da proteção avançada contra ameaças do Microsoft defender com o Microsoft Cloud App Security

*Aplica-se a: Microsoft Cloud App Security*

O Microsoft Cloud App Security integra-se com o Microsoft defender com a ATP (proteção avançada contra ameaças) nativamente. A integração simplifica a distribuição do Cloud Discovery, estende as funcionalidades do Cloud Discovery para além da rede corporativa e permite a investigação baseada em computador. A [ATP (proteção avançada contra ameaças) do Microsoft defender](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection) é uma plataforma de segurança para proteção, detecção, investigação e resposta inteligentes. O Microsoft defender ATP protege pontos de extremidade contra ameaças cibernéticos, detecta ataques avançados e violações de dados, automatiza incidentes de segurança e melhora a postura de segurança.

Microsoft Cloud App Security usa as informações de tráfego coletadas pelo Microsoft defender ATP sobre os aplicativos de nuvem e os serviços que estão sendo acessados por computadores Windows 10 gerenciados por ti. A integração permite que você execute o Cloud Discovery em qualquer computador na rede corporativa, usando Wi-Fi público, roaming e acesso remoto. Também permite a investigação baseada em computador.

Depois de identificar um usuário de risco, você poderá verificar todos os computadores acessados pelo usuário para detectar riscos potenciais. Caso identifique um computador de risco, verifique todos os usuários que o utilizaram para detectar riscos potenciais. Os logs dos seus pontos de extremidade roteados para o Cloud App Security fornecem informações de usuário para atividades de tráfego. A atividade de rede do Microsoft defender ATP fornece o contexto do dispositivo. Emparelhe o contexto de dispositivo com o nome de usuário para fornecer uma visão completa da rede na qual o usuário executou uma atividade específica de um computador específico.

Microsoft Cloud App Security usa a integração nativa com o Microsoft defender ATP para aproveitar dados sobre o tráfego de serviço e aplicativo de nuvem de dispositivos Windows gerenciados. A integração não exige nenhuma implantação adicional e funciona prontamente. Você não precisa rotear nem espelhar o tráfego dos pontos de extremidade, nem executar etapas de integração complexas.

> [!NOTE]
> Quer experimentar o Microsoft defender ATP? [Inscreva-se para uma avaliação gratuita](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-assignaccess-abovefoldlink).
>


## <a name="prerequisites"></a>Pré-requisitos

- Licença do Microsoft Cloud App Security
- Licença do Microsoft defender ATP
- Windows 10 versão 1709 (so Build 16299,1085 com KB4493441), Windows 10 versão 1803 (so Build 17134,704 com KB4493464), Windows 10 versão 1809 (so Build 17763,379 com KB4489899) ou versões posteriores do Windows 10
- Ative a **versão prévia dos recursos** para habilitar este recurso no Cloud App Security

## <a name="how-it-works"></a>Como funciona

Por conta própria, o Cloud App Security coleta logs dos seus pontos de extremidade usando [logs carregados por você](create-snapshot-cloud-discovery-reports.md) ou [configurando o upload de log automático](discovery-docker.md). A integração nativa permite que você aproveite os logs que o agente do Microsoft defender ATP cria quando é executado no Windows e monitora as transações de rede. Use essas informações para a descoberta de TI de sombra nos computadores Windows de sua rede.

Para permitir que você execute Cloud Discovery em outras plataformas, é melhor usar o [coletor de logs](discovery-docker.md)do Cloud app Security, juntamente com a integração do Microsoft defender ATP para monitorar suas máquinas com Windows 10.

## <a name="how-to-integrate-microsoft-defender-atp-with-cloud-app-security"></a>Como integrar o Microsoft defender ATP com o Cloud App Security

Para habilitar a integração com o Cloud App Security do Microsoft defender ATP:

1. No portal do Microsoft defender ATP, no painel de navegação, selecione **configuração de preferências**.
2. No menu **Configurações**, em **Geral**, selecione **Recursos avançados**.
3. Alterne o **Microsoft Cloud App Security** para **Ativado**.
4. Clique em **Salvar preferências**.

>[!NOTE]
> Demora até duas horas para os dados serem exibidos no Cloud App Security após você habilitar a integração.
>

   ![Configurações do WD ATP](./media/wdatp-settings.png)

## <a name="investigate-machines-in-cloud-app-security"></a>Investigar computadores no Cloud App Security

Depois de integrar o Microsoft defender ATP com o Cloud App Security, você pode investigar os dados do computador descoberto no painel do Cloud Discovery.

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
> - O defender ATP encaminha dados para Cloud App Security em partes de ~ 4 MB (~ 4000 transações de ponto de extremidade)
> - Se o limite de 4 MB não for atingido em 1 hora, o defender ATP relatará todas as transações executadas na última hora.

## <a name="related-videos"></a>Vídeos Relacionados

[Sombra da descoberta de ti além da rede corporativa com Microsoft defender ATP e Cloud App Security](https://www.youtube.com/watch?v=f8hbvbY1Hnc)  

## <a name="next-steps"></a>Próximas etapas 
[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md) 

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/)  
  

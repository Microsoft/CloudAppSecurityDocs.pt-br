---
title: Integrar a proteção avançada contra ameaças do Windows Defender ao Cloud App Security | Microsoft Docs
description: Este artigo fornece informações sobre como integrar o Windows Defender ATP à integração perfeita do Cloud App Security e uma visibilidade aprimorada no gerenciamento de riscos e TI sombra.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/3/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: b35ca44c-da8e-49ec-89d1-c076d123c14f
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 23989eeb09bafaea994f9911c0bc0b4ee63b22c5
ms.sourcegitcommit: da651fb36d26d0dfe796b988e86205f41f7dc5de
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2018
ms.locfileid: "48251792"
---
*Aplica-se ao: Microsoft Cloud App Security*


# <a name="windows-defender-advanced-threat-protection-integration-with-microsoft-cloud-app-security"></a>Integração da Proteção Avançada contra Ameaças do Windows Defender ao Microsoft Cloud App Security | Microsoft Docs

O Microsoft Cloud App Security integra-se ao Windows Defender ATP (Proteção Avançada contra Ameaças) nativamente, para simplificar a distribuição do Cloud Discovery, expandir as funcionalidades do Cloud Discovery para além de sua rede corporativa e habilitar a integração baseada em computador. 

[Windows Defender ATP (Proteção Avançada contra Ameaças)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection) é uma plataforma de segurança para proteção, detecção, investigação e resposta inteligentes. O Windows Defender ATP protege pontos de extremidade contra ameaças cibernéticas, detecta violações de dados e ataques avançados, automatiza os incidentes de segurança e melhora a postura de segurança.

O Microsoft Cloud App Security usa as informações do tráfego coletadas pelo Windows Defender ATP sobre os aplicativos e serviços de nuvem que estão sendo acessados em computadores Windows 10 gerenciados por TI. Isso permite que você execute o Cloud Discovery em qualquer computador na rede corporativa, que usa WiFi público, ao usar perfil móvel e por acesso remoto. Isso também permite a investigação baseada em computador: após identificar um usuário arriscado, será possível verificar todos os computadores que o usuário acessou para detectar potenciais riscos; se você identificar um computador arriscado, será possível verificar todos os usuários que o usaram para detectar potenciais riscos. Os logs dos seus pontos de extremidade roteados para o Cloud App Security fornecem informações de usuário para atividades de tráfego. A atividade de rede do Windows Defender ATP fornece contexto de dispositivo que pode ser emparelhado com o nome de usuário para fornecer um panorama completo de qual usuário executou qual atividade de qual computador em sua rede. O Microsoft Cloud App Security aproveita a integração nativa com o Windows Defender ATP para acessar dados sobre o aplicativo de nuvem e o tráfego de serviço de dispositivos Windows gerenciados. Essa integração perfeita não exige nenhuma implantação adicional e funciona prontamente. Não é necessário rotear nem espelhar o tráfego dos seus pontos de extremidade nem seguir etapas de integração complexas.

> [!NOTE]
> Deseja experimentar o Windows Defender ATP? [Inscreva-se para uma avaliação gratuita](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-assignaccess-abovefoldlink).
>


## <a name="prerequisites"></a>Pré-requisitos

- Licença do Microsoft Cloud App Security
- Licença do Windows Defender ATP
- Computadores Windows 10 executando o Windows Defender ATP RS5


## <a name="how-it-works"></a>Como funciona

Por conta própria, o Cloud App Security coleta logs dos seus pontos de extremidade usando [logs carregados por você](create-snapshot-cloud-discovery-reports.md) ou [configurando o upload de log automático](discovery-docker.md). Essa integração nativa permite que você use os logs que o agente do Windows Defender ATP cria quando é executado no Windows e monitora transações de rede e as utiliza para descoberta de TI sombra nos computadores Windows em sua rede. 

Para permitir que você execute o Cloud Discovery em outras plataformas, é melhor usar o [coletor de logs](discovery-docker.md) do Cloud App Security, assim como a integração com o Windows Defender ATP para monitorar seus computadores Windows 10.


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

Após integrar o Windows Defender ATP ao Cloud App Security, será possível investigar os dados de computador descobertos no painel do Cloud Discovery.

1. No portal do Cloud App Security, clique em **Cloud Discovery** e, em seguida, **Painel do Cloud Discovery**.
2. Na barra de navegação superior, em **Relatórios contínuos**, selecione **Usuários de ponto de extremidade do Win10**.
  ![Relatório do WD ATP](./media/win10-dashboard-report.png)
4. Observe que, na parte superior, número de computadores descobertos foi adicionado após a integração.
5. Clique na guia **Computadores**.
6. É possível fazer drill down de cada computador listado, e usar as guias para exibir os dados de investigação, e localizar as correlações entre os computadores e os usuários, endereços IP e aplicativos que estavam envolvidos em incidentes:
   - **Visão geral**
      - Transações: fornece informações sobre o número de transações que ocorreram no computador durante o período selecionado.
      - Tráfego total: fornece informações sobre o volume total de tráfego (em MB) durante o período selecionado.
     - Uploads: fornece informações sobre o volume total de tráfego (em MB) carregado pelo computador durante o período selecionado.
     - Downloads: fornece informações sobre o volume total de tráfego (em MB) baixado pelo computador durante o período selecionado.
   - **Aplicativos descobertos**<br>
  Lista todos os aplicativos descobertos que foram acessados pelo computador.
   - **Histórico de usuários**<br>
    Lista todos os usuários que se conectaram ao computador.
   - **Histórico de endereços IP**<br>
    Lista todos os endereços IP que foram atribuídos ao computador.
 ![Visão geral de computadores](./media/machines-overview.png)
 

Assim como acontece com qualquer outra fonte do Cloud Discovery, é possível exportar os dados do relatório de usuários de ponto de extremidade do Win10 para uma investigação adicional. 


## <a name="related-videos"></a>Vídeos Relacionados  
[Integrações do Cloud App Security + Proteção de Informações do Azure](https://channel9.msdn.com/Shows/Microsoft-Security/MCAS--AIP-Integrations)  

## <a name="see-also"></a>Consulte Também  
[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)   

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  

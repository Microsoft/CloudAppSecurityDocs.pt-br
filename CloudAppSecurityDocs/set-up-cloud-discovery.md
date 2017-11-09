---
title: Implante o Cloud Discovery com o Cloud App Security | Microsoft Docs
description: "Este tópico descreve o procedimento de configuração para colocar o Cloud Discovery em funcionamento."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/29/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: a9b5bd8d-305b-4e93-9a4c-a4683ea09080
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 0fa9125b611574d4f4fafb18c8bc649de82b1ad6
ms.sourcegitcommit: 1c9ed4923cb6b761aebd13a6caa3a6605412419a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2017
---
# <a name="set-up-cloud-discovery"></a>Configurar o Cloud Discovery
O Cloud Discovery analisa os logs de tráfego e os compara com o catálogo de aplicativos de nuvem do Cloud App Security de mais de 15 mil em aplicativos de nuvem que são classificados e pontuados com base em mais de 60 fatores de risco, a fim de fornecer visibilidade contínua do uso da nuvem, TI sombra e o risco que a TI sombra representa para sua organização.
 
## <a name="snapshot-and-continuous-risk-assessment-reports"></a>Relatórios contínuo e de instantâneo de avaliação de riscos 

Há dois tipos de relatórios que você pode gerar: 
- **Relatórios de instantâneo** fornecem visibilidade ad hoc em um conjunto de logs de tráfego que são carregados manualmente dos seus firewalls e proxies.
 
- **Relatórios contínuos** analisam todos os logs que são encaminhados da sua rede usando o coletor de logs do Cloud App Security. Eles oferecem maior visibilidade em todos os dados e identificam automaticamente usos anormais com o mecanismo de detecção de anomalias do Machine Learning ou por meio de políticas personalizadas que você definir.
 
## <a name="log-process-flow-from-raw-data-to-risk-assessment"></a>Fluxo do processo de log: dos dados brutos a avaliação de riscos  
O processo de geração de uma avaliação de riscos consiste nas seguintes etapas e leva de alguns minutos a várias horas, dependendo da quantidade de dados processados.  
  
-   **Carregar** – os logs do tráfego da Web da sua rede são carregados no portal.  
  
-   **Analisar** – O Cloud App Security analisa e extrai dados de tráfego dos logs de tráfego com um analisador dedicado para cada fonte de dados.  
  
-   **Analisar** – os dados de tráfego são examinados em relação ao Catálogo de aplicativos de nuvem para identificar mais de 15.000 aplicativos de nuvem e avaliar sua pontuação de risco. Os usuários ativos e os endereços IP também são identificados como parte da análise.  
  
-   **Gerar relatório** – Um relatório de avaliação de risco dos dados extraídos dos arquivos de log é gerado.   
 
 
>[!NOTE]
>- Os dados de relatórios contínuos são analisados duas vezes por dia.
>- O coletor de logs compacta os dados antes de os carregar. O tráfego de saída no coletor de logs representará 10% do tamanho dos logs de tráfego recebidos. 
 
## <a name="using-traffic-logs-for-cloud-discovery"></a>Usar os logs de tráfego para Cloud Discovery
O Cloud Discovery utiliza os dados em seus logs de tráfego. Quanto mais detalhado o log, melhor é a visibilidade obtida. O Cloud Discovery requer dados de tráfego da Web com os seguintes atributos:
- Data da transação
- IP de Origem
- Usuário de origem ‑ altamente recomendado
- Endereço IP de destino
- URL de destino **recomendada** (URLs fornecem maior precisão para detecção de aplicativos de nuvem que endereços IP)
- Quantidade total de dados (as informações dos dados são muito valiosas)
- Quantidade de dados carregados ou baixados (fornece informações sobre os padrões de uso dos aplicativos de nuvem)
- Ação executada (permitida/bloqueada)
 
O Cloud Discovery não pode mostrar ou analisar atributos que não estão incluídos em seus logs.
Por exemplo, o formato de log padrão do **Cisco ASA Firewall** não contém a **Quantidade de bytes carregados por transação**, **Username** nem a **URL de destino** (somente o IP de destino).
Portanto, esses atributos não serão exibidos nos dados do Cloud Discovery para esses logs e a visibilidade sobre os aplicativos de nuvem poderá ser limitada. Para firewalls Cisco ASA, é necessário definir o nível de informações para 6. 
 

Para gerar um relatório do Cloud Discovery com êxito, os logs de tráfego devem atender às seguintes condições:
1.  A fonte de dados tem suporte (consulte a lista abaixo).
2.  O formato de log corresponde ao formato padrão esperado (isso será verificado após o upload pela Ferramenta de log).
3.  Os eventos têm menos de 90 dias.
4.  O arquivo de log é válido e inclui informações de tráfego de saída.
 


## <a name="supported-firewalls-and-proxies"></a>Proxies e firewalls com suporte

- Barracuda - Firewall de aplicativo Web (W3C)
- Blue Coat Proxy SG – Log de acesso (W3C)
- Check Point
- Firewall Cisco ASA (Para firewalls Cisco ASA, é necessário definir o nível de informações para 6)
- Cisco ASA com FirePOWER
- Cisco IronPort WSA
- Cisco ScanSafe
- Cisco Meraki – log de URLs
- Clavister NGFW (Syslog)
- Dell Sonicwall
- Fortinet Fortigate
- Juniper SRX
- Juniper SSG
- McAfee Secure Web Gateway
- Microsoft Forefront Threat Management Gateway (W3C)
- Firewall da série Palo Alto
- Sophos SG
- Sophos Cyberoam
- Squid (Comum)
- Squid (Nativo)
- Websense – Soluções de segurança da Web – Relatório detalhado de investigação (CSV)
- Websense – Soluções de segurança da Web – Log de atividades de Internet (CEF)
- Zscaler

> [!NOTE]
> O Cloud Discovery oferece suporte a endereços IPv4 e IPv6.

Se seu log não tiver suporte, selecione **Outro** na **Fonte de dados** e especifique o dispositivo e o log que você está tentando carregar. O log será analisado pela equipe de analistas do Cloud App Security e você será notificado se o suporte para o tipo de log for adicionado. Como alternativa, você pode definir um analisador personalizado que corresponda ao seu formato. Para saber mais, confira [Usar analisador de log personalizado](custom-log-parser.md).


Atributos de dados (de acordo com a documentação do fornecedor):

|Fonte de dados|URL do aplicativo de destino|IP do aplicativo de destino|Nome de usuário|IP de Origem|Tráfego total|Bytes carregados|
|----|----|----|-----|----|----|----|
|Barracuda|**Sim**|**Sim**|**Sim**|**Sim**|Não|Não|
|Blue Coat|**Sim**|Não|**Sim**|**Sim**|**Sim**|**Sim**|
|Checkpoint|Não|**Sim**|Não|**Sim**|Não|Não|
|Cisco ASA|Não|**Sim**|Não|**Sim**|**Sim**|Não|
|Cisco ASA com FirePOWER|**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|
|Cisco FWSM|Não|**Sim**|Não|**Sim**|**Sim**|Não|
|Cisco Ironport WSA|**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|
|Cisco Meraki|**Sim**|**Sim**|Não|**Sim**|Não|Não||Cisco Scansafe|**Sim**|Não|**Sim**|**Sim**|**Sim**|**Sim**|
|Clavister NGFW (Syslog)|**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|
|Dell SonicWall|**Sim**|**Sim**|Não|**Sim**|**Sim**|**Sim**|
|Fortigate|Não|**Sim**|Não|**Sim**|**Sim**|**Sim**|
|Juniper SRX|Não|**Sim**|Não|**Sim**|**Sim**|**Sim**|
|Juniper SSG|Não|**Sim**|Não|**Sim**|**Sim**|**Sim**|
|McAfee SWG|**Sim**|Não|Não|**Sim**|**Sim**|**Sim**|
|MS TMG|**Sim**|Não|**Sim**|**Sim**|**Sim**|**Sim**|
|Redes de Palo Alto|**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|
|Sophos|**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|Não|
|Squid (Comum)|**Sim**|Não|**Sim**|**Sim**|Não|**Sim**|
|Squid (Nativo)|**Sim**|Não|**Sim**|**Sim**|Não|**Sim**|
|Websense – Relatório de detalhes investigativo (CSV)|**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|
|Websense – Log de atividades da Internet (CEF)|**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|
|Zscaler|**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|



## <a name="see-also"></a>Veja também
 
[Criar instantâneo de relatórios do Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

[Configurar upload de log automático para relatórios contínuos](configure-automatic-log-upload-for-continuous-reports.md)

[Trabalhando com os dados do Cloud Discovery](working-with-cloud-discovery-data.md)
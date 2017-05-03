---
title: Implantar o Cloud Discovery com o Cloud App Security | Microsoft Docs
description: "Este tópico descreve o procedimento de configuração para colocar o Cloud Discovery em funcionamento."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/30/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: a9b5bd8d-305b-4e93-9a4c-a4683ea09080
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: f9c86d2ce7b45a8de88ebba84ff8608b67117080
ms.sourcegitcommit: 7e9ae94cb4f90fbccaa84f19bdebb4652a425e45
translationtype: HT
---
# <a name="set-up-cloud-discovery"></a>Configurar o Cloud Discovery
O Cloud Discovery analisa os logs de tráfego e os compara com o catálogo de aplicativos de nuvem do Cloud App Security de mais de 13.000 em aplicativos de nuvem que são classificados e pontuados com base em mais de 50 atributos, a fim de fornecer visibilidade contínua do uso da nuvem, TI sombra e o risco que a TI sombra representa para sua organização.
O **Catálogo de aplicativos de nuvem** classifica o risco para seus aplicativos de nuvem com base em certificações regulatórias, padrões da indústria e práticas recomendadas. Quatro processos complementares são executados no Catálogo de aplicativos de nuvem para mantê-lo atualizado:
1.    Extração de dados automatizada diretamente do aplicativo de nuvem (para atributos como conformidade com SOC 2).
2.    Extração de dados avançada automatizada dos algoritmos do Cloud App Security (para atributos como cabeçalhos de segurança HTTP).
3.    Análise contínua da equipe de analistas de nuvem do Cloud App Security (para atributos como criptografia em repouso).
4.    Solicitações de revisão baseada no cliente, com base nas solicitações de envio de cliente para alterações no Catálogo de aplicativos de nuvem. Todas as solicitações são revisadas por nossa equipe de analistas de nuvem e atualizadas com base em suas descobertas.
  
## <a name="cloud-discovery-data-anonymization"></a>Anonimização de dados do Cloud Discovery

A anonimização de dados do Cloud Discovery permite proteger a privacidade do usuário. Após o log de dados ser carregado no portal do Cloud App Security, o log é limpo e todas as informações de nome de usuário são substituídas por nomes de usuário criptografados. Dessa forma, todas as atividades na nuvem são mantidas anônimas. Para obter mais informações, consulte [Anonimização do Cloud Discovery](cloud-discovery-anonymizer.md).

## <a name="snapshot-and-continuous-risk-assessment-reports"></a>Relatórios contínuo e de instantâneo de avaliação de riscos 

Há dois tipos de relatórios que você pode gerar: 
- **Relatórios de instantâneo** fornecem visibilidade ad hoc em um conjunto de logs de tráfego que são carregados manualmente dos seus firewalls e proxies.
 
- **Relatórios contínuos** analisam todos os logs que são encaminhados da sua rede usando o coletor de logs do Cloud App Security. Eles oferecem maior visibilidade em todos os dados e identificam automaticamente usos anormais com o mecanismo de detecção de anomalias do Machine Learning ou por meio de políticas personalizadas que você definir.
 
## <a name="log-process-flow-from-raw-data-to-risk-assessment"></a>Fluxo do processo de log: dos dados brutos a avaliação de riscos  
O processo de geração de uma avaliação de riscos consiste nas seguintes etapas e leva de alguns minutos a várias horas, dependendo da quantidade de dados processados.  
  
-   **Carregar** – os logs do tráfego da Web da sua rede são carregados no portal.  
  
-   **Analisar** – O Cloud App Security analisa e extrai dados de tráfego dos logs de tráfego com um analisador dedicado para cada fonte de dados.  
  
-   **Examinar** – os dados de tráfego são examinados em relação ao Catálogo de aplicativos de nuvem para identificar mais de 13.000 aplicativos de nuvem e avaliar sua pontuação de risco. Os usuários ativos e os endereços IP também são identificados como parte da análise.  
  
-   **Gerar relatório** – Um relatório de avaliação de risco dos dados extraídos dos arquivos de log é gerado.   
 
 
>[!NOTE]
>Os dados de relatórios contínuos são analisados duas vezes por dia.
 
## <a name="using-traffic-logs-for--cloud-discovery"></a>Usando os logs de tráfego para o Cloud Discovery
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
- Blue Coat Proxy SG – Log de acesso (W3C)
- Check Point
- Firewall Cisco ASA (Para firewalls Cisco ASA, é necessário definir o nível de informações para 6)
- Cisco IronPort WSA
- Cisco ScanSafe
- Cisco Meraki – log de URLs
- Dell Sonicwall
- Fortinet Fortigate
- Juniper SRX
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


Se seu log não tiver suporte, selecione **Outro** na **Fonte de dados** e especifique o dispositivo e o log que você está tentando carregar. O log será analisado pela equipe de analistas do Cloud App Security e você será notificado se o suporte para o tipo de log for adicionado. 


Atributos de dados (de acordo com a documentação do fornecedor):

|Fonte de dados|URL do aplicativo de destino|IP do aplicativo de destino|Nome de usuário|IP de Origem|Tráfego total|Bytes carregados|
|----|----|----|-----|----|----|----|
|Blue Coat|**Sim**|Não|**Sim**|**Sim**|**Sim**|**Sim**|
|Checkpoint|Não|**Sim**|Não|**Sim**|Não|Não|
|Cisco ASA|Não|**Sim**|Não|**Sim**|**Sim**|Não|
|Cisco FWSM|Não|**Sim**|Não|**Sim**|**Sim**|Não|
|Cisco Ironport WSA|**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|
|Cisco Scansfe|**Sim**|Não|**Sim**|**Sim**|**Sim**|**Sim**|
|Dell SonicWall|**Sim**|**Sim**|Não|**Sim**|**Sim**|**Sim**|
|Fortigate|Não|**Sim**|Não|**Sim**|**Sim**|**Sim**|
|Juniper SRX|Não|**Sim**|Não|**Sim**\*|**Sim**|**Sim**|
|McAfee SWG|**Sim**|Não|Não|**Sim**|**Sim**|**Sim**|
|Meraki|**Sim**|**Sim**|Não|**Sim**|Não|Não|
|MS TMG|**Sim**|Não|**Sim**|**Sim**|**Sim**|**Sim**|
|Redes de Palo Alto|**Sim**|**Sim**|**Sim**|**Sim**\*|**Sim**|**Sim**|
|Sophos|**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|Não|
|Websense – Relatório de detalhes investigativo (CSV)|**Sim**|Não|Não|**Sim**|Não|Não|
|Websense – Log de atividades da Internet (CEF)|**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|
|Zscaler|**Sim**|Não|**Sim**|Não|**Sim**|**Sim**|

\* Cloud Discovery dá suporte a IPv6.

## <a name="see-also"></a>Veja também
 
[Criar instantâneo de relatórios do Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

[Configurar upload de log automático para relatórios contínuos](configure-automatic-log-upload-for-continuous-reports.md)

[Trabalhando com os dados do Cloud Discovery](working-with-cloud-discovery-data.md)
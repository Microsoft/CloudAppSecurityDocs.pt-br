---
title: Configurar o upload automático de logs para relatórios contínuos no Cloud App Security
description: Este artigo descreve o processo de configuração do upload automático de logs para relatórios contínuos no Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: barbkess
ms.date: 04/04/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: c75ba963-ad5a-48e6-8d5d-610fc6e0b990
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 99cca2a7a5fbc8bf57eb7a211bd32a28b102a78a
ms.sourcegitcommit: 28b3ab878b1fc403d2c3b617e989f711320530d4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59233489"
---
# <a name="configure-automatic-log-upload-for-continuous-reports"></a>Configurar upload de log automático para relatórios contínuos

*Aplica-se a: Microsoft Cloud App Security*

Os coletores de log permitem que você automatize facilmente o upload de logs da sua rede. O coletor de log é executado em sua rede e recebe logs por Syslog ou FTP. Cada log é automaticamente processado, compactado e transmitido para o portal. Os logs de FTP são carregados para o Microsoft Cloud App Security após o arquivo concluir a transferência do FTP para o coletor de logs. Para o Syslog, o Coletor de Logs grava os logs recebidos no disco. Em seguida, o coletor carrega o arquivo no Cloud App Security quando o tamanho do arquivo é maior que 40 KB. 

Depois que um log é carregado no Cloud App Security, ele é movido para um diretório de backup. O diretório de backup armazena os últimos 20 logs. Quando novos logs chegam, os antigos são excluídos. Sempre que o espaço em disco do coletor de logs está cheio, o coletor de logs remove os novos logs até que tenha mais espaço livre em disco. Você receberá um aviso na guia **Coletores de logs** das configurações **Fazer upload de logs automaticamente** quando isso acontecer.

Antes de configurar a coleta automática de arquivos de log, verifique se o log corresponde ao tipo de log esperado. Você deseja ter certeza de que o Cloud App Security pode analisar seu arquivo específico. Para obter mais informações, confira [Usando logs de tráfego para o Cloud Discovery](create-snapshot-cloud-discovery-reports.md#log-format).


> [!NOTE]
>-  O Cloud App Security dá suporte para encaminhamento de logs do servidor SIEM para o Coletor de Log, supondo que os logs estão sendo encaminhados em seu formato original. No entanto, é altamente recomendável que você integre o coletor de logs diretamente ao seu firewall e/ou proxy.
>- O coletor de logs compacta os dados antes de os carregar. O tráfego de saída no coletor de logs representará 10% do tamanho dos logs de tráfego recebidos. 
>-  Se o coletor de logs encontrar problemas, você receberá um alerta quando deixar de receber dados por 48 horas.
>

## <a name="deployment-modes"></a>Modos de implantação

O coletor de log dá suporte a dois modos de implantação:

-   **Contêiner**: Executado como uma imagem do Docker no [Ubuntu local](discovery-docker-ubuntu.md), no [Ubuntu no Azure](discovery-docker-ubuntu-azure.md) ou no [RHEL local](discovery-docker-ubuntu.md). 

-   **Solução de virtualização**:  É executado como uma imagem no hipervisor Hyper-V ou VMware (preterido)




## <a name="next-steps"></a>Próximas etapas
 
[Criar instantâneo de relatórios do Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

[Trabalhando com os dados do Cloud Discovery](working-with-cloud-discovery-data.md)


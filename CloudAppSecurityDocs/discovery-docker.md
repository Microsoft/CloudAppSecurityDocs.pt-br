---
title: Configurar o upload de log automático para relatórios contínuos | Microsoft Docs
description: Este tópico descreve o processo de configuração de upload automático de logs para relatórios contínuos no Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 6/11/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: c75ba963-ad5a-48e6-8d5d-610fc6e0b990
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 06b011e28a293c09f6d3f40e904252178045431d
ms.sourcegitcommit: 0ac08ca7b3140b79f1d36ff7152476c188fa12b3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44143557"
---
*Aplica-se ao: Microsoft Cloud App Security*


# <a name="configure-automatic-log-upload-for-continuous-reports"></a>Configurar upload de log automático para relatórios contínuos


Os coletores de log permitem que você automatize facilmente o upload de logs da sua rede. O coletor de log é executado em sua rede e recebe logs por Syslog ou FTP. Cada log é automaticamente processado, compactado e transmitido para o portal. Os logs de FTP são carregados para o Microsoft Cloud App Security após o arquivo concluir a transferência do FTP para o coletor de logs.  Para Syslog, o coletor de logs grava os logs recebidos no disco e carrega o arquivo para o Cloud App Security quando o tamanho do arquivo é maior do que 40 KB.

Depois que um log for carregado no Cloud App Security, ele é movido para um diretório de backup que armazena os últimos 20 logs a qualquer momento. Quando novos logs chegam, os antigos são excluídos. Quando o espaço em disco do coletor de log está cheio, o coletor de log descarta novos logs até que tenha mais espaço livre em disco. Quando isso acontecer, você receberá um aviso na guia **Coletores de logs** das configurações **Carregar logs automaticamente**.

Antes de configurar a coleta de arquivos de log automática, verifique se o log corresponde ao tipo de log esperado para garantir que o Cloud App Security possa analisar seu arquivo específico.

> [!NOTE]
>-  O Cloud App Security dá suporte para encaminhamento de logs do servidor SIEM para o Coletor de Log, supondo que os logs estão sendo encaminhados em seu formato original. No entanto, é altamente recomendável que você integre o coletor de logs diretamente ao seu firewall e/ou proxy.
>- O coletor de logs compacta os dados antes de os carregar. O tráfego de saída no coletor de logs representará 10% do tamanho dos logs de tráfego recebidos. 

## <a name="deployment-modes"></a>Modos de implantação

O Coletor de logs dá suporte a dois modos de implantação:

-   **Contêiner**: é executado como uma imagem do Docker no [Ubuntu no local](discovery-docker-ubuntu.md), no [Ubuntu no Azure](discovery-docker-ubuntu-azure.md) ou [RHEL local](discovery-docker-ubuntu.md). 

-   **Solução de virtualização**: [é executado como uma imagem no hipervisor do Hyper-V ou do VMware](configure-automatic-log-upload-for-continuous-reports.md)




## <a name="see-also"></a>Consulte também
 
[Criar instantâneo de relatórios do Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

[Trabalhando com os dados do Cloud Discovery](working-with-cloud-discovery-data.md)


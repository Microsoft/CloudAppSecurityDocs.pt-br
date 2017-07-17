---
title: "Configurar o upload de log automático para relatórios contínuos | Microsoft Docs"
description: "Este tópico descreve o processo de configuração do upload automático de log para relatórios contínuos no Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 7/9/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: c75ba963-ad5a-48e6-8d5d-610fc6e0b990
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 9f17366c62b202432d8b0c750290b4915f64c929
ms.sourcegitcommit: b2e3af9d0a62dcb6410cc3992183c2888bdf6a2f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2017
---
# Configurar upload de log automático para relatórios contínuos
<a id="configure-automatic-log-upload-for-continuous-reports" class="xliff"></a>


Os coletores de log permitem que você automatize facilmente o upload de logs da sua rede. O coletor de log é executado em sua rede e recebe logs por Syslog ou FTP. Cada log é automaticamente processado, compactado e transmitido para o portal. Logs de FTP são carregados no Cloud App Security após o arquivo finalizar a transferência por FTP para o coletor de log.  Para Syslog, o coletor de log grava os logs recebidos para o disco e carrega o arquivo no Cloud App Security quando o tamanho do arquivo é maior que 40 KB.

Depois que um log for carregado no Cloud App Security, ele é movido para um diretório de backup que armazena os últimos 20 logs a qualquer momento. Quando novos logs chegam, os antigos são excluídos. Quando o espaço em disco do coletor de log está cheio, o coletor de log descarta novos logs até que tenha mais espaço livre em disco.

Antes de configurar a coleta de arquivos de log automática, verifique se o log corresponde ao tipo de log esperado para garantir que o Cloud App Security possa analisar seu arquivo específico.

> [!NOTE]
> O Cloud App Security dá suporte para encaminhamento de logs do servidor SIEM para o Coletor de Log, supondo que os logs estão sendo encaminhados em seu formato original. No entanto, é altamente recomendável que o coletor de log seja integrado diretamente com seu firewall e/ou proxy.

## Modos de implantação
<a id="deployment-modes" class="xliff"></a>

O coletor de log dá suporte a dois modos de implantação:

-   **Contêiner** (*baseado no Docker CE*): é executado como uma imagem do Docker no [Windows](discovery-docker-windows.md) e no [Ubuntu](discovery-docker-ubuntu.md), localmente ou no Azure.

-   **Solução de virtualização** (*em substituição*): [é executada como uma imagem em um hipervisor VMware ou Hyper-V](configure-automatic-log-upload-for-continuous-reports.md)




## Consulte também
<a id="see-also" class="xliff"></a>
 
[Criar instantâneo de relatórios do Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

[Trabalhando com os dados do Cloud Discovery](working-with-cloud-discovery-data.md)


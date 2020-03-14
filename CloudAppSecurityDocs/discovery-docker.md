---
title: Configurar o carregamento de log automático para relatórios contínuos no Cloud App Security
description: Este artigo descreve o processo de configuração do carregamento de log automático para relatórios contínuos no Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 7/22/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: fb79f5515799ad93e456bb3a97bfa26d16416e5c
ms.sourcegitcommit: 4f3883a9e85d0aaf2802b10433b221c3f1838d88
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79285260"
---
# <a name="configure-automatic-log-upload-for-continuous-reports"></a>Configurar upload de log automático para relatórios contínuos

*Aplica-se a: Microsoft Cloud App Security*

Os coletores de log permitem que você automatize facilmente o upload de logs da sua rede. O coletor de log é executado em sua rede e recebe logs por Syslog ou FTP. Cada log é automaticamente processado, compactado e transmitido para o Portal. Os logs de FTP são carregados para Microsoft Cloud App Security depois que o arquivo terminar a transferência de FTP para o coletor de logs. Para o syslog, o coletor de logs grava os logs recebidos no disco. Em seguida, o coletor carregará o arquivo para Cloud App Security quando o tamanho do arquivo for maior do que 40 KB.

Depois que um log é carregado para Cloud App Security, ele é movido para um diretório de backup. O diretório de backup armazena os últimos 20 logs. Quando novos logs chegam, os antigos são excluídos. Sempre que o espaço em disco do coletor de logs estiver cheio, o coletor de logs descartará novos logs até que ele tenha mais espaço livre em disco. Você receberá um aviso na guia **coletores de log** dos **logs de upload** , configurações automaticamente quando isso acontecer.

Antes de configurar a coleta automática de arquivos de log, verifique se o log corresponde ao tipo de log esperado. Você quer ter certeza de que Cloud App Security pode analisar o arquivo específico. Para obter mais informações, consulte [usando logs de tráfego para Cloud Discovery](create-snapshot-cloud-discovery-reports.md#log-format).

> [!NOTE]
>
> * O Cloud App Security dá suporte para encaminhamento de logs do servidor SIEM para o Coletor de Log, supondo que os logs estão sendo encaminhados em seu formato original. No entanto, é altamente recomendável que o coletor de log seja integrado diretamente com seu firewall e/ou proxy.
> * O coletor de logs compacta os dados antes de carregá-los. O tráfego de saída no coletor de logs será de 10% do tamanho dos logs de tráfego que recebe.
> * Se o coletor de logs encontrar problemas, você receberá um alerta depois que os dados não tiverem sido recebidos por 48 horas.

## <a name="deployment-modes"></a>Modos de implantação

O coletor de log dá suporte a dois modos de implantação:

* **Contêiner**: é executado como uma imagem do Docker no [Windows](discovery-docker-windows.md), [Ubuntu local](discovery-docker-ubuntu.md), [Ubuntu no Azure](discovery-docker-ubuntu-azure.md), [RHEL no local](discovery-docker-ubuntu.md) ou CentOS.

* **Dispositivo virtual**: é executado como uma imagem sobre o Hyper-V ou o hipervisor do VMware (preterido)

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Criar instantâneo de relatórios do Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

> [!div class="nextstepaction"]
> [Trabalhando com os dados do Cloud Discovery](working-with-cloud-discovery-data.md)

---
title: Configurar o upload automático de logs para relatórios contínuos no Cloud App Security
description: Este artigo descreve o processo de configuração do upload automático de logs para relatórios contínuos no Cloud App Security.
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
ms.openlocfilehash: 73b9f8a7ea1bd3f2b93b4199b58cfb5178f13edc
ms.sourcegitcommit: 72c96b9b2b9f6555e5e20749ebe61593072b1d50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84487756"
---
# <a name="configure-automatic-log-upload-for-continuous-reports"></a>Configurar upload de log automático para relatórios contínuos

*Aplica-se a: Microsoft Cloud App Security*

Os coletores de log permitem que você automatize facilmente o upload de logs da sua rede. O coletor de log é executado em sua rede e recebe logs por Syslog ou FTP. Cada log é automaticamente processado, compactado e transmitido para o portal. Os logs de FTP são carregados para o Microsoft Cloud App Security após o arquivo concluir a transferência do FTP para o coletor de logs. Para o Syslog, o Coletor de Logs grava os logs recebidos no disco. Em seguida, o coletor carrega o arquivo no Cloud App Security quando o tamanho do arquivo é maior que 40 KB.

Depois que um log é carregado no Cloud App Security, ele é movido para um diretório de backup. O diretório de backup armazena os últimos 20 logs. Quando novos logs chegam, os antigos são excluídos. Sempre que o espaço em disco do coletor de logs está cheio, o coletor de logs remove os novos logs até que tenha mais espaço livre em disco. Você receberá um aviso na guia **Coletores de logs** das configurações **Fazer upload de logs automaticamente** quando isso acontecer.

Antes de configurar a coleta automática de arquivos de log, verifique se o log corresponde ao tipo de log esperado. Você deseja ter certeza de que o Cloud App Security pode analisar seu arquivo específico. Para obter mais informações, confira [Usando logs de tráfego para o Cloud Discovery](create-snapshot-cloud-discovery-reports.md#log-format).

> [!NOTE]
>
> * O Cloud App Security dá suporte para encaminhamento de logs do servidor SIEM para o Coletor de Log, supondo que os logs estão sendo encaminhados em seu formato original. No entanto, é altamente recomendável que você integre o coletor de logs diretamente ao seu firewall e/ou proxy.
> * O coletor de logs compacta os dados antes de eles serem carregados. O tráfego de saída no coletor de logs representará 10% do tamanho dos logs de tráfego recebidos.
> * Se o coletor de logs encontrar problemas, você receberá um alerta quando deixar de receber dados por 48 horas.

## <a name="deployment-modes"></a>Modos de implantação

O Coletor de logs dá suporte a dois modos de implantação:

* **Contêiner**: é executado como uma imagem do Docker no [Windows](discovery-docker-windows.md), [Ubuntu local](discovery-docker-ubuntu.md), [Ubuntu no Azure](discovery-docker-ubuntu-azure.md), [RHEL no local](discovery-docker-ubuntu.md) ou CentOS.

* **Dispositivo virtual**: é executado como uma imagem sobre o Hyper-V ou o hipervisor do VMware (preterido)

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Trabalhando com dados do Cloud Discovery](working-with-cloud-discovery-data.md)

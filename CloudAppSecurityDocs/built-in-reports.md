---
title: Como gerar relatórios no Microsoft Cloud App Security | Microsoft Docs
description: Este tópico fornece instruções para gerar relatórios de gerenciamento de dados no Microsoft Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 6/10/2018
ms.topic: article
ms.prod: ''
ms.app: cloud-app-security
ms.technology: ''
ms.assetid: 0dcc3c35-f787-4822-84c6-d4dff897dd6c
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 3265f1fe6d5a75ac65ec89142c571583cb5e098a
ms.sourcegitcommit: 41fbc8e235befd240ad7a1eed52339cfafb5d906
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/10/2018
ms.locfileid: "35251694"
---
*Aplica-se ao: Microsoft Cloud App Security*



# <a name="generate-data-management-reports"></a>Gerar relatórios de gerenciamento de dados

O Microsoft Cloud App Security permite gerar relatórios que oferecem uma visão geral dos arquivos nos seus aplicativos de nuvem.

Como gerar esses relatórios

1. Vá para **Arquivos**. 
2. No canto superior direito, clique nos três pontos e em **Relatórios de gerenciamento de dados**, selecione um dos seguintes relatórios.

   ![relatórios](./media/reports.png) I
## <a name="data-sharing-overview"></a>Visão geral do compartilhamento de dados 

Isso lista o número de arquivos armazenados nos aplicativos de nuvem, divididos de acordo com as permissões de acesso. O compartilhamento se tornou fácil com os aplicativos de nuvem devido à facilidade de acesso e onipresença. Um arquivo que não é compartilhado com ninguém exceto seu proprietário é chamado de um arquivo particular. Se o arquivo for compartilhado, o Cloud App Security diferenciará entre quatro tipos de estados: <br> - Um arquivo da compartilhado publicamente (Web) pode ser acessado sem qualquer autenticação, até mesmo por um resultado de mecanismo de pesquisa.<br> - Um arquivo compartilhado publicamente é um arquivo que pode ser acessado sem qualquer autenticação usando um link.<br> - Um arquivo compartilhado externamente é um arquivo que pode ser acessado por pessoas fora da organização após se autenticarem no aplicativo de nuvem.<br> – Um arquivo compartilhado internamente é um arquivo que pode ser acessado por todos ou por alguns usuários da organização.

## <a name="outbound-sharing-by-domain"></a>Compartilhamento de saída por domínio

Isso lista os domínios com os quais os arquivos corporativos são compartilhados por seus funcionários. Para cada domínio, o relatório detalha quais usuários da corporação estão compartilhando arquivos com esse domínio, quais arquivos foram compartilhados e quais são os parceiros com quem os arquivos foram compartilhados. É recomendável que você gerencie o compartilhamento com esses domínios por meio da guia Arquivos na página do aplicativo de cada aplicativo relevante.

## <a name="owners-of-shared-files"></a>Proprietários de arquivos compartilhados

Isso lista os usuários que estão compartilhando arquivos corporativos com o mundo exterior. Os arquivos compartilhados externamente são compartilhados com parceiros externos específicos. Os arquivos compartilhados publicamente são acessíveis para todas as pessoas na Internet por meio de um link privado e podem ser localizados apenas por usuários que são explicitamente expostos ao link. Os arquivos compartilhados publicamente (Internet) podem ser acessados por qualquer pessoa na Internet, até mesmo por meio de um resultado de mecanismo de pesquisa. Se você encontrar usuários que compartilham uma quantidade excessiva de arquivos, será recomendável que você investigue a natureza dessas permissões de compartilhamento excessivas usando a guia Arquivos e entre em contato com esses usuários para compreender melhor o uso do compartilhamento externo.


  
## <a name="see-also"></a>Consulte Também 
[Controle](control.md)   

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
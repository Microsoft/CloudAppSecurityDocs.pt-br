---
title: Como gerar relatórios no Microsoft Cloud App Security | Microsoft Docs
description: Este tópico fornece instruções para gerar relatórios de gerenciamento de dados no Microsoft Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/11/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 0dcc3c35-f787-4822-84c6-d4dff897dd6c
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 7684e6e3172076d8f7e8a4d69b1ddd70d322a200
ms.sourcegitcommit: 82052a88acbc33893f7b9e0d10cc2e8c652ef003
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2018
ms.locfileid: "49349501"
---
*Aplica-se ao: Microsoft Cloud App Security*



# <a name="generate-data-management-reports"></a>Gerar relatórios de gerenciamento de dados

O Microsoft Cloud App Security permite gerar relatórios que oferecem uma visão geral dos arquivos nos seus aplicativos de nuvem.

Como gerar esses relatórios

1. Vá para **Arquivos**. 
2. No canto superior direito, clique nos três pontos e em **Relatórios de gerenciamento de dados**, selecione um dos seguintes relatórios.

 ![relatórios](./media/reports.png)

## <a name="data-sharing-overview"></a>Visão geral do compartilhamento de dados 

Este relatório lista o número de arquivos armazenados nos aplicativos de nuvem, divididos de acordo com as permissões de acesso. O compartilhamento se tornou muito fácil com serviços de nuvem devido à facilidade de acesso e onipresença. Um **Arquivo particular** não é compartilhado com ninguém exceto com seu proprietário. Se o arquivo for compartilhado, o Cloud App Security diferenciará entre quatro tipos de estados:
- Um arquivo **Compartilhado publicamente (Internet)** é um arquivo que pode ser acessado sem qualquer autenticação, até mesmo por um resultado de mecanismo de pesquisa.
 - Um arquivo **Compartilhado publicamente** é um arquivo que pode ser acessado sem qualquer autenticação, usando um link.
 - Um arquivo **Compartilhado externamente** é um arquivo que pode ser acessado por pessoas fora da organização, após se autenticarem no aplicativo de nuvem.
- Um arquivo **Compartilhado internamente** é um arquivo que pode ser acessado por todos ou por alguns usuários da sua organização.

## <a name="outbound-sharing-by-domain"></a>Compartilhamento de saída por domínio

Este relatório lista os domínios com os quais os arquivos corporativos são compartilhados por seus funcionários. Para cada domínio, o relatório mostra quais usuários estão compartilhando arquivos com aquele domínio. O relatório também mostra quais arquivos são compartilhados e com quem os arquivos dos colaboradores são compartilhados. É recomendável que você gerencie o compartilhamento com esses domínios. Você pode gerenciar o compartilhamento por meio da guia arquivos na página do aplicativo de cada aplicativo relevante.

## <a name="owners-of-shared-files"></a>Proprietários de arquivos compartilhados

Isso lista os usuários que estão compartilhando arquivos corporativos com o mundo exterior. Os arquivos compartilhados externamente são compartilhados com colaboradores externos específicos. Os arquivos compartilhados publicamente são acessíveis para qualquer pessoa na Internet, por meio de um link privado. Esses arquivos podem ser encontrados somente por pessoas que são explicitamente expostas ao link. Os arquivos compartilhados publicamente (Internet) podem ser acessados por qualquer pessoa na Internet, até mesmo por meio de um resultado de mecanismo de pesquisa. Se você encontrar usuários que compartilham um número excessivo de arquivos, é recomendável investigar o motivo. Você pode investigar usando a guia arquivos e, em seguida, entre em contato com esses usuários para compreender melhor o uso do compartilhamento externo.


  
## <a name="next-steps"></a>Próximas etapas 
[Controle](control.md)   

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
---
title: Usar o mecanismo RegEx no Cloud App Security para políticas de inspeção de conteúdo
description: Este artigo fornece instruções de uso do RegEx para correspondência de padrões em políticas do Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: barbkess
ms.date: 12/14/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: dc8b87e5-e6c1-4a65-ab8c-067fb527fce4
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 07085a2c2e8a27e6e6ad35d9e088a95f8d543522
ms.sourcegitcommit: 8ef0438fa35916c48625ff750cb85e9628d202f2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56281110"
---
# <a name="working-with-the-regex-engine"></a>Trabalhando com o mecanismo RegEx

*Aplica-se a: Microsoft Cloud App Security*
 
Este artigo fornece instruções de uso do RegEx para correspondência de padrões em políticas do Cloud App Security.

## <a name="regular-expressions-in-cloud-app-security"></a>Expressões regulares no Cloud App Security

As políticas de inspeção de conteúdo do Microsoft Cloud App Security usam o RegEx para correspondência de padrões. A inspeção de conteúdo pode ser aplicada como parte das políticas de arquivos.

### <a name="testing-regular-expressions"></a>Testando expressões regulares

Para testar expressões regulares, use os seguintes sites:  
  
- [https://regexpal.com/](https://regexpal.com/) – selecione **Sem distinção entre maiúsculas e minúsculas**.  
  
- [https://regex101.com/](https://regex101.com/) – fornece uma análise detalhada do RegEx.  

### <a name="limitations-of-regular-expressions-in-cloud-app-security"></a>Limitações de expressões regulares no Cloud App Security

As limitações a seguir são impostas em expressões regulares personalizadas:  
  
- A pesquisa nunca faz distinção entre maiúsculas e minúsculas  

- Quantificadores permitidos: {n,m} em que n, m < 10  
  
- Todos os grupos devem ser de não captura, por exemplo: (?:xxx)  
  
     Em vez de (group) use (?:group)  
  
- Quantificadores não permitidos: *, +, {n,}  
  
     Em vez de * use {0,9}  
  
     Em vez de + use {1,9}  
  
- Referência inversa não permitida: \\<número\> ou \k\<nome>  
  
### <a name="example-expressions"></a>Expressões de exemplo  

A tabela a seguir fornece expressões de exemplo e indica se elas são correspondentes ou não.

|                                                               |                                                               |                                    |
|---------------------------------------------------------------|---------------------------------------------------------------|------------------------------------|
|              <strong>Expressão regular</strong>              |                     <strong>Dados</strong>                     |      <strong>Correspondências</strong>      |
|            Colou?r (?:black&#124;blue&#124;white)             |   Cor preta<br /><br /> Cor branca<br /><br /> Cor vermelha   | Sim<br /><br /> Sim<br /><br /> Não |
|           [a-z0-9]{1,9}@[a-z0-9]{1,9}\\.[a-z]{2,3}            | Some1@abc.com<br /><br /> user@host.org<br /><br /> @bad.com  | Sim<br /><br /> Sim<br /><br /> Não |
| 20\d{2}-(?:0[1-9]&#124;1[0-2])-(?:[0-2][0-9]&#124;30&#124;31) |   2015-12-31<br /><br /> 2015-01-09<br /><br /> 1999-12-31    | Sim<br /><br /> Sim<br /><br /> Não |
|                       d.n't\s{0,10}c.r.                       | Não importa<br /><br /> D!n'tcor0<br /><br /> Não importa | Sim<br /><br /> Sim<br /><br /> Não |

## <a name="check-out-this-video"></a>Confira este vídeo!

[Trabalhando com o mecanismo Regex](https://channel9.msdn.com/Shows/Microsoft-Security/Microsoft-Cloud-App-Security-Working-with-the-Regex-Engine)

## <a name="next-steps"></a>Próximas etapas

[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/)  
  

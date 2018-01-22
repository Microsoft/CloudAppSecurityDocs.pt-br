---
title: "Usando o mecanismo RegEx para políticas de inspeção de conteúdo | Microsoft Docs"
description: "Este tópico fornece instruções para usar RegEx para correspondência de padrão de políticas do Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/15/2018
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: dc8b87e5-e6c1-4a65-ab8c-067fb527fce4
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 1f6ee1a96a7f65c903fe6e0978fd9a31d850697e
ms.sourcegitcommit: 458e936e1ac548eda37e9bf955b439199bbdd018
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2018
---
# <a name="working-with-the-regex-engine"></a>Trabalhando com o mecanismo RegEx
 
As políticas de inspeção de conteúdo do Cloud App Security utilizam o RegEx para a correspondência de padrões. A inspeção de conteúdo pode ser aplicada como parte das políticas de arquivos. Para testar expressões regulares, você pode usar os seguintes sites:  
  
-   [http://regexpal.com/](http://regexpal.com/)  
  
     Verifique se você selecionou **Sem distinção entre maiúsculas e minúsculas**.  
  
-   [https://regex101.com/](https://regex101.com/)  
  
     Fornece uma análise detalhada do RegEx.  
  
As limitações a seguir são impostas em expressões regulares personalizadas:  
  
-   A pesquisa nunca faz distinção entre maiúsculas e minúsculas  
   
-   Quantificadores permitidos: {n,m} em que n, m < 10  
  
-   Todos os grupos devem ser de não captura, por exemplo: (?:xxx)  
  
     Em vez de (group) use (?:group)  
  
-   Quantificadores não permitidos: *, +, {n,}  
  
     Em vez de *, use {0,9}  
  
     Em vez de +, use {1,9}  
  
-   Referência inversa não permitida: \\<número\> ou \k\<nome>  
  
Expressões de exemplo  
  
||||  
|-|-|-|  
|**Expressão regular**|**Dados**|**Correspondências**|  
|Colou?r (?:black&#124;blue&#124;white)|Cor preta<br /><br /> Cor branca<br /><br /> Cor vermelha|Sim<br /><br /> Sim<br /><br /> Não|  
|[a-z0-9]{1,9}@[a-z0-9]{1,9}\\.[a-z]{2,3}|Some1@abc.com<br /><br /> user@host.org<br /><br /> @bad.com|Sim<br /><br /> Sim<br /><br /> Não|  
|20\d{2}-(?:0[1-9]&#124;1[0-2])-(?:[0-2][0-9]&#124;30&#124;31)|2015-12-31<br /><br /> 2015-01-09<br /><br /> 1999-12-31|Sim<br /><br /> Sim<br /><br /> Não|  
|d.n't\s{0,10}c.r.|Não importa<br /><br /> D!n'tcor0<br /><br /> Não importa|Sim<br /><br /> Sim<br /><br /> Não|  
 

## <a name="see-also"></a>Consulte Também  
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  

## <a name="check-out-this-video"></a>Confira este vídeo!
[Trabalhando com o mecanismo Regex](https://channel9.msdn.com/Shows/Microsoft-Security/Microsoft-Cloud-App-Security-Working-with-the-Regex-Engine)    
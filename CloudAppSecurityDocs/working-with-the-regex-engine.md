---
title: "Usando o mecanismo RegEx para políticas de inspeção de conteúdo | Microsoft Docs"
description: "Este tópico fornece instruções para usar RegEx para correspondência de padrão de políticas do Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/26/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: dc8b87e5-e6c1-4a65-ab8c-067fb527fce4
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 0b635a9d2f2e5befa53abea6b7d59876def0a115
ms.sourcegitcommit: 3bacec2f1e5b7bd34175ab5975f7be74792007e4
translationtype: HT
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
 

## <a name="see-also"></a>Veja também  
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
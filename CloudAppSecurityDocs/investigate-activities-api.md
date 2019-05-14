---
title: Investigar atividades usando a API - Cloud App Security | Microsoft Docs
description: Este artigo fornece informações sobre como usar a API para investigar a atividade do usuário no Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: rkarlin
ms.date: 03/26/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 0f2f971d-10e3-496d-8004-96d9fad71cae
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: db4e10c7ecc8e82795d3a75fb915757bfada6bb9
ms.sourcegitcommit: 9f0c562322394a3dfac7f1d84286e673276a28b1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65568289"
---
# <a name="investigate-activities-using-the-api"></a>Investigar atividades usando a API

*Aplica-se a: Microsoft Cloud App Security*

Microsoft Cloud App Security fornece uma API REST com suporte completo para que você possa interagir programaticamente com o serviço.

Você pode usar as APIs do Microsoft Cloud App Security para investigar as atividades executadas pelos usuários em aplicativos de nuvem conectados. 

O modo de API de atividades do Cloud App Security é otimizado para verificação e a recuperação de grandes quantidades de dados (mais de 5.000 atividades). A API de verificação consultas os dados da atividade repetidamente até que todos os resultados foram verificados. 

> [!NOTE] 
> Para grandes quantidades de atividades e implantações em grande escala, é recomendável que você use o [agente SIEM](siem.md) para verificação de atividade.

**Para usar a API de verificação de atividade:**

1. Execute a consulta em seus dados.
1. Se houver mais registros do que poderiam estar listadas em uma única verificação, você obterá um comando de retorno com `nextQueryFilters` que deve ser executado. Você obterá esse comando sempre que digitalizar até que a consulta retornou todos os resultados.
 
 
**Parâmetros de corpo de solicitação**:
- "filtros": Filtro de objetos com todos os filtros de pesquisa para a solicitação, consulte [filtros de atividade](activity-filters.md) para obter mais informações. Para evitar que suas solicitações limitadas, certifique-se de incluir uma limitação à sua consulta, por exemplo, consultar atividades do último dia ou filtrar para um determinado aplicativo.
- “isScan”: Valor booliano. Habilita o modo de verificação.
- “sortDirection”: A direção de classificação, os valores possíveis são "asc" e "desc" 
- "sortField": Campos usados para classificar as atividades. Os possíveis valores são: 
    - a data - a data em que, em seguida, a atividade ocorreu (esse é o padrão).
    - criado - o carimbo de hora quando a atividade foi salvo.
- “limit”: Número inteiro. No modo de verificação, entre 500 e 5000 (o padrão é 500). Controla o número de iterações usadas para verificação de todos os dados. 

**Parâmetros de resposta**:
- "dados": os dados retornados. Conterá até "limitar" o número de registros de cada iteração. Se houver mais registros a serem retirados (hasNext = true), a última alguns registros serão removidos para garantir que todos os dados é listada apenas uma vez.
- “hasNext”: Valor booliano. Indica se a outra iteração nos dados é necessária.
- “nextQueryFilters”: Se for necessária outra iteração, ele contém a consulta consecutiva do JSON para ser executado. Use isso como o parâmetro "filtros" na próxima solicitação.

O exemplo de Python a seguir obtém todas as atividades do dia anterior do Exchange Online.

      import requests
      import json
      ACTIVITIES_URL = 'https://<your_tenant>.portal.cloudappsecurity.com/api/v1/activities/'
    
      your_token = '<your_token>'
         headers = {
         'Authorization': 'Token {}'.format(your_token),
        }
    
        filters = {
          # optionally, edit to match your filters
          'date': {'gte_ndays': 1},
          'service': {'eq': [20893]}
        }
        request_data = {
         'filters': filters,
         'isScan': True
        }
        
        records = []
        has_next = True
        while has_next:
            content = json.loads(requests.post(ACTIVITIES_URL, json=request_data, headers=headers).content)
            response_data = content.get('data', [])
            records += response_data
            print('Got {} more records'.format(len(response_data)))
            has_next = content.get('hasNext', False)
            request_data['filters'] = content.get('nextQueryFilters')
        
        print('Got {} records in total'.format(len(records)))
        
 
## <a name="next-steps"></a>Próximas etapas
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/)  
  

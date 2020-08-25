---
title: Investigar atividades usando a API-Cloud App Security
description: Este artigo fornece informações sobre como usar a API para investigar a atividade do usuário no Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/26/2019
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: a2465690efe239e3a420a1fe6f651346e7730c81
ms.sourcegitcommit: 29a8e66c665f51d831516924ae4d9d8047b39276
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88781422"
---
# <a name="investigate-activities-using-the-api"></a>Investigar atividades usando a API

*Aplica-se a: Microsoft Cloud App Security*

Microsoft Cloud App Security fornece uma API REST com suporte total para permitir que você interaja programaticamente com o serviço.

Você pode usar as APIs de Microsoft Cloud App Security para investigar as atividades executadas pelos usuários em aplicativos de nuvem conectados.

O modo de API de atividades Cloud App Security é otimizado para verificação e recuperação de grandes quantidades de dados (mais de 5.000 atividades). A verificação de API consulta os dados da atividade repetidamente até que todos os resultados tenham sido verificados.

> [!NOTE]
> Para grandes quantidades de atividades e implantações em grande escala, recomendamos que você use o [agente Siem](siem.md) para verificação de atividade.

**Para usar a API de verificação de atividade:**

1. Execute a consulta em seus dados.
1. Se houver mais registros do que o que pudesse ser listado em uma única verificação, você receberá um comando de retorno com o `nextQueryFilters` que deve ser executado. Você receberá esse comando sempre que examinar até que a consulta tenha retornado todos os resultados.

**Parâmetros do corpo da solicitação**:

- "filtros": filtrar objetos com todos os filtros de pesquisa para a solicitação, consulte [filtros de atividade](activity-filters.md) para obter mais informações. Para evitar que suas solicitações sejam limitadas, lembre-se de incluir uma limitação em sua consulta, por exemplo, consultar as atividades do último dia ou filtrar um aplicativo específico.
- "ISSCAN": booliano. Habilita o modo de verificação.
- "sortDirection": a direção da classificação, os valores possíveis são "ASC" e "desc"
- "SortField": campos usados para classificar atividades. Os valores possíveis são:
  - data-a data em que a atividade ocorreu (esse é o padrão).
  - Created-o carimbo de data/hora quando a atividade foi salva.
- "Limit": inteiro. No modo de verificação, entre 500 e 5000 (o padrão é 500). Controla o número de iterações usadas para verificar todos os dados.

**Parâmetros de resposta**:

- "dados": os dados retornados. Conterá até "limitar" o número de registros de cada iteração. Se houver mais registros a serem puxados (hasNext = true), os últimos registros serão descartados para garantir que todos os dados sejam listados apenas uma vez.
- "hasNext": booliano. Denota se outra iteração nos dados é necessária.
- "nextQueryFilters": se outra iteração for necessária, ela conterá a consulta JSON consecutiva a ser executada. Use-o como o parâmetro "Filters" na próxima solicitação.

O exemplo de Python a seguir obtém todas as atividades do dia anterior do Exchange Online.

``` python
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
```

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]

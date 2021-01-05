---
title: Investigar atividades usando a API
description: Este artigo fornece informações sobre como usar a API para investigar a atividade do usuário no Cloud App Security.
ms.date: 12/22/2020
ms.topic: how-to
ms.openlocfilehash: 799e248ed69626b301d9281c43c14053b6ff03cf
ms.sourcegitcommit: 90df07ce9cd64fd9c46fb6563f0249079204e174
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/04/2021
ms.locfileid: "97859161"
---
# <a name="investigate-activities-using-the-api"></a>Investigar atividades usando a API

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Você pode usar as APIs de atividades para investigar as atividades executadas pelos usuários em aplicativos de nuvem conectados.

O modo de API de atividades é otimizado para verificação e recuperação de grandes quantidades de dados (mais de 5.000 atividades). A verificação de API consulta os dados da atividade repetidamente até que todos os resultados tenham sido verificados.

> [!NOTE]
> Para grandes quantidades de atividades e implantações em grande escala, recomendamos que você use o [agente Siem](siem.md) para verificação de atividade.

## <a name="to-use-the-activity-scan-script"></a>Para usar o script de verificação de atividade

1. Execute a consulta em seus dados.
1. Se houver mais registros do que o que pudesse ser listado em uma única verificação, você receberá um comando de retorno com o `nextQueryFilters` que deve ser executado. Você receberá esse comando sempre que examinar até que a consulta tenha retornado todos os resultados.

## <a name="request-body-parameters"></a>Parâmetros do corpo da solicitação

- "filtros": filtrar objetos com todos os filtros de pesquisa para a solicitação, consulte [filtros de atividade](activity-filters-queries.md) para obter mais informações. Para evitar que suas solicitações sejam limitadas, lembre-se de incluir uma limitação em sua consulta, por exemplo, consultar as atividades do último dia ou filtrar um aplicativo específico.
- "ISSCAN": booliano. Habilita o modo de verificação.
- "sortDirection": a direção da classificação, os valores possíveis são "ASC" e "desc"
- "SortField": campos usados para classificar atividades. Os valores possíveis são:
  - data-a data em que a atividade ocorreu (esse é o padrão).
  - Created-o carimbo de data/hora quando a atividade foi salva.
- "Limit": inteiro. No modo de verificação, entre 500 e 5000 (o padrão é 500). Controla o número de iterações usadas para verificar todos os dados.

## <a name="response-parameters"></a>Parâmetros de resposta

- "dados": os dados retornados. Conterá até "limitar" o número de registros de cada iteração. Se houver mais registros a serem puxados (hasNext = true), os últimos registros serão descartados para garantir que todos os dados sejam listados apenas uma vez.
- "hasNext": booliano. Denota se outra iteração nos dados é necessária.
- "nextQueryFilters": se outra iteração for necessária, ela conterá a consulta JSON consecutiva a ser executada. Use-o como o parâmetro "Filters" na próxima solicitação.

O exemplo de Python a seguir obtém todas as atividades do dia anterior do Exchange Online.

``` python
import requests
import json
ACTIVITIES_URL = 'https://<your_tenant>.<tenant_region>.contoso.com/api/v1/activities/'

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

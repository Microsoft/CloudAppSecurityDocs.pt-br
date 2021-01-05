---
title: Gerenciar intervalos de endereços IP usando a API
description: Este artigo fornece informações sobre como usar a API para gerenciar intervalos de endereços IP em Cloud App Security.
ms.date: 01/04/2021
ms.topic: how-to
ms.openlocfilehash: 4351649e023128cbb7635c366e3ab5449956c144
ms.sourcegitcommit: 90df07ce9cd64fd9c46fb6563f0249079204e174
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/04/2021
ms.locfileid: "97859164"
---
# <a name="manage-ip-address-ranges-using-the-api"></a>Gerenciar intervalos de endereços IP usando a API

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Você pode usar as APIs de enriquecimento de dados para gerenciar intervalos de endereços IP.

## <a name="to-use-the-manage-ip-address-ranges-script"></a>Para usar o script gerenciar intervalos de endereços IP

1. Crie um arquivo CSV com os seguintes campos esperados: nome, IP_Address_Ranges, categoria, marca (ID) e Override_ISP_Name.

1. Atualize os valores para as seguintes variáveis de script: **OPTION_DELETE_ENABLED**, **IP_RANGES_BASE_URL**, **CSV_ABSOLUTE_PATH** **YOUR_TOKEN**

    > [!IMPORTANT]
    > Se você definir **OPTION_DELETE_ENABLED** como **true**, todos os intervalos de endereços IP definidos no seu locatário, mas não EXISTIRem nos arquivos CSV, serão excluídos do locatário pelo script. Se você usar essa opção, certifique-se de que o arquivo CSV define todos os intervalos de endereços IP que você deseja em seu locatário.

1. Execute o script para criar novos registros e atualizar as regras existentes com o nome correspondente.

## <a name="request-body-parameters"></a>Parâmetros do corpo da solicitação

- "filtros": filtrar objetos com todos os filtros de pesquisa para a solicitação, consulte [filtros de enriquecimento de dados](api-data-enrichment.md#filters) para obter mais informações. Para evitar que suas solicitações sejam limitadas, certifique-se de incluir uma limitação em sua consulta.
- "Limit": inteiro. No modo de verificação, entre 500 e 5000 (o padrão é 500). Controla o número de iterações usadas para verificar todos os dados.

## <a name="response-parameters"></a>Parâmetros de resposta

- "dados": os dados retornados. Conterá até "limitar" o número de registros de cada iteração. Se houver mais registros a serem puxados (hasNext = true), os últimos registros serão descartados para garantir que todos os dados sejam listados apenas uma vez.
- "hasNext": booliano. Denota se outra iteração nos dados é necessária.
- "nextQueryFilters": se outra iteração for necessária, ela conterá a consulta JSON consecutiva a ser executada. Use-o como o parâmetro "Filters" na próxima solicitação.

O exemplo de Python a seguir usa o conteúdo de um arquivo CSV para gerenciar (criar, atualizar ou excluir) intervalos de endereços IP em seu ambiente de Cloud App Security.

```python
import csv
import requests
import json

OPTION_DELETE_ENABLED = False
IP_RANGES_BASE_URL = 'https://<tenant_id>.<tenant_region>.contoso.com/api/v1/subnet/'
IP_RANGES_UPDATE_SUFFIX = 'update_rule/'
IP_RANGES_CREATE_SUFFIX = 'create_rule/'
CSV_ABSOLUTE_PATH = 'rules.csv'
YOUR_TOKEN = '<your_token>'
HEADERS = {
  'Authorization': 'Token {}'.format(YOUR_TOKEN),
}

# Get all records.
def get_records():
  list_request_data = {
    # Optionally, edit to match your filters
    'filters': {},
    "skip": 0,
    "limit": 20
  }
  records = []
  has_next = True
  while has_next:
    content = json.loads(requests.post(IP_RANGES_BASE_URL, json=list_request_data, headers=HEADERS).content)
    response_data = content.get('data', [])
    records += response_data
    has_next = content.get('hasNext', False)
    list_request_data["skip"] += len(response_data)
  return records

# Rule fields are compared to the CSV row.
def rule_matching(record, ip_address_ranges, category, tag, isp_name, ):
  rule_exists_conditions = [sorted([subnet.get('originalString', False) for subnet in record.get('subnets', [])]) !=
                            sorted(ip_address_ranges.split(' ')),
                            str(record.get('category', False)) != category,
                            len(record.get('tags', [])) != len(tag.split(' ')) and
                            (len(record.get('tags', [])) != 0 and len(tag) == 1),
                            bool(record.get('organization', False)) != bool(isp_name) or
                            (record.get('organization', False) is not None and not isp_name)]
  if any(rule_exists_conditions):
    return False
  for tag in record.get('tags', []):
    tag_id = tag.get('id')
    if tag_id and tag_id not in tag.split(' '):
      return False
  return True

def create_update_rule(name, ip_address_ranges, category, tag, isp_name, records, request_data):
  for record in records:
    # Records are compared by name(unique).
    # This can be changed to id (to update the name), it will include adding id to the CSV and changing row shape.
    if record["name"] == name:
      # request_data["_tid"] = record["_tid"]
      if not rule_matching(record, ip_address_ranges, category, tag, isp_name):
        # Update existing rule
        json.loads(
          requests.post(f"{IP_RANGES_BASE_URL}{record['_id']}/{IP_RANGES_UPDATE_SUFFIX}", json=request_data, headers=HEADERS).content)
        return record
      else:
        # The exact same rule exists. no need for change.
        return record
  # Create new rule.
  requests.post(f"{IP_RANGES_BASE_URL}{IP_RANGES_CREATE_SUFFIX}", json=request_data, headers=HEADERS)

# Request data creation.
def create_request_data(name, ip_address_ranges, category, tag, isp_name):
  request_data = {"name": name, "subnets": ip_address_ranges.split(' '), "category": category,
                  "tags": tag.split(' ') if tag else ''}
  if isp_name:
    request_data["overrideOrganization"] = True
    request_data["organization"] = isp_name
  return request_data

def main():
  # CSV fields are: Name,IP_Address_Ranges,Category,Tag(id),Override_ISP_Name
  # Multiple values (eg: multiple subnets) will be space-separated. (eg: value1 value2)
  records = get_records()
  with open(CSV_ABSOLUTE_PATH, newline='\n') as your_file:
    reader = csv.reader(your_file, delimiter=',')
    for row in reader:
      name, ip_address_ranges, category, tag, isp_name = row
      request_data = create_request_data(name, ip_address_ranges, category, tag, isp_name)
      if records:
        # Existing records were retrieved from your tenant
        record = create_update_rule(name, ip_address_ranges, category, tag, isp_name, records, request_data)
        record_id = record['_id']
      else:
        # No existing records were retrieved from your tenant
        record_id = json.loads(requests.post(f"{IP_RANGES_BASE_URL}{IP_RANGES_CREATE_SUFFIX}", json=request_data, headers=HEADERS).content)
      if OPTION_DELETE_ENABLED:
        # Remove CSV file record from tenant records.
        if record_id:
          for record in records:
            if record['_id'] == record_id:
              records.remove(record)
  if OPTION_DELETE_ENABLED:
    # Delete remaining tenant records, i.e. records that aren't in the CSV file.
    for record in records:
      requests.delete(f"{IP_RANGES_BASE_URL}{record['_id']}/", headers=HEADERS)
  
if __name__ == '__main__':
  main()
```

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]

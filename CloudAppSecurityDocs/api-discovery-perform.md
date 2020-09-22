---
title: Executar o upload de arquivo-API de Cloud Discovery
description: Este artigo descreve a solicitação executar upload de arquivo na API Cloud Discovery do Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: a943bf41934a6f90bd8d23b1b6bb358d673f35e7
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90880568"
---
# <a name="perform-file-upload---cloud-discovery-api"></a>Executar o upload de arquivo-API de Cloud Discovery

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Carregue o conteúdo do arquivo executando uma solicitação HTTP PUT. Você será solicitado a usar a URL retornada pela solicitação de [carregamento de arquivo de inicialização](api-discovery-initiate.md) .

O Azure e o AWS têm diferentes cabeçalhos e limitações ao carregar arquivos na URL de destino.

> [!NOTE]
>
> - Você pode carregar arquivos individuais de até 5 GB. Se você precisar carregar arquivos maiores, divida os dados de Cloud Discovery em várias partes.
> - Se você não souber qual ambiente está executando, marque a solicitação [Iniciar upload de arquivo](api-discovery-initiate.md) , que retorna essas informações.

## <a name="http-request"></a>Solicitação HTTP

```rest
PUT https://<initiate_file_upload_response_url>
```

> [!NOTE]
>
> Para o Azure:
> - Se o arquivo estiver abaixo de 64 MB, adicione o cabeçalho "x-ms-blob-Type: BlockBlob" à sua solicitação.
> - Se o tamanho do arquivo for maior que 64MB, carregue-o em partes. a maneira mais fácil de fazer isso é usando o [SDK do Azure](https://azure.microsoft.com/downloads/).

## <a name="example"></a>Exemplo

### <a name="request"></a>Solicitação

Aqui está um exemplo da solicitação do Azure.

```rest
curl --request PUT --upload-file <file_to_upload> -H "x-ms-blob-type: BlockBlob" "https://<initiate_file_upload_response_url>"
```

Aqui está um exemplo da solicitação para o SDK do Java do Azure.

```java
File fileReference = new File("file.name");
// Create a blob using the URI that contains the shared access signature.
CloudBlockBlob sasBlob = new CloudBlockBlob(uri);

// Upload the file to the blob.
sasBlob.upload(new FileInputStream(fileReference), fileReference.length());
```

[!INCLUDE [Open support ticket](includes/support.md)]

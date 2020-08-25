---
title: Configuração de FTP do coletor de logs
description: Este artigo descreve o processo para modificar a configuração do Docker do Cloud Discovery do Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 8/7/2019
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 53eaa7b96a22c7574a63b6051dce64076fafaa39
ms.sourcegitcommit: 29a8e66c665f51d831516924ae4d9d8047b39276
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88781660"
---
# <a name="log-collector-ftp-configuration"></a>Configuração de FTP do coletor de logs

*Aplica-se a: Microsoft Cloud App Security*

Este artigo descreve como modificar a configuração do Docker do Cloud Discovery do Cloud App Security.

## <a name="docker-deployment"></a>Implantação do Docker

Talvez você precise modificar a configuração do Docker do Cloud Discovery do Cloud App Security.

### <a name="changing-the-ftp-password"></a>Alterar a senha do FTP

1. Conecte-se ao host do coletor de logs.

2. Execute `docker exec -it <collector name> pure-pw passwd <ftp user>`

    1. Insira a nova senha.
    2. Insira a nova senha novamente para confirmação.

3. Execute o `docker exec -it <collector name> pure-pw mkdb` para aplicar a alteração.

    ![alterar a senha do FTP](media/ftp-connect.png)

### <a name="customize-certificate-files"></a>Personalizar arquivos de certificado

Siga este procedimento para personalizar os arquivos de certificado usados para conexões seguras com o docker do Cloud Discovery.

1. Abra um cliente de FTP e conecte-se ao coletor de logs.

    ![Conecte-se ao cliente de FTP](media/ftp-connect.png)

2. Navegue até o diretório `ssl_update`.
3. Carregue novos arquivos de certificado no diretório `ssl_update` (os nomes são obrigatórios).

    ![Carregar arquivos de certificado](media/new-certs.png)

    - **Para FTP:** apenas um arquivo é necessário. O arquivo tem os dados de chave e de certificado, nessa ordem, e é denominado **pure-ftpd.pem**.
    - **Para o syslog:** Três arquivos são necessários: **ca. pem**, * * Server-Key. pem e **Server-CERT. pem**. Se um dos arquivos estiver ausente, a atualização não ocorrerá.

4. Em um terminal, execute: `docker exec -t <collector name> update_certs`. O comando deve produzir uma saída semelhante à mostrada na captura de tela a seguir.

    ![Atualizar arquivos de certificado](media/update-certs.png)

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Implantar o Cloud Discovery](set-up-cloud-discovery.md)

[!INCLUDE [Open support ticket](includes/support.md)]

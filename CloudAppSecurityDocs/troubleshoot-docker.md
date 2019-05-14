---
title: Modificar as configurações de FTP
description: Este artigo descreve o processo para modificar a configuração do Docker do Cloud Discovery do Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: rkarlin
ms.date: 04/18/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 776e834f-3c20-4d5f-9fab-4c5b975edb06
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: bb21ffbef29395ca480fa718ac20f1f372253f23
ms.sourcegitcommit: 9f0c562322394a3dfac7f1d84286e673276a28b1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65568626"
---
# <a name="log-collector-ftp-configuration"></a>Configuração do FTP do coletor de log

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

  ![alterar a senha do FTP](./media/ftp-connect.png)

### <a name="customize-certificate-files"></a>Personalizar arquivos de certificado

Siga este procedimento para personalizar os arquivos de certificado usados para conexões seguras com o docker do Cloud Discovery.

1. Abra um cliente de FTP e conecte-se ao coletor de logs.

   ![Conecte-se ao cliente de FTP](./media/ftp-connect.png)

2. Navegue até o diretório `ssl_update`.
3. Carregue novos arquivos de certificado no diretório `ssl_update` (os nomes são obrigatórios).

   ![Alterar a senha do FTP](./media/new-certs.png)

    - **Para FTP:** Apenas um arquivo é necessário. O arquivo tem os dados de chave e de certificado, nessa ordem, e é denominado **pure-ftpd.pem**.
    - **Para Syslog:** Três arquivos são necessários: **ca.pem**, **server-key.pem e **server-cert.pem**. Se um dos arquivos estiver ausente, a atualização não ocorrerá.

4. Em um terminal, execute: `docker exec -t <collector name> update_certs`. O comando deve produzir uma saída semelhante à mostrada na captura de tela a seguir.

   ![Alterar a senha do FTP](./media/update-certs.png)

## <a name="next-steps"></a>Próximas etapas

[Implantar o Cloud Discovery](set-up-cloud-discovery.md)

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier](https://premier.microsoft.com/)

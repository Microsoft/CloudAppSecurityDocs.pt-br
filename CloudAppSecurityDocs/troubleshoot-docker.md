---
title: Solução de problemas de implantação do Docker do Cloud Discovery
description: Este artigo descreve o processo para modificar a configuração do Docker do Cloud Discovery do Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: barbkess
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 776e834f-3c20-4d5f-9fab-4c5b975edb06
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 01fa2f69422bd3c1c272a76c113254f819b90137
ms.sourcegitcommit: 8ef0438fa35916c48625ff750cb85e9628d202f2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56280872"
---
# <a name="troubleshooting-the-microsoft-cloud-app-security-cloud-discovery-deployment"></a>Solucionando problemas da implantação do Cloud Discovery do Microsoft Cloud App Security

*Aplica-se a: Microsoft Cloud App Security*

Este artigo descreve como modificar a configuração do Docker do Cloud Discovery do Cloud App Security.

## <a name="windows-defender-atp-integration"></a>Integração do Windows Defender ATP

Se você integrou o Windows Defender ATP ao Cloud App Security, mas os resultados da integração não aparecem, ou seja, não há nenhum relatório de **usuários do ponto de extremidade do Win10**, verifique se os computadores aos quais você está se conectando são Windows 10 versão 1809 ou posterior e se você aguardou as duas horas necessárias para que os dados possam ser acessados.

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

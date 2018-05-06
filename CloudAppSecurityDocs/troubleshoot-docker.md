---
title: Solução de problemas de implantação do docker do Cloud Discovery | Microsoft Docs
description: Este tópico descreve o processo para modificar a configuração do docker do Cloud Discovery do Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/22/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 776e834f-3c20-4d5f-9fab-4c5b975edb06
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 395faee1afcf58f1750983672760cd881f2a3441
ms.sourcegitcommit: 45311f2cafef79483e40d971a4c61c7673834d96
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2018
---
*Aplica-se ao: Microsoft Cloud App Security*

# <a name="troubleshooting-the-microsoft-cloud-app-security-cloud-discovery-docker"></a>Solução de problemas do docker do Microsoft Cloud Discovery do Cloud App Security

## <a name="changing-the-ftp-password"></a>Alterar a senha do FTP


1. Conecte-se ao host do coletor de logs.

2.  Execute `docker exec -it <collector name> pure-pw passwd <ftp user>`

    1. Insira a nova senha.
    2. Insira a nova senha novamente para confirmação.
 
3.  Execute o `docker exec -it <collector name> pure-pw mkdb` para aplicar a alteração.


  ![alterar a senha do FTP](./media/ftp-connect.png)

## <a name="customize-certificate-files"></a>Personalizar arquivos de certificado

Siga este procedimento para personalizar os arquivos de certificado usados para conexões seguras com o docker do Cloud Discovery.

1. Abra um cliente de FTP e conecte-se ao coletor de logs.

   ![Conecte-se ao cliente de FTP](./media/ftp-connect.png)

2. Navegue até o diretório `ssl_update`.
3. Carregue novos arquivos de certificado no diretório `ssl_update` (os nomes são obrigatórios).

   ![Alterar a senha do FTP](./media/new-certs.png)

   1.  Para FTP: somente um arquivo é necessário, contendo a chave e os dados de certificado, nessa ordem, denominado **pure-ftpd.pem**.
    
   2.  Para Syslog: três arquivos são necessários: **ca.pem**, **server-key.pem** e **server-cert.pem**. Caso algum dos arquivos esteja faltando, a atualização não ocorrerá.

4. Em um terminal, execute: `docker exec -t <collector name> update_certs`. Isso deverá produzir um resultado similar ao exibido na próxima tela.

   ![Alterar a senha do FTP](./media/update-certs.png)

## <a name="see-also"></a>Consulte Também
[Implantar o Cloud Discovery](set-up-cloud-discovery.md)

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier](https://premier.microsoft.com/)


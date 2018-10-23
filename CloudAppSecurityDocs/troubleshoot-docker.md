---
title: Solução de problemas de implantação do docker do Cloud Discovery | Microsoft Docs
description: Este tópico descreve o processo para modificar a configuração do docker do Cloud Discovery do Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/07/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 776e834f-3c20-4d5f-9fab-4c5b975edb06
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: f53eca16b08b72798e2b3b0ababcad7ae676765d
ms.sourcegitcommit: 53a1c990ff06674c26563a9ebcb1979818c3c063
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/09/2018
ms.locfileid: "48881764"
---
*Aplica-se ao: Microsoft Cloud App Security*

# <a name="troubleshooting-the-microsoft-cloud-app-security-cloud-discovery-deployment"></a>Solucionando problemas da implantação do Cloud Discovery do Microsoft Cloud App Security

## <a name="windows-defender-atp-integration"></a>Integração do Windows Defender ATP
Se você integrou o Windows Defender ATP ao Cloud App Security e não vê os resultados da integração, não há nenhum relatório de **usuários do ponto de extremidade do Win10** – certifique-se de que os computadores aos quais você está se conectando sejam Windows 10 versão 1809 ou posterior, e que você aguardou as horas necessárias que leva antes de os seus dados poderem ser acessados.

## <a name="docker-deployment"></a>Implantação do Docker

### <a name="changing-the-ftp-password"></a>Alterar a senha do FTP


1. Conecte-se ao host do coletor de logs.

2.  Execute `docker exec -it <collector name> pure-pw passwd <ftp user>`

    1. Insira a nova senha.
    2. Insira a nova senha novamente para confirmação.
 
3.  Execute o `docker exec -it <collector name> pure-pw mkdb` para aplicar a alteração.


  ![alterar a senha do FTP](./media/ftp-connect.png)

### <a name="customize-certificate-files"></a>Personalizar arquivos de certificado

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


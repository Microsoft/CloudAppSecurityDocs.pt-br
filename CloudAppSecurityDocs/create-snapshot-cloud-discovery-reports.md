---
title: "Criar relatórios instantâneos do uso de aplicativos na nuvem do Cloud Discovery | Microsoft Docs"
description: "Este artigo fornece informações sobre como carregar logs manualmente para criar um relatório de instantâneo de seus aplicativos do Cloud Discovery."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 7/16/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: ecc1949d-c861-4636-952a-c3a260719bb5
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: bce725777964ac46a21b03434d24ac725280d84d
ms.sourcegitcommit: ae4c8226f6037c5eb286eb27142d6bbb397609e9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/16/2017
---
# <a name="create-snapshot-cloud-discovery-reports"></a>Criar instantâneo de relatórios do Cloud Discovery
É importante carregar um log manualmente e permitir que o Cloud App Security analise-o antes de tentar usar o coletor de logs automático.
Se você ainda não tiver um log e desejar ver um exemplo da aparência do seu log, siga o procedimento abaixo e baixe um arquivo de log de exemplo para ver qual deve ser a aparência do seu log.


Para criar um relatório de instantâneo:
  
1.  Colete arquivos de log do firewall e do proxy por meio dos quais os usuários da sua organização acessam a Internet. Certifique-se de coletar logs durante os períodos de tráfego de pico que representam a atividade de todos os usuários na sua organização.  
  
2.  No portal do Cloud App Security, clique em **Descobrir** e **Criar novo relatório de instantâneo**.  
  
   ![Criar novo relatório de instantâneo](./media/create-new-snapshot-report.png)
     
3.  Insira um **Nome do relatório** e uma **Descrição**
  
     ![Novo relatório de instantâneo](./media/new-snapshot-report.png) 

4.  Selecione a **Fonte de dados** da qual você deseja carregar os arquivos de log.  
  
5. Verifique o formato do seu log para certificar-se de que ele está formatado corretamente de acordo com o exemplo que pode ser baixado. Clique em **Exibir e Verificar** e, em seguida, clique em **Baixar Log de Exemplo**. Em seguida, compare seu log com o exemplo fornecido para verificar se ele é compatível. 

 ![Verifique o formato do seu log](./media/cloud-discovery-snapshot-verify.png)  

  > [!NOTE]
  > O formato de exemplo FTP tem suporte em instantâneos e no upload automatizado enquanto o syslog tem suporte somente no upload automatizado.<br></br>
Baixar um exemplo de log também baixará um exemplo de log FTP.


5.  **Escolha os logs de tráfego** que você deseja carregar. Você pode carregar até 20 arquivos ao mesmo tempo. Também há suporte para arquivos compactados.  
  
6.  Clique em **Criar**.  

7.  Após o upload ser concluído, a mensagem de status será exibida no canto superior direito da tela avisando que o log foi carregado com êxito.  
  
8.  Depois de carregar os arquivos de log, levará algum tempo para que eles possam ser analisados e examinados.  
Após o processamento dos arquivos de log ser concluído, você receberá um email para avisar que ele está pronto. 
  
9. Uma faixa de notificação aparecerá na barra de status na parte superior do portal para atualizar o status de processamento dos arquivos de log.  
![barra de menus do arquivo de log de processamento](./media/processing-log-file-menu-bar.png) 
   
10. Depois que os logs forem carregados com êxito, você deverá ver uma notificação informando que o processamento do arquivo de log foi concluído com êxito. Neste ponto, você pode exibir o relatório clicando no link na barra de status ou indo para a engrenagem de Configurações e selecionando **Configurações do Cloud Discovery**.   
  
     ![Guia Configurações de descoberta](./media/discovery-settings-tab.png)
11. Em seguia, selecione **Gerenciar relatórios de instantâneo** e seu relatório de instantâneo.
 
![gerenciamento de relatório de instantâneo](./media/snapshot-report-managment.png)

  
      
## <a name="see-also"></a>Veja também  
[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
    
      
  
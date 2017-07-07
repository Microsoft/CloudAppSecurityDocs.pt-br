---
title: Bloqueando aplicativos descobertos | Microsoft Docs
description: "Este tópico descreve o procedimento para exportar scripts de bloqueio para aplicativos descobertos."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 2/21/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: e451031e-4764-411a-b366-73a49d4f25df
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: cf14aaa243baaea8223cc6a271e7a237a0a1e287
ms.sourcegitcommit: 2f4474084c7e07ac4853945ab5aa1ea78950675d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/28/2017
---
## <a name="govern-discovered-apps"></a>Controlar aplicativos descobertos

Depois de revisar a lista de aplicativos descobertos em seu ambiente, você pode proteger seu ambiente contra o uso de aplicativos indesejados das seguintes maneiras.

### <a name="sanctioningunsanctioning-an-app"></a>Sanção/cancelamento de um aplicativo 

Você pode cancelar um aplicativo de risco específico ao clicar nos três pontos no final da linha e selecionar **Cancelar sanção**.
O cancelamento de sanção de um aplicativo não bloqueia o uso, mas permite monitorar seu uso mais facilmente com os filtros do Cloud Discovery. Então, você pode notificar os usuários do aplicativo que ele a sanção cancelada e sugerir uma alternativa, um aplicativo seguro para seu uso.

![Marcar como não sancionado](./media/tag-as-unsanctioned.png)  


Se você tiver uma lista de aplicativos que você deseja sancionar ou cancelar a sanção, você poderá usar a caixa de seleção para marcar todos os aplicativos que você deseja gerenciar e, em seguida, selecionar a ação.


## <a name="export-a-block-script-to-govern-discovered-apps"></a>Exporte um script de bloqueio para controlar aplicativos descobertos

O Cloud App Security permite que você bloqueie o acesso a aplicativos não sancionados aproveitando os dispositivos de segurança locais existentes. Gere um script de bloqueio dedicado e importe-o no seu dispositivo.
Essa solução não exige redirecionamento de todo o tráfego da web da organização para um proxy.

1. No painel do Cloud Discovery, marque quaisquer aplicativos que deseja bloquear como **Não sancionado**.

   ![Marcar como não sancionado](./media/tag-as-unsanctioned.png)  

2. Na barra de título, clique nos três pontos e selecione **Gerar script de bloqueio...**. 

   ![Gerar script de bloqueio](./media/generate-block-script.png)  

3. Em **Gerar script de bloqueio**, selecione o dispositivo para o qual deseja gerar o script de bloqueio. 

   ![Pop-up da opção Gerar script de bloqueio](./media/generate-block-script-popup.png)  

4. Em seguida, clique no botão Gerar script. Isso criará um script de bloqueio para todos os seus aplicativos não sancionados. Por padrão, o arquivo será nomeado com a data em que foi exportado e o tipo de dispositivo selecionado, por exemplo: *2017-02-19_CAS_Fortigate_block_script.txt* 

   ![Botão Gerar script de bloqueio](./media/generate-block-script-button.png)  

5. Importe o arquivo criado para seu dispositivo.



## <a name="see-also"></a>Veja também  
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
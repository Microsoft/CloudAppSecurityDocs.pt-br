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
ms.openlocfilehash: ca4a10f64429c481f49c75740f651302b1c7d1ef
ms.sourcegitcommit: 7493d88e4fe7c827f870b81e2090ffcc77f1408a
translationtype: HT
---
# <a name="governing-discovered-apps"></a>Controlando aplicativos descobertos
O Cloud App Security permite que você bloqueie o acesso a aplicativos não sancionados aproveitando os dispositivos de segurança locais existentes. Gere um script de bloqueio dedicado e importe-o no seu dispositivo.
Essa solução não exige redirecionamento de todo o tráfego da web da organização para um proxy.


## <a name="export-a-block-script-to-govern-discovered-apps"></a>Exporte um script de bloqueio para controlar aplicativos descobertos

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
  
  
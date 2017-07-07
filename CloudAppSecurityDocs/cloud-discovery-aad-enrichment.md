---
title: "Aprimorar dados do Cloud App Security Discovery com nomes de usuário do Azure AD | Microsoft Docs"
description: "Este artigo fornece informações sobre como aprimorar os dados do Cloud App Security Discovery com nomes de usuário do Azure AD."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 6/19/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 45295c2c-3e4d-4482-bf95-2e47072f9236
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 909fa75c48fb9c698d083f2fb85f5f53bfadf76c
ms.sourcegitcommit: 2f4474084c7e07ac4853945ab5aa1ea78950675d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/28/2017
---
# <a name="cloud-discovery-enrichment"></a>Aprimoramento do Cloud Discovery

Os dados do Cloud Discovery agora podem ser aprimorados com os dados de nome de usuário do Azure Active Directory. Quando você habilita esse recurso, o nome de usuário recebido nos logs de tráfego de descoberta serão correspondidos e substituídos pelo nome de usuário do Azure AD, habilitando os seguintes novos recursos:
-   Você pode investigar o uso de TI sombra pelo usuário do Azure Active Directory.
-   Você pode correlacionar o uso do aplicativo de nuvem Descoberto com as atividades coletadas pela API.
-   Então, você pode criar logs personalizados com base nos grupos de usuários do Azure AD. Por exemplo, um relatório de TI sombra para um departamento de Marketing específico.


## <a name="prerequisites"></a>Pré-requisitos:
- A fonte de dados deve fornecer informações de nome de usuário
- Conector de aplicativos do Office 365 conectado

## <a name="enabling-user-data-enrichment"></a>Permitindo o aprimoramento de dados de usuário 
    
1. Na engrenagem Configurações, selecione **Configurações do Cloud Discovery**.
     
2. Na guia **Aprimoramento do usuário**, habilite a Cloud App Security para usar os dados do Azure Active Directory para aprimorar os nomes de usuário por padrão, selecione **Aprimorar identificadores de usuário descobertos com nomes de usuário do Azure Active Directory**.

3. Clique em **Salvar**.
 
![Aprimorar o Cloud App Security Discovery com nomes de usuário do Azure AD](./media/discovery-enrichment.png)
  

  
      
## <a name="see-also"></a>Veja também  
[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
    
      
  
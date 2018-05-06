---
title: Aprimorar dados do Cloud App Security Discovery com nomes de usuário do Azure AD | Microsoft Docs
description: Este artigo fornece informações sobre como aprimorar os dados do Cloud App Security Discovery com nomes de usuário do Azure AD.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/22/2018
ms.topic: article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 45295c2c-3e4d-4482-bf95-2e47072f9236
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 7778f1a2798975f5e292a4f013d07d2665f05536
ms.sourcegitcommit: 45311f2cafef79483e40d971a4c61c7673834d96
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2018
---
*Aplica-se ao: Microsoft Cloud App Security*


# <a name="cloud-discovery-enrichment"></a>Aprimoramento do Cloud Discovery

Os dados do Cloud Discovery agora podem ser aprimorados com os dados de nome de usuário do Azure Active Directory. Quando você habilita esse recurso, o nome de usuário recebido nos logs de tráfego de descoberta são correspondidos e substituídos pelo nome de usuário do Azure AD, habilitando os seguintes novos recursos:
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
  

  
      
## <a name="see-also"></a>Consulte Também  
[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)   

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
    
      
  
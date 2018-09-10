---
title: Forneça as configurações da sua organização no portal do Cloud App Security para melhores resultado | Microsoft Docs
description: Este artigo explica como fornecer informações sobre sua organização no Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/22/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 2e7e57b0-db54-4d75-896c-4700dd9abe48
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: be1254ef4e4f623e898e3e94b713a924e493476a
ms.sourcegitcommit: 0ac08ca7b3140b79f1d36ff7152476c188fa12b3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44143439"
---
*Aplica-se ao: Microsoft Cloud App Security*

# <a name="basic-setup"></a>Configuração básica
O procedimento a seguir fornece instruções para personalizar o portal do Microsoft Cloud App Security.

## <a name="prerequisites"></a>Pré-requisitos 
Para acessar o portal, é necessário adicionar os seguintes endereços IP à lista de permissões de seu firewall para fornecer acesso ao portal do Cloud App Security:  
  
- 104.42.231.28  
  
> [!NOTE]  
>  Para obter atualizações quando URLs e endereços IP forem alterados, assine o RSS conforme explicado em: [URLs e intervalos de endereços IP do Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).  
  
## <a name="set-up-the-portal"></a>Configurar o portal  
  
1. No portal do Cloud App Security, na barra de menus, clique no ícone de configurações ![ícone de configurações](./media/settings-icon.png "ícone de configurações") e selecione **Configurações** para configurar os detalhes da sua organização.     

2. Em **Detalhes da organização**, é importante que você forneça um **Nome de exibição da organização** para sua organização. Ele é exibido em emails e páginas da Web enviadas do sistema.  
  
3. Forneça um **Nome do ambiente** (locatário). Isso será especialmente importante se você gerenciar vários locatários.  
  
4. Também é possível fornecer um **Logotipo** que é exibido em notificações de email enviadas do sistema e em páginas da Web enviadas do sistema. O logotipo deve ser um arquivo png com um tamanho máximo de 150 x 50 pixels em uma tela de fundo transparente.  

5. Certifique-se de adicionar uma lista de seus **Domínios gerenciados**. Esta é uma etapa essencial porque o Cloud App Security usa os domínios gerenciados para determinar quais usuários são internos, quais são externos e onde os arquivos devem e não devem ser compartilhados. Isso é usado para relatórios, bem como alertas.  
   > [!NOTE] 
   > - Usuários em domínios que não estão configurados como internos são marcados como externos e seus arquivos e atividades não são verificados.

6. Se você estiver se integrando com a integração da Proteção de Informações do Azure, consulte [Integração da Proteção de Informações do Azure](azip-integration.md) para obter informações. 

   >[!NOTE]
   > Para trabalhar com a integração da Proteção de Informações do Azure, habilite o [Conector de aplicativos para o Office 365](connect-office-365-to-microsoft-cloud-app-security.md).
  
7. Se a qualquer momento você desejar fazer o backup das suas configurações do portal, essa tela permitirá que você faça isso. Clique em **Exportar configurações do portal** para criar um arquivo JSON de todas as suas configurações do portal, incluindo regras de política, grupos de usuários e intervalos de endereços IP.  
  
   
> [!NOTE] 
> Se você usa o ExpressRoute, o Cloud App Security é implantado no Azure e totalmente integrado com o [ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-introduction/). Todas as interações com os aplicativos do Cloud App Security e o tráfego enviado a ele, incluindo o upload de logs de descoberta, são roteados por meio do **emparelhamento público** do ExpressRoute para aprimorar a latência, o desempenho e a segurança. Não há nenhuma etapa de configuração necessária do lado do cliente. <br></br>Para obter mais informações sobre o emparelhamento público, consulte [Circuitos da Rota Expressa e domínios de roteamento](https://azure.microsoft.com/documentation/articles/expressroute-circuit-peerings/).  
    
## <a name="see-also"></a>Consulte Também  
[Configurar o Cloud Discovery](set-up-cloud-discovery.md)   

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
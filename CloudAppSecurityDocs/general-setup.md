---
title: "Forneça as configurações da sua organização no portal do Cloud App Security para melhores resultado | Microsoft Docs"
description: "Este artigo explica como fornecer informações sobre sua organização no Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/10/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 2e7e57b0-db54-4d75-896c-4700dd9abe48
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: cb2b4b26ee9a5f0340409090318fcbe1421b90d5
ms.sourcegitcommit: 50fac1cec86dfb8170ba9c63a8f58a4bf24e3c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2017
---
# <a name="basic-set-up"></a>Configuração básica
O procedimento a seguir fornece instruções para personalizar o portal do Cloud App Security.
  
## <a name="set-up-the-portal"></a>Configurar o portal  
  
1.  No portal do Cloud App Security, na barra de menus, clique no ícone de configurações ![ícone de configurações](./media/settings-icon.png "ícone de configurações") e selecione **Configurações Gerais** para configurar o seguinte:  
     
     ![configurações gerais](./media/general-settings.png "configurações gerais")  
  
3.  Em **Detalhes da organização**, é importante que você forneça um **Nome de exibição da organização** para sua organização. Ele será exibido em emails e páginas da Web enviadas do sistema.  
  
4. Forneça um **Nome do ambiente** (locatário). Isso será especialmente importante se você gerenciar vários locatários.  
  
4. Também é possível fornecer um **logotipo** que será exibido em notificações de email enviadas do sistema e em páginas da web enviadas do sistema. O logotipo deve ser um arquivo png com um tamanho máximo de 150 x 50 pixels em uma tela de fundo transparente.  

4.  Certifique-se de adicionar uma lista de seus **Domínios gerenciados**. Esta é uma etapa essencial porque o Cloud App Security usa os domínios gerenciados para determinar quais usuários são internos, quais são externos e onde os arquivos devem e não devem ser compartilhados. Isso é usado para relatórios, bem como alertas.  
> [!NOTE] 
> - Os usuários em domínios que não estão configurados como interno serão marcados como externos e seus arquivos e atividades não serão verificados.

5. Se você estiver se integrando com a integração da Proteção de Informações do Azure, consulte [Integração da Proteção de Informações do Azure](azip-integration.md) para obter informações. 
  
  
6.  Se a qualquer momento você desejar fazer o backup das suas configurações do portal, essa tela permitirá que você faça isso. Clique em **Exportar configurações do portal** para criar um arquivo JSON de todas as suas configurações do portal, incluindo as regras de política, grupos de usuários e intervalos de endereços IP.  
  
       



> [!NOTE] 
> Se você usa o ExpressRoute, o Cloud App Security é implantado no Azure e totalmente integrado com o [ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-introduction/). Todas as interações com os aplicativos do Cloud App Security e o tráfego enviado ele, incluindo o upload de logs de descoberta, são roteados por meio do **emparelhamento público** do ExpressRoute para latência, desempenho e segurança aprimorados. Não há nenhuma etapa de configuração necessária do lado do cliente.  
    Para obter mais informações sobre o emparelhamento público, consulte [Circuitos da ExpressRoute e domínios de roteamento](https://azure.microsoft.com/documentation/articles/expressroute-circuit-peerings/).  
    
## <a name="see-also"></a>Veja também  
[Configurar o Cloud Discovery](set-up-cloud-discovery.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
---
title: Defina as configurações da sua organização no Cloud App Security
description: Este artigo explica como fornecer informações sobre sua organização no Cloud App Security.
ms.date: 11/08/2020
ms.topic: how-to
ms.openlocfilehash: e46b7c651d67fbd655d548f9d77228c29794ab74
ms.sourcegitcommit: 1bea874c7531c1926b6e46b96eac00ceeeeb69f2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/07/2020
ms.locfileid: "96749812"
---
# <a name="basic-setup-for-cloud-app-security"></a>Configuração básica do Cloud App Security

[!INCLUDE [Banner for top of topics](includes/banner.md)]

O procedimento a seguir fornece instruções para personalizar o portal do Microsoft Cloud App Security.

## <a name="prerequisites"></a>Pré-requisitos

Para acesso ao portal, é necessário adicionar os seguintes endereços IP à lista de permissões do firewall para fornecer acesso ao portal de Cloud App Security:

* 104.42.231.28

Para clientes de GCC do governo dos EUA, também é necessário adicionar os seguintes endereços IP à lista de permissões do firewall para fornecer acesso ao portal do Cloud App Security GCC High:

* 52.227.143.223
* 13.72.19.4

> [!NOTE]
> Para obter atualizações quando URLs e endereços IP forem alterados, assine o RSS conforme explicado em: [URLs e intervalos de endereços IP do Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).

## <a name="set-up-the-portal"></a>Configurar o portal

1. No portal de Cloud App Security, na barra de menus, clique no ícone configurações engrenagem ![configurações](media/settings-icon.png "Ícone de configurações") e selecione **configurações** para configurar os detalhes da sua organização.

1. Em **Detalhes da organização**, é importante que você forneça um **Nome de exibição da organização** para sua organização. Ele é exibido em emails e páginas da Web enviadas do sistema.

1. Forneça um **Nome do ambiente** (locatário). Essa informação é especialmente importante se você gerencia mais de um locatário.

1. Também é possível fornecer um **Logotipo** que é exibido em notificações por email e páginas da Web enviadas do sistema. O logotipo deve ser um arquivo png com um tamanho máximo de 150 x 50 pixels em uma tela de fundo transparente.

1. Certifique-se de adicionar uma lista de seus **domínios gerenciados** para identificar usuários internos. A adição de domínios gerenciados é uma etapa crucial. O Cloud App Security usa os domínios gerenciados para determinar quais usuários são internos, externos e em que locais os arquivos devem e não devem ser compartilhados. Essas informações são usadas para relatórios e alertas.

    * Os usuários em domínios que não estão configurados como internos são marcados como externos. Os usuários externos não são verificados quanto a arquivos ou atividades.

1. Em **saída automática**, especifique a quantidade de tempo que uma sessão pode permanecer inativa antes que a sessão seja desconectada automaticamente.

1. Se você estiver se integrando com a integração da Proteção de Informações do Azure, confira [Integração da Proteção de Informações do Azure](azip-integration.md) para obter informações.

    * Para trabalhar com a integração da Proteção de Informações do Azure, habilite o [Conector de aplicativos para o Office 365](connect-office-365-to-microsoft-cloud-app-security.md).

1. Se você estiver integrando com o Microsoft defender para integração de identidade, consulte [integração do Microsoft defender para identidade](azip-integration.md) para obter informações.

1. Se a qualquer momento você desejar fazer o backup das suas configurações do portal, essa tela permitirá que você faça isso. Clique em **exportar configurações do portal** para criar um arquivo JSON de todas as configurações do portal, incluindo regras de política, grupos de usuários e intervalos de endereços IP.

> [!NOTE]
> Se você usa o ExpressRoute, o Cloud App Security é implantado no Azure e totalmente integrado com o [ExpressRoute](/azure/expressroute/expressroute-introduction). Todas as interações com os aplicativos Cloud App Security e o tráfego enviados para Cloud App Security, incluindo o carregamento de logs de descoberta, são roteadas por meio do ExpressRoute para melhorar a latência, o desempenho e a segurança. Não há nenhuma etapa de configuração necessária do lado do cliente.
>
> Para obter mais informações sobre o emparelhamento público, consulte [Circuitos da Rota Expressa e domínios de roteamento](/azure/expressroute/expressroute-circuit-peerings).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Configurar Cloud Discovery](set-up-cloud-discovery.md)

[!INCLUDE [Open support ticket](includes/support.md)]
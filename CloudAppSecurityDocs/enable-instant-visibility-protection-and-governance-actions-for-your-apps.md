---
title: Conecte os aplicativos para obter visibilidade e controle Cloud App Security | Microsoft Docs
description: Este artigo descreve o processo de conexão de aplicativos com conectores de API para aplicativos na nuvem da sua organização.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 11/12/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 0aa55a99017a1768bf58fd2c2a40688c1a5c95e6
ms.sourcegitcommit: 4f3883a9e85d0aaf2802b10433b221c3f1838d88
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79285340"
---
# <a name="connect-apps"></a>Conectar aplicativos

*Aplica-se a: Microsoft Cloud App Security*

Os conectores de aplicativos usam as APIs dos provedores de aplicativos para permitir maior visibilidade e controle pelo Microsoft Cloud App Security sobre os aplicativos aos quais você se conecta.

Microsoft Cloud App Security aproveita as APIs fornecidas pelo provedor de nuvem. Cada serviço tem sua própria estrutura e limitações de API, como limitação, limites de API, janelas de API de mudança de tempo dinâmicas e outros. Microsoft Cloud App Security trabalhou com os serviços para otimizar o uso das APIs e para fornecer o melhor desempenho. Levando em conta diferentes limitações que os serviços impõem nas APIs, os mecanismos de Cloud App Security usam a capacidade permitida. Algumas operações, como a verificação de todos os arquivos no locatário, exigem várias APIs para que fiquem espalhadas por um período mais longo. Espere algumas que algumas políticas sejam executadas por várias horas ou vários dias.

## <a name="multi-instance-support"></a>Suporte a várias instâncias

Cloud App Security dá suporte a várias instâncias do mesmo aplicativo conectado. Por exemplo, se você tiver mais de uma instância do Salesforce (uma para vendas, uma para marketing), poderá se conectar tanto ao Cloud App Security. Você pode gerenciar as diferentes instâncias do mesmo console para criar políticas granulares e uma investigação mais profunda. Esse suporte se aplica somente a aplicativos conectados à API, não a aplicativos descobertos na nuvem ou a aplicativos conectados por proxy.

> [!NOTE]
> Não há suporte para várias instâncias no Office 365 e no Azure.

## <a name="how-it-works"></a>Como funciona

O Cloud App Security é implantado com privilégios de administrador do sistema para permitir o acesso completo a todos os objetos em seu ambiente.

O fluxo do Conector de Aplicativos é da maneira a seguir:

1. Cloud App Security examina e salva as permissões de autenticação.
2. A Segurança de Aplicativo de Nuvem solicita a lista de usuários. Na primeira vez que a solicitação for concluída, pode levar algum tempo até que a verificação seja concluída. Depois que a verificação do usuário for encerrada, a Segurança de Aplicativo de Nuvem continuará com as atividades e arquivos. Assim que a verificação for iniciada, algumas atividades estarão disponíveis na Segurança de Aplicativo de Nuvem.
3. Após a conclusão da solicitação do usuário, Cloud App Security verifica periodicamente os usuários, os grupos, as atividades e os arquivos. Todas as atividades estarão disponíveis após a primeira verificação.

Essa conexão pode levar algum tempo, dependendo do tamanho do locatário, do número de usuários e do tamanho e do número de arquivos que precisam ser verificados.

Dependendo do aplicativo ao qual você está se conectando, a conexão de API habilita os seguintes itens:

- **Informações da conta** -visibilidade de usuários, contas, informações de perfil, grupos de status (suspensos, ativos, desabilitados) e privilégios.

- **Trilha de auditoria** -visibilidade das atividades do usuário, atividades administrativas, atividade de entrada.

- **Verificação de dados** – verificação de dados não estruturados usando dois processos – periodicamente (a cada 12 horas) e verificação em tempo real (disparada sempre que uma alteração é detectada).

- **Permissões de aplicativo** -visibilidade de tokens emitidos e suas permissões.

- **Governança de conta** – capacidade de suspender usuários, revogar senhas etc.

- **Governança de dados** – capacidade de colocar arquivos em quarentena, incluindo arquivos na lixeira e substituir arquivos.

- **Governança de permissão do aplicativo** – capacidade de remover tokens.

A tabela a seguir lista por aplicativo de nuvem, quais recursos têm suporte com os conectores de aplicativo:

> [!div class="mx-tableFixed"]
>
> | | AWS | Caixa | Dropbox | GCP | G Suite | Office 365 | Okta | Service Now | Salesforce | Webex | Jornada de trabalho |
> |-|-|-|-|-|-|-|-|-|-|-|-|
> | **Listar contas** | ✔ | ✔ | ✔ | Conexão do pacote G do assunto | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |
> | **Listar grupos** | ✔ | ✔ | ✔ | Conexão do pacote G do assunto | ✔ | ✔ | ✔ | ✔ | ✔ | | Sem suporte pelo provedor |
> | **Listar privilégios** | | ✔ | ✔ | Conexão do pacote G do assunto | ✔ | ✔ | Sem suporte pelo provedor | ✔ | ✔ | ✔ | Não pported por provedor |
> | **Governança de usuário** | | ✔ | Em breve | Conexão do pacote G do assunto | ✔ | ✔ | | Em breve | ✔ | Em breve | t com suporte do provedor |
> | **Atividade de logon** | ✔ | ✔ | ✔ | Conexão do pacote G do assunto | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |
> | **Atividade do usuário** | Não aplicável | ✔ | ✔ | ✔ | ✔-requer o Google Business ou Enterprise | ✔ | ✔ | Parcial | Com suporte com o lesforce Shield | ✔ | ✔ |
> | **Atividade administrativa** | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | Parcial | ✔ | ✔ | Sem suporte pelo provedor |
> | **DLP – verificação periódica** | | ✔ | Em breve | Não aplicável | ✔ | ✔ | Não aplicável | | | | Sem suporte do ovider |
> | **DLP – verificação quase em tempo real** | | ✔ | ✔ | Não aplicável | ✔-requer o Google Business Enterprise | ✔ | Não aplicável | ✔ | ✔ | ✔ | Sem suporte pelo provedor |
> | **Controle de compartilhamento** | ✔ | ✔ | ✔ | Não aplicável | ✔ | ✔ | Não aplicável | Não aplicável | | ✔ | Sem suporte do ovider |
> | **Governança de arquivos** | ✔ | ✔ | ✔ | Não aplicável | ✔ | ✔ | Não aplicável | | ✔ | | Sem suporte pelo provedor |
> | **Exibir permissões de aplicativo** | Não aplicável | Sem suporte pelo provedor | Chegando em | Não aplicável | ✔ | ✔ | Não aplicável | | ✔ | Não aplicável | Não aplicável |
> | **Revogar permissões de aplicativo** | Não aplicável | Sem suporte pelo provedor | Ming em breve | Não aplicável | ✔ | ✔ | Não aplicável | | ✔ | Não aplicável | Não aplicável |
> | **Aplicar rótulos da proteção de informações do Azure** | Não aplicável | ✔ | | Não aplicável | ✔ | ✔ | Não aplicável | | | Não aplicável | Não aplicável |

## <a name="prerequisites"></a>Prerequisites

- Para alguns aplicativos, pode ser necessário para os endereços IP da lista branca para permitir que Cloud App Security coletem logs e forneçam acesso ao console do Cloud App Security. Para obter mais informações, consulte [requisitos de rede](network-requirements.md).

- Para cada aplicativo que desejar conectar com a integração de API do Cloud App Security, recomendamos criar uma conta de serviço de administrador dedicada ao Cloud App Security.

> [!NOTE]
> Para obter atualizações quando URLs e endereços IP forem alterados, assine o RSS conforme explicado em: [URLs e intervalos de endereços IP do Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).

Para usar os conectores de aplicativos, você precisa verificar se tem os seguintes itens para cada aplicativo específico:

| Aplicativo | Tipo de licença | User |
|-----|--------------|------|
| Azure | | Administrador global |
| AWS | | Usuário recém-criado |
| Caixa | Enterprise | É altamente recomendável que você se conecte ao box como um administrador. Conectar-se como um coadministrador resultará em apenas visibilidade parcial dos dados. Se você se conectar como um coadministrador, certifique-se de selecionar todas as permissões. |
| Dropbox | Business/Enterprise | Administração |
| GCP | | Consulte os [pré-requisitos do Connect GCP](connect-google-gcp-to-microsoft-cloud-app-security.md#prerequisites) |
| G Suite | G Suite Business ou Enterprise preferido<br /><br />G Suite Enterprise (no mínimo) | Superadministrador |
| Office 365 | | Administrador global |
| Okta | Enterprise (não de avaliação) | Administração |
| Salesforce | | Administração |
| ServiceNow | Eureka e superior | Função admin + RestAPI |
| Webex | | Admin + administrador de conformidade |
| Jornada de trabalho | | Consulte os [pré-requisitos do workday de conexão](connect-workday-to-microsoft-cloud-app-security.md#prerequisites) |

### <a name="expressroute"></a>ExpressRoute

O Cloud App Security é implantado no Azure e totalmente integrado com o [ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-introduction/). Todas as interações com os aplicativos Cloud App Security e o tráfego enviados para Cloud App Security, incluindo o carregamento de logs de descoberta, são roteadas por meio do **emparelhamento público** do ExpressRoute para melhorar a latência, o desempenho e a segurança. Não há nenhuma etapa de configuração necessária do lado do cliente.
Para obter mais informações sobre o emparelhamento público, consulte [Circuitos da ExpressRoute e domínios de roteamento](https://azure.microsoft.com/documentation/articles/expressroute-circuit-peerings/).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]

## <a name="check-out-this-video"></a>Confira este vídeo!

> [!div class="nextstepaction"]
> [Microsoft Cloud App Security – APIs REST e tokens](https://channel9.msdn.com/Shows/Microsoft-Security/Microsoft-Cloud-App-Security--REST-APIs-and-Tokens)

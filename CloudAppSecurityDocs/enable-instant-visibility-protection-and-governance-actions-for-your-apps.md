---
title: Conectar aplicativos para obter visibilidade e controle – Cloud App Security | Microsoft Docs
description: Este artigo descreve o processo para conexão de aplicativos com conectores de API aos aplicativos na nuvem de sua organização.
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
ms.sourcegitcommit: 7c93b6f93d2699d466b172590710ed01697bbdad
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74720248"
---
# <a name="connect-apps"></a>Conectar aplicativos

*Aplica-se ao: Microsoft Cloud App Security*

Os conectores de aplicativos usam as APIs de provedores de aplicativos para permitir maior visibilidade e controle com o Microsoft Cloud App Security sobre os aplicativos aos quais você se conecta.

O Microsoft Cloud App Security aproveita as APIs fornecidas pelo provedor de nuvem. Cada serviço tem sua própria estrutura e limitações de API como limitação, limites de API, janelas de API de mudança de tempo dinâmicas e outros. O Microsoft Cloud App Security trabalhou com os serviços para otimizar o uso das APIs e garantir o melhor desempenho. Levando em conta diferentes limitações impostas pelos serviços sobre as APIs, os mecanismos do Cloud App Security usam a capacidade permitida. Algumas operações, como verificação de todos os arquivos no locatário, exigem várias APIs e, portanto, elas são distribuídas por um período mais longo. Espere algumas que algumas políticas sejam executadas por várias horas ou vários dias.

## <a name="multi-instance-support"></a>Suporte para várias instâncias

O Cloud App Security agora dá suporte a várias instâncias do mesmo aplicativo conectado. Por exemplo, caso você tenha mais de uma instância do Salesforce (uma para venda, uma para marketing), poderá conectar as duas ao Cloud App Security. Você pode gerenciar as diferentes instâncias no mesmo console para criar políticas granulares e uma investigação mais profunda. Esse suporte se aplica somente a aplicativos conectados por API, e não a aplicativos descobertos na nuvem ou aplicativos conectados por proxy.

> [!NOTE]
> Não há suporte para várias instâncias no Office 365 e no Azure.

## <a name="how-it-works"></a>Como funciona

O Cloud App Security é implantado com privilégios de administrador do sistema para permitir o acesso completo a todos os objetos em seu ambiente.

O fluxo do Conector de Aplicativos é da maneira a seguir:

1. O Cloud App Security examina e salva as permissões de autenticação.
2. A Segurança de Aplicativo de Nuvem solicita a lista de usuários. Na primeira vez que a solicitação é feita, é necessário algum tempo até que a verificação seja concluída. Depois que a verificação do usuário for encerrada, a Segurança de Aplicativo de Nuvem continuará com as atividades e arquivos. Assim que a verificação for iniciada, algumas atividades estarão disponíveis na Segurança de Aplicativo de Nuvem.
3. Após a conclusão da solicitação do usuário, o Cloud App Security examina periodicamente usuários, grupos, atividades e arquivos. Todas as atividades estarão disponíveis após a primeira verificação.

Essa conexão pode levar algum tempo, dependendo do tamanho do locatário, do número de usuários e do tamanho e número de arquivos que precisam ser examinados.

Dependendo do aplicativo ao qual você está se conectando, a conexão de API permite os seguintes itens:

- **Dados da conta** – visibilidade de usuários, contas, informações de perfil, grupos de status (suspenso, ativo, desabilitado) e privilégios.

- **Trilha de auditoria** – visibilidade das atividades do usuário, atividades de administração e atividades de entrada.

- **Verificação de dados** – verificação de dados não estruturados usando dois processos: periodicamente (a cada 12 horas) e verificação em tempo real (disparada sempre que uma alteração é detectada).

- **Permissões de aplicativo** – visibilidade dos tokens emitidos e suas permissões.

- **Governança de conta** – capacidade de suspender usuários, revogar senhas, etc.

- **Governança de Dados** – capacidade de colocar arquivos em quarentena, incluindo arquivos na lixeira, bem como de substituir arquivos.

- **Governança de permissão do aplicativo** – capacidade de remover tokens.

A tabela a seguir lista por aplicativo de nuvem, quais recursos têm suporte com os conectores de aplicativo:

> [!div class="mx-tableFixed"]
>
> | | AWS | Caixa | Dropbox | GCP | G Suite | Office 365 | Okta | Serviço agora | Salesforce | WebEx | Workday |
> |-|-|-|-|-|-|-|-|-|-|-|-|
> | **Listar contas** | ✔ | ✔ | ✔ | Conexão do pacote G do assunto | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |
> | **Listar grupos** | ✔ | ✔ | ✔ | Conexão do pacote G do assunto | ✔ | ✔ | ✔ | ✔ | ✔ | | Sem suporte pelo provedor |
> | **Listar privilégios** | | ✔ | ✔ | Conexão do pacote G do assunto | ✔ | ✔ | Sem suporte pelo provedor | ✔ | ✔ | ✔ | Não pported por provedor |
> | **Governança de usuário** | | ✔ | Em breve | Conexão do pacote G do assunto | ✔ | ✔ | | Em breve | ✔ | Em breve | t com suporte do provedor |
> | **Atividade de logon** | ✔ | ✔ | ✔ | Conexão do pacote G do assunto | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |
> | **Atividade do usuário** | Não Aplicável | ✔ | ✔ | ✔ | ✔ – requer o Google Business ou Enterprise | ✔ | ✔ | Parcial | Com suporte com o lesforce Shield | ✔ | ✔ |
> | **Atividade administrativa** | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | Parcial | ✔ | ✔ | Sem suporte pelo provedor |
> | **DLP – verificação periódica** | | ✔ | Em breve | Não Aplicável | ✔ | ✔ | Não Aplicável | | | | Sem suporte do ovider |
> | **DLP – verificação quase em tempo real** | | ✔ | ✔ | Não Aplicável | ✔-requer o Google Business Enterprise | ✔ | Não Aplicável | ✔ | ✔ | ✔ | Sem suporte pelo provedor |
> | **Controle de compartilhamento** | ✔ | ✔ | ✔ | Não Aplicável | ✔ | ✔ | Não Aplicável | Não Aplicável | | ✔ | Sem suporte do ovider |
> | **Governança de arquivos** | ✔ | ✔ | ✔ | Não Aplicável | ✔ | ✔ | Não Aplicável | | ✔ | | Sem suporte pelo provedor |
> | **Exibir permissões de aplicativo** | Não Aplicável | Sem suporte pelo provedor | Chegando em | Não Aplicável | ✔ | ✔ | Não Aplicável | | ✔ | Não Aplicável | Não Aplicável |
> | **Revogar permissões de aplicativo** | Não Aplicável | Sem suporte pelo provedor | Ming em breve | Não Aplicável | ✔ | ✔ | Não Aplicável | | ✔ | Não Aplicável | Não Aplicável |
> | **Aplique os rótulos da Proteção de Informações do Azure** | Não Aplicável | ✔ | | Não Aplicável | ✔ | ✔ | Não Aplicável | | | Não Aplicável | Não Aplicável |

## <a name="prerequisites"></a>Pré-requisitos

- Em alguns aplicativos, pode ser necessário adicionar endereços IP à lista de permissões para permitir que o Cloud App Security colete logs e forneça acesso ao console do Cloud App Security. Para obter mais informações, confira [Requisitos de rede](network-requirements.md).

- Para cada aplicativo que desejar conectar com a integração de API do Cloud App Security, recomendamos criar uma conta de serviço de administrador dedicada ao Cloud App Security.

> [!NOTE]
> Para obter atualizações quando URLs e endereços IP forem alterados, assine o RSS conforme explicado em: [URLs e intervalos de endereços IP do Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).

Para usar Conectores de Aplicativos, você precisa ter certeza de que tem os seguintes itens para cada aplicativo específico:

| Aplicativo | Tipo de licença | User |
|-----|--------------|------|
| Azure | | Administrador global |
| AWS | | Usuário recém-criado |
| Caixa | Enterprise | É altamente recomendável que você se conecte ao box como um administrador. Conectar-se como um coadministrador resultará em apenas visibilidade parcial dos dados. Se você se conectar como Coadministrador, lembre-se de selecionar todas as permissões. |
| Dropbox | Business/Enterprise | Administração |
| GCP | | Consulte os [pré-requisitos do Connect GCP](connect-google-gcp-to-microsoft-cloud-app-security.md#prerequisites) |
| G Suite | G Suite Business ou Enterprise preferencial<br /><br />G Suite Enterprise (no mínimo) | Superadministrador |
| Office 365 | | Administrador global |
| Okta | Enterprise (não de avaliação) | Administração |
| Salesforce | | Administração |
| ServiceNow | Eureka e superior | Função admin + RestAPI |
| WebEx | | Admin + administrador de conformidade |
| Workday | | Consulte os [pré-requisitos do workday de conexão](connect-workday-to-microsoft-cloud-app-security.md#prerequisites) |

### <a name="expressroute"></a>ExpressRoute

O Cloud App Security é implantado no Azure e totalmente integrado com o [ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-introduction/). Todas as interações com os aplicativos do Cloud App Security e o tráfego enviado a ele, incluindo o upload de logs de descoberta, são roteados por meio do **emparelhamento público** do ExpressRoute para aprimorar a latência, o desempenho e a segurança. Não há nenhuma etapa de configuração necessária do lado do cliente.
Para obter mais informações sobre o emparelhamento público, consulte [Circuitos da Rota Expressa e domínios de roteamento](https://azure.microsoft.com/documentation/articles/expressroute-circuit-peerings/).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]

## <a name="check-out-this-video"></a>Confira este vídeo!

> [!div class="nextstepaction"]
> [Microsoft Cloud App Security – API REST e Tokens](https://channel9.msdn.com/Shows/Microsoft-Security/Microsoft-Cloud-App-Security--REST-APIs-and-Tokens)

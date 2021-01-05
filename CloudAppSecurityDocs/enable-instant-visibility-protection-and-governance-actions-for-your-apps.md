---
title: Conectar aplicativos para obter visibilidade e controle
description: Este artigo descreve o processo para conexão de aplicativos com conectores de API aos aplicativos na nuvem de sua organização.
ms.date: 01/05/2021
ms.topic: how-to
ms.openlocfilehash: 1df724883ff1944e0ff5c1e62c1fe6fbcaef233a
ms.sourcegitcommit: ee66e70f711aa11501e308e53b1a4b46f2175e4e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97894647"
---
# <a name="connect-apps"></a>Conectar aplicativos

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Os conectores de aplicativos usam as APIs de provedores de aplicativos para permitir maior visibilidade e controle pelo Microsoft Cloud App Security sobre os aplicativos aos quais você se conecta.

O Microsoft Cloud App Security aproveita as APIs fornecidas pelo provedor de nuvem. Toda a comunicação entre Cloud App Security e aplicativos conectados é criptografada usando HTTPS. Cada serviço tem a própria estrutura e limitações de API, como limitação, limites de API, janelas de API de mudança de tempo dinâmica e outros. O Microsoft Cloud App Security trabalhou com os serviços para otimizar o uso das APIs e garantir o melhor desempenho. Levando em conta diferentes limitações impostas pelos serviços sobre as APIs, os mecanismos do Cloud App Security usam a capacidade permitida. Algumas operações, como verificação de todos os arquivos no locatário, exigem várias APIs e, portanto, elas são distribuídas por um período mais longo. Espere algumas que algumas políticas sejam executadas por várias horas ou vários dias.

## <a name="multi-instance-support"></a>Suporte de várias instâncias

O Cloud App Security agora dá suporte a várias instâncias do mesmo aplicativo conectado. Por exemplo, caso você tenha mais de uma instância do Salesforce (uma para venda, uma para marketing), poderá conectar as duas ao Cloud App Security. Você pode gerenciar as diferentes instâncias no mesmo console para criar políticas granulares e uma investigação mais profunda. Esse suporte se aplica somente a aplicativos conectados por API, e não a aplicativos descobertos na nuvem ou aplicativos conectados por proxy.

> [!NOTE]
> Não há suporte para várias instâncias no Office 365 e no Azure.

## <a name="how-it-works"></a>Como ele funciona

O Cloud App Security é implantado com privilégios de administrador do sistema para permitir o acesso completo a todos os objetos em seu ambiente.

O fluxo do Conector de Aplicativos é da maneira a seguir:

1. O Cloud App Security examina e salva as permissões de autenticação.
2. A Segurança de Aplicativo de Nuvem solicita a lista de usuários. Na primeira vez que a solicitação é feita, é necessário algum tempo até que a verificação seja concluída. Depois que a verificação do usuário for encerrada, a Segurança de Aplicativo de Nuvem continuará com as atividades e arquivos. Assim que a verificação for iniciada, algumas atividades estarão disponíveis na Segurança de Aplicativo de Nuvem.
3. Após a conclusão da solicitação do usuário, o Cloud App Security examina periodicamente usuários, grupos, atividades e arquivos. Todas as atividades estarão disponíveis após a primeira verificação.

Essa conexão pode levar algum tempo, dependendo do tamanho do locatário, do número de usuários e do tamanho e número de arquivos que precisam ser examinados.

Dependendo do aplicativo ao qual você está se conectando, a conexão de API permite os seguintes itens:

- **Dados da conta** – visibilidade de usuários, contas, informações de perfil, grupos de status (suspenso, ativo, desabilitado) e privilégios.

- **Trilha de auditoria** -visibilidade das atividades do usuário, atividades administrativas, atividades de entrada.

- **Verificação de dados** – verificação de dados não estruturados usando dois processos: periodicamente (a cada 12 horas) e verificação em tempo real (disparada sempre que uma alteração é detectada).

- **Permissões de aplicativo** – visibilidade dos tokens emitidos e suas permissões.

- **Governança de conta** – capacidade de suspender usuários, revogar senhas, etc.

- **Governança de Dados** – capacidade de colocar arquivos em quarentena, incluindo arquivos na lixeira, bem como de substituir arquivos.

- **Governança de permissão do aplicativo** – capacidade de remover tokens.

A tabela a seguir lista por aplicativo de nuvem, quais recursos têm suporte com os conectores de aplicativo:

| | AWS | Box | Dropbox | GitHub | GCP | Google Workspace | Office 365 | Okta | Service Now | Salesforce | Webex | Workday |
|-|-|-|-|-|-|-|-|-|-|-|-|-|
| **Listar contas** | ✔ | ✔ | ✔ | ✔ | Entidade de conexão do Google Workspace | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |
| **Listar grupos** | ✔ | ✔ | ✔ | ✔ | Entidade de conexão do Google Workspace | ✔ | ✔ | ✔ | ✔ | ✔ | | Sem suporte pelo provedor |
| **Listar privilégios** | | ✔ | ✔ | ✔ | Entidade de conexão do Google Workspace | ✔ | ✔ | Sem suporte pelo provedor | ✔ | ✔ | ✔ | Sem suporte pelo provedor |
| **Governança de usuário** | | ✔ | Em breve | | Entidade de conexão do Google Workspace | ✔ | ✔ | | | ✔ | | Sem suporte pelo provedor |
| **Atividade de logon** | ✔ | ✔ | ✔ | | Entidade de conexão do Google Workspace | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |
| **Atividade do usuário** | Não se aplica | ✔ | ✔ | ✔ | ✔ | ✔ – requer o Google Business ou Enterprise | ✔ | ✔ | Parcial | Com suporte com o Salesforce Shield | ✔ | ✔ |
| **Atividade administrativa** | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | Parcial | ✔ | ✔ | Sem suporte pelo provedor |
| **DLP – verificação periódica** | | ✔ | ✔ | | Não se aplica | ✔ | ✔ | Não se aplica | ✔ | ✔ | ✔ | Sem suporte pelo provedor |
| **DLP – verificação quase em tempo real** | | ✔ | | | Não se aplica | ✔-requer o Google Business Enterprise | ✔ | Não se aplica | | | ✔ | Sem suporte pelo provedor |
| **Controle de compartilhamento** | ✔ | ✔ | ✔ | | Não se aplica | ✔ | ✔ | Não se aplica | Não se aplica | | ✔ | Sem suporte pelo provedor |
| **Governança de arquivos** | ✔ | ✔ | ✔ | | Não se aplica | ✔ | ✔ | Não se aplica | | ✔ | | Sem suporte pelo provedor |
| **Exibir permissões de aplicativo** | Não se aplica | Sem suporte pelo provedor | Em breve | ✔ | Não se aplica | ✔ | ✔ | Não se aplica | | ✔ | Não se aplica | Não se aplica |
| **Revogar permissões de aplicativo** | Não se aplica | Sem suporte pelo provedor | Em breve | | Não se aplica | ✔ | ✔ | Não se aplica | | ✔ | Não se aplica | Não se aplica |
| **Aplique os rótulos da Proteção de Informações do Azure** | Não se aplica | ✔ | | | Não se aplica | ✔ | ✔ | Não se aplica | | | Não se aplica | Não se aplica |

## <a name="prerequisites"></a>Pré-requisitos

- Para alguns aplicativos, pode ser necessário permitir que os endereços IP da lista habilitem Cloud App Security para coletar logs e fornecer acesso ao console do Cloud App Security. Para obter mais informações, consulte [requisitos de rede](network-requirements.md).

- Para cada aplicativo que desejar conectar com a integração de API do Cloud App Security, recomendamos criar uma conta de serviço de administrador dedicada ao Cloud App Security.

> [!NOTE]
> Para obter atualizações quando URLs e endereços IP forem alterados, assine o RSS conforme explicado em: [URLs e intervalos de endereços IP do Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).

Para usar Conectores de Aplicativos, você precisa ter certeza de que tem os seguintes itens para cada aplicativo específico:

| Aplicativo | Tipo de licença | Usuário |
|-----|--------------|------|
| Azure | | Administrador global |
| AWS | | Usuário recém-criado |
| Box | Enterprise | É altamente recomendável que você se conecte ao box como um administrador. conectar-se como um coadministrador resultará em apenas visibilidade parcial dos dados. Se você se conectar como Coadministrador, lembre-se de selecionar todas as permissões. |
| Dropbox | Business/Enterprise | Administrador |
| GitHub | GitHub Enterprise Cloud | Proprietário |
| GCP | | Consulte os [pré-requisitos do Connect GCP](connect-google-gcp-to-microsoft-cloud-app-security.md#prerequisites) |
| Google Workspace | Do Google Workspace Business ou Enterprise preferido<br /><br />Google Workspace Enterprise (minimamente) | Superadministrador |
| Office 365 | | Administrador global |
| Okta | Enterprise (não de avaliação) | Administrador |
| Salesforce | | Administrador |
| ServiceNow | Eureka e superior | Função admin + RestAPI |
| Webex | | Admin + administrador de conformidade |
| Workday | | Consulte os [pré-requisitos do workday de conexão](connect-workday-to-microsoft-cloud-app-security.md#prerequisites) |

### <a name="expressroute"></a>ExpressRoute

O Cloud App Security é implantado no Azure e totalmente integrado com o [ExpressRoute](/azure/expressroute/expressroute-introduction). Todas as interações com os aplicativos Cloud App Security e o tráfego enviados para Cloud App Security, incluindo o carregamento de logs de descoberta, são roteadas por meio do ExpressRoute para melhorar a latência, o desempenho e a segurança. Não há nenhuma etapa de configuração necessária do lado do cliente.
Para obter mais informações sobre o emparelhamento público, consulte [Circuitos da Rota Expressa e domínios de roteamento](/azure/expressroute/expressroute-circuit-peerings).

## <a name="disable-app-connectors"></a>Desabilitar conectores de aplicativos

> [!NOTE]
>
> - Antes de desabilitar um conector de aplicativo, verifique se você tem os detalhes de conexão disponíveis, pois você precisará deles se quiser reabilitar o conector.
> - Essas etapas não podem ser usadas para desabilitar o conector do Azure.
> - Essas etapas não podem ser usadas para desabilitar Controle de Aplicativos de Acesso Condicional aplicativos e aplicativos de configuração de segurança.

Para desabilitar aplicativos conectados:

1. Na página **aplicativos conectados** , na linha relevante, clique nos três pontos e selecione **desabilitar conector de aplicativo**.
1. No pop-up, clique em **desabilitar instância do conector de aplicativo** para confirmar a ação.

Uma vez desabilitada, a instância do conector interromperá o consumo de dados do conector.

## <a name="re-enable-app-connectors"></a>Habilitar novamente os conectores de aplicativos

Para reabilitar os aplicativos conectados:

1. Na página **aplicativos conectados** , na linha relevante, clique nos três pontos e selecione **Editar aplicativo**. Isso inicia o processo para adicionar um conector.
1. Adicione o conector usando as etapas no guia do conector de API relevante. Por exemplo, se você estiver reabilitando o GitHub, use as etapas em [conectar o GitHub Enterprise Cloud a Cloud app Security](connect-github-ec-to-microsoft-cloud-app-security.md).

## <a name="related-videos"></a>Vídeos relacionados

> [!div class="nextstepaction"]
> [Conectando aplicativos de terceiros Webinar](webinars.md#on-demand-webinars)

> [!div class="nextstepaction"]
> [Microsoft Cloud App Security – APIs REST e tokens](https://channel9.msdn.com/Shows/Microsoft-Security/Microsoft-Cloud-App-Security--REST-APIs-and-Tokens)

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]

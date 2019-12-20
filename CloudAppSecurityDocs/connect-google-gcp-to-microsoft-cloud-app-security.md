---
title: Conectar Google Cloud Platform ao Cloud App Security
description: Este artigo fornece informações sobre como conectar seu Google Cloud Platform para Cloud App Security usando o conector de API para visibilidade e controle sobre o uso.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 10/16/2019
ms.topic: conceptual
ms.service: cloud-app-security
ms.collection: M365-security-compliance
ms.openlocfilehash: e03f24023968d9e3169aef8636061b8adf05d646
ms.sourcegitcommit: db5ec79d219dd6674939c872ace7cd2ca80860a4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75189733"
---
# <a name="connect-google-cloud-platform-to-microsoft-cloud-app-security-preview"></a>Conectar Google Cloud Platform ao Microsoft Cloud App Security (versão prévia)

*Aplica-se ao: Microsoft Cloud App Security*

Este artigo fornece instruções para conectar Microsoft Cloud App Security à sua conta do Google Cloud Platform (GCP) existente usando as APIs do conector. Essa conexão fornece visibilidade e controle sobre o uso do GCP. Para obter informações sobre como Cloud App Security protege o GCP, consulte [proteger o GCP](protect-gcp.md).

> [!NOTE]
> As instruções para conectar seu ambiente GCP seguem as [recomendações do Google](https://cloud.google.com/blog/products/gcp/best-practices-for-working-with-google-cloud-audit-logging) para consumir logs agregados. A integração aproveita o Google StackDriver e consumirá recursos adicionais que podem afetar sua cobrança. Os recursos consumidos são:
>
> * [Coletor de exportação agregado – nível da organização](https://cloud.google.com/logging/docs/export/aggregated_exports#concept)
> * [Mdb/subtópico – nível de projeto GCP](https://cloud.google.com/logging/docs/export/using_exported_logs#pubsub-overview)
> * [Assinatura pub/sub – nível de projeto GCP](https://cloud.google.com/logging/docs/export/using_exported_logs#pubsub-overview)
>
> Atualmente, Cloud App Security importa somente logs de auditoria de atividade de administrador; O acesso a dados e os logs de auditoria de eventos do sistema não são importados. Para obter mais informações sobre logs do GCP, consulte [logs de auditoria de nuvem](https://go.microsoft.com/fwlink/?linkid=2109230).

Recomendamos que você use um projeto dedicado para a integração e restrinja o acesso ao projeto para manter a integração estável e evitar exclusões/modificações do processo de instalação. Além disso, se sua instância do GCP fizer parte de uma instância do G Suite que já está conectada a Cloud App Security, recomendamos seguir o **para uma instância do GCP que faça parte de uma organização conectada do g Suite** quando você adicionar os detalhes de conexão do GCP.

## <a name="prerequisites"></a>Pré-requisitos

O usuário de integração do GCP deve ter as seguintes permissões:

* **Editar iam e admin** – nível da organização
* **Criação e edição de projeto**

## <a name="configure-google-cloud-platform"></a>Configurar Google Cloud Platform

* Entre no portal do GCP usando sua conta de usuário de integração do GCP.

### <a name="create-a-dedicated-project"></a>Criar um projeto dedicado

Crie um projeto dedicado no GCP em sua organização para habilitar o isolamento de integração e a estabilidade

1. Clique em **criar projeto** para iniciar um novo.
1. Na tela **novo projeto** , nomeie seu projeto e clique em **criar**.

    ![Captura de tela mostrando a caixa de diálogo Criar projeto do GCP](media/connect-gcp-create-project.png)

### <a name="enable-the-pubsub-api"></a>Habilitar a API pub/sub

1. Alterne para o projeto dedicado.
1. Vá para a guia pub/sub. Uma mensagem de ativação de serviço deve ser exibida.

### <a name="create-a-dedicated-service-account-for-the-integration"></a>Criar uma conta de serviço dedicada para a integração

1. Em **administrador de & iam**, clique em **contas de serviço**.
1. Clique em **criar conta de serviço** para criar uma conta de serviço dedicada.
1. Insira um nome de conta e, em seguida, clique em **criar**.
1. Especifique a **função** como **administrador pub/sub** e, em seguida, clique em **salvar**.

    ![Captura de tela mostrando GCP Adicionar função IAM](media/connect-gcp-iam-role.PNG)

1. Copie o valor de **email** , você precisará dele mais tarde.

    ![Captura de tela mostrando a caixa de diálogo conta de serviço GCP](media/connect-gcp-create-service-account.png)

1. Em **administrador de & iam**, clique em **iam**.

    1. Mudar para o nível da organização.
    1. Clique em **Adicionar**.
    1. Na caixa **novos membros** , Cole o valor de **email** que você copiou anteriormente.
    1. Especifique a **função** como **gravador de configuração de logs** e clique em **salvar**.

        ![Captura de tela mostrando a caixa de diálogo Adicionar membro](media/connect-gcp-add-member.png)

### <a name="create-a-private-key-for-the-dedicated-service-account"></a>Criar uma chave privada para a conta de serviço dedicada

1. Mudar para o nível de projeto.
1. Em **administrador de & iam**, clique em **contas de serviço**.
1. Abra a conta de serviço dedicada e clique em **Editar**.
1. Clique em **criar chave**.
1. Na tela **criar chave privada** , selecione **JSON**e, em seguida, clique em **criar**.

    ![Captura de tela mostrando a caixa de diálogo Criar chave privada](media/connect-gcp-create-private-key.png)

    > [!NOTE]
    > Você precisará do arquivo JSON que é baixado em seu computador mais tarde.

### <a name="retrieve-your-organization-id"></a>Recuperar a ID da sua organização

Anote a ID da sua **organização**. você precisará dela mais tarde. Para obter mais informações, consulte [obtendo a ID da sua organização](https://cloud.google.com/resource-manager/docs/creating-managing-organization#retrieving_your_organization_id).
    ![captura de tela mostrando a caixa de diálogo ID da organização](media/connect-gcp-org-id.png)

## <a name="configure-cloud-app-security"></a>Configurar o Microsoft Cloud App Security

* No portal do Cloud App Security, clique em **Investigar** e em **Aplicativos conectados**.

### <a name="add-the-gcp-connection-details"></a>Adicionar os detalhes de conexão do GCP

Para fornecer os detalhes de conexão do GCP, em **conectores de aplicativos**, siga um destes procedimentos:

**Para uma instância do GCP que não faz parte de uma organização do G Suite conectada**

1. Clique no sinal de adição seguido por **Google Cloud Platform**.

    ![Captura de tela mostrando o menu Adicionar GCP](media/connect-gcp-add.png)

1. No pop-up, forneça um nome para o conector e clique em **conectar Google Cloud Platform**.

1. Na página Google Cloud Platform, faça o seguinte:
    1. Na caixa **ID da organização** , insira a organização que você fez antes.
    1. Na caixa **arquivo de chave privada** , navegue até o arquivo JSON baixado anteriormente.
    1. Clique em **conectar Google Cloud Platform**.

    > [!NOTE]
    > Recomendamos que você conecte sua instância do G Suite para obter governança e gerenciamento de usuários unificados. Isso é recomendado mesmo que você não use nenhum produto G Suite e os usuários do GCP sejam gerenciados por meio do sistema de gerenciamento de usuários do G Suite.

**Para uma instância do GCP que faz parte de uma organização do G Suite conectada**

1. Na lista de instâncias conectadas, no final da linha em que o conector G Suite aparece, clique nos três pontos e, em seguida, clique em **adicionar Google Cloud Platform**.

1. Na página Google Cloud Platform, faça o seguinte:
    1. Na caixa **ID da organização** , insira a organização que você fez antes.
    1. Na caixa **arquivo de chave privada** , navegue até o arquivo JSON baixado anteriormente.
    1. Clique em **conectar Google Cloud Platform**.

    > [!NOTE]
    > Isso habilita o gerenciamento de usuário unificado e governança por meio do realm de identidade de usuário do G Suite.

### <a name="test-the-connection"></a>Testar a conexão

Certifique-se de que a conexão foi bem-sucedida clicando em **Testar API**.

O teste pode levar alguns minutos. Quando ele for concluído, você receberá uma notificação de Êxito ou Falha. Depois de receber uma notificação de êxito, clique em **Concluído**.

## <a name="aggregated-export-sink"></a>Coletor de exportação agregado

Atualmente, desabilitar o coletor de exportação agregado só é possível por meio do Google Cloud Shell.

### <a name="to-disable-aggregated-export-sink"></a>Para desabilitar o coletor de exportação agregado

| Etapa | Script | Para obter mais informações |
|-|-|-|
| 1. iniciar uma sessão do Google Cloud Shell. | | [Usando Cloud Shell](https://cloud.google.com/shell/docs/using-cloud-shell) |
| 2. defina o projeto atual. | `gcloud config set project {PROJECT_ID}` | [conjunto de configuração gcloud](https://cloud.google.com/sdk/gcloud/reference/config/set) |
| 3. liste os coletores de nível de organização. | `gcloud logging sinks list --organization={ORGANIZATION_ID}` | [lista de coletores de log gcloud](https://cloud.google.com/sdk/gcloud/reference/logging/sinks/list) |
| 4. exclua o coletor relevante. | `gcloud logging sinks delete {SINK_NAME} --organization={ORGANIZATION_ID}` | [exclusão de coletores de log gcloud](https://cloud.google.com/sdk/gcloud/reference/logging/sinks/delete) |

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]

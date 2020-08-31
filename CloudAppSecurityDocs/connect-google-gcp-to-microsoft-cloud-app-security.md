---
title: Conectar Google Cloud Platform ao Cloud App Security
description: Este artigo fornece informações sobre como conectar seu Google Cloud Platform para Cloud App Security usando o conector de API para visibilidade e controle sobre o uso.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 06/28/2020
ms.topic: how-to
ms.service: cloud-app-security
ms.collection: M365-security-compliance
ms.openlocfilehash: 60710c450515b6cf7cf355b3dc370798df24cbe8
ms.sourcegitcommit: c174a7ada5c6a14f0fea9870672898c54e5e3b52
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89149883"
---
# <a name="connect-google-cloud-platform-to-microsoft-cloud-app-security"></a>Conectar Google Cloud Platform ao Microsoft Cloud App Security

*Aplica-se a: Microsoft Cloud App Security*

Este artigo fornece instruções para conectar Microsoft Cloud App Security à sua conta do Google Cloud Platform (GCP) existente usando as APIs do conector. Essa conexão fornece visibilidade e controle sobre o uso do GCP. Para obter informações sobre como Cloud App Security protege o GCP, consulte [proteger o GCP](protect-gcp.md).

Recomendamos que você use um projeto dedicado para a integração e restrinja o acesso ao projeto para manter a integração estável e evitar exclusões/modificações do processo de instalação. Além disso, se sua instância do GCP fizer parte de uma instância do G Suite que já está conectada a Cloud App Security, recomendamos seguir o **para uma instância do GCP que faça parte de uma organização conectada do g Suite** quando você adicionar os detalhes de conexão do GCP.

## <a name="prerequisites"></a>Pré-requisitos

O usuário de integração do GCP deve ter as seguintes permissões:

- **Editar iam e admin** – nível da organização
- **Criação e edição de projeto**

Você pode conectar um ou ambos os GCP a seguir para Cloud App Security conexões:

- **Auditoria de segurança**: essa conexão fornece visibilidade e controle sobre o uso do aplicativo GCP.
- **Configuração de segurança**: essa conexão fornece recomendações de segurança fundamentais com base no parâmetro de comparação de CIS (Center for Internet Security) para GCP.

Como você pode adicionar uma ou ambas as conexões, as etapas neste artigo são escritas como instruções independentes. Se você já tiver adicionado uma das conexões, quando relevante, edite as configurações existentes.

## <a name="how-to-connect-gcp-security-auditing-to-cloud-app-security"></a>Como conectar a auditoria de segurança do GCP ao Cloud App Security

Conectar a auditoria de segurança do GCP fornece visibilidade e controle sobre o uso do aplicativo GCP.

Siga estas etapas para conectar a auditoria de segurança do GCP ao Cloud App Security.

> [!div class="checklist"]
>
> - [Configurar Google Cloud Platform](#configure-google-cloud-platform)
> - [Conectar Google Cloud Platform auditoria ao Cloud App Security](#connect-google-cloud-platform-auditing-to-cloud-app-security)
> - [Coletor de exportação agregado](#aggregated-export-sink)

### <a name="configure-google-cloud-platform"></a>Configurar Google Cloud Platform

> [!NOTE]
> As instruções para conectar seu ambiente GCP para auditoria seguem as [recomendações do Google](https://cloud.google.com/blog/products/gcp/best-practices-for-working-with-google-cloud-audit-logging) para consumir logs agregados. A integração aproveita o Google StackDriver e consumirá recursos adicionais que podem afetar sua cobrança. Os recursos consumidos são:
>
> - [Coletor de exportação agregado – nível da organização](https://cloud.google.com/logging/docs/export/aggregated_exports#concept)
> - [Mdb/subtópico – nível de projeto GCP](https://cloud.google.com/logging/docs/export/using_exported_logs#pubsub-overview)
> - [Assinatura pub/sub – nível de projeto GCP](https://cloud.google.com/logging/docs/export/using_exported_logs#pubsub-overview)
>
> A conexão de auditoria Cloud App Security somente importa logs de auditoria de atividade de administrador; O acesso a dados e os logs de auditoria de eventos do sistema não são importados. Para obter mais informações sobre logs do GCP, consulte [logs de auditoria de nuvem](https://go.microsoft.com/fwlink/?linkid=2109230).

#### <a name="create-a-dedicated-project"></a>Criar um projeto dedicado

Crie um projeto dedicado no GCP em sua organização para habilitar o isolamento de integração e a estabilidade

1. Entre no portal do GCP usando sua conta de usuário de integração do GCP.
1. Clique em **criar projeto** para iniciar um novo.
1. Na tela **novo projeto** , nomeie seu projeto e clique em **criar**.

    ![Captura de tela mostrando a caixa de diálogo Criar projeto do GCP](media/connect-gcp-create-project.png)

#### <a name="enable-required-apis"></a>Habilitar APIs necessárias

1. Alterne para o projeto dedicado.
1. Vá para a guia **biblioteca** .
1. Procure e selecione **API de log de nuvem**e, em seguida, na página da API, clique em **habilitar**.
1. Pesquise e selecione **API pub/sub de nuvem**e, na página da API, clique em **habilitar**.

    > [!NOTE]
    > Certifique-se de não selecionar **API pub/sub Lite**.

#### <a name="create-a-dedicated-service-account-for-the-security-auditing-integration"></a>Criar uma conta de serviço dedicada para a integração de auditoria de segurança

1. Em **administrador de & iam**, clique em **contas de serviço**.
1. Clique em **criar conta de serviço** para criar uma conta de serviço dedicada.
1. Insira um nome de conta e, em seguida, clique em **criar**.
1. Especifique a **função** como **administrador pub/sub** e, em seguida, clique em **salvar**.

    ![Captura de tela mostrando GCP Adicionar função IAM](media/connect-gcp-iam-role.PNG)

1. Copie o valor de **email** , você precisará dele mais tarde.

    ![Captura de tela mostrando a caixa de diálogo conta de serviço GCP](media/connect-gcp-create-service-account.png)

1. Em **administrador de & iam**, clique em **iam**.

    1. Mudar para o nível da organização.
    1. Clique em **ADICIONAR**.
    1. Na caixa **novos membros** , Cole o valor de **email** que você copiou anteriormente.
    1. Especifique a **função** como **gravador de configuração de logs** e clique em **salvar**.

        ![Captura de tela mostrando a caixa de diálogo Adicionar membro](media/connect-gcp-add-member.png)

#### <a name="create-a-private-key-for-the-dedicated-service-account"></a>Criar uma chave privada para a conta de serviço dedicada

1. Mudar para o nível de projeto.
1. Em **administrador de & iam**, clique em **contas de serviço**.
1. Abra a conta de serviço dedicada e clique em **Editar**.
1. Clique em **criar chave**.
1. Na tela **criar chave privada** , selecione **JSON**e, em seguida, clique em **criar**.

    ![Captura de tela mostrando a caixa de diálogo Criar chave privada](media/connect-gcp-create-private-key.png)

    > [!NOTE]
    > Você precisará do arquivo JSON que é baixado em seu computador mais tarde.

#### <a name="retrieve-your-organization-id"></a>Recuperar a ID da sua organização

Anote a ID da sua **organização**. você precisará dela mais tarde. Para obter mais informações, consulte [obtendo a ID da sua organização](https://cloud.google.com/resource-manager/docs/creating-managing-organization#retrieving_your_organization_id).

![Captura de tela mostrando a caixa de diálogo ID da organização](media/connect-gcp-org-id.png)

### <a name="connect-google-cloud-platform-auditing-to-cloud-app-security"></a>Conectar Google Cloud Platform auditoria ao Cloud App Security

#### <a name="add-the-gcp-connection-details"></a>Adicionar os detalhes de conexão do GCP

1. No portal do Cloud App Security, clique em **Investigar** e em **Aplicativos conectados**.

1. Na página **conectores de aplicativos** , para fornecer as credenciais do conector AWS, siga um destes procedimentos:

    > [!NOTE]
    > Recomendamos que você conecte sua instância do G Suite para obter governança e gerenciamento de usuários unificados. Isso é recomendado mesmo que você não use nenhum produto G Suite e os usuários do GCP sejam gerenciados por meio do sistema de gerenciamento de usuários do G Suite.

    **Para um novo conector**

    1. Clique no sinal de adição seguido por **Google Cloud Platform**.

        ![conectar GCP](media/connect-gcp-add.png)

    1. No pop-up, forneça um nome para o conector e clique em **conectar Google Cloud Platform**.

        ![Nome do conector do GCP](media/connect-gcp-name.png)

    1. Na página **detalhes do projeto** , faça o seguinte e clique em **conectar Google Cloud Platform**.
        1. Na caixa **ID da organização** , insira a organização que você fez antes.
        1. Na caixa **arquivo de chave privada** , navegue até o arquivo JSON baixado anteriormente.

        ![Conectar a auditoria do GCP app Security para o novo conector](media/connect-gcp-app-audit.png)

    **Para um conector existente**

    1. Na lista de conectores, na linha na qual o conector AWS aparece, clique em **conectar auditoria de segurança**.

        ![Captura de tela da página aplicativos conectados, mostrando o link editar auditoria de segurança](media/connect-gcp-app-edit-audit.png)

    1. Na página **detalhes do projeto** , faça o seguinte e clique em **conectar Google Cloud Platform**.
        1. Na caixa **ID da organização** , insira a organização que você fez antes.
        1. Na caixa **arquivo de chave privada** , navegue até o arquivo JSON baixado anteriormente.

        ![Conectar a auditoria do GCP app Security para o conector existente](media/connect-gcp-app-edit-audit-creds.png)

1. Clique em **testar API** para ter certeza de que a conexão foi bem-sucedida.

    O teste pode levar alguns minutos. Quando tiver terminado, você receberá uma notificação de êxito ou falha. Depois de receber uma notificação de êxito, clique em **Concluído**.

Se você tiver problemas para conectar o aplicativo, consulte [Solucionando problemas de conectores de aplicativos](troubleshooting-api-connectors-using-error-messages.md).

### <a name="aggregated-export-sink"></a>Coletor de exportação agregado

Atualmente, desabilitar o coletor de exportação agregado só é possível por meio do Google Cloud Shell.

#### <a name="to-disable-aggregated-export-sink"></a>Para desabilitar o coletor de exportação agregado

| Etapa | script | Para obter mais informações |
|-|-|-|
| 1. iniciar uma sessão do Google Cloud Shell. | | [Usando Cloud Shell](https://cloud.google.com/shell/docs/using-cloud-shell) |
| 2. defina o projeto atual. | `gcloud config set project {PROJECT_ID}` | [conjunto de configuração gcloud](https://cloud.google.com/sdk/gcloud/reference/config/set) |
| 3. liste os coletores de nível de organização. | `gcloud logging sinks list --organization={ORGANIZATION_ID}` | [lista de coletores de log gcloud](https://cloud.google.com/sdk/gcloud/reference/logging/sinks/list) |
| 4. exclua o coletor relevante. | `gcloud logging sinks delete {SINK_NAME} --organization={ORGANIZATION_ID}` | [exclusão de coletores de log gcloud](https://cloud.google.com/sdk/gcloud/reference/logging/sinks/delete) |

## <a name="how-to-connect-gcp-security-configuration-to-cloud-app-security"></a>Como conectar a configuração de segurança do GCP ao Cloud App Security

A conexão da configuração de segurança do GCP fornece informações sobre recomendações de segurança fundamentais com base no benchmark do CIS (centro para Internet Security) para GCP.

Siga estas etapas para conectar a configuração de segurança do GCP ao Cloud App Security.

> [!div class="checklist"]
>
> - [Configurar o centro de comando de segurança do GCP com a análise de integridade de segurança](#set-up-gcp-security-command-center-with-security-health-analytics)
> - [Habilitar a API do centro de comando de segurança](#enable-security-command-center-api)
> - [Criar uma conta de serviço dedicada para a integração de configuração de segurança](#create-a-dedicated-service-account-for-the-security-configuration-integration)
> - [Conectar Google Cloud Platform configuração de segurança ao Cloud App Security](#connect-google-cloud-platform-security-configuration-to-cloud-app-security)

### <a name="set-up-gcp-security-command-center-with-security-health-analytics"></a>Configurar o centro de comando de segurança do GCP com a análise de integridade de segurança

1. Configurar a [central de comandos de segurança](https://cloud.google.com/security-command-center/docs/quickstart-security-command-center).
1. [Habilite a análise de integridade de segurança do GCP](https://cloud.google.com/security-command-center/docs/how-to-use-security-health-analytics).
1. Verifique se há dados que fluem para o centro de comando de segurança.

    > [!NOTE]
    >
    > - As instruções para conectar seu ambiente GCP para configuração de segurança seguem as [recomendações do Google](https://cloud.google.com/security-command-center/docs/how-to-notifications#enable-scc-api) para o consumo de recomendações de configuração de segurança. A integração aproveita o centro de comando de segurança do Google e consumirá recursos adicionais que podem afetar sua cobrança.
    > - Quando você habilita a análise de integridade de segurança pela primeira vez, pode levar várias horas para que os dados estejam disponíveis.

### <a name="enable-security-command-center-api"></a>Habilitar a API do centro de comando de segurança

1. Na biblioteca de API do console de nuvem, selecione o projeto ao qual você deseja se conectar Cloud App Security.
1. Na biblioteca de API, procure e selecione a "API do centro de comando de segurança".
1. Na página da API, clique em **habilitar**.

### <a name="create-a-dedicated-service-account-for-the-security-configuration-integration"></a>Criar uma conta de serviço dedicada para a integração de configuração de segurança

1. No centro de comando de segurança do GCP, selecione o projeto ao qual você deseja se conectar Cloud App Security.
1. Em **administrador de & iam**, clique em **contas de serviço**.
1. Clique em **criar conta de serviço** para criar uma conta de serviço dedicada.
1. Insira um nome de conta e, em seguida, clique em **criar**.
1. Especifique a **função** como **Visualizador de administração da central de segurança** e clique em **salvar**.

    ![Captura de tela mostrando o item de menu Adicionar GCP para o Visualizador de administração da central de segurança](media/connect-gcp-security-configuration-1.png)

1. Copie o valor de **email** , você precisará dele mais tarde.

    ![Captura de tela mostrando a conta de serviço GCP de cópia](media/connect-gcp-security-configuration-2.png)

1. Em **administrador de & iam**, clique em **iam**.

    1. Mudar para o nível da organização.
    1. Clique em **ADICIONAR**.
    1. Na caixa **novos membros** , Cole o valor de **email** que você copiou anteriormente.
    1. Especifique a **função** como **Visualizador de administração da central de segurança** e clique em **salvar**.

        ![Captura de tela mostrando a caixa de diálogo Adicionar membro ao projeto](media/connect-gcp-security-configuration-3.png)

#### <a name="create-a-private-key-for-the-dedicated-service-account"></a>Criar uma chave privada para a conta de serviço dedicada

1. Mudar para o nível de projeto.
1. Em **administrador de & iam**, clique em **contas de serviço**.
1. Abra a conta de serviço dedicada e clique em **Editar**.
1. Clique em **criar chave**.
1. Na tela **criar chave privada** , selecione **JSON**e, em seguida, clique em **criar**.

    ![Captura de tela mostrando a caixa de diálogo Criar chave privada para conta de serviço dedicada](media/connect-gcp-security-configuration-4.png)

    > [!NOTE]
    > Você precisará do arquivo JSON que é baixado em seu computador mais tarde.

#### <a name="retrieve-your-organization-id"></a>Recuperar a ID da sua organização

Anote a ID da sua **organização**. você precisará dela mais tarde. Para obter mais informações, consulte [obtendo a ID da sua organização](https://cloud.google.com/resource-manager/docs/creating-managing-organization#retrieving_your_organization_id).
    ![Captura de tela mostrando a caixa de diálogo ID da organização](media/connect-gcp-org-id.png)

### <a name="connect-google-cloud-platform-security-configuration-to-cloud-app-security"></a>Conectar Google Cloud Platform configuração de segurança ao Cloud App Security

1. Em Cloud App Security, clique em **investigar**e, em seguida, selecione **aplicativos conectados**.

1. Na guia **aplicativos de configuração de segurança** , clique no botão de adição e, em seguida, selecione **Google Cloud Platform**.

    ![Captura de tela mostrando a opção de menu Adicionar GCP](media/connect-gcp-security-configuration-5.png)

1. Na página **nome da instância** , escolha o tipo de instância e clique em **Avançar**.

    - Para um conector existente, escolha a instância relevante.

        ![Seleção de instância de GCP](media/connect-gcp-existing-instance.png)

    - Para um novo conector, forneça um nome para a instância.

        ![Nome do novo conector do GCP](media/connect-gcp-new-instance.png)

1. Na página **detalhes do projeto** , faça o seguinte e clique em **Avançar**.
    1. Na caixa **ID da organização** , insira a organização que você fez antes.
    1. Na caixa **arquivo de chave privada** , navegue até o arquivo JSON baixado anteriormente.

    ![Adicionar detalhes do projeto GCP](media/connect-gcp-security-configuration-6.png)

1. Na página **concluído** , verifique se a conexão foi bem-sucedida e clique em **concluído**.

Se você tiver problemas para conectar o aplicativo, consulte [Solucionando problemas de conectores de aplicativos](troubleshooting-api-connectors-using-error-messages.md).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]

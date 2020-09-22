---
title: Conectar Amazon Web Services com Cloud App Security
description: Este artigo fornece informações sobre como conectar o aplicativo AWS ao Cloud App Security usando o conector de API para obter visibilidade e controle sobre o uso.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 06/24/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 62dfd007a54df2365aff04178d172257e3d15b44
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90881509"
---
# <a name="connect-aws-to-microsoft-cloud-app-security"></a>Conectar o AWS ao Microsoft Cloud App Security

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Este artigo fornece instruções para conectar sua conta do Amazon Web Services (AWS) existente para Microsoft Cloud App Security usando as APIs do conector. Para obter informações sobre como Cloud App Security protege o AWS, consulte [proteger o AWS](protect-aws.md).

Você pode conectar um ou ambos os AWS a seguir para Cloud App Security conexões:

- **Auditoria de segurança**: essa conexão fornece visibilidade e controle sobre o uso do aplicativo AWS.
- **Configuração de segurança**: essa conexão fornece recomendações de segurança fundamentais com base no parâmetro de comparação de CIS (Center for Internet Security) para AWS.

Como você pode adicionar uma ou ambas as conexões, as etapas neste artigo são escritas como instruções independentes. Se você já tiver adicionado uma das conexões, quando relevante, edite as configurações existentes.

## <a name="how-to-connect-aws-security-auditing-to-cloud-app-security"></a>Como conectar a auditoria de segurança do AWS ao Cloud App Security

Use as etapas a seguir para configurar a auditoria do AWS e, em seguida, conectá-la ao Cloud App Security.

### <a name="step-1-configure-amazon-web-services-auditing"></a>Etapa 1: configurar a auditoria de Amazon Web Services

1. No [console do Amazon Web Services](https://console.aws.amazon.com/), em **segurança, identidade & conformidade**, clique em **iam**.

    ![Identidade e acesso do AWS](media/aws-identity-and-access.png "Identidade e acesso do AWS")

1. Selecione **usuários** e clique em **Adicionar usuário**.

    ![AWS usuários](media/aws-users.png "AWS usuários")

1. Na etapa **Detalhes**, forneça um novo nome de usuário para o Cloud App Security. Verifique se, em **tipo de acesso** , selecione **acesso programático** e clique em **próximo permissões**.<a name="set-permissions"></a>

    ![Criar usuário no AWS](media/aws-create-user.png "Criar usuário no AWS")

1. Clique na guia **JSON** :

    ![Guia JSON AWS](media/aws-json.png "Guia JSON AWS")

1. Cole o seguinte script na área fornecida:

    ```json
    {
      "Version" : "2012-10-17",
      "Statement" : [{
          "Action" : [
            "cloudtrail:DescribeTrails",
            "cloudtrail:LookupEvents",
            "cloudtrail:GetTrailStatus",
            "cloudwatch:Describe*",
            "cloudwatch:Get*",
            "cloudwatch:List*",
            "iam:List*",
            "iam:Get*",
            "s3:ListAllMyBuckets",
            "s3:PutBucketAcl",
            "s3:GetBucketAcl",
            "s3:GetBucketLocation"
          ],
          "Effect" : "Allow",
          "Resource" : "*"
        }
      ]
     }
    ```

     ![Código AWS](media/aws-code.png "Código AWS")

1. Clique em **Revisar política**.

1. Forneça um **Nome** e clique em **Criar política**.

    ![Forneça o nome da política AWS](media/aws-create-policy.png "Forneça o nome da política AWS")

1. De volta à tela **Adicionar usuário**, atualize a lista se necessário, selecione o usuário que você criou e clique em **Próxima Revisão**.

    ![Anexar a política existente no AWS](media/aws-attach-policy.png "Anexar a política existente no AWS")

1. Se todos os detalhes estiverem corretos, clique em **Criar usuário**.

    ![Permissões de usuário em AWS](media/aws-user-permissions.png "Examinar permissões de usuário no AWS")

1. Quando você receber a mensagem de êxito, clique em **Baixar .csv** para salvar uma cópia das credenciais do novo usuário, elas serão necessárias posteriormente.

    ![Baixar CSV no AWS](media/aws-download-csv.png "Baixar CSV no AWS")

1. No console do AWS, clique em **Serviços** e, em **Ferramentas de Gerenciamento**, clique **CloudTrail**.

    ![AWS CloudTrail](media/aws-cloudtrail.png "AWS CloudTrail")

    Caso ainda não tenha usado o CloudTrail antes, clique em **Introdução** e configure-o fornecendo um nome e selecionando o bucket S3 adequado e clique em **Ativar**. Para verificar se você tem uma cobertura completa, defina **Aplicar a todas as regiões** como **Sim**.

    ![Ativar CloudTrail em AWS](media/aws-turnon-cloudtrail.png "Ativar CloudTrail em AWS")

    Você verá o novo nome de CloudTrail na lista **Trilhas**.

    ![Lista de CloudTrail em AWS](media/aws-cloudtrail-list.png "Lista de CloudTrail em AWS")

    > [!NOTE]
    > Depois de conectar o AWS, você receberá eventos por sete dias antes da conexão. Se você acabou de habilitar CloudTrail, receberá eventos a partir do momento em que habilitou o CloudTrail.

### <a name="step-2-connect-amazon-web-services-auditing-to-cloud-app-security"></a>Etapa 2: conectar Amazon Web Services auditoria ao Cloud App Security

1. No portal do Cloud App Security, clique em **Investigar** e em **Aplicativos conectados**.

1. Na página **conectores de aplicativos** , para fornecer as credenciais do conector AWS, siga um destes procedimentos:

    **Para um novo conector**

    1. Clique no sinal de adição seguido por **Amazon Web Services**.

        ![conectar a auditoria do AWS](media/connect-aws.png "conectar AWS")

    1. No pop-up, forneça um nome para o conector e clique em **conectar Amazon Web Services**.

        ![Nome do conector de auditoria AWS](media/connect-aws-name.png)

    1. Na página conectar o Amazon Web Services, selecione **auditoria de segurança**, Cole a **chave de acesso** e a **chave secreta** do arquivo. csv nos campos relevantes e clique em **conectar**.

        ![Conectar a auditoria do AWS app Security para o novo conector](media/aws-connect-app-audit.png "Conectar a auditoria do AWS app Security")

    **Para um conector existente**

    1. Na lista de conectores, na linha na qual o conector AWS aparece, clique em **conectar auditoria de segurança**.

        ![Captura de tela da página aplicativos conectados, mostrando o link editar auditoria de segurança](media/aws-connect-app-edit-audit.png)

    1. Na página conectar Amazon Web Services, Cole a **chave de acesso** e a **chave secreta** do arquivo. csv nos campos relevantes e clique em **conectar**.

        ![Conectar a auditoria do AWS app Security para o conector existente](media/aws-connect-app-edit-audit-creds.png "Conectar a auditoria do AWS app Security")

1. Clique em **testar API** para ter certeza de que a conexão foi bem-sucedida.

    O teste pode levar alguns minutos. Quando tiver terminado, você receberá uma notificação de êxito ou falha. Depois de receber uma notificação de êxito, clique em **Concluído**.

## <a name="how-to-connect-aws-security-configuration-to-cloud-app-security"></a>Como conectar a configuração de segurança do AWS ao Cloud App Security

A conexão da configuração de segurança do AWS fornece informações sobre recomendações de segurança fundamentais com base no benchmark do CIS (centro para Internet Security) para AWS.

Siga estas etapas para conectar a configuração de segurança do AWS ao Cloud App Security.

> [!div class="checklist"]
>
> - [Configurar o Hub de segurança do AWS](#set-up-aws-security-hub)
> - [Conectar a configuração de segurança do AWS ao Cloud App Security](#connect-aws-security-configuration-to-cloud-app-security)

### <a name="set-up-aws-security-hub"></a>Configurar o Hub de segurança do AWS

Para exibir as recomendações de segurança para várias regiões, repita as etapas a seguir para cada região relevante.

> [!NOTE]
> Se você estiver usando uma conta mestre, repita essas etapas para configurar a conta mestre e todas as contas de membro conectadas em todas as regiões relevantes.

1. Habilite a [configuração do AWS](https://docs.aws.amazon.com/config/latest/developerguide/gs-console.html).
1. Habilite o [Hub de segurança do AWS](https://docs.aws.amazon.com/securityhub/latest/userguide/securityhub-settingup.html).
1. Verifique se há dados que fluem para o Hub de segurança.

    > [!NOTE]
    > Quando você habilita o Hub de segurança pela primeira vez, pode levar várias horas para que os dados estejam disponíveis.

### <a name="connect-aws-security-configuration-to-cloud-app-security"></a>Conectar a configuração de segurança do AWS ao Cloud App Security

Antes de poder conectar a configuração de segurança do AWS, verifique se você [configurou seu ambiente AWS](#set-up-aws-security-hub) para coletar recomendações fundamentais de segurança e conformidade.

> [!NOTE]
> Se você estiver usando uma [conta mestre do AWS](https://aws.amazon.com/security-hub/faqs/), use as etapas a seguir para conectar-se à conta mestre. Conectar sua conta mestra permite que você receba recomendações para todas as contas de membro em todas as regiões.

### <a name="step-1-configure-amazon-web-services-security-configuration"></a>Etapa 1: configurar Amazon Web Services configuração de segurança

1. Siga o *How to Connect AWS Security Auditing* Steps to Get to the [Permissions](#set-permissions) Page.

1. Na página permissões, clique em **anexar políticas existentes diretamente**, aplique as políticas **AWSSecurityHubReadOnlyAccess** e **SecurityAudit** e clique em **próximas marcas**.

    ![Anexar a política existente no AWS](media/aws-attach-policy.png "Anexar a política existente no AWS")

1. Opcional: adicionar marcas ao usuário.

    ![Adicionar marcas ao usuário no AWS](media/aws-add-tags.png)

    > [!NOTE]
    > A adição de marcas ao usuário não afetará a conexão.

1. Clique em **próximo revisão**.

1. Se todos os detalhes estiverem corretos, clique em **Criar usuário**.

    ![Permissões de usuário em AWS](media/aws-user-permissions.png "Examinar permissões de usuário no AWS")

1. Quando você receber a mensagem de êxito, clique em **baixar. csv** para salvar uma cópia da **ID de chave de acesso** e a chave de acesso de **segredo**. você precisará delas mais tarde.

    ![Baixar CSV no AWS](media/aws-download-csv.png "Baixar CSV no AWS")

### <a name="step-2-connect-amazon-web-services-security-configuration-to-cloud-app-security"></a>Etapa 2: conectar Amazon Web Services configuração de segurança ao Cloud App Security

1. Em Cloud App Security, clique em **investigar**e, em seguida, selecione **aplicativos conectados**.

1. Na guia **aplicativos de configuração de segurança** , clique no botão de adição e, em seguida, selecione **Amazon Web Services**.

    ![conectar a configuração de segurança do AWS](media/connect-aws-security-configuration.png)

1. Na página **nome da instância** , escolha o tipo de instância e clique em **Avançar**.

    - Para um conector existente, escolha a instância relevante.

        ![Seleção de instância de AWS](media/connect-aws-existing-instance.png)

    - Para um novo conector, forneça um nome para a instância.

        ![Nome do conector de configuração de segurança AWS](media/aws-connect-name.png)

1. Na página **detalhes da conta** , Cole a **chave de acesso** e a **chave secreta** do arquivo. csv nos campos relevantes e clique em **Avançar**.

    ![Detalhes da conta do AWS Connect](media/aws-connect-account-details.png)

1. Na página **concluído** , verifique se a conexão foi bem-sucedida e clique em **concluído**.

Se você tiver problemas para conectar o aplicativo, consulte [Solucionando problemas de conectores de aplicativos](troubleshooting-api-connectors-using-error-messages.md).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]

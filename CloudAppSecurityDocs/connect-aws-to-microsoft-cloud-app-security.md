---
title: Conectar Amazon Web Services com Cloud App Security
description: Este artigo fornece informações sobre como conectar o aplicativo AWS ao Cloud App Security usando o conector de API para obter visibilidade e controle sobre o uso.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 8/13/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 89a14c0fa629a0affd9fde58b1faf4c3716de143
ms.sourcegitcommit: 7c93b6f93d2699d466b172590710ed01697bbdad
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74719549"
---
# <a name="connect-aws-to-microsoft-cloud-app-security"></a>Conectar o AWS ao Microsoft Cloud App Security

*Aplica-se ao: Microsoft Cloud App Security*

Este artigo fornece instruções para conectar sua conta do Amazon Web Services (AWS) existente para Microsoft Cloud App Security usando as APIs do conector.

Você pode conectar um ou ambos os AWS a seguir para Cloud App Security conexões:

- **Auditoria de segurança**: essa conexão fornece visibilidade e controle sobre o uso do aplicativo AWS.
- **Configuração de segurança**: essa conexão fornece recomendações de segurança fundamentais com base no parâmetro de comparação de CIS (Center for Internet Security) para AWS.

Como você pode adicionar uma ou ambas as conexões, as etapas neste artigo são escritas como instruções independentes. Se você já tiver adicionado uma das conexões, quando relevante, edite as configurações existentes.

## <a name="how-to-connect-aws-security-auditing-to-cloud-app-security"></a>Como conectar a auditoria de segurança do AWS ao Cloud App Security

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

1. Clique em **Examinar política**.

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

1. No portal do Cloud App Security, clique em **Investigar** e em **Aplicativos conectados**.

1. Na página **conectores de aplicativos** , para fornecer as credenciais do conector AWS, siga um destes procedimentos:

    **Para um novo conector**

    1. Clique no sinal de adição seguido por **Amazon Web Services**.

        ![conectar AWS](media/connect-aws.png "conectar AWS")

    1. No pop-up, forneça um nome para o conector e clique em **conectar Amazon Web Services**.

        ![Nome do conector do AWS](media/aws-connect-name.png)

    1. Na página conectar o Amazon Web Services, selecione **auditoria de segurança**, Cole a **chave de acesso** e a **chave secreta** do arquivo. csv nos campos relevantes e clique em **conectar**.

        ![Conectar a auditoria do AWS app Security](media/aws-connect-app-audit.png "Conectar a auditoria do AWS app Security")

    **Para um conector existente**

    1. Na lista de conectores, na linha na qual o conector AWS aparece, clique em **conectar auditoria de segurança**.

        ![Captura de tela da página aplicativos conectados, mostrando o link editar auditoria de segurança](media/aws-connect-app-edit-audit.png)

    1. Na página conectar Amazon Web Services, Cole a **chave de acesso** e a **chave secreta** do arquivo. csv nos campos relevantes e clique em **conectar**.

        ![Conectar a auditoria do AWS app Security](media/aws-connect-app-edit-audit-creds.png "Conectar a auditoria do AWS app Security")

1. Certifique-se de que a conexão foi bem-sucedida clicando em **Testar API**.  

    O teste pode levar alguns minutos. Quando ele for concluído, você receberá uma notificação de Êxito ou Falha. Depois de receber uma notificação de êxito, clique em **Concluído**.

## <a name="how-to-connect-aws-security-configuration-to-cloud-app-security"></a>Como conectar a configuração de segurança do AWS ao Cloud App Security

Siga o [How to Connect AWS Security Auditing](#how-to-connect-aws-security-auditing-to-cloud-app-security) Steps to Get to the [Permissions](#set-permissions) Page.

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

1. No portal do Cloud App Security, clique em **Investigar** e em **Aplicativos conectados**.

1. Na página **conectores de aplicativos** , para fornecer as credenciais do conector AWS, siga um destes procedimentos:

    **Para um novo conector**

    1. Clique no sinal de adição seguido por **Amazon Web Services**.<br />

        ![conectar AWS](media/connect-aws.png "conectar AWS")

    1. No pop-up, forneça um nome para o conector e clique em **conectar Amazon Web Services**.

        ![Nome do conector do AWS](media/aws-connect-name.png)

    1. Na página conectar o Amazon Web Services, selecione **configuração de segurança**, Cole **a chave de acesso** e a **chave secreta** do arquivo. csv nos campos relevantes e clique em **conectar**.

        ![Conectar a configuração do AWS app Security](media/aws-connect-app-config.png "Conectar a configuração do AWS app Security")

    **Para um conector existente**

    1. Na lista de conectores, na linha na qual o conector AWS aparece, clique em **conectar configuração de segurança**.

        ![Captura de tela da página aplicativos conectados, mostrando o link Editar configuração de segurança](media/aws-connect-app-edit-config.png)

    1. Na página conectar Amazon Web Services, Cole a **chave de acesso** e a **chave secreta** do arquivo. csv nos campos relevantes e clique em **conectar**.

        ![Conectar a configuração do AWS app Security](media/aws-connect-app-edit-config-creds.png "Conectar a configuração do AWS app Security")

1. Certifique-se de que a conexão foi bem-sucedida clicando em **Testar API**.  

    O teste pode levar alguns minutos. Quando ele for concluído, você receberá uma notificação de Êxito ou Falha. Depois de receber uma notificação de êxito, clique em **Concluído**.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]

---
title: Connect Amazon Web Services with Cloud App Security
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
ms.assetid: a6b4c745-cd5c-4458-819c-80cbe8b25f29
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 387a9a9184bb805db7659d6f67eae26239f812f3
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2019
ms.locfileid: "74461069"
---
# <a name="connect-aws-to-microsoft-cloud-app-security"></a>Conectar o AWS ao Microsoft Cloud App Security

*Aplica-se ao: Microsoft Cloud App Security*

This article provides instructions for connecting your existing Amazon Web Services (AWS) account to Microsoft Cloud App Security using the connector APIs.

You can connect one or both of the following AWS to Cloud App Security connections:

- **Security auditing**: This connection gives you visibility into and control over AWS app use.
- **Security configuration**: This connection gives you fundamental security recommendations based on the Center for Internet Security (CIS) benchmark for AWS.

Since you can add either or both of the connections, the steps in this article are written as independent instructions. If you have already added one of the connections, where relevant edit the existing configurations.

## <a name="how-to-connect-aws-security-auditing-to-cloud-app-security"></a>How to connect AWS Security auditing to Cloud App Security

1. In your [Amazon Web Services console](https://console.aws.amazon.com/), under **Security, Identity & Compliance**, click **IAM**.

    ![AWS identity and access](media/aws-identity-and-access.png "AWS identity and access")

1. Select **Users** and then click **Add user**.

    ![AWS users](media/aws-users.png "AWS users")

1. Na etapa **Detalhes**, forneça um novo nome de usuário para o Cloud App Security. Make sure that under **Access type** you select **Programmatic access** and click **Next Permissions**.<a name="set-permissions"></a>

    ![Create user in AWS](media/aws-create-user.png "Create user in AWS")

1. Click on the **JSON** tab:

    ![AWS JSON tab](media/aws-json.png "AWS JSON tab")

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

     ![AWS code](media/aws-code.png "AWS code")

1. Clique em **Examinar política**.

1. Forneça um **Nome** e clique em **Criar política**.

    ![Provide AWS policy name](media/aws-create-policy.png "Provide AWS policy name")

1. De volta à tela **Adicionar usuário**, atualize a lista se necessário, selecione o usuário que você criou e clique em **Próxima Revisão**.

    ![Attach existing policy in AWS](media/aws-attach-policy.png "Attach existing policy in AWS")

1. Se todos os detalhes estiverem corretos, clique em **Criar usuário**.

    ![User permissions in AWS](media/aws-user-permissions.png "Review user permissions in AWS")

1. Quando você receber a mensagem de êxito, clique em **Baixar .csv** para salvar uma cópia das credenciais do novo usuário, elas serão necessárias posteriormente.

    ![Download csv in AWS](media/aws-download-csv.png "Download csv in AWS")

1. No console do AWS, clique em **Serviços** e, em **Ferramentas de Gerenciamento**, clique **CloudTrail**.

    ![AWS CloudTrail](media/aws-cloudtrail.png "AWS CloudTrail")

    Caso ainda não tenha usado o CloudTrail antes, clique em **Introdução** e configure-o fornecendo um nome e selecionando o bucket S3 adequado e clique em **Ativar**. Para verificar se você tem uma cobertura completa, defina **Aplicar a todas as regiões** como **Sim**.

    ![Turn on CloudTrail in AWS](media/aws-turnon-cloudtrail.png "Turn on CloudTrail in AWS")

    Você verá o novo nome de CloudTrail na lista **Trilhas**.

    ![CloudTrail list in AWS](media/aws-cloudtrail-list.png "CloudTrail list in AWS")

    > [!NOTE]
    > Depois de conectar o AWS, você receberá eventos por sete dias antes da conexão. If you just enabled CloudTrail, you'll receive events from the time you enabled CloudTrail.

1. No portal do Cloud App Security, clique em **Investigar** e em **Aplicativos conectados**.

1. In the **App connectors** page, to provide the AWS connector credentials, do one of the following:

    **For a new connector**

    1. Click the plus sign followed by **Amazon Web Services**.

        ![connect AWS](media/connect-aws.png "conectar AWS")

    1. In the pop-up, provide a name for the connector, and then click **Connect Amazon Web Services**.

        ![AWS connector name](media/aws-connect-name.png)

    1. On the Connect Amazon Web services page, select **Security auditing**, paste the **Access key** and **Secret key** from the .csv file into the relevant fields, and click **Connect**.

        ![Connect AWS app security auditing](media/aws-connect-app-audit.png "Connect AWS app security auditing")

    **For an existing connector**

    1. In the list of connectors, on the row in which the AWS connector appears, click **Connect security auditing**.

        ![Screenshot of the Connected Apps page, showing edit Security Auditing link](media/aws-connect-app-edit-audit.png)

    1. On the Connect Amazon Web Services page, paste the **Access key** and **Secret key** from the .csv file into the relevant fields, and click **Connect**.

        ![Connect AWS app security auditing](media/aws-connect-app-edit-audit-creds.png "Connect AWS app security auditing")

1. Certifique-se de que a conexão foi bem-sucedida clicando em **Testar API**.  

    O teste pode levar alguns minutos. Quando ele for concluído, você receberá uma notificação de Êxito ou Falha. Depois de receber uma notificação de êxito, clique em **Concluído**.

## <a name="how-to-connect-aws-security-configuration-to-cloud-app-security"></a>How to connect AWS Security configuration to Cloud App Security

Follow the [How to connect AWS Security auditing](#how-to-connect-aws-security-auditing-to-cloud-app-security) steps to get to the [permissions](#set-permissions) page.

1. On the permissions page, click **Attach existing policies directly**, apply the **AWSSecurityHubReadOnlyAccess** and **SecurityAudit** policies, and then click **Next Tags**.

    ![Attach existing policy in AWS](media/aws-attach-policy.png "Attach existing policy in AWS")

1. Optional: Add tags to the user.

    ![Add tags to user in AWS](media/aws-add-tags.png)

    > [!NOTE]
    > Adding tags to the user won't affect the connection.

1. Click **Next Review**.

1. Se todos os detalhes estiverem corretos, clique em **Criar usuário**.

    ![User permissions in AWS](media/aws-user-permissions.png "Review user permissions in AWS")

1. When you get the success message, click **Download .csv** to save a copy of the **Access key ID** and the **Secret access key**, you need these later.

    ![Download csv in AWS](media/aws-download-csv.png "Download csv in AWS")

1. No portal do Cloud App Security, clique em **Investigar** e em **Aplicativos conectados**.

1. In the **App connectors** page, to provide the AWS connector credentials, do one of the following:

    **For a new connector**
    1. Click the plus sign followed by **Amazon Web Services**.<br>

        ![connect AWS](media/connect-aws.png "conectar AWS")

    1. In the pop-up, provide a name for the connector, and then click **Connect Amazon Web Services**.

        ![AWS connector name](media/aws-connect-name.png)

    1. On the Connect Amazon Web services page, select **Security configuration**, paste the **Access key** and **Secret key** from the .csv file into the relevant fields, and click **Connect**.

        ![Connect AWS app security configuration](media/aws-connect-app-config.png "Connect AWS app security configuration")

    **For an existing connector**
    1. In the list of connectors, on the row in which the AWS connector appears, click **Connect security configuration**.

        ![Screenshot of the Connected Apps page, showing edit Security Configuration link](media/aws-connect-app-edit-config.png)

    1. On the Connect Amazon Web Services page, paste the **Access key** and **Secret key** from the .csv file into the relevant fields, and click **Connect**.

        ![Connect AWS app security configuration](media/aws-connect-app-edit-config-creds.png "Connect AWS app security configuration")

1. Certifique-se de que a conexão foi bem-sucedida clicando em **Testar API**.  

    O teste pode levar alguns minutos. Quando ele for concluído, você receberá uma notificação de Êxito ou Falha. Depois de receber uma notificação de êxito, clique em **Concluído**.

## <a name="next-steps"></a>Próximas etapas

[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
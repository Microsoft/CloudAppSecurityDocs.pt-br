---
title: Conectar AWS a Cloud App Security para visibilidade e controle de uso | Microsoft Docs
description: Este tópico fornece informações sobre como conectar seu aplicativo do AWS ao Cloud App Security usando o conector de API.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/29/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: a6b4c745-cd5c-4458-819c-80cbe8b25f29
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: d6c3e680ec17d8a62977e4c25af5b9163244afea
ms.sourcegitcommit: bb010d8dd0a6eff39df31e33c2cc9c37ec321b46
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50217281"
---
*Aplica-se ao: Microsoft Cloud App Security*

# <a name="connect-aws-to-microsoft-cloud-app-security"></a>Conectar o AWS ao Microsoft Cloud App Security
Esta seção fornece instruções para conectar o Microsoft Cloud App Security à sua conta do Amazon Web Services existente usando as APIs do conector.  
  
## <a name="how-to-connect-amazon-web-services-to-cloud-app-security"></a>Como conectar o Amazon Web Services ao Cloud App Security  
  
1.  No seu [Console do Amazon Web Services](https://console.aws.amazon.com/), em **Segurança, Identidade e Conformidade**, clique em **IAM**.  
  
     ![Identidade e acesso do AWS](./media/aws-identity-and-access.png "Identidade e acesso do AWS")  
  
2.  Clique na guia **Usuários** e, em seguida, clique em **Adicionar usuário**.  
  
     ![Usuários do AWS](./media/aws-users.png "Usuários do AWS")      
  
4.  Na etapa **Detalhes**, forneça um novo nome de usuário para o Cloud App Security. Certifique-se de que, em **Tipo de acesso** você selecione **Acesso programático** e clique em **Próximas Permissões**.  

     ![criar usuário no AWS](./media/aws-create-user.png "Criar usuário no AWS")

5. Clique na guia JSON:

     ![AWS JSON](./media/aws-json.png "guia AWS JSON")

6. Cole o seguinte script na área fornecida:

    ```     
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

     ![Código AWS](./media/aws-code.png "Código AWS")
    
6. Clique em **Examinar política**.

7. Forneça um **Nome** e clique em **Criar política**.

     ![Nomear política no AWS](./media/aws-create-policy.png "Criar política no AWS")

9. De volta à tela **Adicionar usuário**, atualize a lista se necessário, selecione o usuário que você criou e clique em **Próxima Revisão**.

   ![Revisar a política de usuário no AWS](./media/aws-review-user.png "Revisar usuário no AWS")

10. Se todos os detalhes estiverem corretos, clique em **Criar usuário**.

    ![Permissões de usuário no AWS](./media/aws-user-permissions.png "Revisar permissões de usuário no AWS")

11. Quando você receber a mensagem de êxito, clique em **Baixar .csv** para salvar uma cópia das credenciais do novo usuário, elas serão necessárias posteriormente.  

    ![Baixar o csv no AWS](./media/aws-download-csv.png "Baixar o csv no AWS")
  
10. No console do AWS, clique em **Serviços** e, em **Ferramentas de Gerenciamento**, clique **CloudTrail**.  
  
     ![CloudTrail do AWS](./media/aws-cloudtrail.png "Cloudtrail do AWS")  
  
    Caso ainda não tenha usado o CloudTrail antes, clique em **Introdução** e configure-o fornecendo um nome e selecionando o bucket S3 adequado e clique em **Ativar**. Para verificar se você tem uma cobertura completa, defina **Aplicar a todas as regiões** como **Sim**.
  
       ![Ligar CloudTrail no AWS](./media/aws-turnon-cloudtrail.png "Ligar CloudTrail no AWS")
  
    Você verá o novo nome de CloudTrail na lista **Trilhas**.
    
      ![Lista do CloudTrail no AWS](./media/aws-cloudtrail-list.png "Lista do CloudTrail no AWS")
  
11. No portal do Cloud App Security, clique em **Investigar** e em **Aplicativos conectados**.  
  
12. Na página **Conectores de aplicativos**, clique no sinal de mais antes de **Amazon Web Services**.  
  
     ![Conectar ao AWS](./media/connect-aws.png "connect AWS")  
  
13. No pop-up, cole a **Chave de acesso** e a **Chave secreta** do arquivo csv nos campos relevantes e clique em **Conectar**.  
   ![Conectar o aplicativo AWS](./media/aws-connect-app.png "Conectar o aplicativo AWS") 
  
14. Certifique-se de que a conexão foi bem-sucedida clicando em **Testar API**.  
  
     O teste pode levar alguns minutos. Quando ele for concluído, você receberá uma notificação de Êxito ou Falha. Depois de receber uma notificação de êxito, clique em **Concluído**.  
  
Depois de conectar o AWS, você receberá eventos por sete dias antes da conexão. Se você acabou de habilitar o CloudTrail, nesse caso, você receberá eventos a partir do momento em que habilitou o CloudTrail.
  
## <a name="next-steps"></a>Próximas etapas  
[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)   

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
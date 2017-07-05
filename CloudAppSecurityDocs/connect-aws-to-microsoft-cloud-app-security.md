---
title: Conectar AWS a Cloud App Security para visibilidade e controle de uso | Microsoft Docs
description: "Este tópico fornece informações sobre como conectar seu aplicativo do AWS ao Cloud App Security usando o conector de API."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/19/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: a6b4c745-cd5c-4458-819c-80cbe8b25f29
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 68d4c221626706ca641a5d3e1986da543771561a
ms.sourcegitcommit: 2f4474084c7e07ac4853945ab5aa1ea78950675d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/28/2017
---
# <a name="connect-aws-to-microsoft-cloud-app-security"></a>Conectar o AWS ao Microsoft Cloud App Security
Esta seção fornece instruções para conectar o Cloud App Security à sua conta do Amazon Web Services existente usando as APIs do conector.  
  
## <a name="how-to-connect-amazon-web-services-to-cloud-app-security"></a>Como conectar o Amazon Web Services ao Cloud App Security  
  
1.  No seu [Console do Amazon Web Services](https://console.aws.amazon.com/), em **Segurança, Identidade e Conformidade**, clique em **IAM**.  
  
     ![Identidade e acesso do AWS](./media/aws-identity-and-access.png "aws identity and access")  
  
2.  Clique na guia **Usuários** e, em seguida, clique em **Adicionar usuário**.  
  
     ![Usuários do AWS](./media/aws-users.png "aws users")      
  
4.  Na etapa **Detalhes**, forneça um novo nome de usuário para Cloud App Security e certifique-se de que em **Tipo de acesso** você selecione **Acesso programático** e clique em **Próximas permissões**.  

     ![Criar usuário do AWS](./media/aws-create-user.png "AWS create user")

5. Na etapa **Permissões**, selecione **Anexar as políticas existentes diretamente** e, em seguida, clique em **Criar política**.

   ![Anexar usuário no AWS](./media/aws-attach-user-policy.png "Anexar política existente no AWS")

6.  Em **Criar Política**, selecione **Criar sua Própria Política**.
 
    ![Criar a sua própria política no AWS](./media/aws-create-own-policy.png "Criar política no AWS")
 
7.  Em **Examinar Política**, forneça um **Nome da Política**, por exemplo CloudAppSecurityPolicy.

    ![Examinar política no AWS](./media/aws-review-policy.png "AWS review policy")

8. Em seguida, cole o seguinte no campo **Documento de política** e clique em **Criar política**:
  
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
            "iam:Get*"  
          ],  
          "Effect" : "Allow",  
          "Resource" : "*"  
        }  
      ]  
     }  
  
    ```  
  
9. De volta à tela **Adicionar usuário**, atualize a lista se necessário, selecione o usuário que você acabou de criar e clique em **Próxima Revisão**.

   ![Examinar política de usuário no AWS](./media/aws-review-user.png "Examinar usuário no AWS")

10. Se todos os detalhes estiverem corretos, clique em **Criar usuário**.

    ![Permissões de usuário do AWS](./media/aws-user-permissions.png "Examinar permissões de usuário do AWS")

11. Quando você receber a mensagem de êxito, clique em **Baixar .csv** para salvar uma cópia das credenciais do novo usuário, as quais serão necessária posteriormente.  

    ![Baixar CSV no AWS](./media/aws-download-csv.png "AWS download csv")
  
10. No console do AWS, clique em **Serviços** e, em **Ferramentas de Gerenciamento**, clique **CloudTrail**.  
  
     ![CloudTrail do AWS](./media/aws-cloudtrail.png "aws cloudtrail")  
  
    Caso ainda não tenha usado o CloudTrail antes, clique em **Introdução** e configure-o ao fornecer um nome e selecionando o bucket S3 adequado e clique em **Ativar**. Para verificar se você tem uma cobertura completa, defina **Aplicar a todas as regiões** como **Sim**.
  
       ![Ligar CloudTrail no AWS](./media/aws-turnon-cloudtrail.png "AWS turn on CloudTrail")
  
    Você verá o novo nome de CloudTrail na lista **Trilhas**.
    
      ![Lista do AWS CloudTrail](./media/aws-cloudtrail-list.png "Lista do AWS CloudTrail")
  
11. No portal do Cloud App Security, clique em **Investigar** e em **Aplicativos conectados**.  
  
12. Na página **Conectores de aplicativos**, clique no sinal de mais antes de **AWS**.  
  
     ![Conectar ao AWS](./media/connect-aws.png "connect AWS")  
  
13. No pop-up, cole a **Chave de acesso** e a **Chave secreta** do arquivo csv nos campos relevantes e clique em **Conectar**.  
   ![Conectar aplicativo ao AWS](./media/aws-connect-app.png "AWS connect app") 
  
14. Certifique-se de que a conexão foi bem-sucedida clicando em **Testar API**.  
  
     O teste pode levar alguns minutos. Quando ele for concluído, você receberá uma notificação de Êxito ou Falha. Depois de receber uma notificação de êxito, clique em **Concluído**.  
  
Depois de conectar o AWS, você receberá eventos por 7 dias antes da conexão, a menos que você tenha acabado de habilitar o CloudTrail, caso em que você receberá eventos desde o momento em que habilitar o CloudTrail.
  
## <a name="see-also"></a>Consulte Também  
[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
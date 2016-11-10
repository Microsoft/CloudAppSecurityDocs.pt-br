---
title: Conectar o AWS ao Microsoft Cloud App Security | Microsoft Docs
description: "Este tópico fornece informações sobre como conectar seu aplicativo do AWS ao Cloud App Security usando o conector de API."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: a6b4c745-cd5c-4458-819c-80cbe8b25f29
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed4ea71b24767d3602d40894d1cbac7447bcd8a2
ms.openlocfilehash: 4b9ab028bb45f77513217dd3784cefc73e984962


---

# <a name="connect-aws-to-microsoft-cloud-app-security"></a>Conectar o AWS ao Microsoft Cloud App Security
Esta seção fornece instruções para conectar o Cloud App Security à sua conta do Amazon Web Services existente usando as APIs do conector.  
  
## <a name="how-to-connect-amazon-web-services-to-cloud-app-security"></a>Como conectar o Amazon Web Services ao Cloud App Security  
  
1.  No seu console do Amazon Web Services, clique em **Gerenciamento de Identidades e Acesso**.  
  
     ![identidade e acesso do aws](./media/aws-identity-and-access.png "aws identity and access")  
  
2.  Clique na guia **Usuários**.  
  
     ![usuários do aws](./media/aws-users.png "aws users")  
  
3.  Clique em **Criar Novos Usuários**.  
  
     ![Criar usuário do AWS](./media/aws-create-user.png "AWS create user")  
  
4.  Crie um novo usuário do Cloud App Security e verifique se a caixa de seleção **Gerar uma chave de acesso para cada usuário)** está marcada.  
  
5.  Clique em **Download Credentials (Baixar Credenciais)**.  
  
     ![credenciais de dl aws](./media/aws-dl-cred.png "aws dl cred")  
  
6.  Na guia **Permissões**, clique em **Anexar Política**.  
  
     ![anexar a política de usuário do aws](./media/aws-attach-user-policy.png "aws attach user policy")  
  
7.  A tela **Examinar Política** é aberta.
 
     ![examinar política](./media/aws-review-policy.png "aws review policy")  
  

8. Em **Nome da Política**, digite “AdallomTrustPolicy”. 
10. Em **Documento de Política**, copie e cole o seguinte:  
  
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
  
9. No arquivo baixado `credentials.csv`, localize as credenciais do novo usuário. Você precisará copiá-las mais tarde.  
  
10. Retorne à página principal do console do AWS e, no canto superior direito, selecione sua região principal na janela suspensa e clique em **CloudTrail** no menu principal.  
  
     ![aws cloudtrail](./media/aws-cloudtrail.png "aws cloudtrail")  
  
    1.  Caso ainda não tenha usado o CloudTrail para essa região antes, clique no botão **Introdução** e configure-o selecionando o bucket S3 adequado.  
  
         Clique na guia **Configuração** no canto superior esquerdo da tela. Em **Configuração adicional**, clique no ícone de edição.  
  
         ![configuração do aws cloudtrail](./media/aws-cloudtrail-config.png "aws cloudtrail config")  
  
    2.  Clique em **Sim** quando a pergunta **Include global services (Incluir serviços globais)** surgir e clique em **Salvar**. Isso se aplica somente à região selecionada.  
  
         ![aws inclui global svc](./media/aws-include-global-svc.png "aws include global svc")  
  
    3.  Repita a Etapa 11 para todas as regiões, mas não configure nenhuma outra região para incluir serviços globais.  
  
11. No portal do Cloud App Security, clique em **Investigar** e em **Aplicativos sancionados**.  
  
12. Na linha AWS, clique em **Conectar** na coluna **Status do Conector de Aplicativos** ou clique no botão **Conectar um aplicativo** seguido por **AWS**.  
  
     ![conectar AWS](./media/connect-aws.png "connect AWS")  
  
13. Na página de configurações do Amazon Web Services, cole a **Chave de acesso** e a **Chave secreta** do arquivo csv nos campos na página de API e clique **Atualizar Chave de Acesso**.  
  
14. Certifique-se de que a conexão foi bem-sucedida clicando em **Testar API**.  
  
     O teste pode levar alguns minutos. Quando ele for concluído, você receberá uma notificação de Êxito ou Falha. Depois de receber uma notificação de êxito, clique em **Concluído**.  
  
Depois de conectar o AWS, você receberá eventos por 7 dias antes da conexão.
  
## <a name="see-also"></a>Veja também  
[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Oct16_HO4-->



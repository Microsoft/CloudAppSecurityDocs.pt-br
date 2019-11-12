---
title: Obter recomendações de configuração de segurança para AWS-Cloud App Security | Microsoft Docs
description: Este artigo fornece informações sobre como obter recomendações de configuração de segurança no Cloud App Security integrando com Amazon Web Services.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 8/1/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: c6d8f8af-867b-43ab-adee-f06520577fe7
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 40d8d1f578f826f1782cfbf643f8b2db136f24d2
ms.sourcegitcommit: 8a49c166424fea83853b0a6895212367526abe78
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71084996"
---
# <a name="security-configuration-for-aws"></a>Configuração de segurança para o AWS

*Aplica-se a: Microsoft Cloud App Security*

Microsoft Cloud App Security fornece uma avaliação de configuração de segurança de seu ambiente de Amazon Web Services. Essa avaliação fornece recomendações de segurança fundamentais com base no parâmetro de comparação de CIS (centro de segurança da Internet) para AWS.

## <a name="prerequisites"></a>Pré-requisitos

- O Hub de segurança do AWS deve ser configurado para todas as suas regiões de conta do AWS. Para obter mais informações, consulte [Configurando o Hub de segurança do AWS](https://go.microsoft.com/fwlink/?linkid=2100208).
    > [!NOTE]
    > Se esta for a primeira vez que você está habilitando o Hub de segurança, pode levar várias horas para que os dados iniciais fiquem disponíveis.
- Seu Amazon Web Services deve estar conectado a Cloud App Security. Para obter mais informações, consulte [conectar o AWS ao Microsoft Cloud app Security](connect-aws-to-microsoft-cloud-app-security.md).

## <a name="how-to-view-aws-security-recommendation"></a>Como exibir a recomendação de segurança do AWS

1. Em Cloud app Security, navegue para **investigar** > **configuração de segurança**e, em seguida, selecione a guia **Amazon Web Services** .
    - O Microsoft Cloud App Security fornece recomendações apenas para as 50 principais assinaturas.
    - Pode levar até 15 minutos para que as alterações entrem em vigor.

     ![menu de configuração de segurança](media/security-configuration-menu.png)

1. Você pode filtrar as recomendações por tipo, por recurso e por contas. Além disso, você pode clicar no ícone de configuração de segurança ![Ícone ASC](./media/asc-icon.png) para abrir a recomendação no Hub de segurança do Amazon para obter mais informações e aprofundar-se na recomendação.

   ![configuração de segurança](media/security-configuration-aws.png)

## <a name="next-steps"></a>Próximas etapas 
[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
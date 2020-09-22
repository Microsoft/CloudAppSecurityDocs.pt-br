---
title: Obter recomendações de configuração de segurança para o AWS
description: Este artigo fornece informações sobre como obter recomendações de configuração de segurança no Cloud App Security integrando com Amazon Web Services.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 06/28/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 87a3eb690c81930baaa0cee5dba02f5d9fe62e59
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90878951"
---
# <a name="security-configuration-for-aws"></a>Configuração de segurança para o AWS

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Microsoft Cloud App Security fornece uma avaliação de configuração de segurança de seu ambiente de Amazon Web Services. Essa avaliação fornece recomendações de segurança fundamentais com base no parâmetro de comparação de CIS (centro de segurança da Internet) para AWS.

## <a name="prerequisites"></a>Pré-requisitos

- O Hub de segurança do AWS deve ser configurado para todas as suas regiões de conta do AWS. Para obter mais informações, consulte [Configurando o Hub de segurança do AWS](https://go.microsoft.com/fwlink/?linkid=2100208).
    > [!NOTE]
    > Se esta for a primeira vez que você está habilitando o Hub de segurança, pode levar várias horas para que os dados iniciais fiquem disponíveis.
- Seu Amazon Web Services deve estar conectado a Cloud App Security. Para obter mais informações, consulte [conectar o AWS ao Microsoft Cloud app Security](connect-aws-to-microsoft-cloud-app-security.md).

## <a name="how-to-view-aws-security-recommendations"></a>Como exibir as recomendações de segurança do AWS

1. Em Cloud app Security, navegue para **investigar**  >  **configuração de segurança**e, em seguida, selecione a guia **Amazon Web Services** .

    > [!NOTE]
    > Pode levar até 15 minutos para que as alterações entrem em vigor.

    ![menu de configuração de segurança](media/security-configuration-menu.png)

1. Você pode filtrar as recomendações por tipo, por recurso e por contas. Além disso, você pode clicar no ícone de configuração de segurança ![Ícone ASC](media/asc-icon.png) para abrir a recomendação no Hub de segurança do Amazon para obter mais informações e aprofundar-se na recomendação.

    > [!NOTE]
    > Para simplificar ainda mais a investigação, você pode criar consultas personalizadas e salvá-las para uso posterior. Após concluir a criação da sua consulta, clique no botão **Salvar como** no canto superior direito dos filtros. No pop-up **Salvar consulta** , nomeie sua consulta.

    ![configuração de segurança](media/security-configuration-aws.png)

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]

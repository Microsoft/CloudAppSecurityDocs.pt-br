---
title: Obter recomendações de configuração de segurança para o Azure
description: Este artigo fornece informações sobre como obter recomendações de configuração de segurança no Cloud App Security integrando-se à central de segurança do Azure.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 06/29/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 0d821e574dc241097d70814cf854c46e4db2664b
ms.sourcegitcommit: 29a8e66c665f51d831516924ae4d9d8047b39276
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88781541"
---
# <a name="security-configuration-for-azure"></a>Configuração de segurança para o Azure

*Aplica-se a: Microsoft Cloud App Security*

O Microsoft Cloud App Security fornece uma avaliação de configuração de segurança do seu ambiente do Azure. A avaliação, alimentada pela Central de Segurança do Azure, fornece recomendações para configuração ausente e controle de segurança.

## <a name="enable-security-configuration-recommendations"></a>Habilitar as recomendações de configuração de segurança

Para usar esse recurso, você precisa ter as permissões apropriadas no Azure AD e no portal do Azure. Por padrão, a função de Administrador global do Azure AD não fornece acesso às assinaturas do Azure. Eleve as permissões para permitir acesso a assinaturas do Azure para você e outros usuários.

> [!IMPORTANT]
> É recomendado que você desabilite a elevação depois de concluir o processo a seguir.

## <a name="how-to-enable-azure-security-recommendations"></a>Como habilitar as recomendações de segurança do Azure

Para habilitar as recomendações de configuração de segurança no Microsoft Cloud App Security:

1. <a href="https://docs.microsoft.com/azure/security-center/security-center-management-groups" target="_blank">Obter visibilidade em todo o locatário para a central de segurança do Azure</a>. Esse processo inclui:

    - Conceder a função de leitor para todas as assinaturas a si mesmo e a todos os outros administradores do Microsoft Cloud App Security aos quais você deseja permitir acesso a esta página.
    - Atribuir a função ao grupo de gerenciamento raiz na Central de Segurança do Azure
    - Elevar o seu administrador Global do Azure AD para permitir acesso a assinaturas do Azure.
    - O artigo descreve o processo para tornar-se um administrador da segurança. Para que essa integração funcione, as permissões mínimas necessárias são **leitor**.

1. Abra a <a href="https://ms.portal.azure.com/#blade/Microsoft_Azure_Security/SecurityMenuBlade/0" target="_blank">Central de Segurança do Azure</a> para que as alterações entrem em vigor.

## <a name="how-to-view-azure-security-recommendations"></a>Como exibir as recomendações de segurança do Azure

1. Em Cloud app Security, navegue para **investigar**a  >  **configuração de segurança**e, em seguida, selecione a guia **Azure** .

    > [!NOTE]
    > Pode levar até 15 minutos para que as alterações entrem em vigor.

    ![menu de configuração de segurança](media/security-configuration-menu.png)

1. Você pode filtrar as recomendações por tipo, recurso e assinatura. Além disso, você pode clicar no ícone de configuração de segurança ![Ícone ASC](media/asc-icon.png) para abrir a recomendação na Central de Segurança do Azure para obter mais informações e se aprofundar na recomendação.

    > [!NOTE]
    > Para simplificar ainda mais a investigação, você pode criar consultas personalizadas e salvá-las para uso posterior. Após concluir a criação da sua consulta, clique no botão **Salvar como** no canto superior direito dos filtros.  No pop-up **Salvar consulta** , nomeie sua consulta.

    ![configuração de segurança](media/security-configuration-azure.png)

Para obter informações de como implementar as recomendações de segurança, confira [Gerenciando recomendações de segurança na Central de Segurança do Azure](https://docs.microsoft.com/azure/security-center/security-center-recommendations).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]

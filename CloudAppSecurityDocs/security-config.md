---
title: Obter recomendações de configuração de segurança para o Azure-Cloud App Security | Microsoft Docs
description: Este artigo fornece informações de como obter recomendações de configuração de segurança no Cloud App Security por meio da integração com a Central de segurança do Azure.
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
ms.openlocfilehash: 1e53dcc94b6ca96aeefcfd511e4ae4e9557e5a21
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2019
ms.locfileid: "74460494"
---
# <a name="security-configuration-for-azure"></a>Configuração de segurança para o Azure

*Aplica-se ao: Microsoft Cloud App Security*

O Microsoft Cloud App Security fornece uma avaliação de configuração de segurança do seu ambiente do Azure. A avaliação, alimentada pela Central de Segurança do Azure, fornece recomendações para configuração ausente e controle de segurança.

## <a name="enable-security-configuration-recommendations"></a>Habilitar as recomendações de configuração de segurança

Para usar esse recurso, você precisa ter as permissões apropriadas no Azure AD e no portal do Azure. Por padrão, a função de Administrador global do Azure AD não fornece acesso às assinaturas do Azure. Eleve as permissões para permitir acesso a assinaturas do Azure para você e outros usuários.

> [!IMPORTANT]
> É recomendado que você desabilite a elevação depois de concluir o processo a seguir.

Para habilitar as recomendações de configuração de segurança no Microsoft Cloud App Security:

1. <a href="https://docs.microsoft.com/azure/security-center/security-center-management-groups" target="_blank">Obtenha visibilidade de todos os locatários na Central de Segurança do Azure</a>. Esse processo inclui:
   - Conceder a função de leitor para todas as assinaturas a si mesmo e a todos os outros administradores do Microsoft Cloud App Security aos quais você deseja permitir acesso a esta página.
   - Atribuir a função ao grupo de gerenciamento raiz na Central de Segurança do Azure
   - Elevar o seu administrador Global do Azure AD para permitir acesso a assinaturas do Azure.
   - O artigo descreve o processo para tornar-se um administrador da segurança. Para que essa integração funcione, as permissões mínimas necessárias são de **Leitor**.

2. Abra a <a href="https://ms.portal.azure.com/#blade/Microsoft_Azure_Security/SecurityMenuBlade/0" target="_blank">Central de Segurança do Azure</a> para que as alterações entrem em vigor.

3. Em Cloud App Security, navegue para **investigar** > **configuração de segurança**e, em seguida, selecione a guia **Azure** .
    - O Microsoft Cloud App Security fornece recomendações apenas para as 50 principais assinaturas.
    - Pode levar até 15 minutos para que as alterações entrem em vigor.

     ![menu de configuração de segurança](media/security-configuration-menu.png)

4. Você pode filtrar as recomendações por tipo, recurso e assinatura. Além disso, você pode clicar no ícone de configuração de segurança ![Ícone ASC](./media/asc-icon.png) para abrir a recomendação na Central de Segurança do Azure para obter mais informações e se aprofundar na recomendação.

Para obter informações de como implementar as recomendações de segurança, confira [Gerenciando recomendações de segurança na Central de Segurança do Azure](https://docs.microsoft.com/azure/security-center/security-center-recommendations).

   ![configuração de segurança](media/security-configuration-azure.png)

## <a name="next-steps"></a>Próximas etapas

[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
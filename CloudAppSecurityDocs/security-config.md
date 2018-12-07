---
title: Obter recomendações de configuração de segurança no Cloud App Security | Microsoft Docs
description: Este artigo fornece informações de como obter recomendações de configuração de segurança no Cloud App Security por meio da integração com a Central de segurança do Azure.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/30/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: c6d8f8af-867b-43ab-adee-f06520577fe7
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 23872b74d9069ee1092d9321667e165c32bdb3c2
ms.sourcegitcommit: cae782d508db9d1a7c0c362e9a23e83f74d48b21
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2018
ms.locfileid: "52743549"
---
# <a name="security-configuration"></a>Configuração de segurança

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

3. No portal do Microsoft Cloud App Security, acesse **Investigar** e, em seguida **Configuração de segurança**. 
    - O Microsoft Cloud App Security fornece recomendações apenas para as 50 principais assinaturas. 
    - Pode levar até 15 minutos para que as alterações entrem em vigor.

     ![menu de configuração de segurança](./media/security-configuration-menu.png)

4. Você pode filtrar as recomendações por tipo, recurso e assinatura. Além disso, você pode clicar no ícone de configuração de segurança ![Ícone ASC](./media/asc-icon.png) para abrir a recomendação na Central de Segurança do Azure para obter mais informações e se aprofundar na recomendação. 

Para obter informações de como implementar as recomendações de segurança, confira [Gerenciando recomendações de segurança na Central de Segurança do Azure](https://docs.microsoft.com/azure/security-center/security-center-recommendations).

   ![configuração de segurança](./media/security-configuration1.png)

## <a name="next-steps"></a>Próximas etapas 
[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  

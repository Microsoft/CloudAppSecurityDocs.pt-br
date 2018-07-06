---
title: Obter recomendações de configuração de segurança no Cloud App Security | Microsoft Docs
description: Este artigo fornece informações de como obter recomendações de configuração de segurança no Cloud App Security por meio da integração com a Central de segurança do Azure.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 6/27/2018
ms.topic: article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: c6d8f8af-867b-43ab-adee-f06520577fe7
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 0d21df4cac9ca31207b94061d5bb18ec857668ac
ms.sourcegitcommit: c7e4351345d55cfeb0517651446490ce5f208651
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2018
ms.locfileid: "37140764"
---
*Aplica-se ao: Microsoft Cloud App Security*


# <a name="security-configuration"></a>Configuração de segurança

O Microsoft Cloud App Security fornece uma avaliação da configuração de segurança do seu ambiente do Azure e recomendações sobre configurações e controles de segurança ausentes, na plataforma Central de Segurança do Azure. 

Para usar esse recurso, você precisa ter as permissões apropriadas no Azure AD e no portal do Azure.
 
Por padrão, a função de Administrador global do Azure AD não fornece acesso às assinaturas do Azure. Por isso, você precisa elevar suas permissões para poder conceder a si mesmo e a outros usuários o acesso às assinaturas do Azure. 

> [!NOTE]
> É recomendado que você desabilite a elevação depois de concluir o processo a seguir.

Para habilitar as recomendações de configuração de segurança no Microsoft Cloud App Security:

1. <a href="https://docs.microsoft.com/azure/security-center/security-center-management-groups" target="_blank">Obtenha visibilidade de todo o locatário na Central de Segurança do Azure</a> concedendo a você e a todos os outros administradores do Microsoft Cloud App Security que precisam de acesso a essa página a função de Leitor para todas as assinaturas, atribuindo a função no grupo de gerenciamento raiz na Central de Segurança do Azure e elevando seu Administrador global do Azure AD para permitir acesso de assinaturas do Azure. 

   > [!NOTE]
   > O artigo descreve o processo para tornar-se um administrador da segurança. Para que essa integração funcione, as permissões mínimas necessárias são de Leitor.

2. Abra a <a href="https://ms.portal.azure.com/#blade/Microsoft_Azure_Security/SecurityMenuBlade/0" target="_blank">Central de Segurança do Azure</a> para que as alterações entrem em vigor.

3. No portal do Microsoft Cloud App Security, acesse **Investigar** e, em seguida **Configuração de segurança**. 

   ![menu de configuração de segurança](./media/security-configuration-menu.png)

   > [!NOTE]
   > O Microsoft Cloud App Security fornece recomendações apenas para as 50 principais assinaturas.
   > Pode levar até 15 minutos para que as alterações entrem em vigor.

5. Você pode filtrar as recomendações por tipo, recurso e assinatura. Além disso, você pode clicar no ícone de configuração de segurança ![Ícone da ASC](./media/asc-icon.png) para abrir a recomendação na Central de Segurança do Azure para obter mais informações e aprofundar-se na recomendação. <br></br><br></br>Para obter informações de como implementar as recomendações de segurança, confira [Gerenciando recomendações de segurança na Central de Segurança do Azure](https://docs.microsoft.com/azure/security-center/security-center-recommendations).

 
   ![configuração de segurança](./media/security-configuration1.png)

 

## <a name="see-also"></a>Consulte Também  
[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)   

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  

---
title: "Criar políticas para controlar o uso de aplicativos de nuvem com o proxy do Cloud App Security | Microsoft Docs"
description: "Este tópico fornece informações sobre como criar políticas para controlar o uso de aplicativos de nuvem com o proxy do Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 7/16/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: b419aff0-3f50-4917-9ee2-9ecf7539a5d7
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 4544f5b48484f9341bb85d09d8fdc8d11fd4ba00
ms.sourcegitcommit: c5a0d07af558239976ce144c14ae56c81642191b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/03/2017
---
# <a name="controlling-app-use-with-proxy-control"></a>Controlar o uso de aplicativos com o controle de Proxy

Depois de implantar o proxy, você pode controlar o acesso e as sessões na nuvem da sua organização com a criação de políticas para bloquear o acesso e o comportamento indesejados.

## <a name="create-access-control-policies-in-cloud-app-security"></a>Criar políticas de controle de acesso no Cloud App Security

Para criar políticas de controle de acesso:

1.  Em **Controle,** selecione **Políticas**.

2.  Em **Criar política**, escolha **Política de proxy** e, em seguida, como o **Tipo de atividade**, selecione **Log de logon único no**.

3.  Em seguida, escolha o aplicativo relevante e os filtros, e escolha a opção de atenuante que preferir.

>[!NOTE]
> Em filtros, você pode escolher **Marca de dispositivo** e defini-lo para ser igual ou não a **Dispositivo gerenciado**. Veja abaixo para obter mais informações sobre [Dispositivos gerenciados](#_Managed_devices).

Além disso, observe que, nas **Ações atenuantes,** você pode escolher **Log** ou **Bloquear o acesso**, ou **Rota para o Cloud App Security**, que permitirá que você monitore e crie políticas na sessão. Isso será explicado com mais detalhes em [Criar políticas de controle de sessão no Cloud App Security](#_Creating_session_control).

## <a name="create-session-control-policies-in-cloud-app-security"></a>Criar políticas de controle de sessão no Cloud App Security 

Depois de implantar o proxy, você pode adicionar recursos de controle de sessão definindo políticas de sessão no portal do Cloud App Security.

É recomendável que você inicie permitindo o controle de sessão para um pequeno grupo de usuários antes de implantá-lo em sua organização. Além disso, não recomendamos habilitar o controle de sessão para todas as sessões ou para a maioria das sessões. Como o controle de sessão se baseia em uma implantação sem agente que tem suas limitações, ele é projetado para abranger os casos em que você terá controle limitado ou nenhum sobre o dispositivo e o aplicativo.

Para criar políticas de controle de sessão:

1.  Crie uma [política de acesso](#working-with-proxy-control-features) e, em seguida, como a ação atenuante, escolha **Rota para o Cloud App Security**.

2.  Em **Controle**, vá para **Políticas** e, em **Criar política** escolha **Política de proxy.**

3.  Em seguida, como o **Tipo de atividade,** escolha **Arquivo de Download** ou **Exportar relatório**. Escolha o aplicativo relevante e os filtros, e escolha a opção de atenuante conforme o necessário.

## <a name="enabling-managedunmanaged-device-control"></a>Habilitar o controle de dispositivo gerenciado/não gerenciado

### <a name="step-1-deploy-certificates"></a>ETAPA 1: Implantar certificados

Para o Cloud App Security identificar quais dispositivos que se conectam a sua nuvem são gerenciados ou não gerenciados, você deverá implantar certificados do cliente. Isso pode ser realizado de várias maneiras, geralmente aproveitando os certificados do uma solução de gerenciamento de dispositivo móvel existente ou usando as políticas de grupo do Active Directory.

### <a name="step-2-upload-the-root-certificate-to-cloud-app-security"></a>ETAPA 2: Carregue o certificado raiz para o Cloud App Security

Para ativar a identificação dos dispositivos gerenciados no portal do Cloud App Security, primeiro você precisa carregar o certificado raiz da autoridade de certificação:

1.  Clique na engrenagem Configurações e escolha **Dispositivos gerenciados.**

2.  Habilite **Identificação de dispositivo**.

3. Carregue o certificado raiz.

![certificado do dispositivo gerenciado de proxy do cloud app security](./media/managed-device-cert.png)

### <a name="step-3-create-managed-device-policies"></a>ETAPA 3: Criar políticas do dispositivo gerenciado

Depois que o certificado raiz é carregado, use o filtro **Marcar dispositivo** é igual ou não **Dispositivo gerenciado** para criar políticas de proxy ou pesquisar eventos no log de atividades.

Ao usar certificados do cliente como uma maneira de identificar os dispositivos gerenciados, é recomendável iniciar no modo de monitoramento antes de tentar bloquear ou monitorar a sessão. Isso significa que você define uma política de acesso com um filtro de **Dispositivo gerenciado** no qual a ação de atenuante é **Log apenas**. Depois que tiver alguma experiência com os usuários, você poderá adicionar outras ações de atenuação como bloquear o acesso ou monitorar a sessão.


## <a name="see-also"></a>Veja também  
[Trabalhando com o proxy do Cloud App Security](proxy-intro.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
---
title: Trabalhando com o proxy do Cloud App Security | Microsoft Docs
description: "Este tópico fornece informações sobre como funciona o proxy do Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 8/9/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 28317b70-1851-4610-b1d6-863bc5994bb6
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: d4b01d92f705566bac36d764a7aede0eaa8defcc
ms.sourcegitcommit: 4cf65f627f2d370ee4a4decae1acbb9658874056
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2017
---
# <a name="working-with-the-cloud-app-security-proxy"></a>Trabalhando com o proxy do Cloud App Security

Na área de trabalho de hoje em dia, geralmente não é suficiente saber o que está acontecendo em seu ambiente de nuvem após o fato, você deseja ser capaz de parar as violações e os vazamentos em tempo real, antes que os funcionários intencional ou inadvertidamente coloquem seus dados e sua organização em risco. Você precisa ser capaz de permitir que os usuários em sua organização aproveitem ao máximo os serviços e as ferramentas disponíveis para eles em aplicativos de nuvem e tragam seus próprios dispositivos para o trabalho. Ao mesmo tempo, você precisa de ferramentas que ajudem a proteger a sua organização contra vazamentos de dados, ataques de ransomware e roubo de dados em massa. 

## <a name="introducing-the-cloud-app-security-proxy"></a>Introduzindo o proxy do Cloud App Security
O proxy do Cloud App Security fornece as ferramentas necessárias para executar o monitoramento em tempo real e controlar o acesso ao seu ambiente de nuvem, bem como as atividades executadas nele.
Com o proxy do Cloud App Security, você pode proteger sua organização de:
- Evitar o vazamento de dados bloqueando os downloads antes que eles ocorram
- Minimizar a exposição a ransomware gerenciando e bloqueando o acesso à sua rede de dispositivos não gerenciados que podem não ser protegidos por senha ou têm software antivírus instalado
- Definir as regras que forçam os dados armazenados em e baixados da nuvem a serem protegidos com criptografia
- Obter visibilidade para pontos de extremidade desprotegidos para que você possa monitorar o que está sendo feito em dispositivos não gerenciados
- Controlar o acesso de endereços IP arriscados e provedores de identidade herdados

Para habilitar esses recursos exclusivos, use os dois níveis de controle fornecidos pelo proxy: controle de acesso e controle de sessão. Os dois tipos de controle aproveitam as informações do usuário, as informações de local e as informações do dispositivo (usadas para identificar quais dispositivos são gerenciados e não gerenciados), para tomar decisões de política para cada aplicativo.

## <a name="access-control"></a>Controle de acesso
O controle de acesso oferece a capacidade de monitorar, auditar e bloquear o acesso – com base no aplicativo, no dispositivo, no usuário e no local. Dessa forma, é possível controlar, em tempo real, o acesso aos seus aplicativos de nuvem.

O controle de acesso permite criar políticas avançadas, como:
 - bloquear o acesso a todos os aplicativos de nuvem de dispositivos não gerenciados
 - bloquear o acesso a aplicativos de nuvem específicos para usuários específicos
 - monitorar o acesso a aplicativos de nuvem específicos de locais específicos
 - limitar o acesso a aplicativos de nuvem a locais e grupos de usuários específicos

Para usar o Controle de acesso no Cloud App Security, implante o proxy fazendo algumas alterações em sua configuração de provedor de identidade existente e defina uma política para controlar os aplicativos de nuvem. 

> [!NOTE]
> -  Não é necessário alterar as políticas existentes do provedor de identidade.

### <a name="how-access-control-works"></a>Como funciona o controle de acesso

Como parte da implantação do proxy, você modificará a configuração do provedor de identidade e do aplicativo para redirecionar as solicitações de logon para o proxy. 

Depois disso, todos os eventos de logon serão roteados por meio do proxy, e o proxy poderá decidir se deseja permitir o acesso ao aplicativo, negá-lo ou monitorá-lo.

### <a name="supported-apps-and-identity-providers"></a>Aplicativos e provedores de identidade compatíveis

O Controle de acesso dá suporte a qualquer aplicativo e a qualquer provedor de identidade compatível com os protocolos Web Services Federation e SAML. A equipe do Cloud App Security testou os principais provedores de identidade e os principais aplicativos com os recursos de controle de acesso. Contudo, como há muitos provedores de identidade e muitos aplicativos de nuvem, é recomendável testar o processo de logon único com seu provedor de identidade e o aplicativo em uma área restrita ou em um ambiente de teste antes de implantá-lo em um ambiente de produção.

## <a name="session-control"></a>Controle de sessão

O Controle de sessão oferece uma camada de controle adicional, fornecendo informações sobre cada atividade em cada sessão de usuário. O Controle de sessão permite um profundo monitoramento do nível de sessão, conferindo-lhe visibilidade granular sobre os aplicativos de nuvem como a de proxies em linha para aplicativos locais. Em vez de permitir e bloquear o acesso completamente, com o controle de sessão, é possível limitar as atividades de sessão específicas. 

Por exemplo, é possível decidir que, de dispositivos não gerenciados ou, para sessões provenientes de locais específicos, você deseja permitir que o usuário acesse o aplicativo, mas limitar o download de arquivos confidenciais. 

### <a name="how-session-control-works"></a>Como funciona o controle de sessão

O controle de sessão do proxy é criado com base no controle de acesso. Depois de controlar o acesso a um aplicativo, é possível definir políticas de sessão que redirecionarão as sessões de usuário para o controle de sessão do proxy. Daí em diante, as solicitações do usuário e as respostas passam pelo proxy em vez de diretamente para o aplicativo.

Para manter o usuário dentro da sessão, o proxy substitui todas as URLs, os scripts Java e os cookies relevantes dentro do aplicativo para páginas duplicadas no proxy. Por exemplo: se o aplicativo retorna uma página com links que terminam com *myapp.com*, o proxy a substituirá por páginas que terminam com algo como *myapp.com.cas.ms*.

Depois que uma sessão é direcionada por meio do proxy, o proxy pode inspecionar o tráfego, exibir os eventos que identifica no portal do proxy do Cloud App e aplicar as políticas na sessão.

## <a name="device-identification"></a>Identificação de dispositivo

O Cloud App Security permite identificar e criar políticas de Proxy com base na postura do dispositivo. Para identificar se um dispositivo é gerenciado ou não, o Cloud App Security usa:
 - Dispositivos em conformidade com o Intune* 
 - Dispositivos ingressados no domínio do Azure AD * 
 - Implantação de certificados do cliente (para todos os aplicativos)

* Disponível somente para aplicativos do Azure AD em que o acesso condicional está disponível

## <a name="architecture"></a>Arquitetura

A integração com os recursos de proxy é simplificada com o Azure Active Directory. Também é possível usar os dispositivos em conformidade com o Intune e ingressados no domínio do Azure AD para facilitar a identificação de dispositivos na criação de políticas. 

Para definir outros provedores de identidade e aplicativos para trabalhar com o proxy, ambos precisam ser configurados para redirecionar as solicitações de logon para o proxy.

Além disso, a fim de identificar os dispositivos gerenciados, o Proxy pode solicitar certificados do cliente de dispositivos gerenciados. Quando um certificado do cliente é recebido pelo proxy, o dispositivo é considerado gerenciado e políticas em dispositivos gerenciados e não gerenciados entram em vigor.

Para obter mais informações sobre o processo de implantação, consulte [Proxy deployment](proxy-deployment.md) (Implantação do proxy).

![Arquitetura do proxy do Cloud App Security](./media/proxy-architecture.png)

## <a name="user-login-flow"></a>Fluxo de logon do usuário

1. O usuário envia uma solicitação ao provedor de identidade e fornece credenciais.
2.  Se o acesso for permitido, o provedor de identidade redirecionará o usuário para o proxy do Cloud App Security.
3.  Se o usuário tiver um certificado do cliente instalado e houver uma política correspondente que verifica os dispositivos gerenciados ou não gerenciados, o usuário será solicitado a fornecer certificados do cliente. De qualquer forma, uma política de acesso é avaliada.
4.   Neste ponto, há três opções possíveis:
    -   O usuário tem permissão para acessar o aplicativo
    -   O usuário está impedido de acessar o aplicativo
    -   O usuário tem permissão para acessar o aplicativo, mas em modo monitorado
        -   Nesse caso, o usuário é redirecionado novamente para o proxy do Cloud App Security, que monitora toda a sessão entre o usuário e o aplicativo. Durante o monitoramento, o proxy avalia as políticas de sessão e pode executar ações de bloqueio adequadamente.

>[!NOTE]
> O diagrama acima descreve um *Logon iniciado pelo provedor de identidade*. Se o usuário iniciar pelo aplicativo, um *Logon iniciado pelo provedor de serviço*, ele será direcionado ao proxy do Cloud App Security e, em seguida, ao provedor de identidade antes de concluir o fluxo do *Logon iniciado pelo provedor de identidade*.

## <a name="managed-devices-flow"></a>Fluxo de dispositivos gerenciados

Para identificar os dispositivos gerenciados não gerenciados pelo Azure AD, o proxy usa o mecanismo de certificados do cliente. O mecanismo funciona da seguinte maneira:

1   Se o usuário tiver um certificado do cliente instalado no dispositivo e houver uma política correspondente que verifica os dispositivos gerenciados ou não gerenciados.
   -   Quando o usuário entra na página do proxy durante a fase de logon, o proxy solicita um certificado do cliente do dispositivo do usuário.

   -   O dispositivo de usuário é solicitado a fornecer o certificado do cliente e se ele aprova, o certificado do cliente é enviado para o proxy.

   -   O proxy autentica o certificado do cliente em relação ao certificado raiz fornecido pelo administrador.

   -   Se o certificado do cliente fornecido pelo dispositivo for autenticado com êxito com o certificado raiz, o dispositivo será considerado gerenciado.

-   Se qualquer uma das etapas anteriores não for concluída, o dispositivo será considerado não gerenciado.



## <a name="see-also"></a>Veja também  
[Implantação do proxy](proxy-deployment.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
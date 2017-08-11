---
title: Trabalhando com o proxy do Cloud App Security | Microsoft Docs
description: "Este tópico fornece informações sobre como funciona o proxy do Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 7/31/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 28317b70-1851-4610-b1d6-863bc5994bb6
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 46377a8447ca7a7c0e98183b9d114c329d040e74
ms.sourcegitcommit: c5a0d07af558239976ce144c14ae56c81642191b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/03/2017
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

### <a name="access-control"></a>Controle de acesso
<more information about what is access control including examples> O Controle de acesso de proxy permite que você crie políticas de acesso avançadas para seus aplicativos de nuvem e fornece os seguintes recursos:

Para usar o Controle de acesso no Cloud App Security, implante o Proxy fazendo algumas alterações em sua configuração de provedor de identidade existente e defina uma política para controlar os aplicativos de nuvem. 

> [!NOTE]
> -  Não é necessário alterar as políticas existentes do provedor de identidade.

### <a name="supported-apps-and-identity-providers"></a>Aplicativos e provedores de identidade compatíveis

O Controle de acesso do proxy foi projetado para dar suporte a qualquer aplicativo e qualquer provedor de identidade que oferece suporte a protocolos SAML ou Web Services Federation. A equipe do Cloud App Security está testando os principais provedores de identidade e os aplicativos principais com os recursos de controle de acesso. No entanto, como há muitos provedores de identidade e muitos aplicativos de nuvem, nem toda combinação de provedores de identidade e aplicativo é testada. É recomendável testar o processo de logon único com seu provedor de identidade e o aplicativo em uma área restrita ou ambiente de teste antes de implantá-lo em um ambiente de produção.

### <a name="session-control"></a>Controle de sessão

O Controle de sessão é uma camada adicional de controle fornecida pelo proxy. Ele permite o controle ainda mais granular e em tempo real sobre seus aplicativos de nuvem. Em vez de configurar uma política ampla para permitir ou bloquear o acesso a um determinado aplicativo, você pode permitir o acesso e, enquanto monitora a sessão de cada usuário no aplicativo, limitar o acesso de várias maneiras. Por exemplo, você pode decidir que, de determinados dispositivos ou para sessões provenientes de locais específicos, deseja permitir que o usuário acesse o aplicativo, mas limitar o download de arquivos confidenciais.

#### <a name="supported-apps-and-flows"></a>Fluxos e aplicativos compatíveis

Atualmente, o Controle de sessão permite que você bloqueie o download de arquivo e a exportação de relatórios no Salesforce.com. Você pode criar políticas com base em usuário, local e dispositivo, e também com base no conteúdo que deseja baixar.

Além disso, esta versão oferece suporte a sessões limitadas para os usuários que fazem logon em navegadores. Por exemplo, se você quiser limitar o acesso para sessões provenientes de aplicativos nativos, precisará definir uma política de acesso para bloquear esse acesso quando o filtro **Marca de agente do usuário** for igual a **Cliente nativo**.

O Salesforce é testado em todos os fluxos normais. No entanto, como o Salesforce tem vários aplicativos de terceiros, pode haver alguns que não foram testados e podem não funcionar com o Controle de sessão e até mesmo impedir o funcionamento de algumas páginas. Para verificar que é realmente um problema de aplicativo de terceiros, remova todos os aplicativos de terceiros e teste o aplicativo com o controle de sessão. Se tudo correr bem, adicione os aplicativos de terceiros um de cada vez até encontrar o aplicativo problemático. 

## <a name="device-management"></a>Gerenciamento de dispositivos

O Cloud App Security permite identificar e criar políticas de Proxy com base na postura do dispositivo. Para identificar se um dispositivo é gerenciado ou não, o Cloud App Security aproveita o mecanismo de certificados do cliente, no qual os certificados do cliente são implantados em dispositivos gerenciados da sua organização. Depois que os usuários realizam logons em um aplicativo, eles deverão fornecer o certificado do cliente instalado no dispositivo. Se um certificado do cliente for fornecido, o Cloud App Security considera o dispositivo gerenciado. 
> [!NOTE]
>  O usuário pode optar por recusar o envio de certificados do cliente e, nesse caso, o dispositivo será considerado não gerenciado.
<Agora você sabe se é gerenciado ou não. E o que se faz com ele?>

### <a name="supported-browsers-and-native-apps"></a>Navegadores e aplicativos nativos compatíveis

O proxy do Cloud App Security permite que você... com base nos certificados do cliente...

Os Certificados do cliente são um mecanismo bem conhecido que os desenvolvedores de navegador e aplicativos nativos podem decidir implementar ou não. A maioria dos navegadores na maioria das plataformas dão suporte a ele, mas a situação em aplicativos nativos é mais complicada.

O suporte para certificados do cliente em aplicativos nativos, que incluem aplicativos de área de trabalho e aplicativos móveis, às vezes pode variar dependendo da plataforma e até mesmo do estado do dispositivo. Por exemplo, no Salesforce1, o aplicativo móvel do Salesforce, os certificados do cliente funcionarão somente se houver um MDM implantado no dispositivo e o Salesforce1 estiver configurado para enviar os certificados do cliente.

Os certificados do cliente foram testados com êxito no Internet Explorer, no Edge, no Chrome, no Safari e no Firefox nas versões mais recentes do Windows, do OSX, do Android e do iOS (cada um com os navegadores correspondentes).

> [!NOTE]
> No iOS, apenas o navegador Safari funciona com certificados do cliente.

Mesmo em casos nos quais navegadores ou aplicativos nativos dão suporte a certificados do cliente, em alguns casos os usuários poderão ter problemas para fornecer o certificado; por exemplo, se um usuário se recusar a enviar um certificado do cliente uma vez, o navegador ou aplicativo nativo pode se lembrar da opção e não solicitar o certificado ao usuário novamente. Para resolver esses problemas, recomendamos fechar todas as instâncias abertas do navegador e, em seguida, abrir novas, ou desmarcar todos os cookies e tentar novamente.

Por outro lado, há alguns navegadores e aplicativos nativos que oferecem suporte à opção para suprimir o pop-up que solicita certificados do cliente e, em vez disso, enviá-los automaticamente.

Em geral, recomendamos que você teste solicitações de certificado do cliente de usuários sem impor políticas, apenas em um modo de monitor. Você pode fazer isso criando uma política de **log apenas** para identificar os dispositivos gerenciados.

## <a name="architecture"></a>Arquitetura

O Proxy é integrado com seu provedor de identidade e o aplicativo, e ambos precisam ser configurados para redirecionar as solicitações de logon para o Proxy.

Além disso, a fim de identificar os dispositivos gerenciados, o Proxy pode solicitar certificados do cliente de dispositivos gerenciados. Quando um certificado do cliente é recebido pelo proxy, o dispositivo é considerado gerenciado e políticas em dispositivos gerenciados e não gerenciados entram em vigor.

Para saber mais sobre o processo de implantação, veja a seção Implantação.

![Arquitetura do proxy do Cloud App Security](./media/proxy-architecture.png)

## <a name="user-login-flow"></a>Fluxo de logon do usuário

O diagrama acima descreve um logon que é iniciado pelo provedor de identidade, também conhecido como *Logon iniciado pelo provedor de identidade*. Se o usuário inicia pelo aplicativo, conhecido como *Logon iniciado pelo provedor de identidade*, ele é direcionado para o Proxy do Cloud App Security que direciona o usuário para o provedor de identidade e o restante do processo de logon é semelhante ao fluxo do *Logon iniciado pelo provedor de identidade*.

Este é o fluxo do *Logon iniciado pelo provedor de identidade*:
-   O usuário envia uma solicitação para o provedor de identidade e fornece as credenciais

-   Se o acesso for permitido, o provedor de identidade redirecionará o usuário para o Proxy do Cloud App Security

-   Se o usuário tiver um certificado do cliente instalado e houver uma política correspondente que verifica os dispositivos gerenciados ou não gerenciados, o usuário será solicitado a fornecer certificados do cliente. De qualquer forma, uma política de acesso é avaliada

-   Neste ponto, há três opções possíveis:

    -   O usuário tem permissão para acessar o aplicativo

    -   O usuário está impedido de acessar o aplicativo

    -   O usuário tem permissão para acessar o aplicativo, mas em modo monitorado

        -   Nesse caso, o usuário é redirecionado novamente para o Proxy do Cloud App Security, que monitora toda a sessão entre o usuário e o aplicativo

        -   Durante o monitoramento, o Proxy avalia as políticas de sessão e pode executar ações de bloqueio correspondentes

## <a name="how-access-control-works"></a>Como funciona o controle de acesso

Como parte da implantação do Proxy, você precisa alterar as configurações no provedor de identidade e no aplicativo que você deseja controlar. Isso inclui alterações de URL para que o provedor de identidade e o aplicativo redirecione as solicitações de logon para o proxy. Além disso, e se for necessário, os certificados também são substituídos.

Depois que essas etapas forem concluídas, todos os eventos de logon passam pelo proxy e o proxy pode decidir se eles têm permissão para acessar o aplicativo, se tiveram o acesso negado ou se podem acessar em modo monitorado. Observe que, neste estágio, o Proxy pode solicitar certificados do cliente do dispositivo e usar o estado do dispositivo para tomar decisões sobre a política.

## <a name="how-session-control-works"></a>Como funciona o controle de sessão

O controle de sessão do proxy é criado com base no controle de acesso. Depois que você controla o acesso a um aplicativo, pode decidir, com base nas políticas de acesso, monitorar a sessão redirecionando suas sessões para o controle de sessão do proxy. Daí em diante, as solicitações do usuário e as respostas passam pelo proxy em vez de diretamente para o aplicativo.

Para manter o usuário dentro da sessão, o proxy substitui todas as URLs, os scripts Java e os cookies relevantes dentro do aplicativo para páginas duplicadas no proxy. Por exemplo: se o aplicativo retorna uma página com links que terminam com *myapp.com*, o proxy a substituirá por páginas que terminam com algo como *myapp.com.cas.ms*.

Depois que uma sessão é direcionada por meio do proxy, o proxy pode inspecionar o tráfego, exibir os eventos que identifica no portal do proxy do Cloud App e aplicar as políticas na sessão.

## <a name="how-identifying-managed-devices-works"></a>Como funciona a identificação de dispositivos gerenciados

Para identificar os dispositivos gerenciados, o proxy usa o mecanismo de certificados do cliente. O mecanismo funciona da seguinte maneira:

-   Se o usuário tiver um certificado do cliente instalado no dispositivo e houver uma política correspondente que verifica os dispositivos gerenciados ou não gerenciados.

    -   Quando o usuário entra na página do proxy durante a fase de logon, o proxy solicita um certificado do cliente do dispositivo do usuário.

    -   O dispositivo de usuário é solicitado a fornecer o certificado do cliente e se ele aprova, o certificado do cliente é enviado para o proxy.

    -   O proxy autentica o certificado do cliente em relação ao certificado raiz fornecido pelo administrador.

    -   Se o certificado do cliente fornecido pelo dispositivo for autenticado com êxito com o certificado raiz, o dispositivo será considerado gerenciado.

-   Se qualquer uma das etapas anteriores não for concluída, o dispositivo será considerado não gerenciado.



## <a name="see-also"></a>Veja também  
[Implantação do proxy](proxy-deployment.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
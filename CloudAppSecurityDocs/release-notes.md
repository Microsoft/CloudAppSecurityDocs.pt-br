---
title: Novidades do Cloud App Security | Microsoft Docs
description: Este tópico é atualizado com frequência para você saber quais são as novidades na versão mais recente do Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/11/2018
ms.topic: article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: d418ef3d-76ee-45d5-b5ae-21346e5239a3
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 9f76d43ab9bda33632502ea2acd7491d8ec7b32a
ms.sourcegitcommit: d9b65152d06b9924231b296ffe565689b44ab93e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="whats-new-with-microsoft-cloud-app-security"></a>Novidades do Microsoft Cloud App Security

## <a name="cloud-app-security-release-120"></a>Cloud App Security versão 120
Lançado em 8 de abril de 2018

-   Para o Office 365 e para o Azure AD, agora estamos implementando gradualmente a capacidade de detectar aplicativos internos como atividades de conta do usuário realizada por aplicativos do Office 365 e do Azure AD (tanto internos quanto externos). Isso permite criar políticas que alertarão você caso um aplicativo execute atividades inesperadas e não autorizadas. 
-   Ao exportar uma lista de permissões de aplicativo para csv, campos adicionais como editor, nível de permissões e uso da comunidade são incluídos para auxiliar no processo de investigação e na conformidade.
-   O aplicativo conectado ServiceNow foi aprimorado para que atividades de serviço internas não sejam mais registradas como tendo sido executadas por "Convidado" e não disparem mais alertas falsos positivos. Agora essas atividades são representadas como N/D, assim como todos os outros aplicativos conectados.


## <a name="cloud-app-security-release-119"></a>Cloud App Security versão 119
Lançado em 18 de março de 2018

-   A página de intervalos de endereços IP inclui os endereços IP internos descobertos pelo Cloud App Security. São incluídos endereços IP de serviços de nuvem identificados, como o Office 365 e o Azure, bem como o feed de inteligência contra ameaças que enriquece automaticamente os endereços IP com informações sobre endereços IP arriscados conhecidos. 
-   Agora, quando tenta executar uma ação de governança em um arquivo e falha porque o arquivo está bloqueado, o Cloud App Security automaticamente tenta a ação de governança novamente. 

## <a name="cloud-app-security-release-118"></a>Cloud App Security versão 118
Lançado em 4 de março de 2018

- Agora você pode tirar proveito dos recursos de descoberta e monitoramento de TI sombra do Microsoft Cloud App Security em seus próprios aplicativos personalizados. A nova capacidade de adicionar aplicativos personalizados ao Cloud Discovery permite monitorar o uso do aplicativo e receber alertas sobre alterações no padrão de uso. Para saber mais, confira [Proteger seus aplicativos personalizados](cloud-discovery-custom-apps.md). Esse recurso está sendo implantado gradativamente.

- As páginas de **Configurações** do portal do Cloud App Security foram reformuladas. O novo design consolida todas as páginas de configurações, fornece a funcionalidade de pesquisa e um design aprimorado. 

- Agora, o Cloud Discovery dá suporte a Firewalls Barracuda série F e streaming de log da Web do Firewall Barracuda série F.

- Agora, a funcionalidade de pesquisa nas páginas de endereço IP e de Usuário permite o preenchimento automático para facilitar a localização do que você está procurando.

- Agora você pode executar ações em massa nas páginas de configurações Excluir entidades e Excluir endereços IP. Isso facilita a seleção de vários usuários e grupos ou endereços IP e os exclui do monitoramento como parte do Cloud Discovery em sua organização. 

## <a name="cloud-app-security-release-117"></a>Cloud App Security versão 117
Lançado em 20 de fevereiro de 2018

-   Agora, a integração avançada do Cloud App Security com a Proteção de Informações do Azure permite que você proteja arquivos no G Suite. Esse recurso de visualização pública permite examinar e classificar arquivos no G Suite, e aplicar automaticamente os rótulos da Proteção de Informações do Azure para proteção. Para obter mais informações, consulte [Integração com a Proteção de Informações do Azure](azip-integration.md).

-   Agora, o Cloud Discovery dá suporte a [Digital artes i-FILTER](http://www.daj.jp/en/products/if/).

-   A tabela de agentes do SIEM agora inclui mais detalhes para um gerenciamento mais fácil.

## <a name="cloud-app-security-release-116"></a>Cloud App Security versão 116
Lançado em 4 de fevereiro de 2018
- Melhoramos a política de detecção de anomalias do Cloud App Security com novas **detecções baseadas em cenários**, como viagem impossível, atividade de um endereço IP suspeito e várias tentativas de logon com falha. As novas políticas são habilitadas automaticamente, fornecendo a detecção de ameaças pronta para uso no ambiente de nuvem. Além disso, as novas políticas expõem mais dados do mecanismo de detecção do Cloud App Security para ajudar a acelerar o processo de investigação e conter as ameaças em andamento. Para saber mais, confira o artigo [Obter análise comportamental e detecção de anomalias instantaneamente](https://docs.microsoft.com/en-us/cloud-app-security/anomaly-detection-policy).

- Implementação gradual: o Cloud App Security agora correlaciona os usuários e suas contas em aplicativos SaaS. Isso permite investigar facilmente todas as atividades de um usuário, em todos os vários aplicativos SaaS correlacionados, independentemente de qual aplicativo ou conta usaram.  

-   Implementação gradual: o Cloud App Security agora dá suporte a várias instâncias do mesmo aplicativo conectado. Se você tiver várias instâncias do Salesforce (uma para venda, uma para marketing), por exemplo, poderá conectar os dois ao Cloud App Security e gerenciá-los no mesmo console para criar políticas granulares e uma investigação mais detalhada. 

- Os analisadores do Cloud Discovery agora oferecem suporte a dois formatos de ponto de verificação adicionais, XML e KPC.



## <a name="cloud-app-security-release-115"></a>Lançamento 115 do Cloud App Security
Lançado em 21 de janeiro de 2018

- Este lançamento fornece uma experiência aprimorada ao selecionar pastas específicas nas políticas de arquivo. Agora, é possível exibir e selecionar rapidamente várias pastas para incluir em uma política. 
- Na página **Aplicativos descobertos**: 
  - o recurso de marcação em lotes permite aplicar marcações personalizadas, além das marcações Sancionado e Não Sancionado. 
  - Quando você **Gerar um relatório de endereço IP** ou **Gerar o relatório de um usuário**, os relatórios exportados agora incluirão informações sobre a proveniência do tráfego de aplicativos sancionados ou não sancionados. 
- Você já pode solicitar um novo Conector de aplicativos da API à equipe do Microsoft Cloud App Security diretamente no portal, na página **Conectar um aplicativo**. 


## <a name="cloud-app-security-release-114"></a>Cloud App Security versão 114
Lançado em 7 de janeiro de 2018

- A partir da versão 114, gradualmente, desenvolvemos a capacidade de criar e salvar consultas personalizadas no log de Atividades e nas páginas de Aplicativos descobertos. As consultas personalizadas possibilitam criar modelos de filtro que podem ser reutilizados para uma investigação profunda. Além disso, as **Consultas sugeridas** foram adicionadas para fornecer modelos de investigação prontos para uso, a fim de filtrar as atividades e os aplicativos descobertos. As **Consultas sugeridas** incluem filtros personalizados para identificar riscos, como atividades de representação, atividades de administrador, aplicativos de armazenamento em nuvem que apresentam riscos e que estão fora de conformidade, aplicativos empresariais com criptografia fraca e riscos de segurança. Use as **Consultas sugeridas** como ponto de partida, modifique-as conforme considerar adequado e, em seguida, salve-as como uma nova consulta. Para obter mais informações, consulte [Filtros e consultas de atividades](activity-filters-queries.md) e [Filtros e consultas de aplicativos descobertos](discovered-app-queries.md).
 
- Agora você pode verificar o status atual do serviço do Cloud App Security acessando [status.cloudappsecurity.com](https://status.cloudappsecurity.com) ou diretamente no portal clicando em **Ajuda**>**Status do sistema**. 
 


## <a name="see-also"></a>Consulte Também  

Confira a descrição dos lançamentos anteriores aos relacionados aqui em [Lançamentos anteriores do Microsoft Cloud App Security](release-note-archive.md).

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
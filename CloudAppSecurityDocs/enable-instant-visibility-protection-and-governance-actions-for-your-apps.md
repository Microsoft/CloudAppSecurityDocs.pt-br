---
title: Conectar aplicativos para obter visibilidade e controle – Cloud App Security | Microsoft Docs
description: Este artigo descreve o processo para conexão de aplicativos com conectores de API aos aplicativos na nuvem de sua organização.
keywords: ''
author: ShlomoSagir-MS
ms.author: shsagir
manager: ShlomoSagir-MS
ms.date: 7/21/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 3b15ba46-ac9c-4b4f-aefc-137edc903bc1
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: baef4566b6ee972191e0bb36efa1ed3df0946d9e
ms.sourcegitcommit: d1eb8ccf09840c659ba7170a2b92cd62d9d97a02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68494208"
---
# <a name="connect-apps"></a>Conectar aplicativos 

*Aplica-se a: Microsoft Cloud App Security*

Os conectores de aplicativos usam as APIs de provedores de aplicativos para permitir maior visibilidade e controle com o Microsoft Cloud App Security sobre os aplicativos aos quais você se conecta.  

O Microsoft Cloud App Security aproveita as APIs fornecidas pelo provedor de nuvem. Cada serviço tem sua própria estrutura e limitações de API como limitação, limites de API, janelas de API de mudança de tempo dinâmicas e outros. O Microsoft Cloud App Security trabalhou com os serviços para otimizar o uso das APIs e garantir o melhor desempenho. Levando em conta diferentes limitações impostas pelos serviços sobre as APIs, os mecanismos do Cloud App Security usam a capacidade permitida. Algumas operações, como verificação de todos os arquivos no locatário, exigem várias APIs e, portanto, elas são distribuídas por um período mais longo. Espere algumas que algumas políticas sejam executadas por várias horas ou vários dias.  

## <a name="multi-instance-support"></a>Suporte para várias instâncias

O Cloud App Security agora dá suporte a várias instâncias do mesmo aplicativo conectado. Por exemplo, caso você tenha mais de uma instância do Salesforce (uma para venda, uma para marketing), poderá conectar as duas ao Cloud App Security. Você pode gerenciar as diferentes instâncias no mesmo console para criar políticas granulares e uma investigação mais profunda. Esse suporte se aplica somente a aplicativos conectados por API, e não a aplicativos descobertos na nuvem ou aplicativos conectados por proxy.

> [!NOTE]
> Não há suporte para várias instâncias no Office 365 e no Azure.

## <a name="how-it-works"></a>Como funciona  
O Cloud App Security é implantado com privilégios de administrador do sistema para permitir o acesso completo a todos os objetos em seu ambiente.  

O fluxo do Conector de Aplicativos é da maneira a seguir:

1. O Cloud App Security examina e salva as permissões de autenticação.
2. A Segurança de Aplicativo de Nuvem solicita a lista de usuários. Na primeira vez que a solicitação é feita, é necessário algum tempo até que a verificação seja concluída. Depois que a verificação do usuário for encerrada, a Segurança de Aplicativo de Nuvem continuará com as atividades e arquivos. Assim que a verificação for iniciada, algumas atividades estarão disponíveis na Segurança de Aplicativo de Nuvem.
3. Após a conclusão da solicitação do usuário, o Cloud App Security examina periodicamente usuários, grupos, atividades e arquivos. Todas as atividades estarão disponíveis após a primeira verificação.

Essa conexão pode levar algum tempo, dependendo do tamanho do locatário, do número de usuários e do tamanho e número de arquivos que precisam ser examinados. 

Dependendo do aplicativo ao qual você está se conectando, a conexão de API permite os seguintes itens:  

- **Dados da conta** – visibilidade de usuários, contas, informações de perfil, grupos de status (suspenso, ativo, desabilitado) e privilégios.  

- **Trilha de auditoria** – visibilidade das atividades do usuário, atividades de administração e atividades de entrada.  

- **Verificação de dados** – verificação de dados não estruturados usando dois processos: periodicamente (a cada 12 horas) e verificação em tempo real (disparada sempre que uma alteração é detectada).  

- **Permissões de aplicativo** – visibilidade dos tokens emitidos e suas permissões.  

- **Governança de conta** – capacidade de suspender usuários, revogar senhas, etc.  

- **Governança de Dados** – capacidade de colocar arquivos em quarentena, incluindo arquivos na lixeira, bem como de substituir arquivos.  

- **Governança de permissão do aplicativo** – capacidade de remover tokens.  

A tabela a seguir lista por aplicativo de nuvem, quais recursos têm suporte com os conectores de aplicativo:  

> [!div class="mx-tableFixed"]
> 
> ||**Office 365**|**Box**|**Okta**|**G Suite**|**Service Now**|**Salesforce**|**Dropbox**|**AWS**|**Webex**|**Workday**|
> |-|-|-|-|-|-|-|-|-|-|-|
> |**Listar contas**|✔|✔|✔|✔|✔|✔|✔|✔|✔|✔|
> |**Grupo**|✔|✔|✔|✔|✔|✔|✔|✔|Não Aplicável|Não Aplicável|
> |**Privilégios**|✔|✔|Sem suporte pelo provedor|✔|✔|✔|✔||✔|Não Aplicável|
> |**Governança de usuário**|✔|✔||✔|Em breve|Em breve|Em breve||Em breve|Em breve|
> |**Atividade de logon**|✔|✔|✔|✔|✔|✔|✔|✔|✔|✔|
> |**Atividade do usuário**|✔*|✔|✔|✔ – requer o Google Business ou Enterprise|Parcial|Com suporte com o Salesforce Shield|✔|Não Aplicável|✔|✔|
> |**Atividade administrativa**|✔|✔|✔|✔|Parcial|✔|✔|✔|✔|✔|
> |**Verificação de arquivo periódica**|✔|✔|Não Aplicável|✔|✔|✔|✔|Não Aplicável|||
> |**Verificação de arquivo quase em tempo real**|✔|✔|Não Aplicável|✔ – requer o Google Business ou Enterprise|||Em breve||✔||
> |**Controle de compartilhamento**|✔|✔|Não Aplicável|✔|Não Aplicável||✔||✔||
> |**Quarentena**|✔|✔|Não Aplicável|Em breve|||Em breve||Não Aplicável|Não Aplicável|
> |**Exibir permissões de aplicativo**|✔|Sem suporte pelo provedor|Não Aplicável|✔||✔|Sem suporte pelo provedor||Não Aplicável|Não Aplicável|
> |**Revogar permissões de aplicativo**|✔||Não Aplicável|✔||✔|Não Aplicável||Não Aplicável|Não Aplicável|
> |**Aplique os rótulos da Proteção de Informações do Azure**|✔|✔||✔|||||Não Aplicável|Não Aplicável|

## <a name="prerequisites"></a>Pré-requisitos  

- Em alguns aplicativos, pode ser necessário adicionar endereços IP à lista de permissões para permitir que o Cloud App Security colete logs e forneça acesso ao console do Cloud App Security. Para obter mais informações, confira [Requisitos de rede](network-requirements.md).

- Para cada aplicativo que desejar conectar com a integração de API do Cloud App Security, recomendamos criar uma conta de serviço de administrador dedicada ao Cloud App Security.  

> [!NOTE]  
>  Para obter atualizações quando URLs e endereços IP forem alterados, assine o RSS conforme explicado em: [URLs e intervalos de endereços IP do Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).  

Para usar Conectores de Aplicativos, você precisa ter certeza de que tem os seguintes itens para cada aplicativo específico:  

| Aplicativo        | Tipo de licença                                                                        | User                                                                                                                                                                                                  |
|------------|-------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Caixa        | Enterprise                                                                          | É altamente recomendável que você se conecte ao Box como um Administrador. A conexão como Coadministrador resultará em uma visibilidade apenas parcial dos dados. Se você se conectar como Coadministrador, lembre-se de selecionar todas as permissões. |
| G Suite    | G Suite Business ou Enterprise preferencial<br /><br /> G Suite Enterprise (no mínimo) | Superadministrador                                                                                                                                                                                           |
| Office 365 |                                                                                     | Administrador global                                                                                                                                                                                          |
| AWS        |                                                                                     | Usuário recém-criado                                                                                                                                                                                    |
| Dropbox    | Business/Enterprise                                                                 | Administrador                                                                                                                                                                                                 |
| Okta       | Enterprise (não de avaliação)                                                              | Administrador                                                                                                                                                                                                 |
| Exchange   |                                                                                     | Administrador global                                                                                                                                                                                          |
| ServiceNow | Eureka e superior                                                                       | Função admin + RestAPI                                                                                                                                                                                  |
| Salesforce |                                                                                     | Administrador                                                                                                                                                                                                 |
| Webex      |                                                                                     | Admin + administrador de conformidade                                                                                                                                                                              |

<!--| Workday      |                                                                                     | Admin                                                                                                                                                                              |-->

**ExpressRoute**

O Cloud App Security é implantado no Azure e totalmente integrado com o [ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-introduction/). Todas as interações com os aplicativos do Cloud App Security e o tráfego enviado a ele, incluindo o upload de logs de descoberta, são roteados por meio do **emparelhamento público** do ExpressRoute para aprimorar a latência, o desempenho e a segurança. Não há nenhuma etapa de configuração necessária do lado do cliente.  
Para obter mais informações sobre o emparelhamento público, consulte [Circuitos da Rota Expressa e domínios de roteamento](https://azure.microsoft.com/documentation/articles/expressroute-circuit-peerings/).  

## <a name="next-steps"></a>Próximas etapas
 
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/)  

## <a name="check-out-this-video"></a>Confira este vídeo!

[Microsoft Cloud App Security – API REST e Tokens](https://channel9.msdn.com/Shows/Microsoft-Security/Microsoft-Cloud-App-Security--REST-APIs-and-Tokens)  

---
title: "Habilitar ações de visibilidade, proteção e governança instantâneas para seus aplicativos | Microsoft Docs"
description: "Este tópico descreve o processo para habilitar os conectores de API para aplicativos na nuvem da sua organização."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 3b15ba46-ac9c-4b4f-aefc-137edc903bc1
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed4ea71b24767d3602d40894d1cbac7447bcd8a2
ms.openlocfilehash: e74cd96f9bf8537f230dcb58715492bc6fccd2f0


---

# <a name="enable-instant-visibility-protection-and-governance-actions-for-your-apps"></a>Habilitar ações de visibilidade, proteção e governança instantâneas para seus aplicativos
Os conectores de aplicativos aproveitam as APIs de provedores de aplicativo para proporcionar maior visibilidade e controle com o Cloud App Security sobre os aplicativos aos quais você se conecta.  
  
O Cloud App Security aproveita as APIs fornecidas pelo provedor de nuvem, cada serviço tem sua própria estrutura e limitações de API. Ele trabalhou com os serviços para otimizar o uso das APIs de para garantir o melhor desempenho. Considerando as diferentes limitações que os serviços impõem sobre as APIs (como as limitações, limites de API, janelas de API de mudança de tempo dinâmicas etc.), os mecanismos do Cloud App Security aproveitam a capacidade permitida. Algumas operações, como a verificação de todos os arquivos no locatário, exigem uma grande quantidade de APIs e, portanto, são distribuídas por um período mais longo. Espere algumas que algumas políticas sejam executadas por várias horas ou vários dias.  
  
**ExpressRoute**  
  
O Cloud App Security é implantado no Azure e totalmente integrado com o [ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-introduction/). Todas as interações com os aplicativos do Cloud App Security e o tráfego enviado ele, incluindo o upload de logs de descoberta, são roteados por meio do **emparelhamento público** do ExpressRoute para latência, desempenho e segurança aprimorados. Não há nenhuma etapa de configuração necessária do lado do cliente.  
Para obter mais informações sobre o emparelhamento público, consulte [Circuitos da ExpressRoute e domínios de roteamento](https://azure.microsoft.com/documentation/articles/expressroute-circuit-peerings/).  
  
## <a name="how-it-works"></a>Como funciona  
O Cloud App Security é implantado com privilégios de administrador do sistema para permitir o acesso completo a todos os objetos em seu ambiente.  
  
O fluxo do Conector de Aplicativos é da maneira a seguir:
1. A Segurança de Aplicativo de Nuvem examina e salva as permissões de autenticação.
2.  A Segurança de Aplicativo de Nuvem solicita a lista de usuários. Na primeira vez que isso é executado, pode levar algum tempo até que a verificação seja concluída. Depois que a verificação do usuário for encerrada, a Segurança de Aplicativo de Nuvem continuará com as atividades e arquivos. Assim que a verificação for iniciada, algumas atividades estarão disponíveis na Segurança de Aplicativo de Nuvem. 
4. Após a conclusão da solicitação do usuário, a Segurança do Aplicativo de Nuvem verifica periodicamente usuários, grupos, atividades e arquivos. Todas as atividades estarão disponíveis após a primeira verificação. 
 
Isso pode levar algum tempo, dependendo do tamanho do locatário, o número de usuários e o tamanho e número de arquivos que precisam ser verificados. 
 
Dependendo do aplicativo ao qual você está se conectando (consulte a tabela abaixo), a conexão da API habilita o seguinte:  
  
-   **Informações da conta:**  
  
     Visibilidade de usuários, contas, informações de perfil, grupos de status (suspenso, ativo, desabilitado) e privilégios.  
  
-   **Trilha de auditoria:**  
  
     Visibilidade em atividades do usuário, atividades do administrador, atividade de logon.  
  
-   **Verificação de dados:**  
  
     Verificação de dados não estruturados usando dois processos: periodicamente (a cada 12 horas) e verificação em tempo real (disparada sempre que uma alteração é detectada).  
  
-   **Permissões de aplicativo:**  
  
     Visibilidade de tokens emitidos e suas permissões.  
  
-   **Governança de conta:**  
  
     Capacidade de suspender usuários, revogar senhas etc.  
  
-   **Governança de Dados:**  
  
     Capacidade de colocar arquivos em quarentena, incluindo arquivos na Lixeira, e substituir arquivos.  
  
-   **Governança de permissão de aplicativo:**  
  
     Capacidade de remover tokens.  
  
A tabela a seguir lista por aplicativo de nuvem, quais recursos têm suporte com os conectores de aplicativo:  
  
||||||||||  
|-|-|-|-|-|-|-|-|-|  
||**Office 365**|**Box**|**Okta**|**Google Apps**|**Service Now**|**Salesforce**|**Dropbox**|**AWS**|  
|**Listar contas**|✔|✔|✔|✔|✔|✔|✔|✔|  
|**Grupo**|✔|✔|✔|✔|✔|✔|✔|✔|  
|**Privilégios**|✔|✔|Sem suporte pelo provedor|✔|✔|✔|✔||  
|**Governança de usuário**|✔|✔||✔|Em breve|Em breve|Em breve||  
|**Atividade de logon**|✔|✔|✔|✔|✔|✔|✔|✔|  
|**Atividade do usuário**|✔*|✔|✔|✔ – requer Google Unlimited|Parcial|Com suporte com o Salesforce Shield|✔|Não Aplicável|  
|**Atividade administrativa**|✔|✔|✔|✔|Parcial|✔|✔|✔|  
|**Verificação de arquivo periódica**|✔|✔|Não Aplicável|✔|✔|✔|✔|Em breve|  
|**Verificação de arquivo quase em tempo real**|Em breve|✔|Não Aplicável|✔ – requer Google Unlimited|||Em breve||  
|**Controle de compartilhamento**|✔|✔|Não Aplicável|✔|Não Aplicável||✔||  
|**Quarentena**|✔|✔|Não Aplicável|Em breve|||Em breve||  
|**Exibir permissões de aplicativo**|✔|Sem suporte pelo provedor|Não Aplicável|✔||✔|Sem suporte pelo provedor||  
|**Revogar permissões de aplicativo**|✔||Não Aplicável|✔||✔|Não Aplicável||  
  
\* O Conector de Aplicativos do Office 365 inclui atividades de administração para o Exchange Online. Para adicionar a atividade do usuário para o Exchange Online, você precisará implantar o conector do Exchange Online separadamente.  
  
## <a name="prerequisites"></a>Pré-requisitos  
Para alguns aplicativos, pode ser necessário adicionar os seguintes endereços IP à lista de permissões para permitir que Cloud App Security colete logs e forneça acesso para o console do Cloud App Security:  
  
-   Para os logs:  
  
     104.209.35.177  
  
     13.91.98.185  
  
-   Para o console:  
  
     104.42.231.28  
  
> [!NOTE]  
>  Para obter atualizações quando URLs e endereços IP forem alterados, assine o RSS conforme explicado em: [URLs e intervalos de endereços IP do Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).  
  
Para usar conectores de aplicativos, você precisa ter certeza de que tem o seguinte para cada aplicativo específico:  
  
|Aplicativo|Tipo de licença|User|  
|---------|------------------|----------|  
|Caixa|Enterprise|É altamente recomendável que você se conecte ao Box como um Administrador. Conectar-se como um co-administrador resultará apenas em visibilidade parcial dos dados. Se você se conectar como um co-administrador, lembre-se de selecionar todas as permissões.|  
|Google Apps|Google Apps Unlimited preferencial<br /><br /> Google Apps Enterprise (no mínimo)|Superadministrador|  
|Office 365||Administrador global|  
|AWS||Usuário recém-criado|  
|Dropbox|Business/Enterprise|Administrador|  
|Okta|Enterprise (não de avaliação)|Administrador|  
|Exchange||Administrador global|  
|ServiceNow|Eureka e superior|Função de Administrador +RestAPI|  
|Salesforce||Administrador|  
  
## <a name="see-also"></a>Veja também  
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
   


<!--HONumber=Oct16_HO4-->



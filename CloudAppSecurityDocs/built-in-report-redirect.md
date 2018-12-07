---
title: Como localizar relatórios internos preterido no Cloud App Security | Microsoft Docs
description: Este artigo fornece instruções para gerar relatórios preteridos no Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/13/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: a9660e5b-d5bd-4a32-8cb9-0de70af6f1e9
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 40b119b9ea8702ee4e887e5f8d9c94dfe9127091
ms.sourcegitcommit: 77850c6777504c2478611cb71a387e7fcc5f2551
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/13/2018
ms.locfileid: "51597418"
---
# <a name="how-to-find-built-in-deprecating-reports"></a>Como localizar relatórios internos preteridos

*Aplica-se ao: Microsoft Cloud App Security*

Estamos atualizando a funcionalidade de relatórios internos inserindo-a em outras partes do portal. A atualização dessa funcionalidade está em andamento para melhoria dos relatórios do Microsoft Cloud App Security.

## <a name="deprecating-reports"></a>Reprovando relatórios

Essa tabela ajuda você a exibir as informações fornecidas pelos relatórios preteridos usando outras funcionalidades do Cloud App Security:

| Tipo de relatório | Nome do relatório interno | Descrição | Novo local dos dados |
|----|----|----|----|
| Segurança | Atividade | Esse relatório permite exibir uma lista dos países dos quais a atividade foi originada em seus aplicativos na nuvem. O relatório mostra diferentes parâmetros revelando o volume de atividades de cada país, como o número de eventos, o número de usuários e assim por diante. Isso ajuda você a obter uma visão geral da distribuição geográfica dos seus usuários. | Essas informações estão disponíveis para aplicativos, usuários e endereços IP específicos. Para cada aplicativo, clique no aplicativo. Nele, você pode ver o mapa de atividades com todos os locais. Para cada usuário, clique no usuário e na gaveta de insights do usuário. Nele, você pode ver os locais usados recentemente e o número de endereços IP e ISPs usados. Para cada endereço IP, clique no endereço IP específico. Na gaveta do endereço IP, você pode ver quantos usuários e administradores o utilizaram. |
| Segurança | Uso de navegador | Os ataques baseados em navegador estão entre os vetores de ataques mais comuns. Os fornecedores investem grandes quantidades de recursos na proteção do software de navegação, criando um mecanismo de atualização efetivo para publicar atualizações nos pontos de extremidade. O uso de navegadores preteridos muito tempo depois de sua atualização estar vencida torna-os um alvo fácil para invasores que usam kits de exploração disponíveis. Essa funcionalidade permite que você obtenha uma lista dos navegadores desatualizados usados nos últimos 7 dias por usuários que acessam seus aplicativos na nuvem. Também permite saber se o uso de navegador desatualizado foi realizado por um robô. | Vá para o **Log de atividades** e abra **Filtros avançados**. Em seguida, defina o filtro para **Marca de agente do usuário** como igual a **Navegador desatualizado** e **Sistema operacional desatualizado** para ver uma lista de todos os sistemas operacionais e navegadores desatualizados em uso. |
| Segurança | Endereços IP ‑ contas com privilégios| Esse relatório lista os endereços IP usados por dispositivos que executam atividades administrativas nos últimos 7 dias em seu ambiente de nuvem protegido pelo Cloud App Security. A data é baseada em logs de auditoria acumulados pelo Cloud App Security. Os endereços IP são associados a uma localização geográfica e a uma organização de origem. Essas informações permitem identificar os endereços IP suspeitos que se conectam aos seus aplicativos protegidos. Você pode exibir os logs de auditoria para cada endereço IP clicando nele. | Clique em um usuário específico. Em seguida, na gaveta de insights do usuário, você pode ver os locais usados recentemente e o número de endereços IP e ISPs usados. |
| Gerenciamento de usuários | Contas inativas | Contas inativas são contas que têm acesso à sua instância de nuvem, mas não executaram nenhum evento durante os últimos 60 dias. Essa falta de ação sugere que essas contas não estão mais ativas e devem ser suspensas para impedir o acesso futuro por invasores ou ex-funcionários. Seguir essa prática recomendada não apenas melhora sua postura de segurança, mas também reduz os custos operacionais. | Acesse a página **Usuários e contas** e use o filtro **Visto pela última vez** para gerar uma lista de todos os usuários que não executaram nenhuma atividade recentemente. |
| Gerenciamento de usuários | Usuários privilegiados | Este relatório lista os usuários com privilégios elevados nos aplicativos corporativos, como administradores, nos últimos sete dias. Contas com privilégios como essas são um vetor de ataque preferencial para invasores, uma vez que elas podem permitir que eles obtenham acesso substancial às informações corporativas e à configuração de rede. Se houver contas com privilégios que não foram usadas recentemente, isso poderá indicar uma falta de conscientização da segurança de TI nas empresas, potencialmente, abrindo caminho para uma onda de violações de dados. Você pode investigar mais o uso de privilégios de usuário elevados por meio do Log de auditoria e considerar revogar privilégios quando desnecessário. | Vá para a página **Usuários e contas** e use o filtro **Grupos** para gerar uma lista de usuários privilegiados que pertencem ao grupo de administradores. |
| Gerenciamento de usuários | Contas privilegiadas especiais | O Salesforce tem vários tipos de contas com privilégios, incluindo modificar todos os dados, exibir todos os dados e gerenciar todos os usuários. Já que contas com privilégios como essas são um vetor de ataque preferencial para invasores, pois podem permitir que eles obtenham acesso substancial às configurações e informações corporativas, é útil exibir uma lista de contas privilegiadas. | Ir para o Salesforce. Clique na guia **Contas privilegiadas especiais**. |
| Gerenciamento de dados | Visão geral do compartilhamento de dados | Este relatório lista o número de arquivos armazenados nos aplicativos de nuvem, divididos de acordo com as permissões de acesso. O compartilhamento se tornou fácil com os aplicativos de nuvem devido à facilidade de acesso e onipresença. Um arquivo que não é compartilhado com ninguém, exceto seu proprietário, é chamado de arquivo particular. Se o arquivo for compartilhado, o Cloud App Security diferenciará entre quatro tipos de estados: <br> - Um arquivo da compartilhado publicamente (Web) pode ser acessado sem qualquer autenticação, até mesmo por um resultado de mecanismo de pesquisa.<br> - Um arquivo compartilhado publicamente é um arquivo que pode ser acessado sem qualquer autenticação usando um link.<br> - Um arquivo compartilhado externamente é um arquivo que pode ser acessado por pessoas fora da organização após se autenticarem no aplicativo de nuvem.<br> - Um arquivo compartilhado internamente é um arquivo que pode ser acessado por todos ou alguns dos usuários da sua organização.|Vá para **Arquivos**. No canto superior direito, clique nos três pontos e, em **Relatórios de gerenciamento de dados**, selecione **Visão geral do compartilhamento de dados**. |
| Gerenciamento de dados | Compartilhamento de saída por domínio | Este relatório lista os domínios com os quais os arquivos corporativos são compartilhados por seus funcionários. Para cada domínio, o relatório detalha quais usuários corporativos estão compartilhando arquivos com aquele domínio, quais arquivos são compartilhados e quais são os parceiros com quem os arquivos são compartilhados. É recomendável que você gerencie o compartilhamento com esses domínios por meio da guia Arquivos na página de cada aplicativo relevante. | Vá para **Arquivos**. No canto superior direito, clique nos três pontos e, em **Relatórios de gerenciamento de dados**, selecione **Compartilhamento de saída por domínio**. |
| Gerenciamento de dados | Proprietários de arquivos compartilhados | Isso lista os usuários que estão compartilhando arquivos corporativos com o mundo exterior. Os arquivos compartilhados externamente são compartilhados com parceiros externos específicos. Os arquivos compartilhados publicamente são acessíveis para todas as pessoas na Internet, por meio de um link particular, sendo que podem ser encontrados apenas por usuários que são explicitamente expostos ao link. Os arquivos compartilhados publicamente (Internet) podem ser acessados por qualquer pessoa na Internet, até mesmo por meio de um resultado de mecanismo de pesquisa. Se você encontrar usuários que compartilham uma quantidade excessiva de arquivos, investigue a natureza dessas permissões de compartilhamento excessivas usando a guia Arquivos e entre em contato com esses usuários para compreender melhor o uso do compartilhamento externo. | Vá para **Arquivos**. No canto superior direito, clique nos três pontos e, em **Relatórios de gerenciamento de dados**, selecione **Proprietários dos arquivos compartilhados**. |



  
## <a name="next-steps"></a>Próximas etapas 
[Controle](control.md)   

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
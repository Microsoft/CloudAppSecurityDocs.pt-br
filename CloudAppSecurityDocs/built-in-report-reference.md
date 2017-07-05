---
title: "Entender os campos nos relatórios internos do Cloud App Security | Microsoft Docs"
description: "Este tópico fornece uma lista de relatórios internos e seus usos."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/1/2017
ms.topic: article
ms.prod: 
ms.app: cloud-app-security
ms.technology: 
ms.assetid: 588b3639-f748-45a6-bc4b-a6ee47c1865e
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: d159cb95c9f0468e8c658c13586d07f0f20049ef
ms.sourcegitcommit: 2f4474084c7e07ac4853945ab5aa1ea78950675d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/28/2017
---
# <a name="built-in-report-reference"></a>Referência de relatório interno

O CAS fornece uma lista completa de relatórios internos prontos que permitem a obtenção de informações e o monitoramento de como as pessoas usam a nuvem. Você pode usar os filtros em cada relatório para personalizar o relatório e exportá-lo para sua conveniência.


A tabela a seguir fornece uma lista de relatórios internos e os tipos de eventos que talvez você queira usá-los para monitorar.  
  
## <a name="built-in-report-list"></a>Lista de relatórios internos  
  
|Tipo de relatório|Nome do relatório interno|Descrição|  
|-----------------|---------------------------|-----------------|  
|Segurança|Atividade por local|Este relatório lista os países dos quais a atividade foi originada em seus aplicativos de nuvem e diferentes parâmetros representando o volume de atividades de cada país, como o número de eventos, número de usuários etc. Use-o para obter uma visão geral da distribuição geográfica dos seus usuários.|  
|Segurança|Uso de navegador|Os ataques baseados em navegador estão entre os vetores de ataques mais comuns. Os fornecedores investem inúmeros recursos na proteção do software de navegação, criando um mecanismo de atualização eficaz para disseminar as atualizações aos pontos de extremidade. Usar navegadores preteridos muito tempo depois de sua atualização estar vencida os torna um alvo fácil para invasores usando kits de exploração disponíveis. Este relatório lista os navegadores desatualizados usados nos últimos sete dias por usuários para acessar seus aplicativos de nuvem. O relatório também permite saber se o uso de navegador desatualizado foi realizado por um robô.|  
|Segurança|Endereços IP ‑ contas com privilégios|Este relatório lista os endereços IP usados por dispositivos para executar atividades administrativas nos últimos 7 dias, em seu ambiente de nuvem protegido pelo Cloud App Security. O relatório é baseado em logs de auditoria acumulados pelo Cloud App Security. Os endereços IP são geralmente associados a uma localização geográfica e a uma organização de origem. Use esse relatório para identificar os endereços IP suspeitos se conectando aos seus aplicativos protegidos. Você pode exibir os logs de auditoria para cada endereço IP clicando nele.|  
|Gerenciamento de usuários|Contas inativas|Contas inativas são contas que têm acesso à sua instância de nuvem, mas não executaram nenhum evento durante os últimos 60 dias. Isso sugere que essas contas não estão mais ativas e devem ser suspensas para impedir o acesso futuro por invasores ou funcionários saindo da empresa. Seguir essa prática recomendada não apenas melhora sua postura de segurança, mas também reduz os custos operacionais.|  
|Gerenciamento de usuários|Usuários privilegiados|Este relatório lista os usuários com privilégios elevados nos aplicativos corporativos, como administradores, nos últimos sete dias. Contas com privilégios como essas são um vetor de ataque preferencial para invasores, uma vez que elas podem permitir que eles obtenham acesso substancial às informações corporativas e à configuração de rede. Se houver contas com privilégios que não foram usadas recentemente, isso poderá indicar uma falta de conscientização da segurança de TI nas empresas, potencialmente abrindo caminho para uma onda de violações de dados. Você pode investigar mais o uso de privilégios de usuário elevados por meio do Log de Auditoria e considerar revogar privilégios quando desnecessário.|  
|Gerenciamento de usuários|Contas privilegiadas especiais|O Salesforce tem vários tipos de contas com privilégios, incluindo Modificar todos os dados, Exibir todos os dados e Gerenciar todos os usuários. Contas com privilégios como essas são um vetor de ataque preferencial para invasores, uma vez que elas podem permitir que eles obtenham acesso substancial às configurações e informações corporativas.|  
|Gerenciamento de dados|Visão geral do compartilhamento de dados|Este relatório lista o número de arquivos armazenados nos aplicativos de nuvem, divididos de acordo com as permissões de acesso. O compartilhamento se tornou muito fácil com os aplicativos de nuvem devido à facilidade de acesso e onipresença.<br /><br /> Um arquivo que não é compartilhado com ninguém exceto seu proprietário é chamado de um arquivo particular. Se o arquivo for compartilhado, o Cloud App Security diferenciará entre quatro tipos de estados:<br /><br /> Um arquivo da compartilhado publicamente (Web) pode ser acessado sem qualquer autenticação, até mesmo por um resultado de mecanismo de pesquisa.<br /><br /> Um arquivo compartilhado publicamente é um arquivo que pode ser acessado sem qualquer autenticação usando um link.<br /><br /> Um arquivo compartilhado externamente é um arquivo que pode ser acessado por pessoas fora da organização após se autenticarem no aplicativo de nuvem.<br /><br /> Um arquivo compartilhado internamente é um arquivo que pode ser acessado por todos ou alguns dos usuários da sua organização.|  
|Gerenciamento de dados|Compartilhamento de saída por domínio|Este relatório lista os domínios com os quais os arquivos corporativos são compartilhados por seus funcionários. Para cada domínio, o relatório detalha quais usuários corporativos estão compartilhando arquivos com aquele domínio, quais arquivos são compartilhados e quais são os parceiros com quem os arquivos são compartilhados. É recomendável que você gerencie o compartilhamento com esses domínios por meio da guia Arquivos na página do aplicativo de cada aplicativo relevante.|  
|Gerenciamento de dados|Proprietários de arquivos compartilhados|Este relatório lista os usuários que estão compartilhando arquivos corporativos com o mundo exterior. Os arquivos compartilhados externamente são compartilhados com parceiros externos específicos. Os arquivos compartilhados publicamente são acessíveis para qualquer pessoa na Internet, por meio de um link privado, e podem ser localizados apenas por aqueles que são explicitamente expostos ao link. Os arquivos compartilhados publicamente (Internet) podem ser acessados por qualquer pessoa na Internet, até mesmo por meio de um resultado de mecanismo de pesquisa.  Se você encontrar usuários que compartilham uma quantidade excessiva de arquivos, será recomendável que você investigue a natureza dessas permissões de compartilhamento excessivas usando a guia Arquivos e entre em contato com esses usuários para compreender melhor o uso do compartilhamento externo.|  
  
## <a name="see-also"></a>Veja também  
[Controle](control.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
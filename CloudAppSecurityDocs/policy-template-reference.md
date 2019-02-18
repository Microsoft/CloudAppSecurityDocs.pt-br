---
title: Referência de modelo de política do Cloud App Security
description: Este artigo fornece informações sobre como as políticas são usadas e configuradas para controlar o uso de aplicativos na nuvem.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: barbkess
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: a6658937-57a2-484a-85cb-5a4cdbeeb002
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 77402ec7fa10eb9b91ee2822e5ebaf544b65b1dc
ms.sourcegitcommit: 8ef0438fa35916c48625ff750cb85e9628d202f2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56281807"
---
# <a name="policy-template-reference"></a>Referência de modelo de política

*Aplica-se a: Microsoft Cloud App Security*

Este artigo fornece informações sobre modelos de política incluídos no Microsoft Cloud App Security. 

## <a name="policy-templates"></a>Modelos de Política

É recomendável iniciar a criação de políticas com base em um modelo existente sempre que possível para facilidade de uso. Esta tabela apresenta modelos de política existentes no Microsoft Cloud App Security.

|Categoria de risco|Nome do modelo|Descrição|
|-----|----|----|
|Cloud Discovery|Comportamentos anormais em usuários descobertos|Alerta ao detectar comportamentos anormais em usuários e aplicativos descobertos, como: grandes quantidades de dados carregados em comparação com outros usuários, grandes transações de usuário em comparação com o histórico do usuário.|
|Cloud Discovery|Comportamentos anormais de endereços IP descobertos|Alertas ao detectar comportamentos anômalos em endereços IP e aplicativos descobertos, como: grandes quantidades de dados carregados em comparação com outros endereços IP, transações grandes de aplicativo em comparação com o histórico do endereço IP.|
|Cloud Discovery|Verificação de conformidade de aplicativo de colaboração|Alerta quando novos aplicativos de colaboração são descobertos que não tem conformidade com SOC2 e SSAE 16 e são usados por mais de 50 usuários com um uso diário total de mais de 50 MB.|
|Cloud Discovery|Verificação de conformidade de aplicativo de armazenamento em nuvem|Alerta quando novos aplicativos de armazenamento em nuvem são descobertos que não tem conformidade com SOC2, SSAE 16, ISAE 3402, PCI DSS e são usados por mais de 50 usuários com um uso diário total de mais de 50 MB.|
|Cloud Discovery|Verificação de conformidade do aplicativo CRM|Alerta quando novos aplicativos CRM são descobertos que não tem conformidade com SOC2, SSAE 16, ISAE 3402, HIPAA e ISO 27001 e são usados por mais de 50 usuários com um uso diário total de mais de 50 MB.|
|Cloud Discovery|Novo aplicativo de armazenamento em nuvem|Alerta quando novos aplicativos de armazenamento em nuvem são descobertos e que são usados por mais de 50 usuários com um uso diário total de mais de 50 MB.|
|Cloud Discovery|Novo aplicativo de hospedagem de código|Alerta quando novos aplicativos de hospedagem de código são descobertos e que são usados por mais de 50 usuários com um uso diário total de mais de 50 MB.|
|Cloud Discovery|Novo aplicativo de colaboração|Alerta quando novos aplicativos de colaboração são descobertos e que são usados por mais de 50 usuários com um uso diário total de mais de 50 MB.|
|Cloud Discovery|Novo aplicativo CRM|Alerta quando são descobertos novos aplicativos de CRM usados por mais de 50 usuários com um uso total diário de mais de 50 MB.|
|Cloud Discovery|Novo aplicativo de alto volume|Alerta quando novos aplicativos são descobertos que têm tráfego diário total de mais de 500 MB.|
|Cloud Discovery|Novo aplicativo do upload de alto volume|Alerta quando novos aplicativos são descobertos cujo tráfego de upload diário total é maior que 500 MB.|
|Cloud Discovery|Novo aplicativo de gerenciamento de recursos humanos|Alerta quando novos aplicativos de gerenciamento de recursos humanos são usados por mais de 50 usuários com um uso diário total de mais de 50 MB.|
|Cloud Discovery|Novo aplicativo de reunião online|Alerta quando novos aplicativos de reunião online são descobertos e que são usados por mais de 50 usuários com um uso diário total de mais de 50 MB.|
|Cloud Discovery|Novo aplicativo popular|Alerta quando novos aplicativos são descobertos e que são usados por mais de 500 usuários.|
|Cloud Discovery|Novo aplicativo com risco|Alerta quando novos aplicativos são descobertos com pontuação de risco menor do que 6 e que são usados por mais de 50 usuários com um uso diário total de mais de 50 MB.|
|Cloud Discovery|Novo aplicativo de vendas|Alerta quando novos aplicativos de vendas são descobertos e que são usados por mais de 50 usuários com um uso diário total de mais de 50 MB.|
|Cloud Discovery|Novos aplicativos do sistema de gerenciamento de fornecedor|Alerta quando novos aplicativos do sistema de gerenciamento de fornecedor são descobertos e que são usados por mais de 50 usuários com um uso diário total de mais de 50 MB.|
|DLP|Código-fonte compartilhado externamente|Alerta quando um arquivo que contém o código-fonte é compartilhado fora da sua organização.|
|DLP|Arquivo contendo PCI detectado na nuvem (mecanismo de DLP interno)|Alertar quando um arquivo contendo dados de informações de cartão de pagamento for detectado pelo mecanismo interno de DLP (prevenção contra perda de dados) do Microsoft Cloud App Security, em um dos aplicativos de nuvem sancionados.|
|DLP|Arquivo contendo PHI detectado na nuvem (mecanismo de DLP interno)|Alertar quando um arquivo com PHI (informações de saúde protegidas) for detectado pelo mecanismo DLP (prevenção contra perda de dados) integrado do Microsoft Cloud App Security em um aplicativo de nuvem sancionado.|
|DLP|Arquivo contendo informações de integridade protegidas detectado na nuvem (mecanismo interno de DLP)|Alertar quando um arquivo contendo dados pessoais é detectado pelo mecanismo DLP (prevenção contra perda de dados) integrado do Microsoft Cloud App Security em um aplicativo de nuvem sancionado.|
|Detecção de ameaças|Atividade administrativa de um endereço IP não corporativo|Alerta quando um usuário administrador executa uma atividade administrativa de um endereço IP que não está incluído na categoria de intervalo de endereços IP corporativos. Primeiro, configure os endereços IP corporativos; para fazer isso, vá até a página Configurações e defina **Intervalos de Endereços IP**.|
|Detecção de ameaças|Detecção geral de anomalias|Alerta quando uma sessão anômala é detectada em um dos aplicativos sancionados, como: viagem impossível, padrão de entrada, conta inativa.|
|Detecção de ameaças|Logon de um endereço IP com risco|Alerta quando um usuário entra em seus aplicativos sancionados de um endereço IP com risco. A categoria de endereço IP Arriscada contém, por padrão, endereços que têm marcas de endereço IP de proxy Anônimos, Tor ou Botnet. Você pode adicionar mais endereços IP para essa categoria na página de configurações de intervalos de endereço IP.|
|Detecção de ameaças|Download em massa por um único usuário|Alerta quando um usuário executa mais de 50 downloads dentro de 1 minutos.|
|Detecção de ameaças|Várias tentativas de logon do usuário com falha em um aplicativo|Alerta quando um único usuário tenta entrar em um aplicativo e falha de mais de 10 vezes em 5 minutos.|
|Detecção de ameaças|Atividade de ransomware potencial|Alerta quando um usuário carrega arquivos para a nuvem que podem ser infectados com ransomware.|
|Detecção de ameaças|Logon de usuário em um endereço IP não categorizado|Alerta quando um usuário faz logon de um endereço IP que não está incluído em uma categoria específica de intervalo de IP. Você pode categorizar os endereços IP indo para a página Configurações e selecionando os intervalos de endereços IP.|
|Controle de compartilhamento|Arquivo compartilhado com endereços de email pessoal|Alerta quando um arquivo é compartilhado com o endereço de email pessoal do usuário.|
|Controle de compartilhamento|Arquivo compartilhado com domínio não autorizado|Alertar quando um arquivo for compartilhado com um domínio não autorizado (por exemplo, de seu concorrente).|
|Controle de compartilhamento|Certificados digitais compartilhados (extensões de arquivo)|Alerta quando um arquivo que contém os certificados digitais publicamente é compartilhado. Use este modelo para gerenciar o armazenamento do AWS.|
|Controle de compartilhamento|Buckets do S3 acessíveis publicamente (AWS)|Alertar quando um bucket do S3 do AWS for compartilhado publicamente.|
|Controle de compartilhamento|Arquivos obsoletos compartilhados externamente|Localize arquivos compartilhados externamente que não foram abertos nem modificados por seis meses.|



## <a name="next-steps"></a>Próximas etapas 
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/)  
  

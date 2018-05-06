---
title: Referência de modelo de política no Cloud App Security | Microsoft Docs
description: Este tópico fornece informações sobre como as políticas são usadas e configuradas para controlar o uso de aplicativos de nuvem.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/22/2018
ms.topic: article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: a6658937-57a2-484a-85cb-5a4cdbeeb002
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 6dbfa26443bf1b05c689aec563b8ee71599076c9
ms.sourcegitcommit: 45311f2cafef79483e40d971a4c61c7673834d96
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2018
---
*Aplica-se ao: Microsoft Cloud App Security*


# <a name="policy-templates"></a>Modelos de Política

A seguir está uma lista de todos os modelos de política que existem no Microsoft Cloud App Security. É recomendável iniciar a criação de políticas com base em um modelo existente sempre que possível para facilidade de uso.

|Categoria de risco|Nome do modelo|Descrição|
|-----|----|----|
|Cloud Discovery|Comportamentos anormais em usuários descobertos|Alerta ao detectar comportamentos anormais em usuários e aplicativos descobertos, como: grandes quantidades de dados carregados em comparação com outros usuários, grandes transações de usuário em comparação com o histórico do usuário.|
|Cloud Discovery|Comportamentos anormais de endereços IP descobertos|Alertas ao detectar comportamentos anômalos em endereços IP e aplicativos descobertos, como: grandes quantidades de dados carregados em comparação com outros endereços IP, transações grandes de aplicativo em comparação com o histórico do endereço IP.|
|Cloud Discovery|Verificação de conformidade de aplicativo de colaboração|Alerta quando novos aplicativos de colaboração são descobertos que não tem conformidade com SOC2 e SSAE 16, e são usados por mais de 50 usuários com um uso diário total de mais de 50 MB.|
|Cloud Discovery|Verificação de conformidade de aplicativo de armazenamento em nuvem|Alerta quando novos aplicativos de armazenamento em nuvem são descobertos que não tem conformidade com SOC2, SSAE 16, ISAE 3402, PCI DSS e são usados por mais de 50 usuários com um uso diário total de mais de 50 MB.|
|Cloud Discovery|Verificação de conformidade do aplicativo CRM|Alerta quando novos aplicativos CRM são descobertos que não tem conformidade com SOC2, SSAE 16, ISAE 3402, HIPAA e ISO 27001 e são usados por mais de 50 usuários com um uso diário total de mais de 50 MB.|
|Cloud Discovery|Novo aplicativo de armazenamento em nuvem|Alerta quando novos aplicativos de armazenamento em nuvem são descobertos e que são usados por mais de 50 usuários com um uso diário total de mais de 50 MB.|
|Cloud Discovery|Novo aplicativo de hospedagem de código|Alerta quando novos aplicativos de hospedagem de código são descobertos e que são usados por mais de 50 usuários com um uso diário total de mais de 50 MB.|
|Cloud Discovery|Novo aplicativo de colaboração|Alerta quando novos aplicativos de colaboração são descobertos e que são usados por mais de 50 usuários com um uso diário total de mais de 50 MB.|
|Cloud Discovery|Novo aplicativo CRM|Alerta quando novos aplicativos CRM são descobertos e que são usados por mais de 50 usuários com um uso diário total de mais de 50 MB.|
|Cloud Discovery|Novo aplicativo de alto volume|Alerta quando novos aplicativos são descobertos que têm tráfego diário total de mais de 500 MB.|
|Cloud Discovery|Novo aplicativo do upload de alto volume|Alerta quando novos aplicativos são descobertos cujo tráfego de upload diário total é maior que 500 MB.|
|Cloud Discovery|Novo aplicativo de gerenciamento de recursos humanos|Alerta quando novos aplicativos de gerenciamento de recursos humanos são usados por mais de 50 usuários com um uso diário total de mais de 50 MB.|
|Cloud Discovery|Novo aplicativo de reunião online|Alerta quando novos aplicativos de reunião online são descobertos e que são usados por mais de 50 usuários com um uso diário total de mais de 50 MB.|
|Cloud Discovery|Novo aplicativo popular|Alerta quando novos aplicativos são descobertos e que são usados por mais de 500 usuários.|
|Cloud Discovery|Novo aplicativo com risco|Alerta quando novos aplicativos são descobertos com pontuação de risco menor do que 6 e que são usados por mais de 50 usuários com um uso diário total de mais de 50 MB.|
|Cloud Discovery|Novo aplicativo de vendas|Alerta quando novos aplicativos de vendas são descobertos e que são usados por mais de 50 usuários com um uso diário total de mais de 50 MB.|
|Cloud Discovery|Novos aplicativos do sistema de gerenciamento de fornecedor|Alerta quando novos aplicativos do sistema de gerenciamento de fornecedor são descobertos e que são usados por mais de 50 usuários com um uso diário total de mais de 50 MB.|
|DLP|Código-fonte compartilhado externamente|Alerta quando um arquivo que contém o código-fonte é compartilhado fora da sua organização.|
|DLP|Arquivo contendo PCI detectado na nuvem (mecanismo de DLP interno)|Alerta quando um arquivo que contém informações de cartão de pagamento (PCI) é detectado pelo nosso mecanismo interno de prevenção de perda de dados (DLP) em um aplicativo de nuvem sancionado.|
|DLP|Arquivo contendo PHI detectado na nuvem (mecanismo de DLP interno)|Alerta quando um arquivo que contém informações protegidas de saúde (PHI) é detectado pelo nosso mecanismo interno de prevenção de perda de dados (DLP) em um aplicativo de nuvem sancionado.|
|DLP|Arquivo contendo PII detectado na nuvem (mecanismo de DLP interno)|Alerta quando um arquivo que contém informações de identificação pessoal (PII) é detectado pelo nosso mecanismo interno de prevenção de perda de dados (DLP) em um aplicativo de nuvem sancionado.|
|Detecção de ameaças|Atividade administrativa de um endereço IP não corporativo|Alerta quando um usuário administrador executa uma atividade administrativa de um endereço IP que não está incluído na categoria de intervalo de endereços IP corporativos. Você deve primeiro configurar seus endereços IP corporativos indo para a página Configurações e definindo **Intervalos de endereços IP**.|
|Detecção de ameaças|Detecção geral de anomalias|Alerta quando uma sessão anômala é detectada em um dos aplicativos sancionados, tais como: viagem impossível, padrão logon, conta inativa.|
|Detecção de ameaças|Logon de um endereço IP com risco|Alerta quando um usuário faz logon em seus aplicativos sancionados de um endereço IP com risco. Por padrão, a categoria de endereço IP com risco contém endereços que têm marcas de endereço IP de proxy anônimo, TOR ou Botnet. Você pode adicionar mais endereços IP para essa categoria na página de configurações de intervalos de endereço IP.|
|Detecção de ameaças|Download em massa por um único usuário|Alerta quando um usuário executa mais de 50 downloads dentro de 1 minutos.|
|Detecção de ameaças|Logon do usuário com falha em várias tentativas para um aplicativo|Alerta quando um usuário tenta fazer logon em um aplicativo e falha de mais de 10 vezes em 5 minutos.|
|Detecção de ameaças|Atividade de ransomware potencial|Alerta quando um usuário carrega arquivos para a nuvem que podem ser infectados com ransomware.|
|Detecção de ameaças|Logon de usuário de um endereço IP não categorizado|Alerta quando um usuário faz logon de um endereço IP que não está incluído em uma categoria específica de intervalo de IP. Você pode categorizar os endereços IP indo para a página Configurações e selecionando os intervalos de endereços IP.|
|Controle de compartilhamento|Arquivo compartilhado com endereços de email pessoal|Alerta quando um arquivo é compartilhado com o endereço de email pessoal do usuário.|
|Controle de compartilhamento|Arquivo compartilhado com domínio não autorizado|Alerta quando um arquivo é compartilhado com um domínio não autorizado (tal como seu concorrente).|
|Controle de compartilhamento|Certificados digitais compartilhados (extensões de arquivo)|Alerta quando um arquivo que contém os certificados digitais publicamente é compartilhado.|
|Controle de compartilhamento|Arquivos obsoletos compartilhados externamente|Localizar arquivos compartilhados externamente que ainda não foram abertos ou modificados por 6 meses e removê-los da unidade de disco.|



## <a name="see-also"></a>Consulte Também  
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
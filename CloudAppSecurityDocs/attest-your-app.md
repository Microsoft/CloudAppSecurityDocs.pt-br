---
title: Atestar a seus aplicativos – o Cloud App Security | Microsoft Docs
description: Este artigo fornece instruções para atestar a seus aplicativos no Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: barbkess
ms.date: 04/29/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 3536c0a5-fa56-4931-9534-cc7cc4b4dfb0
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: e395e0ca1ee0fe0805a37e75a6201c6d9a224cdf
ms.sourcegitcommit: ea1c0f7638eaf0601ae476fea0d40e01bf8a6f4d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/20/2019
ms.locfileid: "67298870"
---
# <a name="attest-your-app"></a>Atestar seu aplicativo

Microsoft Cloud App Security permite que você atestar a seu aplicativo, para que você certifique-se de que a conformidade e os detalhes de segurança, que podemos usar para avaliar seu aplicativo em nosso catálogo de aplicativos de nuvem estão atualizados.

Se seu aplicativo já está listado no catálogo de aplicativos de nuvem, ou ele é novo, envie um questionário de Atestado Self. Para obter detalhes sobre o processo de Atestado Self e obter o questionário, entre em contato com casfeedback@microsoft.com.

Siga os atributos de serviço descritos abaixo para concluir com êxito o envio do questionário:

| Campo | Categoria de informações | Tipo | Valores aceitos | Descrição |
|------|-------|------|---------|----------|
| Nome do aplicativo | Geral | Cadeia de caracteres | Texto livre | O nome para seu aplicativo como ele deve aparecer no catálogo de aplicativos de nuvem. |
| Descrição | Geral | Cadeia de caracteres | Texto livre | Uma breve explicação do que seu aplicativo permite aos usuários fazer ou conseguir. |
| Category| Geral | Cadeia de caracteres | Fechar lista - fornecida no questionário | Classificação do aplicativo de acordo com o campo ao qual ele se relaciona. |
| Matriz | Geral | Código do país | Fechar lista - fornecida no questionário | O país da sede do provedor.|
| Data center| Geral | Matriz de código do país * | Fechar lista - fornecida no questionário (seleção múltipla) | O país em que reside seu data center (pode ser vários locais) |
| Empresa de hospedagem | Geral | Cadeia de caracteres | Texto livre | O nome da empresa que fornece hospedagem de servidor para o aplicativo. |
| Fundada | Geral | Inteiro | AAAA (não mais tarde do que de 2019) | O ano em que o provedor foi fundado. |
| Mantendo | Geral | Cadeia de caracteres | Privado, público | Exibe se o provedor é uma empresa pública ou privada |
| Domínio de aplicativo | Geral | Matriz de URL * | Texto livre | A lista de domínios que são usadas para interagir com o serviço (por exemplo, ' teams.microsoft.com' para o Microsoft Teams) |
| Termos de serviço | Geral | URL | Texto livre | Este aplicativo fornece um conjunto de regulamentos que os usuários devem concordar em seguir para usar o aplicativo? |
| política de privacidade | Geral | URL | Texto livre | Um link para vinculação legal documento relacionadas a como este provedor lida com informações de cliente de clientes ou funcionários coletadas como parte do aplicativo. |
| URL de logon | Geral | Matriz de URL * | Texto livre | A URL por meio dos usuários que fizerem logon no aplicativo. |
| Fornecedor | Geral | Cadeia de caracteres | Texto livre | O nome do fornecedor que disponibiliza este aplicativo. |
| Tipos de dados | Geral | Cadeia de caracteres | Fechar lista - fornecida no questionário | Quais tipos de dados podem ser carregados pelo usuário para o aplicativo?|
| Homepage | Geral | URL | Texto livre | URL da home page do provedor. |
| Última violação | Segurança | Date | MMM-dd-aaaa | Incidente mais recente em que dados sigilosos, protegidos ou confidenciais, propriedade do aplicativo foi exibidos, roubados ou usados por um indivíduo não autorizado a fazê-lo. |
| Método de criptografia de dados em repouso | Segurança | Cadeia de caracteres | Fechar lista - fornecida no questionário | O tipo de criptografia de dados em repouso realizado no aplicativo. |
| Autenticação Multifator | Segurança | Booliano | Verdadeiro, FALSO | Este aplicativo dá suporte a soluções de autenticação multifator? |
| Restrição de endereço IP | Segurança | Booliano | Verdadeiro, FALSO | Este aplicativo dá suporte à restrição de endereços IP específicos pelo aplicativo? |
| Trilha de auditoria de usuário | Segurança | Booliano | Verdadeiro, FALSO | Este aplicativo dá suporte à disponibilidade de trilha de auditoria por conta de usuário? |
| Trilha de auditoria de administrador | Segurança | Booliano | Verdadeiro, FALSO | Este aplicativo dá suporte à disponibilidade de uma trilha de auditoria de administrador no aplicativo? |
| Trilha de auditoria de dados | Segurança | Booliano | Verdadeiro, FALSO | Este aplicativo dá suporte à disponibilidade de uma trilha de auditoria de dados no aplicativo? |
| Usuário pode carregar dados | Segurança | Booliano | Verdadeiro, FALSO | Dados de usuário carregado de suporte esse aplicativo? |
| Classificação de dados | Segurança | Booliano | Verdadeiro, FALSO | Este aplicativo habilita a opção para a classificação dos dados carregados para o aplicativo? |
| Lembrar senha | Segurança | Booliano | Verdadeiro, FALSO | Este aplicativo habilita a opção para lembrar e salvar senhas de usuário no aplicativo? |
| Suporte a funções de usuário | Segurança | Booliano | Verdadeiro, FALSO | Este aplicativo dá suporte à distribuição de usuários por funções e níveis de permissão? |
| Compartilhamento de arquivos | Segurança | Booliano | Verdadeiro, FALSO | Este aplicativo inclui recursos que permitem o compartilhamento de arquivos entre os usuários? |
| Nome do certificado válido | Segurança | Booliano | Verdadeiro, FALSO | O servidor fornece um certificado SSL correspondente ao nome de domínio? |
| Certificado confiável | Segurança | Booliano | Verdadeiro, FALSO | O servidor fornece um certificado SSL confiável (cadeia de assinatura não expirado, verificado e confiável, etc.)? |
| Protocolo de criptografia | Segurança | Cadeia de caracteres | Fechar lista - fornecida no questionário | A última versão do protocolo de criptografia de segurança de camada de transporte (TLS) tem suportada entre o provedor de ponto de extremidade e o aplicativo do usuário. Se o certificado do servidor for inexistente ou não é válido, a criptografia será considerada sem suporte.|
| Com correções para Heartbleed | Segurança | Booliano | Verdadeiro, FALSO | É a implementação de SSL do servidor para o bug Heartbleed para reduzir a vulnerabilidade? |
| Cabeçalhos de segurança HTTP: Segurança de transporte estrito | Segurança | Booliano | Verdadeiro, FALSO | HTTP Strict-Transport-Security os cabeçalhos é implementados pelo aplicativo em seu site? |
| Cabeçalhos de segurança HTTP: Content-Security-Policy | Segurança | Booliano | Verdadeiro, FALSO | HTTP Content-Security-Policy os cabeçalhos é implementados pelo aplicativo em seu site? |
| Cabeçalhos de segurança HTTP: X-Frame-Options | Segurança | Booliano | Verdadeiro, FALSO | Cabeçalhos HTTP X-Frame-Options são implementados pelo aplicativo em seu site? |
| Cabeçalhos de segurança HTTP: X-Content-Type-Options | Segurança | Booliano | Verdadeiro, FALSO | Cabeçalhos HTTP X-Content-Type-Options são implementados pelo aplicativo em seu site? |
| Cabeçalhos de segurança HTTP: X-XSS-Protection | Segurança | Booliano | Verdadeiro, FALSO | HTTP X-XSS-Protection os cabeçalhos é implementados pelo aplicativo em seu site? |
| Dá suporte a SAML | Segurança | Booliano | Verdadeiro, FALSO | Esse aplicativo oferece suporte ao padrão SAML para troca de dados de autenticação e autorização? |
| Protegido contra DROWN | Segurança | Booliano | Verdadeiro, FALSO | Os servidores de aplicativos estão protegidos contra ataques DROWN? |
| Os testes de penetração | Segurança | Booliano | Verdadeiro, FALSO | Este aplicativo realiza teste de penetração para detectar e avaliar vulnerabilidades de rede? |
| Requer autenticação de usuário | Segurança | Booliano | Verdadeiro, FALSO | Este aplicativo requer autenticação e permite o uso anônimo? |
| Política de senha: Limite de comprimento de senha | Segurança | Booliano | Verdadeiro, FALSO | Este aplicativo impõe um limite de comprimento na criação de senha? |
| Política de senha: Combinação de caracteres | Segurança | Booliano | Verdadeiro, FALSO | Este aplicativo impõe uma combinação de caracteres na criação de senha? |
| Política de senha: Período de alteração de senha | Segurança | Booliano | Verdadeiro, FALSO | Este aplicativo impõe que os usuários para redefinir sua senha periodicamente? |
| Política de senha: Reutilização e histórico de senha | Segurança | Booliano | Verdadeiro, FALSO | Este aplicativo não permitir a reutilização de senhas antigas? |
| Política de senha: Uso de informações pessoais | Segurança | Booliano | Verdadeiro, FALSO | Este aplicativo não permitir o uso de informações pessoais em senhas? |
| política de senha | Segurança | Booliano | Verdadeiro, FALSO | Este aplicativo impõe uma política de senha está em conformidade com as práticas recomendadas? |
| FINRA | Conformidade | Booliano | Verdadeiro, FALSO, n/d | Este aplicativo está em conformidade com o FINRA, um conjunto padrão para organizações não fins lucrativos autorizado pelo Congresso que regula e impõe o aprimoramento de garantias de investidores e integridade do mercado? |
| FISMA | Conformidade | Booliano | Verdadeiro, FALSO, n/d | Este aplicativo está em conformidade com o FISMA, a legislação dos EUA que define uma estrutura abrangente para proteger as informações do governo, operações e ativos em órgãos federais contra ameaças? |
| GAAP | Conformidade | Booliano | Verdadeiro, FALSO, n/d | Este aplicativo está em conformidade com o GAAP, um conjunto de regras de contabilidade normalmente seguidas e padrões para relatórios financeiros? |
| HIPAA | Conformidade | Booliano | Verdadeiro, FALSO, n/d | Este aplicativo está em conformidade com HIPAA, a legislação dos EUA que define padrões para proteger a confidencialidade e a segurança das informações de saúde individualmente identificáveis? |
| ISAE 3402 | Conformidade | Booliano | Verdadeiro, FALSO, n/d | Este aplicativo está em conformidade com o ISAE 3402, a norma global que fornece garantia de que uma organização de serviço tem os controles adequados em vigor? |
| ISO 27001 | Conformidade | Booliano | Verdadeiro, FALSO, n/d | É esse aplicativo a certificação ISO 27001, um certificado concedido a empresas que cumprem reconhecidas internacionalmente diretrizes e princípios gerais para iniciar, implementar, manter e aprimorar o gerenciamento de segurança de informações dentro de uma organização? |
| ITAR | Conformidade | Booliano | Verdadeiro, FALSO, n/d | Este aplicativo é compatível com o ITAR, regulamentos que controlam a exportação e importação de artigos relacionados à defesa e serviços encontrados na lista de Munições dos? |
| SOC 1 | Conformidade | Booliano | Verdadeiro, FALSO, n/d | Este aplicativo está em conformidade com SOC 1, relatando os controles em uma organização de serviço que são relevantes para o controle de entidades de usuário interno através de relatórios financeiros? |
| SOC 2 | Conformidade | Booliano | Verdadeiro, FALSO, n/d | Este aplicativo está em conformidade com SOC 2, gerar relatórios sobre o processamento não financeiro com base em um ou mais dos critérios de serviços a confiança em segurança, privacidade, disponibilidade, confidencialidade e integridade de processamento? |
| SOC 3 | Conformidade | Booliano | Verdadeiro, FALSO, n/d | Este aplicativo está em conformidade com SOC 3, relatando com base em critérios de serviço a relação de confiança, que podem ser distribuídos livremente e contêm apenas a declaração do gerenciamento de que cumpriu os requisitos dos critérios escolhidos? |
| SOX | Conformidade | Booliano | Verdadeiro, FALSO, n/d | Este aplicativo está em conformidade com o SOX, legislação dos EUA visa proteger acionistas e o público em geral contra fraudes e erros contábeis, bem como melhorar a precisão das divulgações corporativas? |
| SP 800-53 | Conformidade | Booliano | Verdadeiro, FALSO, n/d | Este aplicativo está em conformidade com o SP80053, controles de segurança para sistemas de informação federal e organizações recomendados? |
| SSAE 16 | Conformidade | Booliano | Verdadeiro, FALSO, n/d | Este aplicativo está em conformidade com a norma SSAE 16 para auditar os controles de conformidade interna da organização de serviços e processos de relatórios? |
| Versão do PCI DSS | Conformidade | Cadeia de caracteres | 1, 2, 3, 3.1, 3.2, N/A | A versão do protocolo PCI-DSS compatível com este serviço. |
| ISO 27018 | Conformidade | Booliano | Verdadeiro, FALSO, n/d | Este aplicativo está em conformidade com ISO 27018, que estabelece comumente aceitos controles e diretrizes para processar e proteger informações pessoalmente identificáveis (PII) em um público ambiente de computação em nuvem? |
| GLBA | Conformidade | Booliano | Verdadeiro, FALSO, n/d | Este aplicativo está em conformidade com o Gramm-Leach-Bliley Act (GLBA), que exige que as instituições financeiras para estabelecer padrões para proteger a segurança e a confidencialidade das informações pessoais de clientes? |
| Nível de FedRAMP | Conformidade | Cadeia de caracteres | Alto, moderado, baixo, n/d | O nível da solução compatível com FedRAMP fornecido por este aplicativo. |
| Nível do CSA STAR | Conformidade | Cadeia de caracteres | Autoavaliação, certificação, Atestado, avaliação C-STAR, monitoramento contínuo, n/d | O nível do programa CSA STAR no qual o aplicativo é certificado |
| Privacy Shield | Conformidade | Booliano | Verdadeiro, FALSO, n/d | Este aplicativo está em conformidade com a estrutura de escudo de privacidade da UE-EUA, que impõe obrigações mais em empresas norte-americanas para proteger dados pessoais dos europeus? |
| ISO 27017 | Conformidade | Booliano | Verdadeiro, FALSO, n/d | Este aplicativo está em conformidade com ISO 27017, que estabelece controles normalmente aceitos e diretrizes para processar e proteger as informações do usuário em um ambiente de computação em nuvem pública? |
| COBIT | Conformidade | Booliano | Verdadeiro, FALSO, n/d | Este aplicativo está em conformidade com COBIT, que define as práticas recomendadas para a governança e controle de sistemas de informação e tecnologia e alinha os princípios de negócios à equipe de TI? |
| COPPA | Conformidade | Booliano | Verdadeiro, FALSO, n/d | Este aplicativo está em conformidade com o COPPA, que define os requisitos de site e os operadores de serviços online que fornecem conteúdo aos filhos menos de 13 anos de idade? |
| FERPA | Conformidade | Booliano | Verdadeiro, FALSO, n/d | Este aplicativo está em conformidade com a FERPA, uma lei federal que protege a privacidade dos registros educacionais de alunos? |
| GAPP | Conformidade | Booliano | Verdadeiro, FALSO, n/d | Este aplicativo está em conformidade com GAPP, uma coleção de regras normalmente seguidas que abordam os riscos de privacidade em uma organização? |
| HITRUST CSF | Conformidade | Booliano | Verdadeiro, FALSO, n/d | Este aplicativo está em conformidade com CSF HITRUST, um conjunto de controles que harmonizes os requisitos de normas de segurança de informações e padrões? |
| Jericho fórum mandamentos | Conformidade | Booliano | Verdadeiro, FALSO, n/d | Este aplicativo siga Jericho fórum mandamentos, um conjunto de se proteger de princípios a serem observadas ao arquitetar sistemas para a operação em ambientes de desprovisionamento perimeterized? |
| ISO 27002 | Conformidade | Booliano | Verdadeiro, FALSO, n/d | Este aplicativo está em conformidade com ISO 27002, que estabelece diretrizes comuns para os padrões de segurança de informações organizacionais e práticas de gerenciamento de segurança de informações? |
| FFIEC | Conformidade | Booliano | Verdadeiro, FALSO, n/d | Este aplicativo está em conformidade com as diretrizes do Federal financeiros instituições exame do conselho sobre os controles de gerenciamento de risco necessários para autenticar os serviços em um ambiente de serviços bancários Internet? |
| Propriedade dos dados | Legal | Booliano | Verdadeiro, FALSO | Este aplicativo totalmente preservar a posse do usuário de dados carregados? |
| DMCA | Legal | Booliano | Verdadeiro, FALSO | Este aplicativo está em conformidade com o Digital Millennium Copyright Act (DMCA), que criminaliza qualquer tentativa de acessar ilegalmente material protegido por direitos autorais? |
| Política de retenção de dados | Legal | Booliano | Verdadeiro, FALSO | O que é a política do aplicativo para a retenção de dados do usuário após o encerramento da conta? |
| Instrução de prontidão para GDPR | Legal | URL | Texto livre | Um link para seu site, quando relevante, que explica como o fornecedor planeja lidar com a conformidade com GDPR. |
| GDPR - direita para eliminação | Legal | Booliano | Verdadeiro, FALSO, n/d | Este aplicativo parar o processamento e excluir dados pessoais de um indivíduo mediante solicitação? |
| GDPR - violações de dados de relatório | Legal | Booliano | Verdadeiro, FALSO, n/d | É essa violações de dados de relatório de aplicativo para autoridades de supervisão e pessoas afetadas por violação, dentro de 72 horas de detecção de violação de? |
| GDPR – avaliação de impacto | Legal | Booliano | Verdadeiro, FALSO, n/d | Este aplicativo conduzir avaliações de impacto de proteção de dados para identificar os riscos para pessoas físicas? |
| GDPR - controle de seguro transfronteiriça de dados | Legal | Booliano | Verdadeiro, FALSO, n/d | Esse aplicativo transferir dados com segurança entre as fronteiras? |
| GDPR - diretor de proteção de dados | Legal | Booliano | Verdadeiro, FALSO, n/d | Esse aplicativo designa um dados diretor de proteção para supervisionar a estratégia de segurança de dados e a conformidade com GDPR? |
| GDPR - direita para objeto | Legal | Booliano | Verdadeiro, FALSO, n/d | Este aplicativo fornece aos indivíduos com a capacidade de objeto para o processamento de seus dados pessoais em determinadas circunstâncias? |
| GDPR - o direito de acesso | Legal | Booliano | Verdadeiro, FALSO, n/d | Este aplicativo fornece aos indivíduos com a capacidade de saber, mediante solicitação, quais dados pessoais, uma empresa está usando e como ele está sendo usado? |
| GDPR - direita para dados Portablility | Legal | Booliano | Verdadeiro, FALSO, n/d | Este aplicativo fornece aos indivíduos com a capacidade de obter e reutilizar seus dados pessoais para suas próprias finalidades em diferentes serviços mediante solicitação? |
| GDPR - direito para ser informado | Legal | Booliano | Verdadeiro, FALSO, n/d | Este aplicativo informar indivíduos as garantias apropriado necessário quando os dados pessoais são transferidos para um país não ou para uma organização internacional? |
| GDPR - direita para a restrição de processamento | Legal | Booliano | Verdadeiro, FALSO, n/d | Este aplicativo fornece aos indivíduos com a capacidade de bloquear ou suprimir o processamento de dados pessoais? |
| GDPR - direitos relacionados a tomada de decisões automatizada | Legal | Booliano | Verdadeiro, FALSO, n/d | Este aplicativo fornece aos indivíduos com a capacidade de optar por não estar sujeito a uma decisão com base unicamente no processamento automatizado? Isso inclui a criação de perfil, que pode ter implicações legais. |
| GDPR - base legal para processamento | Legal | Booliano | Verdadeiro, FALSO, n/d | Este aplicativo processar dados pessoais legalmente de acordo com consentimento, contrato, obrigação legal, interesses vitais, interesses legítimos, categoria especial, dados e dados de crime? |
| GDPR - direita para retificação | Legal | Booliano | Verdadeiro, FALSO, n/d | Este aplicativo fornece aos indivíduos com a capacidade de corrigir seus dados pessoais? O controlador deve responder a todas as solicitações de suas entidades de dados dentro de um mês. |


\* Campos do tipo *matriz* devem ser separados por ponto e vírgula (;).

## <a name="next-steps"></a>Próximas etapas 
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/) 


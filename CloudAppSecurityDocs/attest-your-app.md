---
title: Atestar seus aplicativos
description: Este artigo fornece instruções para atestar seus aplicativos no Cloud App Security.
ms.date: 01/30/2020
ms.topic: conceptual
ms.openlocfilehash: 3c2c1b392bdd4f1640b76c80ce227ad9379f4902
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96313739"
---
# <a name="attest-your-app"></a>Atestar seu aplicativo

Microsoft Cloud App Security permite que você atestar seu aplicativo, para que você tenha certeza de que os detalhes de conformidade e segurança que usamos para classificar seu aplicativo em nosso catálogo de aplicativos de nuvem estão atualizados.

Se seu aplicativo já estiver listado no catálogo de aplicativos de nuvem ou se for novo, envie um [questionário de autoatestado](https://go.microsoft.com/fwlink/?linkid=2106624). Para obter detalhes sobre o processo de autoatestado, contate casfeedback@microsoft.com .

Siga os atributos de serviço descritos abaixo para concluir com êxito o envio do questionário:

| Campo | Categoria de informações | Type | Valores aceitos | Descrição |
|------|-------|------|---------|----------|
| Nome do aplicativo | Geral | String | Texto livre | O nome do seu aplicativo como deve aparecer no catálogo de aplicativos de nuvem. |
| Descrição | Geral | String | Texto livre | Breve explicação do que seu aplicativo permite que os usuários façam ou alcancem. |
| Categoria| Geral | String | Fechar lista – fornecido no questionário | Classificação do aplicativo de acordo com o campo ao qual ele se relaciona. |
| Matriz | Geral | Código do país | Fechar lista – fornecido no questionário | O país/região da sede do provedor.|
| Data center| Geral | Matriz de códigos do país * | Fechar lista – fornecida no questionário (seleção múltipla) | O país/região no qual o data center reside (pode ser vários locais) |
| Empresa de hospedagem | Geral | String | Texto livre | O nome da empresa que fornece Hospedagem de servidor para o aplicativo. |
| Fundada | Geral | Integer | AAAA (não depois de 2019) | O ano em que o provedor foi fundado. |
| Holding | Geral | String | Privado, público | Exibe se o provedor é uma empresa pública ou privada |
| Domínio do aplicativo | Geral | Matriz de URL * | Texto livre | A lista de domínios específicos que são usados para interagir com o serviço. Por exemplo, ' teams.microsoft.com ' para Microsoft Teams e não o domínio genérico ' microsoft.com '. |
| Termos de serviço | Geral | URL | Texto livre | Este aplicativo fornece um conjunto de regulamentos que os usuários devem concordar em seguir para usar o aplicativo? |
| Política de privacidade | Geral | URL | Texto livre | Um link para um documento de associação legal relacionado a como esse provedor lida com informações de cliente, cliente ou funcionário coletadas como parte do aplicativo. |
| URL de logon | Geral | Matriz de URL * | Texto livre | A URL por meio da qual os usuários fazem logon no aplicativo. |
| Fornecedor | Geral | String | Texto livre | O nome do fornecedor que fornece este aplicativo. |
| Tipos de dados | Geral | String | Fechar lista – fornecido no questionário | Quais tipos de dados podem ser carregados pelo usuário para o aplicativo?|
| Home page | Geral | URL | Texto livre | A URL de home page do provedor. |
| Plano de recuperação de desastre | Geral | Boolean | Verdadeiro, Falso | Este aplicativo tem um plano de recuperação de desastres que inclui uma estratégia de backup e restauração? |
| Violação mais recente | Segurança | Data | MMM-dd-aaaa | O incidente mais recente em que dados confidenciais, protegidos ou confidenciais pertencentes ao aplicativo foram exibidos, roubados ou usados por um indivíduo não autorizado para fazer isso. |
| Método de criptografia de dados em repouso | Segurança | String | Fechar lista – fornecido no questionário | O tipo de criptografia de dados em repouso executado no aplicativo. |
| Autenticação multifator | Segurança | Boolean | Verdadeiro, Falso | Este aplicativo dá suporte a soluções de autenticação multifator? |
| Restrição de endereço IP | Segurança | Boolean | Verdadeiro, Falso | Este aplicativo dá suporte à restrição de endereços IP específicos pelo aplicativo? |
| Trilha de auditoria do usuário | Segurança | Boolean | Verdadeiro, Falso | Este aplicativo dá suporte à disponibilidade da trilha de auditoria por conta de usuário? |
| Trilha de auditoria de administrador | Segurança | Boolean | Verdadeiro, Falso | Este aplicativo dá suporte à disponibilidade de uma trilha de auditoria de administrador no aplicativo? |
| Trilha de auditoria de dados | Segurança | Boolean | Verdadeiro, Falso | Este aplicativo dá suporte à disponibilidade de uma trilha de auditoria de dados no aplicativo? |
| O usuário pode carregar dados | Segurança | Boolean | Verdadeiro, Falso | Este aplicativo dá suporte a dados carregados pelo usuário? |
| Classificação de dados | Segurança | Boolean | Verdadeiro, Falso | Este aplicativo habilita a opção de classificação dos dados carregados para o aplicativo? |
| Lembrar senha | Segurança | Boolean | Verdadeiro, Falso | Este aplicativo habilita a opção para lembrar e salvar senhas de usuário no aplicativo? |
| Suporte a funções de usuário | Segurança | Boolean | Verdadeiro, Falso | Este aplicativo dá suporte à distribuição de usuários por funções e níveis de permissão? |
| Compartilhamento de arquivos | Segurança | Boolean | Verdadeiro, Falso | Este aplicativo inclui recursos que permitem o compartilhamento de arquivos entre usuários? |
| Oferece suporte a SAML | Segurança | Boolean | Verdadeiro, Falso | Este aplicativo dá suporte ao padrão SAML para a troca de dados de autenticação e autorização? |
| Protegido contra AFOGAdo | Segurança | Boolean | Verdadeiro, Falso | Os servidores de aplicativos estão protegidos contra ataques de afoga? |
| Teste de penetração | Segurança | Boolean | Verdadeiro, Falso | Este aplicativo executa testes de penetração para detectar e avaliar vulnerabilidades de rede? |
| Requer autenticação do usuário | Segurança | Boolean | Verdadeiro, Falso | Este aplicativo requer autenticação e não permite o uso anônimo? |
| Política de senha: limite de comprimento da senha | Segurança | Boolean | Verdadeiro, Falso | Este aplicativo impõe um limite de comprimento para a criação de senha? |
| Política de senha: combinação de caracteres | Segurança | Boolean | Verdadeiro, Falso | Este aplicativo impõe uma combinação de caracteres na criação de senha? |
| Política de senha: alterar o período da senha | Segurança | Boolean | Verdadeiro, Falso | Este aplicativo impõe que os usuários redefinam sua senha periodicamente? |
| Política de senha: histórico e reutilização de senha | Segurança | Boolean | Verdadeiro, Falso | Este aplicativo não permite a reutilização de senhas antigas? |
| Política de senha: uso de informações pessoais | Segurança | Boolean | Verdadeiro, Falso | Este aplicativo não permite o uso de informações pessoais em senhas? |
| Política de senha | Segurança | Boolean | Verdadeiro, Falso | Este aplicativo impõe uma política de senha que está em conformidade com as práticas recomendadas? |
| FINRA | Conformidade | Boolean | True, false, N/A | Este aplicativo está em conformidade com o FINRA, um conjunto padrão para organizações sem fins lucrativos autorizado pelo Congresso que regula e impõe o aprimoramento de garantias de investidores e integridade do mercado? |
| FISMA | Conformidade | Boolean | True, false, N/A | Este aplicativo está em conformidade com a FISMA, a legislação dos EUA que define uma estrutura abrangente para proteger informações governamentais, operações e ativos dentro das agências federais, contra ameaças? |
| GAAP | Conformidade | Boolean | True, false, N/A | Este aplicativo está em conformidade com o GAAP, uma coleção de padrões e regras de contabilidade mais bem visitadas para relatórios financeiros? |
| HIPAA | Conformidade | Boolean | True, false, N/A | Este aplicativo está em conformidade com a HIPAA, a legislação dos EUA que define os padrões para proteger a confidencialidade e a segurança de informações de integridade de identificação individual? |
| ISAE 3402 | Conformidade | Boolean | True, false, N/A | Este aplicativo está em conformidade com o ISAE 3402, o padrão global, fornecendo à garantia que uma organização de serviço tem os controles adequados em vigor? |
| ISO 27001 | Conformidade | Boolean | Verdadeiro, Falso | Este aplicativo ISO 27001 certificadou, um certificado fornecido para empresas que mantêm diretrizes reconhecidas internacionalmente e princípios gerais para iniciar, implementar, manter e melhorar o gerenciamento da segurança de informações em uma organização? |
| ITAR | Conformidade | Boolean | True, false, N/A | Este aplicativo está em conformidade com ITAR, regulamentos que controlam a exportação e a importação de artigos e serviços relacionados à defesa encontrados na lista de munições dos EUA? |
| SOC 1 | Conformidade | Boolean | True, false, N/A | Este aplicativo está em conformidade com o SOC 1, relatando controles em uma organização de serviço que são relevantes para o controle interno das entidades de usuário sobre relatórios financeiros? |
| SOC 2 | Conformidade | Boolean | Verdadeiro, Falso | Este aplicativo está em conformidade com o SOC 2, relatando o processamento não financeiro com base em um ou mais dos critérios de serviço de confiança sobre segurança, privacidade, disponibilidade, confidencialidade e integridade de processamento? |
| SOC 3 | Conformidade | Boolean | Verdadeiro, Falso | Este aplicativo está em conformidade com o SOC 3, relatando com base nos critérios do serviço de confiança, que podem ser distribuídos livremente e contêm apenas a asserção do gerenciamento de que eles atenderam aos requisitos dos critérios escolhidos? |
| SOX | Conformidade | Boolean | True, false, N/A | Este aplicativo está em conformidade com SOX, legislação dos EUA destinado à proteção de acionistas e ao público geral de erros e fraudes de contabilidade, além de melhorar a precisão das divulgações corporativas? |
| SP 800-53 | Conformidade | Boolean | Verdadeiro, Falso | Este aplicativo está em conformidade com o SP80053, os controles de segurança recomendados para organizações e sistemas de informações federais? |
| SSAE 16 | Conformidade | Boolean | True, false, N/A | Este aplicativo está em conformidade com o padrão SSAE 16 para auditar os controles de conformidade internos da organização de serviços e os processos de relatório? |
| Versão do PCI DSS | Conformidade | String | 1, 2, 3, 3,1, 3,2, N/A | A versão do protocolo PCI-DSS com suporte por este aplicativo. |
| ISO 27018 | Conformidade | Boolean | True, false, N/A | Este aplicativo está em conformidade com o ISO 27018, que estabelece controles e diretrizes comumente aceitos para processar e proteger informações de identificação pessoal (PII) em um ambiente de computação em nuvem pública? |
| GLBA | Conformidade | Boolean | True, false, N/A | Este aplicativo está em conformidade com a lei Gramm-Leach-Bliley (GLBA), que exige que as instituições financeiras estabeleçam padrões para proteger a segurança e a confidencialidade das informações pessoais dos clientes? |
| Nível de FedRAMP | Conformidade | String | Alta, moderada, baixa Li-SaaS | O nível da solução compatível com FedRAMP fornecida por este aplicativo. |
| Nível do CSA STAR | Conformidade | String | Autoavaliação, certificação, atestado, avaliação C-STAR, monitoramento contínuo | O nível do programa CSA STAR no qual o aplicativo é certificado |
| Defesa de Privacidade | Conformidade | Boolean | True, false, N/A | Este aplicativo está em conformidade com a estrutura do Privacy Shield da UE-US, que impõe obrigações mais fortes em empresas dos EUA para proteger os dados pessoais do Europeans? |
| ISO 27017 | Conformidade | Boolean | Verdadeiro, Falso | Este aplicativo está em conformidade com o ISO 27017, que estabelece controles e diretrizes comumente aceitos para processar e proteger as informações do usuário em um ambiente de computação em nuvem pública? |
| COBIT | Conformidade | Boolean | Verdadeiro, Falso | Este aplicativo está em conformidade com o COBIT, que define as práticas recomendadas para governança e controle de sistemas de informações e tecnologia, além de alinhá-los com os princípios de negócios? |
| COPPA | Conformidade | Boolean | True, false, N/A | Este aplicativo está em conformidade com o COPPA, que define os requisitos do site e dos operadores de serviços online que fornecem conteúdo a crianças menos de 13 anos de idade? |
| FERPA | Conformidade | Boolean | True, false, N/A | Este aplicativo está em conformidade com o FERPA, uma lei federal que protege a privacidade dos registros educativos dos alunos? |
| GAPP | Conformidade | Boolean | True, false, N/A | Este aplicativo está em conformidade com o GAPP, uma coleção de regras normalmente seguidas que abordam os riscos de privacidade em uma organização? |
| HITRUST CSF | Conformidade | Boolean | True, false, N/A | Este aplicativo está em conformidade com o HITRUST CSF, um conjunto de controles que harmoniza os requisitos das normas e dos padrões de segurança de informações? |
| Comandos do fórum do Jericho | Conformidade | Boolean | Verdadeiro, Falso | Este aplicativo segue os comandos do fórum Jericho, um conjunto de princípios a serem observados ao arquitetar sistemas para operação segura em ambientes de desativação? |
| ISO 27002 | Conformidade | Boolean | True, false, N/A | Este aplicativo está em conformidade com o ISO 27002, que estabelece diretrizes comuns para padrões de segurança de informações organizacionais e práticas de gerenciamento de segurança de informações? |
| FFIEC | Conformidade | Boolean | True, false, N/A | Este aplicativo está em conformidade com as diretrizes do Conselho de exame de instituições financeiras federais sobre os controles de gerenciamento de riscos necessários para autenticar serviços em um ambiente de Internet Banking? |
| Propriedade dos dados | Ofício | Boolean | Verdadeiro, Falso | Este aplicativo preserva totalmente a propriedade do usuário dos dados carregados? |
| DMCA | Ofício | Boolean | Verdadeiro, Falso | Este aplicativo está em conformidade com o Digital Millennium Copyright Act (DMCA), que criminaliza qualquer tentativa de acessar ilegalmente o material protegido por direitos autorais? |
| Política de retenção de dados | Ofício | Boolean | Verdadeiro, Falso | Qual é a política do aplicativo para a retenção de dados do usuário após o encerramento da conta? |
| Instrução de preparação de GDPR | Ofício | URL | Texto livre | Um link para seu site, quando relevante, relacionando como esse provedor planeja lidar com a conformidade do GDPR. |
| GDPR-direito de eliminação | Ofício | Boolean | True, false, N/A | Este aplicativo interrompe o processamento e exclui os dados pessoais de um indivíduo mediante solicitação? |
| GDPR-violações de dados de relatório | Ofício | Boolean | True, false, N/A | Este aplicativo relata violações de dados para autoridades de supervisão e indivíduos afetados pela violação, dentro de 72 horas de detecção de violação? |
| GDPR-avaliação de impacto | Ofício | Boolean | True, false, N/A | Este aplicativo realiza avaliações de impacto na proteção de dados para identificar o risco aos indivíduos? |
| GDPR-controle de dados de borda cruzada seguro | Ofício | Boolean | True, false, N/A | Este aplicativo transfere dados com segurança entre bordas? |
| GDPR – responsável pela proteção de dados | Ofício | Boolean | True, false, N/A | Este aplicativo indica um responsável pela proteção de dados para supervisionar a estratégia de segurança de dados e a conformidade GDPR? |
| GDPR-direito de objeto | Ofício | Boolean | True, false, N/A | Este aplicativo fornece aos indivíduos a capacidade de objeto para o processamento de seus dados pessoais em determinadas circunstâncias? |
| GDPR-direito de acesso | Ofício | Boolean | True, false, N/A | Esse aplicativo fornece aos indivíduos a capacidade de saber, mediante solicitação, quais dados pessoais uma empresa está usando e como ele está sendo usado? |
| GDPR-direito de Portablility de dados | Ofício | Boolean | True, false, N/A | Este aplicativo fornece aos indivíduos a capacidade de obter e reutilizar seus dados pessoais para suas próprias finalidades em diferentes serviços mediante solicitação? |
| GDPR-direito de ser informado | Ofício | Boolean | True, false, N/A | Este aplicativo informa as pessoas sobre as proteções apropriadas que ele leva quando os dados pessoais são transferidos para um país/região não-UE ou para uma organização internacional? |
| GDPR-direito de restrição de processamento | Ofício | Boolean | True, false, N/A | Este aplicativo fornece aos indivíduos a capacidade de bloquear ou suprimir o processamento de dados pessoais? |
| GDPR-direitos relacionados à tomada de decisões automatizadas | Ofício | Boolean | True, false, N/A | Este aplicativo fornece aos indivíduos a capacidade de optar por não estar sujeito a uma decisão baseada apenas no processamento automatizado? Isso inclui a criação de perfil, que pode ter ramificações legais. |
| GDPR-base ilegal para processamento | Ofício | Boolean | True, false, N/A | Este aplicativo processa dados pessoais de forma legal, de acordo com o consentimento, contrato, obrigações legais, interesses vitais, interesses legítimos, categoria especial, dados e dados ataque criminais? |
| GDPR-direito de retificação | Ofício | Boolean | True, false, N/A | Este aplicativo fornece aos indivíduos a capacidade de retificar seus dados pessoais? O controlador deve responder a todas as solicitações de suas entidades de dados dentro de um mês. |

\* Os campos do tipo *matriz* devem ser separados por um ponto e vírgula (;).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]

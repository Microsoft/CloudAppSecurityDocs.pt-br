---
title: Políticas do Cloud Discovery - Cloud App Security | Microsoft Docs
description: Este tópico descreve as etapas para configurar várias políticas de Cloud Discovery no Cloud App Security.
author: rkarlin
ms.author: rkarlin
ms.date: 06/13/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.assetid: 570da960-771d-484f-932d-b086f2ec2978
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 4c9d90852f1dbdf18da285f63abbb46e91595655
ms.sourcegitcommit: 9f671d5dd5e5da023d598425442d8736546ca183
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66837754"
---
# <a name="cloud-discovery-policies"></a>Políticas de Cloud Discovery

*Aplica-se a: Microsoft Cloud App Security*

Este artigo fornece uma visão geral de como começar a usar o Cloud App Security para obter visibilidade da sua organização sobre TI sombra usando o Cloud Discovery.

Cloud App Security permite descobrir e analisar aplicativos em nuvem que estão sendo usados na ambiente da sua organização. Painel do Cloud Discovery mostra todos os aplicativos de nuvem em execução no ambiente e os classifica pela preparação para a função e enterprise. Para cada aplicativo, descobrir os usuários associados, endereços IP, as máquinas, transações e avaliação de risco conduz sem a necessidade de instalar um agente em seus dispositivos de ponto de extremidade.

## Detectar o uso do novo aplicativo de alto volume ou largos <a name= "detect-volume"></a>

Detecte novos aplicativos são altamente usados, em termos de número de usuários ou a quantidade de tráfego em sua organização.

### <a name="prerequisites"></a>Pré-requisitos

Configurar o upload de log automático para o Cloud Discovery contínuo relatórios, conforme descrito em [configurar o upload de log automático para relatórios contínuos](configure-automatic-log-upload-for-continuous-reports.md).

### <a name="steps"></a>Etapas

1.  Sobre o **políticas** página, crie um novo **política de descoberta de aplicativo**

2.  No **modelo de política** campo, selecione **novo aplicativo de alto volume** ou **novo aplicativo popular** e aplique o modelo.

3.  Personalize os filtros de política para atender aos requisitos da sua organização.

4.  Configure as ações a ser tomada quando um alerta é disparado.

> [!NOTE]
>  Um alerta é gerado uma vez para cada novo aplicativo que não foi descoberto nos últimos 90 dias.

## <a name="detect-new-risky-or-non-compliant-app-use"></a>Detectar o uso do novo aplicativo arriscado ou fora de conformidade

Detecte a exposição potencial da sua organização em aplicativos de nuvem que não atendem aos padrões de segurança.

### <a name="prerequisites"></a>Pré-requisitos

Configurar o upload de log automático para o Cloud Discovery contínuo relatórios, conforme descrito em [configurar o upload de log automático para relatórios contínuos](configure-automatic-log-upload-for-continuous-reports.md).

### <a name="steps"></a>Etapas

1.  Sobre o **políticas** página, crie um novo **política de descoberta de aplicativo.**

2.  No **modelo de política** campo, selecione o **novo aplicativo arriscado** modelo e aplique o modelo.

3.  Sob **aplicativo correspondentes a todos os seguintes** definir os [pontuação de risco](risk-score.md) controle deslizante e e o fator de risco de conformidade para personalizar a você é o nível de risco que você deseja disparar um alerta e defina os outros filtros de política para atender às requisitos de segurança da sua organização.

    1.  Opcional: Para obter as detecções mais significativas, personalize a quantidade de tráfego que vai disparar um alerta.

        1.  Verifique as **disparar uma correspondência de política se todas as seguintes situações ocorrerem no mesmo dia** caixa de seleção.

        2.  Selecione **tráfego diário** maior que 2.000 GB (ou outro).

4.  Configure ações de governança a ser tomada quando um alerta é disparado. Sob **governança**, selecione **marcar aplicativo como não sancionado.**<br>Acesso ao aplicativo será bloqueado automaticamente quando a política é correspondida.

5.  Opcional: Aproveite [integrações nativas do Cloud App Security](set-up-cloud-discovery.md) com Gateways de Web seguro para bloquear o acesso do aplicativo.

## <a name="detect-use-of-unsanctioned-business-apps"></a>Detectar o uso de aplicativos de negócios não sancionados

Você pode detectar quando os funcionários continuam a usar aplicativos não sancionados como uma substituição para aplicativos corporativos aprovados.

### <a name="prerequisites"></a>Pré-requisitos

-   Configurar o upload de log automático para o Cloud Discovery contínuo relatórios, conforme descrito em [configurar o upload de log automático para relatórios contínuos](configure-automatic-log-upload-for-continuous-reports.md).

### <a name="steps"></a>Etapas

1.  No catálogo de aplicativos de nuvem, procure por seus aplicativos prontos para empresa e marcá-los com um [marca de aplicativo personalizada](discovered-app-queries.md#creating-and-managing-custom-app-tags).

2.  Siga as etapas em [detectar novos alto volume ou uso do aplicativo ampla](#detect-volume).

3.  Adicionar um **marca do aplicativo** filtrar e escolha as marcas de aplicativo que você criou para seus aplicativos prontos para empresa.

4.  Configure ações de governança a ser tomada quando um alerta é disparado. Em um controle, selecione **marcar aplicativo como não sancionado**.<br>Acesso ao aplicativo será bloqueado automaticamente quando a política é correspondida.

5.  Opcional: Aproveite [integrações nativas do Cloud App Security](set-up-cloud-discovery.md) com Gateways de Web seguro para bloquear o acesso do aplicativo.

## <a name="detect-unusual-usage-patterns-on-your-network"></a>Detectar padrões de uso incomum em sua rede

Detecte padrões de uso de tráfego anormal (uploads/downloads) em seus aplicativos de nuvem, que se originam de usuários ou endereços IP dentro da rede da sua organização.

### <a name="prerequisites"></a>Pré-requisitos

Configurar o upload de log automático para o Cloud Discovery contínuo relatórios, conforme descrito em [configurar o upload de log automático para relatórios contínuos](configure-automatic-log-upload-for-continuous-reports.md).

### <a name="steps"></a>Etapas

1.  Sobre o **diretivas** página, crie um novo **política de detecção de anomalias do Cloud Discovery**.

2.  No **modelo de política** campo, selecione **comportamentos anormais em usuários descobertos** ou **comportamentos anormais em endereços IP descobertos**.

3.  Personalize os filtros para atender aos requisitos da sua organização.

4. Se você quiser ser alertado somente quando há anomalias envolvendo aplicativos arriscados, use o **pontuação de risco** filtra e defina o intervalo no qual aplicativos são considerados de risco.

4.  Use o controle deslizante para **selecionar sensibilidade de detecção de anomalias**.

> [!NOTE]
>  Depois que o upload de log contínua é estabelecido, o mecanismo de detecção de anomalias demora alguns dias até que uma linha de base (período de aprendizado), é estabelecida para o comportamento esperado em sua organização. Após o estabelecimento de uma linha de base, você começa a receber alertas com base em discrepâncias do comportamento esperado do tráfego entre aplicativos de nuvem feitas por usuários ou de endereços IP.

## <a name="detect-data-exfiltration-to-unsanctioned-storage-apps"></a>Detectar vazamento de dados para aplicativos de armazenamento não sancionados

Detecte possíveis vazamento de dados por um usuário a um aplicativo de armazenamento de nuvem não autorizados.

### <a name="prerequisites"></a>Pré-requisitos

Configurar o upload de log automático para o Cloud Discovery contínuo relatórios, conforme descrito em [configurar o upload de log automático para relatórios contínuos](configure-automatic-log-upload-for-continuous-reports.md).

### <a name="steps"></a>Etapas

1.  Sobre o **diretivas** página, edite a política interna **vazamento de dados para aplicativos não sancionados**.

2.  Selecione o filtro **categoria de aplicativo** é igual a **armazenamento em nuvem**.

3.  Selecione a caixa de seleção **criar um alerta para cada evento correspondente com a gravidade da política**.

4.  Configure as ações a ser tomada quando um alerta é disparado.

## <a name="detect-risky-oauth-apps"></a>Detectar aplicativos arriscados de OAuth

Obtenha visibilidade e controle sobre [aplicativos de OAuth](investigate-risky-oauth.md) que estão instaladas em aplicativos como Salesforce, Office 365 e G Suite. Aplicativos de OAuth que solicitar permissões alta e tem comunidade rara usar podem ser considerados arriscados.

### <a name="prerequisites"></a>Pré-requisitos

Configurar o upload de log automático para o Cloud Discovery contínuo relatórios, conforme descrito em [configurar o upload de log automático para relatórios contínuos](configure-automatic-log-upload-for-continuous-reports.md).

### <a name="steps"></a>Etapas

1.  Sobre o **políticas** página, crie um novo **política de aplicativo OAuth**.

2.  Selecione o filtro **aplicativo** e defina o aplicativo a política deve abranger, G Suite, Office 365 ou Salesforce.

3.  Selecione **nível de permissão** filtrar equals **alta** (disponível para o G Suite e no O365).

4.  Adicione o filtro **uso da comunidade** é igual a **Rare**.

4.  Configure as ações a ser tomada quando um alerta é disparado. Por exemplo, para o Office 365, verifique **revogar aplicativo** para aplicativos de OAuth detectados pela política.

> [!NOTE]
>  Suporte para lojas de aplicativos do Office 365, Salesforce e o G Suite.

## <a name="next-steps"></a>Próximas etapas 

[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  

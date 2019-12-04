---
title: Políticas de Cloud Discovery – Cloud App Security | Microsoft Docs
description: Este artigo descreve as etapas para configurar muitas políticas de Cloud Discovery no Cloud App Security.
author: shsagir
ms.author: shsagir
ms.date: 06/13/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 58208567133bf9c8257e456a415c60ab3dacee0b
ms.sourcegitcommit: 7c93b6f93d2699d466b172590710ed01697bbdad
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74719197"
---
# <a name="cloud-discovery-policies"></a>Políticas de Cloud Discovery

*Aplica-se ao: Microsoft Cloud App Security*

Este artigo fornece uma visão geral de como começar a usar o Cloud App Security para obter visibilidade em sua organização em Shadow IT usando Cloud Discovery.

Cloud App Security permite que você descubra e analise aplicativos de nuvem que estão em uso no ambiente da sua organização. O painel de Cloud Discovery mostra todos os aplicativos de nuvem em execução no ambiente e os categoriza por função e preparação para a empresa. Para cada aplicativo, descubra os usuários associados, os endereços IP, os computadores, as transações e realiza a avaliação de risco sem a necessidade de instalar um agente em seus dispositivos de ponto de extremidade.

## Detectar novo uso de aplicativo de alto volume ou amplo<a name= "detect-volume"></a>

Detecte novos aplicativos que são altamente usados, em termos de número de usuários ou quantidade de tráfego em sua organização.

### <a name="prerequisites"></a>Pré-requisitos

Configure o upload de log automático para relatórios Cloud Discovery contínuos, conforme descrito em [Configurar upload de log automático para relatórios contínuos](configure-automatic-log-upload-for-continuous-reports.md).

### <a name="steps"></a>Etapas

1. Na página **políticas** , crie uma nova **política de descoberta de aplicativo**

2. No campo **modelo de política** , selecione **novo aplicativo de alto volume** ou **novo aplicativo popular** e aplique o modelo.

3. Personalize filtros de política para atender aos requisitos da sua organização.

4. Configure as ações a serem executadas quando um alerta for disparado.

> [!NOTE]
> Um alerta é gerado uma vez para cada novo aplicativo que não foi descoberto nos últimos 90 dias.

## <a name="detect-new-risky-or-non-compliant-app-use"></a>Detectar novo uso de aplicativo arriscado ou não compatível

Detecte uma possível exposição da sua organização em aplicativos de nuvem que não atendem aos seus padrões de segurança.

### <a name="prerequisites"></a>Pré-requisitos

Configure o upload de log automático para relatórios Cloud Discovery contínuos, conforme descrito em [Configurar upload de log automático para relatórios contínuos](configure-automatic-log-upload-for-continuous-reports.md).

### <a name="steps"></a>Etapas

1. Na página **políticas** , crie uma nova **política de descoberta de aplicativo.**

2. No campo **modelo de política** , selecione o **novo modelo de aplicativo arriscado** e aplique o modelo.

3. Em **aplicativo que corresponde a todos os itens a seguir** , defina o controle deslizante de [Pontuação de risco](risk-score.md) e o fator de risco de conformidade para personalizá-lo é o nível de risco para o qual você deseja disparar um alerta e defina os outros filtros de política para atender aos requisitos de segurança de sua organização.

    1. Opcional: para obter detecções mais significativas, personalize a quantidade de tráfego que irá disparar um alerta.

    2. Marque a caixa de seleção **disparar uma correspondência de política se todos os itens a seguir ocorrerem no mesmo dia** .

    3. Selecione o **tráfego diário** maior que 2000 GB (ou outro).

4. Configure ações de governança a serem executadas quando um alerta for disparado. Em **governança**, selecione **aplicativo de marca como não aprovado.**<br />O acesso ao aplicativo será bloqueado automaticamente quando a política for correspondida.

5. Opcional: Aproveite [Cloud app Security integrações nativas](set-up-cloud-discovery.md) com gateways Web seguros para bloquear o acesso ao aplicativo.

## <a name="detect-use-of-unsanctioned-business-apps"></a>Detectar o uso de aplicativos de negócios não aprovados

Você pode detectar quando seus funcionários continuam a usar aplicativos não aprovados como substituição para aplicativos prontos para os negócios aprovados.

### <a name="prerequisites"></a>Pré-requisitos

- Configure o upload de log automático para relatórios Cloud Discovery contínuos, conforme descrito em [Configurar upload de log automático para relatórios contínuos](configure-automatic-log-upload-for-continuous-reports.md).

### <a name="steps"></a>Etapas

1. No catálogo de aplicativos de nuvem, pesquise seus aplicativos prontos para a empresa e marque-os com uma [marca de aplicativo personalizada](discovered-app-queries.md#creating-and-managing-custom-app-tags).

2. Siga as etapas em [detectar novo uso de aplicativo grande ou de alto volume](#detect-volume).

3. Adicione um filtro de **marca de aplicativo** e escolha as marcas de aplicativo que você criou para seus aplicativos prontos para os negócios.

4. Configure ações de governança a serem executadas quando um alerta for disparado. Em governança, selecione **aplicativo de marca como não aprovado**.<br />O acesso ao aplicativo será bloqueado automaticamente quando a política for correspondida.

5. Opcional: Aproveite [Cloud app Security integrações nativas](set-up-cloud-discovery.md) com gateways Web seguros para bloquear o acesso ao aplicativo.

## <a name="detect-unusual-usage-patterns-on-your-network"></a>Detectar padrões de uso incomuns em sua rede

Detectar padrões de uso de tráfego anormal (uploads/downloads) em seus aplicativos de nuvem, que se originam de usuários ou endereços IP dentro da rede da sua organização.

### <a name="prerequisites"></a>Pré-requisitos

Configure o upload de log automático para relatórios Cloud Discovery contínuos, conforme descrito em [Configurar upload de log automático para relatórios contínuos](configure-automatic-log-upload-for-continuous-reports.md).

### <a name="steps"></a>Etapas

1. Na página **políticas** , crie uma nova **política de detecção de anomalias Cloud Discovery**.

2. No campo **modelo de política** , selecione **comportamento anormal em usuários descobertos** ou **comportamento anormal em endereços IP descobertos**.

3. Personalize os filtros para atender aos requisitos da sua organização.

4. Se você quiser ser alertado somente quando houver anomalias envolvendo aplicativos arriscados, use os filtros de **Pontuação de risco** e defina o intervalo no qual os aplicativos são considerados arriscados.

5. Use o controle deslizante para **selecionar a sensibilidade de detecção de anomalias**.

> [!NOTE]
> Após o carregamento de log contínuo ser estabelecido, o mecanismo de detecção de anomalias leva alguns dias até que uma linha de base (período de aprendizagem) seja estabelecida para o comportamento esperado em sua organização. Depois que uma linha de base é estabelecida, você começa a receber alertas com base em discrepâncias do comportamento de tráfego esperado entre aplicativos de nuvem feitos por usuários ou de endereços IP.

## <a name="detect-data-exfiltration-to-unsanctioned-storage-apps"></a>Detectar dados vazamento a aplicativos de armazenamento não aprovados

Detecte dados potenciais de vazamento por um usuário para um aplicativo de armazenamento em nuvem não aprovado.

### <a name="prerequisites"></a>Pré-requisitos

Configure o upload de log automático para relatórios Cloud Discovery contínuos, conforme descrito em [Configurar upload de log automático para relatórios contínuos](configure-automatic-log-upload-for-continuous-reports.md).

### <a name="steps"></a>Etapas

1. Na página **políticas** , edite os dados de política internos **vazamento para aplicativos não aprovados**.

2. Selecione a **categoria filtrar aplicativo** é igual ao **armazenamento em nuvem**.

3. Marque a caixa de seleção para **criar um alerta para cada evento de correspondência com a severidade da política**.

4. Configure as ações a serem tomadas quando um alerta for disparado.

## <a name="detect-risky-oauth-apps"></a>Detectar aplicativos OAuth arriscados

Obtenha visibilidade e controle sobre os [aplicativos OAuth](investigate-risky-oauth.md) instalados dentro de aplicativos como G Suite, Office 365 e Salesforce. Os aplicativos OAuth que solicitam permissões altas e têm um uso raro da Comunidade podem ser considerados arriscados.

### <a name="prerequisites"></a>Pré-requisitos

Você deve ter o G Suite, o Office 365 ou o aplicativo Salesforce conectado usando os [conectores de aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Etapas

1. Na página **políticas** , crie uma nova **política de aplicativo OAuth**.

2. Selecione o **aplicativo** de filtro e defina o aplicativo que a política deve abranger, G Suite, Office 365 ou Salesforce.

3. Selecione filtro de **nível de permissão** é igual a **alto** (disponível para o G Suite e O365).

4. Adicionar o filtro **uso da Comunidade** é igual a **raro**.

5. Configure as ações a serem tomadas quando um alerta for disparado. Por exemplo, para o Office 365, marque **revogar aplicativo** para aplicativos OAuth detectados pela política.

> [!NOTE]
> Com suporte para o G Suite, o Office 365 e as lojas de aplicativos do Salesforce.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]

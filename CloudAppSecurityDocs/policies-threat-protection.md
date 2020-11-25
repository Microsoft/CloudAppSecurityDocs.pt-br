---
title: Políticas de proteção contra ameaças
description: Este tópico descreve as etapas para configurar muitas políticas de proteção contra ameaças no Cloud App Security.
author: shsagir
ms.author: shsagir
ms.date: 11/08/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 97bb8c60dfc04858d20ee4bc0a12236ea060eb65
ms.sourcegitcommit: a0a8e25bda77fb21f280a0e504896be85b89ed6f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96034153"
---
# <a name="threat-protection-policies"></a>Políticas de proteção contra ameaças

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Cloud App Security permite identificar o uso de alto risco e problemas de segurança na nuvem, detectar comportamento anormal do usuário e evitar ameaças em seus aplicativos de nuvem aprovados. Obtenha visibilidade das atividades de usuário e administrador e defina políticas para alertar automaticamente quando um comportamento suspeito ou atividades específicas consideradas arriscadas forem detectadas. Desenhe com a vasta quantidade de dados de pesquisa de ameaças e segurança da Microsoft para ajudar a garantir que seus aplicativos aprovados tenham todos os controles de segurança de que você precisa em vigor e o ajudem a manter o controle sobre eles.

> [!NOTE]
> Ao integrar Cloud App Security com o Microsoft defender para identidade, as políticas do defender para identidade também aparecem na página políticas. Para obter uma lista de políticas do defender for Identity, consulte [alertas de segurança](/defender-for-identity/suspicious-activity-guide).

## <a name="detect-and-control-user-activity-from-unfamiliar-locations"></a>Detectar e controlar a atividade do usuário de locais desconhecidos

Detecção automática de acesso de usuário ou atividade de locais desconhecidos que nunca foram visitados por mais ninguém em sua organização.

### <a name="prerequisites"></a>Pré-requisitos

Você deve ter pelo menos um aplicativo conectado usando [conectores de aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) ou integrados usando o [controle de aplicativo de acesso condicional com controles de sessão](proxy-deployment-aad.md).

### <a name="steps"></a>Etapas

Essa detecção é automaticamente configurada para alertar você quando houver acesso de novos locais. Você não precisa realizar nenhuma ação para configurar essa política. Confira mais informações em [Políticas de detecção de anomalias](anomaly-detection-policy.md).

## <a name="detect-compromised-account-by-impossible-location-impossible-travel"></a>Detectar conta comprometida por local impossível (viagem impossível)

Detecção automática de acesso de usuário ou atividade de 2 locais diferentes em um período de tempo menor do que o tempo necessário para viajar entre os dois.

### <a name="prerequisites"></a>Pré-requisitos

Você deve ter pelo menos um aplicativo conectado usando [conectores de aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) ou integrados usando o [controle de aplicativo de acesso condicional com controles de sessão](proxy-deployment-aad.md).

### <a name="steps"></a>Etapas

1. Essa detecção é automaticamente configurada para alertar você quando houver acesso de locais impossíveis. Você não precisa realizar nenhuma ação para configurar essa política. Confira mais informações em [Políticas de detecção de anomalias](anomaly-detection-policy.md).
2. Opcional: você pode [Personalizar políticas de detecção de anomalias](anomaly-detection-policy.md#scope-anomaly-detection-policies):

    - Personalizar o escopo de detecção em termos de usuários e grupos

    - Escolha os tipos de entradas a serem consideradas

    - Definir sua preferência de sensibilidade para alertas

3. Crie a política de detecção de anomalias.

## <a name="detect-suspicious-activity-from-an-on-leave-employee"></a>Detectar atividades suspeitas de um funcionário "de saída"

Detectar quando um usuário, quem está na licença não paga e não deve estar ativo em nenhum recurso organizacional, está acessando qualquer um dos recursos de nuvem de sua organização.

### <a name="prerequisites"></a>Pré-requisitos

- Você deve ter pelo menos um aplicativo conectado usando os [conectores de aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

- Crie um grupo de segurança em Azure Active Directory para os usuários em uma licença não paga e adicione todos os usuários que você deseja monitorar.

### <a name="steps"></a>Etapas

1. Na tela [grupos de usuários](user-groups.md) , clique em **Criar grupo de usuários** e importe o grupo do Azure ad relevante.

2. Na página **políticas** , crie uma nova **política de atividade**.

3. Defina o **grupo de usuários** de filtro igual ao nome dos grupos de usuários que você criou no Azure ad para os usuários de licença não paga.

4. Opcional: defina as ações de **governança** a serem executadas nos arquivos quando uma violação for detectada. As ações de governança disponíveis variam de acordo com os serviços. Você pode escolher **suspender usuário**.

5. Crie a política de arquivo.

## <a name="detect-and-notify-when-outdated-browser-os-is-used"></a>Detectar e notificar quando um sistema operacional de navegador desatualizado for usado

Detectar quando um usuário está usando um navegador com uma versão de cliente desatualizada que pode representar riscos de conformidade ou segurança para sua organização.

### <a name="prerequisites"></a>Pré-requisitos

Você deve ter pelo menos um aplicativo conectado usando [conectores de aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) ou integrados usando o [controle de aplicativo de acesso condicional com controles de sessão](proxy-deployment-aad.md).

### <a name="steps"></a>Etapas

1. Na página **políticas** , crie uma nova **política de atividade**.

2. Defina a **marca de agente de usuário** de filtro igual ao **navegador desatualizado** e ao **sistema operacional desatualizado**.

3. Defina as ações de **governança** a serem executadas nos arquivos quando uma violação for detectada. As ações de governança disponíveis variam de acordo com os serviços. Em **todos os aplicativos**, selecione **notificar usuário**, para que os usuários possam agir sobre o alerta e atualizar os componentes necessários.

4. Crie a política de atividade.

## <a name="detect-and-alert-when-admin-activity-is-detected-on-risky-ip-addresses"></a>Detectar e alertar quando a atividade de administrador for detectada em endereços IP arriscados

Detecte as atividades de administrador realizadas a partir de e o endereço IP que é considerado um endereço IP arriscado e notifique o administrador do sistema para investigar ainda mais ou definir uma ação de governança na conta do administrador.

### <a name="prerequisites"></a>Pré-requisitos

- Você deve ter pelo menos um aplicativo conectado usando os [conectores de aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

- Na engrenagem de configurações, selecione **intervalos de endereços IP** e clique em + para adicionar intervalos de endereços IP para suas sub-redes internas e seus endereços IP públicos de saída. Defina a **categoria** como **interna**.

### <a name="steps"></a>Etapas

1. Na página **políticas** , crie uma nova **política de atividade**.

2. Defina **agir** para **atividade única**.

3. Definir o **endereço IP** do filtro como **categoria** é igual a **arriscado**

4. Defina a **atividade administrativa** do filtro como **true**

5. Defina as ações de **governança** a serem executadas nos arquivos quando uma violação for detectada. As ações de governança disponíveis variam de acordo com os serviços. Em **todos os aplicativos**, selecione **notificar usuário**, para que os usuários possam agir sobre o alerta e atualizar os componentes necessários do **CC do gerente do usuário**.

6. Crie a política de atividade.

## <a name="detect-activities-by-service-account-from-external-ip-addresses"></a>Detectar atividades por conta de serviço de endereços IP externos

Detectar as atividades da conta de serviço provenientes de endereços IP não internos. Isso pode indicar um comportamento suspeito ou uma conta comprometida.

### <a name="prerequisites"></a>Pré-requisitos

- Você deve ter pelo menos um aplicativo conectado usando os [conectores de aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).
- Na engrenagem de configurações, selecione **intervalos de endereços IP** e clique em + para adicionar intervalos de endereços IP para suas sub-redes internas e seus endereços IP públicos de saída. Defina a **categoria** como **interna**.

- Padronize uma Convenção de nomenclatura para contas de serviço em seu ambiente, por exemplo, defina todos os nomes de conta para começar com "svc".

### <a name="steps"></a>Etapas

1. Na página **políticas** , crie uma nova **política de atividade**.

2. Defina o **usuário** de filtro para **nomear** e, em seguida, **comece com** e insira sua Convenção de nomenclatura, como svc.

3. Defina o filtro **endereço IP** como **categoria** não é igual a **outros** e **corporativos**.

4. Defina as ações de **governança** a serem executadas nos arquivos quando uma violação for detectada. As ações de governança disponíveis variam de acordo com os serviços.

5. Crie a política.

## <a name="detect-mass-download-data-exfiltration"></a>Detectar download em massa (data vazamento)

Detectar quando um determinado usuário acessa ou baixa um grande número de arquivos em um curto período de tempo.

### <a name="prerequisites"></a>Pré-requisitos

Você deve ter pelo menos um aplicativo conectado usando [conectores de aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) ou integrados usando o [controle de aplicativo de acesso condicional com controles de sessão](proxy-deployment-aad.md).

### <a name="steps"></a>Etapas

1. Na página **políticas** , crie uma nova **política de atividade**.

2. Defina os **endereços IP** de filtro como **marca** não é igual a **Microsoft Azure**. Isso excluirá as atividades não interativas baseadas em dispositivo.

3. Defina os **tipos de atividade** de filtro igual a e selecione todas as atividades de download relevantes.

4. Defina as ações de **governança** a serem executadas nos arquivos quando uma violação for detectada. As ações de governança disponíveis variam de acordo com os serviços.
5. Crie a política.

## <a name="detect-potential-ransomware-activity"></a>Detectar a possível atividade de ransomware

Detecção automática de atividade de ransomware potencial.

### <a name="prerequisites"></a>Pré-requisitos

Você deve ter pelo menos um aplicativo conectado usando os [conectores de aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Etapas

1. Essa detecção é automaticamente configurada para alertar você quando houver um risco de ransomware potencial detectado. Você não precisa realizar nenhuma ação para configurar essa política. Confira mais informações em [Políticas de detecção de anomalias](anomaly-detection-policy.md).

2. É possível configurar o **escopo** da detecção e personalizar as ações de governança a serem executadas quando um alerta for disparado. Para obter mais informações sobre como Cloud App Security identifica ransomware, consulte [protegendo sua organização contra ransomware](use-case-ransomware.md).

> [!NOTE]
> Isso se aplica ao Office 365, G Suite, Box e dropbox.

## <a name="detect-malware-in-the-cloud"></a>Detectar malware na nuvem

Detecte arquivos que contenham malware em seus ambientes de nuvem utilizando a integração de Cloud App Security com o mecanismo de inteligência contra ameaças da Microsoft.

### <a name="prerequisites"></a>Pré-requisitos

- Para detecção de malware do Office 365, você deve ter uma licença válida para o Microsoft defender para Office 365 P1.
- Você deve ter pelo menos um aplicativo conectado usando os [conectores de aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Etapas

- Essa detecção é automaticamente configurada para alertar quando há um arquivo que pode conter malware. Você não precisa realizar nenhuma ação para configurar essa política. Confira mais informações em [Políticas de detecção de anomalias](anomaly-detection-policy.md).

## <a name="detect-rogue-admin-takeover"></a>Detectar tomada de administrador não autorizado

Detectar a atividade de administrador repetida que pode indicar intenções mal-intencionadas.

### <a name="prerequisites"></a>Pré-requisitos

Você deve ter pelo menos um aplicativo conectado usando os [conectores de aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Etapas

1. Na página **políticas** , crie uma nova **política de atividade**.

2. Defina **agir** para a **atividade repetida** e personalize as **atividades repetidas mínimas** e defina um **período de tempo** para estar em conformidade com a política da sua organização.

3. Defina o **usuário** de filtro para **do grupo** igual a e selecione todos os grupos de administradores relacionados como **ator apenas**.

4. Defina o **tipo de atividade** de filtro igual a todas as atividades relacionadas a atualizações de senha, alterações e redefinições.

5. Defina as ações de **governança** a serem executadas nos arquivos quando uma violação for detectada. As ações de governança disponíveis variam de acordo com os serviços.
6. Crie a política.

## <a name="detect-suspicious-inbox-manipulation-rules"></a>Detectar regras de manipulação de caixa de entrada suspeitas

Se uma regra de caixa de entrada suspeita foi definida na caixa de entrada de um usuário, isso pode indicar que a conta de usuário está comprometida e que a caixa de correio está sendo usada para distribuir spam e malware em sua organização.

### <a name="prerequisites"></a>Pré-requisitos

- Uso do Microsoft Exchange para email.

### <a name="steps"></a>Etapas

- Essa detecção é automaticamente configurada para alertar você quando houver um conjunto de regras de caixa de entrada suspeita. Você não precisa realizar nenhuma ação para configurar essa política. Confira mais informações em [Políticas de detecção de anomalias](anomaly-detection-policy.md).

## <a name="detect-leaked-credentials"></a>Detectar credenciais vazadas

Quando os criminosos virtuais comprometem senhas válidas de usuários legítimos, eles geralmente compartilham essas credenciais. Geralmente, isso é feito postando-as publicamente na dark Web ou em paste sites, ou então permutando-as ou vendendo-as no mercado negro.

Cloud App Security utiliza a inteligência contra ameaças da Microsoft para corresponder essas credenciais para aquelas usadas dentro de sua organização.

### <a name="prerequisites"></a>Pré-requisitos

Você deve ter pelo menos um aplicativo conectado usando os [conectores de aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Etapas

Essa detecção é automaticamente configurada para alertar você quando um possível vazamento de credencial for detectado. Você não precisa realizar nenhuma ação para configurar essa política. Confira mais informações em [Políticas de detecção de anomalias](anomaly-detection-policy.md).

## <a name="detect-anomalous-file-downloads"></a>Detectar downloads de arquivos anormais

Detectar quando os usuários executam várias atividades de download de arquivo em uma única sessão, em relação à linha de base aprendida. Isso pode indicar uma tentativa de violação.

### <a name="prerequisites"></a>Pré-requisitos

Você deve ter pelo menos um aplicativo conectado usando [conectores de aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) ou integrados usando o [controle de aplicativo de acesso condicional com controles de sessão](proxy-deployment-aad.md).

### <a name="steps"></a>Etapas

1. Essa detecção é automaticamente configurada para alertar quando ocorre um download anormal. Você não precisa realizar nenhuma ação para configurar essa política. Confira mais informações em [Políticas de detecção de anomalias](anomaly-detection-policy.md).

2. É possível configurar o escopo da detecção e personalizar a ação a ser executada quando um alerta é disparado.

## <a name="detect-anomalous-file-shares-by-a-user"></a>Detectar compartilhamentos de arquivos anormais por um usuário

Detectar quando os usuários executam várias atividades de compartilhamento de arquivos em uma única sessão em relação à linha de base aprendida, o que pode indicar uma tentativa de violação.

### <a name="prerequisites"></a>Pré-requisitos

Você deve ter pelo menos um aplicativo conectado usando [conectores de aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) ou integrados usando o [controle de aplicativo de acesso condicional com controles de sessão](proxy-deployment-aad.md).

### <a name="steps"></a>Etapas

1. Essa detecção é automaticamente configurada para alertar você quando os usuários executam vários compartilhamento de arquivos. Você não precisa realizar nenhuma ação para configurar essa política. Confira mais informações em [Políticas de detecção de anomalias](anomaly-detection-policy.md).

2. É possível configurar o escopo da detecção e personalizar a ação a ser executada quando um alerta é disparado.

## <a name="detect-anomalous-activities-from-infrequent-country"></a>Detectar atividades anômalas de um país infrequente

Detectar atividades de um local que não foi recentemente ou que nunca foi visitado pelo usuário ou por nenhum usuário em sua organização.

### <a name="prerequisites"></a>Pré-requisitos

Você deve ter pelo menos um aplicativo conectado usando [conectores de aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) ou integrados usando o [controle de aplicativo de acesso condicional com controles de sessão](proxy-deployment-aad.md).

### <a name="steps"></a>Etapas

1. Essa detecção é automaticamente configurada para alertar quando ocorre uma atividade anômala de um país/região infrequente. Você não precisa realizar nenhuma ação para configurar essa política. Confira mais informações em [Políticas de detecção de anomalias](anomaly-detection-policy.md).

2. É possível configurar o escopo da detecção e personalizar a ação a ser executada quando um alerta é disparado.

> [!NOTE]
> Detectar locais anormais exige um período de aprendizado inicial de 7 dias. Durante o período de aprendizagem, Cloud App Security não gera alertas para novos locais.

## <a name="detect-activity-performed-by-a-terminated-user"></a>Detectar atividade executada por um usuário encerrado

Detecte quando um usuário que não é mais um funcionário da sua organização realiza uma atividade em um aplicativo aprovado. Isso pode indicar atividades mal-intencionadas por um funcionário demitido que ainda tem acesso aos recursos corporativos.

### <a name="prerequisites"></a>Pré-requisitos

Você deve ter pelo menos um aplicativo conectado usando os [conectores de aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Etapas

1. Essa detecção é automaticamente configurada para alertar quando uma atividade é executada por um funcionário encerrado. Você não precisa realizar nenhuma ação para configurar essa política. Confira mais informações em [Políticas de detecção de anomalias](anomaly-detection-policy.md).

2. É possível configurar o escopo da detecção e personalizar a ação a ser executada quando um alerta é disparado.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
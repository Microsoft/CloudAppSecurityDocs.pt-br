---
title: Políticas de proteção - Cloud App Security ameaças | Microsoft Docs
description: Este tópico descreve as etapas para configurar várias políticas de proteção contra ameaças no Cloud App Security.
author: rkarlin
ms.author: rkarlin
ms.date: 06/13/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.assetid: 7c8d5bfd-194e-40ba-b0b0-dfae80f45ecb
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 4cb65835bf2f03eb6bef2fc5973be3420cdedb3d
ms.sourcegitcommit: 9f671d5dd5e5da023d598425442d8736546ca183
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66837764"
---
# <a name="threat-protection-policies"></a>Políticas de proteção contra ameaças

*Aplica-se a: Microsoft Cloud App Security*


Cloud App Security permite que você identifique problemas de segurança de nuvem e de uso alto risco, detecte comportamentos anormais de usuários e evite ameaças em seus aplicativos de nuvem sancionados. Obtenha visibilidade das atividades de administrador e usuário e defina políticas para alertar quando são detectadas atividades específicas que você considere arriscadas ou comportamento suspeito. Desenhar a partir a enorme quantidade de dados de pesquisa de segurança para ajudar a garantir que seus aplicativos sancionados tenham todos os controles de segurança que você precisa no lugar e ajudam você a manter o controle sobre eles e inteligência contra ameaças da Microsoft.

## <a name="detect-and-control-user-activity-from-unfamiliar-locations"></a>Detectar e controlar a atividade do usuário de locais desconhecidos

Detecção automática de acesso de usuário ou atividade de locais desconhecidos que nunca foram visitados por mais ninguém em sua organização.

### <a name="prerequisites"></a>Pré-requisitos

Você deve ter pelo menos um aplicativo conectado usando [conectores de aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) ou integrado usando [controle de acesso condicional do aplicativo com controles de sessão](proxy-deployment-aad.md).

### <a name="steps"></a>Etapas

Esta detecção é configurada automaticamente out-of-the-box para alertá-lo quando não há acesso de novos locais. Você não precisa realizar nenhuma ação para configurar essa política. Para obter mais informações, confira [Políticas de detecção de anomalias](anomaly-detection-policy.md).

## <a name="detect-compromised-account-by-impossible-location-impossible-travel"></a>Detectar uma conta comprometida por localização impossível (viagem impossível)

Detecção automática de acesso de usuário ou atividade de 2 locais diferentes dentro de um período de tempo que for menor do que o tempo de viagem entre os dois.

### <a name="prerequisites"></a>Pré-requisitos

Você deve ter pelo menos um aplicativo conectado usando [conectores de aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) ou integrado usando [controle de acesso condicional do aplicativo com controles de sessão](proxy-deployment-aad.md).
### <a name="steps"></a>Etapas

1.  Esta detecção é configurada automaticamente out-of-the-box para alertá-lo quando não há acesso de locais impossíveis. Você não precisa realizar nenhuma ação para configurar essa política. Para obter mais informações, confira [Políticas de detecção de anomalias](anomaly-detection-policy.md).
2. Opcional: você pode [personalizar as políticas de detecção de anomalias](anomaly-detection-policy.md#scope-anomaly-detection-policies): 
    - Personalizar o escopo de detecção em termos de usuários e grupos

    - Escolha os tipos de entradas a serem considerados

    - Definir sua preferência de sensibilidade para o alerta

3.  Crie a política de detecção de anomalias.

## <a name="detect-suspicious-activity-from-an-on-leave-employee"></a>Detectar uma atividade suspeita de um funcionário "no-leave"

Detecte quando um usuário, que de licença não paga e não deve estar ativo em qualquer recurso organizacional, é acessar qualquer um dos recursos de nuvem da sua organização.

### <a name="prerequisites"></a>Pré-requisitos

- Você deve ter pelo menos um aplicativo conectado usando [conectores de aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

- Criar um grupo de segurança no Azure Active Directory para os usuários de licença não pagas e adicionar todos os usuários que você deseja monitorar.

### <a name="steps"></a>Etapas

1.  Sobre o [grupos de usuários](user-groups.md) tela, clique em **criar grupo de usuário** e grupo de importação do Azure AD relevante.

2.  Sobre o **diretivas** página, crie um novo **política de atividade**.

3.  Defina o filtro **grupo de usuários** igual ao nome dos grupos de usuários que você criou no Azure AD para não paga deixe que os usuários.

4.  Opcional: Defina as **governança** ações a serem tomadas nos arquivos quando uma violação é detectada. As ações de governança disponíveis variam entre os serviços. Você pode escolher **suspender usuário**.

6.  Crie a política de arquivo.

## <a name="detect-and-notify-when-outdated-browser-os-is-used"></a>Detectar e notificar quando desatualizado será usado o navegador do sistema operacional

Detecte quando um usuário estiver usando um navegador com uma versão desatualizada do cliente que possa apresentar riscos de segurança para sua organização ou de conformidade.

### <a name="prerequisites"></a>Pré-requisitos

Você deve ter pelo menos um aplicativo conectado usando [conectores de aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) ou integrado usando [controle de acesso condicional do aplicativo com controles de sessão](proxy-deployment-aad.md).

### <a name="steps"></a>Etapas

1.  Sobre o **diretivas** página, crie um novo **política de atividade**.

2.  Defina o filtro **marca de agente do usuário** é igual a **navegador desatualizado** e **sistema operacional desatualizado**.

3. Defina as **governança** ações a serem tomadas nos arquivos quando uma violação é detectada. As ações de governança disponíveis variam entre os serviços. Sob **todos os aplicativos**, selecione **notificar usuário**, de modo que os usuários podem agir sobre o alerta e atualizar os componentes necessários.

5.  Crie a política de atividade.

## <a name="detect-and-alert-when-admin-activity-is-detected-on-risky-ip-addresses"></a>Detectar e endereços de alerta quando são detectadas atividades de administrador no IP arriscado

Detectar atividades administrativas executadas do e o endereço IP que é considerado um endereço IP arriscado, e notificar o administrador do sistema para uma investigação adicional ou definir uma ação de governança na conta do administrador.

### <a name="prerequisites"></a>Pré-requisitos

- Você deve ter pelo menos um aplicativo conectado usando [conectores de aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).
 
- Na engrenagem de configurações, selecione **intervalos de endereços IP** e clique em de + para Adicionar intervalos de endereços IP para suas sub-redes internas e seus endereços IP públicos de saída. Defina as **categoria** à **interno**.

### <a name="steps"></a>Etapas

1.  Sobre o **diretivas** página, crie um novo **política de atividade**.

2.  Definir **agir** para **único atividade**.

3.  Defina o filtro **endereço IP** à **categoria** é igual a **arriscados**

4.  Defina o filtro **a atividade administrativa** para **True**

5.  Defina as **governança** ações a serem tomadas nos arquivos quando uma violação é detectada. As ações de governança disponíveis variam entre os serviços. Sob **todos os aplicativos**, selecione **notificar usuário**, de modo que os usuários podem agir sobre o alerta e atualizar os componentes necessários **CC o gerente do usuário**.

7.  Crie a política de atividade.

## <a name="detect-activities-by-service-account-from-external-ip-addresses"></a>Detectar atividades pela conta de serviço de endereços IP externos

Detectar atividades de conta de serviço provenientes de um endereço IP não interno endereços. Isso pode indicar comportamento suspeito ou uma conta comprometida.

### <a name="prerequisites"></a>Pré-requisitos

- Você deve ter pelo menos um aplicativo conectado usando [conectores de aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).
- Na engrenagem de configurações, selecione **intervalos de endereços IP** e clique em de + para Adicionar intervalos de endereços IP para suas sub-redes internas e seus endereços IP públicos de saída. Defina as **categoria** à **interno**.

- Padronizar um convenções de nomenclatura de contas de serviço no seu ambiente, por exemplo, defina todos os nomes de conta para começar com "svc".

### <a name="steps"></a>Etapas

1.  Sobre o **diretivas** página, crie um novo **política de atividade**.

2.  Defina o filtro **usuário** à **nome** e, em seguida, **começa com** e insira sua convenção de nomenclatura, como svc.

3.  Defina o filtro **endereço IP** à **categoria** não é igual a **outros** e **corporativo**.

4.  Defina as **governança** ações a serem tomadas nos arquivos quando uma violação é detectada. As ações de governança disponíveis variam entre os serviços.

5.  Crie a política.

## <a name="detect-mass-download-data-exfiltration"></a>Detectar o download em massa (remoção de dados)

Detecte quando um determinado usuário acessa ou baixa um grande número de arquivos em um curto período de tempo.

### <a name="prerequisites"></a>Pré-requisitos

Você deve ter pelo menos um aplicativo conectado usando [conectores de aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) ou integrado usando [controle de acesso condicional do aplicativo com controles de sessão](proxy-deployment-aad.md).

### <a name="steps"></a>Etapas

1.  Sobre o **diretivas** página, crie um novo **política de atividade**.

2.  Defina o filtro **endereços IP** à **marca** não é igual a **Microsoft Azure**. Isso excluirá as atividades não interativa baseada em máquina.

3.  Defina o filtro **tipos de atividade** é igual a e, em seguida, selecione todas as atividades de download relevantes.

4. Defina as **governança** ações a serem tomadas nos arquivos quando uma violação é detectada. As ações de governança disponíveis variam entre os serviços.
5.  Crie a política.

## <a name="detect-potential-ransomware-activity"></a>Detectar uma atividade Ransomware potencial

Detecção automática de atividade de Ransomware potencial.

### <a name="prerequisites"></a>Pré-requisitos

Você deve ter pelo menos um aplicativo conectado usando [conectores de aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Etapas

- Esta detecção é configurada automaticamente out-of-the-box para alertar você quando há um risco potencial de ransomware detectado. Você não precisa realizar nenhuma ação para configurar essa política. Para obter mais informações, confira [Políticas de detecção de anomalias](anomaly-detection-policy.md).  

- É possível configurar o **escopo** da detecção e personalizar as ações de governança a ser tomada quando um alerta é disparado. Para obter mais informações sobre como o Cloud App Security identifica Ransomware, consulte [proteger sua organização contra ransomware](use-case-ransomware.md).

> [!NOTE]
> Isso se aplica ao Office 365, G Suite, Box e Dropbox.

## <a name="detect-malware-in-the-cloud"></a>Detectar malware na nuvem

Detecte arquivos que contêm malware em seus ambientes de nuvem utilizando a integração do Cloud App Security com o mecanismo de inteligência contra ameaças da Microsoft.

### <a name="prerequisites"></a>Pré-requisitos

Você deve ter pelo menos um aplicativo conectado usando [conectores de aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Etapas

- Esta detecção é configurada automaticamente out-of-the-box para alertar você quando há um arquivo que pode conter malware. Você não precisa realizar nenhuma ação para configurar essa política. Para obter mais informações, confira [Políticas de detecção de anomalias](anomaly-detection-policy.md).  

## <a name="detect-rogue-admin-takeover"></a>Detectar a tomada de controle do invasor admin

Detecte uma atividade admin repetidas que pode indicar más intenções.

### <a name="prerequisites"></a>Pré-requisitos

Você deve ter pelo menos um aplicativo conectado usando [conectores de aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Etapas

1.  Sobre o **diretivas** página, crie um novo **política de atividade**.

2.  Definir **agir sobre** para **atividade repetida** e personalizar o **atividades repetidas do mínimo** e defina um **período de tempo** em conformidade com seu política da organização...

3.  Defina o filtro **usuário** para **do grupo** equals e selecione grupo de administrador relacionado **apenas ator**.

4.  Defina o filtro **tipo de atividade** é igual a todas as atividades relacionadas a atualizações de senha, as alterações e redefine.

5. Defina as **governança** ações a serem tomadas nos arquivos quando uma violação é detectada. As ações de governança disponíveis variam entre os serviços.
6.  Crie a política.

## <a name="detect-suspicious-inbox-manipulation-rules"></a>Detectar as regras de manipulação de caixa de entrada suspeita

Se uma regra de caixa de entrada suspeita foi definida na caixa de entrada do usuário, isso poderá indicar que a conta de usuário seja comprometida, e que a caixa de correio está sendo usada para distribuir o spam e malware em sua organização.

### <a name="prerequisites"></a>Pré-requisitos

- Uso do Microsoft Exchange para email.

### <a name="steps"></a>Etapas

- Esta detecção é configurada automaticamente out-of-the-box para alertar você quando há um conjunto de regra de caixa de entrada suspeitas. Você não precisa realizar nenhuma ação para configurar essa política. Para obter mais informações, confira [Políticas de detecção de anomalias](anomaly-detection-policy.md).  


## <a name="detect-leaked-credentials"></a>Detectar credenciais perdidas
  
Quando cibercriminosos comprometem senhas válidas de usuários legítimos, eles muitas vezes compartilham essas credenciais. Geralmente, isso é feito postando-as publicamente na dark web ou em paste sites ou por comerciais ou vender as credenciais no mercado negro.

Cloud App Security utiliza a inteligência contra ameaças da Microsoft de acordo com essas credenciais para aqueles usados dentro da sua organização.

### <a name="prerequisites"></a>Pré-requisitos

Você deve ter pelo menos um aplicativo conectado usando [conectores de aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Etapas

Esta detecção é configurada automaticamente out-of-the-box para alertar quando um credencial possível vazamento for detectado. Você não precisa realizar nenhuma ação para configurar essa política. Para obter mais informações, confira [Políticas de detecção de anomalias](anomaly-detection-policy.md).  


## <a name="detect-anomalous-file-downloads"></a>Detectar downloads de arquivos anormais

Detecte quando os usuários executam várias atividades de download de arquivo em uma única sessão em relação à linha de base aprendida. Isso pode indicar uma tentativa de violação.

### <a name="prerequisites"></a>Pré-requisitos

Você deve ter pelo menos um aplicativo conectado usando [conectores de aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) ou integrado usando [controle de acesso condicional do aplicativo com controles de sessão](proxy-deployment-aad.md).

### <a name="steps"></a>Etapas

- Esta detecção é configurada automaticamente out-of-the-box para alertar você quando ocorre um download anormal. Você não precisa realizar nenhuma ação para configurar essa política. Para obter mais informações, confira [Políticas de detecção de anomalias](anomaly-detection-policy.md).  
- É possível configurar o escopo da detecção e para personalizar a ação a ser tomada quando um alerta é disparado.

## <a name="detect-anomalous-file-shares-by-a-user"></a>Detectar os compartilhamentos de arquivos anormais por um usuário

Detecte quando os usuários executam várias atividades de compartilhamento de arquivos em uma única sessão em relação à linha de base aprendida, que pode indicar uma tentativa de violação.

### <a name="prerequisites"></a>Pré-requisitos
Você deve ter pelo menos um aplicativo conectado usando [conectores de aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) ou integrado usando [controle de acesso condicional do aplicativo com controles de sessão](proxy-deployment-aad.md).
### <a name="steps"></a>Etapas

- Esta detecção é configurada automaticamente out-of-the-box para alertá-lo quando os usuários executam várias o compartilhamento de arquivos. Você não precisa realizar nenhuma ação para configurar essa política. Para obter mais informações, confira [Políticas de detecção de anomalias](anomaly-detection-policy.md).  
- É possível configurar o escopo da detecção e para personalizar a ação a ser tomada quando um alerta é disparado.

## <a name="detect-anomalous-activities-from-infrequent-country"></a>Detectar atividades anormais de país não frequente

Detecte atividades de um local que não foi recentemente ou nunca foi visitado pelo usuário ou por qualquer usuário em sua organização.

### <a name="prerequisites"></a>Pré-requisitos

Você deve ter pelo menos um aplicativo conectado usando [conectores de aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) ou integrado usando [controle de acesso condicional do aplicativo com controles de sessão](proxy-deployment-aad.md).

### <a name="steps"></a>Etapas

- Esta detecção é configurada automaticamente out-of-the-box para alertar você quando ocorre uma atividade anormal em um país não frequente. Você não precisa realizar nenhuma ação para configurar essa política. Para obter mais informações, confira [Políticas de detecção de anomalias](anomaly-detection-policy.md).  
- É possível configurar o escopo da detecção e para personalizar a ação a ser tomada quando um alerta é disparado.

> [!NOTE]
> Detectar locais anormais é necessário um período inicial de assimilação de 7 dias. Durante o período de aprendizado, o Cloud App Security não geram alertas para novos locais.

## <a name="detect-activity-performed-by-a-terminated-user"></a>Detectar uma atividade realizada por um usuário encerrado

Detecte quando um usuário que não seja um funcionário da sua organização executa uma atividade em um aplicativo sancionado. Isso pode indicar atividades mal-intencionadas por um funcionário terminado que ainda tem acesso aos recursos corporativos.

### <a name="prerequisites"></a>Pré-requisitos

Você deve ter pelo menos um aplicativo conectado usando [conectores de aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Etapas

- Esta detecção é configurada automaticamente out-of-the-box para alertar quando uma atividade é executada por um funcionário terminado. Você não precisa realizar nenhuma ação para configurar essa política. Para obter mais informações, confira [Políticas de detecção de anomalias](anomaly-detection-policy.md).  
- É possível configurar o escopo da detecção e para personalizar a ação a ser tomada quando um alerta é disparado.


## <a name="next-steps"></a>Próximas etapas 

[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  

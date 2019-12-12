---
title: Políticas de proteção de informações-Cloud App Security | Microsoft Docs
description: Este tópico descreve as etapas para configurar muitas políticas de proteção de informações no Cloud App Security.
author: shsagir
ms.author: shsagir
ms.date: 06/13/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 3a5f6f6eb607faac7aec7eb9dda3ec1d66cadb5f
ms.sourcegitcommit: 6eff466c7a6817b14a60d8c3b2c201c7ae4c2e2c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74719710"
---
# <a name="information-protection-policies"></a>Políticas de proteção de informações

*Aplica-se ao: Microsoft Cloud App Security*

Cloud App Security políticas de arquivo permitem impor uma ampla variedade de processos automatizados. As políticas podem ser definidas para fornecer proteção de informações, incluindo verificações de conformidade contínuas, tarefas de eDiscovery legais e DLP para conteúdo confidencial compartilhado publicamente.

Cloud App Security pode monitorar qualquer tipo de arquivo com base em mais de 20 filtros de metadados, por exemplo, nível de acesso e tipo de arquivo. Para obter mais informações, consulte [políticas de arquivo](data-protection-policies.md).

## <a name="detect-and-prevent-external-sharing-of-sensitive-data"></a>Detectar e impedir o compartilhamento externo de dados confidenciais

Detecte quando os arquivos com informações de identificação pessoal ou outros dados confidenciais são armazenados em um serviço de nuvem e compartilhados com usuários externos à sua organização que violam a política de segurança da empresa e cria uma possível violação de conformidade.

### <a name="prerequisites"></a>Pré-requisitos

Você deve ter pelo menos um aplicativo conectado usando os [conectores de aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Etapas

1. Na página **políticas** , crie uma nova **política de arquivo**.

2. Defina o **nível de acesso** do filtro igual a **público (Internet)/público/externo**.

3. Em **método de inspeção**, selecione **serviços de classificação de dados (DCS)** e, em **Selecionar tipo** , selecione o tipo de informações confidenciais que você deseja que os DCS inspecionem.

4. Configure as ações de **governança** a serem tomadas quando um alerta for disparado. Por exemplo, você pode criar uma ação de governança que é executada em violações de arquivo detectadas no G Suite no qual você seleciona a opção para **remover usuários externos** e **remover o acesso público**.

5. Crie a política de arquivo.

## <a name="detect-externally-shared-confidential-data"></a>Detectar dados confidenciais compartilhados externamente

Detectar quando os arquivos rotulados como **confidenciais** e armazenados em um serviço de nuvem são compartilhados com usuários externos, violando as políticas da empresa.

### <a name="prerequisites"></a>Pré-requisitos

- Você deve ter pelo menos um aplicativo conectado usando os [conectores de aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

- Habilite a [integração da proteção de informações do Azure](azip-integration.md).

### <a name="steps"></a>Etapas

1. Na página **políticas** , crie uma nova **política de arquivo**.

2. Defina o **rótulo filtrar classificação** como **proteção de informações do Azure** é igual ao rótulo **confidencial** ou o equivalente da sua empresa.

3. Defina o **nível de acesso** do filtro igual a **público (Internet)/público/externo**.

4. Opcional: defina as ações de **governança** a serem executadas nos arquivos quando uma violação for detectada. As ações de governança disponíveis variam de acordo com os serviços.

5. Crie a política de arquivo.

## <a name="detect-and-encrypt-sensitive-data-at-rest"></a>Detectar e criptografar dados confidenciais em repouso

Detectar arquivos que contêm informações de identificação pessoal e outros dados confidenciais que são compartilhados em um aplicativo de nuvem e aplicar rótulos de classificação para limitar o acesso somente aos funcionários de sua empresa.

### <a name="prerequisites"></a>Pré-requisitos

- Você deve ter pelo menos um aplicativo conectado usando os [conectores de aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

- Habilite a [integração da proteção de informações do Azure](azip-integration.md).

### <a name="steps"></a>Etapas

1. Na página **políticas** , crie uma nova **política de arquivo**.

2. Em **método de inspeção**, selecione **DCS (serviço de classificação de dados)** e, em **Selecionar tipo** , selecione o tipo de informações confidenciais que você deseja que os DCS inspecionem.

3. Em **alerta**, marque **aplicar governança de rótulo de classificação** e selecione o rótulo de classificação que sua empresa usa para restringir o acesso aos funcionários da empresa.

4. Crie a política de arquivo.

> [!NOTE]
> Atualmente, a capacidade de aplicar um rótulo de classificação diretamente no Cloud App Security só é compatível com o box, o G Suite, o SharePoint Online e o OneDrive for Business.

## <a name="detect-stale-externally-shared-data"></a>Detectar dados compartilhados externamente obsoletos

Detectar arquivos não utilizados e obsoletos, arquivos que não foram atualizados recentemente, que podem ser acessados publicamente por meio de link público direto, pesquisa na Web ou usuários externos específicos.

### <a name="prerequisites"></a>Pré-requisitos

Você deve ter pelo menos um aplicativo conectado usando os [conectores de aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Etapas

1. Na página **políticas** , crie uma nova **política de arquivo**.

2. Selecione e aplique o modelo de política **obsoleto arquivos compartilhados externamente**.

3. Personalize o filtro **modificado pela última vez** para corresponder à política da sua organização.

4. Opcional: defina as ações de **governança** a serem executadas nos arquivos quando uma violação for detectada. As ações de governança disponíveis variam de acordo com os serviços. Por exemplo:

    - G Suite: tornar o arquivo privado e notificar o último editor de arquivo

    - Box: notificar o último editor de arquivo

    - SharePoint Online: tornar o arquivo privado e enviar um resumo de correspondência de política para o proprietário do arquivo

5. Crie a política de arquivo.

## <a name="detect-data-access-from-an-unauthorized-location"></a>Detectar acesso a dados de um local não autorizado

Detecte quando os arquivos são acessados de um local não autorizado, com base nos locais comuns de sua organização, para identificar um possível vazamento de dados ou acesso mal-intencionado.

### <a name="prerequisites"></a>Pré-requisitos

Você deve ter pelo menos um aplicativo conectado usando os [conectores de aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Etapas

1. Na página **políticas** , crie uma nova **política de atividade**.

2. Defina o **tipo de atividade** de filtro para as atividades de arquivo e pasta que lhe interessam, como **Exibir**, **baixar**, **acessar**e **Modificar**.

3. Definir o **local** do filtro não é igual e, em seguida, inserir os países dos quais sua organização espera atividade.

    1. Opcional: você pode usar a abordagem oposta e definir o filtro como **local** igual a se sua organização bloquear o acesso de países específicos.

4. Opcional: Crie ações de **governança** a serem aplicadas à violação detectada (a disponibilidade varia entre os serviços), como **suspender usuário**.

5. Crie a política de atividade.

## <a name="detect-and-protect-confidential-data-store-in-a-non-compliant-sp-site"></a>Detectar e proteger o armazenamento de dados confidenciais em um site de SP não compatível

Detectar arquivos rotulados como confidenciais e que são armazenados em um site do SharePoint sem conformidade.

### <a name="prerequisites"></a>Pré-requisitos

Os rótulos da proteção de informações do Azure são configurados e usados dentro da organização.

### <a name="steps"></a>Etapas

1. Na página **políticas** , crie uma nova **política de arquivo**.

2. Defina o **rótulo filtrar classificação** como **proteção de informações do Azure** é igual ao rótulo **confidencial** ou o equivalente da sua empresa.

3. Defina a **pasta pai** do filtro que não seja igual e, em **Selecione uma pasta** , escolha todas as pastas em conformidade em sua organização.

4. Em **alertas** , selecione **criar um alerta para cada arquivo correspondente**.

5. Opcional: defina as ações de **governança** a serem executadas nos arquivos quando uma violação for detectada. As ações de governança disponíveis variam de acordo com os serviços. Por exemplo, defina **caixa** para **Enviar resumo de correspondência de política ao proprietário do arquivo** e **colocar em quarentena do administrador**.

6. Crie a política de arquivo.

## <a name="detect-externally-shared-source-code"></a>Detectar código-fonte compartilhado externamente

Detectar quando os arquivos que contêm conteúdo que podem ser código-fonte são compartilhados publicamente ou compartilhados com usuários fora da sua organização.

### <a name="prerequisites"></a>Pré-requisitos

Você deve ter pelo menos um aplicativo conectado usando os [conectores de aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Etapas

1. Na página **políticas** , crie uma nova **política de arquivo**.

2. Selecione e aplique o modelo de política **código-fonte compartilhado externamente**

3. Opcional: Personalize a lista de **extensões** de arquivo para corresponder às extensões de arquivo de código-fonte da sua organização.

4. Opcional: defina as ações de **governança** a serem executadas nos arquivos quando uma violação for detectada. As ações de governança disponíveis variam de acordo com os serviços. Por exemplo, no box, **envie o resumo de correspondência de política para o proprietário do arquivo** e **Coloque em quarentena do administrador**.

5. Selecionar e aplicar o modelo de política

## <a name="detect-unauthorized-access-to-group-data"></a>Detectar acesso não autorizado aos dados do grupo

Detectar quando determinados arquivos que pertencem a um grupo de usuários específico estão sendo acessados excessivamente por um usuário que não faz parte do grupo, o que pode ser uma ameaça Insider potencial.

### <a name="prerequisites"></a>Pré-requisitos

Você deve ter pelo menos um aplicativo conectado usando os [conectores de aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Etapas

1. Na página **políticas** , crie uma nova **política de atividade**.

2. Em **agir em** selecione a **atividade repetida** e personalize as **atividades repetidas mínimas** e defina um **período de tempo** para estar em conformidade com a política da sua organização.

3. Defina o **tipo de atividade** de filtro para as atividades de arquivo e pasta que lhe interessam, como **Exibir**, **baixar**, **acessar**e **Modificar**.

4. Defina o filtro **usuário** como **do grupo** igual a e selecione os grupos de usuários relevantes.

    > [!NOTE]
    > Os [grupos de usuários podem ser importados manualmente](user-groups.md) de aplicativos com suporte.

5. Defina os arquivos **e as pastas** de filtro para **arquivos ou pastas específicas** igual a e escolha os arquivos e pastas que pertencem ao grupo de usuários auditados.

6. Defina as ações de **governança** a serem executadas nos arquivos quando uma violação for detectada. As ações de governança disponíveis variam de acordo com os serviços. Por exemplo, você pode optar por **suspender o usuário**.

7. Crie a política de arquivo.

## <a name="detect-publicly-accessible-s3-buckets"></a>Detectar buckets S3 acessíveis publicamente

Detecte e proteja contra possíveis vazamentos de dados de buckets S3 AWS.

### <a name="prerequisites"></a>Pré-requisitos

Você deve ter uma instância AWS conectada usando os [conectores de aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Etapas

1. Na página **políticas** , crie uma nova **política de arquivo**.

2. Selecione e aplique o modelo de política de **buckets S3 publicamente acessíveis (AWS)** .

3. Defina as ações de **governança** a serem executadas nos arquivos quando uma violação for detectada. As ações de governança disponíveis variam de acordo com os serviços. Por exemplo, defina AWS para **tornar privado** o que tornaria os buckets S3 privados.

4. Crie a política de arquivo.

## <a name="detect-and-protect-gdpr-related-data-across-file-storage-apps"></a>Detectar e proteger dados relacionados ao GDPR em aplicativos de armazenamento de arquivos

Detectar arquivos compartilhados em aplicativos de armazenamento em nuvem e conter informações de identificação pessoal e outros dados confidenciais associados a uma política de conformidade do GDPR. Em seguida, aplique automaticamente rótulos de classificação para limitar o acesso somente ao pessoal autorizado.

### <a name="prerequisites"></a>Pré-requisitos

- Você deve ter pelo menos um aplicativo conectado usando os [conectores de aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

- A [integração da proteção de informações do Azure](azip-integration.md) está habilitada e o rótulo GDPR está configurado em AIP.

### <a name="steps"></a>Etapas

1. Na página **políticas** , crie uma nova **política de arquivo**.

2. Em **método de inspeção**, selecione **DCS (serviço de classificação de dados)** e, em **Selecionar tipo** , selecione um ou mais tipos de informações que estejam em conformidade com a conformidade do GDPR, por exemplo: número do cartão de débito da UE, número de licença dos drivers da UE, número de identificação nacional da UE, número do Passport da UE, número de identificação do imposto da su.

3. Defina as ações de **governança** a serem executadas nos arquivos quando uma violação for detectada, selecionando **aplicar governança de rótulo de classificação** para cada aplicativo com suporte.

4. Criar a política de arquivo

> [!NOTE]
> Atualmente, o **rótulo aplicar classificação** só tem suporte para Box, G Suite, SharePoint Online e onedrive for Business.

## <a name="block-downloads-for-external-users-in-real-time"></a>Bloquear downloads para usuários externos em tempo real

Impedir que os dados da empresa sejam exfiltrateddos por usuários externos, bloqueando downloads de arquivos em tempo real, utilizando [controles de sessão](proxy-intro-aad.md)de Cloud app Security.

### <a name="prerequisites"></a>Pré-requisitos

- [Implante o controle de aplicativo de acesso condicional para aplicativos do Azure ad](proxy-deployment-aad.md).

- Verifique se seu aplicativo é baseado em SAML que utiliza o Azure AD para logon único. Para obter mais informações sobre aplicativos com suporte, consulte [aplicativos e clientes com suporte](proxy-intro-aad.md#supported-apps-and-clients).

### <a name="steps"></a>Etapas

1. Na página **políticas** , crie uma nova **política de sessão**.

2. Em **Tipo de controle de sessão**, selecione **Download do arquivo de controle (com DLP)** .

3. Em **filtros de atividade**, **selecione usuário** e defina-o como **do grupo** igual a **usuários externos**.

    >[!NOTE]
    > Você não precisa definir nenhum filtro de aplicativo para permitir que essa política seja aplicada a todos os aplicativos.

4. Você pode usar o **filtro de arquivo** para personalizar o tipo de arquivo. Isso lhe dá um controle mais granular sobre o tipo de arquivos que a política de sessão controla.

5. Em **ações**, selecione **Bloquear**. Você pode selecionar **Personalizar mensagem de bloqueio** para definir uma mensagem personalizada a ser enviada aos seus usuários para que eles compreendam o motivo pelo qual o conteúdo é bloqueado e como eles podem habilitá-lo aplicando o rótulo de classificação correto.

6. Clique em **Criar**.

## <a name="enforce-read-only-mode-for-external-users-in-real-time"></a>Impor o modo somente leitura para usuários externos em tempo real

Impedir que os dados da empresa sejam exfiltrateddos por usuários externos, bloqueando atividades de impressão e cópia/colagem em tempo real, utilizando [controles de sessão](proxy-intro-aad.md)de Cloud app Security.

### <a name="prerequisites"></a>Pré-requisitos

- [Implante o controle de aplicativo de acesso condicional para aplicativos do Azure ad](proxy-deployment-aad.md).
- Verifique se seu aplicativo é baseado em SAML que utiliza o Azure AD para logon único. Para obter mais informações sobre aplicativos com suporte, consulte [aplicativos e clientes com suporte](proxy-intro-aad.md#supported-apps-and-clients).

### <a name="steps"></a>Etapas

1. Na página **políticas** , crie uma nova **política de sessão**.

2. Em **tipo de controle de sessão**, selecione **bloquear atividades**.

3. No filtro de **origem da atividade** :

    1. Selecione **usuário** e defina **do grupo** para **usuários externos**.

    2. Selecione o **tipo de atividade** é igual a **Imprimir** e **recortar/copiar item**.

    > [!NOTE]
    > Você não precisa definir nenhum filtro de aplicativo para permitir que essa política seja aplicada a todos os aplicativos.

4. Opcional: em **método de inspeção**, selecione o tipo de inspeção a ser aplicado e defina as condições necessárias para a verificação de DLP.

5. Em **ações**, selecione **Bloquear**. Você pode selecionar **Personalizar mensagem de bloqueio** para definir uma mensagem personalizada a ser enviada aos seus usuários para que eles compreendam o motivo pelo qual o conteúdo é bloqueado e como eles podem habilitá-lo aplicando o rótulo de classificação correto.

6. Clique em **Criar**.

## <a name="block-upload-of-unclassified-documents-in-real-time"></a>Bloquear o carregamento de documentos não classificados em tempo real

Impedir que os usuários carreguem dados desprotegidos na nuvem, utilizando [controles de sessão](proxy-intro-aad.md)de Cloud app Security.

### <a name="prerequisites"></a>Pré-requisitos

- [Implante o controle de aplicativo de acesso condicional para aplicativos do Azure ad](proxy-deployment-aad.md).

- Verifique se seu aplicativo é baseado em SAML que utiliza o Azure AD para logon único. Para obter mais informações sobre aplicativos com suporte, consulte [aplicativos e clientes com suporte](proxy-intro-aad.md#supported-apps-and-clients).

- Os rótulos de classificação da proteção de informações do Azure devem ser configurados e usados dentro de sua organização.

### <a name="steps"></a>Etapas

1. Na página **políticas** , crie uma nova **política de sessão**.

2. Em **tipo de controle de sessão**, selecione **controle de carregamento de arquivo (com DLP)** ou **download de arquivo de controle (com DLP)** .

   >[!NOTE]
   > Você não precisa definir nenhum filtro para permitir que essa política se aplique a todos os usuários e aplicativos.

3. Selecione o rótulo de **classificação** de filtro de arquivo não é igual e, em seguida, selecione os rótulos que sua empresa usa para marcar arquivos classificados.

4. Opcional: em **método de inspeção**, selecione o tipo de inspeção a ser aplicado e defina as condições necessárias para a verificação de DLP.

5. Em **ações**, selecione **Bloquear**. Você pode selecionar **Personalizar mensagem de bloqueio** para definir uma mensagem personalizada a ser enviada aos seus usuários para que eles compreendam o motivo pelo qual o conteúdo é bloqueado e como eles podem habilitá-lo aplicando o rótulo de classificação correto.

6. Clique em **Criar**.

> [!NOTE]
> Para obter a lista de tipos de arquivo que Cloud App Security atualmente dá suporte para rótulos de classificação da proteção de informações do Azure, consulte [pré-requisitos de integração da proteção de informações do Azure](azip-integration.md#prerequisites).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]

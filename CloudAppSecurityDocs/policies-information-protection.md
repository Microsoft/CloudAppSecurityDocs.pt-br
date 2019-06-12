---
title: Políticas de proteção de informações – o Cloud App Security | Microsoft Docs
description: Este tópico descreve as etapas para configurar várias políticas de proteção de informações no Cloud App Security.
author: rkarlin
ms.author: rkarlin
ms.date: 06/13/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.assetid: 9a616767-4558-46f1-9da8-aa337920ae45
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: e4b07d47ece8da911e7d8a4a1bd210641f590b36
ms.sourcegitcommit: 9f671d5dd5e5da023d598425442d8736546ca183
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66837774"
---
# <a name="information-protection-policies"></a>Políticas de proteção de informações

*Aplica-se a: Microsoft Cloud App Security*

Políticas de arquivo do Cloud App Security permitem que você aplique uma ampla gama de processos automatizados. As políticas podem ser definidas para fornecer proteção de informações, incluindo verificações de conformidade contínuas, tarefas de descoberta eletrônica jurídica e DLP para conteúdo confidencial compartilhado publicamente.

Cloud App Security pode monitorar qualquer tipo de arquivo com base em mais de 20 filtros de metadados, por exemplo, o nível de acesso e o arquivo de tipo. Para obter mais informações, consulte [políticas de arquivos](data-protection-policies.md).

## <a name="detect-and-prevent-external-sharing-of-sensitive-data"></a>Detectar e evitar o compartilhamento externo de dados confidenciais

Detecte quando os arquivos com informações de identificação pessoal ou outros dados confidenciais são armazenados em um serviço de nuvem e compartilhados com usuários que são externos à sua organização que viola a política de segurança da sua empresa e cria uma possível violação de conformidade.

### <a name="prerequisites"></a>Pré-requisitos

Você deve ter pelo menos um aplicativo conectado usando [conectores de aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).
 
### <a name="steps"></a>Etapas

1. Sobre o **diretivas** página, crie um novo **política de arquivo**.

2. Defina o filtro **nível de acesso** é igual a **pública (Internet) / público / externo**.

3. Sob **método de inspeção**, selecione **serviço de classificação de dados (DCS)** e, em **selecione tipo** selecione o tipo de informações confidenciais que você deseja que os controladores de domínio a ser inspecionado.

6. Configurar o **governança** ações a ser tomada quando um alerta é disparado. Por exemplo, você pode criar uma ação de governança que é executado em violações de arquivo detectado no G Suite, em que você selecione a opção para **remover usuários externos** e **remover acesso público**.

7. Crie a política de arquivo.

## <a name="detect-externally-shared-confidential-data"></a>Detectar dados confidenciais externamente compartilhados

Detectar quando arquivos rotulados **confidencial** e são armazenados em uma nuvem de serviço são compartilhados com usuários externos, violando as políticas da empresa.

### <a name="prerequisites"></a>Pré-requisitos

- Você deve ter pelo menos um aplicativo conectado usando [conectores de aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

- Habilitar [integração do Azure Information Protection](azip-integration.md).

### <a name="steps"></a>Etapas

1.  Sobre o **diretivas** página, crie um novo **política de arquivo**.

2.  Defina o filtro **rótulo de classificação** para **proteção de informações do Azure** é igual a **confidencial** rótulo ou sua empresa equivalente de.

3.  Defina o filtro **nível de acesso** é igual a **pública (Internet) / público / externo**.

1.  Opcional: Defina as **governança** ações a serem tomadas nos arquivos quando uma violação é detectada. As ações de governança disponíveis variam entre os serviços.

5.  Crie a política de arquivo.

## <a name="detect-and-encrypt-sensitive-data-at-rest"></a>Detectar e criptografar dados confidenciais em repouso

Detectar arquivos que contêm informações de identificação pessoal e outros dados confidenciais que é compartilham em um aplicativo de nuvem e aplicam rótulos de classificação para limitar o acesso apenas aos funcionários em sua empresa.

### <a name="prerequisites"></a>Pré-requisitos

- Você deve ter pelo menos um aplicativo conectado usando [conectores de aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

- Habilitar [integração do Azure Information Protection](azip-integration.md).
 
### <a name="steps"></a>Etapas

1.  Sobre o **diretivas** página, crie um novo **política de arquivo**.

2.  Sob **método de inspeção**, selecione **serviço de classificação de dados (DCS)** e, em **selecione tipo** selecione o tipo de informações confidenciais que você deseja que os controladores de domínio a ser inspecionado.

5.  Sob **alerta**, verifique **aplicar o controle de rótulo de classificação** e selecione o rótulo de classificação que sua empresa Use para restringir o acesso aos funcionários da empresa. 

6.  Crie a política de arquivo.

> [!NOTE]
> A capacidade de aplicar um rótulo de classificação diretamente no Cloud App Security está atualmente só tem suporte para o Box, G Suite, SharePoint online e OneDrive para empresas.

## <a name="detect-stale-externally-shared-data"></a>Detectar obsoletos compartilhados externamente dados

Detecte arquivos não utilizados e obsoletos, arquivos que não foram atualizados recentemente, que são acessíveis publicamente por meio do link público direto, pesquisa na web, ou para usuários externos específicos.

### <a name="prerequisites"></a>Pré-requisitos

Você deve ter pelo menos um aplicativo conectado usando [conectores de aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Etapas

1.  Sobre o **diretivas** página, crie um novo **política de arquivo**.

2.  Selecione e aplicar o modelo de política **arquivos obsoletos compartilhados externamente**.

3.  Personalizar o filtro **modificado pela última vez** para corresponder à política da sua organização.

4.  Opcional: Definir **governança** ações a serem tomadas nos arquivos quando uma violação é detectada. As ações de governança disponíveis variam entre os serviços. Por exemplo:

    - G Suite: Tornar o arquivo privado e notificar último editor do arquivo

    - Caixa: Notificar último editor do arquivo

    - SharePoint online: Tornar o arquivo privado e enviar um resumo de correspondência de política para o proprietário do arquivo

6.  Crie a política de arquivo.

## <a name="detect-data-access-from-an-unauthorized-location"></a>Detectar o acesso a dados de um local não autorizado

Detecte quando arquivos são acessados a partir de um local não autorizado, com base em locais comuns da sua organização, para identificar uma potencial perda de dados ou o acesso mal-intencionado.

### <a name="prerequisites"></a>Pré-requisitos

Você deve ter pelo menos um aplicativo conectado usando [conectores de aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).
### <a name="steps"></a>Etapas

1. Sobre o **diretivas** página, crie um novo **política de atividade**.

2. Defina o filtro **tipo de atividade** para as atividades de arquivos e pastas que lhe interessam, como **exibição**, **baixar**, **acesso**e  **Modificar**.

3. Defina o filtro **local** não iguais e, em seguida, insira os países dos quais sua organização espera que a atividade. 

    1.  Opcional: Você pode usar a abordagem oposta e defina o filtro para **local** é igual a se sua organização bloqueia o acesso de países específicos.

4.  Opcional: Crie **governança** detectou de ações a ser aplicado à violação (disponibilidade varia entre os serviços), tais como **suspender usuário**.

6.  Crie a política de atividade.

## <a name="detect-and-protect-confidential-data-store-in-a-non-compliant-sp-site"></a>Detectar e proteger o armazenamento de dados confidenciais em um site de SP não compatível

Detecte arquivos que são rotulados como confidenciais e são armazenados em um site do SharePoint fora de conformidade.

### <a name="prerequisites"></a>Pré-requisitos

Rótulos de proteção de informações do Azure são configurados e usados dentro da organização.

### <a name="steps"></a>Etapas

1.  Sobre o **diretivas** página, crie um novo **política de arquivo**.

2.  Defina o filtro **rótulo de classificação** para **proteção de informações do Azure** é igual a **confidencial** rótulo ou sua empresa equivalente de.

3.  Defina o filtro **pasta pai** não for igual e, em **selecionar uma pasta** escolha todas as pastas em conformidade em sua organização.

6.  Sob **alertas** selecionar **criar um alerta para cada arquivo correspondente**.

7.  Opcional: Defina as **governança** ações a serem tomadas nos arquivos quando uma violação é detectada. As ações de governança disponíveis variam entre os serviços. Por exemplo, defina **caixa de** à **digest de correspondência de política de envio para o proprietário do arquivo** e **colocar em quarentena do administrador**.

8.  Crie a política de arquivo.

## <a name="detect-externally-shared-source-code"></a>Detectar o código-fonte compartilhado externamente

Detecte quando os arquivos que contêm o conteúdo que pode ser o código-fonte são compartilhados publicamente ou são compartilhados com usuários fora da sua organização.

### <a name="prerequisites"></a>Pré-requisitos

Você deve ter pelo menos um aplicativo conectado usando [conectores de aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Etapas

1.  Sobre o **diretivas** página, crie um novo **política de arquivo**.

2.  Selecione e aplicar o modelo de política **externamente compartilhados de código-fonte**

3.  Opcional: Personalizar a lista de arquivos **extensões** para coincidir com extensões de arquivo de código de origem da sua organização.

4. Opcional: Defina as **governança** ações a serem tomadas nos arquivos quando uma violação é detectada. As ações de governança disponíveis variam entre os serviços. Por exemplo, na caixa, **digest de correspondência de política de envio para o proprietário do arquivo** e **colocar em quarentena do administrador**.

5. Selecione e aplicar o modelo de política

## <a name="detect-unauthorized-access-to-group-data"></a>Detectar acesso não autorizado aos dados de grupo

Detecte quando determinados arquivos que pertencem a um grupo de usuários específicos estão sendo acessados excessivamente, por um usuário que não faz parte do grupo, que pode ser uma ameaça em potencial insider.

### <a name="prerequisites"></a>Pré-requisitos

Você deve ter pelo menos um aplicativo conectado usando [conectores de aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Etapas

1. Sobre o **diretivas** página, crie um novo **política de atividade**.

2.  Sob **agir sobre** selecionar **atividade repetida** e personalizar o **atividades repetidas do mínimo** e defina um **período de tempo** em conformidade com seu política da organização.

3.  Defina o filtro **tipo de atividade** para as atividades de arquivos e pastas que lhe interessam, como **exibição**, **baixar**, **acesso**e  **Modificar**.

4.  Defina o filtro **usuário** à **do grupo** é igual a e, em seguida, selecione os grupos de usuários relevantes. 

> [!NOTE]
> [Grupos de usuários podem ser importados manualmente](user-groups.md) de aplicativos com suporte.

6.  Defina o filtro **arquivos e pastas** à **arquivos ou pastas específicas** é igual a e, em seguida, escolha os arquivos e pastas que pertencem ao grupo de usuários auditados.

9.  Defina as **governança** ações a serem tomadas nos arquivos quando uma violação é detectada. As ações de governança disponíveis variam entre os serviços. Por exemplo, você pode optar por **suspender usuário**.

11. Crie a política de arquivo.

## <a name="detect-publicly-accessible-s3-buckets"></a>Detectar publicamente acessíveis buckets de S3

Detecta e protege contra possíveis vazamentos de dados do AWS S3 buckets.

### <a name="prerequisites"></a>Pré-requisitos

Você deve ter uma instância AWS conectada usando [conectores de aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Etapas

1.  Sobre o **diretivas** página, crie um novo **política de arquivo**.

2.  Selecione e aplicar o modelo de política **buckets de S3 publicamente acessíveis (AWS)** .

3.  Defina as **governança** ações a serem tomadas nos arquivos quando uma violação é detectada. As ações de governança disponíveis variam entre os serviços. Por exemplo, defina o AWS como **tornar privado** que tornaria o S3 buckets privada.

5.  Crie a política de arquivo.

## <a name="detect-and-protect-gdpr-related-data-across-file-storage-apps"></a>Detecta e protege o GDPR dados relacionados em aplicativos de armazenamento de arquivo 

Detectar arquivos que são compartilhados em aplicativos de armazenamento em nuvem e contêm informações de identificação pessoal e outros dados confidenciais que são associados por uma política de conformidade de GDPR. Em seguida, aplica automaticamente os rótulos de classificação para limitar o acesso somente ao pessoal autorizado.

### <a name="prerequisites"></a>Pré-requisitos

- Você deve ter pelo menos um aplicativo conectado usando [conectores de aplicativos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

- [Integração da proteção de informações do Azure](azip-integration.md) está habilitado e o rótulo GDPR é configurado no AIP.

### <a name="steps"></a>Etapas

1.  Sobre o **diretivas** página, crie um novo **política de arquivo**.

2.  Sob **método de inspeção**, selecione **serviço de classificação de dados (DCS)** e, em **selecione tipo** selecionar um ou mais tipos de informações que estão em conformidade com GDPR conformidade, por exemplo: Número de cartão de débito da união Europeia, da Europa de carteira de número, o número de identificação nacional da união Europeia, o número de passaporte da união Europeia, o número de identificação de imposto da UE SSN, SU.

5.  Defina a **governança** ações a serem tomadas nos arquivos quando for detectada uma violação, selecionando **governança de rótulo Aplicar classificação** para cada aplicativo com suporte.

7.  Criar a política de arquivo

> [!NOTE]
>  No momento, **aplicar rótulo de classificação** tem suporte apenas para Box, G Suite, SharePoint online e OneDrive para empresas.

## <a name="block-downloads-for-external-users-in-real-time"></a>Bloquear downloads para usuários externos em tempo real

Impedir que os dados da empresa do que está sendo exfiltrated por usuários externos, por bloquear downloads de arquivos em tempo real, utilizando o Cloud App Security [controles de sessão](proxy-intro-aad.md).

### <a name="prerequisites"></a>Pré-requisitos

- [Implantar o controle de aplicativo de acesso condicional para aplicativos do Azure AD](proxy-deployment-aad.md).

- Verifique se que seu aplicativo for um aplicativos baseado em SAML que utiliza o Azure AD para logon único. Para obter mais informações sobre aplicativos com suporte, consulte [suporte para aplicativos e clientes](proxy-intro-aad.md#supported-apps-and-clients).

### <a name="steps"></a>Etapas

1. Sobre o **diretivas** página, crie um novo **política de sessão**.

2. Em **Tipo de controle de sessão**, selecione **Download do arquivo de controle (com DLP)** .

3. Sob **filtros de atividade**, selecione **usuário** e defina-a como **de grupo** é igual a **usuários externos**.

   >[!NOTE]
   > Você não precisa definir os filtros de aplicativo para habilitar essa política se aplique a todos os aplicativos.

1. Você pode usar o **filtro de arquivo** para personalizar o tipo de arquivo. Isso lhe dá controle mais granular sobre que tipo de arquivos que os controles de política de sessão.

2. Sob **ações**, selecione **bloco**. Você pode selecionar **personalizar a mensagem de bloco** para definir uma mensagem personalizada a ser enviada aos usuários para que eles entendem o motivo pelo qual o conteúdo é bloqueado e como eles podem permitir aplicando o rótulo de classificação à direita.

3. Clique em **Criar**.

  
## <a name="enforce-read-only-mode-for-external-users-in-real-time"></a>Impor o modo somente leitura para usuários externos em tempo real

Impedir que os dados da empresa sendo exfiltrated por usuários externos, bloqueando imprimir e copiar/colar as atividades em tempo real, o uso do Cloud App Security [controles de sessão](proxy-intro-aad.md).

### <a name="prerequisites"></a>Pré-requisitos

-   [Implantar o controle de aplicativo de acesso condicional para aplicativos do Azure AD](proxy-deployment-aad.md).
-   Verifique se que seu aplicativo for um aplicativos baseado em SAML que utiliza o Azure AD para logon único. Para obter mais informações sobre aplicativos com suporte, consulte [suporte para aplicativos e clientes](proxy-intro-aad.md#supported-apps-and-clients).
 
### <a name="steps"></a>Etapas

1. Sobre o **diretivas** página, crie um novo **política de sessão**.

2. Sob **tipo de controle de sessão**, selecione **bloquear atividades**.

3. No **fonte da atividade** filtro:
   
    1. Selecione **usuário** e defina **do grupo** para **usuários externos**.

    2. Selecione **tipo de atividade** é igual a **impressão** e **item Recortar/copiar**.

    > [!NOTE]
    > Você não precisa definir os filtros de aplicativo para habilitar essa política se aplique a todos os aplicativos.

4. Opcional: Sob **método de inspeção**, selecione o tipo de inspeção para aplicar e definir as condições necessárias para a verificação DLP.

5. Sob **ações**, selecione **bloco**. Você pode selecionar **personalizar a mensagem de bloco** para definir uma mensagem personalizada a ser enviada aos usuários para que eles entendem o motivo pelo qual o conteúdo é bloqueado e como eles podem permitir aplicando o rótulo de classificação à direita.

6. Clique em **Criar**.

## <a name="block-upload-of-unclassified-documents-in-real-time"></a>Carregamento de bloco de documentos não classificados em tempo real

Impedir que os usuários carreguem dados desprotegidos na nuvem, utilizando o Cloud App Security [controles de sessão](proxy-intro-aad.md).

### <a name="prerequisites"></a>Pré-requisitos

- [Implantar o controle de aplicativo de acesso condicional para aplicativos do Azure AD](proxy-deployment-aad.md).

- Verifique se que seu aplicativo for um aplicativos baseado em SAML que utiliza o Azure AD para logon único. Para obter mais informações sobre aplicativos com suporte, consulte [suporte para aplicativos e clientes](proxy-intro-aad.md#supported-apps-and-clients).

- Rótulos de classificação da proteção de informações do Azure devem ser configurados e usados dentro de sua organização.

### <a name="steps"></a>Etapas

1. Sobre o **diretivas** página, crie um novo **política de sessão**.

2. Sob **tipo de controle de sessão**, selecione **upload do arquivo de controle (com DLP)** ou **download do arquivo de controle (com DLP)** .

   >[!NOTE]
   > Você não precisa definir os filtros para habilitar essa política se aplique a todos os usuários e aplicativos.

3. Selecione o filtro de arquivo **rótulo de classificação** não iguais e, em seguida, selecione os rótulos de sua empresa usa para marcar os arquivos confidenciais.

2. Opcional: Sob **método de inspeção**, selecione o tipo de inspeção para aplicar e definir as condições necessárias para a verificação DLP.

3. Sob **ações**, selecione **bloco**. Você pode selecionar **personalizar a mensagem de bloco** para definir uma mensagem personalizada a ser enviada aos usuários para que eles entendem o motivo pelo qual o conteúdo é bloqueado e como eles podem permitir aplicando o rótulo de classificação à direita.

4. Clique em **Criar**.

> [!NOTE]
> Para obter a lista de tipos de arquivo que o Cloud App Security atualmente oferece suporte para rótulos de classificação da proteção de informações do Azure, consulte [pré-requisitos de integração do Azure Information Protection](azip-integration.md#prerequisites).


## <a name="next-steps"></a>Próximas etapas 

[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  

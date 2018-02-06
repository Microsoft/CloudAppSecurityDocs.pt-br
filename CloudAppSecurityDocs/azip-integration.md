---
title: "Integrar a Proteção de Informações do Azure ao Cloud App Security | Microsoft Docs"
description: "Este artigo fornece informações sobre como utilizar os rótulos da Proteção de Informações do Azure no Cloud App Security para controle adicional sobre o uso de aplicativos de nuvem da sua organização."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/31/2018
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 8168319a-199f-4e6c-ad68-e0f236480803
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 9682c7badb19365ea74ffc78a7a2a38152f84669
ms.sourcegitcommit: bfe898e82c195981cc2fdaa899b0f8ab48957a00
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/05/2018
---
# <a name="azure-information-protection-integration"></a>Integração da Proteção de Informações do Azure

O Cloud App Security permite aplicar rótulos de classificação da Proteção de Informações do Azure automaticamente, com ou sem proteção, a arquivos como uma ação de governança da política de arquivo. Também é possível investigar arquivos com a filtragem do rótulo de classificação aplicado no portal do Cloud App Security. Isso permite maior visibilidade e controle de seus dados confidenciais na nuvem. A integração de Proteção de Informações do Azure ao Cloud App Security é tão fácil quanto marcar uma única caixa de seleção. 

Integrando a Proteção de Informações do Azure no Cloud App Security, você pode aproveitar todo o potencial dos dois serviços e proteger arquivos na nuvem, incluindo:
- A capacidade de aplicar rótulos de classificação como uma ação de governança a arquivos que correspondem a políticas específicas
- A capacidade de exibir todos os arquivos classificados em um local central
- A capacidade de executar investigações de acordo com o nível de classificação e quantificar a exposição de dados confidenciais em seus aplicativos de nuvem
- A capacidade de criar políticas para garantir que os arquivos confidenciais sejam tratados corretamente


> [!NOTE] 
> Para habilitar esse recurso, você precisa de uma licença do Cloud App Security e de uma licença da Proteção de Informações do Azure Premium P2. Assim que as duas licenças estiverem em vigor, o Cloud App Security sincronizará os rótulos das organizações do serviço Proteção de Informações do Azure.


## <a name="prerequisites"></a>Pré-requisitos

- Para trabalhar com a integração da Proteção de Informações do Azure, habilite o [Conector de aplicativos para o Office 365](connect-office-365-to-microsoft-cloud-app-security.md).

Atualmente, o Cloud App Security permite a aplicação de rótulos de classificação da Proteção de Informações do Azure para os seguintes tipos de arquivo:

- Word: docm, docx, dotm, dotx
- Excel: xlam, xlsm, xlsx, xltx
- PowerPoint: potm, potx, ppsx, ppsm, pptm, pptx
- Os arquivos PDF e de imagem estarão disponíveis em versões futuras 

Esse recurso atualmente está disponível para arquivos que são armazenados no Box, SharePoint Online e OneDrive for Business. Mais aplicativos de nuvem serão compatíveis em versões futuras.

Arquivos que foram rotulados com proteção fora do Cloud App Security atualmente não podem ser examinados nem alterados pelo Cloud App Security. Arquivos que foram rotulados (sem proteção) externamente ao Cloud App Security podem ser examinados, e o Cloud App Security pode aplicar um rótulo diferente (com ou sem proteção), conforme definido nas políticas do Cloud App Security.


## <a name="how-it-works"></a>Como funciona
Provavelmente você já está familiarizado com os rótulos de classificação de arquivos na [Proteção de Informações do Azure](https://docs.microsoft.com/information-protection/). As marcações de classificação da Proteção de Informações do Azure são exibidas no Cloud App Security. Assim que você integrar o Cloud App Security à Proteção de Informações do Azure, o Cloud App Security verificará os arquivos da seguinte maneira:
1. O Cloud App Security recupera a lista de todos os rótulos de classificação usados em seu locatário. Isso é executado a cada hora para manter a lista atualizada.
2. Em seguida, o Cloud App Security verifica os arquivos quanto aos rótulos de classificação, da seguinte maneira: a. Se você habilitar a varredura automática (veja a seguir), todos os arquivos novos ou modificados serão adicionados à fila de varredura e todos os arquivos e repositórios existentes serão verificados, classificados e protegidos.
    b. Se você definiu uma política de arquivos (veja o seguinte) para pesquisar rótulos de classificação, esses arquivos serão adicionados à fila de verificação de rótulos de classificação.
3. Conforme observado acima, essas são verificações dos rótulos de classificação descobertos na verificação inicial que o Cloud App Security executa para saber quais rótulos de classificação são usados em seu locatário. Rótulos externos, ou seja, rótulos de classificação definidos por alguém externo ao seu locatário, são adicionados à lista de rótulos de classificação. Se não quiser examinar esses rótulos, marque a caixa de seleção **Somente examinar arquivos para rótulos de classificação da Proteção de Informações do Azure deste locatário** (veja a seguir).
4. Depois que você habilitar a Proteção de Informações do Azure no Cloud App Security, todos os novos arquivos que forem adicionados ao Office 365 também serão verificados quanto aos rótulos de classificação.
5. Crie novas políticas no Cloud App Security que aplicam os rótulos de classificação automaticamente.

## <a name="how-to-integrate-azure-information-protection-with-cloud-app-security"></a>Como integrar a Proteção de Informações do Azure ao Cloud App Security
  
### <a name="enable-azure-information-protection"></a>Habilitar a Proteção de Informações do Azure

Tudo o que você precisa fazer para integrar a Proteção de Informações do Azure ao Cloud App Security é: habilitar a verificação automática para habilitar a pesquisa de rótulos de classificação da Proteção de Informações do Azure nos arquivos do Office 365, sem precisar criar uma política. Depois de habilitar isso, se houver arquivos em seu ambiente de nuvem que estejam rotulados com rótulos de classificação da Proteção de Informações do Azure, eles serão exibidos no Cloud App Security.

Para permitir que o Cloud App Security verifique arquivos com a inspeção de conteúdo habilitada para rótulos de classificação:

1. No Cloud App Security, na engrenagem de configurações, selecione a página **Configurações gerais**.
2. Na Proteção de Informações do Azure, selecione **Examinar arquivos automaticamente para rótulos de classificação da Proteção de Informações do Azure**. 

Depois de habilitar a Proteção de Informações do Azure, os arquivos com rótulos de classificação serão exibidos e você poderá filtrá-los por rótulo no Cloud App Security. Depois que o Cloud App Security estiver conectado ao aplicativo na nuvem, você poderá usar os recursos de integração da Proteção de Informações do Azure no Cloud App Security que permitem aplicar rótulos da Proteção de Informações do Azure (com ou sem proteção) diretamente no portal do Cloud App Security, adicionando-os diretamente a arquivos ou configurando uma política de arquivo para aplicar os rótulos de classificação automaticamente como uma ação de governança.


 ![habilitar a Proteção de Informações do Azure](./media/enable-azip.png)

> [!NOTE] 
> A verificação automática não verifica arquivos existentes até que eles sejam modificados novamente. Para verificar rótulos de classificação em arquivos existentes da Proteção de Informações do Azure, você deve ter pelo menos um **Política de arquivo para inspeção de conteúdo**. Se não tiver nenhuma, crie uma nova **Política de arquivo**, exclua todos os filtros predefinidos, verifique a opção **Inspeção de conteúdo**. Em seguida, em **Inspeção de conteúdo**, clique em **Incluir arquivos que correspondem a uma expressão predefinida**, selecione qualquer valor predefinido e salve a política. Isso permite a inspeção do conteúdo, que detecta automaticamente os rótulos de classificação da Proteção de Informações do Azure.

#### <a name="set-internal-and-external-tags"></a>Definir marcações internas e externas
Por padrão, o Cloud App Security examina rótulos de classificação que foram definidos em sua organização, bem como aqueles externos que foram definidos por outras organizações. 


Para ignorar os rótulos de classificação definidos fora da sua organização, no portal do Cloud App Security, em **Configurações gerais** em **Configurações de segurança do Azure**, selecione **Ignorar rótulos de classificação da Proteção de Informações do Azure de outros locatários**.
 
![ignorar rótulos](./media/azip-ignore.png)

### <a name="apply-labels-directly-to-files"></a>Aplicar rótulos diretamente a arquivos

1. Na página **Arquivos**, selecione o arquivo que deseja proteger e, em seguida, clique nos três pontos ao final da linha do arquivo e escolha **Aplicar rótulo de classificação**.

 ![proteger aplicativo](./media/protect-app.png)
  
  >[!NOTE]
  > O Cloud App Security pode aplicar a Proteção de Informações do Azure em arquivos de até 50 MB.  

2. Você deve escolher um dos rótulos de classificação de sua organização a serem aplicados ao arquivo e clicar em **Aplicar**. 
![rótulo de classificação de proteção](./media/protect-template.png)

3. Depois de escolher um rótulo de classificação e clicar em Aplicar, o Cloud App Security aplicará o rótulo de classificação ao arquivo original.

5. Também remova rótulos de classificação escolhendo a opção **Remover rótulo de classificação**. 


Para obter mais informações sobre como o Cloud App Security e a Proteção de Informações do Azure funcionam juntos, consulte [Proteger dados contra erros de usuário](https://docs.microsoft.com/enterprise-mobility-security/solutions/protect-data-user-mistake).

### <a name="automatically-label-files-preview"></a>Rotular arquivos automaticamente (versão prévia)

Aplique rótulos de classificação a arquivos automaticamente criando uma política de arquivo e configurando **Aplicar rótulo de classificação** como a ação de governança.

Siga estas instruções para criar a política de arquivo:

1.  Criar uma política de arquivo.
2.  Defina a política, incluindo o tipo de arquivo que você deseja detectar, por exemplo, todos os arquivos em que **Nível de acesso** não é igual a **Interno** e em que **UO do Proprietário** é igual à sua equipe de finanças. 
3.  Nas ações de governança do aplicativo relevante, selecione **Aplicar um rótulo de classificação** e, em seguida, o tipo de rótulo.

   ![Aplicar rótulo](./media/aip-gov-action.png)

### <a name="control-file-exposure"></a>Controlar a exposição de arquivo

- Se esse for o documento rotulado com um rótulo de classificação da Proteção de Informações do Azure:

   ![Exemplo de tela da Proteção de Informações do Azure](./media/azip-screen.png)

- Você pode exibir esse arquivo no Cloud App Security, na página **Arquivos**, filtrando pelo rótulo de classificação:

   ![Cloud App Security comparado com a Proteção de Informações do Azure](./media/cas-compared-azip.png)

- Obtenha mais informações sobre esses arquivos e seus rótulos de classificação na gaveta do arquivo, clicando no arquivo relevante na página **Arquivos** e verifique se ele tem um rótulo de classificação:

   ![gaveta de arquivos](./media/azip-file-drawer.png)

- Em seguida, você pode criar políticas de arquivo no Cloud App Security para controlar arquivos que são compartilhados inadequadamente e localizar arquivos rotulados que foram modificados recentemente.
- Além disso, você pode disparar alertas sobre atividades relacionadas a arquivos confidenciais.

  ![rótulos da Proteção de Informações do Azure no Cloud App Security](./media/azip-tags-in-cas.png)

- Também crie uma política que aplica automaticamente um rótulo de classificação a arquivos específicos.


> [!Note]
> Quando os rótulos do Azure Identity Protection estiverem desabilitados em um arquivo, os rótulos desabilitados serão exibidos como desabilitados no Cloud App Security. Rótulos excluídos não são exibidos.


**Política de exemplo – dados confidenciais externamente compartilhados no Box:**

1.  Criar uma política de arquivo.
2.  Definir o nome, gravidade e categoria da política.
3.  Adicionar os seguintes filtros para localizar todos os dados confidenciais que são externamente compartilhados no Box:

![política de confidencialidade](./media/azip-confidentiality-policy.png) 

**Política de exemplo – dados restritos que recentemente foram modificados fora da pasta Finanças no SharePoint:**

1.  Criar uma política de arquivo.
2.  Definir o nome, gravidade e categoria da política.
3.  Adicionar os seguintes filtros para localizar todos os dados restritos que foram modificados recentemente e adicionar excluir a pasta Finanças na opção de seleção de pasta: 
 
![política de dados restritos](./media/azip-restricted-data-policy.png) 

Você também pode optar por definir alertas, notificação do usuário ou tomar ação imediata para essas políticas.
Saiba mais sobre [ações de governança](governance-actions.md).

Saiba mais sobre [Proteção de Informações do Azure](https://docs.microsoft.com/en-us/information-protection/understand-explore/what-is-information-protection) e confira o [tutorial de Início Rápido](https://docs.microsoft.com/en-us/information-protection/get-started/infoprotect-quick-start-tutorial) da Proteção de Informações do Azure.


 
## <a name="related-videos"></a>Vídeos Relacionados  
[Integrações do Cloud App Security + Proteção de Informações do Azure](https://channel9.msdn.com/Shows/Microsoft-Security/MCAS--AIP-Integrations)  

## <a name="see-also"></a>Consulte Também  
[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)   

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  

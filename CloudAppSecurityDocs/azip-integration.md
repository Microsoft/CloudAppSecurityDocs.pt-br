---
title: Integrar a proteção de informações do Azure com o Cloud App Security
description: Este artigo fornece informações sobre como aproveitar as marcas da proteção de informações do Azure em Cloud App Security para controle adicional do uso do aplicativo de nuvem da sua organização.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/09/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: b32007479ece2828cc13376f88188bfdc08ade7c
ms.sourcegitcommit: 288c279a0d2dd62a8ad8d7425c3e9e98857bf5f4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/05/2020
ms.locfileid: "80666457"
---
# <a name="azure-information-protection-integration"></a>Integração à Proteção de Informações do Azure

*Aplica-se a: Microsoft Cloud App Security*

Microsoft Cloud App Security permite aplicar rótulos de classificação da proteção de informações do Azure automaticamente, com ou sem proteção, aos arquivos como uma ação de governança de política de arquivo. Você também pode investigar arquivos filtrando o rótulo de classificação aplicado no portal de Cloud App Security. O uso de classificações permite maior visibilidade e controle de seus dados confidenciais na nuvem. A integração da proteção de informações do Azure com o Cloud App Security é tão fácil quanto marcar uma única caixa de seleção.

> [!NOTE]
> Este artigo também é relevante para rótulos de sensibilidade unificada do Office 365 se você já tiver [migrado seus rótulos de classificação para o centro de conformidade e segurança do office 365](https://docs.microsoft.com/azure/information-protection/configure-policy-migrate-labels). Se você não migrou os rótulos de classificação existentes e começa a criar novos rótulos no centro de conformidade e segurança do Office 365, Cloud App Security usará somente os rótulos preexistentes configurados no portal da proteção de informações do Azure.

Ao integrar a proteção de informações do Azure ao Cloud App Security, você pode usar todo o poder dos serviços e proteger os arquivos em sua nuvem, incluindo:

- A capacidade de aplicar rótulos de classificação como uma ação de governança a arquivos que correspondem a políticas específicas
- A capacidade de exibir todos os arquivos classificados em um local central
- A capacidade de investigar de acordo com o nível de classificação e quantificar a exposição de dados confidenciais em seus aplicativos de nuvem
- A capacidade de criar políticas para garantir que os arquivos classificados estejam sendo tratados corretamente

> [!NOTE]
> Para habilitar esse recurso, você precisa de uma licença Cloud App Security e uma licença para a proteção de informações do Azure Premium P1. Assim que ambas as licenças estiverem em vigor, o Cloud App Security sincronizará os rótulos das organizações do serviço de proteção de informações do Azure.

## <a name="prerequisites"></a>{1&gt;{2&gt;Pré-requisitos&lt;2}&lt;1}

- Para trabalhar com a integração da proteção de informações do Azure, você deve habilitar o [conector de aplicativos para o Office 365](connect-office-365-to-microsoft-cloud-app-security.md).

Para usar rótulos no Cloud App Security, os rótulos devem ser publicados como parte da política. Se você estiver usando a proteção de informações do Azure, os rótulos deverão ser publicados por meio do portal da proteção de informações do Azure. Se você migrou para rótulos unificados, os rótulos devem ser publicados por meio do centro de conformidade e segurança do Office 365.

O Cloud App Security atualmente dá suporte à aplicação de rótulos de classificação da proteção de informações do Azure para os seguintes tipos de arquivo:

- Word: docm, docx, dotm, dotx
- Excel: xlam, xlsm, xlsx, xltx
- PowerPoint: potm, potx, ppsx, ppsm, pptm, pptx
- PDF
  > [!NOTE]
  > Para PDF, você deve usar rótulos unificados.

Esse recurso está disponível atualmente para arquivos armazenados no box, G Suite, SharePoint Online e OneDrive for Business. Mais aplicativos de nuvem terão suporte em versões futuras.

Os arquivos que foram rotulados com proteção fora do Cloud App Security não podem ser alterados pelo Cloud App Security. No entanto, você pode verificar esses arquivos concedendo permissões para [inspecionar o conteúdo de arquivos protegidos](content-inspection.md#content-inspection-for-protected-files).

## <a name="how-it-works"></a>Como funciona

Você provavelmente está familiarizado com rótulos de classificação de arquivos na [proteção de informações do Azure](https://docs.microsoft.com/azure/information-protection/what-is-information-protection). Você pode ver as marcas de classificação da proteção de informações do Azure em Cloud App Security. Assim que você integrar Cloud App Security com a proteção de informações do Azure, Cloud App Security verificará os arquivos da seguinte maneira:

1. Cloud App Security recupera a lista de todos os rótulos de classificação usados em seu locatário. Essa ação é executada a cada hora para manter a lista atualizada.

2. Cloud App Security examina os arquivos em busca de rótulos de classificação, da seguinte maneira:

    - Se você tiver habilitado a verificação automática, todos os arquivos novos ou modificados serão adicionados à fila de verificação e todos os arquivos e repositórios existentes serão verificados.
    - Se você definir uma política de arquivo para pesquisar rótulos de classificação, esses arquivos serão adicionados à fila de verificação para rótulos de classificação.

3. Conforme observado acima, essas verificações são para os rótulos de classificação descobertos na verificação inicial Cloud App Security faz para ver quais rótulos de classificação são usados em seu locatário. Rótulos externos, rótulos de classificação definidos por alguém externo ao seu locatário, são adicionados à lista de rótulos de classificação. Se você não quiser verificar isso, marque a caixa de seleção **verificar somente os arquivos de verificação dos rótulos de classificação da proteção de informações do Azure deste locatário** .

4. Depois de habilitar a proteção de informações do Azure no Cloud App Security, todos os novos arquivos adicionados aos seus aplicativos de nuvem conectados serão verificados em busca de rótulos de classificação.

5. Você pode criar novas políticas dentro de Cloud App Security que aplicam seus rótulos de classificação automaticamente.

## <a name="how-to-integrate-azure-information-protection-with-cloud-app-security"></a>Como integrar a proteção de informações do Azure com o Cloud App Security
  
### <a name="enable-azure-information-protection"></a>Habilitar a proteção de informações do Azure

Tudo o que você precisa fazer para integrar a proteção de informações do Azure com Cloud App Security é clicar em uma única caixa de seleção. Habilitando a verificação automática, você habilita a pesquisa de rótulos de classificação da proteção de informações do Azure nos arquivos do Office 365 sem a necessidade de criar uma política. Depois de habilitá-lo, se você tiver arquivos em seu ambiente de nuvem rotulados com rótulos de classificação da proteção de informações do Azure, você os verá em Cloud App Security.

Para habilitar Cloud App Security verificar arquivos com a inspeção de conteúdo habilitada para rótulos de classificação:

1. Em Cloud App Security, sob as configurações engrenagem, selecione a página **configurações** no título **sistema** .

    ![Menu configurações](media/azip-system-settings.png)
1. Em **proteção de informações do Azure**, selecione **examinar automaticamente os arquivos para rótulos de classificação da proteção de informações do Azure**.

    ![habilitar a proteção de informações do Azure](media/enable-azip.png)

Depois de habilitar a proteção de informações do Azure, você poderá ver os arquivos que têm rótulos de classificação e filtrá-los por rótulo em Cloud App Security. Depois que Cloud App Security estiver conectado ao aplicativo de nuvem, você poderá usar os recursos de integração da proteção de informações do Azure para aplicar rótulos de classificação da proteção de informações do Azure (com ou sem proteção) no portal de Cloud App Security, adicionando-os diretamente aos arquivos ou configurando uma política de arquivo para aplicar rótulos de classificação automaticamente como uma ação de governança.

> [!NOTE]
> A verificação automática não verifica os arquivos existentes até que eles sejam modificados novamente. Para verificar os arquivos existentes dos rótulos de classificação da proteção de informações do Azure, você deve ter pelo menos uma **política de arquivo** que inclua a inspeção de conteúdo. Se você não tiver nenhum, crie uma nova **política de arquivo**, exclua todos os filtros predefinidos, em método de **inspeção** , selecione **DLP interno**. No campo **inspeção de conteúdo** , selecione **incluir arquivos que correspondam a uma expressão predefinida** e selecione qualquer valor predefinido e salve a política. Isso habilita a inspeção de conteúdo, que detecta automaticamente os rótulos de classificação da proteção de informações do Azure.

#### <a name="set-internal-and-external-tags"></a>Definir marcas internas e externas

Por padrão, Cloud App Security examina rótulos de classificação que foram definidos em sua organização, bem como externos definidos por outras organizações. 

Para ignorar os rótulos de classificação definidos como externos à sua organização, no portal Cloud App Security, vá em **configurações** e **proteção de informações do Azure**. Selecione **somente arquivos de verificação para rótulos de classificação da proteção de informações do Azure e avisos de inspeção de conteúdo deste locatário**.

![ignorar rótulos](media/azip-ignore.png)

### <a name="apply-labels-directly-to-files"></a>Aplicar rótulos diretamente aos arquivos

1. Na página **arquivos** em **investigar**, selecione o arquivo que você deseja proteger. Clique nos três pontos no final da linha do arquivo e escolha **aplicar rótulo de classificação**.  

    ![proteger aplicativo](media/protect-app.png)
  
    >[!NOTE]
    > Cloud App Security pode aplicar a proteção de informações do Azure em arquivos com até 50 MB.

2. Você será solicitado a escolher um dos rótulos de classificação da sua organização para aplicar ao arquivo e clicar em **aplicar**.

    ![rótulo de classificação de proteção](media/protect-template.png)

3. Depois de escolher um rótulo de classificação e clicar em aplicar, Cloud App Security aplicará o rótulo de classificação ao arquivo original.

4. Você também pode remover rótulos de classificação escolhendo a opção **remover rótulo de classificação** .

> [!NOTE]
> Você pode remover rótulos somente se eles não incluírem proteção e se eles foram aplicados no Cloud App Security, não rótulos aplicados diretamente na proteção de informações.

Para obter mais informações sobre como Cloud App Security e a proteção de informações do Azure funcionam em conjunto, consulte [proteger dados contra erros do usuário](https://docs.microsoft.com/enterprise-mobility-security/solutions/protect-data-user-mistake).

### <a name="automatically-label-files"></a>Rotular arquivos automaticamente

Você pode aplicar automaticamente rótulos de classificação a arquivos criando uma política de arquivo e configurando **aplicar rótulo de classificação** como a ação de governança.

Siga estas instruções para criar a política de arquivo:

1. Crie uma política de arquivo.
2. Defina a política para incluir o tipo de arquivo que você deseja detectar. Por exemplo, selecione todos os arquivos em que **nível de acesso** não é igual **interno** e onde a **UO proprietária** é igual à sua equipe de finanças.
3. Em ações de governança para o aplicativo relevante, clique em **aplicar um rótulo de classificação** e selecione o tipo de rótulo.

    ![Aplicar rótulo](media/aip-gov-action.png)

> [!NOTE]
> A capacidade de aplicar automaticamente um rótulo de Proteção de Informações do Azure por meio de uma política de arquivos é um recurso poderoso. Para proteger os clientes de aplicarem por engano um rótulo a um grande número de arquivos, como precaução de segurança, há um limite diário de 100 ações **Aplicar rótulo** por aplicativo, por locatário. Depois que o limite diário for atingido, a ação "Aplicar rótulo" será pausada temporariamente e continuará automaticamente no dia seguinte (após as 00:00 UTC). Para aumentar o limite do seu locatário, abra um tíquete de suporte.

### <a name="control-file-exposure"></a>Controlar a exposição do arquivo

- Por exemplo, se a seguir for um documento rotulado com um rótulo de classificação da proteção de informações do Azure:

    ![tela de proteção de informações do Azure de exemplo](media/azip-screen.png)

- Você pode ver este documento em Cloud App Security filtrando o rótulo classificação da proteção de informações do Azure na página **arquivos** .

    ![Cloud App Security em comparação com a proteção de informações do Azure](media/cas-compared-azip.png)

- Você pode obter mais informações sobre esses arquivos e seus rótulos de classificação na gaveta de arquivos. Basta clicar no arquivo relevante na página **arquivos** e verificar se ele tem um rótulo de classificação.

    ![gaveta de arquivos](media/azip-file-drawer.png)

- Em seguida, você pode criar políticas de arquivo em Cloud App Security para controlar arquivos que são compartilhados incorretamente e localizar arquivos rotulados e foram modificados recentemente.

- Você pode criar uma política que aplica automaticamente um rótulo de classificação a arquivos específicos.
- Você também pode disparar alertas sobre atividades relacionadas à classificação de arquivos.

> [!Note]
> Quando os rótulos da proteção de informações do Azure são desabilitados em um arquivo, os rótulos desabilitados aparecem como desabilitados no Cloud App Security. Os rótulos excluídos não são exibidos.

**Política de exemplo – dados confidenciais compartilhados externamente no box:**

1. Crie uma política de arquivo.
2. Defina o nome, a severidade e a categoria da política.
3. Adicione os filtros a seguir para localizar todos os dados confidenciais que são compartilhados externamente na caixa:

    ![política de confidencialidade](media/azip-confidentiality-policy.png)

**Dados de exemplo restritos por política que foram modificados recentemente fora da pasta finanças no SharePoint:**

1. Crie uma política de arquivo.
2. Defina o nome, a severidade e a categoria da política.
3. Adicione os filtros a seguir para localizar todos os arquivos restritos modificados recentemente ao excluir a pasta Finance na opção de seleção de pasta:

    ![política de dados restritos](media/azip-restricted-data-policy.png)

Você também pode optar por definir alertas, notificação do usuário ou executar uma ação imediata para essas políticas.
Saiba mais sobre as [ações de governança](governance-actions.md).

Saiba mais sobre a [proteção de informações do Azure](https://docs.microsoft.com/information-protection/understand-explore/what-is-information-protection) e confira o [tutorial de início rápido](https://docs.microsoft.com/information-protection/get-started/infoprotect-quick-start-tutorial)da proteção de informações do Azure.

## <a name="next-steps"></a>{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}

> [!div class="nextstepaction"]
> [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

## <a name="related-videos"></a>Vídeos relacionados

> [!div class="nextstepaction"]
> [Cloud App Security + integrações da proteção de informações do Azure](https://channel9.msdn.com/Shows/Microsoft-Security/MCAS--AIP-Integrations)  

[!INCLUDE [Open support ticket](includes/support.md)]

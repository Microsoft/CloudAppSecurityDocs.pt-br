---
title: "Integrar a Proteção de Informações do Azure ao Cloud App Security | Microsoft Docs"
description: "Este artigo fornece informações sobre como utilizar os rótulos da Proteção de Informações do Azure no Cloud App Security para controle adicional sobre o uso de aplicativos de nuvem da sua organização."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/10/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 8168319a-199f-4e6c-ad68-e0f236480803
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 79e784c332045ebe300a34f5c6da918343a0df45
ms.sourcegitcommit: 2f4474084c7e07ac4853945ab5aa1ea78950675d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/28/2017
---
# <a name="azure-information-protection-integration"></a>Integração da Proteção de Informações do Azure

O Cloud App Security permite investigar arquivos e definir políticas com base nos rótulos de classificação da Proteção de Informações do Azure, permitindo maior visibilidade e controle dos dados confidenciais na nuvem. A integração de Proteção de Informações do Azure ao Cloud App Security é tão fácil quanto marcar uma única caixa de seleção. 

Integrando a Proteção de Informações do Azure no Cloud App Security, você pode aproveitar todo o potencial dos dois serviços e proteger arquivos na nuvem, incluindo:
- A capacidade de exibir todos os arquivos classificados em um local central
- A capacidade de executar investigações de acordo com o nível de classificação e quantificar a exposição de dados confidenciais em seus aplicativos de nuvem
- A capacidade de criar políticas para garantir que os arquivos confidenciais sejam tratados corretamente

> [!NOTE] 
> Para habilitar esse recurso você precisará uma licença do Cloud App Security e uma licença para a Proteção de Informações do Azure Premium P1 ou P2. Assim que as duas licenças estiverem em vigor, o Cloud App Security sincronizará os rótulos das organizações do serviço de Proteção de Informações do Azure.

## <a name="how-it-works"></a>Como funciona
Provavelmente você já está familiarizado com os rótulos de classificação de arquivos na [Proteção de Informações do Azure](https://docs.microsoft.com/information-protection/). As marcações de classificação da Proteção de Informações do Azure são exibidas no Cloud App Security. Assim que você integrar o Cloud App Security à Proteção de Informações do Azure, o Cloud App Security verificará os arquivos da seguinte maneira:
1. O Cloud App Security recupera a lista de todos os rótulos de classificação usados em seu locatário. Isso é executado a cada hora para manter a lista atualizada.
2. Em seguida, o Cloud App Security verifica os arquivos quanto aos rótulos de classificação, da seguinte maneira: a. Se você habilitou a verificação automática (veja abaixo), todos os arquivos novos ou modificados serão adicionados à fila de verificação.
    b. Se você definiu uma política de arquivos (veja abaixo) para pesquisar rótulos de classificação, esses arquivos serão adicionados à fila de verificação de rótulos de classificação.
3. Conforme observado acima, essas são verificações dos rótulos de classificação descobertos na verificação inicial que o Cloud App Security executa para saber quais rótulos de classificação são usados em seu locatário. Rótulos externos, ou seja, rótulos de classificação definidos por alguém externo ao seu locatário, são adicionados à lista de rótulos de classificação. Se você não deseja verificar esses rótulos, marque a caixa de seleção **Somente arquivos de varredura para rótulos de classificação da Proteção de Informações do Azure deste locatário** (veja abaixo).
4. Depois que você habilitar a Proteção de Informações do Azure no Cloud App Security, todos os novos arquivos que forem adicionados ao Office 365 também serão verificados quanto aos rótulos de classificação.

## <a name="how-to-integrate-azure-information-protection-with-cloud-app-security"></a>Como integrar a Proteção de Informações do Azure ao Cloud App Security
  
### <a name="enable-azure-information-protection"></a>Habilitar a Proteção de Informações do Azure

Tudo o que você precisa fazer para integrar a Proteção de Informações do Azure ao Cloud App Security é: habilitar a verificação automática para habilitar a pesquisa de rótulos de classificação da Proteção de Informações do Azure nos arquivos do Office 365, sem precisar criar uma política. Depois de habilitar isso, se houver arquivos em seu ambiente de nuvem que estejam rotulados com rótulos de classificação da Proteção de Informações do Azure, eles serão exibidos no Cloud App Security.

Para permitir que o Cloud App Security verifique arquivos com a inspeção de conteúdo habilitada para rótulos de classificação:

1. No Cloud App Security, na engrenagem de configurações, selecione a página **Configurações gerais**.
2. Na Proteção de Informações do Azure, selecione **Examinar arquivos automaticamente para rótulos de classificação da Proteção de Informações do Azure**. 

Depois de habilitar a Proteção de Informações do Azure, os arquivos com rótulos de classificação serão exibidos e você poderá filtrá-los por rótulo no Cloud App Security.

 ![habilitar a Proteção de Informações do Azure](./media/enable-azip.png)

> [!NOTE] 
> A verificação automática não verificará arquivos existentes até que eles sejam modificados novamente. Para verificar rótulos de classificação em arquivos existentes da Proteção de Informações do Azure, você deve ter pelo menos um **Política de arquivo para inspeção de conteúdo**. Se não tiver nenhuma, crie uma nova **Política de arquivo**, exclua todos os filtros predefinidos, verifique a opção **Inspeção de conteúdo**. Em seguida, em **Inspeção de conteúdo**, clique em **Incluir arquivos que correspondem a uma expressão predefinida**, selecione qualquer valor predefinido e salve a política. Isso permitirá a inspeção de conteúdo, que detectará automaticamente os rótulos de classificação da Proteção de Informações do Azure.

### <a name="set-internal-and-external-tags"></a>Definir marcações internas e externas
Por padrão, o Cloud App Security examinará rótulos de classificação que foram definidos em sua organização, bem como aqueles externos que foram definidos por outras organizações. 

Para ignorar os rótulos de classificação definidos fora da sua organização, no portal do Cloud App Security, em **Configurações gerais** em **Configurações de segurança do Azure**, selecione **Ignorar rótulos de classificação da Proteção de Informações do Azure de outros locatários**.
 
![ignorar rótulos](./media/azip-ignore.png)

### <a name="control-file-exposure"></a>Controlar a exposição de arquivo
- Se esse for o documento rotulado com um rótulo de classificação da Proteção de Informações do Azure:

![tela de exemplo do azip](./media/azip-screen.png)

- Você poderá exibir esse arquivo no Cloud App Security, na página **Arquivos**, filtrando pelo rótulo de classificação:

![cas em comparação com o azip](./media/cas-compared-azip.png)

- Você pode obter mais informações sobre esses arquivos e seus rótulos de classificação na gaveta do arquivo.

- Na página **Arquivos**, clique no arquivo relevante para ver se ele tem rótulos de classificação:

![gaveta de arquivos](./media/azip-file-drawer.png)

- Você pode clicar no rótulo de classificação para exibir mais informações ou para ver a lista completa de rótulos de classificação:
 
![lista de rótulos](./media/azip-tags-list.png)

- Em seguida, você pode criar políticas de arquivo no Cloud App Security para controlar arquivos que são compartilhados inadequadamente e localizar arquivos rotulados que foram modificados recentemente.
- Além disso, você pode disparar alertas sobre atividades relacionadas a arquivos confidenciais.

![rótulos da Proteção de Informações do Azure no Cloud App Security](./media/azip-tags-in-cas.png)

> [!Note]
> Quando os rótulos do Azure Identity Protection estiverem desabilitados em um arquivo, os rótulos desabilitados serão exibidos como desabilitados no Cloud App Security. Os rótulos excluídos não serão exibidos.


**Política nº 1 – dados confidenciais externamente compartilhados no Box:**

1.  Criar uma política de arquivo.
2.  Definir o nome, severidade e categoria da política.
3.  Adicionar os seguintes filtros para localizar todos os dados confidenciais que são externamente compartilhados no Box:

![política de confidencialidade](./media/azip-confidentiality-policy.png) 

**Política nº 2 – dados restritos que recentemente foram modificados fora da pasta de Finanças no SharePoint:**

1.  Criar uma política de arquivo.
2.  Definir o nome, severidade e categoria da política.
3.  Adicionar os seguintes filtros para localizar todos os dados restritos que foram modificados recentemente e adicionar excluir a pasta Finanças na opção de seleção de pasta: 
 
![política de dados restritos](./media/azip-restricted-data-policy.png) 

Você também pode optar por definir alertas, notificação do usuário ou tomar ação imediata para essas políticas.
Saiba mais sobre [ações de governança](governance-actions.md).

Saiba mais sobre [Proteção de Informações do Azure](https://docs.microsoft.com/en-us/information-protection/understand-explore/what-is-information-protection) e confira o [tutorial de Início Rápido](https://docs.microsoft.com/en-us/information-protection/get-started/infoprotect-quick-start-tutorial) da Proteção de Informações do Azure.


## <a name="integration-with-azure-rights-management"></a>Integração com o Azure Rights Management

Sua organização deve ter o Azure Rights Management licenciado e ativado para integrar com o Cloud App Security.  Essas duas etapas separadas podem ser encontradas em [Ativando o Azure Rights Management](https://docs.microsoft.com/information-protection/deploy-use/activate-service).

O Cloud App Security atualmente oferece suporte apenas para o nível de proteção Genéricos. A proteção nativa para arquivos do Office, PDF e de imagem estará disponível em versões futuras. 

Esse recurso atualmente está disponível para arquivos que são armazenados no SharePoint Online e no OneDrive for Business. Mais aplicativos de nuvem serão compatíveis em versões futuras.

Depois que o Cloud App Security estiver conectado ao seu serviço do Office 365, será possível usar os recursos da integração com RMS que possibilitam proteger os documentos com RMS diretamente no portal do Cloud App Security, conforme explicado a seguir:

1. Na página **Arquivos**, selecione o arquivo que deseja proteger e clique nos três pontos no final da linha do arquivo. Em seguida, escolha **Proteger**. 
![proteger aplicativo](./media/protect-app.png)
2. Você será solicitado a escolher um dos modelos da sua organização para proteger o arquivo. Depois clique em **Proteger**. 
![modelo de proteção](./media/protect-template.png)
3. Depois de escolher um modelo e clicar em Proteger, o Cloud App Security aplicará o modelo e protegerá o arquivo original. O arquivo protegido terá o mesmo nome do arquivo original, mas com uma nova extensão de arquivo: ".pfile".
> [!NOTE]
>   Recomenda-se aplicar os modelos de RMS que abrangem toda a empresa em arquivos, para que todos os usuários da organização possam acessar esses arquivos, incluindo o proprietário original do arquivo. O proprietário do arquivo, a política de compartilhamento de arquivo e a lista de usuários que já têm acesso a ele não mudam quando o arquivo se torna protegido.

4. Se os usuários desejam acessar o arquivo protegido, eles precisam ter o aplicativo RMS sharing instalado em seus dispositivos. Para saber mais, veja a [Visão geral técnica e detalhes sobre proteção para o aplicativo de compartilhamento Microsoft Rights Management](https://docs.microsoft.com/information-protection/rms-client/sharing-app-admin-guide-technical).

5. Você pode reverter essa ação a qualquer momento no **Log de governança** clicando no botão **Reverter** no final da linha da ação Proteger executada anteriormente. 


Para obter mais informações sobre como o Cloud App Security e a Proteção de Informações do Azure funcionam juntos, consulte [Proteger dados contra erros de usuário](https://docs.microsoft.com/enterprise-mobility-security/solutions/protect-data-user-mistake)

 
## <a name="see-also"></a>Veja também  
[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  

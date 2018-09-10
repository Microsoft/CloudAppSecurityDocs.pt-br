---
title: Criar políticas para monitorar e proteger arquivos em seus aplicativos de nuvem | Microsoft Docs
description: Este tópico descreve o procedimento para configurar uma política de dados para monitorar e controlar os dados e arquivos em uso nos aplicativos de nuvem da sua organização.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/22/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: ac53fbd6-4d31-4bce-b2bc-9dc65ad83b3e
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 97eb234c1b5d7eef9f5b3789fde2279fd2e2dacb
ms.sourcegitcommit: 0ac08ca7b3140b79f1d36ff7152476c188fa12b3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44144288"
---
*Aplica-se ao: Microsoft Cloud App Security*

# <a name="file-policies"></a>Políticas de arquivos  
As políticas de arquivos permitem que você aplique uma ampla gama de processos automatizados, utilizando as APIs do provedor de nuvem. As políticas podem ser configuradas para fornecer verificações de conformidade contínuas, tarefas de Descoberta Eletrônica legais, DLP para conteúdo confidencial compartilhado publicamente e muito mais casos de uso.  <br></br>

O Cloud App Security pode monitorar qualquer tipo de arquivo com base em mais de 20 filtros de metadados (como por exemplo, nível de acesso e tipo de arquivo). 
 
**Tipos de arquivos com suporte** 

Mecanismos de DLP internos do Cloud App Security executam inspeção de conteúdo extraindo texto de todos os tipos de arquivo comuns (mais de 100), incluindo Office, Open Office, arquivos compactados, vários formatos de texto avançado, XML, HTML e muito mais.

O mecanismo combina três aspectos em cada política:  
  
-   Verificação de conteúdo com base em modelos predefinidos ou expressões personalizadas.  
  
-   Filtros de contexto, incluindo funções de usuário, metadados de arquivo, nível de compartilhamento, integração do grupo organizacional, contexto de colaboração e atributos personalizáveis adicionais.  
  
-   Ações automatizadas para governança e correção. Para obter mais informações, consulte [Control](control.md) (Controlar).  
  
Quando habilitada, a política examina continuamente seu ambiente de nuvem, identifica arquivos que correspondem aos filtros de contexto e conteúdo e aplica as ações automatizadas solicitadas. Essas políticas detectam e corrigem violações de informações em repouso ou quando novo conteúdo é criado. As políticas podem ser monitoradas usando alertas em tempo real ou relatórios gerados do console.  
  
A seguir estão exemplos das políticas de arquivos que podem ser criadas:  
  
-   Arquivos compartilhados publicamente: <br></br>
    Receba um alerta sobre qualquer arquivo na sua nuvem que esteja compartilhado publicamente selecionando todos os arquivos cujo nível de compartilhamento é público.  
  
-   O nome do arquivo compartilhado publicamente contém o nome da organização: <br></br> Receba um alerta sobre qualquer arquivo que contenha o nome da sua organização e esteja compartilhado publicamente. Selecione os arquivos com um nome de arquivo que contenha o nome da sua organização e que estejam compartilhados publicamente.  
  
-   Compartilhando com domínios externos:  <br></br>
    Receba um alerta sobre qualquer arquivo compartilhado com contas de propriedade de domínios externos específicos, por exemplo, com o domínio de um concorrente. Selecione o domínio externo com o qual você deseja limitar o compartilhamento.  
  
-   Arquivos compartilhados em quarentena não modificados durante o último período:  <br></br>
    Receba um alerta sobre arquivos compartilhados que ninguém modificou recentemente, para colocá-los em quarentena ou optar por ativar uma ação automatizada. Exclua todos os arquivos particulares que não foram modificados durante um intervalo de datas especificado. No G Suite, você pode optar por colocar esses arquivos em quarentena usando a caixa de seleção "Colocar arquivo em quarentena", na página de criação de política.  
  
-   Compartilhando com usuários não autorizados:  <br></br>
    Receba um alerta sobre os arquivos sendo compartilhados com um grupo de usuários não autorizados em sua organização. Selecione os usuários para os quais o compartilhamento é proibido.  
  
-   Extensão do arquivo confidencial:  <br></br>
    Receba um alerta sobre arquivos com extensões específicas com potencial de alta exposição. Selecione a extensão específica (por exemplo, crt para certificados) ou o nome do arquivo e exclua aqueles com o nível de compartilhamento privado.  
  
Para criar uma nova política de arquivos, siga este procedimento:  
  
1. No console, clique em **Controlar** seguido por **Políticas**.  
  
2. Clique em **Criar política** e selecione a política **Arquivo**.  
  
3. Atribua um nome e uma descrição à sua política. Se desejar, poderá baseá-la em um modelo. Para obter mais informações sobre modelos de política, consulte [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md).  
  
4. Forneça uma **Gravidade de política** à sua política. Se você configura o Cloud App Security para enviar notificações sobre correspondências de política para um nível de gravidade de política específico, isso é usado para determinar se essas correspondências disparam uma notificação.

5. Em **Categoria**, vincule a política ao tipo de risco mais apropriado. Este campo é somente informativo e ajuda você a pesquisar políticas e alertas específicos posteriormente, com base no tipo de risco.  O risco já pode estar pré-selecionado de acordo com a categoria para a qual você optou por criar a política. Por padrão, as políticas de arquivos são definidas para DLP.  
  
6. Para definir quais aplicativos descobertos disparam uma política, **Crie um filtro para os arquivos em que esta política atuará**. Restrinja os filtros de política até chegar ao conjunto mais preciso de arquivos nos quais você deseja agir. Seja o mais restritivo possível para evitar falsos positivos. Por exemplo, se você quiser remover permissões públicas, lembre-se de adicionar o filtro **Público**, se quiser remover um usuário externo, use o filtro "Externo" etc.  
   > [!NOTE] 
   > Ao usar os filtros de política, **contém** pesquisa somente palavras inteiras: separadas por vírgulas, pontos, espaços ou sublinhados. Por exemplo, se você pesquisar **malware** ou **vírus**, ele localizará virus_malware_file.exe, mas não localizará malwarevirusfile.exe. Se pesquisar **malware.exe**, você encontrará TODOS os arquivos com malware ou exe em seu nome de arquivo, enquanto se pesquisar **"malware.exe"** (com aspas), encontrará apenas arquivos que contêm exatamente "malware.exe". **É igual a** pesquisa apenas a cadeia de caracteres completa, por exemplo, se você pesquisar **malware.exe**, ele localizará malware.exe, mas não malware.exe.txt.  
7. Sob o primeiro filtro **Aplicar a**, selecione **pastas selecionadas** ou **todos os arquivos, excluindo pastas selecionadas** para Box, SharePoint, Dropbox, OneDrive, onde você pode aplicar a política a todas as políticas de arquivos a todos os arquivos no aplicativo ou a pastas específicas. Você é redirecionado para fazer logon no aplicativo de nuvem e, em seguida, adicionar as pastas relevantes.  

8. Sob o segundo filtro **Aplicar a**, selecione **todos os proprietários de arquivos**, **proprietários de arquivo de grupos selecionados** ou **todos os proprietários de arquivos, excluindo grupos selecionados** e, em seguida, selecione os grupos de usuários relevantes para determinar quais usuários e grupos devem ser incluídos na política.
  
9. Selecione o **Método de inspeção de conteúdo**. O DLP interno permite filtrar os arquivos pelo conteúdo. Para verificar arquivos quanto ao conteúdo, selecione **DLP Interno**. Depois que a inspeção estiver habilitada, você poderá optar por usar expressões predefinidas ou pesquisar outras expressões personalizadas, seja com uma subcadeia de caracteres ou uma [expressão regular](working-with-the-regex-engine.md) própria.  <br></br>

   Além disso, você pode especificar uma expressão regular para excluir um arquivo dos resultados. Isso será muito útil se você tiver um padrão de palavra-chave de classificação interno que você deseja excluir da política. <br></br> Você pode definir o número mínimo de violações de conteúdo que deseja corresponder antes de o arquivo ser considerado uma violação. Por exemplo, você poderá escolher 10 se quiser ser alertado sobre arquivos com pelo menos 10 números de cartão de crédito encontrados em seu conteúdo.  <br></br>
   Quando o conteúdo é comparado com a expressão selecionada, o texto de violação é substituído por caracteres "X". Por padrão, as violações são mascaradas e mostradas em seu contexto, exibindo 100 caracteres antes e após a violação. Os números no contexto da expressão são substituídos por caracteres "#" e nunca são armazenados no Cloud App Security. Você pode selecionar a opção para **Remover a máscara dos últimos quatro caracteres de uma violação** para remover a máscara dos últimos quatro caracteres da própria violação. É necessário definir quais tipos de dados a expressão regular pesquisa: conteúdo, metadados e/ou nome do arquivo. Por padrão, ela pesquisa o conteúdo e os metadados. Você precisa selecionar pelo menos um tipo de dados a pesquisar ou a expressão regular não funcionará e a política não poderá ser criada. 
  
10. Escolha as ações de **Governança** que você deseja que o Cloud App Security realize quando uma correspondência for detectada.  
  
11. Depois de criar sua política, você pode exibi-la na guia **Política de arquivos**. Você sempre pode editar uma política, calibrar seus filtros ou alterar as ações automatizadas. A política é habilitada automaticamente no momento da criação e inicia a verificação de seus arquivos de nuvem imediatamente.  Tenha muito cuidado ao definir as ações de controle, elas podem causar uma perda irreversível de permissões de acesso para seus arquivos. É recomendável restringir os filtros para representar exatamente os arquivos nos quais você deseja agir, usando vários campos de pesquisa. Quanto mais restritos forem os filtros, melhor. Para obter orientação, você pode usar o botão **Editar e visualizar resultados** na seção Filtros.  
  
    ![editar a política do arquivo e visualizar os resultados](./media/file-policy-edit-and-preview-results.png "editar a política do arquivo e visualizar os resultados")  
  
12. Para exibir correspondências de política de arquivo, os arquivos com suspeita de violar a política, clique em **Controle** e **Políticas**. Filtre os resultados para exibir somente as políticas do arquivo usando o filtro **Tipo** na parte superior. Para obter mais informações sobre as correspondências para cada política, clique em uma política. Isso exibe os arquivos de Correspondência agora para a política. Clique na guia **Histórico** para ver um histórico de até seis meses anteriores de arquivos que correspondem à política.     
  
## <a name="file-policy-reference"></a>Referência de política de arquivos  
Esta seção fornece detalhes de referência sobre as políticas, fornecendo explicações sobre cada tipo de política e os campos que podem ser configurados para cada política. 
  
Uma **Política de arquivos** é uma política baseada em API que permite que você controle o conteúdo da sua organização na nuvem, considerando mais de 20 filtros de metadados (incluindo o nível de compartilhamento e de proprietário), bem como resultados de inspeção de conteúdo. Com base nos resultados de política, as ações de governança podem ser aplicadas. O mecanismo de inspeção de conteúdo pode ser estendido por meio de mecanismos de DLP de terceiros, bem como soluções antimalware.  
  
Cada política é composta pelas seguintes partes:  
  
-   Filtros de arquivos – permitem criar condições granulares com base nos metadados.  
  
-   Inspeção de conteúdo – permite restringir a política, com base nos resultados do mecanismo de DLP. É possível incluir uma expressão personalizada ou uma expressão predefinida. As exclusões podem ser definidas, e é possível escolher o número de correspondências. Também é possível usar a anonimização para mascarar o nome de usuário. 
  
-   Ações – a política fornece a um conjunto de ações de governança que podem ser aplicadas automaticamente quando violações são encontradas.  Essas são divididas em ações de colaboração, ações de segurança e ações de investigação.

-   Extensões  
   
    -  A inspeção de conteúdo pode ser executada por meio de mecanismos de terceiros para recursos antimalware ou de DLP aprimorados.  

  
## <a name="see-also"></a>Consulte Também  
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
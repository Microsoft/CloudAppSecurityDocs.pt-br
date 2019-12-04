---
title: Entendendo os dados de arquivo e os filtros disponíveis no Cloud App Security
description: Este artigo de referência fornece informações sobre os tipos e filtros de arquivo usados pelo Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagirn
ms.date: 7/7/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 12522fbcdade562d9809ae81efd3d4a2c758033c
ms.sourcegitcommit: 7c93b6f93d2699d466b172590710ed01697bbdad
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74719390"
---
# <a name="files"></a>Arquivos

*Aplica-se ao: Microsoft Cloud App Security*

Para oferecer proteção de dados, o Microsoft Cloud App Security proporciona visibilidade de todos os arquivos de seus aplicativos conectados. Depois que você conectar o Microsoft Cloud App Security a um aplicativo usando o conector de aplicativos, o Microsoft Cloud App Security examina todos os arquivos, por exemplo, todos os arquivos armazenados no OneDrive e no Salesforce. Em seguida, o Cloud App Security examina novamente cada arquivo sempre que ele é modificado – a modificação pode ser em conteúdo, metadados ou permissões de compartilhamento. Os tempos de verificação dependem do número de arquivos armazenados em seu aplicativo. Também é possível usar a página **Arquivos** para filtrar os arquivos a fim de investigar qual tipo de dados está salvo em seus aplicativos de nuvem.

## <a name="file-filter-examples"></a>Exemplos de filtros de arquivo

Por exemplo, use a página **Arquivos** para proteger arquivos compartilhados externamente rotulados como **confidenciais** da seguinte maneira: depois de conectar um aplicativo ao Cloud App Security, integre-o à Proteção de Informações do Azure. Em seguida, na página **Arquivos**, filtre os arquivos rotulados como **confidenciais** e exclua seu domínio no filtro **Colaboradores**. Se você observar que há arquivos confidenciais compartilhados fora de sua organização, crie uma política de arquivo para detectá-los. Você pode aplicar ações de governança automáticas a esses arquivos, como **Remover colaboradores externos** e **Enviar resumo de correspondência de política para o proprietário do arquivo** para evitar a perda de dados para sua organização.

![Filtro de arquivo confidencial](media/file-filter-confidential.png)

Veja outro exemplo de como você pode usar a página **Arquivos**. Garanta que ninguém em sua organização esteja compartilhando arquivos pública ou externamente que não foram modificados nos últimos seis meses: conecte um aplicativo ao Cloud App Security e acesse a página **Arquivos**. Filtre os arquivos cujo nível de acesso é **Externo** ou **Público** e defina a data da **Última modificação** para seis meses atrás. Crie uma política de arquivo que detecte esses arquivos públicos obsoletos clicando em **Nova política da pesquisa**. Aplique ações de governança automática a eles, como **Remover usuários externos**, para impedir a perda de dados em sua organização.

![Filtro de arquivo obsoleto externo](media/file-example-stale-external.png)

O filtro básico fornece excelentes ferramentas para começar a usar a filtragem de seus arquivos.

![filtro básico do log arquivos](media/file-log-filter-basic-1.png)

Para analisar arquivos mais específicos, você pode expandir o filtro básico clicando em Avançado.

![filtro avançado do log arquivo](media/file-log-filter-advanced-1.png)

## <a name="Filefilters"></a> Filtros de arquivos

O Cloud App Security pode monitorar qualquer tipo de arquivo com base em mais de 20 filtros de metadados (como por exemplo, nível de acesso e tipo de arquivo).

Os mecanismos de DLP internos do Cloud App Security executam a inspeção de conteúdo extraindo o texto de tipos de arquivos comuns. Alguns dos tipos de arquivos incluídos são PDF, arquivos do Office, RTF, HTML e arquivos de código.

Abaixo está uma lista de filtros de arquivos que podem ser aplicados. Para fornecer uma ferramenta avançada para a criação de políticas, a maioria dos filtros dá suporte a vários valores e a um valor NOT.

> [!NOTE]
> Ao usar os filtros de política de arquivos, **Contém** pesquisará somente **palavras inteiras** – separadas por vírgulas, pontos, espaços ou sublinhados a serem pesquisados.
>
> - Espaços entre palavras funcionam como OR, por exemplo, se você pesquisar **malware** **virus**, serão encontrados todos os arquivos com "malware" ou "virus" no nome, portanto, encontrará malware-virus.exe e virus.exe.
> - Se você desejar pesquisar uma cadeia de caracteres, coloque as palavras entre aspas. Isso funciona como AND, por exemplo, se você pesquisar **"malware"** **"virus"** , será encontrado virus_malware_file.exe, mas não será encontrado malwarevirusfile.exe nem malware.exe. No entanto, será pesquisada a cadeia de caracteres exata. Se você pesquisar **"malware virus"** , não será encontrado **"virus"** nem **"virus_malware"** .
>
> **É igual a** pesquisará apenas a cadeia de caracteres completa, por exemplo, se você pesquisar **malware.exe**, ele localizará malware.exe, mas não malware.exe.txt.

- **Nível de acesso** – nível de acesso de compartilhamento: público, externo, interno ou particular.  Para obter mais informações sobre arquivos externos, consulte [Configuração geral, Configurar o portal](getting-started-with-cloud-app-security.md)

    - **Internos** – todos os arquivos que estão dentro dos domínios Internos definidos em [Configuração geral](General-setup.md).
    - **Externos** – todos os arquivos salvos em locais que não estão dentro dos domínios internos definidos.
    - **Compartilhados** – arquivos que têm o nível de compartilhamento acima de particular. A opção Compartilhados inclui:
        - Compartilhamento interno – arquivos compartilhados nos domínios internos.
        - Compartilhamento externo – arquivos compartilhados em domínios que não estão listados nos domínios internos.
        - Públicos com um link – arquivos que podem ser compartilhados com qualquer pessoa por meio de um link.
        - Públicos – arquivos que podem ser encontrados com pesquisas na Internet.

      > [!NOTE]
      > Os arquivos compartilhado em seus aplicativos de armazenamento conectados por usuários externos são manipulados como se segue pelo Cloud App Security:
      >
      > - **OneDrive:** o OneDrive atribui um usuário interno como o proprietário de qualquer arquivo colocado no seu OneDrive por um usuário externo. Como esses arquivos são considerados como pertencentes à sua organização, O Cloud App Security os examina e aplica políticas como acontece com qualquer outro arquivo no seu OneDrive.
      > - **Google Drive:** o Google Drive os considera como pertencentes ao usuário externo e, devido às restrições legais dos arquivos e dados que não são de propriedade da sua organização, o Cloud App Security não tem acesso a esses arquivos.
      > - **Box:** como o Box considera arquivos de propriedade externa como informações confidenciais, os Administradores Globais do Box não conseguem ver seu conteúdo. Por esse motivo, o Cloud App Security não tem acesso a esses arquivos.
      > - **Dropbox:** como o Dropbox considera arquivos de propriedade externa como informações confidenciais, os Administradores Globais do Dropbox não conseguem ver seu conteúdo. Por esse motivo, o Cloud App Security não tem acesso a esses arquivos.

- **Aplicativo** – pesquise apenas arquivos dentro desses aplicativos.

- **Colaboradores** – Inclua/exclua grupos de colaboradores específicos.

    - **Qualquer um do domínio** – se um usuário desse domínio tiver acesso ao arquivo.

    - **Todo o domínio** – se todo o domínio tiver acesso ao arquivo.

    - **Grupos** – se um grupo específico tiver acesso ao arquivo. Os grupos podem ser importados do Active Directory, aplicativos de nuvem ou criados manualmente no serviço.

    - **Usuários** – determinado conjunto de usuários que podem ter acesso ao arquivo.

- **Criado** – hora da criação do arquivo. O filtro dá suporte a antes/após datas e a um intervalo de datas.

- **Extensão** – concentre-se em extensões de arquivo específicas. Por exemplo, todos os arquivos que são executáveis (exe).

- **ID de Arquivo** – pesquisa IDs de arquivo específicas. IDs de Arquivo é um recurso avançado que permite que você acompanhe determinados arquivos de alto valor sem uma dependência do proprietário, da localização ou do nome.

- **Nome de arquivo** – nome de arquivo ou subcadeia de caracteres do nome, conforme definido no aplicativo na nuvem, por exemplo, todos os arquivos com uma senha no nome.

- **Rótulo de classificação** – pesquise arquivos com conjunto de marcas específicas. Rótulos são:
    - **Marcas da Proteção de Informações do Azure** – exige a integração com a Proteção de Informações do Azure.
    - **Marcas do Cloud App Security** – fornece mais insights sobre os arquivos examinados. Para cada arquivo examinado pelo DLP do Cloud App Security, você pode saber se a inspeção foi bloqueada devido ao arquivo estar criptografado ou corrompido. Por exemplo, você pode configurar políticas para alertá- e arquivos protegidos por senha em quarentena que são compartilhados externamente.
        - **Azure RMS criptografado** – arquivos cujo conteúdo não foi inspecionado porque têm um conjunto de criptografia do Azure RMS.
        - **Criptografado por senha** – arquivos cujo conteúdo não foi inspecionado porque são protegidos por senha pelo usuário.
        - **Arquivo corrompido** – arquivos cujo conteúdo não foi inspecionado porque seu conteúdo não pôde ser lido.

- **Tipo de arquivo** – o Cloud App Security usa o tipo MIME recebido do serviço e examina o arquivo para determinar o verdadeiro tipo de arquivo. Essa verificação destina-se a arquivos que são relevantes para a verificação de dados (documentos, imagens, apresentações, planilhas, arquivos de texto e zip/arquivos). O filtro funciona por tipo de arquivo/pasta. Por exemplo, Todas as pastas que são... ou Todos os arquivos de planilha que são...

    ![policy_file de filtros de lixo](media/policy_file-filters-trash.png "lixeira de filtros policy_file")

- **Na lixeira** – exclui/inclui arquivos na pasta da lixeira. Esses arquivos ainda podem ser compartilhados e representam um risco.

- **Última modificação** – hora da modificação do arquivo. O filtro dá suporte a antes e após datas, intervalo de datas e expressões de tempo relativas. Por exemplo, todos os arquivos que não foram modificados nos últimos seis meses.

- **Política correspondente** – os arquivos correspondentes a uma política ativa do Cloud App Security.

- **Tipo MIME** – verificação de tipo MIME do arquivo, aceita texto livre.

- **Proprietário** – inclua/exclua proprietários de arquivos específicos. Por exemplo, acompanhar todos os arquivos compartilhados por rogue_employee_ #100.

- **UO do proprietário** – inclua ou exclua proprietários de arquivos que pertencem a determinado grupo organizacional. Por exemplo, todos os arquivos públicos, exceto arquivos compartilhados por EMEA_marketing. Aplica-se somente aos arquivos armazenados no Google Drive.

- **Pasta pai** – inclua ou exclua arquivos com base na pasta pai. Por exemplo, todos os arquivos compartilhados publicamente, exceto os arquivos nesta pasta.

- **Em quarentena** – o arquivo foi colocado em quarentena pelo serviço? Por exemplo, mostrar todos os arquivos que estão em quarentena.

Defina também a política a ser executada em arquivos específicos definindo o filtro **Aplicar a**. Filtre para **todos os arquivos**, **pastas selecionadas** ou **todos os arquivos, exceto as pastas selecionadas**. Em seguida, selecione os arquivos ou as pastas relevantes.

![aplicar ao filtro](media/apply-to-filter.png "aplicar para filtrar")
<!--
>[!NOTE]
> If at any point you want to clear the filters, you can do so by clicking the clear filters icon ![clear filters icon](media/clear-filters.png).
-->

## <a name="authorizing-files"></a>Autorizando arquivos

Depois que Cloud App Security identificar arquivos como apresentando um risco de malware ou DLP, recomendamos que você investigue os arquivos. Se você determinar que os arquivos são seguros, poderá autorizá-los. Autorizar um arquivo o remove do relatório de detecção de malware e suprime correspondências futuras nele.

### <a name="to-authorize-files"></a>Para autorizar arquivos

1. Em Cloud App Security, clique em **controle** e em **políticas**.
1. Na lista de políticas, na linha na qual a política que disparou a investigação aparece, na coluna **contagem** , clique no link correspondências.

    > [!TIP]
    > Você pode filtrar a lista de políticas por tipo. A tabela a seguir lista, por tipo de risco, qual tipo de filtro deve ser usado:
    >
    > | Tipo de risco | Tipo de filtro |
    > | --- | --- |
    > | DLP | Política de arquivos |
    > | Malware | Política de detecção de malware |

1. Na lista de arquivos correspondentes, na linha na qual o arquivo em investigação aparece, clique em **autorizar**.

## <a name="working-with-the-file-drawer"></a>Trabalhando com a Gaveta de arquivos

Exiba mais informações sobre cada arquivo clicando no próprio arquivo no log de arquivo. Clicar abre a **gaveta de arquivos** que fornece as seguintes ações adicionais que você pode executar no arquivo:

- **URL** – leva você para a localização do arquivo.
- **Identificadores de arquivo** – abre um pop-up com detalhes de dados brutos sobre o arquivo, incluindo a ID do arquivo e as chaves de criptografia.
- **Proprietário** – exiba a página de usuário para o proprietário desse arquivo.
- **Políticas correspondentes** – veja uma lista de políticas com as quais o arquivo é correspondente.
- **Rótulo de classificação** – exiba a lista de rótulos de classificação da Proteção de Informações do Azure encontrados neste arquivo. Em seguida, você poderá filtrar por todos os arquivos que corresponderem a esse rótulo.

Os campos da gaveta Arquivos fornecem links contextuais para arquivos adicionais e análises detalhadas que você talvez queira executar diretamente na gaveta. Por exemplo, se você mover o cursor ao lado do campo **Proprietário**, poderá usar o ícone "adicionar ao filtro" ![adicionar ao filtro](media/add-to-filter-icon.png) para adicionar o proprietário imediatamente ao filtro da página atual. Você também pode usar o ícone de engrenagem de configurações ![ícone de configurações](media/contextual-settings-icon.png) que aparece diretamente na página de configurações necessária para alterar a configuração de um dos campos, tais como **Rótulos de classificação**.

![Gaveta de arquivos](media/file-drawer.png "Gaveta de arquivos")

Para obter uma lista de ações de governança disponíveis, consulte [Ações de governança de arquivo](governance-actions.md#file-governance-actions).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
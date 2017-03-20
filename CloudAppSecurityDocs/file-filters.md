---
title: "Entendendo os dados e filtros de arquivos disponíveis no Cloud App Security | Microsoft Docs"
description: "Este tópico de referência fornece informações sobre os tipos e filtros de arquivos usados pelo Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/12/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: cadcd6db-05b2-4974-91fe-cfac3d57aecd
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 81330b5333050bea2352f0907ac5c83d71af14bf
ms.sourcegitcommit: b840b945b270e616560f565bcc6590dd68ad5ebd
translationtype: HT
---
# <a name="files"></a>Arquivos


Para oferecer proteção de dados, o Cloud App Security proporciona visibilidade de todos os arquivos de seus aplicativos conectados. Depois que você conectar o Cloud App Security a um aplicativo usando o conector de aplicativos, o Cloud App Security examina todos os arquivos, por exemplo, todos os arquivos armazenados no OneDrive e no Salesforce. Assim, o Cloud App Security examinará novamente cada arquivo sempre que ele for modificado – a modificação pode ser em conteúdo, metadados ou permissões de compartilhamento. Os tempos de verificação dependem do número de arquivos armazenados em seu aplicativo. Também é possível usar a página **Arquivos** para filtrar os arquivos a fim de investigar qual tipo de dados está salvo em seus aplicativos de nuvem. 

Por exemplo, é possível usar a página **Arquivos** para proteger arquivos compartilhados externamente rotulados como **confidenciais** da seguinte maneira: depois de conectar um aplicativo ao Cloud App Security, é possível integrar-se à Proteção de Informações do Azure. Em seguida, na página **Arquivos**, filtre os arquivos rotulados como **confidenciais**. Se você perceber que há arquivos **confidenciais** compartilhados fora da sua organização aplicando o filtro **Colaboradores** para excluir seu domínio, você poderá criar uma política de arquivo que detecta arquivos **confidenciais** que têm níveis de acesso incorretos aplicados a eles e aplicar ações de governança automática, como **Remover colaboradores externos** e **Enviar resumo de correspondência de política ao proprietário do arquivo** para evitar a perda de dados para sua organização.

 ![Filtro de arquivo confidencial](media/file-filter-confidential.png)

Veja outro exemplo de como você pode usar a página **Arquivos**. Para verificar que ninguém na sua organização esteja compartilhando externa ou publicamente arquivos que não foram modificados nos últimos seis meses: depois de conectar um aplicativo ao Cloud App Security, na página **Arquivos**, filtre os arquivos cujo nível de acesso é **Externo** ou **Público** e defina a data da **Última modificação** para seis meses atrás. Você pode criar uma política de arquivo que detecta os arquivos públicos obsoletos clicando em **Nova política de pesquisa** e aplicar ações de controle automático a eles, como **Remover usuários externos** para evitar a perda de dados para sua organização.

 ![Filtro de arquivo obsoleto externo](media/file-example-stale-external.png)

O filtro básico fornece excelentes ferramentas para começar a usar a filtragem de seus arquivos.

 ![filtro básico do log arquivos](media/file-log-filter-basic.png)

Para analisar arquivos mais específicos, você pode expandir o filtro básico clicando em Avançado.

 ![filtro avançado do log arquivo](media/file-log-filter-advanced.png)
 
###  <a name="Filefilters"></a> Filtros de arquivos 
 
O Cloud App Security pode monitorar qualquer tipo de arquivo com base em mais de 20 filtros de metadados (como por exemplo, nível de acesso e tipo de arquivo). 
 
Os mecanismos de DLP internos do Cloud App Security executam inspeção de conteúdo extraindo texto de tipos de arquivos comuns (PDF, arquivo do Office, RTF, HTML, arquivos de código, etc.).

Abaixo está uma lista de filtros de arquivos que podem ser aplicados. A maioria dos filtros dá suporte a vários valores, bem como NOT, para fornecer uma ferramenta muito poderosa para a criação de políticas.  
> [!NOTE] 
> Ao usar os filtros de política de arquivos, **Contém** pesquisará somente **palavras inteiras** – separadas por vírgulas, pontos, espaços ou sublinhados a serem pesquisados. 
> - Espaços entre palavras funcionam como OR, por exemplo, se você pesquisar **malware** **virus**, serão encontrados todos os arquivos com "malware" ou "virus" no nome, portanto, encontrará malware-virus.exe e virus.exe.  
> - Se você desejar pesquisar uma cadeia de caracteres, coloque as palavras entre aspas. Isso funciona como AND, por exemplo, se você pesquisar **"malware"** **"virus"**, será encontrado virus_malware_file.exe, mas não será encontrado malwarevirusfile.exe nem malware.exe. No entanto, será pesquisada a cadeia de caracteres exata. Se você pesquisar **"malware virus"**, não será encontrado **"virus"** nem **"virus_malware"**.

>**É igual a** pesquisará apenas a cadeia de caracteres completa, por exemplo, se você pesquisar **malware.exe**, ele localizará malware.exe, mas não malware.exe.txt. 

-   Nível de acesso – nível de acesso de compartilhamento, público, externo, interno ou privado.  Para obter mais informações sobre arquivos externos, consulte [Configuração geral, configuração do portal](getting-started-with-cloud-app-security.md) Internos são todos os arquivos dentro dos domínios Internos definidos na [Configuração geral](General-setup.md). Externos são arquivos salvos em locais que não estão dentro dos domínios internos que você definiu. Compartilhados são arquivos que têm nível de compartilhamento acima de particular (arquivos compartilhados em seus domínios internos), compartilhamento externo (arquivos compartilhados em domínios que não estão listados em seus domínios internos), públicos com um link (arquivos que podem ser compartilhados com qualquer pessoa por meio de um link) e públicos (arquivos que podem ser encontrados por pesquisas da Internet). 

> [!NOTE]
>  Os arquivos compartilhado em seus aplicativos de armazenamento conectados por usuários externos são manipulados como se segue pelo Cloud App Security:
> - **OneDrive:** o OneDrive atribui um usuário interno como o proprietário de qualquer arquivo colocado no seu OneDrive por um usuário externo. Como esses arquivos são considerados como pertencentes à sua organização, O Cloud App Security os examina e aplica políticas como acontece com qualquer outro arquivo no seu OneDrive.
> - **Google Drive:** o Google Drive os considera como pertencentes ao usuário externo e, devido às restrições legais dos arquivos e dados que não são de propriedade da sua organização, o Cloud App Security não tem acesso a esses arquivos.
> - **Box:** como o Box considera arquivos de propriedade externa como informações confidenciais, os Administradores Globais do Box não conseguem ver seu conteúdo. Por esse motivo, o Cloud App Security não tem acesso a esses arquivos. 
> - **Dropbox:** como o Dropbox considera arquivos de propriedade externa como informações confidenciais, os Administradores Globais do Box não conseguem ver seu conteúdo. Por esse motivo, o Cloud App Security não tem acesso a esses arquivos.

-   Aplicativo – pesquisa apenas arquivos dentro desses aplicativos.  
  
-   Colaboradores – Inclui/exclui grupos de colaboradores específicos.  
  
    -   Qualquer um do domínio – se qualquer usuário desse domínio tiver acesso ao arquivo.  
  
    -   Domínio inteiro – se todo o domínio tiver acesso ao arquivo.  
  
    -   Grupos – se um grupo específico tiver acesso ao arquivo. Os grupos podem ser importados do Active Directory, aplicativos de nuvem ou criados manualmente no serviço.  
  
    -   Usuários – determinado conjunto de usuários que podem ter acesso ao arquivo.  
  
-   Criado – hora da criação do arquivo. O filtro dá suporte a datas antes/depois, bem como a intervalo de datas.  
  
-   Extensão – Foco em extensões de arquivo específicas, como por exemplo, todos os arquivos que são executáveis (exe).  
  
-   ID do arquivo – Pesquisa por IDs de arquivo específicas. Esse é um recurso avançado que permite que você acompanhe certos arquivos de alto valor sem depender de seu proprietário/local/nome.  
  
-   Nome do arquivo – nome do arquivo ou subcadeia de caracteres do nome conforme definido no aplicativo de nuvem, por exemplo, todos os arquivos com uma senha em seu nome.   
  
-   Rótulo de classificação – pesquise arquivos com marcas específicas definidas pela Proteção de Informações do Azure. Isso exige integração à Proteção de Informações do Azure.

-   Tipo de arquivo – O Cloud App Security usa o tipo MIME recebido do serviço e examina o arquivo para determinar o verdadeiro tipo de arquivo. Observe que se essa verificação destina-se a arquivos que são relevantes para a verificação de dados (documentos, imagens, apresentações, planilhas, arquivos de texto e zip/arquivo morto). O filtro funciona por tipo de arquivo/pasta, por exemplo, todas as pastas que são... ou todos os arquivos de planilha que são...


 ![lixeira de filtros policy_file](./media/policy_file-filters-trash.png "lixeira de filtros policy_file")  

  
-   Na lixeira – Exclui/inclui arquivos na pasta da lixeira. Esses arquivos ainda podem ser compartilhados e representam um risco.  
  
-   Última modificação – hora da modificação do arquivo. O filtro dá suporte a datas antes/depois de, intervalo de datas e expressões de tempo relativo, como por exemplo, todos os arquivos que não foram modificados nos últimos seis meses.  

-   Política correspondente — os arquivos que são correspondentes por uma política ativa do Cloud App Security.

-   Tipo MIME – verificação de tipo MIME do arquivo, aceita texto livre.  
  
-   Proprietário ‑ Inclui/exclui os proprietários de arquivos específicos, por exemplo, rastrear todos os arquivos compartilhados por rogue_employee_#100.  
  
-   UO do Proprietário – Inclui/exclui proprietários de arquivos que pertencem a um determinado grupo organizacional, por exemplo, todos os arquivos públicos, exceto aqueles compartilhados por EMEA_marketing.  
  
-   Pasta pai – Inclui/exclui com base na pasta pai, por exemplo, todos os arquivos compartilhados publicamente, exceto arquivos nesta pasta.  
  
-   Em quarentena – o arquivo foi colocado em quarentena pelo serviço, por exemplo, mostre-me todos os arquivos que estão em quarentena.  
  
Você também pode definir a política para ser executada em arquivos específicos definindo o filtro **Aplicar a** como Todos os arquivos, Pastas selecionadas ou todos os arquivos, exceto as pastas selecionadas e selecionar os arquivos ou pastas que são relevantes.  
  
![aplicar para filtrar](./media/apply-to-filter.png "aplicar para filtrar")  
  
## <a name="working-with-the-file-drawer"></a>Trabalhando com a Gaveta de arquivos

Você pode exibir mais informações sobre cada arquivo, clicando no próprio Arquivo no Log de arquivo. Isso abre a Gaveta de arquivos que fornece as seguintes ações adicionais que você pode executar no arquivo:

- URL: leva ao local do arquivo.
- Identificadores de arquivo: clicar em Identificadores de arquivo abre um pop-up com detalhes de dados brutos sobre o arquivo, incluindo a ID do arquivo e as chaves de criptografia.
- Proprietário: clique no proprietário para exibir a página de usuário do proprietário deste arquivo.
- Políticas correspondentes: clique no link Políticas correspondentes para ver uma lista de políticas correspondentes a este arquivo.
- Rótulo de classificação: clique no rótulo de classificação para exibir a lista de rótulos de classificação da Proteção de Informações do Azure encontrados neste arquivo. Em seguida, você poderá filtrar por todos os arquivos que corresponderem a esse rótulo.    

![Arquivador](./media/file-drawer.png "Arquivador")  
  
Para obter uma lista de ações de governança disponíveis, consulte [Ações de governança de arquivo](governance-actions.md#file-governance-actions).

## <a name="see-also"></a>Veja também  
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
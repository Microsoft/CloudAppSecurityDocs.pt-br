---
title: Arquivos | Microsoft Docs
description: "Este tópico de referência fornece informações sobre os tipos e filtros de arquivos usados pelo Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/27/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: cadcd6db-05b2-4974-91fe-cfac3d57aecd
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: bf862116fb4db1d4a50c25497d72634a97bb3a80
ms.openlocfilehash: 8fca376e5d414192bdb7c99a7741c97ebcaf3892


---

# <a name="files"></a>Arquivos

O log Arquivos pode ser filtrado para permitir que você encontre arquivos específicos. O filtro básico fornece excelentes ferramentas para começar a usar a filtragem de seus arquivos.

 ![filtro básico do log arquivos](media/file-log-filter-basic.png)

Para analisar arquivos mais específicos, você pode expandir o filtro básico clicando em Avançado.

 ![filtro avançado do log arquivo](media/file-log-filter-advanced.png)
 
###  <a name="a-namefilefiltersa-file-filters"></a><a name="Filefilters"></a> Filtros de arquivos 
 
O Cloud App Security pode monitorar qualquer tipo de arquivo com base em mais de 20 filtros de metadados (como por exemplo, nível de acesso e tipo de arquivo). 
 
Os mecanismos de DLP internos do Cloud App Security executam inspeção de conteúdo extraindo texto de tipos de arquivos comuns (PDF, arquivo do Office, RTF, HTML, arquivos de código, etc.).

Abaixo está uma lista de filtros de arquivos que podem ser aplicados. A maioria dos filtros dá suporte a vários valores, bem como NOT, para fornecer uma ferramenta muito poderosa para a criação de políticas.  
> [!NOTE] 
> Ao usar os filtros de política de arquivos, **Contém** pesquisará somente palavras inteiras: separadas por vírgulas, pontos, espaços ou sublinhados. Colocar palavras entre aspas funciona como AND, portanto, por exemplo, se você pesquisar **"malware"** **"virus"**, ele encontrará virus_malware_file.exe, mas não encontrará malwarevirusfile.exe nem malware.exe. Espaços entre palavras funcionam como OR, por exemplo, se você pesquisar **malware** **virus** ele encontrará todos os arquivos com malware ou virus no nome, portanto, encontrará malware-virus.exe e virus.exe.   **É igual a** pesquisará apenas a cadeia de caracteres completa, por exemplo, se você pesquisar **malware.exe**, ele localizará malware.exe, mas não malware.exe.txt. 

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
  
-   Marca de arquivo — pesquise arquivos com marcas específicas definidas pela Proteção de Informações do Azure. Isso exige integração à Proteção de Informações do Azure.

-   Tipo de arquivo – O Cloud App Security usa o tipo MIME recebido do serviço e examina o arquivo para determinar o verdadeiro tipo de arquivo. Observe que se essa verificação destina-se a arquivos que são relevantes para a verificação de dados (documentos, imagens, apresentações, planilhas, arquivos de texto e zip/arquivo morto). O filtro funciona por tipo de arquivo/pasta, por exemplo, todas as pastas que são... ou todos os arquivos de planilha que são...


 ![lixeira de filtros policy_file](./media/policy_file-filters-trash.png "policy_file filters trash")  

  
-   Na lixeira – Exclui/inclui arquivos na pasta da lixeira. Esses arquivos ainda podem ser compartilhados e representam um risco.  
  
-   Última modificação – hora da modificação do arquivo. O filtro dá suporte a datas antes/depois de, intervalo de datas e expressões de tempo relativo, como por exemplo, todos os arquivos que não foram modificados nos últimos seis meses.  

-   Política correspondente — os arquivos que são correspondentes por uma política ativa do Cloud App Security.

-   Tipo MIME – verificação de tipo MIME do arquivo, aceita texto livre.  
  
-   Proprietário ‑ Inclui/exclui os proprietários de arquivos específicos, por exemplo, rastrear todos os arquivos compartilhados por rogue_employee_#100.  
  
-   UO do Proprietário – Inclui/exclui proprietários de arquivos que pertencem a um determinado grupo organizacional, por exemplo, todos os arquivos públicos, exceto aqueles compartilhados por EMEA_marketing.  
  
-   Pasta pai – Inclui/exclui com base na pasta pai, por exemplo, todos os arquivos compartilhados publicamente, exceto arquivos nesta pasta.  
  
-   Em quarentena – o arquivo foi colocado em quarentena pelo serviço, por exemplo, mostre-me todos os arquivos que estão em quarentena.  
  
Você também pode definir a política para ser executada em arquivos específicos definindo o filtro **Aplicar a** como Todos os arquivos, Pastas selecionadas ou todos os arquivos, exceto as pastas selecionadas e selecionar os arquivos ou pastas que são relevantes.  
  
![aplicar para filtrar](./media/apply-to-filter.png "apply to filter")  
  
## <a name="working-with-the-file-drawer"></a>Trabalhando com a Gaveta de arquivos

Você pode exibir mais informações sobre cada arquivo, clicando no próprio Arquivo no Log de arquivo. Isso abre a Gaveta de arquivos que fornece as seguintes ações adicionais que você pode executar no arquivo:

- URL: leva ao local do arquivo.
- Identificadores de arquivo: clicar em Identificadores de arquivo abre um pop-up com detalhes de dados brutos sobre o arquivo, incluindo a ID do arquivo e as chaves de criptografia.
- Proprietário: clique no proprietário para exibir a página de usuário do proprietário deste arquivo.
- Políticas correspondentes: clique no link Políticas correspondentes para ver uma lista de políticas correspondentes a este arquivo.
- Rótulo de classificação: clique no rótulo de classificação para exibir a lista de rótulos de classificação da Proteção de Informações do Azure encontrados neste arquivo. Em seguida, você poderá filtrar por todos os arquivos que corresponderem a esse rótulo.    

![Gaveta de arquivos](./media/file-drawer.png "File drawer")  
  
Para obter uma lista de ações de governança disponíveis, consulte [Ações de governança de arquivo](governance-actions.md#file-governance-actions).

## <a name="see-also"></a>Veja também  
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Nov16_HO5-->



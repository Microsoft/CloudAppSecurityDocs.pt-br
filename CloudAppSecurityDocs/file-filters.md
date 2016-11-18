---
title: Arquivos | Microsoft Docs
description: "Este tópico de referência fornece informações sobre os tipos e filtros de arquivos usados pelo Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/26/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: cadcd6db-05b2-4974-91fe-cfac3d57aecd
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 400741713d40422a3b1c7680663a572d18e9c692
ms.openlocfilehash: 95dab01c101b6e6171c7985b6571ddb6b4ff5923


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
> Ao usar os filtros de política, **contém** pesquisará somente palavras inteiras: separadas por vírgulas, pontos, espaços ou sublinhados. Por exemplo, se você pesquisar **malware** ou **virus**, ele localizará virus_malware_file.exe, mas não localizará malwarevirusfile.exe. Se você pesquisar **malware.exe**, localizará TODOS os arquivos com malware ou exe em seu nome de arquivo, enquanto se pesquisar **"malware.exe"** (com as aspas), localizará apenas arquivos que contêm exatamente "malware.exe".  **É igual a** pesquisará apenas a cadeia de caracteres completa, por exemplo, se você pesquisar **malware.exe**, ele localizará malware.exe, mas não malware.exe.txt. 

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
  
### <a name="governance-actions"></a>Ações de governança  
  
-   Notificações  
  
    -   Alertas – os alertas podem ser disparados no sistema e propagados por email e mensagem de texto, com base no nível de gravidade.  
  
    -   Notificação de email do usuário – mensagens de email podem ser personalizadas e serão enviadas a todos os proprietários do arquivo em violação.  
  
    -   Copiar gerente – com base na integração de diretório do usuário, as notificações de email também podem ser enviadas para o gerente da pessoa que violar uma política.  
  
-   Notificar usuários específicos – lista específica de endereços de email que receberão essas notificações.  
  
-   Notificar último editor do arquivo – envia notificações para a última pessoa que modificou o arquivo.  
  
-   Ações de governança em aplicativos  
  
     Ações granulares podem ser impostas por aplicativo, ações específicas variam dependendo da terminologia do aplicativo.  
  
    -   Alterar o compartilhamento  
  
        -   Remover o compartilhamento público – permite o acesso apenas aos parceiros nomeados, por exemplo: remover acesso público para Google Apps e Remover o link compartilhado direto para o Box.  
  
        -   Remover usuários externos – permite o acesso somente aos usuários da empresa.  
  
        -   Tornar privado – somente o proprietário pode acessar o arquivo, todos os compartilhamentos são removidos.  
  
        -   Remover um parceiro – remove um parceiro específico do arquivo.  
  
    -   Quarentena  
  
        -   Colocar em quarentena do usuário – Permite o autoatendimento movendo o arquivo para uma pasta de quarentena controlada pelo usuário  
  
        -   Colocar em quarentena do administrador – o arquivo é movido para a quarentena na unidade do administrador e o administrador precisa aprová-lo.  
  
-   Lixeira – move o arquivo para a pasta da lixeira.
  
![alertas de policy_create](./media/policy_create-alerts.png "policy_create alerts")  
  
 
## <a name="see-also"></a>Veja também  
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Oct16_HO5-->



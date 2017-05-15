---
title: "Visão geral do cenário de controle de dados | Microsoft Docs"
description: "Este tópico descreve o cenário para controlar dados em seu ambiente de nuvem."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/20/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 57927618-cb66-4c7f-afd7-c96926460816
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: cae50c83705d91513525c9b90e462e44e07b97ed
ms.sourcegitcommit: 7e9ae94cb4f90fbccaa84f19bdebb4652a425e45
translationtype: HT
---
# <a name="controlling-and-protecting-your-files"></a>Controlar e proteger seus arquivos  

No mundo corporativo atual, em que há tantos dados e tantos dispositivos, pode ser difícil manter o controle de onde seus dados estão e quem tem acesso a eles. O Cloud App Security permite que você assuma o controle sobre seus dados com a proteção de arquivos na nuvem. O Cloud App Security fornece ferramentas para a criação de políticas para o que você deseja ou não permitir em sua nuvem corporativa, e oferece uma ampla gama de processos automatizados para fornecer verificações de conformidade contínuas, tarefas de Descoberta Eletrônica jurídica, DLP para conteúdo confidencial armazenado na sua nuvem, ou compartilhado externamente ou publicamente, e muitos outros casos de uso.  
O Cloud App Security pode monitorar qualquer tipo de arquivo com base em mais de 20 filtros de metadados (como por exemplo, nível de acesso e tipo de arquivo). Para saber mais, veja [Arquivos](file-filters.md). Estes são dois exemplos de ameaças relacionadas a dados que todas as organizações enfrentam, com procedimentos para proteger seus arquivos na nuvem.
 
## <a name="files-that-contain-sensitive-data-are-being-shared-externally"></a>Arquivos que contêm dados confidenciais estão sendo compartilhados externamente 

Esse caso de uso aplica-se ao Office 365, G Suite, Box, Dropbox e Salesforce.

### <a name="the-threat"></a>A AMEAÇA
Um dos maiores benefícios que a tecnologia de nuvem oferece é a capacidade de compartilhar qualquer coisa com qualquer um. Mas com mais poder vem maior responsabilidade; para certificar-se de que nenhum dado confidencial está sendo compartilhado externamente, você precisa saber quais arquivos contêm dados confidenciais e com quem eles são compartilhados. Usando as ferramentas fornecidas com seus aplicativos na nuvem, você não é capaz de dizer o que é salvo no aplicativo na nuvem nem quem tem acesso – impedindo que você reconheça possíveis vazamentos de dados.

### <a name="the-solution"></a>A SOLUÇÃO
Ao encontrar os parâmetros de nível de compartilhamento e confidencialidade e realizar o cruzamento entre eles, você pode identificar essas possíveis violações. O Cloud App Security examina todos os arquivos salvos em seus aplicativos na nuvem e classifica-os automaticamente pelo nível de compartilhamento. Você pode configurar uma política de arquivo do Cloud App Security para pesquisar todos os dados confidenciais salvos em seus aplicativos na nuvem. Uma vez descoberto que um arquivo confidencial compartilhado externamente, você pode realizar ações de correção manual ou você pode definir o Cloud App Security para fazer isso automaticamente para você. Ao fazer isso, você pode remover o risco de vazamento de dados com um clique.

#### <a name="prerequisites"></a>Pré-requisitos

[Conectar](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) ao menos um aplicativo de nuvem ao Cloud App Security.

#### <a name="setting-up-monitoring"></a>Configurar o monitoramento

1.    Inicie o monitoramento de seu aplicativo configurando uma política que verificará todos os arquivos compartilhados externamente quanto a conteúdo sensível:

    1. Na página **Políticas**, clique em [**Criar política de arquivos**](data-protection-policies.md). 
    ![Criar política de arquivos](./media/create-file-policy.png)

    2. No campo [**Modelo de política**](policy-template-reference.md), escolha **Arquivo que contém PII detectado na nuvem (mecanismo de DLP interno)** e clique em **Aplicar modelo**. 
    ![Modelo de política de arquivo](./media/file-policy-template.png)
    3. Para monitorar o compartilhamento inadequado de arquivos que contêm informações confidenciais, adicione um filtro com o nível de acesso que você está tentando impedir. Por exemplo, **Nível de acesso igual a Externo, Público, Público (Internet)**. 
     ![Filtro de política de arquivo](./media/file-policy-filter.png)

2. Investigar suas correspondências
    
    1. Na página **Políticas**, clique no nome da política para ir para **Relatório de Políticas** e analise as correspondências que foram criadas para a política.

    2. Você pode investigar a correspondência clicando em uma correspondência específica para abrir a gaveta de arquivos. Na gaveta, é possível ver as outras políticas que correspondem a este arquivo, o status de verificação do conteúdo e, se você clicar aqui, pode ver as correspondências do conteúdo. Você pode clicar em **Colaboradores** para ver a lista de colaboradores e se há rótulos de classificação no arquivo. Você também pode examinar o **Caminho** para ver onde o arquivo foi salvo e obter mais informações sobre o arquivo em si.
    
    3. Se você descobrir falsos positivos, marque-os com uma marca de verificação para excluí-los do relatório e das correspondências dinâmicas. Você pode usar o recurso de comentários para informar a equipe do Cloud App Security sobre as melhorias que gostaria de adicionar. 


#### <a name="validating-your-policy"></a>Validar a política

1. Crie um novo documento do Word com o seguinte texto: 078-05-1120.
2. Em seguida, salve o arquivo como *arquivo de teste.docx* e compartilhe-o com alguém de fora de seu domínio ou com uma URL pública. 
3. Vá para o relatório de políticas. Uma correspondência de política do arquivo deve aparecer em breve. 
4. Você pode clicar na correspondência para ver o contexto do arquivo. A correspondência em si será mascarada para proteger os dados confidenciais. 

#### <a name="removing-the-risk"></a>Remover o risco

Após você ter validado e ajustado a política, remova eventuais falsos positivos que possam ter correspondido à sua política. Em seguida, faça o seguinte: 
  1. Você pode executar [ações de governança](governance-actions.md) imediatas clicando nos três pontos no final da linha e selecionando a ação de governança relevante; por exemplo, **Colocar em quarentena de usuário**.

 ![governança automática externa](./media/auto-gov-external.png)

   2. Depois que for totalmente validada, você pode defini-la para executar ações de governança automáticas. Por exemplo, no SharePoint e no OneDrive é possível **Remover usuários externos** ou **Colocar em quarentena de usuário** e, para o G Suite e o Box, é possível **Remover usuários externos** e **Remover acesso público**.

  ![aplicar ações de governança automáticas](./media/apply-automatic-gov-actions.png)

## <a name="files-shared-publicly-and-labeled-as-confidential"></a>Arquivos compartilhados publicamente e rotulados como confidenciais

Esse caso de uso aplica-se ao Office 365, G Suite, Box, Dropbox e Salesforce.

Esse caso de uso tira proveito da integração entre o Cloud App Security e a Proteção de Informações do Azure. Se você estiver executando a Proteção de Informações do Azure em sua organização e tiver rotulado os arquivos com rótulos da Proteção de Informações do Azure, o Cloud App Security permite monitorar e controlar o que acontece com esses arquivos depois que eles são rotulados.

### <a name="the-threat"></a>A AMEAÇA

Você sabe que precisa proteger seus dados. Você já teve o trabalho de classificar os arquivos na Proteção de Informações do Azure. Mas após classificá-los, como você saberá onde estão e quem os acessa? 

### <a name="the-solution"></a>A SOLUÇÃO
 Você pode monitorar esses arquivos confidenciais quando estiverem na nuvem usando o Cloud App Security. Isso permite que você certifique-se de que os dados classificados como **confidenciais** (ou outra classificação confidencial) não estejam sendo inadequadamente compartilhados. Deixe que o Cloud App Security monitore e gerencie os arquivos que você classificou na Proteção de Informações do Azure distribuindo a política e ações de governança a seguir.

#### <a name="prerequisites"></a>Pré-requisitos

- [Conectar](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) ao menos um aplicativo de nuvem ao Cloud App Security.
- Siga as [Instruções de integração da Proteção de Informações do Azure](azip-integration.md) para habilitar a verificação automática.

#### <a name="setting-up-monitoring"></a>Configurar o monitoramento

1. Monitore todos os arquivos com os rótulos de classificação desejados que são compartilhados publicamente:    
    
    1. Na página **Políticas**, clique em [**Criar política de arquivos**](data-protection-policies.md). 

    2.    Na seção de filtro, é possível remover os filtros de **Nível de acesso** e **Última modificação** para executar essa política em todos os arquivos na sua nuvem. Esses filtros aplicam-se somente a arquivos modificados desse momento em diante. Adicione o filtro **Rótulo de classificação**, **é igual a** e selecione o rótulo de classificação da sua organização. 
    
    ![rótulo de classificação de política de arquivos](./media/file-policy-class-label.png)

    3.    Para monitorar o compartilhamento inadequado desses arquivos classificados, adicione um filtro com o nível de acesso que você está tentando impedir. Por exemplo, **Nível de acesso é igual a Público, Público (Internet)**.  Depois de iniciar a política, o Cloud App Security demora um pouco para verificar os arquivos existentes e quaisquer novos arquivos que você adicionar. Dependendo da quantidade de dados na nuvem, levará algum tempo para concluir a verificação.

    ![filtro de política de arquivos público](./media/file-policy-filter-public.png)

2. Investigar suas correspondências

    1. Clique no nome da política para ir para o **Relatório de políticas** e analise as correspondências que foram criadas para a política.
    
    2. Você pode investigar a correspondência clicando em uma correspondência específica para abrir a gaveta de arquivos. Na gaveta, é possível ver os rótulos de classificação que foram definidos nesse arquivo, outras políticas a que esse arquivo corresponde e você pode clicar em **Colaboradores** para ver a lista de colaboradores. Você também pode examinar o **Caminho** para ver onde o arquivo foi salvo e obter mais informações sobre o arquivo em si.
      
    3. Se você descobrir falsos positivos, marque-os com uma marca de verificação para excluí-los do relatório e das correspondências dinâmicas. Você pode usar o recurso de comentários para informar a equipe do Cloud App Security sobre as melhorias que gostaria de adicionar. 


#### <a name="validating-your-policy"></a>Validar a política

1. Crie um novo documento do Word e use a barra de ferramentas da Proteção de Informações do Azure para definir qualquer rótulo de confidencialidade, como **Confidencial**. 

2. Carregue o arquivo para o aplicativo de nuvem e, em seguida, compartilhe-o com uma URL pública. 

3. Vá para o **Relatório de Políticas**. Uma correspondência de política do arquivo deve aparecer em breve. 

4. Você pode ver o rótulo de classificação clicando no arquivo e abrindo os **Gaveta de arquivos**. 


#### <a name="removing-the-risk"></a>Remover o risco

Após você ter validado e ajustado a política para remover eventuais falsos positivos que possam ter correspondido à sua política, faça o seguinte: 

1. Você pode executar [ações de governança](governance-actions.md) imediatas clicando nos três pontos no final da linha e selecionando a ação de governança relevante; por exemplo, **Colocar em quarentena de usuário**.
    
2. Depois que for totalmente validada, você pode defini-la para executar ações de governança automáticas. Por exemplo, no SharePoint e no OneDrive é possível **Colocar em quarentena de usuário** e, para o G Suite e o Box, é possível **Remover acesso público**.
 
 ![ação de governança automática remover acesso público](./media/gov-action-public-access.png)

## <a name="see-also"></a>Veja também  
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
---
title: "Integração da Proteção de Informações do Azure | Microsoft Docs"
description: "Este artigo fornece informações sobre como utilizar os rótulos da Proteção de Informações do Azure no Cloud App Security para controle adicional sobre o uso de aplicativos de nuvem da sua organização."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/12/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 8168319a-199f-4e6c-ad68-e0f236480803
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 5fe0c3c04f290fb5a087e387560bf742a7192513
ms.openlocfilehash: 0432ccf823234617bb4c8466f88ca8f385704928


---

# <a name="azure-information-protection-integration"></a>Integração da Proteção de Informações do Azure

O Cloud App Security permite investigar arquivos e definir políticas com base nos rótulos de arquivo da Proteção de Informações do Azure, permitindo maior visibilidade e controle dos dados confidenciais na nuvem. Para habilitar isso, defina uma política no Cloud App Security para verificar os arquivos com a inspeção de conteúdo habilitada. Além disso, você pode disparar alertas sobre atividades relacionadas a arquivos confidenciais. A integração com a Proteção de Informações do Azure permite que você:
-   Quantifique a exposição de dados confidenciais em seus aplicativos em nuvem.
-   Crie políticas e alertas sobre violações de carregamento de dados confidenciais em seus aplicativos conectados à nuvem ou coloque em quarentena/bloqueie dados confidenciais para que não sejam compartilhados externamente.
-   Investigue trilhas de auditoria e corrija arquivos que estão violando as políticas 

> [!NOTE] 
> Por padrão, os arquivos são examinados por rótulos somente quando há uma política de arquivo que os examina com a inspeção de conteúdo habilitada. Para examinar rótulos de todos os arquivos sem as políticas de arquivo, habilite o exame automático.

## <a name="terminology-overview"></a>Visão geral da terminologia
-   O rótulo de classificação da Proteção de Informações do Azure – um atributo automaticamente adicionado aos arquivos em sua organização, com base em uma política ou, manualmente, definido por usuários finais.
-   Externo – um rótulo definido por alguém externo à sua organização.
-   Marca de arquivo – a apresentação do rótulo de classificação no Cloud App Security. Este campo é mostrado para cada arquivo na tabela de arquivos e pode ser usado em filtros.
-   Política de arquivo – um conjunto de regras que dependem de filtros de arquivo e permitem que você aplique uma ampla gama de processos automatizados, aproveitando as APIs do provedor de nuvem.

## <a name="license-and-tenant-creation"></a>Criação de licença e locatário
Para habilitar esse recurso você precisará uma licença do Cloud App Security e uma licença para a Proteção de Informações do Azure Premium P1 ou P2. Assim que as duas licenças estiverem em vigor, o Cloud App Security sincronizará os rótulos das organizações do serviço de Proteção de Informações do Azure:

![tela de exemplo do azip](./media/azip-screen.png)

![cas em comparação com o azip](./media/cas-compared-azip.png)
     
Além disso, por padrão, os arquivos que passarão por inspeção de conteúdo por uma ou mais políticas de arquivo, também serão examinados pelos rótulos de classificação.

## <a name="gain-visibility"></a>Obtenha visibilidade

Os rótulos de arquivo que foram examinadas para cada arquivo estão visíveis na gaveta de arquivo.
Na página **Arquivos**, clique no arquivo relevante para ver se ele tem rótulos de arquivo:

![gaveta de arquivos](./media/azip-file-drawer.png)

Você pode clicar nos rótulos para exibir mais informações ou para ver a lista completa de rótulos:
 
![lista de rótulos](./media/azip-tags-list.png)

Use o filtro **Rótulos de arquivo** para pesquisar arquivos que foram marcados com um rótulo específico:
 
![filtro de rótulos de arquivo](./media/azip-file-tags-filter.png)

Ou, para arquivos que foram marcados com qualquer rótulo de arquivo:

![todos os filtros de rótulos de arquivo](./media/azip-file-tags-all-filter.png)

## <a name="how-it-works"></a>Como funciona
Assim que você conectar o Cloud App Security à Proteção de Informações do Azure, o Cloud App Security verificará os arquivos da seguinte maneira:
1. Recuperar a lista de todos os rótulos de classificação usados em seu locatário. Isso é executado a cada hora para manter a lista atualizada.
2. Verificar os arquivos buscando rótulos de classificação. Isso pode ocorrer de duas maneiras: a. Os arquivos que tiverem o conteúdo verificado como parte de uma política de arquivos também serão adicionados à fila de verificação de rótulos de classificação.
    b. Para adicionar todos os arquivos na fila de verificação sem precisar definir uma política de arquivos, habilite a verificação automática (veja abaixo), que verificará todos os arquivos novos ou modificados.
3. Os rótulos externos somente serão adicionados à lista de rótulos de classificação se eles forem vistos em um arquivo específico, a não ser que você marque a caixa de seleção **Ignorar rótulos de classificação da Proteção de Informações do Azure de outros locatários** (veja abaixo).

## <a name="enable-automatic-scan"></a>Habilitar exame automático
A verificação automática permite pesquisar rótulos de classificação de Proteção de Informações do Azure em seus arquivos do Office 365 sem a necessidade de criar uma política. Esse recurso está disponível se você tiver uma licença independente do Cloud App Security.
Para habilitar varreduras automáticas de marcas de arquivos para novos arquivos:

1. No Cloud App Security, vá para a página **Configurações gerais**.
2. Na Proteção de Informações do Azure, selecione **Examinar arquivos automaticamente para rótulos de classificação da Proteção de Informações do Azure**. Depois que ela for habilitada, todos os novos arquivos adicionados ao Office 365, não apenas aqueles que têm o conteúdo examinado por uma política de arquivo, terão rótulos de arquivo examinados.

![habilitar a Proteção de Informações do Azure](./media/enable-azip.png)

> [!NOTE] 
> A verificação automática não verificará arquivos existentes até que eles sejam modificados novamente. Para verificar rótulos de classificação da Proteção de Informações do Azure nos arquivos existentes, crie uma nova **Política de Arquivo** sem filtros, marque a opção **Inspeção de Conteúdo** e salve a política.

## <a name="internal-and-external-tags"></a>Rótulos internos e externos
Por padrão, o Cloud App Security examinará rótulos de classificação que foram definidos em sua organização, bem como aqueles externos que foram definidos por outras organizações. 

Para ignorá-las, no portal do Cloud App Security, em **Configurações gerais** em **Configurações de segurança do Azure**, selecione **Ignorar rótulos de classificação da Proteção de Informações do Azure de outros locatários**.
 
![ignorar rótulos](./media/azip-ignore.png)

> [!Note]
> Se você estiver trabalhando em um locatário de teste, provavelmente não desejará ignorar rótulos de classificação externos para poder testar arquivos recebidos de outros locatários.

![rótulos da Proteção de Informações do Azure no Cloud App Security](./media/azip-tags-in-cas.png)

## <a name="use-azure-information-protection-tags-to-apply-control"></a>Use os rótulos da Proteção de Informações do Azure para aplicar o controle
Crie políticas de arquivo no Cloud App Security para localizar arquivos compartilhados inadequadamente e localizar arquivos que estão rotulados e foram modificados recentemente. 

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

  

## <a name="see-also"></a>Consulte Também  
[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  



<!--HONumber=Dec16_HO2-->



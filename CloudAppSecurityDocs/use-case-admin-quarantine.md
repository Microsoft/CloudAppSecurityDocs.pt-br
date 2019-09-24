---
title: Proteger arquivos com a quarentena do administrador do Cloud App Security
description: Este tutorial descreve o cenário para usar a quarentena do administrador para controlar as violações de dados.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 7/30/2019
ms.topic: tutorial
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 3fc04cfb-ad4c-4ac2-980a-ee9f4c740d88
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 6a147b9db857ee3e8c791f193be4b84e29c3c148
ms.sourcegitcommit: 8a49c166424fea83853b0a6895212367526abe78
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71084904"
---
# <a name="tutorial-protect-files-with-admin-quarantine"></a>Tutorial: Proteger arquivos com quarentena do administrador

*Aplica-se a: Microsoft Cloud App Security*

[Políticas de arquivo](data-protection-policies.md) são uma excelente ferramenta para encontrar ameaças contra as políticas de proteção de informações. Por exemplo, crie políticas de arquivo que encontram locais nos quais os usuários armazenaram informações confidenciais, números de cartão de crédito e arquivos ICAP de terceiros em sua nuvem.

Este tutorial ajuda você a usar o Microsoft Cloud App Security para detectar arquivos indesejados armazenados na nuvem que o deixam vulnerável e a executar uma ação imediata para interrompê-los enquanto agem e bloquear os arquivos que representam uma ameaça usando a **Quarentena do administrador** para proteger os arquivos na nuvem, corrigir problemas e impedir vazamentos futuros.

> [!div class="checklist"]
> * Entender como funciona a quarentena 
> * Configurar a quarentena do administrador

## <a name="understand-how-quarantine-works"></a>Entender como funciona a quarentena

>[!NOTE]
> - Para obter uma lista de aplicativos que dão suporte à quarentena do administrador, consulte a lista de [ações de governança](governance-actions.md).
> - Se um arquivo no SharePoint ou OneDrive for detectado como sendo malware, ele não será posto em quarentena no portal do Cloud App Security.

1. Quando um arquivo corresponde a uma política, a opção **Quarentena do administrador** estará disponível para o arquivo.

2. Execute uma das seguintes ações para colocar o arquivo em quarentena:

   - Aplique manualmente a ação **quarentena do administrador**:

     ![ação de quarentena](./media/quarantine-action.png)

   - Defina-o como uma ação de quarentena automatizada na política:

     ![colocar em quarentena automaticamente](./media/quarantine-automated.png)

3. Quando a **Quarentena do administrador** é aplicada, as seguintes ações ocorrem em segundo plano:

   1. O arquivo original é movido para a pasta de quarentena de administrador que você definir.
   2. O arquivo original é excluído.
   3. Um arquivo de marca de exclusão é carregado para o local do arquivo original.

      ![marca de exclusão de quarentena](./media/quarantine-tombstone.png)

   4. O usuário só pode acessar o arquivo de marca de exclusão. No arquivo, ele pode ler as diretrizes personalizadas fornecidas pela TI e a ID de correlação a ser fornecida à IT para liberar o arquivo.

4. Quando você receber o alerta que um arquivo tiver sido colocado em quarentena, investigue o arquivo na página de **Alertas** do Cloud App Security:

   ![alertas de quarentena](./media/quarantine-alerts.png)

5. Também no **Relatório de política** na guia **Em quarentena**:

   ![relatório de quarentena](./media/quarantine-report.png)

6. Depois que um arquivo foi colocado em quarentena, use o processo a seguir para corrigir a situação de ameaça:

    1. Inspecione o arquivo na pasta de quarentena no SharePoint Online.
    2. Você também pode examinar os logs de auditoria para aprofundar-se nas propriedades de arquivo.
    3. Se você achar que o arquivo está violando a política corporativa, execute o processo de RI (Resposta a Incidentes) da organização.
    4. Se você achar que o arquivo é inofensivo, poderá restaurar o arquivo da quarentena. Nesse momento, o arquivo original é liberado, ou seja, ele é copiado para a localização original, a marca de exclusão é excluída e o usuário pode acessar o arquivo.

       ![restauração da quarentena](./media/quarantine-restore.png)

7. Valide se a política é executada corretamente. Em seguida, você poderá usar as ações de governança automáticas na política para impedir outras perdas e aplicar automaticamente uma Quarentena do administrador quando a política for correspondida.

> [!NOTE]
> Quando você restaurar um arquivo:
> - Compartilhamentos originais não são restaurados, a herança da pasta padrão é aplicada.
> - O arquivo restaurado contém apenas a versão mais recente.
> - O gerenciamento de acesso de site de pasta de quarentena é responsabilidade do cliente.

## <a name="set-up-admin-quarantine"></a>Configurar a quarentena do administrador

1. Defina políticas de arquivo que detectam violações. Exemplos desses tipos de políticas incluem:

    - Uma política somente de metadados, como um rótulo de classificação no SharePoint Online
    - Uma política DLP nativa, como uma política que pesquisa números de cartão de crédito
    - Uma política ICAP de terceiros, como uma política que procura o Vontu

2. Defina um local de quarentena:
   1. Para o Office 365 SharePoint ou o OneDrive for Business, você não pode colocar arquivos na quarentena do administrador como parte de uma política enquanto não configurá-la: ![configurações de quarentena](./media/quarantine-warning.png)

      Para definir configurações de quarentena, na engrenagem de configurações, acesse **Configurações**. Forneça uma localização para os arquivos em quarentena e uma notificação de usuário que o usuário receberá quando seu arquivo for colocado em quarentena.
      ![configurações de quarentena](./media/quarantine-settings.png)

   2. Para o Box, a mensagem do usuário e a localização da pasta de quarentena não podem ser personalizadas. A localização da pasta é a unidade do administrador que conectou o Box ao Cloud App Security e a mensagem do usuário é: Este arquivo foi colocado em quarentena na unidade do administrador, pois pode violar as políticas de segurança e conformidade de sua empresa. Entre em contato com seu administrador de TI para obter ajuda.

## <a name="next-steps"></a>Próximas etapas 
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/)  

---
title: Proteger arquivos com a quarentena do administrador do Microsoft Cloud App Security
description: Este tutorial descreve o cenário de uso da quarentena do administrador para controlar violações de dados.
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
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 83bb7ac4d1b75a98f426f97f09d6019befc221ad
ms.sourcegitcommit: 0b929f7c8feed7dfb40d5294179fd5c6fc079614
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/21/2020
ms.locfileid: "80666423"
---
# <a name="tutorial-protect-files-with-admin-quarantine"></a>Tutorial: Proteger arquivos com quarentena do administrador

*Aplica-se a: Microsoft Cloud App Security*

As [políticas de arquivo](data-protection-policies.md) são uma excelente ferramenta para encontrar ameaças a suas políticas de proteção de informações. Por exemplo, crie políticas de arquivo que encontrem locais onde os usuários armazenaram informações confidenciais, números de cartão de crédito e arquivos ICAP de terceiros em sua nuvem.

Este tutorial ajuda você a usar o Microsoft Cloud App Security para detectar arquivos indesejados armazenados em sua nuvem que deixam você vulnerável. Ajuda ainda a tomar medidas imediatas para interromper esses arquivos e bloquear os arquivos que representam ameaça usando a **Quarentena do administrador** para proteger seus arquivos na nuvem, corrigir problemas e impedir que futuros vazamentos ocorram.

> [!div class="checklist"]
>
> * Como funciona a quarentena
> * Configuração da quarentena do administrador

## <a name="understand-how-quarantine-works"></a>Como funciona a quarentena

>[!NOTE]
>
> * Para obter uma lista de aplicativos que dão suporte à quarentena do administrador, consulte a lista de [ações de governança](governance-actions.md).
> * Se um arquivo no SharePoint ou OneDrive for detectado como sendo malware, ele não será posto em quarentena no portal do Cloud App Security.
> * Os arquivos com rótulos não podem ser colocados em quarentena.

1. Quando um arquivo corresponder a uma política, a opção de **Quarentena do administrador** ficará disponível para o arquivo.

2. Execute uma das seguintes ações para colocar o arquivo em quarentena:

    * Aplique manualmente a ação **Quarentena do administrador**:

    ![ação de quarentena](media/quarantine-action.png)

    * Defina-a como ação de quarentena automatizada na política:

    ![colocado em quarentena automaticamente](media/quarantine-automated.png)

3. Quando a **Quarentena do administrador** é aplicada, as seguintes ações ocorrem nos bastidores:

    1. O arquivo original é movido para a pasta de quarentena do administrador que você definiu.
    2. O arquivo original é excluído.
    3. Um arquivo de marca de exclusão é carregado no local do arquivo original.

    ![marca de exclusão de quarentena](media/quarantine-tombstone.png)

    4. O usuário só pode acessar o arquivo de marca de exclusão. No arquivo, ele pode ler as diretrizes personalizadas fornecidas pelo TI e a ID de correlação para dar ao TI para liberar o arquivo.

4. Quando receber o alerta de que um arquivo foi colocado em quarentena, investigue o arquivo na página **Alertas** do Cloud App Security:

    ![alertas de quarentena](media/quarantine-alerts.png)

5. E também no **Relatório de política**, na guia **Em Quarentena**:

    ![relatório de quarentena](media/quarantine-report.png)

6. Depois que um arquivo tiver siso colocado em quarentena, use o seguinte processo para corrigir a situação de ameaça:

    1. Inspecione o arquivo na pasta de quarentena no SharePoint Online.
    2. Você também pode examinar os logs de auditoria para se aprofundar nas propriedades do arquivo.
    3. Se achar que o arquivo viola a política corporativa, execute o processo IR (Resposta a Incidentes) da organização.
    4. Se achar que o arquivo é inofensivo, poderá restaurá-lo da quarentena. Nesse ponto, o arquivo original será liberado, o que significa que ele será copiado de volta para o local original, a marca de exclusão é excluída, e o usuário pode acessar o arquivo.

      ![restauração da quarentena](media/quarantine-restore.png)

7. Valide se a política é executada sem problemas. Em seguida, você pode usar as ações de governança automáticas na política para evitar vazamentos adicionais e aplicar automaticamente uma Quarentena do administrador quando houver correspondência com a política.

> [!NOTE]
> Ao restaurar um arquivo:
>
> * Os compartilhamentos originais não são restaurados, a herança da pasta padrão é aplicada.
> * O arquivo restaurado contém apenas a versão mais recente.
> * O gerenciamento de acesso ao site da pasta de quarentena é de responsabilidade do cliente.

## <a name="set-up-admin-quarantine"></a>Configuração da quarentena do administrador

1. Defina as políticas de arquivo que detectam violações. Exemplos desses tipos de políticas incluem:

    - Uma política somente de metadados, como um rótulo de classificação no SharePoint Online
    - Uma política de DLP nativa, como uma política que procura números de cartão de crédito
    - Uma política ICAP de terceiros, como uma política que procura o Vontu

2. Defina um local de quarentena:
   1. Para o Office 365 SharePoint ou OneDrive for Business, os arquivos não podem ser colocados em quarentena do administrador como parte de uma política até que você configure: ![configurações de quarentena](media/quarantine-warning.png)

      Defina as configurações de quarentena do administrador na engrenagem de configuração e acesse **Configurações**. Forneça um local para os arquivos em quarentena e uma notificação de usuário que seu usuário receberá quando o arquivo for colocado em quarentena.
      ![configurações de quarentena](media/quarantine-settings.png)

   2. Para o Box, o local da pasta de quarentena e a mensagem do usuário não podem ser personalizados. O local da pasta é a unidade do administrador que conectou o Box ao Cloud App Security, e a mensagem do usuário é: Este arquivo foi colocado em quarentena na unidade do administrador, pois pode violar as políticas de segurança e conformidade de sua empresa. Entre em contato com seu administrador de TI para obter ajuda.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]

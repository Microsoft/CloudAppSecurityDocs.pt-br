---
title: Caso de uso para como investigar e corrigir violações de arquivo usando a quarentena do administrador | Microsoft Docs
description: Este tópico descreve o cenário para usar quarentena do administrador para controlar as violações de dados.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/22/2018
ms.topic: article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 3fc04cfb-ad4c-4ac2-980a-ee9f4c740d88
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 38faca2d4d8da2802ca0043bf53564d840645523
ms.sourcegitcommit: 45311f2cafef79483e40d971a4c61c7673834d96
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2018
---
*Aplica-se ao: Microsoft Cloud App Security*


# <a name="protecting-your-files-with-admin-quarantine"></a>Proteger seus arquivos com quarentena do administrador

> [!NOTE]
> Este é um recurso de versão prévia.

As [Políticas de arquivos](data-protection-policies.md) são uma excelente ferramenta para encontrar ameaças em suas políticas de proteção de informações, por exemplo, para encontrar locais em que os usuários armazenaram informações confidenciais, números de cartão de crédito e arquivos ICAP de terceiros em sua nuvem. Com o Microsoft Cloud App Security, além de detectar estes arquivos indesejados armazenados na sua nuvem, deixando-o vulnerável, você também pode tomar ação imediata para interrompê-los em seus rastreamentos e bloquear os arquivos que representem uma ameaça. Usando **Quarentena do administrador**, você pode proteger os arquivos na nuvem e corrigir problemas, bem como impedir vazamentos futuras. 

>[!NOTE] 
> Para obter uma lista de aplicativos que dão suporte a quarentena do administrador, consulte a lista de [ações de governança](governance-actions.md).
 
## <a name="how-quarantine-works"></a>Como a quarentena funciona 

1. Quando um arquivo corresponde a uma política, a opção **Quarentena do administrador** estará disponível para o arquivo.

2. Execute uma das ações a seguir para colocar o arquivo em quarentena:
   - Aplique manualmente a ação **quarentena do administrador**:
     
     ![ação de quarentena](./media/quarantine-action.png)

   - Defina-o como uma ação de quarentena automatizada na política: 

     ![colocar em quarentena automaticamente](./media/quarantine-automated.png)

3. Quando **Quarentena do administrador** for aplicada, o seguinte ocorre em segundo plano:

   1. O arquivo original é movido para a pasta de quarentena de administrador que você definir.
   2. O arquivo original é excluído.
   3. Um arquivo de marca de exclusão é carregado para o local do arquivo original.

      ![marca de exclusão de quarentena](./media/quarantine-tombstone.png)

   4. O usuário tem acesso somente à marca de exclusão, na qual ele pode ser as diretrizes personalizadas fornecidas pelo IT e a ID de correlação para contatar o IT para liberar o arquivo.

4. Quando você receber o alerta que um arquivo tiver sido colocado em quarentena, investigue o arquivo na página de **Alertas** do Cloud App Security:

   ![alertas de quarentena](./media/quarantine-alerts.png)
 
5. Também no **Relatório de política** na guia **Em quarentena**:

   ![relatório de quarentena](./media/quarantine-report.png)
    
6. Depois que um arquivo foi colocado em quarentena, use o processo a seguir para corrigir a situação de ameaça:
       
    1. Inspecione o arquivo na pasta de quarentena no SharePoint Online.
    3. Você também pode examinar os logs de auditoria para aprofundar-se nas propriedades de arquivo.
    4. Se o arquivo for contra a política corporativa, execute o processo de RI (resposta de incidente) da organização.
    5. Se o arquivo for inofensivo, você poderá restaurar o arquivo da quarentena, no ponto em que o arquivo original for liberado, ou seja, ele será copiado para o local original, a marca de exclusão será excluída e o usuário poderá acessar o arquivo.
       ![restaurar da quarentena](./media/quarantine-restore.png)
7. Após validar que a política é executada sem problemas, você pode usar as ações de governança automáticas na política para evitar mais perdas e aplicar automaticamente quarentena do administrador quando a política for correspondida.

> [!NOTE]
> Quando você restaurar um arquivo:
> - Compartilhamentos originais não são restaurados, a herança da pasta padrão é aplicada.
> - O arquivo restaurado contém apenas a versão mais recente.
> 
> 
> [!NOTE]
> O gerenciamento de acesso de site de pasta de quarentena é responsabilidade do cliente.

#### <a name="how-to-set-up-admin-quarantine"></a>Como configurar a quarentena de administrador

1. Defina políticas de arquivo que detectem violações, como uma política somente de metadados (como um rótulo de classificação no SharePoint Online), uma política DLP nativa (como uma política que procura os números de cartão de crédito) ou uma política de terceiros ICAP (como uma política que procura Vontu).

2. Defina um local de quarentena:
   1. Para o Office 365 SharePoint ou OneDrive for Business, antes de configurar a quarentena do administrador, você não poderá colocar arquivos em quarentena do administrador como parte de uma política: ![configurações de quarentena](./media/quarantine-warning.png)

      Para definir configurações de quarentena, sob o ícone de engrenagem de configurações, acesse **Configurações gerais** e forneça um local para os arquivos em quarentena e uma notificação de usuário que o usuário receberá quando seu arquivo for colocado em quarentena. 
      ![configurações de quarentena](./media/quarantine-settings.png)

   2. Para Box, a mensagem de usuário e o local da pasta de quarentena não podem ser personalizados. O local da pasta é a unidade do administrador que conector o Box ao Cloud App Security e a mensagem do usuário é: Este arquivo foi colocado em quarentena na unidade do administrador porque ele pode violar as políticas de segurança e conformidade de sua empresa. Contate o administrador de TI para obter ajuda.



## <a name="see-also"></a>Consulte Também  
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
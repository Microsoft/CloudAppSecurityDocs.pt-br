---
title: Aplicar automaticamente os rótulos de classificação da Proteção de Informações do Azure
description: Este tutorial descreve como aplicar automaticamente rótulos de classificação da proteção de informações do Azure no Microsoft Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 3/5/2019
ms.topic: tutorial
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 4f8e5c59de4dd05730dc6970ae1cbebe8f941356
ms.sourcegitcommit: 870ca47381a36b4bc04e1ccb9b2a522944431fed
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88964042"
---
# <a name="tutorial-automatically-apply-azure-information-protection-classification-labels"></a>Tutorial: Aplicar automaticamente os rótulos de classificação da Proteção de Informações do Azure

*Aplica-se a: Microsoft Cloud App Security*

Em um mundo perfeito, todos os seus funcionários entendem a importância da proteção de informações e do trabalho em relação às suas políticas. Mas, no mundo real, é provável que um parceiro que trabalhe com contabilidade carregue um documento no seu repositório do Box com as permissões erradas. Uma semana depois, você percebe que as informações confidenciais da sua empresa foram vazadas para a concorrência. O Microsoft Cloud App Security ajuda a evitar que esse tipo de desastre ocorra. Esse recurso está disponível para Box, SharePoint e OneDrive for Business. A aplicação de um rótulo da Proteção de Informações do Azure faz parte de uma longa lista de [ações de governança](governance-actions.md) disponíveis.

Esse tutorial ajuda a identificar quais permissões públicas são definidas em um documento que é salvo em seu armazenamento em nuvem, assim você é alertado caso ocorra uma violação. Além disso, você pode aplicar automaticamente seu rótulo de classificação **confidencial** da Proteção de Informações do Azure para fornecer criptografia adicional aos arquivos.

> [!div class="checklist"]
>
> * Configurar a proteção de dados
> * Validar sua política

## <a name="enhanced-data-level-encryption-protection"></a>Proteção de criptografia aprimorada no nível de dados

A integração do Cloud App Security com a Proteção de Informações do Azure permite um nível de proteção adicional por meio da criptografia automática de arquivos. Quando a Proteção de Informações do Azure criptografa arquivos, os aplicativos com suporte para esse recurso, como o Office 365, saberão como abrir os arquivos e honrarão as permissões definidas nos rótulos de classificação. Use os rótulos para aplicar regras de proteção específicas. Por exemplo, defina um arquivo que possa ser aberto, mas que não possa ser compartilhado, impresso, encaminhado ou editado.

Esse nível forte de proteção vai junto com o arquivo. O arquivo continuará protegido se você o enviar, copiar ou armazenar em seu aplicativo de armazenamento online. Caso um de seus funcionários perca um pen drive com o arquivo, este será bloqueado. Caso alguém tente abrir o arquivo, o proprietário do arquivo receberá um alerta. Com o Cloud App Security, você pode aplicar a proteção automaticamente. Por exemplo, você pode definir que todos os arquivos que tenham números de cartão de crédito ou que foram carregados pelo departamento de finanças e serão compartilhados externamente sejam automaticamente protegidos com um rótulo de classificação.

## <a name="the-threat"></a>A ameaça

Um usuário da sua organização salva os arquivos confidenciais de informações do cliente no Box e os define para serem compartilhados com todos na organização. O usuário não percebe que não é somente sua equipe imediata que tem acesso a essa conta do Box, mas toda a equipe de suporte. Esse acesso inclui fornecedores, parceiros e visitantes que eventualmente visitam o escritório. Agora, qualquer pessoa com acesso à conta do Box da sua organização tem acesso a essas informações. Esse acesso não só pode ser perigoso para sua organização, como também pode violar regulamentos de informações pessoais em muitos países/regiões, causando possíveis problemas legais.

## <a name="the-solution"></a>A solução

Use o Cloud App Security com a Proteção de Informações do Azure para inserir informações de classificação e proteção para uma proteção contínua que segue seus dados, fazendo com que eles permaneçam protegidos, independentemente de onde estejam armazenados ou com quem sejam compartilhados. Essa proteção permite que você compartilhe dados de modo seguro com colegas de trabalho, clientes e parceiros. Defina quem pode acessar os dados e o que eles podem fazer com eles. Por exemplo, você pode permitir que os usuários exibam e editem arquivos, mas não que os imprimam ou os encaminhem. Você também pode adicionar outras [ações de governança](governance-actions.md) com suporte do Cloud App Security aos arquivos, como remover colaboradores e remover recursos de compartilhamento.

## <a name="prerequisites"></a>Pré-requisitos

* [Habilitar o Cloud App Security e a Proteção de Informações do Azure](azip-integration.md) para seu locatário.
* [Conectar o Box](connect-box-to-microsoft-cloud-app-security.md) ao Cloud App Security.

## <a name="set-up-data-protection"></a>Configurar a proteção de dados

Vamos configurar uma política que procure números de cartão de crédito em arquivos armazenados em sua conta do Box. Quando arquivos forem encontrados, aplique automaticamente um rótulo de Proteção de Informações do Azure e controle o que acontece com todos os arquivos com esse rótulo.

1. Comece a proteger os dados que você armazena no Box configurando uma política que criptografará quaisquer dados confidenciais armazenados no Box:

    1. Na guia **Controle**, clique em [**Políticas**](control-cloud-apps-with-policies.md).

    2. Clique em **Criar política** e selecione **Política de arquivos**.

    3. Chame a política de *Proteção de dados do Box*.

    4. Em **Criar um filtro para os arquivos em que esta política atuará**, defina seus dados proprietários e confidenciais como alvo.
        * Por exemplo, selecione **Pasta pai** igual a **Dados do cliente** no Box e selecione **Proprietário** é igual à equipe de finanças.

    5. Dentro dessa pasta, procure arquivos que contenham informações de cartão de crédito. Em **Método de inspeção de conteúdo**, selecione **DLP interno**, depois **Incluir arquivos que correspondam a uma expressão predefinida** e, por fim, **Todos os países:Finanças:Número de cartão de crédito**.

    6. Em **Governança**, abra a seção do **Box** e selecione **Aplicar rótulo de classificação**. Selecione o rótulo que você deseja aplicar.

    7. Como o [Cloud App Security é integrado à Proteção de Informações do Azure](azip-integration.md), você pode fazer a seleção na lista existente de rótulos de classificação a serem usados para proteger os dados.

    8. Clique em **Criar**.

   ![Adicionar rótulo de classificação à política](media/aip-auto-policy.png)

2. Como investigar suas correspondências

    1. Na página **Políticas**, clique no nome da política para acessar o **Relatório de política**. Revise as correspondências que foram acionadas para a política.

    2. Para investigar a correspondência, clique em uma correspondência específica para abrir a gaveta de arquivos. Na gaveta, você pode ver as outras políticas correspondentes a esse arquivo.

## <a name="validate-your-policy"></a>Validar sua política

1. Para simular um alerta, acesse sua conta do Box e tente acessar um arquivo na pasta **Dados do cliente**.
2. Acesse o relatório de política. Uma correspondência à política de arquivo deve aparecer em breve.
3. Você pode clicar na correspondência para ver quais arquivos foram protegidos. A correspondência em si será mascarada para proteger os dados confidenciais.

>[!NOTE]
>
> \* – O Cloud App Security atualmente dá suporte à aplicação automática de rótulos da Proteção de Informações do Azure no Box, no GSuite, no SharePoint e no OneDrive for Business.
> \* – Quando um documento é rotulado usando o Cloud App Security, as marcações visuais não são aplicadas imediatamente, e sim quando esse documento é aberto em um aplicativo do Office e é salvo pela primeira vez. Para obter mais informações, consulte [Como configurar um rótulo para marcações visuais da Proteção de Informações do Azure](/information-protection/deploy-use/configure-policy-markings#when-visual-markings-are-applied).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
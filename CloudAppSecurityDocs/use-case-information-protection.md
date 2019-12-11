---
title: Aplicar automaticamente os rótulos de classificação da Proteção de Informações do Azure
description: Este tutorial descreve como aplicar automaticamente os rótulos de classificação da Proteção de Informações do Azure no Microsoft Cloud App Security.
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
ms.openlocfilehash: 77face48858ae577c4eb2aa4fd85f7fc39c81377
ms.sourcegitcommit: 6eff466c7a6817b14a60d8c3b2c201c7ae4c2e2c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74720788"
---
# <a name="tutorial-automatically-apply-azure-information-protection-classification-labels"></a>Tutorial: Aplicar automaticamente os rótulos de classificação da Proteção de Informações do Azure

*Aplica-se a: Microsoft Cloud App Security*

Em um mundo perfeito, todos os seus funcionários entendem a importância da proteção das informações e do trabalho dentro de suas políticas. Mas, em um mundo real, é provável que um parceiro que trabalhe com contabilidade carregue um documento no repositório do Box com as permissões incorretas. Na semana seguinte, você percebe que as informações confidenciais de sua empresa foram perdidas para a concorrência. O Microsoft Cloud App Security ajuda a impedir que esse tipo de desastre ocorra. Este recurso está disponível para Box, SharePoint e OneDrive for Business. Aplicar um rótulo da Proteção de Informações do Azure é apenas uma ação dentro de uma longa lista de [ações de governança](governance-actions.md) disponíveis.

Este tutorial ajuda você a identificar quais permissões públicas são definidas em um documento que é salvo no seu armazenamento em nuvem, para que você seja alertado quando ocorrer uma violação. Além disso, você pode aplicar automaticamente o rótulo de classificação **Confidencial** da Proteção de Informações do Azure para fornecer uma criptografia adicional aos arquivos.

> [!div class="checklist"]
>
> * Configurar a proteção de dados
> * Validar sua política

## <a name="enhanced-data-level-encryption-protection"></a>Proteção de criptografia de nível de dados avançada

A integração do Cloud App Security com a Proteção de Informações do Azure habilita um nível adicional de proteção ao criptografar automaticamente os arquivos. Quando a Proteção de Informações do Azure criptografa arquivos, os aplicativos que dão suporte à Proteção de Informações do Azure, como o Office 365, conseguem abrir os arquivos e respeitam as permissões definidas nos rótulos de classificação. Use rótulos para aplicar regras de proteção específicas. Por exemplo, defina um arquivo que pode ser aberto, mas não compartilhado, impresso, encaminhado nem editado.

Esse alto nível de proteção acompanha o arquivo. O arquivo ainda fica protegido se você o envia, copia ou armazena em seu aplicativo de armazenamento online. Se um dos funcionários perder um pen drive com o arquivo nele, o arquivo será bloqueado. Caso alguém tente abrir o arquivo, o proprietário do arquivo receberá um alerta. Com o Cloud App Security, você pode aplicar proteção automaticamente. Por exemplo, defina todos os arquivos que têm números de cartão de crédito ou que foram carregados pelo departamento de finanças e são compartilhados externamente, para serem protegidos automaticamente com um rótulo de classificação.

## <a name="the-threat"></a>A ameaça

Um usuário em sua organização salva arquivos de informações confidenciais de clientes no Box e programa-o para ser compartilhado com todas as pessoas na organização. O usuário não percebe que não apenas sua equipe imediata, mas toda a equipe de suporte, tem acesso a essa conta do Box. Esse acesso inclui fornecedores, parceiros e visitantes que ocasionalmente vão ao escritório. Agora, qualquer pessoa com acesso à conta do Box de sua organização tem acesso a essas informações. Esse acesso pode ser não apenas perigoso para sua organização, mas pode infringir os regulamentos de informações pessoais em muitos países, causando possíveis problemas legais.

## <a name="the-solution"></a>A solução

Use o Cloud App Security com a Proteção de Informações do Azure para inserir informações de classificação e proteção a fim de fornecer proteção persistente que segue seus dados – garantindo que permaneçam protegidos, independentemente do local em que estejam armazenados ou do usuário com quem eles forem compartilhados. Essa proteção permite que você compartilhe dados de maneira segura com colegas, clientes e parceiros. Defina quem pode acessar os dados e o que os usuários podem fazer com eles. Por exemplo, permita aos usuários exibir e editar arquivos, mas não imprimir nem encaminhar. Adicione também outras [ações de governança](governance-actions.md) compatíveis com o Cloud App Security aos arquivos, como remover colaboradores e remover capacidades de compartilhamento.

## <a name="prerequisites"></a>Pré-requisitos

* [Habilitar o Cloud App Security e a Proteção de Informações do Azure](azip-integration.md) no locatário.
* [Conectar o Box](connect-box-to-microsoft-cloud-app-security.md) ao Cloud App Security.

## <a name="set-up-data-protection"></a>Configurar a proteção de dados

Vamos configurar uma política que procura números de cartão de crédito em arquivos armazenados em sua conta do Box. Quando os arquivos forem encontrados, aplique automaticamente um rótulo da Proteção de Informações do Azure e controle o que acontecerá com todos os arquivos contendo esse rótulo.

1. Comece a proteger os dados armazenados no Box configurando uma política que criptografará todos os dados confidenciais armazenados no Box:

    1. Na guia **Controle**, clique em [**Políticas**](control-cloud-apps-with-policies.md).

    2. Clique em **Criar política** e selecione **Política de arquivo**.

    3. Chame a política de *Proteção de dados do Box*.

    4. Em **Criar um filtro para os arquivos em que esta política atuará**, defina seus dados confidenciais e proprietários como destino.
        * Por exemplo, selecione **Pasta pai** igual a **Dados do cliente** no Box e selecione **Proprietário** igual à equipe de finanças.

    5. Nessa pasta, procure arquivos que contenham informações de cartão de crédito. Em **Método de inspeção de conteúdo**, selecione **DLP interno**, selecione **Incluir arquivos que correspondam a uma expressão predefinida** e selecione **Todos os países: Finanças: Número de cartão de crédito**.

    6. Em **Governança**, abra a seção **Box** e selecione **Aplicar rótulo de classificação**. Selecione o rótulo que deseja aplicar.

    7. Como o [Cloud App Security está integrado com a Proteção de Informações do Azure](azip-integration.md), você pode selecionar da lista existente de rótulos de classificação a ser usada para proteger os dados.

    8. Clique em **Criar**.

   ![Adicionar rótulo de classificação à política](media/aip-auto-policy.png)

2. Investigar suas correspondências

    1. Na página **Políticas**, clique no nome da política para acessar o **Relatório de política**. Examine as correspondências que foram disparadas para a política.

    2. Você pode investigar a correspondência clicando em uma correspondência específica para abrir a gaveta de arquivos. Na gaveta, você pode ver as outras políticas às quais esse arquivo correspondeu.

## <a name="validate-your-policy"></a>Validar sua política

1. Para simular um alerta, acesse sua conta do Box e tente acessar um arquivo da pasta **Dados do cliente**.
2. Vá para o relatório de políticas. Uma correspondência de política do arquivo deve aparecer em breve.
3. Você pode clicar na correspondência para ver quais arquivos foram protegidos. A correspondência em si será mascarada para proteger os dados confidenciais.

>[!NOTE]
>
> \* – O Cloud App Security atualmente dá suporte à aplicação automática de rótulos da Proteção de Informações do Azure no Box, no GSuite, no SharePoint e no OneDrive for Business.
> \* – Quando um documento é rotulado usando o Cloud App Security, as marcações visuais não são aplicadas imediatamente, e sim quando esse documento é aberto em um aplicativo do Office e é salvo pela primeira vez. Para obter mais informações, consulte [How to configure a label for visual markings for Azure Information Protection](https://docs.microsoft.com/information-protection/deploy-use/configure-policy-markings#when-visual-markings-are-applied) (Como configurar um rótulo para marcações visuais na Proteção de Informações do Azure).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]

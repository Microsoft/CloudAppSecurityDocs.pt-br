---
title: Aplicar automaticamente os rótulos de classificação da Proteção de Informações do Azure | Microsoft Docs
description: Este tópico descreve o processo para aplicar automaticamente os rótulos de classificação da Proteção de Informações do Azure no Microsoft Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/22/2018
ms.topic: article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: eac0b192-98d7-4939-9a07-1d4a7f8c39c3
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: b4d507b5fb3a646b31ba3c380b170c2abca18ddf
ms.sourcegitcommit: 45311f2cafef79483e40d971a4c61c7673834d96
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2018
---
*Aplica-se ao: Microsoft Cloud App Security*



# <a name="automatically-apply-azure-information-protection-classification-labels"></a>Aplicar automaticamente os rótulos de classificação da Proteção de Informações do Azure  

Em um mundo perfeito, todos os seus funcionários entendem a importância da proteção das informações e do trabalho dentro de suas políticas. Mas, em um mundo real, é provável que um parceiro que trabalha com a contabilidade faça o upload de um documento para o repositório do Box com as permissões erradas e, uma semana mais tarde, você percebe que informações confidenciais da sua empresa foram perdidas para a concorrência. 

O Microsoft Cloud App Security ajuda a impedir que esse tipo de desastre ocorra.

O Microsoft Cloud App Security identifica que existem permissões públicas em um documento salvo em sua conta do Box e usa um mecanismo de classificação para identificar que há informações confidenciais no documento compartilhado publicamente. O Cloud App Security envia um alerta para informar isso ocorreu e, além disso, aplica automaticamente o rótulo de classificação **confidencial** da Proteção de Informações do Azure para fornecer criptografia adicional ao arquivo. 

>[!NOTE]
> - Aplicar um rótulo da Proteção de Informações do Azure é apenas uma ação dentro de uma longa lista de [ações de governança](governance-actions.md) disponíveis.
> - Este recurso está disponível para Box, SharePoint e OneDrive for Business.

### <a name="enhanced-data-level-encryption-protection"></a>Proteção de criptografia de nível de dados avançada

A integração do Cloud App Security com a Proteção de Informações do Azure habilita um nível adicional de proteção ao criptografar automaticamente os arquivos. Por exemplo, enquanto a Proteção de Informações do Azure criptografa o arquivo, aplicativos compatíveis com ela (como o Office 365) conseguem abrir os arquivos e cumprir as permissões definidas nos rótulos de classificação. Você pode usar rótulos para aplicar regras de proteção específicas. Por exemplo, você pode programar um arquivo de modo que ele possa ser aberto, mas não possa ser compartilhado, impresso, encaminhado nem editado). 

Esse alto nível de proteção acompanha o arquivo – se você enviar o arquivo, copiá-lo ou armazená-lo em seu aplicativo de armazenamento online, o arquivo ainda estará protegido. Se um de seus funcionários perdeu um pen drive com o arquivo, o arquivo será bloqueado e, se alguém tentar abri-lo, o proprietário do arquivo receberá um alerta. Com o Cloud App Security, você pode aplicar proteção automaticamente. Por exemplo, todos os arquivos que têm números de cartão de crédito ou foram carregados pelo departamento de finanças e são compartilhados externamente podem ser programados para ser protegidos automaticamente com um rótulo de classificação. 

## <a name="the-threat"></a>A ameaça 
Um usuário em sua organização salva arquivos de informações confidenciais de clientes no Box e programa-o para ser compartilhado com todas as pessoas na organização. O usuário não percebe que, além de sua equipe imediata, a equipe de suporte inteira tem acesso a essa conta do Box, incluindo fornecedores, parceiros e os visitantes que ocasionalmente passam no escritório. Agora, qualquer pessoa com acesso à conta do Box de sua organização tem acesso a essas informações. Isso pode ser não apenas perigoso para os clientes, mas pode ser contra os regulamentos de PII em muitos países, causando possíveis problemas legais.

## <a name="the-solution"></a>A solução
Use o Cloud App Security com a Proteção de Informações do Azure para inserir as informações de classificação e proteção para obter uma proteção persistente que segue seus dados – garantindo que permaneçam protegidos, independentemente de onde estão armazenados ou com quem são compartilhados. Isso também permite que você compartilhe dados com segurança com colegas de trabalho, bem como seus parceiros e clientes. Defina quem pode acessar os dados e o que eles podem fazer com eles – como permitir que os usuários exibam e editem arquivos, mas não imprimam nem encaminhem, além de outras [ações de governança](governance-actions.md) compatíveis com o Cloud App Security, como remover colaboradores e remover recursos de compartilhamento.

## <a name="prerequisites"></a>Pré-requisitos

- [Habilitar o Cloud App Security e a Proteção de Informações do Azure](azip-integration.md) no locatário.
- [Conectar o Box](connect-box-to-microsoft-cloud-app-security.md) ao Cloud App Security.

## <a name="setting-up-data-protection"></a>Configurando a proteção de dados

Vamos configurar uma política que procura números de cartão de crédito em arquivos armazenados em sua conta do Box e, quando eles forem encontrados, aplicaremos automaticamente um rótulo da Proteção de Informações do Azure e, em seguida, com esse rótulo, controlaremos o que acontece com todos os arquivos.

1. Comece a proteger os dados armazenados no Box configurando uma política que criptografará todos os dados confidenciais armazenados no Box:

    1. Na guia **Controle**, clique em [**Políticas**](control-cloud-apps-with-policies.md). 
    
    2. Clique em **Criar política** e selecione **Política de arquivo**.
    
    3. Chame a política de *Proteção de dados do Box*.
    
    4. Em **Criar um filtro para os arquivos em que esta política atuará**, defina seus dados confidenciais e proprietários como destino.<br></br>
    Por exemplo, selecione **Pasta pai** igual a **Dados do cliente** no Box e selecione **Proprietário** igual a e selecione a equipe de finanças.
    
    4. Dentro dessa pasta, procure por arquivos que contenham informações de cartão de crédito da seguinte maneira: em **Método de inspeção de conteúdo**, selecione **DLP interno** e, em seguida, selecione **Incluir arquivos que correspondam a uma expressão predefinida** e selecione **Todos os países:Finanças:Número de cartão de crédito**.
    
    5. Em **Governança**, abra a seção **Box** e selecione **Aplicar rótulo de classificação** e selecione o rótulo que deseja aplicar.
    
    6. Como o [Cloud App Security está integrado com a Proteção de Informações do Azure](azip-integration.md), você pode selecionar da lista existente de rótulos de classificação a ser usada para proteger os dados.
 
    7. Clique em **Criar**. 
   
   ![Adicionar rótulo de classificação à política](./media/aip-auto-policy.png)
     
2. Investigar suas correspondências
    
    1. Na página **Políticas**, clique no nome da política para ir para **Relatório de Políticas** e analise as correspondências que foram criadas para a política.

    2. Você pode investigar a correspondência clicando em uma correspondência específica para abrir a gaveta de arquivos. Na gaveta, você pode ver as outras políticas às quais esse arquivo correspondeu. 
     
## <a name="validating-your-policy"></a>Validar a política

1. Para simular um alerta, vá para sua conta do Box e tente acessar um arquivo na pasta **Dados do cliente**.
3. Vá para o relatório de políticas. Uma correspondência de política do arquivo deve aparecer em breve. 
4. Você pode clicar na correspondência para ver quais arquivos foram protegidos. A correspondência em si será mascarada para proteger os dados confidenciais. 

>[!NOTE]
> - O Cloud App Security atualmente é compatível com a aplicação automática de rótulos da Proteção de Informações do Azure no Box, SharePoint e OneDrive for business.
> - Quando um documento é rotulado usando o Cloud App Security, as marcações visuais não são aplicadas imediatamente, e sim quando esse documento é aberto em um aplicativo do Office e é salvo pela primeira vez. Para obter mais informações, consulte [How to configure a label for visual markings for Azure Information Protection](https://docs.microsoft.com/information-protection/deploy-use/configure-policy-markings#when-visual-markings-are-applied) (Como configurar um rótulo para marcações visuais na Proteção de Informações do Azure).

 ## <a name="see-also"></a>Consulte Também  
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
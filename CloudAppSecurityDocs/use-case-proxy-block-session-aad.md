---
title: Bloquear downloads de dispositivos não gerenciados com o Controle de Aplicativos de Acesso Condicional do Cloud App Security
description: Este tutorial descreve o cenário para proteger sua organização contra downloads de dados confidenciais por dispositivos não gerenciados usando as funcionalidades de proxy reverso do Azure AD.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 1/24/2019
ms.topic: tutorial
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 06238ebc-2088-4372-9412-96cceaf3b145
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: a0c1699c3626e7582a3099b4481fce06ae5635d2
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2019
ms.locfileid: "74459563"
---
# <a name="tutorial-block-download-of-sensitive-information"></a>Tutorial: Bloquear o download de informações confidenciais 

*Aplica-se a: Microsoft Cloud App Security*

>[!div class="step-by-step"]
[« ANTERIOR: Como criar uma política de acesso](access-policy-aad.md)

O administrador de TI atual está entre a cruz e a espada. Você quer permitir que seus funcionários sejam produtivos. Isso significa permitir que os funcionários acessem aplicativos para poderem trabalhar a qualquer momento, em qualquer dispositivo. No entanto, você deseja proteger os ativos da empresa, incluindo informações proprietárias e privilegiadas. Como permitir que os funcionários acessem aplicativos na nuvem e, ao mesmo tempo, proteger seus dados? **Este tutorial permite que você bloqueie downloads realizados por usuários com acesso a dados confidenciais em aplicativos de nuvem empresariais usando dispositivos não gerenciados ou locais fora da rede corporativa.**

> [!div class="checklist"]
> * Criar uma política de download de bloqueio para dispositivos não gerenciados
> * Validar sua política


## <a name="the-threat"></a>A ameaça

Um gerente de conta na sua organização quer verificar algo no Salesforce em casa durante o fim de semana, no laptop pessoal dele. Os dados do Salesforce podem incluir informações pessoais ou de cartão de crédito do cliente. O computador doméstico não é gerenciado. Se eles baixarem documentos do Salesforce no computador, ele poderá ser infectado com malware. Em caso de perda ou roubo do computador, ele poderá não estar protegido por senha e qualquer pessoa que o encontrar terá acesso a informações confidenciais.

## <a name="the-solution"></a>A solução

Proteja sua organização monitorando e controlando o uso de aplicativos de nuvem usando o acesso condicional do Azure AD e o Controle de Aplicativo de Acesso Condicional do Microsoft Cloud App Security.  

## <a name="prerequisites"></a>Pré-requisitos

- Uma licença válida do Azure AD Premium P1
- Configurar um aplicativo de nuvem para SSO no Azure AD  
- Certificar-se de que o [aplicativo foi implantado no Cloud App Security](proxy-deployment-aad.md)

## <a name="create-a-block-download-policy-for-unmanaged-devices"></a>Criar uma política de download de bloqueio para dispositivos não gerenciados  

As políticas de sessão do Cloud App Security permitem que você restrinja uma sessão com base no estado do dispositivo. Para obter o controle de uma sessão usando seu dispositivo como uma condição, crie uma política de acesso condicional E uma política de sessão.

### <a name="step-1-create-an-azure-ad-conditional-access-policy"></a>Etapa 1: Criar uma política de acesso condicional do Azure AD

1. Crie uma política de acesso condicional do Azure AD com aplicativo e usuários atribuídos.
2. Selecione **Usar restrições aplicadas pelo Controle de Aplicativo de Acesso Condicional** nos controles de sessão dentro da política de acesso condicional.

Depois de concluir essa tarefa, acesse o portal do Cloud App Security e crie uma política de sessão para monitorar e controlar os downloads de arquivo na sessão.

### <a name="step-2-create-a-session-policy"></a>Etapa 2: Criar uma política de sessão

1. No portal do Cloud App Security, selecione **Controle** e depois **Políticas**. 

2. Na página **Políticas**, clique **Criar política** e depois **Política de sessão**.
 
3. Na página **Criar política de sessão**, dê um nome e uma descrição à sua política. Por exemplo, **Bloquear downloads do Salesforce para dispositivos não gerenciados**.

4. Atribua uma **Severidade da política** e **Categoria**.

5. Em **Tipo de controle de sessão**, selecione **Controlar download de arquivo (com DLP)** . Essa configuração fornece a capacidade de monitorar tudo o que os usuários fazem em uma sessão do Salesforce, fornecendo o controle para bloquear e proteger downloads em tempo real.

6. Em **Origem da atividade** na seção **Atividades que correspondem a todos os seguintes**, selecione os filtros: 

   - **Marca de dispositivo**: Selecione **Não é igual a**. e, em seguida, selecione **Em conformidade**, **Ingressado no domínio** ou **Certificado do cliente válido**. A seleção depende do método usado em sua organização para identificar dispositivos gerenciados. 

   - **Aplicativo**: Selecione o aplicativo que deseja controlar.  

   - **Usuários**: Selecione os usuários que deseja monitorar.  

7. Como alternativa, você pode bloquear os downloads de locais que não fazem parte da rede corporativa. Em **Origem da atividade** na seção **Atividades que correspondem a todos os seguintes**, defina os seguintes filtros:

   - **Endereço IP** ou **Localização**: Use um desses dois parâmetros para identificar localizações não corporativas ou desconhecidas, das quais um usuário pode estar tentando acessar dados confidenciais.

     > [!NOTE]
     > Caso deseje bloquear downloads de dispositivos não gerenciados e locais não corporativos, você precisará criar duas políticas de sessão. Uma política define a **Origem da atividade** usando a localização. A outra política define a **Origem da atividade** para dispositivos não gerenciados.

   - **Aplicativo**: Selecione o aplicativo que deseja controlar.

   - **Usuários**: Selecione os usuários que deseja monitorar.  

8. Em **Origem da atividade** na seção **Arquivos que correspondem a todos os seguintes**, defina os seguintes filtros: 

   - **Rótulos de classificação**: Se você usar os rótulos de classificação da Proteção de Informações do Azure, filtre os arquivos com base em um rótulo de Classificação específico da Proteção de Informações do Azure.

   - Selecione **Nome de arquivo** ou **Tipo de arquivo** para aplicar as restrições com base no nome ou no tipo de arquivo.
9. Habilite **Inspeção de conteúdo** para permitir que a DLP interna examine se há conteúdo confidencial em seus arquivos. 

10. Em **Ações**, selecione **bloquear**. Personalize a mensagem de bloqueio que os usuários recebem quando não conseguem baixar arquivos.  

11. Defina os alertas que você deseja receber quando a política é correspondida. Você pode definir um limite para não receber um número excessivo de alertas. Selecione se deseja receber os alertas como uma mensagem de email, uma mensagem de texto ou ambos.

12. Clique em **Criar**  

## <a name="validate-your-policy"></a>Validar sua política

1. Para simular o download do arquivo bloqueado, em um dispositivo não gerenciado ou uma localização que não seja a rede corporativa, entre no aplicativo. Em seguida, tente baixar um arquivo.

2. O arquivo deverá ser bloqueado e você deverá receber a mensagem definida em **Personalizar mensagens de bloqueio**. 

3. No portal do Cloud App Security, clique em **Controle** e depois **Políticas** e, sem seguida, clique na política criada para exibir o relatório de política. Uma correspondência de política de sessão deve ser exibida em breve. 

4. Na relatório de política, é possível ver quais logons foram redirecionados para o Microsoft Cloud App Security para controle de sessão e quais arquivos foram baixados ou bloqueados das sessões monitoradas.

>[!div class="step-by-step"]
[« ANTERIOR: Como criar uma política de acesso](access-policy-aad.md)

## <a name="next-steps"></a>Próximas etapas
  
[Criar uma política de sessão](session-policy-aad.md)   

[!INCLUDE [Open support ticket](includes/support.md)]  
  
  

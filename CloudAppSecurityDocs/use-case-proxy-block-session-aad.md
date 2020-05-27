---
title: Bloquear os downloads em dispositivos não gerenciados com o Controle de Aplicativos de Acesso Condicional do Cloud App Security
description: Este tutorial descreve o cenário para proteger sua organização contra downloads de dados confidenciais por dispositivos não gerenciados usando recursos de proxy reverso do Azure AD (Azure Active Directory).
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/31/2020
ms.topic: tutorial
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 57fac7776efbb617a382a30f6bf68ac2578ad0a6
ms.sourcegitcommit: e1a0d6a7d639a6d268b0104eb3e5532d2692288b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/18/2020
ms.locfileid: "83551282"
---
# <a name="tutorial-block-download-of-sensitive-information"></a>Tutorial: Bloquear o download de informações confidenciais

*Aplica-se a: Microsoft Cloud App Security*

O administrador de TI atual está em uma encruzilhada. Você deseja permitir que seus funcionários sejam produtivos. Isso significa permitir que os funcionários acessem os aplicativos para que possam trabalhar a qualquer momento, em qualquer dispositivo. No entanto, você deseja proteger os ativos da empresa, incluindo informações proprietárias e privilegiadas. Como você pode permitir que os funcionários acessem os aplicativos na nuvem enquanto os dados são protegidos? **Este tutorial permite bloquear o download por usuários que têm acesso a dados confidenciais em aplicativos na nuvem corporativos a partir de dispositivos não gerenciados ou locais de rede fora da empresa.**

> [!div class="checklist"]
>
> * Criar uma política de bloqueio de download para dispositivos não gerenciados
> * Validar sua política

## <a name="the-threat"></a>A ameaça

Um gerente de conta em sua organização deseja verificar algo no Salesforce em casa no fim de semana, em um laptop pessoal. Os dados do Salesforce podem incluir informações de cartão de crédito de clientes ou informações pessoais. O computador doméstico não é gerenciado. Se os documentos forem baixados do Salesforce para o computador, eles poderão ser infectados com malware do computador. Caso o computador seja perdido ou roubado e não esteja protegido por senha, qualquer pessoa que o encontre terá acesso a informações confidenciais.

## <a name="the-solution"></a>A solução

Proteja sua organização monitorando e controlando o uso de aplicativos na nuvem com uma solução IdP e o Controle de Aplicativos de Acesso Condicional do Microsoft Cloud App Security.

## <a name="prerequisites"></a>Pré-requisitos

* Uma licença válida do Azure AD Premium P1 ou a licença exigida pela sua solução de IdP (provedor de identidade)
* Configure um aplicativo na nuvem para SSO usando um dos seguintes protocolos de autenticação:

    |IdP|Protocolos|
    |---|---|
    |Azure AD|SAML 2.0 ou OpenID Connect|
    |Outros|SAML 2.0|
* Verificar se o [aplicativo está implantado no Cloud App Security](proxy-deployment-aad.md)

## <a name="create-a-block-download-policy-for-unmanaged-devices"></a>Criar uma política de bloqueio de download para dispositivos não gerenciados

As políticas de sessão do Cloud App Security permitem restringir uma sessão com base no estado do dispositivo. Para realizar o controle de uma sessão usando seu dispositivo como uma condição, crie uma política de acesso condicional E uma política de sessão.

### <a name="step-1-configure-your-idp-to-work-with-cloud-app-security"></a>Etapa 1: Configurar seu IdP para trabalhar com o Cloud App Security

Para verificar se você configurou sua solução de IdP para trabalhar com o Cloud App Security, faça o seguinte:

* Para [Acesso condicional do Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal), consulte [Configurar a integração com o Azure AD](proxy-deployment-aad.md#configure-integration-with-azure-ad)
* Para outras soluções do IdP, consulte [Configurar a integração com outras soluções de IdP](proxy-deployment-aad.md#configure-integration-with-other-idp-solutions)

Depois de concluir essa tarefa, vá para o portal do Cloud App Security e crie uma política de sessão para monitorar e controlar os downloads de arquivos na sessão.

### <a name="step-2-create-a-session-policy"></a>Etapa 2: criar uma política de sessão

1. No portal do Cloud App Security, selecione **Controle**, seguido por **Políticas**.

2. Na página **Políticas**, clique em **Criar política**, seguido por **Política de sessão**.

3. Na página **Criar política de sessão**, dê um nome e uma descrição à sua política. Por exemplo, **Bloquear downloads do Salesforce em dispositivos não gerenciados**.

4. Atribua a **Severidade da política** e a **Categoria**.

5. Para o **Tipo de controle de sessão**, selecione **Controlar download de arquivo (com DLP)** . Essa configuração oferece a capacidade de monitorar tudo o que os usuários fazem em uma sessão do Salesforce e proporciona controle para bloquear e proteger downloads em tempo real.

6. Em **Origem da atividade**, na seção **Atividades correspondentes ao seguinte**, selecione os filtros:

   * **Marca do dispositivo**: Selecione **Não é igual a**. Em seguida, selecione **Em conformidade com o Intune**, **Ingressado no Azure AD híbrido** ou **Certificado de cliente válido**. Sua seleção depende do método usado na sua organização para identificar os dispositivos gerenciados.

   * **Aplicativo**: selecione o aplicativo que você deseja controlar.

   * **Usuários**: selecione os usuários que você deseja monitorar.

7. Como alternativa, você pode bloquear os downloads para locais que não fazem parte de sua rede corporativa. Em **Origem da atividade**, na seção **Atividades correspondentes ao seguinte**, configure estes filtros:

   * **Endereço IP** ou **Local**: você pode usar qualquer um desses dois parâmetros para identificar locais não corporativos ou desconhecidos, dos quais um usuário pode estar tentando acessar dados confidenciais.

     > [!NOTE]
     > Se você deseja bloquear os downloads de dispositivos não gerenciados e de locais não corporativos, será necessário criar duas políticas de sessão. Uma política define a **Origem da atividade** usando o local. A outra política define a **Origem da atividade** como dispositivos não gerenciados.

   * **Aplicativo**: selecione o aplicativo que você deseja controlar.

   * **Usuários**: selecione os usuários que você deseja monitorar.

8. Em **Origem da atividade**, na seção **Arquivos correspondentes ao seguinte**, configure estes filtros:

   * **Rótulos de classificação**: se você usar rótulos de classificação da Proteção de Informações do Azure, filtre os arquivos com base em um rótulo específico da Classificação da Proteção de Informações do Azure.

   * Selecione **Nome do arquivo** ou **Tipo de arquivo** para aplicar as restrições com base no nome ou tipo de arquivo.
9. Habilite a **Inspeção de conteúdo** para permitir que a DLP interna verifique os arquivos em busca de conteúdo confidencial.

10. Em **Ações**, selecione **Bloquear**. Personalize a mensagem de bloqueio que os usuários recebem quando não conseguem baixar os arquivos.

11. Defina os alertas que você deseja receber quando a política for correspondida. Você pode definir um limite para não receber muitos alertas. Selecione se deseja receber os alertas como mensagem de email, mensagem de texto ou ambos.

12. Clique em **Criar**

## <a name="validate-your-policy"></a>Validar sua política

1. Para simular o download do arquivo bloqueado, de um dispositivo não gerenciado ou de um local de rede não corporativo, entre no aplicativo. Depois, tente baixar um arquivo.

2. O arquivo deve estar bloqueado, e você deve receber a mensagem definida em **Personalizar mensagens de bloqueio**.

3. No portal do Cloud App Security, clique em **Controlar**, seguido por **Políticas**, depois clique na política que você criou para exibir o relatório de política. Uma correspondência de política de sessão deve aparecer em breve.

4. No relatório de política, você pode ver quais logons são redirecionados ao Microsoft Cloud App Security para controle de sessão e quais arquivos foram baixados ou bloqueados nas sessões monitoradas.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Como criar uma política de acesso](access-policy-aad.md)

> [!div class="nextstepaction"]
> [Como criar uma política de sessão](session-policy-aad.md)

[!INCLUDE [Open support ticket](includes/support.md)]

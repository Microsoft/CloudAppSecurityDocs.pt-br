---
title: "Como bloquear downloads de dados confidenciais para dispositivos não gerenciados usando o proxy do Cloud App Security | Microsoft Docs"
description: "Este tópico descreve o cenário para proteger sua organização contra downloads de dados confidenciais por dispositivos não gerenciados usando os recursos de proxy do Azure AD."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/11/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 06238ebc-2088-4372-9412-96cceaf3b145
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: d086dc6e05d64662625340594f0bb355936c0a7a
ms.sourcegitcommit: 4d84f9d15256b05c785a1886338651b86622070c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2017
---
# <a name="blocking-downloads-of-sensitive-information-using-the-microsoft-cloud-app-security-proxy"></a>Bloqueando downloads de informações confidenciais usando o proxy do Microsoft Cloud App Security


O administrador de TI atual está entre a cruz e a espada: você quer permitir que seus funcionários sejam produtivos. Isso significa permitir que os funcionários acessem aplicativos para poderem trabalhar a qualquer momento, em qualquer dispositivo. Por outro lado, você deseja proteger os ativos da empresa, e que incluem informações proprietárias e privilegiadas. Como é possível permitir que seus funcionários acessem aplicativos de nuvem e, ao mesmo tempo, proteger seus dados? **Este caso de uso permite que você bloqueie downloads realizados por usuários que têm acesso a seus dados confidenciais em aplicativos de nuvem empresariais de dispositivos não gerenciados ou locais fora da rede corporativa.**


## <a name="the-threat"></a>A ameaça
Um gerente de conta na sua organização quer verificar algo no Salesforce em casa durante o fim de semana, no laptop pessoal dele. Os dados do Salesforce podem incluir informações pessoais ou do cartão de crédito do cliente. O computador doméstico não é gerenciado, o que significa que, se ele baixar documentos do Salesforce para o computador, ele poderá ser infectado com malware ou, se ele for extraviado ou roubado, o computador talvez não esteja protegido por senha e qualquer pessoa que o encontrar terá acesso a informações confidenciais. 

## <a name="the-solution"></a>A solução
Proteja sua organização monitorando e controlando o uso de aplicativos de nuvem usando o acesso condicional do Azure AD e o proxy do Cloud App Security.  

## <a name="prerequisites"></a>Pré-requisitos

- Uma licença válida do Azure AD Premium P2
- Configurar um aplicativo de nuvem para SSO no Azure AD  
- Certificar-se de que o [aplicativo foi implantado no Cloud App Security](proxy-deployment-aad.md)

## <a name="create-a-block-download-policy-for-unmanaged-devices"></a>Criar uma política de download de bloqueio para dispositivos não gerenciados  

As políticas de sessão do Cloud App Security permitem que você restrinja ainda mais uma sessão com base no estado do dispositivo. Quando você deseja controlar uma sessão usando seu dispositivo como uma condição, é necessário criar uma política de acesso condicional E uma política de sessão para fazer isso.  

### <a name="step-1-create-an-azure-ad-conditional-access-policy"></a>Etapa 1: Criar uma política de acesso condicional do Azure AD

1. Crie uma política de acesso condicional do Azure AD com aplicativo e usuários atribuídos.
2. Selecione **Usar restrições aplicadas pelo proxy** nos controles de sessão dentro da política de acesso condicional.   

 ![Acesso condicional do Azure AD](./media/proxy-deploy-restrictions-aad.png)

Após concluir essa tarefa, vá para o portal do Cloud App Security e crie uma política de sessão para monitorar e controlar os downloads de arquivo na sessão.

### <a name="step-2-create-a-session-policy"></a>Etapa 2: criar uma política de sessão

1. No portal do Cloud App Security, selecione **Controle** e depois **Políticas**. 

2. Na página **Políticas**, clique **Criar política** e depois **Política de sessão**.
 
 ![criar política de sessão](./media/create-session-policy.png)

2. Na página **Criar política de sessão**, dê um nome e uma descrição à sua política. Por exemplo, **Bloquear downloads do Salesforce para dispositivos não gerenciados**.

3. Atribua uma **Severidade da política** e **Categoria**.

 ![Nova política de sessão](./media/new-session-policy.png)

4. Em **Tipo de controle de sessão**, selecione **Monitorar todas as atividades e controlar o download de arquivos**. Isso dá a você a capacidade de monitorar tudo que seus usuários fazem dentro de uma sessão do Salesforce e dá a você o controle para bloquear e proteger downloads em tempo real.

 ![tipo de controle da política de sessão](./media/session-policy-control-type.png)

5.  em **Origem da atividade** na seção **Atividades que correspondem a todos os seguintes**, selecione os filtros: 
    
    - **Marca do dispositivo**: selecione **É diferente de** e, em seguida, selecione **Em conformidade**, **Ingressado em domínio** ou **Certificado do cliente válido**, dependendo do método usado em sua organização para identificar dispositivos gerenciados. 
    
    - **Aplicativo**: selecione o aplicativo que você deseja controlar.  

    - **Usuários**: selecione os usuários que você deseja monitorar.  
    
7. Ou, se desejar bloquear os downloads para locais que não fazem parte da sua rede corporativa, em **Origem da atividade** na seção **Atividades que correspondem a todos os seguintes**, defina os seguintes filtros: 

  - **Endereço IP** ou **Local**: é possível usar um desses dois parâmetros para identificar locais não corporativos ou desconhecidos, dos quais um usuário pode estar tentando acessar dados confidenciais.

     > [!NOTE]
     > Se desejar bloquear downloads de dispositivos não gerenciados e locais não corporativos, será necessário criar duas políticas de sessão, uma que defina a **Origem da atividade** usando o local e outra que defina a **Origem da atividade** como dispositivos não gerenciados.
 
   - **Aplicativo**: selecione o aplicativo que você deseja controlar.    
   
   - **Usuários**: selecione os usuários que você deseja monitorar.  

6. Em **Origem da atividade** na seção **Arquivos que correspondem a todos os seguintes**, defina os seguintes filtros: 
   
    - **Rótulos de classificação**: se você usar os rótulos de classificação da Proteção de Informações do Azure e desejar filtrar os arquivos com base em um rótulo de classificação específico da Proteção de Informações do Azure.
   
    - Selecione **Nome do arquivo** ou **Tipo de arquivo** para aplicar as restrições com base neles.
 
     ![filtros de arquivo da política de sessão](./media/session-policy-file-filters.png)

7. Habilite **Inspeção de conteúdo** para permitir que a DLP interna examine se há conteúdo confidencial em seus arquivos. 

 ![inspeção do conteúdo da política de sessão](./media/session-policy-content-inspection.png)

8. Em **Ações**, selecione **bloquear**. Personalize a mensagem de bloqueio que seus usuários receberão quando não conseguirem baixar os arquivos.  

 ![ações da política de sessão](./media/session-policy-actions.png)

9. Defina os alertas que você deseja receber quando a política é correspondida. É possível definir um limite para que você não receba um número excessivo de alertas, e é possível selecionar se você deseja receber os alertas como uma mensagem de email, como uma mensagem de texto ou ambos.

 ![alertas da política de sessão](./media/session-policy-alert.png)


10. Clique em **Criar**  
 

## <a name="validate-your-policy"></a>Validar sua política 

1. Para simular o download do arquivo bloqueado, em um dispositivo não gerenciado ou em um local que não seja a rede corporativa, faça logon no aplicativo e tente baixar um arquivo. 

2. O arquivo deverá ser bloqueado e você deverá receber a mensagem definida em **Personalizar mensagens de bloqueio**. 

  ![bloquear mensagem de download](./media/block-download-message.png)

3. No portal do Cloud App Security, clique em **Controle** e depois **Políticas** e, sem seguida, clique na política criada para exibir o relatório de política. Uma correspondência de política de sessão deve ser exibida em breve. 
 
  ![relatório de política de sessão](./media/session-policy-report.png)

4. Na relatório de política, é possível ver quais logons foram redirecionados para o proxy para controle de sessão e quais arquivos foram baixados ou bloqueados das sessões monitoradas.




## <a name="see-also"></a>Veja também  
[Criar uma política de sessão](session-policy-aad.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
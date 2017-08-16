---
title: "Implantação do proxy do Cloud App Security | Microsoft Docs"
description: "Este tópico fornece informações sobre como implantar o proxy do Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 7/31/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 75094bde-e135-47fb-b5c6-7e1168919771
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 2cabdaa94c36dcf7496cc1d1126e720871ee80b9
ms.sourcegitcommit: 4cf65f627f2d370ee4a4decae1acbb9658874056
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2017
---
# <a name="deploying-the-cloud-app-security-proxy"></a>Implantando o proxy do Cloud App Security

> [!NOTE]
> É altamente recomendável tentar a instalação em uma área restrita ou ambiente de teste antes de instalá-lo em um ambiente de produção.

As etapas descritas abaixo devem ser executadas para implantar o proxy do Cloud App Security e habilitar o controle de acesso e o controle de sessão.

Como parte da implantação do Proxy, você precisa alterar as configurações no provedor de identidade e no aplicativo que você deseja controlar. Isso inclui alterações de URL para que o provedor de identidade e o aplicativo redirecione as solicitações de logon para o proxy. Além disso, e se for necessário, os certificados também são substituídos.

Depois que essas etapas forem concluídas, todos os eventos de logon passam pelo proxy e o proxy pode decidir se eles têm permissão para acessar o aplicativo, se tiveram o acesso negado ou se podem acessar em modo monitorado. Observe que, neste estágio, o Proxy pode solicitar certificados do cliente do dispositivo e usar o estado do dispositivo para tomar decisões sobre a política.

## <a name="prerequisites"></a>Pré-requisitos

-   Um ambiente de trabalho no qual seu aplicativo de nuvem esteja configurado com um provedor de identidade. O processo de instalação envolve as alterações de configuração no aplicativo e no provedor de identidade.
- Verifique se você tem acesso às configurações de logon único no seu provedor de identidade e no aplicativo.

## <a name="deploy-the-proxy"></a>Implantar o proxy

Se você estiver instalando o proxy em um ambiente de produção, recomendamos escolher um horário quando a maioria dos usuários não estiver usando o aplicativo, geralmente tarde da noite ou no fim de semana, e avisar aos usuários que pode haver um curto tempo de inatividade do aplicativo.

Antes de começar a fazer alterações de configuração, verifique se sua configuração atual está funcionando. Depois disso, execute as seguintes etapas.

1.  No portal do Cloud App Security, vá até a engrenagem Configurações e escolha **Proxy**.

2. No canto superior direito, clique no sinal de adição.

3. Na janela **Adicionar aplicativo ao proxy**, selecione o aplicativo que você deseja adicionar e clique **Iniciar assistente**. 

 ![adicionar aplicativo ao proxy do Cloud App Security](./media/proxy-add-app.png)

4. Carregue o arquivo de metadados de logon único a partir das configurações de logon único do aplicativo. Se você não tiver um arquivo de metadados, clique em **Preencher os dados manualmente** e forneça os dados solicitados de acordo com o assistente. 

 ![adicionar o arquivo de metadados de logon único ao proxy do Cloud App Security](./media/proxy-w-add-app.png)


5. No portal do provedor de identidade, execute as seguintes etapas. Na maioria dos portais de provedor de identidade, isso é executado em **Aplicativos**:

    1. Crie um novo app SAML personalizado. É necessário criar um novo aplicativo personalizado, pois você terá que alterar as URLs e adicionar os atributos de SAML que talvez não sejam possíveis na galeria de aplicativos.
    
    2. Copie a configuração de logon único do aplicativo existente na lista do provedor de identidade para o novo aplicativo personalizado. Verifique se o **Identificador** (também conhecido como ID de público ou entidade) no aplicativo personalizado corresponde ao **Identificador** das configurações de logon único do aplicativo real. Se seu provedor de identidade não permitir que você use o mesmo **Identificador** para dois aplicativos diferentes, depois de copiá-lo, altere o identificador do aplicativo original.
    
    3. Atribua todos os usuários que atualmente estão atribuídos para o aplicativo original para o novo aplicativo personalizado.
    
    ![adicionar o arquivo de metadados de logon único ao proxy do Cloud App Security](./media/proxy-w-add-external-config.png)

5. Carregue o arquivo de metadados de logon único a partir do provedor de identidade. Se você não tiver um arquivo de metadados, clique em **Preencher os dados manualmente** e forneça os dados solicitados de acordo com o assistente.  

 ![adicionar o arquivo de metadados de logon único ao proxy do Cloud App Security](./media/proxy-w-identity-provider.png)

6. Realize as seguintes alterações de configuração externas no portal do provedor de identidade e, em seguida, no novo aplicativo personalizado que você criou:

    1. Copie a URL fornecida no Assistente. Vá para portal do seu provedor de identidade e cole-a como URL de logon único (ou URL de resposta) no novo aplicativo SAML personalizado que você criou.
    
    2. Copie os atributos e os valores fornecidos no Assistente de proxy e adicione-os como atributos personalizados de SAML.
    
    3. Verifique se os identificadores de nome usados pelo seu aplicativo estão no formato de endereço de email. Isso é necessário para habilitar o proxy do Cloud App Security para impor políticas aos usuários.
    
    4. Salve as configurações para seu novo aplicativo personalizado e clique em **Avançar** no Assistente de proxy.
 ![Atualizar configurações do provedor de identidade no proxy do Cloud App Security](./media/proxy-w-ip-external2.png)

4.  Em seguida, na página de configurações de logon único do aplicativo, faça o seguinte:
    1. Faça backup das suas configurações atuais de aplicativo.
    
    2. Copie a URL do Assistente de proxy para a URL de logon único de SAML do aplicativo.
    
    3. Baixe o certificado SAML do Cloud App Security para o aplicativo.
    
    4. No aplicativo personalizado que você criou, carregue esse certificado SAML no lugar do original e salve suas configurações.
   
    5. No assistente do proxy, clique em **Concluir**.


Em alguns minutos, todas as solicitações de logon para o seu aplicativo serão roteadas por meio do proxy do Cloud App Security. 



### <a name="test-the-configuration"></a>Testar a configuração

1.  Tente fazer logon no aplicativo. Se o logon falhar, verifique se você concluiu todas as etapas do Assistente de proxy corretamente. 

2.  No portal do Cloud App Security, em **Investigar**, selecione **Log de atividades** e verifique se há **log de logon único nos** eventos capturados pelo proxy.



## <a name="see-also"></a>Veja também  
[Trabalhando com o proxy do Cloud App Security](proxy-intro.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
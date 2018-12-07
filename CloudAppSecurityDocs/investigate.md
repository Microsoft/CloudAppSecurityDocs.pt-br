---
title: Investigar riscos e atividades suspeitas na nuvem com o Cloud App Security | Microsoft Docs
description: Este artigo fornece uma descrição do processo para investigar alertas, problemas e atividades suspeitas usando o Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/16/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: a9b00c2a-2f71-499e-8f57-67e560daedc1
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 980a6aba1c9c566e74a9c54be50c198b8bd3516d
ms.sourcegitcommit: 851ff017c226435d38bed18dbece640a632cd2a0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2018
ms.locfileid: "51943729"
---
# <a name="investigate"></a>Investigar

*Aplica-se ao: Microsoft Cloud App Security*

Depois que o Microsoft Cloud App Security for executado no ambiente de nuvem, você precisará de um estágio de aprendizado e investigação. Saiba como usar as ferramentas do Microsoft Cloud App Security para obter uma compreensão mais profunda do que está acontecendo em seu ambiente de nuvem. De acordo com seu ambiente específico e como ele está sendo usado, você pode identificar os requisitos para proteger sua organização contra riscos. Este artigo descreve como fazer uma investigação para obter uma melhor compreensão sobre seu ambiente de nuvem.  

## <a name="dashboards"></a>Painéis  
Os painéis a seguir estão disponíveis para ajudá-lo a investigar aplicativos no seu ambiente de nuvem:  

|Painel|Descrição|  
|---------------|-----------------|  
|Painel principal|Visão geral do status da nuvem (usuários, arquivos e atividades) e ações necessárias (alertas, violações de atividade e violações de conteúdo)|  
|Painel do aplicativo: geral|Visão geral do uso do aplicativo por local, gráficos de uso por número de usuários|  
|Painel do aplicativo: insights|Análise de dados armazenados no aplicativo, divididos por tipo de arquivo e nível de compartilhamento de arquivos|  
|Painel do aplicativo: arquivos|Faça uma busca detalhada nos arquivos; capacidade de filtrar de acordo com o proprietário, nível de compartilhamento e mais; execute ações de governança, como quarentena.|  
|Painel do aplicativo: aplicativos de terceiros|Faça uma busca detalhada nos aplicativos de terceiros atualmente implantados, como o G Suite, e defina políticas para eles|  
|Painel do usuário|Uma visão geral completa do perfil do usuário na nuvem, incluindo grupos, locais, atividades recentes, alertas relacionados e navegadores usados|  

##  <a name="sanctionapp"></a> Marcar aplicativos como sancionados ou não sancionados  
Uma etapa importante para entender sua nuvem é marcar os aplicativos como sancionados ou não sancionados. Depois de sancionar um aplicativo, você poderá filtrar pelos aplicativos que não estão sancionados e iniciar a migração para aplicativos sancionadas do mesmo tipo.  

- No console do Cloud App Security, acesse o Catálogo de aplicativos ou Aplicativos descobertos.  

- Na lista de aplicativos, na linha do aplicativo que você deseja marcar como sancionado, selecione os três pontos no final da linha ![pontos para Marcar como sancionado](./media/sanction-three-dots.png "pontos para Marcar como sancionado") e selecione **Marcar como sancionado**.  

     ![Marcar como sancionado](./media/mark-as-sanctioned.png "marcar como sancionado")  


## <a name="use-the-investigation-tools"></a>Usar as ferramentas de investigação  

1. No portal do Cloud App Security, vá para **Investigar**, examine o **Log de atividades** e filtre por um aplicativo específico. Verifique os seguintes itens:  

    - Quem está acessando o seu ambiente de nuvem?  

    - De quais intervalos de IP?  

    - O que é a atividade do administrador?  

    - De quais locais os administradores estão se conectando?  

    - Existem quaisquer dispositivos desatualizados se conectando ao seu ambiente de nuvem?  

    - Logons com falha estão partindo de endereços IP esperados?  

2. Acesse **Investigar** e, em seguida, **Arquivos** e verifique os seguintes itens:  

    - Quantos arquivos são compartilhados publicamente para que qualquer pessoa possa acessá-los sem um link?  

    - Com quais parceiros você está compartilhando arquivos (compartilhamento de saída)?  

    - Algum arquivo tem um nome sigiloso?  

    - Qualquer um dos arquivos está sendo compartilhado com a conta pessoal de outra pessoa?  

3. Acesse **Investigar** e, em seguida, **Usuários e contas** e verifique os seguintes itens:  

    - Alguma conta esteve inativa em um determinado serviço por muito tempo? Talvez você precise revogar a licença desse usuário para esse serviço.  

    - Você deseja saber quais usuários têm uma função específica?  

    - Alguém foi demitido, mas ainda tem acesso a um aplicativo e pode usar esse acesso para roubar informações?  

    - Você deseja revogar a permissão de um usuário a um aplicativo específico ou exigir que um usuário específico use a autenticação multifator?  

    - Faça uma busca detalhada na conta do usuário clicando nos três pontos no final da linha da conta do usuário e selecionando uma ação a ser executada. Execute uma ação, como **Suspender usuário** ou **Remover colaborações do usuário**. Se o usuário foi importado do Azure Active Directory, clique também em **Configurações de conta do Azure AD** para obter fácil acesso a recursos avançados de gerenciamento de usuários. Exemplos de recursos de gerenciamento incluem gerenciamento de grupo, MFA, detalhes sobre as entradas do usuário e a capacidade de bloquear a entrada.

4. Acesse **Investigar**, seguido de **Aplicativos conectados**, e selecione um aplicativo. O painel do aplicativo se abre e fornece informações e insights. Você pode usar as guias na parte superior para verificar:  

    - Que tipo de dispositivos seus usuários estão usando para se conectar ao aplicativo?  

    - Quais tipos de arquivos eles estão salvando na nuvem?  

    - Que atividade está acontecendo no aplicativo agora?  

    - Há algum aplicativo de terceiros conectado ao seu ambiente?  

    - Você estiver familiarizado com esses aplicativos?  

    - Eles estão autorizados para o nível de acesso para o qual têm permissão?  

    - Quantos usuários o implantaram? Quão comuns são esses aplicativos em geral?  
 
    ![Painel de aplicativos](./media/investigate-app.png "investigar aplicativo")  

5. Acesse o **Painel do Cloud Discovery** e verifique os seguintes itens:  

    - Quais aplicativos na nuvem estão sendo usados, até que ponto e por quais usuários?  

    - Para quais fins eles estão sendo usados?  

    - Quantos dados estão sendo carregados nesses aplicativos de nuvem?  

    - Em quais categorias você tem aplicativos de nuvem sancionados e, ainda assim, os usuários estão usando soluções alternativas?  

    - Para a solução alternativa, deseja cancelar a sanção para algum aplicativo de nuvem na sua organização?  

    - Há aplicativos de nuvem que são usados, mas não estão em conformidade com a política da sua organização?  

## <a name="sample-investigation"></a>Investigação de amostra
  
Digamos que você supõe que não há nenhum acesso ao seu ambiente de nuvem por endereços IP de risco. Por exemplo, suponhamos o Tor. Mas você cria uma política de IP arriscado para garantir:  

1. No portal, acesse **Controle** e escolha **Modelos**.  

2. Escolha a **Política de atividade** para o **Tipo**.  

3. No final da linha **Logon de um endereço IP de risco**, escolha o sinal de adição (**+**) para criar uma política.  

4. Altere o nome da política para poder identificá-lo.  

5. Em **Atividades que correspondem a todos os seguintes**, escolha **+** para adicionar um filtro. Role a página para baixo até **Marca de IP** e, em seguida, escolha **Tor**.  

     ![Exemplo de política para IPs arriscados](./media/example-policy-risky-ips.png "Exemplo de política para IPs arriscados")  

Agora que você tem a política em vigor, está surpreso ao ver que recebe um alerta de que a política foi violada.  

1. Vá para a página **Alertas** e exiba o alerta sobre a violação da política.  

2. Se você notar que essa parece uma violação real, contenha ou corrija o risco.  

     Para conter o risco, você pode enviar uma notificação para o usuário para perguntar se a violação foi intencional e se o usuário estava ciente dela.  

     Você também pode detalhar o alerta e suspender o usuário até que possa descobrir o que precisa ser feito.  

3. Se for um evento permitido que provavelmente não ocorrerá novamente, você poderá ignorar o alerta.  

     Se for permitido e esperar-se que ocorra novamente, você poderá modificar a política para evitar que esse tipo de evento seja considerado uma violação no futuro.  

## <a name="next-steps"></a>Próximas etapas
 
Para saber como controlar o aplicativo de nuvem da sua organização, consulte [Controlar](control.md).   

Os clientes Premier também podem escolher o Cloud App Security diretamente no [Portal Premier](https://premier.microsoft.com/).  

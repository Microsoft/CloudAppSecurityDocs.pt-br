---
title: Criar políticas de sessão no Cloud App Security
description: Este artigo descreve o procedimento para configurar uma política de sessão de Controle de Aplicativos de Acesso Condicional do Cloud App Security para obter visibilidade profunda sobre atividades de sessão de usuário e bloquear downloads usando os recursos de proxy reverso.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 745df28a-654c-4abf-9c90-203841169f90
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 5fec505aa7397c2eaa733de750b6030f81daa633
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2019
ms.locfileid: "74460414"
---
# <a name="session-policies"></a>Políticas de sessão 

*Aplica-se ao: Microsoft Cloud App Security*

>[!div class="step-by-step"]
[«ANTERIOR: integração e implantação Controle de Aplicativos de Acesso Condicional para qualquer aplicativo»](proxy-deployment-any-app.md)<br>
[PRÓXIMO: Como criar uma política de acesso »](access-policy-aad.md)


As políticas de sessão do Microsoft Cloud App Security habilitam o monitoramento em tempo real de nível de sessão, oferecendo visibilidade granular de aplicativos de nuvem e a capacidade de executar ações diferentes dependendo da política configurada para uma sessão de usuário. Em vez de [permitir ou bloquear o acesso por completo](access-policy-aad.md), com o controle de sessão, é possível permitir o acesso durante o monitoramento da sessão e/ou limitar atividades de sessão específicas usando os recursos de proxy reverso do Controle de Aplicativo de Acesso Condicional. 

Por exemplo, é possível decidir que, de dispositivos não gerenciados ou, para sessões provenientes de locais específicos, você deseja permitir que o usuário acesse o aplicativo, mas também limitar o download de arquivos confidenciais ou requerer que determinados documentos sejam protegidos no download. As políticas de sessão permitem que você defina esses controles de sessão de usuário e permita o acesso, além de habilitar o seguinte:

- [Monitorar todas as atividades](#monitor-session)
- [Bloquear todos os downloads](#block-download)
- [Bloquear atividades específicas](#block-activities)
- [Proteger arquivos no download](#protect-download)
 
## <a name="prerequisites-to-using-session-policies"></a>Pré-requisitos para usar políticas de sessão

- Licença do Azure AD Premium P1
- Os aplicativos relevantes devem ser [implantados com o Controle de Aplicativo de Acesso Condicional](proxy-deployment-aad.md)
- Uma [política de acesso condicional do Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) que redireciona os usuários para o Microsoft Cloud App Security deve estar em vigor, conforme descrito abaixo.

> [!NOTE]
> As políticas de sessão também dão suporte a aplicativos configurados com provedores de identidade diferentes do Azure AD. Para obter mais informações sobre esse cenário, envie um email para mcaspreview@microsoft.com.

## <a name="create-an-azure-ad-conditional-access-policy"></a>Criar uma política de acesso condicional do Azure AD

As políticas de acesso condicional do Azure Active Directory e as políticas de sessão do Cloud App Security trabalham juntas para examinar cada sessão de usuário e tomar decisões de política para cada aplicativo. Para configurar uma política de acesso condicional no Azure AD, siga este procedimento:

1. Configure uma [política de acesso condicional do Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) com atribuições de um usuário ou grupo de usuários e o aplicativo que você deseja controlar com o Controle de Aplicativos de Acesso Condicional. 

   > [!NOTE]
   > Apenas os aplicativos que foram [implantados com o Controle de Aplicativo de Acesso Condicional](proxy-deployment-aad.md) serão afetados por essa política.

2. Encaminhe usuários para o Microsoft Cloud App Security selecionando **Usar restrições impostas do Controle de Aplicativos de Acesso Condicional** na página **Sessão**.

## <a name="create-a-cloud-app-security-session-policy"></a>Criar uma política de sessão do Cloud App Security 

Para criar uma nova política de sessão, siga este procedimento:

1. No portal, selecione **Controle** e, em seguida, **Políticas**.
2. Na página **Políticas**, clique em **Criar política** e selecione **Política de sessão**.  

3. Na janela **Política de sessão**, atribua um nome para a política, como *Bloquear o download de documentos confidenciais na caixa para usuários de marketing*.

4. No campo **Tipo de controle de sessão**: 

   1. Selecione **Apenas monitorar** se você quiser apenas monitorar atividades por usuários. Essa seleção criará uma política Apenas monitorar para os aplicativos selecionados em que todas as entradas, downloads heurísticos e tipos de Atividade serão baixados.

   2. Selecione **Controlar download de arquivos (com DLP)** se quiser monitorar as atividades do usuário. Você pode executar ações adicionais, como bloquear ou proteger downloads para usuários.
   
   3. Selecione **Bloquear atividades** para bloquear atividades específicas que você pode selecionar usando o filtro **Tipo de atividade**. Todas as atividades de aplicativos selecionados serão monitoradas (e relatadas no Log de atividades). As atividades específicas que você selecionar serão bloqueadas se você selecionar a ação **Bloquear**. As atividades específicas selecionadas gerarão alertas se você selecionar a ação **Testar** e ativar os alertas.

5. Em **Origem da atividade** na seção **Atividades que correspondem a todos os seguintes**, selecione os filtros de atividade adicionais a serem aplicados na política. Esses filtros podem incluir as seguintes opções: 

   - **Marcas de dispositivo**: use este filtro para identificar dispositivos não gerenciados.

   - **Local**: use este filtro para identificar locais desconhecidos (e, portanto, arriscados). 

   - **Endereço IP**: use nesse filtro para filtrar por endereços IP ou usar marcas de endereço IP atribuídas anteriormente. 

   - **Marca de agente do usuário**: use esse filtro para habilitar que a heurística identifique os aplicativos móveis e de área de trabalho. Esse filtro pode ser definido como igual ou diferente do **Cliente nativo**. Esse filtro deve ser testado nos aplicativos móveis e da área de trabalho para cada aplicativo na nuvem.
       
 
     >[!NOTE]
     >As políticas de sessão não dão suporte a aplicativos móveis e de área de trabalho. Os aplicativos móveis e aplicativos da área de trabalho também podem ser bloqueados ou permitidos por meio da criação de uma política de acesso.

6. Se você tiver selecionado a opção de **download do arquivo de controle (com DLP)** :

   1. Em **Origem da atividade** na seção **Arquivos que correspondem a todos os seguintes**, selecione os filtros de arquivos adicionais a serem aplicados na política. Esses filtros podem incluir as seguintes opções:

      - **Rótulo de classificação** – use esse filtro se a organização usar a Proteção de Informações do Azure e seus dados forem protegidos por seus rótulos de classificação. Você pode filtrar arquivos com base no rótulo de Classificação aplicado a eles. Para obter mais informações sobre a integração com a Proteção de Informações do Azure, confira [Integração da Proteção de Informações do Azure](azip-integration.md).

      - **Nome do arquivo** – Use esse filtro para aplicar a política a arquivos específicos.

      - **Tipo de arquivo** – Use esse filtro para aplicar a política a tipos de arquivo específicos, por exemplo, bloquear o download de todos os arquivos. xls.
       
   2. Na seção **Inspeção de conteúdo**, defina se deseja habilitar o exame de documentos e o conteúdo do arquivo pelo mecanismo DLP.
 
   3. Em **Ações**, selecione um dos seguintes itens: 

      - **Testar (Monitorar todas as atividades)** : defina essa ação para permitir o download explicitamente de acordo com os filtros de política que você definir.

      - **Bloquear (bloquear o download de arquivos e monitorar todas as atividades)** : defina essa ação para bloquear explicitamente o download de acordo com os filtros de política que você definir. Para obter mais informações, consulte [Como funciona o bloqueio de download](#block-download).

      - **Proteger (aplicar o rótulo de classificação para baixar e monitorar todas as atividades)** : essa opção só estará disponível se você selecionar **Controlar download de arquivos (com DLP)** em **Política de sessão**. Se sua organização usa a Proteção de Informações do Azure, você pode definir uma **Ação** para aplicar um rótulo de classificação configurado na Proteção de Informações do Azure para o arquivo. Para obter mais informações, consulte [Como funciona o a proteção de download](#protect-download).

7. Você pode **Criar um alerta para cada evento correspondente com a gravidade da política** e definir um limite de alerta. Selecione se deseja que o alerta seja enviado como um email, como uma mensagem de texto ou ambos.


## Monitorar todas as atividades <a name="monitor-session"></a>

Quando você cria uma política de sessão, cada sessão de usuário que corresponde à política é redirecionada para o controle de sessão em vez do aplicativo diretamente. O usuário verá um aviso de monitoramento para que ele saiba que as sessões que estão sendo monitoradas.

Se você não desejar notificar o usuário de que ele está sendo monitorado, poderá desabilitar a mensagem de notificação.

1. Na engrenagem de configurações, selecione **Configurações gerais**. 

2. Em seguida, no **Controle de Aplicativo de Acesso Condicional**, marque a caixa de seleção **Monitoramento de usuário** e desmarque **Notificar os usuários**.

Para manter o usuário dentro da sessão, o Controle de Aplicativo de Acesso Condicional substitui todas as URLs relevantes, os scripts Java e os cookies dentro da sessão do aplicativo por URLs do Microsoft Cloud App Security. Por exemplo, se o aplicativo retornar uma página com links cujos domínios terminam com myapp.com, o Controle de Aplicativos de Acesso Condicional substituirá os links por domínios que terminam com algo como myapp.com.us.cas.ms. Dessa forma, toda a sessão é monitorada pelo Microsoft Cloud App Security.

O Controle de Aplicativo de Acesso Condicional registra os logs de tráfego de todas as sessões de usuário que são roteadas por ele. Os logs de tráfego incluem o agente do usuário, o tempo, o IP, as URLs visitadas e o número de bytes carregados e baixados. Esses logs são analisados e um relatório contínuo, **Controle de Aplicativos de Acesso Condicional do Cloud App Security**, é adicionado à lista de relatórios do Cloud Discovery no painel do Cloud Discovery.

Para exportar esses logs:

1. Acesse a engrenagem de configurações e clique em **Controle de Aplicativo de Acesso Condicional**.
2. No lado direito da tabela, clique no botão Exportar.

   ![botão exportar](./media/export-button.png)
3. Selecione o intervalo do relatório e clique em **Exportar**. Esse processo pode levar algum tempo.

Para baixar o log exportado:

1. Depois que o relatório estiver pronto, vá para **Configurações** e, em seguida **Relatórios exportados**.
2. Na tabela, selecione o relatório relevante na lista de **Logs de tráfego do Controle de Aplicativos de Acesso Condicional** e clique em download.

     ![botão de download](./media/download-button.png)


## Bloquear todos os downloads <a name="block-download"></a>

Quando o **Bloco** for definido como a **Ação** que você deseja executar na política de sessão do Cloud App Security, o Controle de Aplicativos de Acesso Condicional impedirá que um usuário baixe um arquivo conforme os filtros de arquivo da política. Um evento de download é reconhecido pelo Microsoft Cloud App Security para cada aplicativo quando um usuário inicia um download. O Controle de Aplicativos de Acesso Condicional intervirá em tempo real para impedir a execução. Quando é recebido o sinal de que um usuário iniciou um download, o Controle de Aplicativos de Acesso Condicional retorna uma mensagem dizendo **Download restrito** para o usuário e substitui o arquivo baixado por um arquivo de texto. A mensagem do arquivo de texto para o usuário pode ser configurada e personalizada na política da sessão.  

## Bloquear atividades específicas<a name="block-activities"></a>

Quando **Bloquear atividades** é definido como **Tipo de atividade**, você pode selecionar atividades específicas para bloquear em aplicativos específicos. Todas as atividades de aplicativos selecionados serão monitoradas e relatadas no Log de atividades. As atividades específicas que você selecionar serão bloqueadas se você selecionar a ação **Bloquear**. As atividades específicas selecionadas gerarão alertas se você selecionar a ação **Testar** e ativar os alertas.

Escolha **Bloquear atividades específicas** e aplique-as a grupos específicos para criar um modo somente leitura abrangente para sua organização. 

## Proteger arquivos no download <a name="protect-download"></a>

Selecione **Bloquear atividades** para bloquear atividades específicas que você pode localizar usando o filtro **Tipo de atividade**. Todas as atividades de aplicativos selecionados serão monitoradas (e relatadas no Log de atividades). As atividades específicas que você selecionar serão bloqueadas se você selecionar a ação **Bloquear**. As atividades específicas selecionadas gerarão alertas se você selecionar a ação **Testar** e ativar os alertas.

Quando **Proteger** é definido como a **Ação** a ser executada na política de sessão do Cloud App Security, o Controle de Aplicativos de Acesso Condicional determina o rótulo e a proteção subsequentes de um arquivo conforme os filtros de arquivo da política. Os rótulos são configurados no console de Proteção de Informações do Azure e **Proteger** deve ser selecionado no rótulo para que ele seja exibido como uma opção na política do Cloud App Security. Quando um rótulo for selecionado e um arquivo que atende aos critérios da política do Cloud App Security for baixado, o rótulo e a proteção correspondente (com permissões) serão aplicados ao arquivo após o download. O arquivo original permanece como está no aplicativo de nuvem, enquanto o arquivo baixado agora está protegido. Os usuários que tentam acessar o arquivo devem atender os requisitos de permissão determinados pela proteção aplicada.  
 
>[!div class="step-by-step"]
[«ANTERIOR: integração e implantação Controle de Aplicativos de Acesso Condicional para qualquer aplicativo»](proxy-deployment-any-app.md)<br>
[PRÓXIMO: Como criar uma política de acesso »](access-policy-aad.md)

## <a name="next-steps"></a>Próximas etapas
 
[Bloqueando downloads em dispositivos não gerenciados, usando funcionalidades de Controle de Aplicativo de Acesso Condicional do Azure AD](use-case-proxy-block-session-aad.md)   

[!INCLUDE [Open support ticket](includes/support.md)]  
  
  

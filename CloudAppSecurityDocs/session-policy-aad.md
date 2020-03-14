---
title: Criar políticas de sessão no Cloud App Security
description: Este artigo descreve o procedimento para configurar uma Cloud App Security política de sessão de Controle de Aplicativos de Acesso Condicional obter visibilidade profunda das atividades de sessão do usuário e bloquear downloads usando recursos de proxy reverso.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 11/14/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 06a9b0fc0a732f745d370fe28541b0a753bfe0cc
ms.sourcegitcommit: 4f3883a9e85d0aaf2802b10433b221c3f1838d88
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79285720"
---
# <a name="session-policies"></a>Políticas de sessão

*Aplica-se a: Microsoft Cloud App Security*

Microsoft Cloud App Security políticas de sessão habilitam o monitoramento em nível de sessão em tempo real, o que proporciona visibilidade granular dos aplicativos de nuvem e a capacidade de executar ações diferentes dependendo da política definida para uma sessão de usuário. Em vez de permitir [ou bloquear completamente o acesso](access-policy-aad.md), com o controle de sessão, você pode permitir o acesso enquanto monitora a sessão e/ou limita as atividades de sessão específicas usando os recursos de proxy reverso do controle de aplicativos de acesso condicional.

Por exemplo, você pode decidir que de dispositivos não gerenciados ou de sessões provenientes de locais específicos, você deseja permitir que o usuário acesse o aplicativo, mas também limitar o download de arquivos confidenciais ou exigir que determinados documentos sejam protegidos após o download. As políticas de sessão permitem definir esses controles de sessão de usuário e permitir o acesso e permitem que você:

* [Monitorar todas as atividades](#monitor-session)
* [Bloquear todos os downloads](#block-download)
* [Bloquear atividades específicas](#block-activities)
* [Proteger arquivos durante o download](#protect-download)
* [Proteger uploads de arquivos confidenciais](#protect-upload)
* [Instrua os usuários a proteger arquivos confidenciais](#educate-protect)

## <a name="prerequisites-to-using-session-policies"></a>Pré-requisitos para usar políticas de sessão

* Licença do Azure AD Premium P1
* Os aplicativos relevantes devem ser [implantados com controle de aplicativos de acesso condicional](proxy-deployment-aad.md)
* Uma [política de acesso condicional do Azure ad](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) deve estar em vigor para redirecionar os usuários para Microsoft Cloud app Security, conforme descrito abaixo.

> [!NOTE]
> As políticas de sessão também dão suporte a aplicativos configurados com provedores de identidade diferentes do Azure AD. Para obter mais informações sobre esse cenário, envie um email para mcaspreview@microsoft.com.

## <a name="create-an-azure-ad-conditional-access-policy"></a>Criar uma política de acesso condicional do Azure AD

Azure Active Directory políticas de acesso condicional e Cloud App Security políticas de sessão funcionam em conjunto para examinar cada sessão do usuário e tomar decisões sobre a política para cada aplicativo. Para configurar uma política de acesso condicional no Azure AD, siga este procedimento:

1. Configure uma [política de acesso condicional do Azure ad](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) com atribuições para um usuário ou grupo de usuários e o aplicativo que você deseja controlar com o controle de aplicativos de acesso condicional.

    > [!NOTE]
    > Somente os aplicativos que foram [implantados com controle de aplicativos de acesso condicional](proxy-deployment-aad.md) serão afetados por essa política.

2. Encaminhe os usuários para Microsoft Cloud App Security selecionando a **controle de aplicativos de acesso condicional restrições impostas** na página da **sessão** .

## <a name="create-a-cloud-app-security-session-policy"></a>Criar uma política de sessão de Cloud App Security

Para criar uma nova política de sessão, siga este procedimento:

1. No portal, selecione **controle** seguido por **políticas**.
1. Na página **políticas** , clique em **criar política** e selecione **política de sessão**.
1. Na janela **política de sessão** , atribua um nome para a política, como *Bloquear download de documentos confidenciais no box para usuários de marketing*.
1. No campo **tipo de controle de sessão** :

    1. Selecione **monitorar somente** se você quiser monitorar atividades por usuários. Essa seleção criará uma política monitorar apenas para os aplicativos selecionados onde todas as entradas, downloads heurísticos e tipos de atividade serão baixados.

    1. Selecione **controlar arquivo baixar (com DLP)** se você quiser monitorar as atividades do usuário. Você pode executar ações adicionais como bloquear ou proteger downloads para usuários.
    1. Selecione **bloquear atividades** para bloquear atividades específicas, que você pode selecionar usando o filtro de **tipo de atividade** . Todas as atividades dos aplicativos selecionados serão monitoradas (e relatadas no log de atividades). As atividades específicas que você selecionar serão bloqueadas se você selecionar a ação **Bloquear** . As atividades específicas que você selecionou emitirão alertas se você selecionar a ação de **teste** e tiver alertas ativados.
1. Em **origem da atividade** na seção **atividades correspondentes a todas as seções a seguir** , selecione filtros de atividade adicionais a serem aplicados à política. Esses filtros podem incluir as seguintes opções:

    * **Marcas de dispositivo**: Use este filtro para identificar dispositivos não gerenciados.

    * **Local**: Use este filtro para identificar locais desconhecidos (e, portanto, arriscados).

    * **Endereço IP**: Use este filtro para filtrar por endereços IP ou use marcas de endereço IP atribuídas anteriormente.

    * **Marca de agente do usuário**: Use este filtro para habilitar a heurística para identificar aplicativos móveis e da área de trabalho. Esse filtro pode ser definido como Equals ou não é um **cliente nativo**igual. Esse filtro deve ser testado em seus aplicativos móveis e de área de trabalho para cada aplicativo de nuvem.

    >[!NOTE]
    >As políticas de sessão não dão suporte a aplicativos móveis e de desktop. Aplicativos móveis e aplicativos de área de trabalho também podem ser bloqueados ou permitidos pela criação de uma política de acesso.

1. Se você selecionou a opção para **controlar o download do arquivo (com DLP)** :

    1. Em **origem da atividade** nos **arquivos correspondentes a todas as seções a seguir** , selecione filtros de arquivo adicionais para aplicar à política. Esses filtros podem incluir as seguintes opções:

        * **Rótulo de classificação** – Use esse filtro se sua organização usar a proteção de informações do Azure e seus dados tiverem sido protegidos por seus rótulos de classificação. Você pode filtrar arquivos com base no rótulo de classificação aplicado a eles. Para obter mais informações sobre a integração com a proteção de informações do Azure, consulte [integração da proteção de informações do Azure](azip-integration.md).

        * **Nome do arquivo** – Use esse filtro para aplicar a política a arquivos específicos.
        * **Tipo de arquivo** – Use esse filtro para aplicar a política a tipos de arquivo específicos, por exemplo, bloquear download para todos os arquivos. xls.
    2. Na seção **inspeção de conteúdo** , defina se deseja habilitar o mecanismo DLP para verificar documentos e conteúdo do arquivo.

    3. Em **ações**, selecione um dos seguintes itens:

        * **Testar (monitorar todas as atividades)** : defina essa ação para permitir o download explicitamente de acordo com os filtros de política definidos.

        * **Bloquear (bloquear arquivo baixar e monitorar todas as atividades)** : defina esta ação para bloquear explicitamente o download de acordo com os filtros de política definidos. Para obter mais informações, consulte [como bloquear download funciona](#block-download).

        * **Proteger (Aplicar rótulo de classificação para baixar e monitorar todas as atividades)** : essa opção só estará disponível se você selecionou **controlar download de arquivo (com DLP)** em **política de sessão**. Se sua organização usa a proteção de informações do Azure, você pode definir uma **ação** para aplicar um rótulo de classificação definido na proteção de informações do Azure ao arquivo. Para obter mais informações, consulte [como proteger o download funciona](#protect-download).

1. Você pode **criar um alerta para cada evento correspondente com a severidade da política** e definir um limite de alerta. Selecione se você deseja o alerta como um email, uma mensagem de texto ou ambos.

## <a name="monitor-session"></a>Monitorar todas as atividades

Quando você cria uma política de sessão, cada sessão de usuário que corresponde à política é redirecionada para o controle de sessão em vez de diretamente para o aplicativo. O usuário verá um aviso de monitoramento para que eles saibam que suas sessões estão sendo monitoradas.

Se você não quiser notificar o usuário de que ele está sendo monitorado, você pode desabilitar a mensagem de notificação.

1. Na engrenagem configurações, selecione **configurações gerais**.

2. Em seguida, em **controle de aplicativos de acesso condicional** selecione **monitoramento de usuário** e desmarque a caixa de seleção **notificar usuários** .

Para manter o usuário dentro da sessão, Controle de Aplicativos de Acesso Condicional substitui todas as URLs relevantes, scripts Java e cookies na sessão de aplicativo por Microsoft Cloud App Security URLs. Por exemplo, se o aplicativo retornar uma página com links cujos domínios terminam com myapp.com, Controle de Aplicativos de Acesso Condicional substituirá os links com domínios que terminam com algo como myapp.com.us.cas.ms. Dessa forma, toda a sessão é monitorada pelo Microsoft Cloud App Security.

Controle de Aplicativos de Acesso Condicional registra os logs de tráfego de cada sessão de usuário que é roteada através dele. Os logs de tráfego incluem a hora, o IP, o agente do usuário, as URLs visitadas e o número de bytes carregados e baixados. Esses logs são analisados e um relatório contínuo, **Cloud App Security controle de aplicativos de acesso condicional**, é adicionado à lista de relatórios de Cloud Discovery no painel Cloud Discovery.

Para exportar esses logs:

1. Vá para as configurações engrenagem e clique em **controle de aplicativos de acesso condicional**.
2. No lado direito da tabela, clique no botão Exportar.

    ![botão Exportar](./media/export-button.png)
3. Selecione o intervalo do relatório e clique em **Exportar**. Esse processo pode levar algum tempo.

Para baixar o log exportado:

1. Depois que o relatório estiver pronto, vá para **configurações** e, em seguida, **relatórios exportados**.
2. Na tabela, selecione o relatório relevante na lista de **controle de aplicativos de acesso condicional logs de tráfego** e clique em baixar.

    ![botão baixar](./media/download-button.png)

## <a name="block-download"></a>Bloquear todos os downloads

Quando o **bloco** é definido como a **ação** que você deseja executar na política de sessão de Cloud app Security, controle de aplicativos de acesso condicional impede que um usuário Baixe um arquivo de acordo com os filtros de arquivo da política. Um evento de download é reconhecido pelo Microsoft Cloud App Security para cada aplicativo quando um usuário inicia um download. Controle de Aplicativos de Acesso Condicional intervi em tempo real para impedir que ele seja executado. Quando é recebido o sinal de que um usuário iniciou um download, Controle de Aplicativos de Acesso Condicional retorna uma mensagem de **Download restrito** ao usuário e substitui o arquivo baixado por um arquivo de texto. A mensagem do arquivo de texto para o usuário pode ser configurada e personalizada da política de sessão.

## <a name="block-activities"></a>Bloquear atividades específicas

Quando **as atividades de bloqueio** são definidas como o **tipo de atividade**, você pode selecionar atividades específicas para bloquear em aplicativos específicos. Todas as atividades dos aplicativos selecionados serão monitoradas e relatadas no log de atividades. As atividades específicas que você selecionar serão bloqueadas se você selecionar a ação **Bloquear** . As atividades específicas que você selecionou emitirão alertas se você selecionar a ação de **teste** e tiver alertas ativados.

**Bloqueie atividades específicas** e aplique-as a grupos específicos para criar um modo de somente leitura abrangente para sua organização.

## <a name="protect-download"></a>Proteger arquivos durante o download

Selecione **bloquear atividades** para bloquear atividades específicas, que você pode encontrar usando o filtro de **tipo de atividade** . Todas as atividades dos aplicativos selecionados serão monitoradas (e relatadas no log de atividades). As atividades específicas que você selecionar serão bloqueadas se você selecionar a ação **Bloquear** . As atividades específicas que você selecionou emitirão alertas se você selecionar a ação de **teste** e tiver alertas ativados.

Quando a **proteção** é definida como a **ação** a ser executada na política de sessão de Cloud app Security, controle de aplicativos de acesso condicional impõe o rotulamento e a proteção subsequente de um arquivo de acordo com os filtros de arquivo da política. Os rótulos são configurados no console da proteção de informações do Azure e a **proteção** deve ser selecionada dentro do rótulo para que ele seja exibido como uma opção na política de Cloud app Security. Quando um rótulo é selecionado, e um arquivo é baixado que atende aos critérios da política de Cloud App Security, o rótulo e a proteção correspondente (com permissões) são aplicados ao arquivo após o download. O arquivo original permanece no estado em que se encontra no aplicativo de nuvem enquanto o arquivo baixado agora está protegido. Os usuários que tentarem acessar o arquivo devem atender aos requisitos de permissão determinados pela proteção aplicada.

O Cloud App Security atualmente dá suporte à aplicação de [Rótulos de classificação da proteção de informações do Azure](azip-integration.md) para os seguintes tipos de arquivo:

* Word: docm, docx, dotm, dotx
* Excel: xlam, xlsm, xlsx, xltx
* PowerPoint: potm, potx, ppsx, ppsm, pptm, pptx
* PDF
  > [!NOTE]
  > Para PDF, você deve usar rótulos unificados.

## <a name="protect-upload"></a>Proteger uploads de arquivos confidenciais

Quando o **carregamento de arquivo de controle (com DLP)** é definido como o **tipo de controle de sessão** na política de sessão de Cloud app Security, controle de aplicativos de acesso condicional impede que um usuário carregue um arquivo de acordo com os filtros de arquivo da política. Quando um evento de upload é reconhecido, Controle de Aplicativos de Acesso Condicional intervi em tempo real para determinar se o arquivo é confidencial e precisa de proteção. Se o arquivo tiver dados confidenciais e não tiver um rótulo adequado, o carregamento do arquivo será bloqueado.

Por exemplo, você pode criar uma política que verifica o conteúdo de um arquivo para determinar se ele contém uma correspondência de conteúdo confidencial, como um número de seguro social. Se ele contiver conteúdo confidencial e não for rotulado com um rótulo confidencial da proteção de informações do Azure, o upload do arquivo será bloqueado. Quando o arquivo é bloqueado, você pode [exibir uma mensagem personalizada para o usuário](#educate-protect) instruindo-o sobre como rotular o arquivo para carregá-lo. Ao fazer isso, você garante que os arquivos armazenados em seus aplicativos de nuvem estejam em conformidade com suas políticas.

## <a name="educate-protect"></a>Instrua os usuários a proteger arquivos confidenciais

É importante instruir os usuários quando eles estiverem violando uma política, para que eles aprendam a cumprir suas políticas organizacionais. Como cada empresa tem necessidades e políticas exclusivas, Cloud App Security permite que você personalize os filtros de uma política e a mensagem que ele exibe para o usuário quando uma violação é detectada. Você pode fornecer orientações específicas para seus usuários, como fornecer instruções sobre como rotular um arquivo apropriadamente ou como registrar um dispositivo não gerenciado, para garantir que os arquivos sejam carregados com êxito.

Por exemplo, se um usuário carregar um arquivo sem um rótulo de proteção de informações do Azure, uma mensagem poderá ser exibida explicando que o arquivo contém conteúdo confidencial que requer um rótulo apropriado. Da mesma forma, se um usuário tentar carregar um documento de um dispositivo não gerenciado, uma mensagem com instruções sobre como registrar esse dispositivo ou um que fornece mais explicações sobre por que o dispositivo deve ser registrado pode ser exibida.

## <a name="next-steps"></a>Próximas etapas

>[!div class="nextstepaction"]
> [«ANTERIOR: integração e implantação Controle de Aplicativos de Acesso Condicional para qualquer aplicativo»](proxy-deployment-any-app.md)

>[!div class="nextstepaction"]
> [Em seguida: como criar uma política de acesso»](access-policy-aad.md)

## <a name="see-also"></a>Veja também

> [!div class="nextstepaction"]
> [Bloqueando downloads em dispositivos não gerenciados usando o Azure AD Controle de Aplicativos de Acesso Condicional](use-case-proxy-block-session-aad.md)

[!INCLUDE [Open support ticket](includes/support.md)]  

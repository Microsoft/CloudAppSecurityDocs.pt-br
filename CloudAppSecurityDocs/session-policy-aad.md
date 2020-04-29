---
title: Criar políticas de sessão no Cloud App Security
description: Este artigo descreve o procedimento para configurar uma política de sessão de Controle de Aplicativos de Acesso Condicional do Cloud App Security para obter visibilidade profunda sobre atividades de sessão de usuário e bloquear downloads usando os recursos de proxy reverso.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/31/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 1b6bd39d420b113a85d9d171ab076769240b9d00
ms.sourcegitcommit: ecb1835d1cd880de38f32ce7a7031b0015f3cae5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81228487"
---
# <a name="session-policies"></a>Políticas de sessão

*Aplica-se a: Microsoft Cloud App Security*

As políticas de sessão do Microsoft Cloud App Security habilitam o monitoramento em tempo real de nível de sessão, oferecendo visibilidade granular de aplicativos de nuvem e a capacidade de executar ações diferentes dependendo da política configurada para uma sessão de usuário. Em vez de [permitir ou bloquear o acesso por completo](access-policy-aad.md), com o controle de sessão, é possível permitir o acesso durante o monitoramento da sessão e/ou limitar atividades de sessão específicas usando os recursos de proxy reverso do Controle de Aplicativo de Acesso Condicional.

Por exemplo, é possível decidir que, de dispositivos não gerenciados ou, para sessões provenientes de locais específicos, você deseja permitir que o usuário acesse o aplicativo, mas também limitar o download de arquivos confidenciais ou requerer que determinados documentos sejam protegidos no download. As políticas de sessão permitem que você defina esses controles de sessão de usuário e permita o acesso, além de habilitar o seguinte:

* [Monitorar todas as atividades](#monitor-session)
* [Bloquear todos os downloads](#block-download)
* [Bloquear atividades específicas](#block-activities)
* [Proteger arquivos no download](#protect-download)
* [Proteger uploads de arquivos confidenciais](#protect-upload)
* [Instrua os usuários a proteger arquivos confidenciais](#educate-protect)

## <a name="prerequisites-to-using-session-policies"></a>Pré-requisitos para usar políticas de sessão

* Azure AD Premium licença P1 ou a licença exigida pela sua solução IdP (provedor de identidade)
* Os aplicativos relevantes devem ser [implantados com o Controle de Aplicativo de Acesso Condicional](proxy-deployment-aad.md)
* Verifique se você configurou sua solução IdP para trabalhar com Cloud App Security, da seguinte maneira:
  * Para [acesso condicional do Azure ad](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal), consulte [Configurar a integração com o Azure ad](proxy-deployment-aad.md#configure-integration-with-azure-ad)
  * Para outras soluções IdP, consulte [Configurar a integração com outras soluções IDP](proxy-deployment-aad.md#configure-integration-with-other-idp-solutions)

## <a name="create-a-cloud-app-security-session-policy"></a>Criar uma política de sessão do Cloud App Security

Para criar uma nova política de sessão, siga este procedimento:

1. No portal, selecione **Controle** e, em seguida, **Políticas**.
1. Na página **Políticas**, clique em **Criar política** e selecione **Política de sessão**.
1. Na janela **Política de sessão**, atribua um nome para a política, como *Bloquear o download de documentos confidenciais na caixa para usuários de marketing*.
1. No campo **Tipo de controle de sessão**:

    1. Selecione **Apenas monitorar** se você quiser apenas monitorar atividades por usuários. Essa seleção criará uma política Apenas monitorar para os aplicativos selecionados em que todas as entradas, downloads heurísticos e tipos de Atividade serão baixados.

    1. Selecione **Controlar download de arquivos (com DLP)** se quiser monitorar as atividades do usuário. Você pode executar ações adicionais, como bloquear ou proteger downloads para usuários.
    1. Selecione **bloquear atividades** para bloquear atividades específicas, que você pode selecionar usando o filtro de **tipo de atividade** . Todas as atividades de aplicativos selecionados serão monitoradas (e relatadas no Log de atividades). As atividades específicas que você selecionar serão bloqueadas se você selecionar a ação **Bloquear**. As atividades específicas selecionadas gerarão alertas se você selecionar a ação **Testar** e ativar os alertas.
1. Em **Origem da atividade** na seção **Atividades que correspondem a todos os seguintes**, selecione os filtros de atividade adicionais a serem aplicados na política. Esses filtros podem incluir as seguintes opções:

    * **Marcas de dispositivo**: use este filtro para identificar dispositivos não gerenciados.

    * **Local**: use este filtro para identificar locais desconhecidos (e, portanto, arriscados).

    * **Endereço IP**: use nesse filtro para filtrar por endereços IP ou usar marcas de endereço IP atribuídas anteriormente.

    * **Marca de agente do usuário**: use esse filtro para habilitar que a heurística identifique os aplicativos móveis e de área de trabalho. Esse filtro pode ser definido como igual ou diferente do **Cliente nativo**. Esse filtro deve ser testado nos aplicativos móveis e da área de trabalho para cada aplicativo na nuvem.

    >[!NOTE]
    >As políticas de sessão não dão suporte a aplicativos móveis e de desktop. Os aplicativos móveis e aplicativos da área de trabalho também podem ser bloqueados ou permitidos por meio da criação de uma política de acesso.

1. Se você tiver selecionado a opção de **download do arquivo de controle (com DLP)**:

    1. Em **Origem da atividade** na seção **Arquivos que correspondem a todos os seguintes**, selecione os filtros de arquivos adicionais a serem aplicados na política. Esses filtros podem incluir as seguintes opções:

        * **Rótulo de classificação** – Use esse filtro se sua organização usar a proteção de informações do Azure e seus dados tiverem sido protegidos por seus rótulos de classificação. Você pode filtrar arquivos com base no rótulo de Classificação aplicado a eles. Para obter mais informações sobre a integração com a Proteção de Informações do Azure, confira [Integração da Proteção de Informações do Azure](azip-integration.md).

        * **Nome do arquivo** – Use esse filtro para aplicar a política a arquivos específicos.
        * **Tipo de arquivo** – Use esse filtro para aplicar a política a tipos de arquivo específicos, por exemplo, bloquear o download de todos os arquivos. xls.
    2. Na seção **Inspeção de conteúdo**, defina se deseja habilitar o exame de documentos e o conteúdo do arquivo pelo mecanismo DLP.

    3. Em **Ações**, selecione um dos seguintes itens:

        * **Testar (Monitorar todas as atividades)**: defina essa ação para permitir o download explicitamente de acordo com os filtros de política que você definir.

        * **Bloquear (bloquear o download de arquivos e monitorar todas as atividades)**: defina essa ação para bloquear explicitamente o download de acordo com os filtros de política que você definir. Para obter mais informações, consulte [Como funciona o bloqueio de download](#block-download).

        * **Proteger (aplicar o rótulo de classificação para baixar e monitorar todas as atividades)**: essa opção só estará disponível se você selecionar **Controlar download de arquivos (com DLP)** em **Política de sessão**. Se sua organização usa a Proteção de Informações do Azure, você pode definir uma **Ação** para aplicar um rótulo de classificação configurado na Proteção de Informações do Azure para o arquivo. Para obter mais informações, consulte [Como funciona o a proteção de download](#protect-download).

1. Você pode **Criar um alerta para cada evento correspondente com a gravidade da política** e definir um limite de alerta. Selecione se deseja que o alerta seja enviado como um email, como uma mensagem de texto ou ambos.

## <a name="monitor-all-activities"></a><a name="monitor-session"></a>Monitorar todas as atividades

Quando você cria uma política de sessão, cada sessão de usuário que corresponde à política é redirecionada para o controle de sessão em vez do aplicativo diretamente. O usuário verá um aviso de monitoramento para que ele saiba que as sessões que estão sendo monitoradas.

Se você não desejar notificar o usuário de que ele está sendo monitorado, poderá desabilitar a mensagem de notificação.

1. Na engrenagem de configurações, selecione **Configurações gerais**.

2. Em seguida, no **Controle de Aplicativo de Acesso Condicional**, marque a caixa de seleção **Monitoramento de usuário** e desmarque **Notificar os usuários**.

Para manter o usuário dentro da sessão, o Controle de Aplicativo de Acesso Condicional substitui todas as URLs relevantes, os scripts Java e os cookies dentro da sessão do aplicativo por URLs do Microsoft Cloud App Security. Por exemplo, se o aplicativo retornar uma página com links cujos domínios terminam com myapp.com, Controle de Aplicativos de Acesso Condicional substituirá os links com domínios que terminam com algo como myapp.com.us.cas.ms. Dessa forma, toda a sessão é monitorada pelo Microsoft Cloud App Security.

O Controle de Aplicativo de Acesso Condicional registra os logs de tráfego de todas as sessões de usuário que são roteadas por ele. Os logs de tráfego incluem o agente do usuário, o tempo, o IP, as URLs visitadas e o número de bytes carregados e baixados. Esses logs são analisados e um relatório contínuo, **Controle de Aplicativos de Acesso Condicional do Cloud App Security**, é adicionado à lista de relatórios do Cloud Discovery no painel do Cloud Discovery.

Para exportar esses logs:

1. Acesse a engrenagem de configurações e clique em **Controle de Aplicativo de Acesso Condicional**.
2. No lado direito da tabela, clique no botão Exportar.

    ![botão exportar](./media/export-button.png)
3. Selecione o intervalo do relatório e clique em **Exportar**. Esse processo pode demorar algum tempo.

Para baixar o log exportado:

1. Depois que o relatório estiver pronto, vá para **Configurações** e, em seguida **Relatórios exportados**.
2. Na tabela, selecione o relatório relevante na lista de **Logs de tráfego do Controle de Aplicativos de Acesso Condicional** e clique em download.

    ![botão download](./media/download-button.png)

## <a name="block-all-downloads"></a><a name="block-download"></a>Bloquear todos os downloads

Quando o **bloco** é definido como a **ação** que você deseja executar na política de sessão de Cloud app Security, controle de aplicativos de acesso condicional impede que um usuário Baixe um arquivo de acordo com os filtros de arquivo da política. Um evento de download é reconhecido pelo Microsoft Cloud App Security para cada aplicativo quando um usuário inicia um download. O Controle de Aplicativos de Acesso Condicional intervirá em tempo real para impedir a execução. Quando é recebido o sinal de que um usuário iniciou um download, o Controle de Aplicativos de Acesso Condicional retorna uma mensagem dizendo **Download restrito** para o usuário e substitui o arquivo baixado por um arquivo de texto. A mensagem do arquivo de texto para o usuário pode ser configurada e personalizada na política da sessão.

## <a name="block-specific-activities"></a><a name="block-activities"></a>Bloquear atividades específicas

Quando **Bloquear atividades** é definido como **Tipo de atividade**, você pode selecionar atividades específicas para bloquear em aplicativos específicos. Todas as atividades de aplicativos selecionados serão monitoradas e relatadas no Log de atividades. As atividades específicas que você selecionar serão bloqueadas se você selecionar a ação **Bloquear**. As atividades específicas selecionadas gerarão alertas se você selecionar a ação **Testar** e ativar os alertas.

Escolha **Bloquear atividades específicas** e aplique-as a grupos específicos para criar um modo somente leitura abrangente para sua organização.

## <a name="protect-files-on-download"></a><a name="protect-download"></a>Proteger arquivos no download

Selecione **Bloquear atividades** para bloquear atividades específicas que você pode localizar usando o filtro **Tipo de atividade**. Todas as atividades de aplicativos selecionados serão monitoradas (e relatadas no Log de atividades). As atividades específicas que você selecionar serão bloqueadas se você selecionar a ação **Bloquear**. As atividades específicas selecionadas gerarão alertas se você selecionar a ação **Testar** e ativar os alertas.

Quando a **proteção** é definida como a **ação** a ser executada na política de sessão de Cloud app Security, controle de aplicativos de acesso condicional impõe o rotulamento e a proteção subsequente de um arquivo de acordo com os filtros de arquivo da política. Os rótulos são configurados no console de Proteção de Informações do Azure e **Proteger** deve ser selecionado no rótulo para que ele seja exibido como uma opção na política do Cloud App Security. Quando um rótulo for selecionado e um arquivo que atende aos critérios da política do Cloud App Security for baixado, o rótulo e a proteção correspondente (com permissões) serão aplicados ao arquivo após o download. O arquivo original permanece como está no aplicativo de nuvem, enquanto o arquivo baixado agora está protegido. Os usuários que tentam acessar o arquivo devem atender os requisitos de permissão determinados pela proteção aplicada.

O Cloud App Security atualmente dá suporte à aplicação de [Rótulos de classificação da proteção de informações do Azure](azip-integration.md) para os seguintes tipos de arquivo:

* Word: docm, docx, dotm, dotx
* Excel: xlam, xlsm, xlsx, xltx
* PowerPoint: potm, potx, ppsx, ppsm, pptm, pptx
* PDF
  > [!NOTE]
  > Para PDF, você deve usar rótulos unificados.

## <a name="protect-uploads-of-sensitive-files"></a><a name="protect-upload"></a>Proteger uploads de arquivos confidenciais

Quando o **carregamento de arquivo de controle (com DLP)** é definido como o **tipo de controle de sessão** na política de sessão de Cloud app Security, controle de aplicativos de acesso condicional impede que um usuário carregue um arquivo de acordo com os filtros de arquivo da política. Quando um evento de upload é reconhecido, Controle de Aplicativos de Acesso Condicional intervi em tempo real para determinar se o arquivo é confidencial e precisa de proteção. Se o arquivo tiver dados confidenciais e não tiver um rótulo adequado, o carregamento do arquivo será bloqueado.

Por exemplo, você pode criar uma política que verifica o conteúdo de um arquivo para determinar se ele contém uma correspondência de conteúdo confidencial, como um número de seguro social. Se ele contiver conteúdo confidencial e não for rotulado com um rótulo confidencial da proteção de informações do Azure, o upload do arquivo será bloqueado. Quando o arquivo é bloqueado, você pode [exibir uma mensagem personalizada para o usuário](#educate-protect) instruindo-o sobre como rotular o arquivo para carregá-lo. Ao fazer isso, você garante que os arquivos armazenados em seus aplicativos de nuvem estejam em conformidade com suas políticas.

## <a name="educate-users-to-protect-sensitive-files"></a><a name="educate-protect"></a>Instrua os usuários a proteger arquivos confidenciais

É importante instruir os usuários quando eles estiverem violando uma política, para que eles aprendam a cumprir suas políticas organizacionais. Como cada empresa tem necessidades e políticas exclusivas, Cloud App Security permite que você personalize os filtros de uma política e a mensagem que ele exibe para o usuário quando uma violação é detectada. Você pode fornecer orientações específicas para seus usuários, como fornecer instruções sobre como rotular um arquivo apropriadamente ou como registrar um dispositivo não gerenciado, para garantir que os arquivos sejam carregados com êxito.

Por exemplo, se um usuário carregar um arquivo sem um rótulo de proteção de informações do Azure, uma mensagem poderá ser exibida explicando que o arquivo contém conteúdo confidencial que requer um rótulo apropriado. Da mesma forma, se um usuário tentar carregar um documento de um dispositivo não gerenciado, uma mensagem com instruções sobre como registrar esse dispositivo ou um que fornece mais explicações sobre por que o dispositivo deve ser registrado pode ser exibida.

## <a name="next-steps"></a>Próximas etapas

>[!div class="nextstepaction"]
> [«ANTERIOR: integração e implantação Controle de Aplicativos de Acesso Condicional para qualquer aplicativo»](proxy-deployment-any-app.md)

>[!div class="nextstepaction"]
> [PRÓXIMO: Como criar uma política de acesso »](access-policy-aad.md)

## <a name="see-also"></a>Confira também

> [!div class="nextstepaction"]
> [Bloqueando downloads em dispositivos não gerenciados usando o Azure AD Controle de Aplicativos de Acesso Condicional](use-case-proxy-block-session-aad.md)

[!INCLUDE [Open support ticket](includes/support.md)]  

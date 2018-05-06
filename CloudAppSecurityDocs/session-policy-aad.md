---
title: Criar políticas de sessão para obter visibilidade profunda sobre as atividades de sessão de usuário e bloquear downloads | Microsoft Docs
description: Este tópico descreve o procedimento para configurar uma política de sessão do proxy do Cloud App Security a fim de obter visibilidade profunda sobre atividades de sessão de usuário e bloquear downloads.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/22/2018
ms.topic: article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 745df28a-654c-4abf-9c90-203841169f90
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: b414597e499919d9d6251777c9bdbea160cac430
ms.sourcegitcommit: 45311f2cafef79483e40d971a4c61c7673834d96
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2018
---
*Aplica-se ao: Microsoft Cloud App Security*

# <a name="session-policies"></a>Políticas de sessão 

> [!NOTE]
> Este é um recurso de versão prévia.

As políticas de sessão do Microsoft Cloud App Security habilitam o monitoramento em tempo real de nível de sessão, oferecendo visibilidade granular de aplicativos de nuvem e a capacidade de executar ações diferentes dependendo da política configurada para uma sessão de usuário. Em vez de [permitir ou bloquear o acesso por completo](access-policy-aad.md), com o controle de sessão, é possível permitir o acesso durante o monitoramento da sessão e/ou limitar atividades de sessão específicas. 

Por exemplo, é possível decidir que, de dispositivos não gerenciados ou, para sessões provenientes de locais específicos, você deseja permitir que o usuário acesse o aplicativo, mas também limitar o download de arquivos confidenciais ou requerer que determinados documentos sejam protegidos no download. As políticas de sessão permitem que você defina esses controles de sessão de usuário e permita o acesso, além de habilitar o seguinte:

- [Monitorar todas as atividades](#monitor-session)
- [Bloquear todos os downloads](#block-download)
- [Bloquear atividades específicas](#block-activities)
- [Proteger arquivos no download](#protect-download)
 

## <a name="prerequisites-to-using-session-policies"></a>Pré-requisitos para usar políticas de sessão

- Licença do Azure AD Premium P2
- Os aplicativos relevantes devem ser [implantados com o proxy](proxy-deployment-aad.md)
- Uma [política de acesso condicional do Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) que redireciona os usuários para o proxy do Cloud App Security deve estar em vigor, conforme descrito abaixo.

> [!NOTE]
> - As políticas de sessão também dão suporte a aplicativos configurados com provedores de identidade diferentes do Azure AD na Versão Prévia Privada. Para obter mais informações sobre a Versão Prévia Privada, envie um email para mcaspreview@microsoft.com.

## <a name="create-an-azure-ad-conditional-access-policy"></a>Criar uma política de acesso condicional do Azure AD

As políticas de acesso condicional do Azure Active Directory e as políticas de sessão do Cloud App Security trabalham juntas para examinar cada sessão de usuário e tomar decisões de política para cada aplicativo. Para configurar uma política de acesso condicional no Azure AD, siga este procedimento:

1. Configure uma [política de acesso condicional do Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) com atribuições de usuário ou grupo de usuários e o aplicativo SAML que você deseja controlar com o proxy do Cloud App Security. 

   > [!NOTE]
   > Apenas os aplicativos que foram [implantados com o proxy](proxy-deployment-aad.md) serão afetados por essa política.

2. Roteie usuários para o proxy do Cloud App Security selecionando **Usar restrições impostas pelo proxy** na folha **Sessão**.

   ![Acesso condicional do Azure AD às restrições do proxy](./media/proxy-deploy-restrictions-aad.png)

## <a name="create-a-cloud-app-security-session-policy"></a>Criar uma política de sessão do Cloud App Security 

Para criar uma nova política de sessão, siga este procedimento:

1. No portal, selecione **Controle** e, em seguida, **Políticas**.
2. Na página **Políticas**, clique em **Criar política** e selecione **Política de sessão**.  

   ![Criar política de sessão](./media/create-session-policy.png)

3. Na janela **Política de sessão**, atribua um nome para a política, como *Bloquear o download de documentos confidenciais na caixa para usuários de marketing*.

   ![Nova política de sessão](./media/new-session-policy.png)

4. No campo **Tipo de controle de sessão**: 

   1. Selecione **Apenas monitorar** se você quiser apenas monitorar atividades por usuários. Isso criará uma política Apenas monitorar em que todas as entradas, downloads heurísticos e tipos de atividades serão baixados para os aplicativos que você selecionou.

   2. Selecione **controlar o download do arquivo (com DLP)** se você desejar monitorar as atividades do usuário e executar ações adicionais, como bloquear ou proteger downloads para usuários.

      ![tipo de controle da política de sessão](./media/session-policy-control-type.png)
   
   3. Selecione **Bloquear atividades** para bloquear atividades específicas que você pode selecionar usando o filtro **Tipo de atividade**. Todas as atividades de aplicativos selecionados serão monitoradas (e relatadas no Log de atividades). As atividades específicas que você selecionar serão bloqueadas se você marcar a ação **Bloquear**, e as atividades específicas que você selecionou gerarão alertas se você selecionar a ação **Testar** e ativar os alertas.

1. Em **Origem da atividade** na seção **Atividades que correspondem a todos os seguintes**, selecione os filtros de atividade adicionais a serem aplicados na política. Eles podem incluir as seguintes opções: 

   - **Marcas de dispositivo**: use este filtro para identificar dispositivos não gerenciados.

   - **Local**: use este filtro para identificar locais desconhecidos (e, portanto, arriscados). 

   - **Endereço IP**: use nesse filtro para filtrar por endereços IP ou usar marcas de endereço IP atribuídas anteriormente. 

   - **Marca de agente do usuário**: use esse filtro para habilitar que a heurística identifique os aplicativos móveis e de área de trabalho. Esse filtro pode ser configurado como igual a ou não igual ao **Cliente nativo** e deve ser testado em relação a seus aplicativos móveis e de área de trabalho para cada aplicativo de nuvem.
         
       ![suporte de cliente nativo](./media/user-agent-tag.png)

     >[!NOTE]
     >As políticas de sessão não dão suporte a aplicativos móveis e de área de trabalho. Certifique-se de testar as políticas de sessão para ver se elas não interferem com a funcionalidade de aplicativo móvel e da área de trabalho. Se necessário, exclua os aplicativos móveis e de área de trabalho das políticas de sessão.

     ![origem da atividade da política de sessão](./media/session-policy-activity-filters.png)

6. Se você tiver selecionado a opção de **download do arquivo de controle (com DLP)**:

   1. Em **Origem da atividade** na seção **Arquivos que correspondem a todos os seguintes**, selecione os filtros de arquivos adicionais a serem aplicados na política. Eles podem incluir as seguintes opções:

      - **Rótulo de classificação** – Use esse filtro se sua organização usar a Proteção de Informações do Azure e seus dados forem protegidos por seus rótulos de classificação. Aqui você poderá filtrar arquivos com base no rótulo de classificação aplicado a eles. Para obter mais informações sobre a integração entre o Cloud App Security e a Proteção de Informações do Azure, consulte [Integração da Proteção de Informações do Azure](azip-integration.md).

      - **Nome do arquivo** – Use esse filtro para aplicar a política a arquivos específicos.

      - **Tipo de arquivo** – Use esse filtro para aplicar a política a tipos de arquivo específicos, por exemplo, bloquear o download de todos os arquivos. xls.

        ![filtros de arquivo da política de sessão](./media/session-policy-file-filters.png)

        
   2. Na seção **Inspeção de conteúdo**, defina se deseja habilitar o exame de documentos e o conteúdo do arquivo pelo mecanismo DLP.
 
      ![inspeção do conteúdo da política de sessão](./media/session-policy-content-inspection.png)

   3. Em **Ações**, selecione uma das seguintes opções: 

      - **Testar (Monitorar todas as atividades)**: defina essa ação para permitir o download explicitamente de acordo com os filtros de política que você definir.

      - **Bloquear (bloquear o download de arquivos e monitorar todas as atividades)**: defina essa ação para bloquear explicitamente o download de acordo com os filtros de política que você definir. Para obter mais informações, consulte [Como funciona o bloqueio de download](#block-download).

      - **Proteger (aplicar o rótulo de classificação para baixar e monitorar todas as atividades)**: isso só está disponível se você seleciona **Controlar download de arquivos (com DLP)** em **Política de sessão**. Se sua organização usa a Proteção de Informações do Azure, você pode definir uma **Ação** para aplicar um rótulo de classificação configurado na Proteção de Informações do Azure para o arquivo. Para obter mais informações, consulte [Como funciona o a proteção de download](#protect-download).

        ![ações da política de sessão](./media/session-policy-actions.png)

7. Você pode **Criar um alerta para cada evento correspondente com a gravidade da política** e configurar um limite de alerta e selecionar se você deseja o alerta como um email, uma mensagem de texto ou ambos.

   ![alerta da política de sessão](./media/session-policy-alert.png)


## Monitorar todas as atividades <a name="monitor-session"></a>

Quando você cria uma política de sessão, cada sessão de usuário que corresponde à política é redirecionada para o controle de sessão de proxy em vez do aplicativo diretamente. O usuário verá um aviso de monitoramento para que ele saiba que as sessões que estão sendo monitoradas.

   ![aviso de monitoramento de sessão](./media/session-monitoring-notice.png)

Se você não desejar notificar o usuário que ele está sendo monitorado, você poderá desabilitar a mensagem de notificação.

1. Na engrenagem de configurações, selecione **Configurações gerais**. 

2. Em seguida, em configurações de proxy do Cloud App Security, desmarque a caixa de seleção **Notificar os usuários**.

    ![desabilitar o aviso de monitoramento de sessão](./media/disable-session-monitoring-notice.png)

Para manter o usuário dentro da sessão, o proxy substitui todas as URLs, os scripts Java e os cookies relevantes dentro da sessão do aplicativo por URLs do proxy. Por exemplo: se o aplicativo retornar uma página com links cujos domínios terminam com myapp.com, o proxy substituirá os links por domínios que terminam com algo como: myapp.com.us.cas.ms. Dessa forma, toda a sessão é monitorada pelo proxy.

O proxy registra os logs de tráfego de todas as sessões de usuário que são roteadas por ele. Os logs de tráfego incluem o agente do usuário, o tempo, o IP, as URLs visitadas e o número de bytes carregados e baixados. Esses logs são analisados e um relatório contínuo chamado **Proxy do Cloud App Security** é adicionado à lista de relatórios do Cloud Discovery no painel do Cloud Discovery.

![relatório do proxy](./media/proxy-report.png)


Para exportar esses logs:

1. Vá para a engrenagem de configurações e clique em **Proxy**.
2. No lado direito da tabela, clique no botão Exportar ![botão exportar](./media/export-button.png). 
3. Selecione o intervalo do relatório e clique em **Exportar**. Esse processo pode levar algum tempo.

Para baixar o log exportado:

1. Depois que o relatório estiver pronto, vá para **Investigar** e **Relatórios personalizados**.
2. Na tabela, selecione o relatório relevante na lista de **Logs de tráfego de proxy** e clique em download ![botão baixar](./media/download-button.png). 


## Bloquear todos os downloads <a name="block-download"></a>

Quando o **bloco** for definido como a **Ação** que deseja colocar na política de sessão de proxy do Cloud App Security, o proxy impedirá que um usuário baixe um arquivo de acordo com os filtros de arquivo da política. Um evento de download é reconhecido pelo proxy para cada aplicativo SAML e, quando um usuário inicia esse evento, o proxy intervém em tempo real para impedir a execução. Quando é recebido o sinal que um usuário iniciou um download, o proxy retorna uma mensagem **Download restringido** para o usuário e substitui o arquivo baixado por um arquivo de texto que contém uma mensagem personalizada para o usuário, que pode ser configurada na política de sessão de proxy.  

## Bloquear atividades específicas<a name="block-activities"></a>

Quando **Bloquear atividades** é definido como **Tipo de atividade**, você pode selecionar atividades específicas para bloquear em aplicativos específicos. Todas as atividades de aplicativos selecionados serão monitoradas (e relatadas no log de atividades), as atividades específicas que você selecionar serão bloqueadas se você marcar a ação **Bloquear**, e as atividades específicas que você selecionou gerarão alertas se você selecionar a ação **Testar** e ativar os alertas.

## Proteger arquivos no download <a name="protect-download"></a>
Selecione **Bloquear atividades** para bloquear atividades específicas que você pode selecionar usando o filtro **Tipo de atividade**. Todas as atividades de aplicativos selecionados serão monitoradas (e relatadas no Log de atividades). As atividades específicas que você selecionar serão bloqueadas se você marcar a ação **Bloquear**, e as atividades específicas que você selecionou gerarão alertas se você selecionar a ação **Testar** e ativar os alertas.
Quando **Proteger** é definido como a **Ação** a ser executada na política de sessão do proxy do Cloud App Security, o proxy determina o rótulo e a proteção subsequentes de um arquivo de acordo com os filtros de arquivo da política. Os rótulos são configurados no console de Proteção de Informações do Azure no Azure e **Proteger** deve ser selecionado no rótulo para que o rótulo seja exibido como uma opção na política do Cloud App Security. Quando um rótulo for selecionado e um arquivo que atende aos critérios da política do Cloud App Security for baixado, o rótulo e a proteção correspondente (com permissões) serão aplicados ao arquivo após o download. O arquivo original permanece como está no aplicativo de nuvem, enquanto o arquivo baixado agora está protegido. Os usuários que tentam acessar o arquivo devem atender os requisitos de permissão determinados pela proteção aplicada.  
 
 
## <a name="see-also"></a>Consulte Também  
[Bloqueando downloads em dispositivos não gerenciados, usando funcionalidades de proxy do Microsoft Azure AD](use-case-proxy-block-session-aad.md)   

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
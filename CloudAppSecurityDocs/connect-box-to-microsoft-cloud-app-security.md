---
title: Conectar o Box ao Cloud App Security
description: Este artigo fornece informações sobre como conectar o aplicativo Box ao Cloud App Security usando o conector de API para obter visibilidade e controle sobre o uso.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/10/2018
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: c32d5343d9069104e0cf02fa1f900dd58c20b3c2
ms.sourcegitcommit: 29a8e66c665f51d831516924ae4d9d8047b39276
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88781116"
---
# <a name="connect-box-to-microsoft-cloud-app-security"></a>Conectar o Box ao Microsoft Cloud App Security

*Aplica-se a: Microsoft Cloud App Security*

Este artigo fornece instruções para conectar o Microsoft Cloud App Security à sua conta existente do Box usando as APIs do Conector de Aplicativos. Essa conexão fornece visibilidade e controle sobre o uso do Box. Para obter informações sobre como Cloud App Security proteger a caixa, consulte [proteger caixa](protect-box.md).

## <a name="how-to-connect-box-to-cloud-app-security"></a>Como conectar o Box ao Cloud App Security

> [!NOTE]
> A implantação com uma conta que não seja uma conta de administrador leva a uma falha no teste da API e não permite que Cloud App Security verifique todos os arquivos no Box. Se isso for um problema para você, é possível realizar a implantação com um coadministrador que tenha todos os privilégios selecionados, mas o teste da API continuará a falhar e os arquivos pertencentes a outros administradores no Box não forem verificados.

1. Se você restringir o acesso de permissão do aplicativo, siga esta etapa. Caso contrário, pule para a etapa 2.

    1. Entre com uma conta de administrador na sua conta do box.
    1. Clique em **aplicativos**  >  **configurações personalizadas aplicativos**  >  **Settings**.

         ![aplicativos do box](media/box-apps.png "aplicativos do box")

    1. Se **desabilitar aplicativos não publicados por padrão** estiver selecionado, na caixa de texto **exceto para** , adicione a chave de API de Cloud app Security:

         |Data center|Chave de API de Cloud App Security|
         |----|----|
         |US1|`nduj1o3yavu30dii7e03c3n7p49cj2qh`|
         |US2|`w0ouf1apiii9z8o0r6kpr4nu1pvyec75`|
         |US3|`dmcyvu1s9284i2u6gw9r2kb0hhve4a0r`|
         |EU1|`me9cm6n7kr4mfz135yt0ab9f5k4ze8qp`|
         |EU2|`uwdy5r40t7jprdlzo85v8suw1l4cdsbf`|

        Em seguida, clique em **Salvar**. Para obter informações sobre como ver a quais Cloud App Security data center você está conectado, consulte [exibir seus data center](network-requirements.md#view-your-data-center).

        ![configurações do box exceto para](media/box-settings-except-for.png)

        > [!NOTE]
        > Se você for um cliente Adallom existente e a URL do console for para Adallom e não Cloud App Security, use este número de série do aplicativo: `bwahmilhdlpbqy2ongkl119o3lrkoshc` .

2. No portal do Cloud App Security, clique em **Investigar** e em **Aplicativos conectados**.

3. Na página **Conectores de aplicativos**, clique no botão de sinal de mais e selecione **Box**.

    ![caixa de conexão](media/connect-box.png "conectar o box")

4. No pop-up **configurações do box** , clique em **seguir este link**.

5. A página de entrada do Box é aberta. Insira suas credenciais para permitir que o Cloud App Security acesse o aplicativo do Box da sua equipe.

6. O Box pergunta se você deseja permitir que o Cloud App Security acesse o log de atividades e as informações da sua equipe e realize atividades como qualquer membro da equipe. Para continuar, clique em **Permitir**.

7. De volta ao portal do Cloud App Security, você deve receber uma mensagem dizendo que o Box foi conectado com êxito.

8. Certifique-se de que a conexão foi bem-sucedida clicando em **Testar API**.

    O teste pode levar alguns minutos. Depois de receber uma notificação de êxito, clique em **Fechar**.

O Box agora está conectado ao Cloud App Security.

Depois de conectar o Box, você receberá eventos por 60 dias antes da conexão.

Após conectar o Box, o Cloud App Security realizará uma verificação completa. Dependendo de quantos arquivos e usuários você tiver, a verificação completa poderá levar algum tempo. Para habilitar a verificação quase em tempo real, os arquivos nos quais as atividades são detectadas são movidos para o início da fila de verificação. Por exemplo, um arquivo editado, atualizado ou compartilhado é verificado imediatamente, em vez de aguardar o processo de verificação normal. A verificação quase em tempo real não se aplica a arquivos que não são modificados por natureza. Por exemplo, os arquivos que são exibidos, visualizados, impressos ou exportados são verificados como parte da verificação agendada regularmente.

Se você tiver problemas para conectar o aplicativo, consulte [Solucionando problemas de conectores de aplicativos](troubleshooting-api-connectors-using-error-messages.md).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]

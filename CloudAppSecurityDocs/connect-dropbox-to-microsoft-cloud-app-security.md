---
title: Conectar o Dropbox ao Cloud App Security
description: Este artigo fornece informações sobre como conectar o aplicativo Dropbox ao Cloud App Security usando o conector de API para obter visibilidade e controle sobre o uso.
ms.date: 12/10/2018
ms.topic: how-to
ms.openlocfilehash: adff9a8dc891fa40fb48c739b06a06980d985530
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96312855"
---
# <a name="connect-dropbox-to-microsoft-cloud-app-security"></a>Conectar o Dropbox ao Microsoft Cloud App Security

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Este artigo fornece instruções para conectar o Microsoft Cloud App Security à sua conta existente do Dropbox usando as APIs do conector. Essa conexão fornece visibilidade e controle sobre o uso do Dropbox. Para obter informações sobre como Cloud App Security protege o Dropbox, consulte [proteger o Dropbox](protect-dropbox.md).

Como Dropbox concede acesso aos arquivos de links compartilhados sem precisar entrar, o Cloud App Security registra esses usuários como usuários não autenticados. Se encontrar usuários não autenticados do Dropbox, isso poderá indicar usuários que não são da sua organização ou eles poderão ser usuários reconhecidos de dentro da sua organização que não entraram.

## <a name="how-to-connect-dropbox-to-cloud-app-security"></a>Como conectar o Dropbox ao Cloud App Security

1. No console do Cloud App Security, clique em **Investigar** e em **Aplicativos conectados**.

2. Na página **conectores de aplicativos** , clique no botão de adição seguido pelo **Dropbox**.

    ![conectar o Dropbox](media/connect-dropbox.png "conectar ao dropbox")

3. No pop-up, insira o endereço de email da conta do administrador.

4. Clique em **Gerar link**.

5. Clique em **Seguir este link**.

    A página de entrada do Dropbox é aberta. Insira suas credenciais para permitir que o Cloud App Security acesse a instância do Dropbox da sua equipe.

6. O Dropbox pergunta se você deseja permitir que o Cloud App Security acesse o log de atividades e as informações da sua equipe e realize atividades como qualquer membro da equipe. Para continuar, clique em **Permitir**.

7. De volta ao console do Cloud App Security, você deverá receber uma mensagem indicando que o Dropbox foi conectado com êxito.

8. Certifique-se de que a conexão foi bem-sucedida clicando em **Testar API**.

    O teste pode levar alguns minutos. Depois de receber uma notificação de êxito, clique em **Fechar**.

Depois de conectar o Dropbox, você receberá eventos por 60 dias antes da conexão.

> [!NOTE]
> Todos os eventos do Dropbox de adição de arquivo são exibidos no Cloud App Security como Carregar arquivo para alinhamento com todos os outros aplicativos conectados ao Cloud App Security.

Se você tiver problemas para conectar o aplicativo, consulte [Solucionando problemas de conectores de aplicativos](troubleshooting-api-connectors-using-error-messages.md).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]

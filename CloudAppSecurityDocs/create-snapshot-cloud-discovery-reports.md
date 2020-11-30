---
title: Criar relatórios de instantâneos do uso de aplicativos na nuvem do Cloud Discovery
description: Este artigo fornece informações sobre como carregar logs manualmente para criar um relatório de instantâneo de seus aplicativos do Cloud Discovery.
ms.date: 04/07/2019
ms.topic: how-to
ms.openlocfilehash: ad1f2ad7c94d543cdd82f655e4b27aaa987bf290
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96312056"
---
# <a name="create-snapshot-cloud-discovery-reports"></a>Criar instantâneo de relatórios do Cloud Discovery

[!INCLUDE [Banner for top of topics](includes/banner.md)]

É importante carregar um log manualmente e permitir que o Microsoft Cloud App Security o analise antes de tentar usar o coletor de logs automático. Para saber mais sobre como o coletor de logs funciona e o formato esperado de log, confira [Usando logs de tráfego para Cloud Discovery](#log-format).

Se você ainda não tiver um log e desejar ver um exemplo de como deverá ser a aparência de seu log, baixe um arquivo de log de exemplo. Siga o procedimento abaixo para ver qual deverá ser a aparência do seu log.

Para criar um relatório de instantâneo:

1. Colete arquivos de log do firewall e do proxy por meio dos quais os usuários da sua organização acessam a Internet. Certifique-se de coletar logs durante os períodos de tráfego de pico que representam a atividade de todos os usuários na sua organização.

1. No portal de Cloud App Security, clique em **descobrir** e, em seguida, clique em **criar relatório de instantâneo**.

    ![Criar novo relatório de instantâneo](media/create-new-snapshot-report.png)

1. Insira um **nome de relatório** e uma **Descrição**

    ![Novo relatório de instantâneo](media/new-snapshot-report.png)

1. Selecione a **Fonte de dados** da qual você deseja carregar os arquivos de log.

1. Verifique o formato do seu log para certificar-se de que ele foi formatado corretamente de acordo com o exemplo que pode ser baixado. Clique em **Exibir e verifique e** clique em **baixar log de exemplo**. Compare seu log com o exemplo fornecido para verificar se ele é compatível.

    ![Verifique seu formato de log](media/cloud-discovery-snapshot-verify.png)

    > [!NOTE]
    > O formato de amostra de FTP tem suporte em instantâneos e upload automatizado, enquanto o syslog tem suporte apenas no upload automatizado. Baixar um exemplo de log também baixará um exemplo de log FTP.

1. **Escolha os logs de tráfego** que você deseja carregar. Você pode carregar até 20 arquivos ao mesmo tempo. Também há suporte para arquivos compactados e zipados.

1. Clique em **Criar**.

1. Após o upload ser concluído, a mensagem de status será exibida no canto superior direito da tela avisando que o log foi carregado com êxito.

1. Depois de carregar os arquivos de log, levará algum tempo para que eles possam ser analisados e examinados.
    Após o processamento dos arquivos de log ser concluído, você receberá um email para avisar que ele está pronto.

1. Uma faixa de notificação será exibida na barra de status na parte superior do **painel do Cloud Discovery**. A faixa atualiza você sobre o status de processamento dos arquivos de log.
    ![processando a barra de menus do arquivo de log](media/processing-log-file-menu-bar.png)

1. Depois que os logs forem carregados com êxito, você deverá ver uma notificação informando que o processamento do arquivo de log foi concluído com êxito. Neste ponto, você pode exibir o relatório clicando no link na barra de status ou clicando no ícone configurações engrenagem ![configurações](media/settings-icon.png "Ícone de configurações")e, em seguida, selecione **configurações**.

1. Em **Cloud Discovery**, selecione **relatórios de instantâneo** e selecione seu relatório de instantâneo.

    ![gerenciamento de relatório de instantâneo](media/snapshot-report-managment.png)

## <a name="using-traffic-logs-for-cloud-discovery"></a>Usar os logs de tráfego para Cloud Discovery <a name="log-format"></a>

O Cloud Discovery usa os dados em seus logs de tráfego. Quanto mais detalhado o log, melhor é a visibilidade obtida. O Cloud Discovery requer dados de tráfego da Web com os seguintes atributos:

- Data da transação
- IP de origem
- Usuário de origem ‑ altamente recomendado
- Endereço IP de destino
- URL de destino **recomendada** (URLs fornecem maior precisão para detecção de aplicativos de nuvem que endereços IP)
- Quantidade total de dados (as informações dos dados são muito valiosas)
- Quantidade de dados carregados ou baixados (fornece informações sobre os padrões de uso dos aplicativos de nuvem)
- Ação realizada (permitido/bloqueado)

O Cloud Discovery não pode mostrar nem analisar atributos que não estão incluídos em seus logs.
Por exemplo, o formato de log padrão do **Cisco ASA Firewall** não tem o **número de bytes carregados por transação**, **Nome de usuário** nem a **URL de destino** (somente o IP de destino).
Portanto, esses atributos não serão exibidos nos dados do Cloud Discovery para esses logs e a visibilidade sobre os aplicativos de nuvem será limitada. Para firewalls Cisco ASA, é necessário definir o nível de informações para 6.

Para gerar com êxito um relatório do Cloud Discovery, seus logs de tráfego devem atender às seguintes condições:

1. A [fonte de dados tem suporte](set-up-cloud-discovery.md#supported-firewalls-and-proxies).
2. O formato de log corresponde ao formato padrão esperado (formato verificado após o upload da Ferramenta de log).
3. Os eventos têm menos de 90 dias.
4. O arquivo de log é válido e inclui informações do tráfego de saída.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]

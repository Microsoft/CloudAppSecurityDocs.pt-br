---
title: Criar relatórios de instantâneos do uso de aplicativos na nuvem do Cloud Discovery
description: Este artigo fornece informações sobre como carregar logs manualmente para criar um relatório de instantâneo de seus aplicativos do Cloud Discovery.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 04/07/2019
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 4bfa89a9794df5cbce0c361e1b2a7d8071cd303c
ms.sourcegitcommit: 29a8e66c665f51d831516924ae4d9d8047b39276
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88780521"
---
# <a name="create-snapshot-cloud-discovery-reports"></a>Criar instantâneo de relatórios do Cloud Discovery

*Aplica-se a: Microsoft Cloud App Security*

É importante carregar um log manualmente e permitir que o Microsoft Cloud App Security o analise antes de tentar usar o coletor de logs automático. Para saber mais sobre como o coletor de logs funciona e o formato esperado de log, confira [Usando logs de tráfego para Cloud Discovery](#log-format).

Se você ainda não tiver um log e desejar ver um exemplo de como deverá ser a aparência de seu log, baixe um arquivo de log de exemplo. Siga o procedimento abaixo para ver qual deverá ser a aparência do seu log.

Para criar um relatório de instantâneo:

1. Colete arquivos de log do firewall e do proxy por meio dos quais os usuários da sua organização acessam a Internet. Certifique-se de coletar logs durante os períodos de tráfego de pico que representam a atividade de todos os usuários na sua organização.

2. No portal do Cloud App Security, clique em **Descobrir** e, em seguida, **Criar relatório de instantâneos**.

    ![Criar novo relatório de instantâneo](media/create-new-snapshot-report.png)

3. Insira um **nome de relatório** e uma **Descrição**

    ![Novo relatório de instantâneo](media/new-snapshot-report.png)

4. Selecione a **Fonte de dados** da qual você deseja carregar os arquivos de log.

5. Verifique o formato do seu log para certificar-se de que ele foi formatado corretamente de acordo com o exemplo que pode ser baixado. Clique em **Exibir e verificar** e, em seguida, **Baixar log de exemplo**. Compare seu log com o exemplo fornecido para verificar se ele é compatível.

    ![Verifique seu formato de log](media/cloud-discovery-snapshot-verify.png)

    > [!NOTE]
    > O formato de exemplo de FTP tem suporte em instantâneos e no carregamento automatizado, enquanto o syslog tem suporte somente no carregamento automatizado.  
    Baixar um exemplo de log também baixará um exemplo de log FTP.

6. **Escolha os logs de tráfego** que você deseja carregar. Você pode carregar até 20 arquivos ao mesmo tempo. Também há suporte para arquivos compactados e zipados.

7. Clique em **Criar**.

8. Após o upload ser concluído, a mensagem de status será exibida no canto superior direito da tela avisando que o log foi carregado com êxito.

9. Depois de carregar os arquivos de log, levará algum tempo para que eles possam ser analisados e examinados.
    Após o processamento dos arquivos de log ser concluído, você receberá um email para avisar que ele está pronto.

10. Uma faixa de notificação será exibida na barra de status na parte superior do **painel do Cloud Discovery**. A faixa atualiza você sobre o status de processamento dos arquivos de log.
    ![processando a barra de menus do arquivo de log](media/processing-log-file-menu-bar.png)

11. Depois que os logs forem carregados com êxito, você deverá ver uma notificação informando que o processamento do arquivo de log foi concluído com êxito. Neste ponto, é possível exibir o relatório clicando no link na barra de status ou indo para a engrenagem de Configurações e selecionando **Configurações do Cloud Discovery**.

    ![Guia Configurações de descoberta](media/discovery-settings-tab.png)
12. Em seguia, selecione **Relatórios de instantâneo** e seu relatório de instantâneo.

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

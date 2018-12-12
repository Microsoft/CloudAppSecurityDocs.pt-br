---
title: Criar relatórios instantâneos do uso de aplicativos na nuvem do Cloud Discovery | Microsoft Docs
description: Este artigo fornece informações sobre como carregar logs manualmente para criar um relatório de instantâneo de seus aplicativos do Cloud Discovery.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/9/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: ecc1949d-c861-4636-952a-c3a260719bb5
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 4704f4ccf93fe369efce5e53d3cf99986ed31eff
ms.sourcegitcommit: c497253a7ab63973bb806607e5f15dece91640be
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53124784"
---
# <a name="create-snapshot-cloud-discovery-reports"></a>Criar instantâneo de relatórios do Cloud Discovery

*Aplica-se ao: Microsoft Cloud App Security*

É importante carregar um log manualmente e permitir que o Microsoft Cloud App Security o analise antes de tentar usar o coletor de logs automático. Para saber mais sobre como o coletor de logs funciona e o formato esperado de log, confira [Usando logs de tráfego para Cloud Discovery](#log-format).

Se você ainda não tiver um log e desejar ver um exemplo de como deverá ser a aparência de seu log, baixe um arquivo de log de exemplo. Siga o procedimento abaixo para ver qual deverá ser a aparência do seu log.


Para criar um relatório de instantâneo:
  
1. Colete arquivos de log do firewall e do proxy por meio dos quais os usuários da sua organização acessam a Internet. Certifique-se de coletar logs durante os períodos de tráfego de pico que representam a atividade de todos os usuários na sua organização.  
  
2. No portal do Cloud App Security, clique em **Descobrir** e, em seguida, **Criar relatório de instantâneos**.  
  
   ![Criar novo relatório de instantâneo](./media/create-new-snapshot-report.png)
     
3. Insira um **Nome do relatório** e uma **Descrição**
  
    ![Novo relatório de instantâneo](./media/new-snapshot-report.png) 

4. Selecione a **Fonte de dados** da qual você deseja carregar os arquivos de log.  
  
5. Verifique o formato do seu log para certificar-se de que ele foi formatado corretamente de acordo com o exemplo que pode ser baixado. Clique em **Exibir e verificar** e, em seguida, **Baixar log de exemplo**. Compare seu log com o exemplo fornecido para verificar se ele é compatível. 

   ![Verifique o formato do seu log](./media/cloud-discovery-snapshot-verify.png)  

   > [!NOTE]
   > O formato de exemplo FTP tem suporte em instantâneos e no upload automatizado enquanto o syslog tem suporte somente no upload automatizado.<br></br>
   Baixar um exemplo de log também baixará um exemplo de log FTP.


6. **Escolha os logs de tráfego** que você deseja carregar. Você pode carregar até 20 arquivos ao mesmo tempo. Também há suporte para arquivos compactados.  
  
7. Clique em **Criar**.  

8. Após o upload ser concluído, a mensagem de status será exibida no canto superior direito da tela avisando que o log foi carregado com êxito.  
  
9. Depois de carregar os arquivos de log, levará algum tempo para que eles possam ser analisados e examinados.  
   Após o processamento dos arquivos de log ser concluído, você receberá um email para avisar que ele está pronto. 
  
10. Uma faixa de notificação será exibida na barra de status na parte superior do **painel do Cloud Discovery**. A faixa atualiza você sobre o status de processamento dos arquivos de log.  
    ![processando a barra de menus do arquivo de log](./media/processing-log-file-menu-bar.png) 
   
11. Depois que os logs forem carregados com êxito, você deverá ver uma notificação informando que o processamento do arquivo de log foi concluído com êxito. Neste ponto, é possível exibir o relatório clicando no link na barra de status ou indo para a engrenagem de Configurações e selecionando **Configurações do Cloud Discovery**.   
  
     ![Guia Configurações de descoberta](./media/discovery-settings-tab.png)
12. Em seguia, selecione **Relatórios de instantâneo** e seu relatório de instantâneo.
 
     ![gerenciamento de relatório de instantâneo](./media/snapshot-report-managment.png)

  
## Usar os logs de tráfego para Cloud Discovery <a name="log-format"></a>
O Cloud Discovery usa os dados em seus logs de tráfego. Quanto mais detalhado o log, melhor é a visibilidade obtida. O Cloud Discovery requer dados de tráfego da Web com os seguintes atributos:
- Data da transação
- IP de Origem
- Usuário de origem ‑ altamente recomendado
- Endereço IP de destino
- URL de destino **recomendada** (URLs fornecem maior precisão para detecção de aplicativos de nuvem que endereços IP)
- Quantidade total de dados (as informações dos dados são muito valiosas)
- Quantidade de dados carregados ou baixados (fornece informações sobre os padrões de uso dos aplicativos de nuvem)
- Ação executada (permitida/bloqueada)

O Cloud Discovery não pode mostrar nem analisar atributos que não estão incluídos em seus logs.
Por exemplo, o formato de log padrão do **Cisco ASA Firewall** não tem o **número de bytes carregados por transação**, **Nome de usuário** nem a **URL de destino** (somente o IP de destino).
Portanto, esses atributos não serão exibidos nos dados do Cloud Discovery para esses logs e a visibilidade sobre os aplicativos de nuvem será limitada. Para firewalls Cisco ASA, é necessário definir o nível de informações para 6. 


Para gerar com êxito um relatório do Cloud Discovery, seus logs de tráfego devem atender às seguintes condições:
1. A fonte de dados tem suporte (consulte a lista abaixo).
2. O formato de log corresponde ao formato padrão esperado (formato verificado após o upload da Ferramenta de log).
3. Os eventos têm menos de 90 dias.
4. O arquivo de log é válido e inclui informações de tráfego de saída.



## Proxies e firewalls com suporte <a name="supported-firewalls-and-proxies"></a>

- Barracuda - Firewall de aplicativo Web (W3C)
- Blue Coat Proxy SG – Log de acesso (W3C)
- Check Point
- Firewall Cisco ASA (Para firewalls Cisco ASA, é necessário definir o nível de informações como 6)
- Cisco ASA com FirePOWER
- Cisco IronPort WSA
- Cisco ScanSafe
- Cisco Meraki – log de URLs
- Clavister NGFW (Syslog)
- Digital Arts i-FILTER
- Fortinet Fortigate
- iboss Secure Cloud Gateway
- Juniper SRX
- Juniper SSG
- McAfee Secure Web Gateway
- Microsoft Forefront Threat Management Gateway (W3C)
- Firewall da série Palo Alto
- Sonicwall (anteriormente conhecido como Dell)
- Sophos SG
- Sophos XG
- Sophos Cyberoam
- Squid (Comum)
- Squid (Nativo)
- Websense – Soluções de segurança da Web – Relatório detalhado de investigação (CSV)
- Websense – Soluções de segurança da Web – Log de atividades de Internet (CEF)
- Zscaler

> [!NOTE]
> O Cloud Discovery oferece suporte a endereços IPv4 e IPv6.

Se não houver suporte para seu log, selecione **Outro** como a **Fonte de dados** e especifique o dispositivo e o log que você está tentando carregar. O log será examinado pela equipe de analista de nuvem do Cloud App Security e você será notificado se for adicionado suporte para seu tipo de log. Como alternativa, você pode definir um analisador personalizado que corresponda ao seu formato. Para saber mais, confira [Usar analisador de log personalizado](custom-log-parser.md).


Atributos de dados (de acordo com a documentação do fornecedor):


|                 Fonte de dados                  |    URL do aplicativo de destino    |    IP do aplicativo de destino     |       Nome de usuário       |      IP de Origem       |    Tráfego total     |    Bytes carregados    |
|----------------------------------------------|----------------------|----------------------|----------------------|----------------------|----------------------|----------------------|
|                  Barracuda                   | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> |          Não          |          Não          |
|                  Blue Coat                   | <strong>Sim</strong> |          Não          | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> |
|                  Checkpoint                  |          Não          | <strong>Sim</strong> |          Não          | <strong>Sim</strong> |          Não          |          Não          |
|              Cisco ASA (Syslog)              |          Não          | <strong>Sim</strong> |          Não          | <strong>Sim</strong> | <strong>Sim</strong> |          Não          |
|           Cisco ASA com FirePOWER           | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> |
|                  Cisco FWSM                  |          Não          | <strong>Sim</strong> |          Não          | <strong>Sim</strong> | <strong>Sim</strong> |          Não          |
|              Cisco Ironport WSA              | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> |
|                 Cisco Meraki                 | <strong>Sim</strong> | <strong>Sim</strong> |          Não          | <strong>Sim</strong> |          Não          |          Não          |
|           Clavister NGFW (Syslog)            | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> |
|                SonicWall (anteriormente conhecido como Dell)                | <strong>Sim</strong> | <strong>Sim</strong> |          Não          | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> |
|            Digital Arts i-FILTER             | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> |
|                  Fortigate                   |          Não          | <strong>Sim</strong> |          Não          | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> |
|                 Juniper SRX                  |          Não          | <strong>Sim</strong> |          Não          | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> |
|                 Juniper SSG                  |          Não          | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> |
|                  McAfee SWG                  | <strong>Sim</strong> |          Não          |          Não          | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> |
|                    MS TMG                    | <strong>Sim</strong> |          Não          | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> |
|              Redes de Palo Alto              |          Não          | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> |
|                    Sophos                    | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> |          Não          |
|                Squid (Comum)                | <strong>Sim</strong> |          Não          | <strong>Sim</strong> | <strong>Sim</strong> |          Não          | <strong>Sim</strong> |
|                Squid (Nativo)                | <strong>Sim</strong> |          Não          | <strong>Sim</strong> | <strong>Sim</strong> |          Não          | <strong>Sim</strong> |
| Websense – Relatório de detalhes investigativo (CSV) | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> |
|    Websense – Log de atividades da Internet (CEF)    | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> |
|                   Zscaler                    | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> | <strong>Sim</strong> |
     
 
## <a name="next-steps"></a>Próximas etapas  
[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)   

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/)  
    
      
  
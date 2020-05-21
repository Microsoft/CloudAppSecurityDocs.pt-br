---
title: Requisitos de rede – Cloud App Security | Microsoft Docs
description: Este artigo descreve os endereços IP e portas que você precisa abrir para trabalhar com o Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 11/01/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: e38d0e3ed58ed83e031d56d5de160751a66b3331
ms.sourcegitcommit: 416457ff6e9095592b3c19a98755786f8bb0683a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83569559"
---
# <a name="network-requirements"></a>Requisitos de rede

*Aplica-se a: Microsoft Cloud App Security*

Este artigo fornece uma lista de portas e endereços IP que você precisa para permitir e permitir que a lista funcione com Microsoft Cloud App Security.

## <a name="view-your-data-center"></a>Exibir seu data center

Alguns dos requisitos abaixo dependem em que data center você está conectado.

Para ver qual data center você está se conectando, execute as seguintes etapas:

1. No portal do Cloud App Security, clique no **ícone de ponto de interrogação** na barra de menus. Em seguida, selecione **Sobre**.

    ![clique em Sobre](media/about-menu.png)

2. Na tela da versão do Cloud App Security, você pode ver a região e o data center.

    ![Exibir seu data center](media/data-center.png)

## <a name="portal-access"></a>Acesso ao portal

Para acessar o portal de Cloud App Security, adicione a **porta de saída 443** para os seguintes endereços IP e nomes DNS à lista de permissões do firewall:

    portal.cloudappsecurity.com
    *.portal.cloudappsecurity.com
    cdn.cloudappsecurity.com
    https://adaproddiscovery.azureedge.net
    *.s-microsoft.com
    *.msecnd.net
    dev.virtualearth.net
    *.cloudappsecurity.com
    flow.microsoft.com
    static2.sharepointonline.com
    dc.services.visualstudio.com
    *.blob.core.windows.net

Para clientes de GCC do governo dos EUA, também é necessário adicionar os seguintes nomes DNS à lista de permissões do firewall para fornecer acesso ao portal do Cloud App Security GCC High:

    portal.cloudappsecurity.us
    *.portal.cloudappsecurity.us
    cdn.cloudappsecurity.com

Além disso, os itens a seguir devem estar na lista de permissões, dependendo do data center usado:
> [!div class="mx-tableFixed"]
>
> |Data center|Endereços IP|Nome DNS|
> |----|----|----|
> |US1|13.64.26.88<br />13.64.29.32<br />13.80.125.22<br />13.91.91.243<br />40.74.1.235<br />40.74.6.204<br />51.143.58.207<br />52.137.89.147<br />52.183.75.62|\*.us.portal.cloudappsecurity.com|
> |US2|13.80.125.22<br />20.36.222.59<br />20.36.222.60<br />40.74.1.235<br />40.74.6.204<br />51.143.58.207<br />52.137.89.147<br />52.183.75.62<br />52.184.165.82|\*.us2.portal.cloudappsecurity.com|
> |US3|13.80.125.22<br />40.74.1.235<br />40.74.6.204<br />40.90.218.196<br />40.90.218.198<br />51.143.58.207<br />52.137.89.147<br />52.183.75.62|*.us3.portal.cloudappsecurity.com|
> |EU1|13.80.125.22<br />40.119.154.72<br />40.74.1.235<br />40.74.6.204<br />51.143.58.207<br />52.137.89.147<br />52.157.238.58<br />52.174.56.180<br />52.183.75.62|\*.eu.portal.cloudappsecurity.com<|
> |EU2|13.80.125.22<br />40.74.1.235<br />40.74.6.204<br />40.81.156.154<br />40.81.156.156<br />51.143.58.207<br />52.137.89.147<br />52.183.75.62|*.eu2.portal.cloudappsecurity.com|
> |Gov US1|13.72.19.4<br />52.227.143.223|*. us1.portal.cloudappsecurity.us|

> [!NOTE]
> Em vez de um caractere curinga (\*), você pode abrir somente a URL específica do locatário, por exemplo, de acordo com a captura de tela acima, você poderá abrir mod244533.us.portal.cloudappsecurity.com

## <a name="access-and-session-controls"></a>Controles de acesso e sessão

Configure o firewall para o proxy reverso usando as configurações relevantes para o seu ambiente.

### <a name="commercial-customers"></a>Clientes comerciais

Para clientes comerciais, para habilitar Cloud App Security proxy reverso, adicione a **porta de saída 443** para os seguintes endereços IP e nomes DNS à lista de permissões do firewall:

    *.cas.ms
    *.mcas.ms
    *.admin-mcas.ms
    mcasproxy.azureedge.net

Além disso, os itens a seguir devem estar na lista de permissões, dependendo do data center usado:

> [!div class="mx-tableFixed"]
>
> |Data center|Endereços IP|||Nome DNS|
> |----|----|----|----|----|
> |US1|40.81.63.1<br />40.81.63.4<br />52.142.112.145<br />52.142.116.135<br />51.105.163.8<br />51.105.163.43<br />40.66.60.118<br />40.66.60.200<br />40.65.169.97<br />40.65.169.236<br />40.81.121.111<br />40.81.120.187<br />40.91.114.46<br />40.91.114.47<br />40.81.63.5<br />40.81.63.2<br />20.40.163.133<br />20.40.163.97<br />52.142.116.174<br />52.142.117.183<br />52.142.121.75<br />52.142.121.6<br />51.105.166.102<br />51.105.165.116<br />51.105.165.37|51.105.165.31<br />40.66.60.207<br />40.66.60.208<br />40.66.62.78<br />20.40.134.94<br />40.65.169.46<br />40.65.169.196<br />52.148.116.37<br />52.148.115.238<br />40.81.127.140<br />40.81.121.107<br />51.137.136.14<br />51.137.136.13<br />40.91.114.49<br />40.91.114.44<br />51.143.111.58<br />40.91.127.44<br />40.81.63.8<br />40.81.62.255<br />52.142.112.146<br />52.142.116.250<br />51.105.166.103<br />51.105.164.8<br />40.66.60.180<br />40.66.60.206|40.119.215.167<br />40.65.170.17<br />40.81.121.127<br />40.81.121.108<br />40.91.114.48<br />40.91.114.45<br />20.40.161.119<br />20.40.161.135<br />52.156.197.254<br />52.156.198.196<br />51.105.166.106<br />51.105.165.63<br />40.66.60.185<br />40.66.59.41<br />20.184.63.216<br />20.184.63.232<br />40.81.122.76<br />40.81.123.124<br />40.90.220.37<br />40.91.126.157<br />13.71.52.249<br />52.140.81.147<br />52.140.81.26<br />52.140.81.150|\*. us.cas.ms<br />\*. us.access-control.cas.ms<br />\*. us.saml.cas.ms|
> |US2|40.81.63.7<br />40.81.59.90<br />40.67.251.0<br />52.156.206.47<br />40.66.60.209<br />40.66.60.216<br />40.65.170.137<br />40.65.170.26<br />40.81.127.139<br />40.81.127.25<br />104.45.170.184<br />104.45.170.185<br />40.81.58.184<br />40.81.58.180<br />20.40.163.96<br />20.40.163.88<br />52.156.205.222<br />52.156.204.99<br />52.155.166.50<br />52.142.127.127<br />40.66.60.219<br />40.66.60.215<br />40.66.63.148<br />20.40.132.195|40.65.170.125<br />40.65.170.123<br />52.139.245.40<br />52.139.245.48<br />40.81.121.140<br />40.81.121.135<br />51.137.137.121<br />51.137.137.118<br />104.45.170.196<br />104.45.170.182<br />52.151.238.5<br />52.151.237.243<br />40.81.58.193<br />40.81.59.93<br />52.156.197.208<br />52.156.206.46<br />40.66.60.210<br />40.66.60.217<br />40.65.170.128<br />40.65.170.133<br />40.81.127.230<br />40.81.127.141<br />104.45.170.188<br />104.45.170.194|20.40.161.141<br />20.40.161.140<br />52.156.205.226<br />52.156.206.45<br />40.66.62.130<br />40.66.56.158<br />40.119.207.131<br />40.119.207.144<br />40.81.124.185<br />40.81.122.62<br />52.191.238.65<br />52.191.237.188<br />191.235.123.242<br />191.235.122.224<br />191.235.117.31<br />191.235.120.17<br />191.235.123.114<br />191.235.121.164<br />191.235.122.101<br />191.235.119.253<br />191.235.122.60<br />191.235.121.69|\*. us2.cas.ms<br />\*. us2.access-control.cas.ms<br />\*. us2.saml.cas.ms|
> |US3|40.81.62.224<br />40.81.62.220<br />40.82.186.168<br />40.82.186.169<br />52.155.180.210<br />52.155.179.84<br />40.66.59.196<br />40.66.60.224<br />40.65.170.80<br />40.65.170.83<br />40.81.127.229<br />40.81.121.66<br />104.45.170.191<br />104.45.170.183<br />40.91.114.40<br />40.91.114.42<br />40.81.62.179<br />40.81.62.223<br />20.40.162.86<br />20.40.162.200<br />40.82.186.182<br />40.82.186.177<br />52.139.21.70<br />52.139.16.105<br />52.155.177.13<br />52.155.180.208<br />52.155.164.131<br />52.155.167.231<br />40.66.60.226<br />40.66.59.193|40.66.61.193<br />40.66.61.158<br />40.65.170.113<br />40.65.170.82<br />52.139.245.1<br />52.139.245.21<br />40.81.120.192<br />40.81.127.239<br />51.137.136.34<br />51.137.137.69<br />104.45.170.70<br />104.45.170.180<br />52.224.190.225<br />52.224.191.62<br />40.91.114.41<br />40.91.78.105<br />52.148.161.45<br />52.148.161.53<br />40.81.62.193<br />40.81.62.162<br />40.82.186.166<br />40.82.186.176<br />52.155.180.209<br />52.155.178.247<br />40.66.59.246<br />40.66.59.195<br />40.65.170.81<br />40.65.170.112<br />40.81.120.191<br />40.81.123.157|104.45.170.186<br />104.45.170.178<br />40.91.114.43<br />40.91.74.37<br />20.40.161.160<br />20.40.161.161<br />52.139.2.0<br />52.139.1.156<br />52.155.180.211<br />52.155.182.138<br />40.66.62.7<br />40.66.62.9<br />20.184.63.158<br />20.184.61.253<br />20.40.106.51<br />20.40.107.84<br />52.224.202.86<br />52.224.202.91<br />51.143.122.59<br />51.143.122.60<br />40.82.186.168<br />40.82.186.169<br />52.139.2.0<br />52.139.1.156<br />40.82.186.182<br />40.82.186.177<br />52.139.21.70<br />52.139.16.105<br />52.139.9.176<br />52.139.9.198|\*. us3.cas.ms<br />\*. us3.access-control.cas.ms<br />\*. us3.saml.cas.ms|
> |EU1|40.81.57.138<br />40.81.57.157<br />52.156.204.139<br />52.156.205.182<br />52.157.232.147<br />52.157.235.144<br />40.119.207.200<br />40.119.207.174<br />40.81.120.13<br />40.81.120.25<br />104.45.168.114<br />104.45.168.103<br />40.80.222.197<br />40.80.220.215<br />40.81.57.169<br />40.81.57.144<br />20.40.163.178<br />20.40.163.179<br />52.156.204.24<br />52.156.204.51<br />52.155.161.88<br />52.155.161.91<br />52.157.233.205<br />52.157.234.160|51.145.181.214<br />51.145.181.195<br />40.119.207.193<br />40.119.207.164<br />52.148.115.188<br />52.148.115.194<br />40.81.121.78<br />40.81.122.203<br />51.137.137.237<br />51.137.137.200<br />104.45.168.106<br />104.45.168.104<br />52.151.247.27<br />52.151.244.65<br />40.80.219.49<br />40.80.222.91<br />52.153.240.107<br />20.188.72.248<br />40.81.57.164<br />40.81.57.141<br />52.156.203.22<br />52.156.205.137<br />52.157.237.213<br />52.157.237.107|40.119.207.182<br />40.119.207.166<br />40.81.121.76<br />40.81.120.24<br />104.45.168.111<br />104.45.168.108<br />40.80.220.246<br />40.80.221.77<br />20.40.161.132<br />20.40.161.131<br />52.156.203.199<br />40.67.254.233<br />52.157.218.232<br />52.157.218.219<br />52.139.251.219<br />52.139.252.105<br />40.81.122.63<br />20.40.106.50<br />52.224.201.216<br />52.224.201.223<br />52.249.25.165<br />52.249.25.160|\*. eu1.cas.ms<br />\*. eu1.access-control.cas.ms<br />\*. eu1.saml.cas.ms|
> |EU2|40.81.62.222<br />40.81.62.212<br />52.155.182.49<br />52.155.181.181<br />52.157.234.222<br />52.157.236.195<br />40.66.60.221<br />40.66.60.101<br />40.119.203.98<br />40.119.203.208<br />104.45.170.174<br />104.45.170.127<br />40.81.62.221<br />40.81.62.206<br />20.40.160.184<br />20.40.163.130<br />52.155.181.183<br />52.155.168.45<br />52.156.202.7<br />52.142.124.23|52.157.233.49<br />52.157.235.27<br />51.105.164.234<br />51.105.164.241<br />40.66.60.232<br />40.66.60.222<br />20.40.134.79<br />40.66.57.203<br />40.119.203.158<br />40.119.203.209<br />20.184.61.67<br />20.184.60.77<br />104.45.170.173<br />104.45.170.176<br />52.224.188.157<br />52.224.188.168<br />40.81.62.209<br />40.81.62.199<br />52.155.181.180<br />52.155.182.50|52.157.237.255<br />52.157.239.132<br />40.66.60.225<br />40.66.60.220<br />40.119.203.159<br />40.119.203.99<br />104.45.170.161<br />104.45.170.175<br />20.40.161.142<br />20.40.161.143<br />52.155.181.182<br />52.155.182.48<br />40.119.145.130<br />40.119.147.102<br />40.66.62.154<br />40.66.62.225<br />20.184.58.46<br />40.90.191.153<br />52.190.31.62<br />52.190.26.220|\*. eu2.cas.ms<br />\*. eu2.access-control.cas.ms<br />\*. eu2.saml.cas.ms|

### <a name="us-government-gcc-high-customers"></a>Clientes com GCC do governo dos EUA

Para clientes do governo dos EUA GCC High, para habilitar Cloud App Security proxy reverso, adicione a **porta de saída 443** para os seguintes nomes DNS à lista de permissões do firewall:

    *.mcas-gov.us
    *.admin-mcas-gov.us
    mcasproxy.azureedge.net

## <a name="siem-agent-connection"></a>Conexão do agente SIEM

Para permitir que Cloud App Security se conectem ao SIEM, adicione a **porta de saída 443** para os seguintes endereços IP à lista de permissões do firewall:

> [!div class="mx-tableFixed"]
>
> |Data center|Endereços IP|
> |----|----|
> |US1|13.64.26.88<br />13.64.29.32<br />13.80.125.22<br />13.91.91.243<br />40.74.1.235<br />40.74.6.204<br />51.143.58.207<br />52.137.89.147<br />52.183.75.62|
> |US2|13.80.125.22<br />20.36.222.59<br />20.36.222.60<br />40.74.1.235<br />40.74.6.204<br />51.143.58.207<br />52.137.89.147<br />52.183.75.62<br />52.184.165.82|
> |US3|13.80.125.22<br />40.74.1.235<br />40.74.6.204<br />40.90.218.196<br />40.90.218.198<br />51.143.58.207<br />52.137.89.147<br />52.183.75.62|
> |EU1|13.80.125.22<br />40.119.154.72<br />40.74.1.235<br />40.74.6.204<br />51.143.58.207<br />52.137.89.147<br />52.157.238.58<br />52.174.56.180<br />52.183.75.62|
> |EU2|13.80.125.22<br />40.74.1.235<br />40.74.6.204<br />40.81.156.154<br />40.81.156.156<br />51.143.58.207<br />52.137.89.147<br />52.183.75.62|
> |Gov US1|13.72.19.4<br />52.227.143.223|

> [!NOTE]
> Se você não especificou um proxy ao configurar o agente SIEM Cloud App Security, precisará permitir conexões http http://ocsp.msocsp.com/ e OCSP.DigiCert.com na porta 80. Isso é usado para verificar o status de revogação de certificado ao se conectar ao portal do Cloud App Security.

## <a name="app-connector"></a>Conector de aplicativo

Para alguns aplicativos de terceiros serem acessados pelo Cloud App Security, esses endereços IP podem ser usados. Os endereços IP permitem ao Cloud App Security coletar logs e fornecer acesso ao console do Cloud App Security.

> [!NOTE]
>Você pode ver esses endereços IP nos logs de atividades do fornecedor porque o Cloud App Security executa as ações de governança e as varreduras desses endereços IP.

Para se conectar a aplicativos de terceiros, habilite o Cloud App Security para se conectar nesses endereços IP:

> [!div class="mx-tableFixed"]
>
> |Data center|Endereços IP||
> |----|----|----|
> |US1|13.64.196.27<br />13.64.198.19<br />13.64.198.97<br />13.64.199.41<br />13.64.26.88<br />13.64.29.32<br />13.64.30.117<br />13.64.30.118<br />13.64.30.76<br />13.64.31.116<br />13.68.76.47|13.86.176.189<br />13.86.176.211<br />13.91.61.249<br />13.91.91.243<br />13.91.98.185<br />13.93.216.68<br />13.93.233.42<br />40.118.211.172<br />104.42.54.148<br />104.209.35.177<br /><br />|
> |US2|13.68.76.47<br />20.36.222.59<br />20.36.222.60<br />40.67.152.91<br />40.67.154.160<br />40.67.155.146<br />40.67.159.55<br />40.84.2.83<br />40.84.4.119<br />40.84.4.93|52.184.165.82<br />52.232.224.227<br />52.232.225.84<br />104.46.116.211<br />104.46.116.211<br />104.46.121.72<br />104.46.121.72<br />104.46.122.189<br />104.42.54.148<br />104.46.122.189<br />|
> |US3|13.68.76.47<br />40.90.218.196<br />40.90.218.197<br />40.90.218.198<br />40.90.218.203<br />40.90.220.190<br />40.90.220.196<br />51.143.120.236<br />51.143.120.242<br />104.42.54.148||
> |EU1|13.80.22.71<br />13.95.29.177<br />13.95.30.46<br />40.114.217.8<br />40.114.217.8<br />40.115.24.65<br />40.115.24.65<br />40.115.25.50<br />40.115.25.50<br />40.119.154.72|40.67.219.133<br />51.105.55.62<br />51.105.179.157<br />51.137.200.32<br />52.157.232.110<br />52.157.233.133<br />52.157.233.92<br />52.157.238.58<br />52.157.239.110<br />52.174.56.180|
> |EU2|40.81.152.171<br />40.81.152.172<br />40.81.156.153<br />40.81.156.154<br />40.81.156.155<br />40.81.156.156<br />51.105.55.62<br />51.137.200.32<br />51.145.108.227<br />51.145.108.250|
> |Gov US1|52.227.138.248<br />52.227.142.192<br />52.227.143.223|

## <a name="third-party-dlp-integration"></a>Integração do DLP de terceiros

Para habilitar o Cloud App Security a enviar dados por meio de seu stunnel para seu servidor ICAP, abra o firewall de rede de perímetro para esses endereços IP com um número da porta de origem dinâmico.

1. **Endereços de origem** – esses endereços devem ser colocados na lista de permissões conforme listado acima para aplicativos de terceiros de conector de API
2. **Porta TCP de origem** – dinâmica
3. **Endereços de destino** – um ou dois endereços IP do stunnel conectado ao servidor ICAP externo
4. **Porta TCP de destino** – conforme definido em sua rede

> [!NOTE]
>
> - Por padrão, o número da porta stunnel é definido como 11344. Você pode alterá-lo para outra porta, se necessário, mas certifique-se de anotar o novo número da porta.
> - Você pode ver esses endereços IP nos logs de atividades do fornecedor porque o Cloud App Security executa as ações de governança e as varreduras desses endereços IP.

Para se conectar a aplicativos de terceiros e integrar soluções de DLP externas, habilite o Cloud App Security para se conectar nesses endereços IP:

> [!div class="mx-tableFixed"]
>
> |Data center|Endereços IP||
> |----|----|----|
> |US1|13.64.196.27<br />13.64.198.19<br />13.64.198.97<br />13.64.199.41<br />13.64.26.88<br />13.64.29.32<br />13.64.30.117<br />13.64.30.118<br />13.64.30.76<br />13.64.31.116|13.86.176.189<br />13.86.176.211<br />13.91.61.249<br />13.91.91.243<br />13.91.98.185<br />13.93.216.68<br />13.93.233.42<br />40.118.211.172<br />104.209.35.177<br /><br />|
> |US2|20.36.222.59<br />20.36.222.60<br />40.67.152.91<br />40.67.154.160<br />40.67.155.146<br />40.67.159.55<br />40.84.2.83<br />40.84.4.119<br />40.84.4.93|52.184.165.82<br />52.232.224.227<br />52.232.225.84<br />104.46.116.211<br />104.46.116.211<br />104.46.121.72<br />104.46.121.72<br />104.46.122.189<br />104.46.122.189|
> |US3|40.90.218.196<br />40.90.218.197<br />40.90.218.198<br />40.90.218.203<br />40.90.220.190<br />40.90.220.196<br />51.143.120.236<br />51.143.120.242||
> |EU1|13.80.22.71<br />13.95.29.177<br />13.95.30.46<br />40.67.219.133<br />40.114.217.8<br />40.114.217.8<br />40.115.24.65<br />40.115.24.65<br />40.115.25.50|40.119.154.72<br />51.105.179.157<br />52.157.232.110<br />52.157.233.133<br />52.157.233.92<br />52.157.238.58<br />52.157.239.110<br />52.174.56.180<br /><br />|
> |EU2|40.81.152.171<br />40.81.152.172<br />40.81.156.153<br />40.81.156.154<br />40.81.156.155<br />40.81.156.156<br />51.145.108.227<br />51.145.108.250||

## <a name="mail-server"></a>Servidor de emails

Para habilitar as notificações a serem enviadas do modelo e das configurações padrão, adicione esses endereços IP à lista de permissões anti-spam. Os endereços IP de email dedicado do Cloud App Security são:

- 65.55.234.192/26
- 207.46.200.0/27
- 65.55.52.224/27
- 94.245.112.0/27
- 111.221.26.0/27
- 207.46.50.192/26

Se você quiser personalizar a identidade do remetente de email, o Microsoft Cloud App Security permitirá essa personalização usando o MailChimp®, um serviço de email de terceiros. Para facilitar o trabalho, no portal do Microsoft Cloud App Security, vá para **Configurações**. Selecione **Configurações de email** e examine os Termos de serviço e a Política de privacidade do MailChimp. Em seguida, dê à Microsoft permissão para usar o MailChimp em seu nome.

Se você não personalizar a identidade do remetente, as notificações de email serão enviadas usando todas as configurações padrão.

Para trabalhar com MailChimp, adicione esse endereço IP à lista de permissões anti-spam para permitir que as notificações sejam enviadas: 198.2.134.139 (mail1.cloudappsecurity.com)

## <a name="log-collector"></a>Coletor de logs

Para habilitar os recursos de Cloud Discovery usando um coletor de logs e detectar TI Sombra na sua organização, abra os seguintes itens:

- Permitir que o coletor de logs receba o tráfego FTP e Syslog de entrada.
- Permitir que o coletor de logs inicie o tráfego de saída para o portal (por exemplo, contoso.cloudappsecurity.com) na porta 443.
- Permita que o coletor de logs inicie o tráfego de saída para o Armazenamento de Blobs do Azure na porta 443:

  | Data center |                        URL                                 |
  |-------------|------------------------------------------------------------|
  |     US1     | https: \/ /adaprodconsole.blob.Core.Windows.net/             |
  |     US2     | https: \/ /prod03use2console1.blob.Core.Windows.net/         |
  |     US3     | https: \/ /prod5usw2console1.blob.Core.Windows.net/          |
  |     EU1     | https: \/ /prod02euwconsole1.blob.Core.Windows.net/          |
  |     EU2     | https: \/ /prod4uksconsole1.blob.Core.Windows.net/           |
  |   Gov US1   | https: \/ /gprd1usgvconsole1.blob.Core.usgovcloudapi.net/    |

> [!NOTE]
>
> - Se o firewall exigir uma lista de acesso de endereço IP estático e não for compatível com a lista de permissões baseada em URL, permita que o coletor de logs inicie o tráfego de saída para os [Intervalos de IP do datacenter do Microsoft Azure](https://www.microsoft.com/download/details.aspx?id=41653) na porta 443.
>- Permita que o coletor de logs inicie o tráfego de saída no portal do Cloud App Security.
>- Se você não especificou um proxy ao configurar o coletor de logs, precisará permitir conexões http http://ocsp.msocsp.com/ e OCSP.DigiCert.com na porta 80. Isso é usado para verificar o status de revogação de certificado ao se conectar ao portal do Cloud App Security.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]

---
title: Requisitos de rede
description: Este artigo descreve os endereços IP e portas que você precisa abrir para trabalhar com o Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 11/01/2019
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 5160d606c28bcd2d9f449f79785aca01a8250875
ms.sourcegitcommit: a0a8e25bda77fb21f280a0e504896be85b89ed6f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96033871"
---
# <a name="network-requirements"></a>Requisitos de rede

[!INCLUDE [Banner for top of topics](includes/banner.md)]

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

```ini
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
```

Para clientes de GCC do governo dos EUA, também é necessário adicionar os seguintes nomes DNS à lista de permissões do firewall para fornecer acesso ao portal do Cloud App Security GCC High:

```ini
    portal.cloudappsecurity.us
    *.portal.cloudappsecurity.us
    cdn.cloudappsecurity.com
```

Além disso, os itens a seguir devem estar na lista de permissões, dependendo do data center usado:

|Data center|Endereços IP|Nome DNS|
|----|----|----|
|US1|13.64.26.88, 13.64.29.32, 13.80.125.22, 13.91.91.243, 40.74.1.235, 40.74.6.204, 51.143.58.207, 52.137.89.147, 52.183.75.62|\*.us.portal.cloudappsecurity.com|
|US2|13.80.125.22, 20.36.222.59, 20.36.222.60, 40.74.1.235, 40.74.6.204, 51.143.58.207, 52.137.89.147, 52.183.75.62, 52.184.165.82|\*.us2.portal.cloudappsecurity.com|
|US3|13.80.125.22, 40.74.1.235, 40.74.6.204, 40.90.218.196, 40.90.218.198, 51.143.58.207, 52.137.89.147, 52.183.75.62|*.us3.portal.cloudappsecurity.com|
|EU1|13.80.125.22, 40.74.1.235, 40.74.6.204, 40.119.154.72, 51.143.58.207, 52.137.89.147, 52.157.238.58, 52.174.56.180, 52.183.75.62|\*.eu.portal.cloudappsecurity.com<|
|EU2|13.80.125.22, 40.74.1.235, 40.74.6.204, 40.81.156.154, 40.81.156.156, 51.143.58.207, 52.137.89.147, 52.183.75.62|*.eu2.portal.cloudappsecurity.com|
|Gov US1|13.72.19.4, 52.227.143.223|*. us1.portal.cloudappsecurity.us|

> [!NOTE]
> Em vez de um caractere curinga (\*), você pode abrir somente a URL específica do locatário, por exemplo, de acordo com a captura de tela acima, você poderá abrir mod244533.us.portal.cloudappsecurity.com

## <a name="access-and-session-controls"></a>Controles de acesso e sessão

Configure o firewall para o proxy reverso usando as configurações relevantes para o seu ambiente.

### <a name="commercial-customers"></a>Clientes comerciais

Para clientes comerciais, para habilitar Cloud App Security proxy reverso, adicione a **porta de saída 443** para os seguintes endereços IP e nomes DNS à lista de permissões do firewall:

```ini
    *.cas.ms
    *.mcas.ms
    *.admin-mcas.ms
    mcasproxy.azureedge.net
```

Além disso, os itens a seguir devem estar na lista de permissões, dependendo do data center usado:

|Data center|Endereços IP|Nome DNS|
|----|----|----|----|----|
|US1|20.40.134.94, 20.40.161.119, 20.40.161.135, 20.40.163.97, 20.40.163.133, 20.184.63.216, 20.184.63.232, 40.65.169.46, 40.65.169.97, 40.65.169.196, 40.65.169.236, 40.65.170.17, 40.66.59.41, 40.66.60.118, 40.66.60.180, 40.66.60.185, 40.66.60.200, 40.66.60.206, 40.66.60.207, 40.66.60.208, 40.66.62.78, 40.81.62.255, 40.81.63.1, 40.81.63.2, 40.81.63.4, 40.81.63.5, 40.81.63.8, 40.81.120.187, 40.81.121.107, 40.81.121.108, 40.81.121.111, 40.81.121.127, 40.81.122.76, 40.81.123.124, 40.81.127.140, 40.81.227.134, 40.81.227.152, 40.81.227.160, 40.81.227.163, 40.90.220.37, 40.91.114.44, 40.91.114.45, 40.91.114.46, 40.91.114.47, 40.91.114.48, 40.91.114.49, 40.91.126.157, 40.91.127.44, 40.119.215.167, 51.105.163.8, 51.105.163.43, 51.105.164.8, 51.105.165.31, 51.105.165.37, 51.105.165.63, 51.105.165.116, 51.105.166.102, 51.105.166.103, 51.105.166.106, 51.137.136.13, 51.137.136.14, 51.143.111.58, 52.142.112.145, 52.142.112.146, 52.142.116.135, 52.142.116.174, 52.142.116.250, 52.142.117.183, 52.142.121.6, 52.142.121.75, 52.148.115.238, 52.148.116.37, 52.156.197.254, 52.156.198.196|\*. us.cas.ms, \* . us.Access-Control.CAS.ms, \* . us.SAML.CAS.ms|
|US2|20.40.132.195, 20.40.161.140, 20.40.161.141, 20.40.163.88, 20.40.163.96, 40.65.170.26, 40.65.170.123, 40.65.170.125, 40.65.170.128, 40.65.170.133, 40.65.170.137, 40.66.56.158, 40.66.60.209, 40.66.60.210, 40.66.60.215, 40.66.60.216, 40.66.60.217, 40.66.60.219, 40.66.62.130, 40.66.63.148, 40.67.251.0, 40.81.58.180, 40.81.58.184, 40.81.58.193, 40.81.59.90, 40.81.59.93, 40.81.63.7, 40.81.121.135, 40.81.121.140, 40.81.122.62, 40.81.124.185, 40.81.127.25, 40.81.127.139, 40.81.127.141, 40.81.127.230, 40.119.207.131, 40.119.207.144, 51.137.137.118, 51.137.137.121, 52.139.245.40, 52.139.245.48, 52.142.127.127, 52.149.59.151, 52.149.60.12, 52.149.61.128, 52.149.61.214, 52.149.63.211, 52.151.237.243, 52.151.238.5, 52.155.166.50, 52.156.88.69, 52.156.88.173, 52.156.89.175, 52.156.89.188, 52.156.90.38, 52.156.197.208, 52.156.204.99, 52.156.205.222, 52.156.205.226, 52.156.206.45, 52.156.206.46, 52.156.206.47, 52.191.237.188, 52.191.238.65, 104.45.170.182, 104.45.170.184, 104.45.170.185, 104.45.170.188, 104.45.170.194, 104.45.170.196, 191.235.117.31, 191.235.119.253, 191.235.120.17, 191.235.121.69, 191.235.121.164, 191.235.122.60, 191.235.122.101, 191.235.122.224, 191.235.123.114, 191.235.123.242|\*. us2.cas.ms, \* . us2.Access-Control.CAS.ms, \* . us2.SAML.CAS.ms|
|US3|20.40.106.51, 20.40.107.84, 20.40.161.160, 20.40.161.161, 20.40.162.86, 20.40.162.200, 20.184.61.253, 20.184.63.158, 40.65.170.80, 40.65.170.81, 40.65.170.82, 40.65.170.83, 40.65.170.112, 40.65.170.113, 40.66.59.193, 40.66.59.195, 40.66.59.196, 40.66.59.246, 40.66.60.224, 40.66.60.226, 40.66.61.158, 40.66.61.193, 40.66.62.7, 40.66.62.9, 40.81.62.162, 40.81.62.179, 40.81.62.193, 40.81.62.220, 40.81.62.223, 40.81.62.224, 40.81.120.191, 40.81.120.192, 40.81.121.66, 40.81.123.157, 40.81.127.229, 40.81.127.239, 40.82.186.166, 40.82.186.168, 40.82.186.168, 40.82.186.169, 40.82.186.169, 40.82.186.176, 40.82.186.177, 40.82.186.177, 40.82.186.182, 40.82.186.182, 40.91.74.37, 40.91.78.105, 40.91.114.40, 40.91.114.41, 40.91.114.42, 40.91.114.43, 51.137.136.34, 51.137.137.69, 51.143.122.59, 51.143.122.60, 52.139.1.156, 52.139.1.156, 52.139.2.0, 52.139.2.0, 52.139.9.176, 52.139.9.198, 52.139.16.105, 52.139.16.105, 52.139.21.70, 52.139.21.70, 52.139.245.1, 52.139.245.21, 52.148.161.45, 52.148.161.53, 52.155.164.131, 52.155.167.231, 52.155.177.13, 52.155.178.247, 52.155.179.84, 52.155.180.208, 52.155.180.209, 52.155.180.210, 52.155.180.211, 52.155.182.138, 52.224.190.225, 52.224.191.62, 52.224.202.86, 52.224.202.91, 104.45.170.70, 104.45.170.178, 104.45.170.180, 104.45.170.183, 104.45.170.186, 104.45.170.191|\*. us3.cas.ms, \* . US3.Access-Control.CAS.ms, \* . US3.SAML.CAS.ms|
|EU1|20.40.106.50, 20.40.161.131, 20.40.161.132, 20.40.163.178, 20.40.163.179, 20.188.72.248, 40.67.254.233, 40.80.219.49, 40.80.220.215, 40.80.220.246, 40.80.221.77, 40.80.222.91, 40.80.222.197, 40.81.57.138, 40.81.57.141, 40.81.57.144, 40.81.57.157, 40.81.57.164, 40.81.57.169, 40.81.120.13, 40.81.120.24, 40.81.120.25, 40.81.121.76, 40.81.121.78, 40.81.122.63, 40.81.122.203, 40.119.207.164, 40.119.207.166, 40.119.207.174, 40.119.207.182, 40.119.207.193, 40.119.207.200, 51.137.137.200, 51.137.137.237, 51.145.181.195, 51.145.181.214, 52.139.251.219, 52.139.252.105, 52.148.115.188, 52.148.115.194, 52.151.244.65, 52.151.247.27, 52.153.240.107, 52.155.161.88, 52.155.161.91, 52.156.203.22, 52.156.203.199, 52.156.204.24, 52.156.204.51, 52.156.204.139, 52.156.205.137, 52.156.205.182, 52.157.218.219, 52.157.218.232, 52.157.232.147, 52.157.233.205, 52.157.234.160, 52.157.235.144, 52.157.237.107, 52.157.237.213, 52.224.201.216, 52.224.201.223, 52.249.25.160, 52.249.25.165, 104.45.168.103, 104.45.168.104, 104.45.168.106, 104.45.168.108, 104.45.168.111, 104.45.168.114|\*. eu1.cas.ms, \* . EU1.Access-Control.CAS.ms, \* . EU1.SAML.CAS.ms|
|EU2|20.40.134.79, 20.40.160.184, 20.40.161.142, 20.40.161.143, 20.40.163.130, 20.184.58.46, 20.184.60.77, 20.184.61.67, 40.66.57.203, 40.66.60.101, 40.66.60.220, 40.66.60.221, 40.66.60.222, 40.66.60.225, 40.66.60.232, 40.66.62.154, 40.66.62.225, 40.81.62.199, 40.81.62.206, 40.81.62.209, 40.81.62.212, 40.81.62.221, 40.81.62.222, 40.90.191.153, 40.119.145.130, 40.119.147.102, 40.119.203.98, 40.119.203.99, 40.119.203.158, 40.119.203.159, 40.119.203.208, 40.119.203.209, 51.105.164.234, 51.105.164.241, 52.142.124.23, 52.155.168.45, 52.155.181.180, 52.155.181.181, 52.155.181.182, 52.155.181.183, 52.155.182.48, 52.155.182.49, 52.155.182.50, 52.156.202.7, 52.157.233.49, 52.157.234.222, 52.157.235.27, 52.157.236.195, 52.157.237.255, 52.157.239.132, 52.190.26.220, 52.190.31.62, 52.224.188.157, 52.224.188.168, 104.45.170.127, 104.45.170.161, 104.45.170.173, 104.45.170.174, 104.45.170.175, 104.45.170.176|\*. eu2.cas.ms, \* . EU2.Access-Control.CAS.ms, \* . EU2.SAML.CAS.ms|

### <a name="us-government-gcc-high-customers"></a>Clientes com GCC do governo dos EUA

Para clientes do governo dos EUA GCC High, para habilitar Cloud App Security proxy reverso, adicione a **porta de saída 443** para os seguintes nomes DNS à lista de permissões do firewall:

```ini
    *.mcas-gov.us
    *.admin-mcas-gov.us
    mcasproxy.azureedge.net
```

## <a name="siem-agent-connection"></a>Conexão do agente SIEM

Para permitir que Cloud App Security se conectem ao SIEM, adicione a **porta de saída 443** para os seguintes endereços IP à lista de permissões do firewall:

|Data center|Endereços IP|
|----|----|
|US1|13.64.26.88, 13.64.29.32, 13.80.125.22, 13.91.91.243, 40.74.1.235, 40.74.6.204, 51.143.58.207, 52.137.89.147, 52.183.75.62|
|US2|13.80.125.22, 20.36.222.59, 20.36.222.60, 40.74.1.235, 40.74.6.204, 51.143.58.207, 52.137.89.147, 52.183.75.62, 52.184.165.82|
|US3|13.80.125.22, 40.74.1.235, 40.74.6.204, 40.90.218.196, 40.90.218.198, 51.143.58.207, 52.137.89.147, 52.183.75.62|
|EU1|13.80.125.22, 40.74.1.235, 40.74.6.204, 40.119.154.72, 51.143.58.207, 52.137.89.147, 52.157.238.58, 52.174.56.180, 52.183.75.62|
|EU2|13.80.125.22, 40.74.1.235, 40.74.6.204, 40.81.156.154, 40.81.156.156, 51.143.58.207, 52.137.89.147, 52.183.75.62|
|Gov US1|13.72.19.4, 52.227.143.223|

> [!NOTE]
> Se você não especificou um proxy ao configurar o agente SIEM Cloud App Security, precisará permitir conexões http http://ocsp.msocsp.com/ e OCSP.DigiCert.com na porta 80. Isso é usado para verificar o status de revogação de certificado ao se conectar ao portal do Cloud App Security.

## <a name="app-connector"></a>Conector de aplicativo

Para alguns aplicativos de terceiros serem acessados pelo Cloud App Security, esses endereços IP podem ser usados. Os endereços IP permitem ao Cloud App Security coletar logs e fornecer acesso ao console do Cloud App Security.

> [!NOTE]
> Você pode ver esses endereços IP nos logs de atividades do fornecedor porque o Cloud App Security executa as ações de governança e as varreduras desses endereços IP.

Para se conectar a aplicativos de terceiros, habilite o Cloud App Security para se conectar nesses endereços IP:

|Data center|Endereços IP|
|----|----|----|
|US1|13.64.26.88, 13.64.29.32, 13.64.30.76, 13.64.30.117, 13.64.30.118, 13.64.31.116, 13.64.196.27, 13.64.198.19, 13.64.198.97, 13.64.199.41, 13.68.76.47, 13.86.176.189, 13.86.176.211, 13.91.61.249, 13.91.91.243, 13.91.98.185, 13.93.216.68, 13.93.233.42, 40.118.211.172, 104.42.54.148, 104.209.35.177|
|US2|13.68.76.47, 20.36.222.59, 20.36.222.60, 40.67.152.91, 40.67.154.160, 40.67.155.146, 40.67.159.55, 40.84.2.83, 40.84.4.93, 40.84.4.119, 52.184.165.82, 52.232.224.227, 52.232.225.84, 104.42.54.148, 104.46.116.211, 104.46.116.211, 104.46.121.72, 104.46.121.72, 104.46.122.189, 104.46.122.189|
|US3|13.68.76.47, 40.90.218.196, 40.90.218.197, 40.90.218.198, 40.90.218.203, 40.90.220.190, 40.90.220.196, 51.143.120.236, 51.143.120.242, 104.42.54.148|
|EU1|13.80.22.71, 13.95.29.177, 13.95.30.46, 40.67.219.133, 40.114.217.8, 40.114.217.8, 40.115.24.65, 40.115.24.65, 40.115.25.50, 40.115.25.50, 40.119.154.72, 51.105.55.62, 51.105.179.157, 51.137.200.32, 52.157.232.110, 52.157.233.92, 52.157.233.133, 52.157.238.58, 52.157.239.110, 52.174.56.180|
|EU2|40.81.152.171, 40.81.152.172, 40.81.156.153, 40.81.156.154, 40.81.156.155, 40.81.156.156, 51.105.55.62, 51.137.200.32, 51.145.108.227, 51.145.108.250|
|Gov US1|52.227.138.248, 52.227.142.192, 52.227.143.223|

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

|Data center|Endereços IP|
|----|----|----|
|US1|13.64.26.88, 13.64.29.32, 13.64.30.76, 13.64.30.117, 13.64.30.118, 13.64.31.116, 13.64.196.27, 13.64.198.19, 13.64.198.97, 13.64.199.41, 13.86.176.189, 13.86.176.211, 13.91.61.249, 13.91.91.243, 13.91.98.185, 13.93.216.68, 13.93.233.42, 40.118.211.172, 104.209.35.177|
|US2|20.36.222.59, 20.36.222.60, 40.67.152.91, 40.67.154.160, 40.67.155.146, 40.67.159.55, 40.84.2.83, 40.84.4.93, 40.84.4.119, 52.184.165.82, 52.232.224.227, 52.232.225.84, 104.46.116.211, 104.46.116.211, 104.46.121.72, 104.46.121.72, 104.46.122.189, 104.46.122.189|
|US3|40.90.218.196, 40.90.218.197, 40.90.218.198, 40.90.218.203, 40.90.220.190, 40.90.220.196, 51.143.120.236, 51.143.120.242|
|EU1|13.80.22.71, 13.95.29.177, 13.95.30.46, 40.67.219.133, 40.114.217.8, 40.114.217.8, 40.115.24.65, 40.115.24.65, 40.115.25.50, 40.119.154.72, 51.105.179.157, 52.157.232.110, 52.157.233.92, 52.157.233.133, 52.157.238.58, 52.157.239.110, 52.174.56.180|
|EU2|40.81.152.171, 40.81.152.172, 40.81.156.153, 40.81.156.154, 40.81.156.155, 40.81.156.156, 51.145.108.227, 51.145.108.250|

## <a name="mail-server"></a>Servidor de emails

Para habilitar as notificações a serem enviadas do modelo e das configurações padrão, adicione esses endereços IP à lista de permissões anti-spam. Os endereços IP de email dedicado do Cloud App Security são:

- 65.55.234.192/26
- 207.46.50.192/26
- 65.55.52.224/27
- 94.245.112.0/27
- 111.221.26.0/27
- 207.46.200.0/27

Se você quiser personalizar a identidade do remetente do email, Microsoft Cloud App Security habilitar a personalização usando &reg; o MailChimp, um serviço de email de terceiros. Para facilitar o trabalho, no portal do Microsoft Cloud App Security, vá para **Configurações**. Selecione **configurações de email** e examine os termos de serviço e a política de privacidade do MailChimp. Em seguida, dê à Microsoft permissão para usar o MailChimp em seu nome.

Se você não personalizar a identidade do remetente, suas notificações de email serão enviadas usando todas as configurações padrão.

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
> - Se o firewall exigir uma lista de acesso a endereços IP estáticos e não oferecer suporte à permissão com base na URL, permita que o coletor de logs inicie o tráfego de saída para os [intervalos de IP do datacenter Microsoft Azure](https://www.microsoft.com/download/details.aspx?id=56519) na porta 443.
> - Permita que o coletor de logs inicie o tráfego de saída no portal do Cloud App Security.
> - Se você não especificou um proxy ao configurar o coletor de logs, precisará permitir conexões http http://ocsp.msocsp.com/ e OCSP.DigiCert.com na porta 80. Isso é usado para verificar o status de revogação de certificado ao se conectar ao portal do Cloud App Security.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]

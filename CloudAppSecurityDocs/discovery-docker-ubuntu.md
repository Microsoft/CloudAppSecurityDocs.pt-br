---
title: "Configurar o upload de log automático para relatórios contínuos | Microsoft Docs"
description: "Este tópico descreve o processo de configuração do upload automático de log para relatórios contínuos no Cloud App Security usando um Docker no Ubuntu."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 7/16/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: cc29a6cb-1c03-4148-8afd-3ad47003a1e3
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: e32eebc75355e8016fcdb62a1b113431db346c31
ms.sourcegitcommit: ae4c8226f6037c5eb286eb27142d6bbb397609e9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/16/2017
---
# <a name="set-up-and-configuration-on-ubuntu"></a>Instalação e configuração no Ubuntu

## <a name="technical-requirements"></a>Requisitos técnicos

-   SO: Ubuntu 14.04 ou superior

-   Espaço em disco: 250 GB

-   CPU: 2

-   RAM: 4 GB

-   Configurações de firewall:

    -   Permitir que o coletor de logs receba o tráfego FTP e Syslog de entrada.

    -   Permitir que o coletor de logs inicie o tráfego de saída para o portal (por exemplo, contoso.cloudappsecurity.com) na porta 443.

## <a name="log-collector-performance"></a>Desempenho do coletor de logs

O coletor de logs pode lidar com êxito com a capacidade de logs de até 50 GB por hora. Os principais afunilamentos no processo de coleta de logs são:

-   Largura de banda da rede: a largura de banda da rede determina a velocidade de upload do log.

-   Desempenho de E/S da máquina virtual alocada pela sua equipe de TI: determina a velocidade na qual os logs são gravados no disco do coletor de logs. O coletor de logs tem um mecanismo de segurança interno que monitora a taxa na qual os logs chegam e a compara à taxa de upload. Em casos de congestionamento, o coletor de logs começa a remover os arquivos de log. Se sua configuração normalmente excede 50 GB por hora, é recomendável dividir o tráfego entre vários coletores de logs.

## <a name="step-1--web-portal-configuration-define-data-sources-and-link-them-to-a-log-collector"></a>Etapa 1 — Configuração do portal da Web: definir fontes de dados e vinculá-las a um coletor de logs

1.  Acesse a página de configuração de upload automatizado:  <br></br>No portal do Cloud App Security, clique no ícone de configurações ![ícone de configurações](./media/settings-icon.png), antes de **Coletores de log**.

2.  Para cada firewall ou proxy do qual você deseja carregar logs, crie uma fonte de dados correspondente:

    ![ubuntu1](./media/ubuntu1.png)

    a. Clique em **Adicionar fonte de dados**.

    b. Atribua o **Nome** do proxy ou firewall.

    c. Selecione o dispositivo na lista **Fonte**.

    d. Compare seu log com o exemplo do formato de log esperado. Se seu formato de arquivo de log não corresponder a esse exemplo, você deverá adicionar sua fonte de dados como **Outro**.

    e. Defina o **Tipo de destinatário** como **FTP**, **FTPS**, **Syslog – UDP** ou **Syslog – TCP** ou **Syslog – TLS**.
    >[!NOTE]
    >A integração com protocolos de transferência segura (FTPS e Syslog – TLS) geralmente requer seu firewall/proxy ou configurações adicionais.

    f. Repita esse processo para cada firewall e proxy cujos logs podem ser usados para detectar o tráfego na rede.

3.  Vá para a guia **Coletores de logs** na parte superior.

    a. Clique em **Adicionar coletor de logs**.

    b. Atribua um **nome** ao coletor de logs.

    c. Insira o **endereço IP do Host** do computador que você usará para implantar o Docker.

    d. Selecione todas as **Fontes de dados** que quer conectar ao coletor e clique em **Atualizar** para salvar a configuração e ver as próximas etapas de implantação.

    ![ubuntu2](./media/ubuntu2.png)

    >  [!NOTE]
    > - Um único coletor de logs pode lidar com várias fontes de dados.
    >- Copie o conteúdo da tela, pois você precisará das informações ao configurar o Coletor de Logs para se comunicar com o Cloud App Security. Se você selecionou Syslog, essa informação incluirá informações sobre qual porta o ouvinte do Syslog está escutando.

4.  Mais informações sobre a implantação serão exibidas.

 ![ubuntu3](./media/ubuntu3.png)

5.  **Copie** o comando de execução da caixa de diálogo. Você pode usar o ícone copiar para área de transferência ![ícone copiar para área de transferência](./media/copy-icon.png).

6.  **Exporte** a configuração de fonte de dados esperada. Essa configuração descreve como você deve definir a exportação de log em seus dispositivos.

  ![ubuntu4](./media/ubuntu4.png)

## <a name="step-2--on-premises-deployment-of-your-machine"></a>Etapa 2 – implantação local de seu computador

> [!Note]
> As etapas a seguir descrevem a implantação no Ubuntu. As etapas de implantação para outras plataformas são ligeiramente diferentes.

1.  Abra um terminal em seu computador Ubuntu.

2.  Altere para privilégios de raiz usando o comando: `Sudo - i`

3.  Desinstale versões antigas e instale o Docker CE executando o seguinte comando:

    `curl -o /tmp/MCASInstallDocker.sh
    https://adaprodconsole.blob.core.windows.net/public-files/MCASInstallDocker.sh
    && chmod +x /tmp/MCASInstallDocker.sh; sudo /tmp/MCASInstallDocker.sh`

    ![ubuntu5](./media/ubuntu5.png)

4.  Implante a imagem do coletor usando o comando de execução gerado no portal.

    ![ubuntu6](./media/ubuntu6.png)

    >[!NOTE]
    >Se precisar configurar um proxy, adicione o endereço IP do proxy e a porta. Por exemplo, se os detalhes de proxy são 192.168.10.1:8080, o comando de execução atualizado é:<br></br>
     `Sudo docker run --name casCollector -p 21:21 -p 20000-20099:20000-20099 -e
    "PUBLICIP='192.168.1.1'" -e "PROXY=192.168.10.1:8080" -e
    "TOKEN=41f8f442c9a30519a058dd3bb9a19c79eb67f34a8816270dc4a384493988863a" -e
    "CONSOLE=tenant2.eu1-rs.adallom.com" -e "COLLECTOR=casCollector" --security-opt
    apparmor:unconfined --cap-add=SYS_ADMIN -dt microsoft/caslogcollector starter`

    ![ubuntu7](./media/ubuntu7.png)

5.  Verifique se o coletor está funcionando corretamente executando o seguinte comando: `Docker logs \<collector_name\>`

Você verá a mensagem: **Concluído com êxito!**

  ![ubuntu8](./media/ubuntu8.png)

## <a name="step-4---on-premises-configuration-of-your-network-appliances"></a>Etapa 4 — Configuração local de seus dispositivos de rede

Configure seus proxies e firewalls de rede para periodicamente exportar logs para a porta de Syslog dedicada do diretório de FTP acordo com as instruções na caixa de diálogo, por exemplo:

    BlueCoat_HQ - Destination path: \<<machine_name>>\BlueCoat_HQ\

## <a name="step-5---verify-the-successful-deployment-in-the-cloud-app-security-portal"></a>Etapa 5 — Verificar a implantação bem-sucedida no portal do Cloud App Security

Verifique o status do coletor na tabela **Coletor de logs** e verifique se o status é **Conectado**. Se for **criado**, será possível que a conexão do coletor de logs e a análise não tenham sido concluídas.

 ![ubuntu9](./media/ubuntu9.png)

Você também pode ir para o **log de governança** e verificar se que os logs estão sendo carregados periodicamente no portal.

Se você encontrar problemas durante a implantação, confira [Solucionando problemas de Cloud Discovery](troubleshooting-cloud-discovery.md).

## <a name="see-also"></a>Consulte também
[Trabalhando com os dados do Cloud Discovery](working-with-cloud-discovery-data.md)  
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security](http://support.microsoft.com/oas/default.aspx?prid=16031)  
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier](https://premier.microsoft.com/)


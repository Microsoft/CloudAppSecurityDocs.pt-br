---
title: "Configurar o upload de log automático para relatórios contínuos | Microsoft Docs"
description: "Este tópico descreve o processo de configuração do upload automático de logs para relatórios contínuos no Cloud App Security usando um Docker no Ubuntu no Azure."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/15/2018
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 9c51b888-54c0-4132-9c00-a929e42e7792
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 03ace8d5bf61ed623ad90b3717c4d35b767498a3
ms.sourcegitcommit: 458e936e1ac548eda37e9bf955b439199bbdd018
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2018
---
# <a name="set-up-and-configuration-on-ubuntu"></a>Instalação e configuração no Ubuntu


## <a name="technical-requirements"></a>Requisitos técnicos

-   Sistema operacional: Ubuntu 14.04 ou superior (não há nenhuma versão estável do docker que seja compatível com o Ubuntu 17.10)

-   Espaço em disco: 250 GB

-   CPU: 2

-   RAM: 4 GB

-   Defina o firewall conforme descrito nos [Requisitos de rede](network-requirements#log-collector)

## <a name="log-collector-performance"></a>Desempenho do coletor de logs

O coletor de logs pode lidar com êxito com a capacidade de logs de até 50 GB por hora. Os principais gargalos no processo de coleta de logs são:

-   Largura de banda da rede: a largura de banda da rede determina a velocidade de upload do log.

-   Desempenho de E/S da máquina virtual alocada pela sua equipe de TI: determina a velocidade na qual os logs são gravados no disco do coletor de logs. O coletor de logs tem um mecanismo de segurança interno que monitora a taxa na qual os logs chegam e a compara à taxa de upload. Em casos de congestionamento, o coletor de logs começa a remover os arquivos de log. Se sua configuração geralmente excede 50 GB por hora, é recomendável que você divida o tráfego entre vários coletores de logs.

## <a name="set-up-and-configuration"></a>Instalação e configuração  

### <a name="step-1--web-portal-configuration-define-data-sources-and-link-them-to-a-log-collector"></a>Etapa 1 — Configuração do portal da Web: definir fontes de dados e vinculá-las a um coletor de logs

1.  Acesse a página de configuração de upload automatizado:  <br></br>No portal do Cloud App Security, clique no ícone de configurações ![ícone de configurações](./media/settings-icon.png), antes de **Coletores de log**.

2.  Para cada firewall ou proxy do qual você deseja carregar logs, crie uma fonte de dados correspondente:

    ![ubuntu1](./media/ubuntu1.png)

    a. Clique em **Adicionar fonte de dados**.

    b. Atribua o **Nome** do proxy ou firewall.

    c. Selecione o dispositivo na lista **Fonte**. Se você selecionar **Formato de log personalizado** para trabalhar com um dispositivo de rede que não esteja listado especificamente, veja [Trabalhando com o analisador de log personalizado](custom-log-parser.md) para obter instruções de configuração.

    d. Compare seu log com o exemplo do formato de log esperado. Se seu formato de arquivo de log não corresponder a esse exemplo, você deverá adicionar sua fonte de dados como **Outro**.

    e. Definir o **Tipo de destinatário** como **FTP**, **FTPS**, **Syslog – UDP** ou **Syslog – TCP** ou **Syslog – TLS**.
    >[!NOTE]
    >A integração com protocolos de transferência segura (FTPS e Syslog – TLS) geralmente requer configuração adicional ou seu firewall/proxy.

    f. Repita esse processo para cada firewall e proxy cujos logs podem ser usados para detectar o tráfego na rede.

3.  Vá para a guia **Coletores de logs** na parte superior.

    a. Clique em **Adicionar coletor de logs**.

    b. Atribua um **nome** ao coletor de logs.

    c. Insira o **Endereço IP de host** do computador que você usará para implantar o Docker. 

     > [!NOTE]
     > O endereço IP do host pode ser substituído pelo nome do computador, caso haja um servidor DNS (ou equivalente) que resolverá o nome do host.

    d. Selecione todas as **Fontes de dados** que quer conectar ao coletor e clique em **Atualizar** para salvar a configuração e consulte as próximas etapas de implantação.

    ![ubuntu2](./media/ubuntu2.png)

    >  [!NOTE]
    > - Um único coletor de logs pode lidar com várias fontes de dados.
    >- Copie o conteúdo da tela, pois você precisará das informações ao configurar o Coletor de Logs para se comunicar com o Cloud App Security. Se você selecionou Syslog, essa informação incluirá informações sobre qual porta o ouvinte do Syslog está escutando.

4.  Mais informações sobre a implantação serão exibidas. **Copiar** o comando de execução na caixa de diálogo. Você pode usar o ícone copiar para a área de transferência ![ícone copiar para a área de transferência](./media/copy-icon.png).

6.  **Exportar** a configuração de fonte de dados esperada. Essa configuração descreve como você deve definir a exportação de log em seus dispositivos.

   ![Crie o coletor de logs](./media/windows7.png)

### <a name="step-2--deployment-of-your-machine-in-azure"></a>Etapa 2 – Implantação de seu computador no Azure

> [!NOTE]
> As etapas a seguir descrevem a implantação no Ubuntu. As etapas de implantação para outras plataformas são ligeiramente diferentes.


1.  Crie um novo computador Ubuntu no seu ambiente do Azure. 
2.  Depois que o computador estiver pronto, abra as portas pelos caminhos a seguir:
    1.  Na exibição de máquina, acesse **Rede** e selecione a interface relevante clicando duas vezes nela.
    2.  Acesse **Grupo de Segurança de Rede** e selecione o grupo de segurança de rede relevante.
    3.  Acesse **Regras de segurança de entrada** e clique em **Adicionar**,
      
      ![Azure no Ubuntu](./media/ubuntu-azure.png)
    
    4. Adicionar as seguintes regras (no modo **Avançado**):

    |Nome|Intervalos de porta de destino|Protocolo|Origem|Destination|
    |----|----|----|----|----|
    |caslogcollector_ftp|21|TCP|<Sub-rede do endereço IP do dispositivo>|qualquer|
    |caslogcollector_ftp_passive|20000-20099|TCP|<Sub-rede do endereço IP do dispositivo>|qualquer|
    |caslogcollector_syslogs_tcp|601-700|TCP|<Sub-rede do endereço IP do dispositivo>|qualquer|
    |caslogcollector_syslogs_udp|514-600|UDP|<Sub-rede do endereço IP do dispositivo>|qualquer|
      
     ![Regras do Azure no Ubuntu](./media/inbound-rule.png)

3.  Volte para o computador e clique em **Conectar** para abrir um terminal no computador.

4.  Altere para privilégios de raiz usando `sudo -i`.

5.  Se aceitar os [termos de licença de software](https://go.microsoft.com/fwlink/?linkid=862492), desinstale as versões antigas e instale o Docker CE executando o seguinte comando:
        
        curl -o /tmp/MCASInstallDocker.sh https://adaprodconsole.blob.core.windows.net/public-files/MCASInstallDocker.sh && chmod +x /tmp/MCASInstallDocker.sh; /tmp/MCASInstallDocker.sh

      ![Comando do Azure no Ubuntu](./media/ubuntu-azure-command.png)

6. No portal do Cloud App Security, na janela **Criar novo coletor de log**, copie o comando para importar a configuração do coletor no computador de hospedagem:

      ![Azure no Ubuntu](./media/windows7.png)

7. Execute o comando para implantar o coletor de logs.
     
        (echo db3a7c73eb7e91a0db53566c50bab7ed3a755607d90bb348c875825a7d1b2fce) | docker run --name MyLogCollector -p 21:21 -p 20000-20099:20000-20099 -e "PUBLICIP='192.168.1.1'" -e "PROXY=192.168.10.1:8080" -e "CONSOLE=mod244533.us.portal.cloudappsecurity.com" -e "COLLECTOR=MyLogCollector" --security-opt apparmor:unconfined --cap-add=SYS_ADMIN --restart unless-stopped -a stdin -i microsoft/caslogcollector starter

     ![Proxy do Ubuntu](./media/ubuntu-proxy.png)

8. Para verificar se o coletor de logs está sendo executado corretamente, execute o seguinte comando: `Docker logs <collector_name>`. Você deve obter os resultados: **Concluído com êxito!**

   ![ubuntu8](./media/ubuntu8.png)

### <a name="step-3---on-premises-configuration-of-your-network-appliances"></a>Etapa 3 — Configuração local de seus dispositivos de rede

Configure seus proxies e firewalls de rede para periodicamente exportar logs para a porta de Syslog dedicada do diretório de FTP acordo com as instruções na caixa de diálogo, por exemplo:

    BlueCoat_HQ - Destination path: \<<machine_name>>\BlueCoat_HQ\

### <a name="step-4---verify-the-successful-deployment-in-the-cloud-app-security-portal"></a>Etapa 4 — Verificar a implantação bem-sucedida no portal do Cloud App Security

Verifique o status do coletor na tabela **Coletor de logs** e verifique se o status é **Conectado**. Se for **criado**, será possível que a conexão do coletor de logs e a análise não tenham sido concluídas.

 ![ubuntu9](./media/ubuntu9.png)

Você também pode acessar o **Log de governança** e verificar se os logs estão sendo carregados periodicamente no portal.

Se você encontrar problemas durante a implantação, confira [Solucionando problemas de Cloud Discovery](troubleshooting-cloud-discovery.md).

### <a name="optional---create-custom-continuous-reports"></a>Opcional – Criar relatórios contínuos personalizados

Após ter verificado que os logs estão sendo carregados no Cloud App Security e os relatórios sendo gerados, você pode criar relatórios personalizados. Agora você pode criar relatórios de descoberta personalizados com base em grupos de usuários do Azure Active Directory. Por exemplo, se você quiser ver o uso de nuvem de seu departamento de marketing, será possível importar o grupo de marketing usando o recurso importar grupo de usuários e, em seguida, criar um relatório personalizado para este grupo. Você também pode personalizar um relatório com base na marca do endereço IP ou intervalos de endereços IP.

1. No portal do Cloud App Security, sob a engrenagem de configurações, selecione **Configurações do Cloud Discovery** e, em seguida, selecione **Gerenciar relatórios contínuos**. 
2. Clique no botão **Criar relatório** e preencha os campos.
3. Em **Filtros**, você pode filtrar os dados de acordo com a fonte de dados, por [grupo de usuários importados](user-groups.md) ou por [marcas e intervalos de endereços IP](ip-tags.md). 

![Relatório contínuo personalizado](./media/custom-continuous-report.png)

## <a name="see-also"></a>Consulte Também
[Solução de problemas de implantação do docker do Cloud Discovery](troubleshoot-docker.md)

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier](https://premier.microsoft.com/)


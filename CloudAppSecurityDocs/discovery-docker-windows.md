---
title: "Configurar o upload de log automático para relatórios contínuos usando um Docker no Windows | Microsoft Docs"
description: "Este tópico descreve o processo de configuração de carregamento automático de log para relatórios contínuos no Cloud App Security usando um Docker no Windows."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 9/6/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 308c06b3-f58b-4a21-86f6-8f87823a893a
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 87bff98075e9ec170442f5611828c79bf7bd43b6
ms.sourcegitcommit: ccee5664f5c49d5bae3748021d5b20dcf637d317
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2017
---
# <a name="set-up-and-configure-the-automatic-log-collector-docker-on-windows-server-2016"></a>Instalar e configurar o Docker de coletor de log automático no Windows Server 2016

> [!NOTE]
> Este recurso está sendo gradualmente distribuído entre locatários. Contate o suporte se você gostaria de ser adicionado à versão prévia.

## <a name="technical-requirements"></a>Requisitos técnicos

-   Sistema operacional: Windows Server 2016 ou Windows 10

-   Espaço em disco: 250 GB

-   CPU: 2

-   RAM: 4 GB

-   Configurações de firewall:

    -   Permitir que o coletor de logs receba o tráfego FTP e Syslog de entrada.

    -   Permitir que o coletor de logs inicie o tráfego de saída para o portal (por exemplo, contoso.cloudappsecurity.com) na porta 443.

## <a name="log-collector-performance"></a>Desempenho do coletor de logs

O coletor de logs pode lidar com êxito com a capacidade de logs de até 50 GB por hora. Os principais afunilamentos no processo de coleta de logs são:

-   Largura de banda da rede: a largura de banda da rede determina a velocidade de upload do log.

-   Desempenho de E/S da máquina virtual alocada pela sua equipe de TI: determina a velocidade na qual os logs são gravados no disco do coletor de logs. O coletor de logs tem um mecanismo de segurança interno que monitora a taxa na qual os logs chegam e a compara à taxa de upload. Em casos de congestionamento, o coletor de logs começa a remover os arquivos de log. Se sua configuração geralmente excede 50 GB por hora, é recomendável dividir o tráfego entre vários coletores de logs.

## <a name="set-up-and-configuration"></a>Instalação e configuração  

### <a name="step-1--web-portal-configuration-define-data-sources-and-link-them-to-a-log-collector"></a>Etapa 1 — Configuração do portal da Web: definir fontes de dados e vinculá-las a um coletor de logs

1.  Acesse a página de configuração de upload automatizado:<br></br> No portal do Cloud App Security, clique no ícone de configurações [ícone de configurações](./media/settings-icon.png), antes de **Coletores de log**.

2.  Para cada firewall ou proxy do qual você deseja carregar logs, crie uma fonte de dados correspondente:

    ![Windows 1](./media/windows1.png)

    a. Clique em **Adicionar fonte de dados**.

    b. Atribua o **Nome** do proxy ou firewall.

    c. Selecione o dispositivo na lista **Fonte**. Se você selecionar **Formato de log personalizado** para trabalhar com um dispositivo de rede que não esteja listado especificamente, veja [Trabalhando com o analisador de log personalizado](custom-log-parser.md) para obter instruções de configuração.

    d. Compare seu log com o exemplo do formato de log esperado. Se seu formato de arquivo de log não corresponder a esse exemplo, você deverá adicionar sua fonte de dados como **Outro**.

    e. Definir o **Tipo de destinatário** como **FTP**, **FTPS**, **Syslog – UDP** ou **Syslog – TCP** ou **Syslog – TLS**.

    > [!NOTE]
    > A integração com protocolos de transferência segura (FTPS e Syslog – TLS) geralmente requer configuração adicional ou seu Firewall/Proxy.

    f. Repita esse processo para cada firewall e proxy cujos logs podem ser usados para detectar o tráfego na rede.

3.  Vá para a guia **Coletores de logs** na parte superior.

    a. Clique em **Adicionar coletor de logs**.

    b. Atribua um **nome** ao coletor de logs.

    c. Insira o **endereço IP de host** do computador que você usará para implantar o Docker.

    d. Selecione todas as **Fontes de dados** que quer conectar ao coletor e clique em **Atualizar** para salvar a configuração e consulte as próximas etapas de implantação.

    ![Windows2](./media/windows2.png)

    > [!NOTE]
    > - Um único coletor de logs pode lidar com várias fontes de dados.

    > -   Copie o conteúdo da tela, pois você precisará das informações ao configurar o Coletor de Logs para se comunicar com o Cloud App Security. Se você selecionou Syslog, essa informação incluirá informações sobre qual porta o ouvinte do Syslog está escutando.

4.  Mais informações sobre a implantação serão exibidas.

    ![Windows3](./media/windows3.png)

5.  **Copiar** o comando de execução na caixa de diálogo. Você pode usar o ícone copiar para a área de transferência [ícone copiar para a área de transferência](./media/copy-icon.png).

6.  **Exportar** a configuração de fontes de dados esperada. Essa configuração descreve como você deve definir a exportação de log em seus dispositivos.

    ![Windows4](./media/windows4.png)

### <a name="step-2--on-premises-deployment-of-your-machine"></a>Etapa 2 – Implantação local de seu computador

>[!NOTE]
>As etapas a seguir descrevem a implantação no Windows Server. As etapas de implantação para outras plataformas são ligeiramente diferentes.

1.  **Baixe** o [Docker estável mais recente para Windows](https://docs.docker.com/docker-for-windows/install/\#download-docker-for-windows).
    
2.  **Execute** o instalador InstallDocker.msi.

3.  Abra um terminal do PowerShell no seu computador Windows.

4.  **Conecte-se** ao hub do Docker usando o seguinte comando:`docker login -u caslogcollector`

5.  Use a senha a seguir `C0llector3nthusiast`

    ![windows5](./media/windows5.png)

6.  **Efetue pull** para a imagem do coletor do hub do Docker usando o seguinte comando:`docker pull microsoft/caslogcollector`

    ![windows6](./media/windows6.png)

7.  Implante a imagem do coletor usando o comando run gerado no portal.

    ![windows8](./media/windows8.png)

    >[!NOTE]
    >Se você precisa configurar um proxy, adicione o endereço IP do proxy e a porta correspondente. Por exemplo, se os detalhes de proxy são 192.168.10.1:8080, seu comando de execução atualizado é:  
 `   docker run --name MyLogCollector -p 21:21 -p 20000-20099:20000-20099 -e
    "PUBLICIP='192.168.1.1'" -e "PROXY=192.168.10.1:8080" -e
    "TOKEN=41f8f442c9a30519a058dd3bb9a19c79eb67f34a8816270dc4a384493988863a" -e
    "CONSOLE=tenant2.eu1-rs.adallom.com" -e "COLLECTOR=MyLogCollector" --security-opt
    apparmor:unconfined --cap-add=SYS_ADMIN -dt microsoft/caslogcollector starter`

    ![windows9](./media/windows9.png)

9.  Verifique se o coletor está sendo executado corretamente executando o seguinte comando:`docker logs <collector_name>`

Você deverá ver a mensagem **Concluído com êxito!**.
  ![windows10](./media/windows10.png)

### <a name="step-3---on-premises-configuration-of-your-network-appliances"></a>Etapa 3 — Configuração local de seus dispositivos de rede

Configure seus proxies e firewalls de rede para periodicamente exportar logs para a porta de Syslog dedicada do diretório de FTP acordo com as instruções na caixa de diálogo, por exemplo:

        BlueCoat_HQ - Destination path: \<<machine_name>>\BlueCoat_HQ\

### <a name="step-4---verify-the-successful-deployment-in-the-cloud-app-security-portal"></a>Etapa 4 — Verificar a implantação bem-sucedida no portal do Cloud App Security

Verifique o status do coletor na tabela **Coletor de logs** e verifique se o status é **Conectado**. Se for **criado**, será possível que a conexão do coletor de logs e a análise não tenham sido concluídas.

![windows11](./media/windows11.png)

Você também pode acessar o **Log de governança** e verificar se os logs estão sendo carregados periodicamente no portal.

Se você encontrar problemas durante a implantação, confira [Solucionando problemas de Cloud Discovery](troubleshooting-cloud-discovery.md).

## <a name="optional---create-custom-continuous-reports"></a>Opcional – Criar relatórios contínuos personalizados

Após ter verificado que os logs estão sendo carregados no Cloud App Security e os relatórios sendo gerados, você pode criar relatórios personalizados. Agora você pode criar relatórios de descoberta personalizados com base em grupos de usuários do Azure Active Directory. Por exemplo, se você quiser ver o uso de nuvem de seu departamento de marketing, será possível importar o grupo de marketing usando o recurso importar grupo de usuários e, em seguida, criar um relatório personalizado para este grupo. Você também pode personalizar um relatório com base na marca do endereço IP ou intervalos de endereços IP.

1. No portal do Cloud App Security, sob a engrenagem de configurações, selecione **Configurações do Cloud Discovery** e, em seguida, selecione **Gerenciar relatórios contínuos**. 
2. Clique no botão **Criar relatório** e preencha os campos.
3. Em **Filtros**, você pode filtrar os dados de acordo com a fonte de dados, por [grupo de usuários importados](user-groups.md) ou por [marcas e intervalos de endereços IP](ip-tags.md). 

![Relatório contínuo personalizado](./media/custom-continuous-report.png)

## <a name="see-also"></a>Veja também
 
[Criar instantâneo de relatórios do Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

[Configurar upload de log automático para relatórios contínuos](configure-automatic-log-upload-for-continuous-reports.md)

[Trabalhando com os dados do Cloud Discovery](working-with-cloud-discovery-data.md)


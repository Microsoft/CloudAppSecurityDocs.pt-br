---
title: Configurar o upload de logs automático para relatórios contínuos no Cloud App Security| Microsoft Docs
description: Este tópico fornece informações sobre como fazer upload dos logs para criar relatórios automáticos do Cloud Discovery.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/22/2018
ms.topic: article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: c4123272-4111-4445-b6bd-2a1efd3e0c5c
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 8e3e75687839e96d92c50f6fba132b49c06c62bd
ms.sourcegitcommit: 45311f2cafef79483e40d971a4c61c7673834d96
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2018
---
*Aplica-se ao: Microsoft Cloud App Security*

# <a name="configure-automatic-log-upload-for-continuous-reports-on-a-virtual-appliance---deprecated"></a>Configurar o carregamento de log automático para relatórios contínuos em uma solução de virtualização – Preterido

> [!WARNING] 
> É altamente recomendável configurar o upload de logs usando o [Docker](discovery-docker.md) para uma implantação mais flexível.

## <a name="technical-requirements"></a>Requisitos técnicos
- Hipervisor: HyperV ou VMware
- Espaço em disco: 250 GB
- CPU: 2
- RAM: 4 GB 
- Defina o firewall conforme descrito nos [Requisitos de rede](network-requirements.md#log-collector)


## <a name="log-collector-performance"></a>Desempenho do coletor de logs
O coletor de logs pode lidar com êxito com a capacidade de logs de até 50 GB por hora.
Os principais gargalos no processo de coleta de logs são:
- Largura de banda da rede: a largura de banda da rede determina a velocidade de upload do log.
- Desempenho de E/S da máquina virtual alocada pela sua equipe de TI: determina a velocidade na qual os logs são gravados no disco do coletor de logs.
O coletor de logs tem um mecanismo de segurança interno que monitora a taxa na qual os logs chegam e a compara à taxa de upload. Em casos de congestionamento, o coletor de logs começa a remover os arquivos de log. Se sua configuração geralmente excede 50 GB por hora, é recomendável dividir o tráfego entre vários coletores de logs.

## <a name="set-up-and-configuration"></a>Instalação e configuração  
  
### <a name="step-1--web-portal-configuration-define-data-sources-and-link-them-to-a-log-collector"></a>Etapa 1 — Configuração do portal da Web: definir fontes de dados e vinculá-las a um coletor de logs  
  
1. Acesse a página de configuração de upload automatizado:  
   No portal do Cloud App Security, clique no ícone de configurações ![ícone de configurações](./media/settings-icon.png "ícone de configurações"), antes de **Coletores de log**.  
  
2. Para cada firewall ou proxy do qual você deseja carregar logs, crie uma fonte de dados correspondente:  
  
   a.  Clique em **Adicionar fonte de dados**.  
  
   b.  Atribua o **Nome** do proxy ou firewall.  
  
   c.  Selecione o dispositivo na lista **Fonte**. Se você selecionar **Formato de log personalizado** para trabalhar com um dispositivo de rede que não esteja listado, veja [Trabalhando com o analisador de log personalizado](custom-log-parser.md) para obter instruções de configuração.
  
   d.  Compare seu log com o exemplo do formato de log esperado. Se seu formato de arquivo de log não corresponder a esse exemplo, você deverá adicionar sua fonte de dados como **Outro**.  
  
   e.  Defina o **Tipo de receptor** como **FTP** ou **Syslog**. Para **Syslog**, escolha **UDP** ou **TCP**.  
  
   f.  Repita esse processo para cada firewall e proxy cujos logs podem ser usados para detectar o tráfego na rede.  
  
3. Vá para a guia **Coletores de logs** na parte superior.  
  
   a.  Clique em **Adicionar coletor de logs**.  
  
   b.  Atribua um **nome** ao coletor de logs.  
  
   c.  Selecione todas as **Fontes de dados** que quer conectar ao coletor e clique em **Atualizar** para salvar a configuração e gerar um token de acesso.  
   ![fontes de dados de descoberta](./media/discovery-data-sources.png)
  
   > [!NOTE] 
   > - Um único coletor de logs pode lidar com várias fontes de dados.
   > - Copie o conteúdo da tela, pois você o usará ao configurar o Coletor de Logs para se comunicar com o Cloud App Security. Se você selecionou Syslog, essa informação incluirá informações sobre qual porta o ouvinte do Syslog está escutando.
4. Se você aceitar os [termos de licença de usuário final](https://go.microsoft.com/fwlink/?linkid=862492), **baixe** uma nova máquina virtual coletora de logs clicando em Hyper-V ou VMWare. Em seguida, descompacte o arquivo usando a senha que você recebeu no portal.  
  
### <a name="step-2--on-premises-deployment-of-the-virtual-machine-and-network-configuration"></a>Etapa 2 — Implantação da máquina virtual no local e configuração de rede   

> [!NOTE] 
> As etapas a seguir descrevem a implantação no Hyper-V. As etapas de implantação do hipervisor da VM são ligeiramente diferentes.  

1. Abra o Gerenciador do Hyper-V.  
  
2. Selecione **Novo**, **Máquina Virtual** e clique em **Próximo**.  
   ![máquina virtual do Hiper-V de descoberta](./media/discovery-hyperv-virtual-machine.png "máquina virtual do Hiper-V de descoberta")  
  
3. Forneça um **Nome** para a nova máquina virtual, por exemplo, CloudAppSecurityLogCollector01 e clique em **Próximo**.  
  
4. Selecione **Geração 1** e clique em **Próximo**.  
  
5. Altere a **Memória de inicialização** para **4096 MB**.  
        
6. Marque **Use Dynamic Memory (Usar Memória Dinâmica)** para essa máquina virtual e clique em **Próximo**.  
  
7. Se estiver disponível, escolha a rede **Conexão** e clique em **Próximo**.  
  
8. Escolha **Usar um disco rígido virtual existente** e selecione o arquivo .**vhd** que foi incluído no arquivo Zip que você baixou.  
  
9. Clique em **Avançar** e clique em **Concluir**.  
   A máquina é adicionada ao seu ambiente do Hyper-V.  
  
10. Clique na máquina virtual na tabela **Máquinas Virtuais** e clique em **Iniciar**.   
  
11. Conecte-se à máquina virtual do Coletor de Logs para ver se há um endereço DHCP atribuído a ela: clique na máquina virtual e selecione **Conectar**. Você deve ver o prompt de logon. Se você encontrar um endereço IP, poderá conectar-se à máquina virtual usando uma ferramenta SSH/terminal.  Se você não encontrar um endereço IP, faça logon usando as ferramentas de conexão do Hyper-V/VMWare com as credenciais que foram copiadas quando você criou o Coletor de Logs anteriormente. Você pode alterar a senha e configurar a máquina virtual usando o utilitário de configuração de rede executando o seguinte comando:
    ```
    sudo network_config
    ```
    > [!NOTE]
    > A máquina virtual é pré-configurada para obter um endereço IP de um servidor DHCP. Se precisar configurar endereços IP estáticos, gateway padrão, nome do host, servidores DNS e NTPS, você poderá usar o utilitário **network_config** ou realizar alterações manualmente.


Neste ponto, seu coletor de logs deve estar conectado à rede e deverá poder alcançar o portal do Cloud App Security.  

### <a name="step-3--on-premises-configuration-of-the-log-collection"></a>Etapa 3 — Configuração local da coleção de logs 
Na primeira vez que você fizer logon no coletor de logs e importar a configuração do coletor de logs no portal, da seguinte maneira. 

1.  Faça logon no coletor de logs via SSH usando as credenciais de administrador interativo fornecidas no portal. Se esse for o primeiro logon no console, você precisará alterar a senha e o logon novamente após a alteração da senha. Se você estiver usando uma sessão de terminal, poderá ser necessário reiniciar a sessão de terminal. )
2.  Execute o utilitário de configuração do coletor com o token de acesso fornecido quando você criou o coletor de logs.```sudo collector_config <access token> ```
3. Insira o domínio do console, por exemplo: ```contoso.portal.cloudappsecurity.com``` Isso está disponível na URL que você vê depois de fazer logon no portal do Cloud App Security. 

4. Insira o nome do coletor de logs que quer configurar, por exemplo: **CloudAppSecurityLogCollector01** ou **NewYork** da imagem anterior.

5.  Importe a configuração do coletor de logs do portal, da seguinte maneira:  
  
      a.  Faça logon no coletor de logs via SSH usando as credenciais de administrador interativo fornecidas no portal.  
  
      b.  Execute o utilitário de configuração do coletor com o token de acesso fornecido no comando ```sudo collector_config \<access token>```  
     
      c.  Insira seu domínio de console, por exemplo: ``` contoso.portal.cloudappsecurity.com ```
  
      d. Insira o nome do coletor de logs que deseja configurar, por exemplo:``` CloudAppSecurityLogCollector01  ```

### <a name="step-4---on-premises-configuration-of-your-network-appliances"></a>Etapa 4 — Configuração local de seus dispositivos de rede

Configure seus proxies e firewalls de rede para periodicamente exportar logs para a porta de Syslog dedicada do diretório de FTP acordo com as instruções na caixa de diálogo, por exemplo:  
  
     `London Zscaler - Destination path: 614`  
  
     BlueCoat_HQ - Destination path: \<<machine_name>>\BlueCoat_HQ\  
  
### <a name="step-5---verify-the-successful-deployment-in-the-cloud-app-security-portal"></a>Etapa 5 — Verificar a implantação bem-sucedida no portal do Cloud App Security

Verifique o status do coletor na tabela **Coletor de logs** e verifique se o status é **Conectado**. Se for **Criado**, talvez a conexão do coletor de logs e a análise não tenham sido concluídos.

![status do coletor de log](./media/log-collector-status.png)

Acesse o log Governança e verifique se os logs estão sendo carregados periodicamente no portal.  
  
Se você encontrar problemas durante a implantação, confira [Solucionando problemas de Cloud Discovery](troubleshooting-cloud-discovery.md).

### <a name="optional---create-custom-continuous-reports"></a>Opcional – Criar relatórios contínuos personalizados

Após ter verificado que os logs estão sendo carregados no Cloud App Security e os relatórios sendo gerados, você pode criar relatórios personalizados. Agora você pode criar relatórios de descoberta personalizados com base em grupos de usuários do Azure Active Directory. Por exemplo, se você quiser ver o uso de nuvem de seu departamento de marketing, será possível importar o grupo de marketing usando o recurso importar grupo de usuários e, em seguida, criar um relatório personalizado para este grupo. Você também pode personalizar um relatório com base na marca do endereço IP ou intervalos de endereços IP.

1. No portal do Cloud App Security, sob a engrenagem de configurações, selecione **Configurações do Cloud Discovery** e, em seguida, selecione **Gerenciar relatórios contínuos**. 
2. Clique no botão **Criar relatório** e preencha os campos.
3. Em **Filtros**, você pode filtrar os dados de acordo com a fonte de dados, por [grupo de usuários importados](user-groups.md) ou por [marcas e intervalos de endereços IP](ip-tags.md). 

> [!NOTE]
> Todos os relatórios personalizados são limitados a no máximo 1 GB de dados não compactados. Se houver mais de 1 GB de dados, o primeiro GB de dados será exportado para o relatório.

![Relatório contínuo personalizado](./media/custom-continuous-report.png)

## <a name="see-also"></a>Consulte Também  
[Trabalhando com os dados do Cloud Discovery](working-with-cloud-discovery-data.md)   

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
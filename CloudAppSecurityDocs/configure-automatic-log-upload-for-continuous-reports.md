---
title: "Configurar o upload de log automático para relatórios contínuos | Microsoft Docs"
description: "Este tópico fornece informações sobre como fazer upload dos logs para criar relatórios automáticos do Cloud Discovery."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: c4123272-4111-4445-b6bd-2a1efd3e0c5c
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed4ea71b24767d3602d40894d1cbac7447bcd8a2
ms.openlocfilehash: 9672336d69f19875d160eb414bf3ca2c525692e1


---

# <a name="configure-automatic-log-upload-for-continuous-reports"></a>Configurar upload de log automático para relatórios contínuos
Antes de configurar a coleta de arquivos de log automática, verifique se o log corresponde ao tipo de log esperado para garantir que o Cloud App Security possa analisar seu arquivo específico. 

## <a name="technical-requirements"></a>Requisitos técnicos
- Hipervisor: HyperV ou VMware
- Espaço em disco: 250 GB
- CPU: 2
- RAM: 4 GB 
- Configurações de firewall: 
- Permitir que o coletor de logs receba o tráfego FTP e Syslog de entrada
- Permitir que o coletor de logs inicie o tráfego de saída para o portal (por exemplo, contoso.cloudappsecurity.com) na porta 443

  
## <a name="set-up-automatic-log-file-collection"></a>Configurar a coleta automática de arquivos de log  
  
Os coletores de log permitem que você automatize facilmente o upload de logs da sua rede. O coletor de log é executado em sua rede e recebe logs por Syslog ou FTP. Cada log é automaticamente processado, compactado e transmitido para o portal. Logs de FTP são carregados para o Cloud App Security depois da conclusão da transferência do arquivo por FTP para o Coletor de Logs e para Syslogs. O Coletor de Logs grava os logs recebidos para o disco a cada 20 minutos e carrega o arquivo para o Cloud App Security.  A máquina virtual do coletor de logs está disponível para hipervisor Hyper-V (formato VHD) e VMware (formato OVF) e requer 250 GB de espaço em disco, 2 CPUs e 4 GB de RAM. 
     
  
     The log collector VHD image can be downloaded and run on Azure servers.  
  
2.  Acesse a página de configuração de upload automatizado:  
    No portal do Cloud App Security, clique no ícone de configurações ![ícone de configurações](./media/settings-icon.png "settings icon"), seguido pelas **Configurações de Cloud Discovery** e selecione a guia **Carregar logs automaticamente**.  
  
3.  Para cada firewall ou proxy do qual você deseja carregar logs, crie uma fonte de dados correspondente:  
  
    1.  Clique em **Adicionar fonte de dados**.  
  
    2.  Atribua o **Nome** do proxy ou firewall.  
  
    3.  Selecione o dispositivo na lista **Fonte**.  
  
    4.  Compare seu log com o exemplo do formato de log esperado. Se seu formato de arquivo de log não corresponder a esse exemplo, você deverá adicionar sua fonte de dados como **Outro**.  
  
    5.  Defina o **Tipo de receptor** como **FTP** ou **Syslog**.  
  
         Para **Syslog**, escolha **UDP** ou **TCP**.  
  
    6.  Repita esse processo para cada firewall e proxy cujos logs podem ser usados para detectar o tráfego na rede.  
  
4.  Vá para a guia **Coletores de logs** na parte superior.  
  
    1.  Clique em **Adicionar coletor de logs**.  
  
    2.  Atribua um **nome** ao coletor de logs.  
  
    3.  Selecione todas as **Fontes de dados** que deseja conectar ao coletor e clique em **Atualizar**.  
  
         > [!NOTE] 
       > Copie o conteúdo da tela, pois você precisará das informações ao configurar o Coletor de Logs para se comunicar com o Cloud App Security. Se você selecionou Syslog, essa informação incluirá informações sobre qual porta o ouvinte do Syslog está escutando.
         
![Origens dos dados de descoberta](./media/discovery-data-sources.png)
> [!NOTE] 
         > Um único coletor de logs pode lidar com várias fontes de dados.
  
4.  **Baixe** uma nova máquina virtual do coletor de logs clicando no Hyper-V ou VMWare e descompacte o arquivo usando a senha que você recebeu no portal.  
  
## <a name="set-up-your-virtual-machine-in-hyperv"></a>Configurar sua máquina virtual no Hyper-V:  
  
1.  Abra o Gerenciador do Hyper-V.  
  
2.  Selecione **Novo**, **Máquina Virtual** e clique em **Próximo**.  
  
             ![discovery hyperv virtual machine](./media/discovery-hyperv-virtual-machine.png "discovery hyperv virtual machine")  
  
3.  Forneça um **Nome** para a nova máquina virtual, por exemplo, CloudAppSecurityLogCollector01 e clique em **Próximo**.  
  
4.  Selecione **Geração 1** e clique em **Próximo**.  
  
5.  Altere a **Memória de inicialização** para **4096 MB**.  
        
6. Marque **Use Dynamic Memory (Usar Memória Dinâmica)** para essa máquina virtual e clique em **Próximo**.  
  
7.  Se estiver disponível, escolha a rede **Conexão** e clique em **Próximo**.  
  
8.  Escolha **Usar um disco rígido virtual existente** e selecione o arquivo .**vhd** que foi incluído no arquivo Zip que você baixou.  
  
9.  Clique em **Avançar** e clique em **Concluir**.  
  
             The machine will be added to your Hyper-V environment.  
  
9. Clique na máquina virtual na tabela **Máquinas Virtuais** e clique em **Iniciar**.   
  
10. Conecte-se à máquina virtual do Coletor de Logs para ver se há um endereço DHCP atribuído a ela: clique na máquina virtual e selecione **Conectar**. Você deve ver o prompt de logon. Se você encontrar um endereço IP, poderá conectar-se à máquina virtual usando uma ferramenta SSH/terminal.  Se você não encontrar um endereço IP, faça logon usando as ferramentas de conexão do Hyper-V/VMWare com as credenciais que foram copiadas quando você criou o Coletor de Logs acima. Você pode alterar a senha e configurar a máquina virtual executando o seguinte comando
```
sudo network_config
```
> [!NOTE]
> A máquina virtual é pré-configurada para obter um endereço IP de um servidor DHCP. Se precisar configurar endereços IP estáticos, gateway padrão, nome do host, servidores DNS e NTPS, você poderá usar o utilitário **network_config** ou realizar alterações manualmente.


Neste ponto, seu coletor de logs deve estar conectado à rede e deverá poder alcançar o portal do Cloud App Security.  

## <a name="log-in-and-import"></a>Entrar e importar 
Na primeira vez que você fizer logon no coletor de logs e importar a configuração do coletor de logs no portal, da seguinte maneira. 

1.  Faça logon no coletor de logs via SSH usando as credenciais de administrador interativo fornecidas no portal. Se esse for o primeiro logon no console, você precisará alterar a senha e o logon novamente após a alteração da senha. Se você estiver usando uma sessão de terminal, poderá ser necessário reiniciar a sessão de terminal. )
2.  Execute o utilitário de configuração do coletor com o token de acesso fornecido quando você criou o coletor de logs. 

```
sudo collector_config <access token>
```

3. Insira seu domínio de console, por exemplo:

```
contoso.portal.cloudappsecurity.com
```

Isso está disponível da URL que você vê depois de fazer logon no portal do Cloud App Security. 
 

4. Insira o nome do coletor de logs que deseja configurar, por exemplo:

**CloudAppSecurityLogCollector01** ou **NewYork** na imagem acima.
 
8.  Importe a configuração do coletor de logs do portal, da seguinte maneira:  
  
      1.  Faça logon no coletor de logs via SSH usando as credenciais de administrador interativo fornecidas no portal.  
  
       2.  Execute o utilitário de configuração do coletor com o token de acesso fornecido no comando **sudo collector_config \<access token>**  
  
             Insira seu domínio de console, por exemplo:  
  
             **contoso.portal.cloudappsecurity.com ** 
  
             Insira o nome do coletor de logs que deseja configurar, por exemplo:  
  
             **CloudAppSecurityLogCollector01**  
  
5.  Configure seus proxies e firewalls de rede para periodicamente exportar logs para a porta de Syslog dedicada do diretório de FTP acordo com as instruções na caixa de diálogo, por exemplo:  
  
     `London Zscaler - Destination path: 614`  
  
     `SF Blue Coat - Destination path: \\CloudAppSecurityCollector01\BlueCoat\`  
  
6.  Use o log de governança para verificar se os logs estão sendo carregados periodicamente no portal.  
  
## <a name="log-collector-performance"></a>Desempenho do coletor de logs
O coletor de logs pode lidar com êxito com a capacidade de logs de até 50 GB por hora.

Os principais afunilamentos no processo de coleta de logs são:
* Largura de banda da rede: a largura de banda da rede determina a velocidade de upload do log.
* Desempenho de E/S da máquina virtual alocada pela sua equipe de TI: determina a velocidade na qual os logs são gravados no disco do coletor de logs.

O coletor de logs tem um mecanismo de segurança interno que monitora a taxa na qual os logs chegam e a compara à taxa de upload. Em casos de congestionamento, o coletor de logs começa a remover os arquivos de log. Se sua configuração geralmente excede 50 GB por hora, é recomendável dividir o tráfego entre vários coletores de logs.


<!--HONumber=Oct16_HO4-->



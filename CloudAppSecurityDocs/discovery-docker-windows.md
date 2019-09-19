---
title: Distribuir relatórios contínuos do Cloud App Security usando um Docker no Windows | Microsoft Docs
description: Este artigo descreve o processo de configuração de upload automático de log para relatórios contínuos no Cloud App Security usando um Docker no Windows em um servidor local.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 8/7/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: ff73a393-da43-4954-8b02-38d2a48d39b3
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 724ff32cbdf4d3d81d60ac1359b5c07fe22bb6e1
ms.sourcegitcommit: 8a49c166424fea83853b0a6895212367526abe78
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71084752"
---
# <a name="docker-on-windows-on-premises"></a>Docker no Windows local

*Aplica-se a: Microsoft Cloud App Security*

Você pode configurar o upload automático de log para relatórios contínuos no Cloud App Security usando um Docker no Windows.

## <a name="prerequisites"></a>Pré-requisitos

- Sistema operacional: **Windows 10** Fall Creators Update e Windows Server **versão 1709 ou superior**

- Espaço em disco: 250 GB

- CPUS 2

- RAM: 4 GB

- Defina o firewall conforme descrito nos [Requisitos de rede](network-requirements.md#log-collector)

- A virtualização no sistema operacional deve ser habilitada com o Hyper-V

> [!IMPORTANT]
> Um usuário deve estar conectado para que o Docker colete logs. Recomendamos que o usuário do Docker se desconecte sem sair.

## <a name="log-collector-performance"></a>Desempenho do coletor de logs

O coletor de logs pode lidar com êxito com a capacidade de logs de até 50 GB por hora. Os principais gargalos no processo de coleta de logs são:

- Largura de banda da rede – a largura de banda da rede determina a velocidade de upload do log.

- Desempenho de E/S da máquina virtual – determina a velocidade em que os logs são gravados no disco do coletor de logs. O coletor de logs tem um mecanismo de segurança interno que monitora a taxa na qual os logs chegam e a compara à taxa de upload. Em casos de congestionamento, o coletor de logs começa a remover os arquivos de log. Se a configuração geralmente excede 50 GB por hora, recomendamos que você divida o tráfego entre vários coletores de logs.

## <a name="set-up-and-configuration"></a>Instalação e configuração  

### <a name="step-1--web-portal-configuration-define-data-sources-and-link-them-to-a-log-collector"></a>Etapa 1 – Configuração do portal da Web: Definir fontes de dados e vinculá-las a um coletor de logs

1. Acesse a página de configurações **Upload automático de logs**. 

     a. No portal do Cloud App Security, clique no ícone de configurações antes de **Coletores de log**.

      ![ícone de configurações](./media/settings-icon.png)

2. Para cada firewall ou proxy do qual você deseja fazer upload de logs, crie uma fonte de dados correspondente.

     a. Clique em **Adicionar fonte de dados**.

      ![Adicionar uma fonte de dados](./media/add-data-source.png)

     b. Atribua o **Nome** do proxy ou firewall.

      ![ubuntu1](./media/ubuntu1.png)

     c. Selecione o dispositivo na lista **Fonte**. Se você selecionar **Formato de log personalizado** para trabalhar com um dispositivo de rede que não esteja listado, confira [Trabalhando com o analisador de log personalizado](custom-log-parser.md) para obter instruções de configuração.

     d. Compare seu log com o exemplo do formato de log esperado. Se o formato de arquivo de log não corresponder a este exemplo, adicione sua fonte de dados como **Outros**.

     e. Defina o **Tipo de destinatário** como **FTP**, **FTPS**, **Syslog – UDP** ou **Syslog – TCP** ou **Syslog – TLS**.

     >[!NOTE]
     >A integração com protocolos de transferência segura (FTPS e Syslog – TLS) geralmente requer seu firewall/proxy ou configurações adicionais.

      f. Repita esse processo para cada firewall e proxy cujos logs podem ser usados para detectar o tráfego na rede. É recomendável configurar uma fonte de dados dedicada por dispositivo de rede para permitir que você:
     - Monitore o status de cada dispositivo separadamente, para fins de investigação.
     - Explore o Shadow IT Discovery por dispositivo, se cada dispositivo for usado por um segmento de usuários diferente.

3. Vá para a guia **Coletores de logs** na parte superior.

   a. Clique em **Adicionar coletor de logs**.

   b. Atribua um **nome** ao coletor de logs.

   c. Insira o **Endereço IP de host** do computador que você usará para implantar o Docker. O endereço IP do host pode ser substituído pelo nome do computador, caso haja um servidor DNS (ou equivalente) que resolverá o nome do host.

   d. Selecione todas as **Fontes de dados** que quer conectar ao coletor e clique em **Atualizar** para salvar a configuração e ver as próximas etapas de implantação.

   ![ubuntu2](./media/ubuntu2.png)

   > [!NOTE]
   > - Um único coletor de logs pode lidar com várias fontes de dados.
   > - Copie o conteúdo da tela, pois você precisará das informações ao configurar o Coletor de Logs para se comunicar com o Cloud App Security. Se você selecionou Syslog, essa informação incluirá informações sobre qual porta o ouvinte do Syslog está escutando.

4. Mais informações sobre a implantação serão exibidas. **Copiar** o comando de execução na caixa de diálogo. Use o ícone Copiar para área de transferência. ![ícone da área de transferência Copiar para](./media/copy-icon.png). Você precisará dele mais tarde.

5. **Exporte** a configuração de fonte de dados esperada. Essa configuração descreve como você deve definir a exportação de log em seus dispositivos.

   ![Crie o coletor de logs](./media/windows7.png)

### <a name="step-2--on-premises-deployment-of-your-machine"></a>Etapa 2 – implantação local de seu computador
As etapas a seguir descrevem a implantação no Windows. As etapas de implantação para outras plataformas são ligeiramente diferentes.

1. Abra um terminal do PowerShell como administrador em seu computador Windows.

2. Use o comando a seguir para baixar o instalador do Docker do Windows:<br>
 `Invoke-WebRequest https://adaprodconsole.blob.core.windows.net/public-files/LogCollectorInstaller.ps1 -OutFile (Join-Path $Env:Temp LogCollectorInstaller.ps1)`
<br>Se você deseja validar se o instalador é assinado pela Microsoft, confira [Validate installer signature](#validate-signature) (Validar assinatura do instalador).

3. Para habilitar a execução de script do PowerShell, execute `Set-ExecutionPolicy RemoteSigned`.

4. Execute: `& (Join-Path $Env:Temp LogCollectorInstaller.ps1)`<br>
Isso instala o cliente do Docker em seu computador. Durante a instalação do contêiner do coletor de logs, o computador será reiniciado duas vezes e você precisará fazer logon novamente. **Verifique se o cliente do Docker está definido para usar contêineres do Linux.**

5. Após cada reinicialização, no diretório em que você salvou o instalador, execute novamente: `& (Join-Path $Env:Temp LogCollectorInstaller.ps1)`<br>  

6. Antes da conclusão da instalação, você precisará colar o comando de execução que copiou anteriormente.

7. Implante a imagem do coletor no computador de hospedagem importando a configuração do coletor. Importe a configuração copiando o comando de execução gerado no portal. Caso precise configurar um proxy, adicione o endereço IP do proxy e o número da porta. Por exemplo, se os detalhes de proxy são 192.168.10.1:8080, seu comando de execução atualizado é:

           (echo db3a7c73eb7e91a0db53566c50bab7ed3a755607d90bb348c875825a7d1b2fce) | docker run --name MyLogCollector -p 21:21 -p 20000-20099:20000-20099 -e "PUBLICIP='192.168.1.1'" -e "PROXY=192.168.10.1:8080" -e "CONSOLE=mod244533.us.portal.cloudappsecurity.com" -e "COLLECTOR=MyLogCollector" --security-opt apparmor:unconfined --cap-add=SYS_ADMIN --restart unless-stopped -a stdin -i microsoft/caslogcollector starter

   ![Crie o coletor de logs](./media/windows7.png)
8. Verifique se o coletor está sendo executado corretamente com o seguinte comando: `docker logs <collector_name>`

Você deverá ver a mensagem: **Concluído com êxito!**

  ![ubuntu8](./media/ubuntu8.png)

### <a name="step-3---on-premises-configuration-of-your-network-appliances"></a>Etapa 3 — Configuração local de seus dispositivos de rede

Configure os proxies e os firewalls de rede para periodicamente exportar logs para a porta do Syslog dedicada do diretório de FTP de acordo com as instruções na caixa de diálogo. Por exemplo:

    BlueCoat_HQ - Destination path: \<<machine_name>>\BlueCoat_HQ\

### <a name="step-4---verify-the-successful-deployment-in-the-cloud-app-security-portal"></a>Etapa 4 — Verificar a implantação bem-sucedida no portal do Cloud App Security

Verifique o status do coletor na tabela **Coletor de logs** e verifique se o status é **Conectado**. Se for **Criado**, talvez a conexão do coletor de logs e a análise não tenham sido concluídas.

 ![ubuntu9](./media/ubuntu9.png)

Você também pode ir para o **log de governança** e verificar se que os logs estão sendo carregados periodicamente no portal.

Se houver problemas durante a implantação, confira [Solução de problemas do Cloud Discovery](troubleshooting-cloud-discovery.md).

### Opcional – criar relatórios contínuos personalizados <a name="continuous-reports"></a>

Verifique se os logs estão sendo carregados no Cloud App Security e se os relatórios são gerados. Após a verificação, crie relatórios personalizados. Crie relatórios de descoberta personalizados com base em grupos de usuários do Azure Active Directory. Por exemplo, caso deseje ver o uso de nuvem de seu departamento de marketing, importe o grupo de marketing usando o recurso Importar grupo de usuários. Em seguida, crie um relatório personalizado para esse grupo. Você também pode personalizar um relatório com base na marca do endereço IP ou intervalos de endereços IP.

1. No portal do Cloud App Security, na engrenagem Configurações, selecione Configurações do Cloud Discovery e, em seguida, **Relatórios contínuos**. 
2. Clique no botão **Criar relatório** e preencha os campos.
3. Em **Filtros**, você pode filtrar os dados de acordo com a fonte de dados, por [grupo de usuários importados](user-groups.md) ou por [marcas e intervalos de endereços IP](ip-tags.md). 

![Relatório contínuo personalizado](./media/custom-continuous-report.png)

### Opcional – Validar a assinatura do instalador <a name="validate-signature"></a>

Para verificar se o instalador do Docker é assinado pela Microsoft:
1. Clique com o botão direito do mouse no arquivo e selecione **Propriedades**.
2. Clique em **Assinaturas Digitais** e verifique se a mensagem **Esta assinatura digital está correta** é exibida.  
3. Verifique se **Microsoft Corporation** está listada como a única entrada em **Nome do signatário**.  

![Assinatura digital válida](./media/digital-signature-successful.png)

Se a assinatura digital não for válida, ela indicará **Esta assinatura digital não é válida**:

![Assinatura digital não válida](./media/digital-signature-unsuccessful.png)

## <a name="next-steps"></a>Próximas etapas

[Configuração de FTP do coletor de logs](log-collector-ftp.md)

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/)

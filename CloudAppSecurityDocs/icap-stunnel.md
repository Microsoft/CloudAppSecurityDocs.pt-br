---
title: "Integração de DLP externa do Cloud App Security por meio de ICAP seguro | Microsoft Docs"
description: "Este tópico fornece as etapas necessárias para configurar a conexão ICAP no Cloud App Security e a instalação do stunnel."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 7/23/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 9656f6c6-7dd4-4c4c-a0eb-f22afce78071
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: b3c9181bf1d56fe515d3e1356d38d631fee2cac5
ms.sourcegitcommit: c6f917ed0fc2329a72b1e5cbb8ccd5e4832c8695
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2017
---
# <a name="external-dlp-integration"></a>Integração de DLP externa

> [!NOTE] 
> Esse recurso está em versão prévia. Fale com <Cloud App Securitypreview@microsoft.com> para experimentar este recurso no locatário.

O Cloud App Security pode integrar soluções DLP existentes para estender esses controles para a nuvem preservando uma política consistente e unificada entre locais e atividades na nuvem. A plataforma exporta interfaces fáceis de usar, incluindo API REST e ICAP, habilitando a integração com sistemas de classificação de conteúdo, como Symantec Data Loss Prevention (antigo Vontu Data Loss Prevention) ou Forcepoint DLP. 

A integração é obtida utilizando o protocolo ICAP padrão, um protocolo http como descrito em [RFC 3507](https://tools.ietf.org/html/rfc3507). Para proteger ICAP para transmissão de dados, é necessário configurar um túnel seguro SSL (stunnel) entre a solução DLP e o Cloud App Security. A configuração de stunnel fornece funcionalidade de criptografia TLS para seus dados durante o tráfego entre o servidor DLP e Cloud App Security. 

Este guia fornece as etapas necessárias para configurar a conexão ICAP no Cloud App Security e a instalação do stunnel para proteger a conexão passando por ele.

## <a name="architecture"></a>Arquitetura
O Cloud App Security examina o ambiente de nuvem e, com base em seu arquivo de configuração de política, decide se deve verificar o arquivo usando o mecanismo DLP interno ou DLP externo. Se a verificação DLP externa é aplicada, o arquivo é enviado por meio do túnel seguro para o ambiente do cliente no qual ele é transmitido para o dispositivo ICAP para o veredicto DLP: permitido/bloqueado. As respostas são enviadas ao Cloud App Security pelo stunnel, onde ele é usado pela política para determinar ações subsequentes, como notificações, quarentena e compartilhamento de controle.

![Arquitetura do stunnel](./media/icap-architecture-stunnel.png)

Como o Cloud App Security é executado no Azure, uma implantação no Azure resultará em desempenho aprimorado. No entanto, há suporte para outras opções, incluindo implantações de Nuvem e Locais. Implantação em outros ambientes pode resultar em degradação do desempenho devido à maior latência e taxa de transferência menor. O servidor ICAP e o stunnel devem ser implantados juntos na mesma rede para garantir que o tráfego seja criptografado.

## <a name="prerequisites"></a>Pré-requisitos
Para o Cloud App Security enviar dados por meio de seu stunnel para seu servidor ICAP, abra o firewall de DMZ para os endereços IP externos usados pelo Cloud App Security com um número da porta de origem dinâmico. 

1.  Endereços de origem: consulte [Conectar aplicativos, em Pré-requisitos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md#prerequisites)
2.  Porta TCP de origem: dinâmico
3.  Endereços de destino: um ou dois endereços IP do stunnel conectado ao servidor ICAP externo que você vai configurar nas próximas etapas
4.  Porta TCP de destino: conforme definido em sua rede

## <a name="step-1--set-up-icap-server"></a>ETAPA 1: configurar o servidor ICAP

Configure um servidor ICAP, anote o número da porta e certifique-se de que você defina **Modo** como **Bloqueio**. O modo de bloqueio define o servidor ICAP para retransmitir o veredicto de classificação de volta ao Cloud App Security.

Consulte a documentação do produto DLP externa para obter instruções sobre como fazer isso. Por exemplo, consulte [Apêndice A: instalação do servidor Forcepoint ICAP](#forcepoint).

## <a name="step-2--set-up-your-stunnel-server"></a>ETAPA 2: configurar o servidor de stunnel 

Nesta etapa você configurará o stunnel conectado ao seu servidor ICAP. 

>[!NOTE]
> Embora altamente recomendada, essa etapa é opcional e pode ser ignorada em cargas de trabalho de teste. 

### <a name="install-stunnel-on-a-server"></a>Instalar stunnel em um servidor

**Pré-requisitos**

- **Um servidor** – um Windows Server ou um servidor do Linux com base em uma distribuição principal.

Consulte o [site do stunnel](https://www.stunnel.org/index.html) para obter detalhes sobre os tipos de servidores que oferecem suporte à instalação de stunnel. Se você estiver usando o Linux, você poderá usar o gerenciador de distribuição do Linux para instalá-lo.

#### <a name="install-stunnel-on-windows"></a>Instalar stunnel em no Windows

1. [Baixe a instalação mais recente do Windows Server](https://www.stunnel.org/downloads.html) (isso deve funcionar em qualquer edição do Windows Server recente).
(instalação padrão)

2. Durante a instalação, não crie um novo certificado autoassinado; você criará um certificado em uma etapa posterior.

3. Clique em **Iniciar servidor após a instalação**.

4. Crie um certificado de uma das seguintes maneiras:

   -    Use o servidor de gerenciamento de certificado para criar um certificado SSL no servidor ICAP e, em seguida, copie as chaves para o servidor preparado para a instalação do stunnel.
   -    Ou, no servidor stunnel, use os seguintes comandos do OpenSSL para gerar uma chave privada e um certificado autoassinado. Substitua essas variáveis:
       -    **key.pem** pelo nome da sua chave privada
       -    **cert.pem** pelo nome do seu certificado
       -    **stunnel-key** pelo nome da chave criada recentemente

5. No seu caminho de instalação de stunnel, abra o diretório de configuração. Por padrão, ele é: c:\Arquivos de programas (x86)\stunnel\config\
6. Execute linha de comando com permissões de administrador:     `..\bin\openssl.exe genrsa -out ey.pem 2048 `
      
     ` ..\bin\openssl.exe  req -new -x509 -config ".\openssl.cnf" -key key.pem -out .\cert.pem -days 1095`

8. Concatene cert.pem e key.pem e salve-os no arquivo: `type cert.pem key.pem >> stunnel-key.pem`

9. [Baixe a chave pública](https://adaprodconsole.blob.core.windows.net/icap/publicCert.pem) e salve-a nesse local **C:\Arquivos de programas (x86)\stunnel\config\CAfile.pem**.

10. Adicione as regras a seguir para abrir a porta no firewall do Windows:

        rem Open TCP Port 11344 inbound and outbound
        netsh advfirewall firewall add rule name="Secure ICAP TCP Port 11344" dir=in action=allow protocol=TCP localport=11344
        netsh advfirewall firewall add rule name="Secure ICAP TCP Port 11344" dir=out action=allow protocol=TCP localport=11344

11. Execute: `c:\Program Files (x86)\stunnel\bin\stunnel.exe` para abrir o aplicativo stunnel. 

12. Clique em **Configuração** e em **Editar configuração**.

   ![Editar configuração do Windows Server](./media/stunnel-windows.png)
 
13. Abra o arquivo e cole as seguintes linhas de configuração de servidor, em que **IP do Servidor de DLP** é o endereço IP do seu servidor ICAP, **stunnel-key** é a chave que você criou na etapa anterior e **CAfile** é o certificado público do cliente stunnel do Cloud App Security. Além disso, exclua qualquer texto de exemplo que esteja em vigor (o exemplo exibe o texto Gmail) e copie o seguinte conteúdo no arquivo:

        [microsoft-Cloud App Security]
        accept = 0.0.0.0:11344
        connect = **ICAP Server IP**:1344
        cert = C:\Program Files (x86)\stunnel\config\**stunnel-key**.pem
        CAfile = C:\Program Files (x86)\stunnel\config\**CAfile**.pem
        TIMEOUTclose = 0
        client = no
12. Salve o arquivo e, em seguida, clique em **Recarregar configuração**.

13. Para validar que tudo está funcionando conforme o esperado, em um prompt de comando, execute: `netstat -nao  | findstr 11344`
 

#### <a name="install-stunnel-on-ubuntu"></a>Instalar stunnel no Ubuntu

O exemplo a seguir é baseado em uma instalação de servidor do Ubuntu, quando conectado como usuário raiz – para outros servidores, use comandos paralelos. 

No servidor preparado, baixe e instale a versão mais recente do stunnel executando o comando a seguir em seu servidor do Ubuntu que instalará o stunnel e o OpenSSL:

    apt-get update
    apt-get install openssl -y
    apt-get install stunnel4 -y
Verifique se o stunnel está instalado ao executar o comando a seguir de um console. Você deve obter o número de versão e uma lista de opções de configuração:

    stunnel-version

### <a name="generate-certificates"></a>Gerar certificados

O servidor ICAP e o Cloud App Security usam uma chave privada e um certificado público para criptografia de servidor e autenticação no stunnel. Certifique-se de criar a chave privada sem uma frase secreta para que stunnel possa ser executado como um serviço em segundo plano. Além disso, defina as permissões nos arquivos como **legível** para o proprietário do stunnel e como **nenhum** para outras pessoas.

Você pode criar os certificados em uma das seguintes maneiras:
-   Use o servidor de gerenciamento de certificado para criar um certificado SSL no servidor ICAP e, em seguida, copie as chaves para o servidor preparado para a instalação do stunnel. 
-   Ou, no servidor stunnel, use os seguintes comandos do OpenSSL para gerar uma chave privada e um certificado autoassinado. Substitua essas variáveis:
    - **“key.pem”** pelo nome da sua chave privada
    - **“cert.pem”** pelo nome do seu certificado
    - **“stunnel-key”** pelo nome da chave criada recentemente
       
            openssl genrsa -out key.pem 2048
            openssl req -new -x509 -key key.pem -out cert.pem -days 1095
            cat key.pem cert.pem >> /etc/ssl/private/stunnel-key.pem

### <a name="download-the-cloud-app-security-stunnel-client-public-key"></a>Baixe a chave pública do cliente do stunnel do Cloud App Security

Baixe a chave pública deste local: https://adaprodconsole.blob.core.windows.net/icap/publicCert.pem e salve-a neste local **/etc/ssl/certs/CAfile.pem**

### <a name="configure-stunnel"></a>Configurar o stunnel 

A configuração do stunnel é definida no arquivo stunnel.conf.

1. Crie o arquivo stunnel.conf no seguinte diretório: **vim /etc/stunnel/stunnel.conf**

3.  Abra o arquivo e cole as seguintes linhas de configuração de servidor, em que **IP do Servidor de DLP** é o endereço IP do seu servidor ICAP, **stunnel-key** é a chave que você criou na etapa anterior e **CAfile** é o certificado público do cliente stunnel do Cloud App Security:

        [microsoft-Cloud App Security]
        accept = 0.0.0.0:11344
        connect = **ICAP Server IP**:1344
        cert = /etc/ssl/private/**stunnel-key**.pem
        CAfile = /etc/ssl/certs/**CAfile**.pem
        TIMEOUTclose = 1
        client = no
> [!NOTE] 
> Por padrão, o número da porta stunnel é definido como 11344. Você pode alterá-lo para outra porta, se necessário, mas certifique-se de anotar o novo número da porta, você deverá inseri-lo na próxima etapa.

### <a name="update-your-ip-table"></a>Atualizar a tabela IP
Atualize a tabela de endereços IP com a seguinte regra de rota:
   
    iptables -I INPUT -p tcp --dport 11344 -j ACCEPT

Para fazer a atualização para sua tabela IP persistente, use os seguintes comandos:

     sudo apt-get install iptables-persistent
     sudo /sbin/iptables-save > /etc/iptables/rules.v4
 

### <a name="run-stunnel"></a>Executar stunnel
1.  No servidor stunnel, execute o seguinte:

        vim /etc/default/stunnel4

2.  Altere a variável ENABLED para 1:

        ENABLED=1

3.  Reinicie o serviço para que a configuração entrar em vigor:

        /etc/init.d/stunnel4 restart

4.  Execute os seguintes comandos para verificar se o stunnel está funcionando corretamente:

        ps -A | grep stunnel

    e que ele está escutando a porta listada:

        netstat -anp | grep 11344

5. Certifique-se de que a rede na qual o servidor de stunnel foi implantado corresponda os pré-requisitos de rede, como mencionado anteriormente. Isso é necessário para permitir conexões de entrada do Cloud App Security para acessar com êxito o servidor.

Se o processo ainda não está funcionando, consulte o [documentação do stunnel](https://www.stunnel.org/docs.html) para solucionar problemas.


## <a name="step-3--connect-to-cloud-app-security"></a>ETAPA 3: conectar-se ao Cloud App Security

1. No Cloud App Security, em **Configurações**, selecione **Extensões de segurança** e selecione a guia **DLP externo**.

2. Clique no sinal de mais para adicionar uma nova conexão. 

3. No assistente **Adicionar novo DLP externo**, forneça um **Nome de conexão** (por exemplo, conector My Forcepoint), que será usado para identificar o conector.

4. Selecione o **Tipo de conexão**:
    - **Symantec Vontu** – selecione esta opção para usar a integração personalizada para soluções de DLP Vontu
    - **Forcepoint DLP** – selecione esta opção para usar a integração personalizada para soluções de Forcepoint DLP
    - **ICAP Genérico – REQMOD** – para outros dispositivos de DLP que usam [Solicitar modificação](https://tools.ietf.org/html/rfc3507)
    - **ICAP Genérico – RESPMOD** – para outros dispositivos de DLP que usam [Modificação de resposta](https://tools.ietf.org/html/rfc3507)
    ![Conexão ICAP do Cloud App Security](./media/icap-wizard1.png)

4. Procure para selecionar a AC raiz pública do seu stunnel para usar para se conectar ao seu stunnel e, em seguida, clique em **Avançar**.

   > [!NOTE]
   > É altamente recomendável selecionar a caixa **Usar ICAP seguro** para definir um gateway de stunnel criptografado. Se, para fins ou se você não tiver um servidor de stunnel, você poderá desmarcar esta opção para integrar diretamente com o servidor DLP. 

5. Na tela **Configuração do servidor**, forneça o **Endereço IP** e a **Porta** do servidor stunnel que você configurou na Etapa 2. Para fins de balanceamento de carga, você pode configurar o **Endereço IP** e a **Porta** de um servidor adicional. Os endereços IP fornecidos devem ser os endereços IP estáticos externos dos seus servidores.

   ![Conexão ICAP do Cloud App Security](./media/icap-wizard2.png)
6. Clique em **Avançar**. O Cloud App Security testará a conectividade com o servidor configurado. Se você receber um erro, examine as instruções e as configurações de rede. Depois de conectado com êxito, você pode clicar em **Encerrar**.

7. Agora, para direcionar o tráfego para esse servidor DLP externo, quando você cria uma **Política de arquivo**, em **Método de inspeção de conteúdo**, selecione a conexão que você acabou de criar. Leia mais sobre [Criar uma política de arquivo](data-protection-policies.md).


## Apêndice A: instalação do servidor ForcePoint ICAP <a name="forcepoint"></a>

No ForcePoint, defina seu dispositivo usando as seguintes etapas:

1.  Em seu dispositivo DLP, vá para **Implantação** > **Módulos do sistema**. 

    ![Implantação ICAP](./media/icap-system-modules.png)

2.  Na guia **Geral**, verifique se **Servidor ICAP** está **Habilitado** e se a **Porta** padrão está definida como **1344**. Além disso, em **Permitir conexão com este Servidor ICAP pelos endereços IP a seguir**, selecione **Qualquer endereço IP**.
 
    ![Configuração do ICAP](./media/icap-ip-address.png)

3.  Na guia HTTP/HTTPS, certifique-se de definir **Modo** como **bloqueio**.
 
    ![Bloqueio de ICAP](./media/icap-blocking.png)
 

## <a name="appendix-b-symantec-deployment-guide"></a>Apêndice B: Guia de Implantação do Symantec

As versões DLP do Symantec com suporte são as de 11 a 14.6. Conforme mencionamos anteriormente, você deve implantar um servidor de detecção no mesmo datacenter do Microsoft Azure em que reside o locatário do Cloud App Security. O servidor de detecção é sincronizado com o servidor de imposição por meio de um túnel IPSec dedicado. 
 
### <a name="detection-server-installation"></a>Instalação do servidor de detecção 
O servidor de detecção usado pelo Cloud App Security é uma prevenção de rede padrão para servidor Web. Há várias opções de configuração que devem ser alteradas:
1.  Desabilite o **modo de avaliação**:
    1. Em **Sistema** > **Servidores e Detectores**, clique no destino de ICAP. 
    
      ![Destino de ICAP](./media/icap-target.png)
    
    2. Clique em **Configurar**. 
    
      ![Configurar o destino de ICAP](./media/configure-icap-target.png)
    
    3. Desabilite o **modo de avaliação**.
    
      ![desabilitar o modo de avaliação](./media/icap-disable-trial-mode.png)
    
2. Em **ICAP** > **Filtragem de resposta**, altere o valor de **Ignorar respostas menores do que** para 1.

3. Em seguida, adicione "application/*" à lista de **Tipo de Conteúdo de Inspeção**.
     ![tipo de conteúdo de inspeção](./media/icap-inspect-content-type.png)
4. Clique em **Salvar**


### <a name="policy-configuration"></a>Configuração de política
O Cloud App Security tem suporte contínuo para todos os tipos de regra de detecção incluídos no DLP do Symantec, portanto não é necessário alterar as regras existentes. No entanto, há uma alteração de configuração que deve ser aplicada a todas as políticas novas e existentes para habilitar a integração completa. Esta alteração representa a inclusão de uma regra de resposta específica para todas as políticas. Adicione a alteração de configuração ao Vontu:
1.  Vá para **Gerenciar** > **Políticas** > **Regras de Resposta** e clique em **Adicionar Regra de Resposta**.
    
    ![adicionar regra de resposta](./media/icap-add-response-rule.png)

2.  Escolha **Resposta Automatizada** e clique em **Avançar**.

    ![resposta automatizada](./media/icap-automated-response.png)

3. Digite um nome de regra, por exemplo, **Bloquear HTTP/HTTPS**. Em **Ações**, escolha **Bloquear HTTP/HTTPS** e clique em **Salvar**.

    ![bloquear http](./media/icap-block-http.png)

Adicione a regra criada para todas as políticas existentes:
1. Alterne para a guia **Resposta** em cada política.
2. Na lista suspensa **Regra de resposta**, escolha a regra de bloqueio de resposta criada anteriormente.
3. Salve a política.
   
    ![desabilitar o modo de avaliação](./media/icap-add-policy.png)

Adicione esta regra a todas as políticas existentes.




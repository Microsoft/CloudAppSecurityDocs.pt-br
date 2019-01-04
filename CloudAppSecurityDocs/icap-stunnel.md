---
title: Integração de DLP externo do Cloud App Security por meio de ICAP seguro
description: Este artigo fornece as etapas necessárias para configurar a conexão ICAP no Cloud App Security e a instalação do stunnel.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/10/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 9656f6c6-7dd4-4c4c-a0eb-f22afce78071
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 86ef20ca985213a369035505232d4bf594a47caf
ms.sourcegitcommit: b86c3afd1093fbc825fec5ba4103e3a95f65758e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53177225"
---
# <a name="external-dlp-integration"></a>Integração de DLP externa

*Aplica-se a: Microsoft Cloud App Security*

O Microsoft Cloud App Security pode integrar soluções DLP existentes para estender esses controles para a nuvem preservando uma política consistente e unificada entre locais e atividades na nuvem. A plataforma exporta interfaces fáceis de usar, incluindo API REST e ICAP, habilitando a integração com sistemas de classificação de conteúdo, como Symantec Data Loss Prevention (antigo Vontu Data Loss Prevention) ou Forcepoint DLP. 

A integração é obtida com o protocolo ICAP padrão, um protocolo semelhante ao HTTP descrito em [RFC 3507](https://tools.ietf.org/html/rfc3507). Para proteger o ICAP para transmissão dos dados, é necessário configurar um túnel SSL seguro (stunnel) entre a solução DLP e o Cloud App Security. A configuração de stunnel fornece funcionalidade de criptografia TLS para seus dados durante o tráfego entre o servidor DLP e Cloud App Security. 

Este guia fornece as etapas necessárias para configurar a conexão ICAP no Cloud App Security e a instalação do stunnel para proteger a conexão passando por ele.


## <a name="architecture"></a>Arquitetura
O Cloud App Security examina o ambiente de nuvem e, com base em seu arquivo de configuração de política, decide se deve examinar o arquivo usando o mecanismo DLP interno ou DLP externo. Se a verificação do DLP externo for aplicada, o arquivo será enviado pelo túnel seguro para o ambiente do cliente no qual ele é transmitido para o dispositivo ICAP para o veredicto do DLP: permitido/bloqueado. As respostas são enviadas novamente ao Cloud App Security pelo stunnel, no qual são usadas pela política para determinar as ações seguintes, como notificações, quarentena e compartilhamento de controle.

![Arquitetura do stunnel](./media/icap-architecture-stunnel.png)

Como o Cloud App Security é executado no Azure, uma implantação no Azure resulta em desempenho aprimorado. No entanto, há suporte para outras opções, incluindo implantações de Nuvem e Locais. Implantação em outros ambientes pode resultar em degradação do desempenho devido à maior latência e taxa de transferência menor. O servidor ICAP e o stunnel devem ser implantados juntos na mesma rede para garantir que o tráfego seja criptografado.

## <a name="prerequisites"></a>Pré-requisitos
Para o Cloud App Security enviar dados por meio de seu stunnel para seu servidor ICAP, abra o firewall de DMZ para os endereços IP externos usados pelo Cloud App Security com um número da porta de origem dinâmico. 

1.  Endereços de origem: Consulte [Conectar aplicativos, em Pré-requisitos](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md#prerequisites)
2.  Porta TCP de origem: Dinâmico
3.  Endereços de destino: um ou dois endereços IP do stunnel conectado ao servidor ICAP externo que você configurará nas próximas etapas
4.  Porta TCP de destino: Conforme definido na rede

> [!NOTE] 
> Por padrão, o número da porta stunnel é definido como 11344. Você pode alterá-lo para outra porta, se necessário, mas certifique-se de anotar o novo número da porta, você deverá inseri-lo na próxima etapa.

## <a name="step-1--set-up-icap-server"></a>ETAPA 1:  Configurar o servidor ICAP

Configure um servidor ICAP, anote o número da porta e certifique-se de definir **Modo** como **Bloqueio**. O modo de bloqueio define o servidor ICAP para retransmitir o veredicto de classificação de volta ao Cloud App Security.

Veja a documentação do produto DLP Externo para obter instruções sobre como fazer essa configuração. Por exemplo, confira [Apêndice A: Instalação do servidor Forcepoint ICAP](#forcepoint) e [Apêndice B: Guia de Implantação da Symantec](#symantec).

## <a name="step-2--set-up-your-stunnel-server"></a>ETAPA 2:  Configurar o servidor de stunnel 

Nesta etapa, você configura o stunnel conectado a seu servidor ICAP. 

>[!NOTE]
> Embora altamente recomendada, essa etapa é opcional e pode ser ignorada em cargas de trabalho de teste. 

### <a name="install-stunnel-on-a-server"></a>Instalar stunnel em um servidor

**Pré-requisitos**

- **Um servidor** – um Windows Server ou um servidor do Linux com base em uma distribuição principal.

Consulte o [site do stunnel](https://www.stunnel.org/index.html) para obter detalhes sobre os tipos de servidores que oferecem suporte à instalação de stunnel. Se estiver usando o Linux, use o gerenciador de distribuição Linux para instalá-lo.

#### <a name="install-stunnel-on-windows"></a>Instalar stunnel em no Windows

1. [Baixe a última instalação do Windows Server](https://www.stunnel.org/downloads.html) (esse aplicativo deve funcionar em qualquer edição recente do Windows Server).
   (instalação padrão)

2. Durante a instalação, não crie um certificado autoassinado. Você criará um certificado em uma etapa posterior.

3. Clique em **Iniciar servidor após a instalação**.

4. Crie um certificado de uma das seguintes maneiras:

   - Use o servidor de gerenciamento de certificados para criar um certificado SSL no servidor ICAP. Em seguida, copie as chaves para o servidor que você preparou para a instalação do stunnel.
   - Ou, no servidor stunnel, use os seguintes comandos do OpenSSL para gerar uma chave privada e um certificado autoassinado. Substitua essas variáveis:
     - **key.pem** pelo nome da sua chave privada
     - **cert.pem** pelo nome do seu certificado
     - **stunnel-key** pelo nome da chave criada recentemente

5. No seu caminho de instalação de stunnel, abra o diretório de configuração. Por padrão, ele é: c:\Arquivos de programas (x86)\stunnel\config\
6. Execute linha de comando com permissões de administrador:     `..\bin\openssl.exe genrsa -out key.pem 2048 `
      
     ` ..\bin\openssl.exe  req -new -x509 -config ".\openssl.cnf" -key key.pem -out .\cert.pem -days 1095`

7. Concatene cert.pem e key.pem e salve-os no arquivo: `type cert.pem key.pem >> stunnel-key.pem`

8. [Baixe a chave pública](https://adaprodconsole.blob.core.windows.net/icap/publicCert.pem) e salve-a nesse local **C:\Arquivos de programas (x86)\stunnel\config\MCASca.pem**.

9. Adicione as regras a seguir para abrir a porta no firewall do Windows:

       rem Open TCP Port 11344 inbound and outbound
       netsh advfirewall firewall add rule name="Secure ICAP TCP Port 11344" dir=in action=allow protocol=TCP localport=11344
       netsh advfirewall firewall add rule name="Secure ICAP TCP Port 11344" dir=out action=allow protocol=TCP localport=11344

10. Execute: `c:\Program Files (x86)\stunnel\bin\stunnel.exe` para abrir o aplicativo stunnel. 

11. Clique em **Configuração** e em **Editar configuração**.

    ![Editar configuração do Windows Server](./media/stunnel-windows.png)
 
12. Abra o arquivo e cole as linhas de configuração do servidor a seguir. O **IP do Servidor DLP** é o endereço IP do servidor ICAP, **stunnel-key** é a chave que você criou na etapa anterior e **MCASCAfile** é o certificado público do cliente de stunnel do Cloud App Security. Exclua qualquer texto de exemplo que esteja em vigor (no exemplo, ele exibe o texto do Gmail) e copie o seguinte texto no arquivo:

        [microsoft-Cloud App Security]
        accept = 0.0.0.0:11344
        connect = **ICAP Server IP**:1344
        cert = C:\Program Files (x86)\stunnel\config\**stunnel-key**.pem
        CAfile = C:\Program Files (x86)\stunnel\config\**MCASCAfile**.pem
        TIMEOUTclose = 0
        client = no
13. Salve o arquivo e, em seguida, clique em **Recarregar configuração**.

14. Para validar que tudo está funcionando conforme o esperado, em um prompt de comando, execute: `netstat -nao  | findstr 11344`
 

#### <a name="install-stunnel-on-ubuntu"></a>Instalar stunnel no Ubuntu

O exemplo a seguir é baseado em uma instalação de servidor do Ubuntu, quando conectado como usuário raiz – para outros servidores, use comandos paralelos. 

No servidor preparado, baixe e instale a última versão do stunnel. Execute o seguinte comando no servidor Ubuntu para instalar o stunnel e o OpenSSL:

    apt-get update
    apt-get install openssl -y
    apt-get install stunnel4 -y

Verifique se o stunnel está instalado ao executar o comando a seguir de um console. Você deve obter o número de versão e uma lista de opções de configuração:

    stunnel-version

### <a name="generate-certificates"></a>Gerar certificados

O servidor ICAP e o Cloud App Security usam uma chave privada e um certificado público para criptografia de servidor e autenticação no stunnel. Certifique-se de criar a chave privada sem uma frase secreta para que stunnel possa ser executado como um serviço em segundo plano. Além disso, defina as permissões nos arquivos como **legível** para o proprietário do stunnel e como **nenhum** para outras pessoas.

Você pode criar os certificados em uma das seguintes maneiras:
- Use o servidor de gerenciamento de certificados para criar um certificado SSL no servidor ICAP. Em seguida, copie as chaves para o servidor que você preparou para a instalação do stunnel. 
- Ou, no servidor stunnel, use os seguintes comandos do OpenSSL para gerar uma chave privada e um certificado autoassinado. Substitua essas variáveis:
    - **“key.pem”** pelo nome da sua chave privada
    - **“cert.pem”** pelo nome do seu certificado
    - **“stunnel-key”** pelo nome da chave criada recentemente
       
            openssl genrsa -out key.pem 2048
            openssl req -new -x509 -key key.pem -out cert.pem -days 1095
            cat key.pem cert.pem >> /etc/ssl/private/stunnel-key.pem

### <a name="download-the-cloud-app-security-stunnel-client-public-key"></a>Baixe a chave pública do cliente do stunnel do Cloud App Security

Baixe a chave pública deste local: https://adaprodconsole.blob.core.windows.net/icap/publicCert.pem e salve-a neste local: **/etc/ssl/certs/MCASCAfile.pem**

### <a name="configure-stunnel"></a>Configurar o stunnel 

A configuração do stunnel é definida no arquivo stunnel.conf.

1. Crie o arquivo stunnel.conf no seguinte diretório: **vim /etc/stunnel/stunnel.conf**

2. Abra o arquivo e cole as linhas de configuração do servidor a seguir.  O **IP do Servidor DLP** é o endereço IP do servidor ICAP, **stunnel-key** é a chave que você criou na etapa anterior e **MCASCAfile** é o certificado público do cliente de stunnel do Cloud App Security:

        [microsoft-Cloud App Security]
        accept = 0.0.0.0:11344
        connect = **ICAP Server IP**:1344
        cert = /etc/ssl/private/**stunnel-key**.pem
        CAfile = /etc/ssl/certs/**MCASCAfile**.pem
        TIMEOUTclose = 1
        client = no


### <a name="update-your-ip-table"></a>Atualizar a tabela IP
Atualize a tabela de endereços IP com a seguinte regra de rota:
   
    iptables -I INPUT -p tcp --dport 11344 -j ACCEPT

Para fazer a atualização para a tabela de IP persistente, use os seguintes comandos:

     sudo apt-get install iptables-persistent
     sudo /sbin/iptables-save > /etc/iptables/rules.v4
 

### <a name="run-stunnel"></a>Executar stunnel
1. No servidor do stunnel, execute o seguinte comando:

        vim /etc/default/stunnel4

2. Altere a variável ENABLED para 1:

        ENABLED=1

3. Reinicie o serviço para que a configuração entrar em vigor:

        /etc/init.d/stunnel4 restart

4. Execute os seguintes comandos para verificar se o stunnel está funcionando corretamente:

        ps -A | grep stunnel

    e se ele está escutando a porta listada:

        netstat -anp | grep 11344

5. Certifique-se de que a rede na qual o servidor de stunnel foi implantado corresponda os pré-requisitos de rede, como mencionado anteriormente. Isso é necessário para permitir conexões de entrada do Cloud App Security para acessar com êxito o servidor.

Se o processo ainda não está funcionando, consulte o [documentação do stunnel](https://www.stunnel.org/docs.html) para solucionar problemas.


## <a name="step-3--connect-to-cloud-app-security"></a>ETAPA 3:  Conectar-se ao Cloud App Security

1. No Cloud App Security, em **Configurações**, selecione **Extensões de segurança** e selecione a guia **DLP externo**.

2. Clique no sinal de mais para adicionar uma nova conexão. 

3. No assistente **Adicionar novo DLP externo**, forneça um **Nome de conexão** (por exemplo, conector My Forcepoint), que será usado para identificar o conector.

4. Selecione o **Tipo de conexão**:
    - **Symantec Vontu** – use a integração personalizada para dispositivos de DLP da Vontu.
    - **Forcepoint DLP** – use a integração personalizada para dispositivos de DLP da Forcepoint.
    - **ICAP Genérico – REQMOD** – use outros dispositivos de DLP que usam [Solicitar Modificação](https://tools.ietf.org/html/rfc3507).
    - **ICAP Genérico – RESPMOD** – use outros dispositivos de DLP que usam [Modificação de Resposta](https://tools.ietf.org/html/rfc3507).
    ![Conexão ICAP do Cloud App Security](./media/icap-wizard1.png)

5. Procure e selecione o certificado público gerado nas etapas anteriores, “cert.pem”, para se conectar ao stunnel. Clique em **Avançar**.

   > [!NOTE]
   > É altamente recomendável selecionar a caixa **Usar ICAP seguro** para definir um gateway de stunnel criptografado. Se for para fins de teste ou se você não tiver um servidor de stunnel, desmarque essa caixa para se integrar diretamente ao servidor DLP. 

5. Na tela **Configuração do servidor**, forneça o **Endereço IP** e a **Porta** do servidor stunnel que você configurou na Etapa 2. Para fins de balanceamento de carga, configure o **Endereço IP** e a **Porta** de um servidor adicional. Os endereços IP fornecidos devem ser os endereços IP estáticos externos dos seus servidores.

   ![Conexão ICAP do Cloud App Security](./media/icap-wizard2.png)
6. Clique em **Avançar**. O Cloud App Security testa a conectividade com o servidor configurado. Se você receber um erro, examine as instruções e as configurações de rede. Depois de conectado com êxito, clique em **Encerrar**.

7. Agora, para direcionar o tráfego para esse servidor DLP externo, quando você criar uma **Política de arquivo**, em **Método de inspeção de conteúdo**, selecione a conexão que você criou. Leia mais sobre [Criar uma política de arquivo](data-protection-policies.md).


## Apêndice A: Instalação do servidor ForcePoint ICAP <a name="forcepoint"></a>

No ForcePoint, defina seu dispositivo usando as seguintes etapas:

1.  Em seu dispositivo DLP, vá para **Implantação** > **Módulos do sistema**. 

    ![Implantação ICAP](./media/icap-system-modules.png)

2.  Na guia **Geral**, verifique se **Servidor ICAP** está **Habilitado** e se a **Porta** padrão está definida como **1344**. Além disso, em **Permitir conexão com este Servidor ICAP pelos endereços IP a seguir**, selecione **Qualquer endereço IP**.
 
    ![Configuração do ICAP](./media/icap-ip-address.png)

3.  Na guia HTTP/HTTPS, certifique-se de definir **Modo** como **bloqueio**.
 
    ![Bloqueio de ICAP](./media/icap-blocking.png)
 

## Apêndice B: Guia de Implantação da Symantec <a name="symantec"></a>

As versões com suporte do Symantec DLP são 11 e superiores. 

Conforme observado acima, você deve implantar um servidor de detecção no mesmo datacenter do Azure onde seu locatário do Cloud App Security reside. O servidor de detecção sincroniza com o servidor de imposição por meio de um túnel IPSec dedicado. 
 
### <a name="detection-server-installation"></a>Instalação do servidor de detecção 
O servidor de detecção usado pelo Cloud App Security é um Network Prevent padrão para servidor Web. Há várias opções de configuração que devem ser alteradas:
1. Desabilite o **Modo de Avaliação**:
   1. Em **Sistema** > **Servidores e Detectores**, clique no destino de ICAP. 
    
      ![Destino de ICAP](./media/icap-target.png)
    
   2. Clique em **Configurar**. 
    
      ![Configurar o destino de ICAP](./media/configure-icap-target.png)
    
   3. Desabilite o **Modo de Avaliação**.
    
      ![desabilite o modo de avaliação](./media/icap-disable-trial-mode.png)
    
2. Em **ICAP** > **Filtragem de Resposta**, altere o valor de **Ignorar Respostas Menores Que** para 1.


3. E adicione "application/\*" à lista de **Inspecionar Tipo de Conteúdo</em>**.
     ![inspecionar tipo de conteúdo](./media/icap-inspect-content-type.png)

4. Clique em **Salvar**


### <a name="policy-configuration"></a>Configuração de política
O Cloud App Security dá suporte direto a todos os tipos de regra de detecção incluídos com o Symantec DLP; portanto, não é necessário alterar as regras existentes. No entanto, há uma alteração de configuração que precisa ser aplicada a todas as políticas novas e existentes para habilitar a integração completa. Essa alteração é a adição de uma regra específica de resposta para todas as políticas. 

Adicione a alteração de configuração ao Vontu:

1.  Vá para **Gerenciar** > **Políticas** > **Regras de Resposta** e clique em **Adicionar Regra de Resposta**.
    
    ![adicionar regra de resposta](./media/icap-add-response-rule.png)

2.  Verifique se **Resposta Automatizada** está selecionado e clique em **Avançar**.

    ![resposta automatizada](./media/icap-automated-response.png)

3. Digite um nome de regra, por exemplo, **Bloquear HTTP/HTTPS**. Em **Ações**, selecione **Bloquear HTTP/HTTPS** e clique em **Salvar**.

    ![bloquear http](./media/icap-block-http.png)

Adicione a regra criada a todas as políticas existentes:

1. Em cada Política, alterne para a guia **Resposta**.

2. Na lista suspensa **Regra de resposta**, selecione a regra de resposta de bloqueio que você criou anteriormente.

3. Salve a política.
   
    ![desabilite o modo de avaliação](./media/icap-add-policy.png)

Essa regra deve ser adicionada a todas as políticas existentes.

>[!NOTE]
> Se você usar o Symantec Vontu para examinar arquivos do Dropbox, o CAS exibirá o arquivo automaticamente como sendo de origem da seguinte URL: http://misc/filename Essa URL de espaço reservado, na verdade, não leva a lugar algum, mas é usada para fins de log.


## <a name="next-steps"></a>Próximas etapas 
[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)   

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/)  

---
title: "Integração do SIEM ao Cloud App Security | Microsoft Docs"
description: "Este tópico fornece informações a respeito da integração do SIEM ao Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/22/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 4649423b-9289-49b7-8b60-04b61eca1364
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 298358657f775ec3a53a52112ee05af5db13ca16
ms.sourcegitcommit: 6e4eac42e553fd288da7de9c67eb79f11a420245
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2017
---
# <a name="siem-integration"></a>Integração ao SIEM
    
Agora você pode integrar o Cloud App Security ao seu servidor SIEM para habilitar o monitoramento centralizado de alertas e de atividades do Office 365. À medida que novas atividades e eventos vão tendo suporte no Office 365, a visibilidade de seu conteúdo é implementada no Cloud App Security. A integração a um serviço SIEM permite que você proteja melhor seus aplicativos na nuvem e, ao mesmo tempo, mantém seu fluxo de trabalho de segurança comum, automatiza os procedimentos de segurança e correlaciona os eventos baseados em nuvem e locais. O agente SIEM do Cloud App Security é executado no servidor e efetua pull de alertas e de atividades do Cloud App Security e transmite-os para o servidor SIEM.

Ao integrar o SIEM primeiro com o Cloud App Security, atividades e alertas dos últimos dois dias serão encaminhadas para o SIEM e todos os alertas e atividades (com base no filtro que você selecionar) daquele momento em diante. Além disso, se você desabilitar esse recurso por um longo período, quando você habilita-o novamente ele encaminhará os últimos dois dias de alertas e atividades e, em seguida, todos os alertas e atividades daquele momento em diante.

## <a name="siem-integration-architecture"></a>Arquitetura de integração do SIEM

O agente SIEM é implantado na rede da sua organização. Quando implantado e configurado, ele efetua pull dos tipos de dados que foram configurados (alertas e atividades) usando as APIs RESTful do Cloud App Security.
O tráfego é, então, enviado por meio de um canal HTTPS criptografado na porta 443.

Depois que o agente SIEM recuperar os dados do Cloud App Security, ele enviará as mensagens do Syslog para seu SIEM local usando as configurações da rede que você forneceu durante a configuração (TCP ou UDP com uma porta personalizada). 

![Arquitetura de integração do SIEM](./media/siem-architecture.png)

## <a name="supported-siems"></a>SIEMs com suporte

O Cloud App Security atualmente oferece suporte apenas a HP ArcSight e CEF genérico.

## <a name="how-to-integrate"></a>Como integrar

A integração ao SIEM é realizada em três etapas:
1. Configurar no portal do Cloud App Security. 
2. Baixar o arquivo JAR e executá-lo no servidor.
3. Valide se o agente SIEM está funcionando.

### <a name="prerequisites"></a>Pré-requisitos

- Um servidor Windows ou Linux padrão (pode ser uma máquina virtual).
- O servidor deve executar o Java 8. Não há suporte para versões anteriores.

## <a name="integrating-with-your-siem"></a>Integrando ao seu SIEM

### <a name="step-1-set-it-up-in-the-cloud-app-security-portal"></a>Etapa 1: configurar no portal do Cloud App Security

1. No portal do Cloud App Security, sob a engrenagem de Configurações, clique em **Extensões de segurança** e, em seguida, clique na guia **Agentes SIEM**.

2. Clique no ícone de adição para iniciar o assistente do **Adicionar agente SIEM**.
3. No assistente, clique em **Adicionar agente SIEM**. 
4. No assistente, preencha um nome, **Selecione o formato do seu SIEM** e defina as **Configurações avançadas** relevantes do formato. Clique em **Avançar**.

   ![Configurações gerais do SIEM](./media/siem1.png)

5. Digite o endereço IP ou nome de host do **Host do syslog remoto** e o **Número da porta do syslog**. Selecione TCP ou UDP como o protocolo do Syslog Remoto.
Você pode consultar seu administrador de segurança para obter esses detalhes caso ainda não os tenha.
Clique em **Avançar**.

  ![Configurações do Syslog Remoto](./media/siem2.png)

6. Selecione quais tipos de dados, **Alertas** e **Atividades** você deseja exportar para o servidor SIEM. Use o controle deslizante para habilitar e desabilitá-los. Por padrão, todas as opções estão marcadas. Você pode usar a lista suspensa **Aplicar a** para definir os filtros para enviarem atividades e alertas específicos ao servidor SIEM.
Você pode clicar em **Editar e visualizar resultados** para verificar se o filtro funciona conforme o esperado. Clique em **Avançar**. 

  ![Configurações de tipos de dados](./media/siem3.png)

7. Copie o token e salve-o para mais tarde. Depois de clicar em Concluir e sair do Assistente, de volta à página SIEM, você poderá ver o agente SIEM adicionado na tabela. Ele exibirá que foi **Criado** até ser conectado posteriormente.

### <a name="step-2-download-the-jar-file-and-run-it-on-your-server"></a>Etapa 2: baixar o arquivo JAR e executá-lo no servidor

1. No [Centro de Download da Microsoft](https://go.microsoft.com/fwlink/?linkid=838596), depois de aceitar os [termos de licença de software](https://go.microsoft.com/fwlink/?linkid=862491), baixe o arquivo .zip e descompacte-o.

2. Extraia o arquivo .jar do arquivo zip e execute-o no servidor.
 Depois de executar o arquivo, execute o seguinte:
    
        java -jar mcas-siemagent-0.87.20-signed.jar [--logsDirectory DIRNAME] [--proxy ADDRESS[:PORT]] --token TOKEN

> [!NOTE]
> - O nome do arquivo pode ser diferente dependendo da versão do agente SIEM.
> - Parâmetros em colchetes [ ] são opcionais e devem ser usados somente se relevantes.
> - É recomendável executar o JAR durante a inicialização do servidor.
>   - Windows: Execute como uma tarefa agendada e configure a tarefa para **Executar estando o usuário conectado ou não** e desmarque a caixa de seleção **Interromper a tarefa se ela for executada por mais tempo que**.
>   - Linux: adicione o comando de execução com um  **&**  para o arquivo rc.local. Por exemplo: `java -jar mcas-siemagent-0.87.20-signed.jar [--logsDirectory DIRNAME] [--proxy ADDRESS[:PORT]] --token TOKEN &`

Quando as seguintes variáveis são usadas:
- DIRNAME é o caminho para o diretório que você deseja usar para os logs locais de depuração do agente.
- ADDRESS[:PORT] é o endereço do servidor proxy e a porta que o servidor usa para se conectar à Internet.
- TOKEN é o token do agente SIEM copiado na etapa anterior.

Você pode digitar -h a qualquer momento para obter ajuda.

Estes são exemplos de logs de atividades enviados para o seu SIEM:
```
    2017-07-11T19:14:55.895Z CEF:0|MCAS|SIEM_Agent|0.102.17|EVENT_CATEGORY_LOGIN|Log on|0|externalId=1499800495894_e453bc33-a7c1-48f7-8397-8ae8e2758183 start=1499800495895 end=1499800495895 msg=Log on suser=admin@contoso.com destinationServiceName=Microsoft Exchange Online dvc=13.82.149.151 requestClientApplication=Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/59.0.3071.115 Safari/537.36 machine_id_149980022970038514 cs1Label=portalURL cs1=https://cloud-app-security.com/#/audits?activity.id\=eq(1499800495894_e453bc33-a7c1-48f7-8397-8ae8e2758183,) cs2Label=uniqueServiceAppIds cs2=APPID_OUTLOOK cs3Label=targetObjects cs3=admin@contoso.com c6a1Label="Device IPv6 Address" c6a1=
    2017-07-11T19:14:56.781Z CEF:0|MCAS|SIEM_Agent|0.102.17|EVENT_CATEGORY_DOWNLOAD_FILE|Download file|0|externalId=1499800496781_2e50118e-dee7-40d7-b912-b81a10feed28 start=1499800496781 end=1499800496781 msg=Download file: file name50280117yyct6t.xlsx suser=roy@adallom.com.test destinationServiceName=Salesforce dvc=13.82.149.151 requestClientApplication=Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/59.0.3071.115 Safari/537.36 machine_id_149979855250880034 cs1Label=portalURL cs1=https://cloud-app-security/#/audits?activity.id\=eq(1499800496781_2e50118e-dee7-40d7-b912-b81a10feed28,) cs2Label=uniqueServiceAppIds cs2=APPID_SALESFORCE cs3Label=targetObjects cs3=name50280117yyct6t.xlsx c6a1Label="Device IPv6 Address" c6a1=
    2017-07-11T19:16:04.666Z CEF:0|MCAS|SIEM_Agent|0.102.17|EVENT_CATEGORY_SSO_LOGIN|Single sign-on log on|0|externalId=1499800564666_06496600-edde-4d81-a995-7632e70fb24f start=1499800564666 end=1499800564666 msg=Single sign-on log on suser=admin@contoso.com destinationServiceName=Microsoft Online Services dvc=13.82.149.151 requestClientApplication=Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/59.0.3071.115 Safari/537.36 machine_id_149980039637481908 cs1Label=portalURL cs1=https://cloud-app-security.com/#/audits?activity.id\=eq(1499800564666_06496600-edde-4d81-a995-7632e70fb24f,) cs2Label=uniqueServiceAppIds cs2=APPID_11394 cs3Label=targetObjects cs3=admin@contoso.com c6a1Label="Device IPv6 Address" c6a1=
    2017-07-12T13:28:29.067Z CEF:0|MCAS|SIEM_Agent|0.102.17|EVENT_CATEGORY_DOWNLOAD_FILE|Download file|0|externalId=1499866109067_8e3fae2c-ca5b-4163-84b6-fb9a03c4d052 start=1499866109067 end=1499866109067 msg=Download file: file CC004.txt suser=admin@box-contoso.com destinationServiceName=Box dvc=194.69.102.134 requestClientApplication=Mozilla/5.0 (Linux; Android 7.0; SAMSUNG SM-G930F Build/NRD90M) AppleWebKit/537.36 (KHTML, like Gecko) SamsungBrowser/5.0 Chrome/51.0.2704.106 Mobile Safari/537.36 cs1Label=portalURL cs1=https://cloud-app-security.com/#/audits?activity.id\=eq(1499866109067_8e3fae2c-ca5b-4163-84b6-fb9a03c4d052,) cs2Label=uniqueServiceAppIds cs2=APPID_BOX cs3Label=targetObjects cs3=CC004.txt c6a1Label="Device IPv6 Address" c6a1=
    2017-07-12T14:15:33.901Z CEF:0|MCAS|SIEM_Agent|0.102.17|EVENT_CATEGORY_UPLOAD_FILE|Upload file|0|externalId=1499868933901_72c21ebe-c206-4d8c-a41b-224035868d09 start=1499868933901 end=1499868933901 msg=Upload file: file response.txt suser=user1@test15-adallom.com destinationServiceName=Google Drive dvc=194.69.102.134 requestClientApplication=Mozilla/5.0 (Windows NT 10.0; WOW64; Trident/7.0; Touch; rv:11.0) like Gecko cs1Label=portalURL cs1=https://cloud-app-security.com/#/audits?activity.id\=eq(1499868933901_72c21ebe-c206-4d8c-a41b-224035868d09,) cs2Label=uniqueServiceAppIds cs2=APPID_26069 cs3Label=targetObjects cs3=response.txt c6a1Label="Device IPv6 Address" c6a1=
    2017-07-12T18:53:16.519Z CEF:0|MCAS|SIEM_Agent|0.102.17|EVENT_CATEGORY_LOGIN|Log on|0|externalId=1499885596519_ed261269-9b07-4418-9ded-8cad464d677f start=1499885596519 end=1499885596519 msg=Log on suser=admin@contoso.com destinationServiceName=Office 365 dvc=13.82.149.151 requestClientApplication=Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/59.0.3071.115 Safari/537.36 machine_id_149988543613557447 cs1Label=portalURL cs1=https://cloud-app-security.com/#/audits?activity.id\=eq(1499885596519_ed261269-9b07-4418-9ded-8cad464d677f,) cs2Label=uniqueServiceAppIds cs2=APPID_O365 cs3Label=targetObjects cs3=admin@contoso.com c6a1Label="Device IPv6 Address" c6a1=
```
Bem como o seguinte exemplo de arquivo de log de alertas:
```
  2017-07-15T20:42:30.531Z CEF:0|MCAS|SIEM_Agent|0.102.17|ALERT_CABINET_EVENT_MATCH_AUDIT|myPolicy|3|externalId=596a7e360c204203a335a3fb start=1500151350531 end=1500151350531 msg=Activity policy ''myPolicy'' was triggered by ''admin@box-contoso.com'' suser=admin@box-contoso.com destinationServiceName=Box cn1Label=riskScore cn1= cs1Label=portalURL cs1=https://cloud-app-security.com/#/alerts/596a7e360c204203a335a3fb cs2Label=uniqueServiceAppIds cs2=APPID_BOX cs3Label=relatedAudits cs3=1500151288183_acc891bf-33e1-424b-a021-0d4370789660
  2017-07-16T09:36:26.550Z CEF:0|MCAS|SIEM_Agent|0.102.17|ALERT_CABINET_EVENT_MATCH_AUDIT|test-activity-policy|3|externalId=596b339b0c204203a33a51ae start=1500197786550 end=1500197786550 msg=Activity policy ''test-activity-policy'' was triggered by ''user@contoso.com'' suser=user@contoso.com destinationServiceName=Salesforce cn1Label=riskScore cn1= cs1Label=portalURL cs1=https://cloud-app-security.com/#/alerts/596b339b0c204203a33a51ae cs2Label=uniqueServiceAppIds cs2=APPID_SALESFORCE cs3Label=relatedAudits cs3=1500197720691_b7f6317c-b8de-476a-bc8f-dfa570e00349
  2017-07-16T09:17:03.361Z CEF:0|MCAS|SIEM_Agent|0.102.17|ALERT_CABINET_EVENT_MATCH_AUDIT|test-activity-policy3|3|externalId=596b2fd70c204203a33a3eeb start=1500196623361 end=1500196623361 msg=Activity policy ''test-activity-policy3'' was triggered by ''admin@contoso.com'' suser=admin@contoso.com destinationServiceName=Office 365 cn1Label=riskScore cn1= cs1Label=portalURL cs1=https://cloud-app-security.com/#/alerts/596b2fd70c204203a33a3eeb cs2Label=uniqueServiceAppIds cs2=APPID_O365 cs3Label=relatedAudits cs3=1500196549157_a0e01f8a-e29a-43ae-8599-783c1c11597d
  2017-07-16T09:17:15.426Z CEF:0|MCAS|SIEM_Agent|0.102.17|ALERT_CABINET_EVENT_MATCH_AUDIT|test-activity-policy|3|externalId=596b2fd70c204203a33a3eec start=1500196635426 end=1500196635426 msg=Activity policy ''test-activity-policy'' was triggered by ''admin@contoso.com'' suser=admin@contoso.com destinationServiceName=Microsoft Office 365 admin center cn1Label=riskScore cn1= cs1Label=portalURL cs1=https://cloud-app-security.com/#/alerts/596b2fd70c204203a33a3eec cs2Label=uniqueServiceAppIds cs2=APPID_O365_PORTAL cs3Label=relatedAudits cs3=1500196557398_3e102b20-d9fa-4f66-b550-8c7a403bb4d8
  2017-07-16T09:17:46.290Z CEF:0|MCAS|SIEM_Agent|0.102.17|ALERT_CABINET_EVENT_MATCH_AUDIT|test-activity-policy4|3|externalId=596b30200c204203a33a4765 start=1500196666290 end=1500196666290 msg=Activity policy ''test-activity-policy4'' was triggered by ''admin@contoso.com'' suser=admin@contoso.com destinationServiceName=Microsoft Exchange Online cn1Label=riskScore cn1= cs1Label=portalURL cs1=https://cloud-app-security.com/#/alerts/596b30200c204203a33a4765 cs2Label=uniqueServiceAppIds cs2=APPID_OUTLOOK cs3Label=relatedAudits cs3=1500196587034_a8673602-7e95-46d6-a1fe-c156c4709c5d
  2017-07-16T09:41:04.369Z CEF:0|MCAS|SIEM_Agent|0.102.17|ALERT_CABINET_EVENT_MATCH_AUDIT|test-activity-policy2|3|externalId=596b34b10c204203a33a5240 start=1500198064369 end=1500198064369 msg=Activity policy ''test-activity-policy2'' was triggered by ''user2@test15-adallom.com'' suser=user2@test15-adallom.com destinationServiceName=Google cn1Label=riskScore cn1= cs1Label=portalURL cs1=https://cloud-app-security.com/#/alerts/596b34b10c204203a33a5240 cs2Label=uniqueServiceAppIds cs2=APPID_33626 cs3Label=relatedAudits cs3=1500197996117_fd71f265-1e46-4f04-b372-2e32ec874cd3
```
#### <a name="sample-cloud-app-security-alerts-in-cef-format"></a>Alertas de exemplo do Cloud App Security em CEF (Formato Comum de Evento)


##### <a name="activity-logs"></a>Logs de Atividade

-   EVENT_CATEGORY_* – Categoria de atividade de alto nível

-   <ACTION> – O tipo de atividade, conforme exibido no portal

-   externalId – ID do evento

-   start – Carimbo de data/hora do alerta

-   end – Carimbo de data/hora do alerta

-   rt – Carimbo de data/hora do alerta

-   msg – Descrição do evento, conforme exibido no portal

-   suser – Atividade do usuário

-   destinationServiceName – Aplicativo de origem da atividade; por exemplo, Office 365, Sharepoint e Box.

-   dvc – IP do dispositivo do cliente

-   requestClientApplication – Agente do usuário do dispositivo do cliente

-   cs<X>Label – Cada rótulo tem um significado diferente, mas o rótulo em si é autoexplicativo; por exemplo, targetObjects (objetos de destino).

-   cs<X> – As informações relacionadas ao rótulo (o usuário de destino da atividade ou do alerta, de acordo com o exemplo de rótulo).

##### <a name="alerts"></a>Alertas

-   <alert type> – Por exemplo, "ALERT_CABINET_EVENT_MATCH_AUDIT"

-   <name> – O nome da política correspondente

-   externalId – ID do alerta

-   start – Carimbo de data/hora do alerta

-   end – Carimbo de data/hora do alerta

-   rt – Carimbo de data/hora do alerta

-   msg – Descrição do alerta conforme exibido no portal

-   suser – Usuário da entidade do alerta

-   destinationServiceName – Aplicativo de origem do alerta; por exemplo, Office 365, SharePoint e Box

-   cs<X>Label – Cada rótulo tem um significado diferente, mas o rótulo em si é autoexplicativo; por exemplo, targetObjects (objetos de destino).

-   cs<X> – As informações relacionadas ao rótulo (o usuário de destino da atividade ou do alerta, de acordo com o exemplo de rótulo).


### <a name="step-3-validate-that-the-siem-agent-is-working"></a>Etapa 3: validar se o agente SIEM está funcionando

1. Verifique se o status do agente SIEM no portal do Cloud App Security não está como **Erro de Conexão** ou **Desconectado** e se não há nenhuma notificação do agente. Ele será exibido como **Erro de Conexão** se a conexão estiver inativa por mais de duas horas e como **Desconectado**, se a conexão estiver inativa por mais de 12 horas.
 ![SIEM desconectado](./media/siem-not-connected.png)
 
   Em vez disso, o status deve ser conectado, conforme visto aqui: ![SIEM conectado](./media/siem-connected.png)

2. No servidor Syslog/SIEM, verifique se você pode ver os alertas e as atividades que chegam do Cloud App Security.


## <a name="regenerating-your-token"></a>Regenerando o token
Se você perder o token, sempre será possível regenerá-lo clicando nos três pontos ao final da linha do agente SIEM na tabela e selecionando **Regenerar token**.

 ![SIEM – regenerar token](./media/siem-regenerate-token.png)

## <a name="editing-your-siem-agent"></a>Editando o agente SIEM 
Se precisar editar o agente SIEM no futuro, você poderá clicar nos três pontos ao final da linha do agente SIEM na tabela e selecionar **Editar**. Se você editar o agente SIEM, não será necessário executar novamente o arquivo .jar; ele será atualizado automaticamente.

![SIEM – editar](./media/siem-edit.png)

## <a name="deleting-your-siem-agent"></a>Excluindo o agente SIEM
Se precisar excluir o agente SIEM no futuro, você poderá clicar nos três pontos ao final da linha do agente SIEM na tabela e selecionar **Excluir**.

![SIEM – excluir](./media/siem-delete.png)

> [!NOTE]
> Esse recurso está em visualização pública.

## <a name="high-availability-options"></a>Opções de alta disponibilidade

O agente SIEM é um ponto de extremidade único que oferece suporte à recuperação de até dois dias de tempo de inatividade. É possível alcançar uma medida adicional de alta disponibilidade com um balanceador de carga como o ponto de extremidade do cliente.

## <a name="see-also"></a>Veja também  
[Solução de problemas de integração de SIEM](troubleshooting-siem.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
---
title: Integração de SIEM genérico com Cloud App Security
description: Este artigo fornece informações sobre como integrar o SIEM genérico com o Cloud App Security.
ms.date: 01/17/2021
ms.topic: how-to
ms.openlocfilehash: 4e0facf906597ec4f66f77d8a2be3dd0001d8bda
ms.sourcegitcommit: bc0bfb2882ebc9f942197544707c987e36650035
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/18/2021
ms.locfileid: "98544218"
---
# <a name="generic-siem-integration"></a>Integração genérica ao SIEM

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Você pode integrar Microsoft Cloud App Security com seu servidor SIEM genérico para habilitar o monitoramento centralizado de alertas e atividades de aplicativos conectados. À medida que novas atividades e eventos se tornam compatíveis com os aplicativos conectados, a visibilidade de seu conteúdo é implementada no Microsoft Cloud App Security. A integração a um serviço SIEM permite que você proteja melhor seus aplicativos na nuvem e, ao mesmo tempo, mantém seu fluxo de trabalho de segurança comum, automatiza os procedimentos de segurança e correlaciona os eventos baseados em nuvem e locais. O agente SIEM do Microsoft Cloud App Security é executado no servidor e efetua pull de alertas e de atividades do Microsoft Cloud App Security e transmite-os para o servidor SIEM.

Ao integrar o SIEM primeiro com o Cloud App Security, atividades e alertas dos últimos dois dias serão encaminhadas para o SIEM e todos os alertas e atividades (com base no filtro que você selecionar) daquele momento em diante. Se você desabilitar esse recurso por um longo período e, em seguida, reabilitar, os últimos dois dias de atividades e alertas serão encaminhados e, em seguida, todos os alertas e atividades daí em diante.

As soluções de integração adicionais incluem:

* **Azure Sentinel** – um Siem escalonável, nativo de nuvem e disparar para integração nativa. Para obter informações sobre como integrar com o Azure Sentinel, consulte [integração do Azure Sentinel](siem-sentinel.md).
* **Microsoft Security Graph API** -um serviço intermediário (ou agente) que fornece uma única interface programática para conectar vários provedores de segurança. Para obter mais informações, consulte [integrações de solução de segurança usando a API de segurança do Microsoft Graph](/graph/security-integration#list-of-connectors-from-microsoft).

> [!IMPORTANT]
> Se você estiver integrando o Microsoft defender para identidade no Cloud App Security e os dois serviços estiverem configurados para enviar notificações de alerta para um SIEM, você começará a receber notificações de SIEM duplicadas para o mesmo alerta. Um alerta será emitido de cada serviço e eles terão diferentes IDs de alerta. Para evitar a duplicação e a confusão, certifique-se de lidar com o cenário. Por exemplo, decida onde você pretende executar o gerenciamento de alertas e, em seguida, interrompa as notificações do SIEM sendo enviadas do outro serviço.

## <a name="generic-siem-integration-architecture"></a>Arquitetura de integração do SIEM genérico

O agente SIEM é implantado na rede da sua organização. Quando implantado e configurado, ele efetua pull dos tipos de dados que foram configurados (alertas e atividades) usando as APIs RESTful do Cloud App Security.
O tráfego é, então, enviado por meio de um canal HTTPS criptografado na porta 443.

Depois que o agente SIEM recupera os dados do Cloud App Security, ele envia as mensagens do Syslog para o SIEM local. O Cloud App Security usa as configurações de rede que você forneceu durante a instalação (TCP ou UDP com uma porta personalizada).

![Arquitetura de integração do SIEM](media/siem-architecture.png)

## <a name="supported-siems"></a>SIEMs com suporte

Atualmente, o Cloud App Security tem suporte para Micro Focus ArcSight e CEF genérico.

## <a name="how-to-integrate"></a>Como integrar

A integração ao SIEM é realizada em três etapas:

1. Configurar no portal do Cloud App Security.
2. Baixar o arquivo JAR e executá-lo no servidor.
3. Valide se o agente SIEM está funcionando.

### <a name="prerequisites"></a>Pré-requisitos

* Um servidor Windows ou Linux padrão (pode ser uma máquina virtual).
* Sistema operacional: Windows ou Linux
* CPU: 2
* Espaço em disco: 20 GB
* RAM: 2 GB
* O servidor deve executar o Java 8. Não há suporte para versões anteriores.
* Segurança de camada de transporte (TLS) 1.2 +. Não há suporte para versões anteriores.
* Defina o firewall conforme descrito nos [Requisitos de rede](network-requirements.md)

## <a name="integrating-with-your-siem"></a>Integrando ao seu SIEM

### <a name="step-1-set-it-up-in-the-cloud-app-security-portal"></a>Etapa 1: configurar no portal do Cloud App Security

1. No portal de Cloud App Security, sob as **configurações** engrenagem, clique em **extensões de segurança**.

1. Na guia **agentes Siem** , clique em Adicionar ( **+** ) e escolha **Siem genérico**.

    ![Captura de tela mostrando o menu Adicionar integração SIEM](media/siem0.png)

1. No assistente, clique em **Iniciar Assistente**.
1. No assistente, preencha um nome, **Selecione o formato do seu SIEM** e defina as **Configurações avançadas** relevantes do formato. Clique em **Próximo**.

    ![Configurações gerais do SIEM](media/siem1.png)

1. Digite o endereço IP ou nome de host do **Host do syslog remoto** e o **Número da porta do syslog**. Selecione TCP ou UDP como o protocolo do Syslog Remoto.
    Você pode consultar seu administrador de segurança para obter esses detalhes caso ainda não os tenha. Clique em **Próximo**.

    ![Configurações do Syslog Remoto](media/siem2.png)

1. Selecione quais tipos de dados você deseja exportar para o servidor SIEM para **Alertas** e **Atividades**. Use o controle deslizante para habilitar e desabilitá-los. Por padrão, todas as opções estão marcadas. Você pode usar a lista suspensa **aplicar a** para definir filtros para enviar apenas alertas e atividades específicas para o servidor Siem. Clique em **Editar e visualizar resultados** para verificar se o filtro funciona conforme o esperado. Clique em **Próximo**.

   ![Configurações de tipos de dados](media/siem3.png)

1. Copie o token e salve-o para mais tarde.
    Clique em Concluir e saia do Assistente. Volte à página SIEM para ver o agente SIEM adicionado na tabela. Ele mostrará que ele será **criado** até que seja conectado posteriormente.

> [!NOTE]
> Tokens são associados ao administrador que os criaram. Isso significa que, se o usuário administrador for removido do Cloud App Security, o token não será mais válido.

### <a name="step-2-download-the-jar-file-and-run-it-on-your-server"></a>Etapa 2: baixar o arquivo JAR e executá-lo no servidor

1. No [Centro de Download da Microsoft](https://go.microsoft.com/fwlink/?linkid=838596), depois de aceitar os [termos de licença de software](https://go.microsoft.com/fwlink/?linkid=862491), baixe o arquivo .zip e descompacte-o.

1. Execute o arquivo extraído no servidor:

    `java -jar mcas-siemagent-0.87.20-signed.jar [--logsDirectory DIRNAME] [--proxy ADDRESS[:PORT]] --token TOKEN`

> [!NOTE]
>
> * O nome do arquivo pode ser diferente dependendo da versão do agente SIEM.
> * Parâmetros em colchetes [ ] são opcionais e devem ser usados somente se relevantes.
> * É recomendável executar o JAR durante a inicialização do servidor.
>   * Windows: execute como uma tarefa agendada e certifique-se de configurar a tarefa para **executar se o usuário está conectado ou não** e desmarque a caixa de seleção **parar a tarefa se ela for executada por mais tempo** .
>   * Linux: Adicione o comando executar com um **&** para o arquivo rc. local. Por exemplo: `java -jar mcas-siemagent-0.87.20-signed.jar [--logsDirectory DIRNAME] [--proxy ADDRESS[:PORT]] --token TOKEN &`

Quando as seguintes variáveis são usadas:

* DIRNAME é o caminho para o diretório que você deseja usar para os logs locais de depuração do agente.
* O endereço [:P classificar] é o endereço do servidor proxy e a porta que o servidor usa para se conectar à Internet.
* TOKEN é o token do agente SIEM copiado na etapa anterior.

Você pode digitar -h a qualquer momento para obter ajuda.

#### <a name="sample-activity-logs"></a>Amostra de log de atividade<a name="siem-samples"></a>

Estes são exemplos de logs de atividades enviados para o seu SIEM:

>`2017-11-22T17:50:04.000Z CEF:0|MCAS|SIEM_Agent|0.111.85|EVENT_CATEGORY_LOGOUT|Log out|0|externalId=1511373015679_167ae3eb-ed33-454a-b548-c2ed6cea6ef0 rt=1511373004000 start=1511373004000 end=1511373004000 msg=Log out suser=admin@contoso.com destinationServiceName=ServiceNow dvc=13.82.149.151 requestClientApplication= cs1Label=portalURL cs1=https://contoso.portal.cloudappsecurity.com/#/audits?activity.id\=eq(1511373015679_167ae3eb-ed33-454a-b548-c2ed6cea6ef0,) cs2Label=uniqueServiceAppIds cs2=APPID_SERVICENOW cs3Label=targetObjects cs3=admin@contoso.com,admin@contoso.com,admin@contoso.com cs4Label=policyIDs cs4= c6a1Label="Device IPv6 Address" c6a1=`
>
>`2017-11-28T19:40:15.000Z CEF:0|MCAS|SIEM_Agent|0.112.68|EVENT_CATEGORY_VIEW_REPORT|View report|0|externalId=1511898027370_e272cd5f-31a3-48e3-8a6a-0490c042950a rt=1511898015000 start=1511898015000 end=1511898015000 msg=View report: ServiceNow Report 23 suser=admin@contoso.com destinationServiceName=ServiceNow dvc= requestClientApplication= cs1Label=portalURL cs1=https://contoso.portal.cloudappsecurity.com/#/audits?activity.id\=eq(1511898027370_e272cd5f-31a3-48e3-8a6a-0490c042950a,) cs2Label=uniqueServiceAppIds cs2=APPID_SERVICENOW cs3Label=targetObjects cs3=23,sys_report,admin@contoso.com,admin@contoso.com,admin@contoso.com cs4Label=policyIDs cs4= c6a1Label="Device IPv6 Address" c6a1=`
>
>`2017-11-28T19:25:34.000Z CEF:0|MCAS|SIEM_Agent|0.112.68|EVENT_CATEGORY_DELETE_OBJECT|Delete object|0|externalId=1511897141625_7558b33f-218c-40ff-be5d-47d2bdd6b798 rt=1511897134000 start=1511897134000 end=1511897134000 msg=Delete object: ServiceNow Object f5122008db360300906ff34ebf96198a suser=admin@contoso.com destinationServiceName=ServiceNow dvc= requestClientApplication= cs1Label=portalURL cs1=https://contoso.portal.cloudappsecurity.com/#/audits?activity.id\=eq(1511897141625_7558b33f-218c-40ff-be5d-47d2bdd6b798,) cs2Label=uniqueServiceAppIds cs2=APPID_SERVICENOW cs3Label=targetObjects cs3=,,admin@contoso.com,admin@contoso.com,admin@contoso.com cs4Label=policyIDs cs4= c6a1Label="Device IPv6 Address" c6a1=`
>
>`2017-11-27T20:40:14.000Z CEF:0|MCAS|SIEM_Agent|0.112.49|EVENT_CATEGORY_CREATE_USER|Create user|0|externalId=1511815215873_824f8f8d-2ecd-439b-98b1-99a1adf7ba1c rt=1511815214000 start=1511815214000 end=1511815214000 msg=Create user: user 747518c0db360300906ff34ebf96197c suser=admin@contoso.com destinationServiceName=ServiceNow dvc= requestClientApplication= cs1Label=portalURL cs1=https://contoso.portal.cloudappsecurity.com/#/audits?activity.id\=eq(1511815215873_824f8f8d-2ecd-439b-98b1-99a1adf7ba1c,) cs2Label=uniqueServiceAppIds cs2=APPID_SERVICENOW cs3Label=targetObjects cs3=,747518c0db360300906ff34ebf96197c,sys_user,admin@contoso.com,admin@contoso.com,admin@contoso.com cs4Label=policyIDs cs4= c6a1Label="Device IPv6 Address" c6a1=`
>
>`2017-11-27T20:41:20.000Z CEF:0|MCAS|SIEM_Agent|0.112.49|EVENT_CATEGORY_DELETE_USER|Delete user|0|externalId=1511815287798_bcf60601-ecef-4207-beda-3d2b8d87d383 rt=1511815280000 start=1511815280000 end=1511815280000 msg=Delete user: user 233490c0db360300906ff34ebf9619ef suser=admin@contoso.com destinationServiceName=ServiceNow dvc= requestClientApplication= cs1Label=portalURL cs1=https://contoso.portal.cloudappsecurity.com/#/audits?activity.id\=eq(1511815287798_bcf60601-ecef-4207-beda-3d2b8d87d383,) cs2Label=uniqueServiceAppIds cs2=APPID_SERVICENOW cs3Label=targetObjects cs3=,233490c0db360300906ff34ebf9619ef,,admin@contoso.com,admin@contoso.com,admin@contoso.com cs4Label=policyIDs cs4= c6a1Label="Device IPv6 Address" c6a1=`
>
>`2017-11-28T19:24:55.000Z LAB-EUW-ARCTEST CEF:0|MCAS|SIEM_Agent|0.112.68|EVENT_CATEGORY_DELETE_OBJECT|Delete object|0|externalId=1511897117617_5be018ee-f676-4473-a9b5-5982527409be rt=1511897095000 start=1511897095000 end=1511897095000 msg=Delete object: ServiceNow Object b1709c40db360300906ff34ebf961923 suser=admin@contoso.com destinationServiceName=ServiceNow dvc= requestClientApplication= cs1Label=portalURL cs1=https://contoso.portal.cloudappsecurity.com/#/audits?activity.id\=eq(1511897117617_5be018ee-f676-4473-a9b5-5982527409be,) cs2Label=uniqueServiceAppIds cs2=APPID_SERVICENOW cs3Label=targetObjects cs3=,,admin@contoso.com,admin@contoso.com,admin@contoso.com cs4Label=policyIDs cs4= c6a1Label="Device IPv6 Address" c6a1=`

O texto a seguir é um exemplo de arquivo de log de alertas:

>`2017-07-15T20:42:30.531Z CEF:0|MCAS|SIEM_Agent|0.102.17|ALERT_CABINET_EVENT_MATCH_AUDIT|myPolicy|3|externalId=596a7e360c204203a335a3fb start=1500151350531 end=1500151350531 msg=Activity policy ''myPolicy'' was triggered by ''admin@box-contoso.com'' suser=admin@box-contoso.com destinationServiceName=Box cn1Label=riskScore cn1= cs1Label=portalURL cs1=https://cloud-app-security.com/#/alerts/596a7e360c204203a335a3fb cs2Label=uniqueServiceAppIds cs2=APPID_BOX cs3Label=relatedAudits cs3=1500151288183_acc891bf-33e1-424b-a021-0d4370789660 cs4Label=policyIDs cs4=59f0ab82f797fa0681e9b1c7`
>
>`2017-07-16T09:36:26.550Z CEF:0|MCAS|SIEM_Agent|0.102.17|ALERT_CABINET_EVENT_MATCH_AUDIT|test-activity-policy|3|externalId=596b339b0c204203a33a51ae start=1500197786550 end=1500197786550 msg=Activity policy ''test-activity-policy'' was triggered by ''user@contoso.com'' suser=user@contoso.com destinationServiceName=Salesforce cn1Label=riskScore cn1= cs1Label=portalURL cs1=https://cloud-app-security.com/#/alerts/596b339b0c204203a33a51ae cs2Label=uniqueServiceAppIds cs2=APPID_SALESFORCE cs3Label=relatedAudits cs3=1500197720691_b7f6317c-b8de-476a-bc8f-dfa570e00349 cs4Label=policyIDs cs4=`
>
>`2017-07-16T09:17:03.361Z CEF:0|MCAS|SIEM_Agent|0.102.17|ALERT_CABINET_EVENT_MATCH_AUDIT|test-activity-policy3|3|externalId=596b2fd70c204203a33a3eeb start=1500196623361 end=1500196623361 msg=Activity policy ''test-activity-policy3'' was triggered by ''admin@contoso.com'' suser=admin@contoso.com destinationServiceName=Office 365 cn1Label=riskScore cn1= cs1Label=portalURL cs1=https://cloud-app-security.com/#/alerts/596b2fd70c204203a33a3eeb cs2Label=uniqueServiceAppIds cs2=APPID_O365 cs3Label=relatedAudits cs3=1500196549157_a0e01f8a-e29a-43ae-8599-783c1c11597d cs4Label=policyIDs cs4=`
>
>`2017-07-16T09:17:15.426Z CEF:0|MCAS|SIEM_Agent|0.102.17|ALERT_CABINET_EVENT_MATCH_AUDIT|test-activity-policy|3|externalId=596b2fd70c204203a33a3eec start=1500196635426 end=1500196635426 msg=Activity policy ''test-activity-policy'' was triggered by ''admin@contoso.com'' suser=admin@contoso.com destinationServiceName=Microsoft 365 admin center cn1Label=riskScore cn1= cs1Label=portalURL cs1=https://cloud-app-security.com/#/alerts/596b2fd70c204203a33a3eec cs2Label=uniqueServiceAppIds cs2=APPID_O365_PORTAL cs3Label=relatedAudits cs3=1500196557398_3e102b20-d9fa-4f66-b550-8c7a403bb4d8 cs4Label=policyIDs cs4=59f0ab35f797fa9811e9b1c7`
>
>`2017-07-16T09:17:46.290Z CEF:0|MCAS|SIEM_Agent|0.102.17|ALERT_CABINET_EVENT_MATCH_AUDIT|test-activity-policy4|3|externalId=596b30200c204203a33a4765 start=1500196666290 end=1500196666290 msg=Activity policy ''test-activity-policy4'' was triggered by ''admin@contoso.com'' suser=admin@contoso.com destinationServiceName=Microsoft Exchange Online cn1Label=riskScore cn1= cs1Label=portalURL cs1=https://cloud-app-security.com/#/alerts/596b30200c204203a33a4765 cs2Label=uniqueServiceAppIds cs2=APPID_OUTLOOK cs3Label=relatedAudits cs3=1500196587034_a8673602-7e95-46d6-a1fe-c156c4709c5d cs4Label=policyIDs cs4=`
>
>`2017-07-16T09:41:04.369Z CEF:0|MCAS|SIEM_Agent|0.102.17|ALERT_CABINET_EVENT_MATCH_AUDIT|test-activity-policy2|3|externalId=596b34b10c204203a33a5240 start=1500198064369 end=1500198064369 msg=Activity policy ''test-activity-policy2'' was triggered by ''user2@test15-adallom.com'' suser=user2@test15-adallom.com destinationServiceName=Google cn1Label=riskScore cn1= cs1Label=portalURL cs1=https://cloud-app-security.com/#/alerts/596b34b10c204203a33a5240 cs2Label=uniqueServiceAppIds cs2=APPID_33626 cs3Label=relatedAudits cs3=1500197996117_fd71f265-1e46-4f04-b372-2e32ec874cd3 cs4Label=policyIDs cs4=`

#### <a name="sample-cloud-app-security-alerts-in-cef-format"></a>Alertas de exemplo do Cloud App Security em CEF (Formato Comum de Evento)

| Aplicável a | Nome do campo CEF | Descrição |
| --- | --- | --- |
| Atividades/Alertas | iniciar | Carimbo de data/hora da atividade ou do alerta |
| Atividades/Alertas | end | Carimbo de data/hora da atividade ou do alerta |
| Atividades/Alertas | rt | Carimbo de data/hora da atividade ou do alerta |
| Atividades/Alertas | msg | Descrição da atividade ou do alerta, conforme mostrado no portal |
| Atividades/Alertas | suser | Usuário de entidade da atividade ou do alerta |
| Atividades/Alertas | destinationServiceName | Aplicativo de origem da atividade ou do alerta; por exemplo, Office 365, SharePoint e Box. |
| Atividades/Alertas | cs\<X>Label | Cada rótulo tem um significado diferente, mas o rótulo em si é autoexplicativo; por exemplo, targetObjects (objetos de destino). |
| Atividades/Alertas | cs\<X> | As informações correspondentes ao rótulo (o usuário de destino da atividade ou do alerta, de acordo com o exemplo de rótulo). |
| Atividades | EVENT_CATEGORY_* | Categoria de alto nível da atividade |
| Atividades | \<ACTION> | O tipo de atividade, conforme exibido no portal |
| Atividades | externalId | ID do evento |
| Atividades | dvc | IP do dispositivo do cliente |
| Atividades | requestClientApplication | Agente do usuário do dispositivo do cliente |
| Alertas | \<alert type> | Por exemplo, "ALERT_CABINET_EVENT_MATCH_AUDIT" |
| Alertas | \<name> | O nome da política correspondente |
| Alertas | externalId | ID do Alerta |
| Alertas | src | Endereço IPv4 do dispositivo cliente |
| Alertas | c6a1 | Endereço IPv6 do dispositivo cliente |

### <a name="step-3-validate-that-the-siem-agent-is-working"></a>Etapa 3: validar se o agente SIEM está funcionando

1. Verifique se o status do agente SIEM no portal do Cloud App Security não está como **Erro de Conexão** ou **Desconectado** e se não há nenhuma notificação do agente. Ele aparecerá como **Erro de conexão** se a conexão estiver inativa por mais de duas horas. O status será mostrado como **Desconectado** se a conexão estiver inativa por mais de 12 horas.
 ![SIEM desconectado](media/siem-not-connected.png)

    Em vez disso, o status deve ser conectado, conforme visto aqui: ![SIEM conectado](media/siem-connected.png)

1. No servidor Syslog/SIEM, verifique se você pode ver os alertas e as atividades que chegam do Cloud App Security.

## <a name="regenerating-your-token"></a>Regenerando o token

Se você perder o token, sempre será possível regenerá-lo clicando nos três pontos ao final da linha do agente SIEM na tabela. Selecione **Regenerar token** para obter um novo token.

![SIEM – regenerar token](media/siem-regenerate-token.png)

## <a name="editing-your-siem-agent"></a>Editando o agente SIEM

Para editar o agente SIEM, clique nos três pontos no final da linha do agente SIEM na tabela e selecione **Editar**. Se você editar o agente SIEM, não será necessário executar novamente o arquivo .jar; ele será atualizado automaticamente.

![SIEM – editar](media/siem-edit.png)

## <a name="deleting-your-siem-agent"></a>Excluindo o agente SIEM

Para excluir o agente SIEM, clique nos três pontos no final da linha do agente SIEM na tabela e selecione **Excluir**.

![SIEM – excluir](media/siem-delete.png)

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Solução de problemas de integração de SIEM](troubleshooting-siem.md)

[!INCLUDE [Open support ticket](includes/support.md)]
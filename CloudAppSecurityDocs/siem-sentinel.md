---
title: Integração do Azure Sentinel com o Cloud App Security
description: Este artigo fornece informações sobre como integrar o SIEM genérico com o Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 10/28/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: f7664685204a2d2f1965800119c946c85f2cbe49
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2019
ms.locfileid: "74460395"
---
# <a name="azure-sentinel-integration-preview"></a>Integração do Azure Sentinel (versão prévia)

*Aplica-se ao: Microsoft Cloud App Security*

Você pode integrar Microsoft Cloud App Security com o Azure Sentinel (um SIEM escalonável, nativo de nuvem e disparar) para permitir o monitoramento centralizado de alertas e dados de descoberta. A integração com o Azure Sentinel permite que você proteja melhor seus aplicativos de nuvem mantendo seu fluxo de trabalho de segurança usual, automatizando procedimentos de segurança e correlacionando entre eventos baseados em nuvem e locais.

Os benefícios de usar o Azure Sentinel incluem:

* Retenção de dados mais longa fornecida pelo Log Analytics.
* As visualizações prontas para uso.
* Use ferramentas como o Microsoft Power BI ou pastas de trabalho do Azure Sentinel para criar suas próprias visualizações de dados de descoberta que atendam às suas necessidades organizacionais.

As soluções de integração adicionais incluem:

* **Siems genéricos** – integre Cloud app Security com seu servidor Siem genérico. Para obter informações sobre como integrar com um SIEM genérico, consulte [integração de Siem genérico](siem.md).
* **Microsoft Security Graph API** -um serviço intermediário (ou agente) que fornece uma única interface programática para conectar vários provedores de segurança. Para obter mais informações, consulte [integrações de solução de segurança usando a API de segurança do Microsoft Graph](https://docs.microsoft.com/graph/security-integration#list-of-connectors-from-microsoft).

## <a name="how-to-integrate"></a>Como integrar

A integração com o SIEM é realizada em duas etapas:

1. Configure-o em Cloud App Security.
1. Configure-o no Azure Sentinel.

### <a name="prerequisites"></a>Pré-requisitos

Para integrar com o Azure Sentinel:

* Você deve ter uma licença válida do Azure Sentinel
* Você deve ser um administrador global ou um administrador de segurança em seu locatário.

### <a name="integrating-with-azure-sentinel"></a>Integração com o Azure Sentinel

1. No portal de Cloud App Security, sob as **configurações** engrenagem, clique em **extensões de segurança**.

1. Na guia **agentes Siem** , clique em adicionar ( **+** ) e, em seguida, escolha **Azure Sentinel**.

    ![Captura de tela mostrando o menu Adicionar integração SIEM](media/siem0.png)

1. No assistente, selecione os tipos de dados que você deseja encaminhar para o Azure Sentinel. Você pode configurar a integração da seguinte maneira:
    1. **Alertas**: os alertas são automaticamente ativados quando o Azure Sentinel está habilitado. <!--Use the **Apply to** drop-down to filter which alerts are sent to Azure Sentinel.-->
    1. **Logs de descoberta**: Use o controle deslizante para habilitá-los e desabilitá-los, por padrão, tudo está selecionado e, em seguida, use a lista suspensa **aplicar a** para filtrar quais logs de descoberta são enviados para o Azure Sentinel.

    ![Captura de tela mostrando a página inicial de configurar a integração do Azure Sentinel](media/siem-sentinel-configuration.png)

1. Clique em **Avançar**e continue para o Azure Sentinel para finalizar a integração. Para obter informações sobre como configurar o Azure Sentinel, consulte [https://docs.microsoft.com/azure/sentinel/connect-cloud-app-security](https://docs.microsoft.com/azure/sentinel/connect-cloud-app-security).

    ![Captura de tela mostrando a página concluir da integração de configurar o Azure Sentinel](media/siem-sentinel-configuration-complete.png)

> [!NOTE]
> Os logs de descoberta começarão a ser encaminhados para o Azure Sentinel dentro de 15 minutos de configuração no portal do Cloud app Security.

## <a name="alerts-and-discovery-logs-in-azure-sentinel"></a>Alertas e logs de descoberta no Azure Sentinel

Depois que a integração for concluída, você poderá exibir Cloud App Security alertas e logs de descoberta no Azure Sentinel.

No Azure Sentinel, em **logs**, em **informações de segurança**, você pode encontrar os logs para os tipos de dados Cloud app Security, da seguinte maneira:

| Tipo de dados | Tabela |
| --- | --- |
| Logs de descoberta | McasShadowItReporting |
| Alertas | SecurityAlert |

A tabela a seguir descreve cada campo no esquema **McasShadowItReporting** :

| Campo | type | Descrição | Exemplos |
| --- | --- | --- | --- |
| TenantId | String | ID do espaço de trabalho | b459b4u5-912x-46d5-9cb1-p43069212nb4 |
| SourceSystem | String | Sistema de origem – valor estático | Azure |
| TimeGenerated [UTC] | DateTime | Data dos dados de descoberta | 2019-07-23T11:00:35.858 Z |
| StreamName | String | Nome do fluxo específico | Departamento de marketing |
| TotalEvents | Integer | Número total de eventos por sessão | 122 |
| BlockedEvents | Integer | Número de eventos bloqueados | 0 |
| UploadedBytes | Integer | Quantidade de dados carregados | 1\.514.874 |
| TotalBytes | Integer | Quantidade total de dados | 4\.067.785 |
| DownloadedBytes | Integer | Quantidade de dados baixados | 2\.552.911 |
| IP | String | Endereço IP de origem | 127.0.0.0 |
| UserName | String | Nome de usuário | `Raegan@contoso.com` |
| EnrichedUserName | String | Nome de usuário aprimorado com username do Azure AD | `Raegan@contoso.com` |
| AppName | String | Nome do aplicativo de nuvem | Microsoft OneDrive para empresas |
| AppId | Integer | Identificador do aplicativo de nuvem | 15600 |
| AppCategory | String | Categoria do aplicativo de nuvem | Armazenamento em nuvem |
| AppTags | Matriz de cadeia de caracteres | Marcas internas e personalizadas definidas para o aplicativo | ["aprovado"] |
| AppScore | Integer | A pontuação de risco do aplicativo em uma escala de 0-10, 10 sendo uma pontuação para um aplicativo não arriscado | 10 |
| type | String | Tipo de logs – valor estático | McasShadowItReporting |

## <a name="use-power-bi-with-cloud-app-security-data-in-azure-sentinel"></a>Usar Power BI com dados de Cloud App Security no Azure Sentinel

Depois que a integração for concluída, você também poderá usar os dados de Cloud App Security armazenados no Azure Sentinel em outras ferramentas.

Esta seção descreve como você pode usar o Microsoft Power BI (Power BI) para formatar e combinar dados facilmente para criar relatórios e painéis que atendam às necessidades da sua organização.

Você pode começar rapidamente usando as seguintes etapas:

1. Em Power BI, importe consultas do Sentinela do Azure para dados de Cloud App Security. Para obter mais informações, consulte [importar Azure monitor dados de log em Power bi](https://docs.microsoft.com/azure/azure-monitor/platform/powerbi).
1. [Instale o aplicativo Cloud App Security Shadow it Discovery](https://aka.ms/MCASShadowITReporting) e [Conecte-](#connect-the-cloud-app-security-app) o aos seus dados de log de descoberta para exibir o painel de Shadow it Discovery interno.

    > [!NOTE]
    > Atualmente, o aplicativo não está publicado no Microsoft AppSource. Portanto, talvez seja necessário entrar em contato com o administrador do Power BI para obter permissões para instalar o aplicativo.

    ![Captura de tela mostrando o painel do Shadow IT Discovery](media/siem-sentinel-configuration-powerbi-dashboard.png)

1. Opcionalmente, crie painéis personalizados em Power BI Desktop e ajuste-os para se adequar aos requisitos de análise visual e relatórios de sua organização.

### <a name="connect-the-cloud-app-security-app"></a>Conectar o aplicativo Cloud App Security

1. Em Power BI, clique em **aplicativos**e, em seguida, clique no aplicativo **Shadow it Discovery** .

1. Na página Introdução **ao novo aplicativo** , clique em **conectar**.

    ![Captura de tela mostrando a página conectar dados do aplicativo](media/siem-sentinel-powerbi-connect.png)

1. Na página ID do espaço de trabalho, insira sua ID do espaço de trabalho do Azure Sentinel conforme exibido na página Visão geral do log Analytics e clique em **Avançar**.

    ![Captura de tela mostrando solicitação de ID do espaço de trabalho](media/siem-sentinel-powerbi-workspace-id.png)

1. Na página autenticação, especifique o método de autenticação e o nível de privacidade e, em seguida, clique em **entrar**.

    ![Captura de tela mostrando a página de autenticação](media/siem-sentinel-powerbi-authentication.png)

1. Depois de conectar seus dados, vá para a guia **conjuntos** de dados de espaço de trabalho e clique em **Atualizar**. Isso atualizará o relatório com seus próprios dados.

[!INCLUDE [Open support ticket](includes/support.md)]

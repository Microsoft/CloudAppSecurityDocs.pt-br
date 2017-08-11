---
title: Trabalhando com aplicativos descobertos no Cloud App Security | Microsoft Docs
description: "Este tópico descreve o processo de identificação e correção de aplicativos de descoberta de nuvem arriscados no Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 8/6/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 645fd8c7-06d0-4f93-a85c-2976e7b3766d
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 683815d0db528ac65b0d547cd8e5ab09ea64321f
ms.sourcegitcommit: f9851779aa15b11f559e56ac818f1333f027c000
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/07/2017
---
# <a name="working-with-discovered-apps"></a>Trabalhando com aplicativos descobertos

## <a name="review-the-cloud-discovery-dashboard"></a>Examinar o Painel do Cloud Discovery

O painel do Cloud Discovery foi projetado para fornecer mais informações sobre como os aplicativos de nuvem estão sendo usados na sua organização. Ele fornece uma visão geral rápida de quais tipos de aplicativos estão sendo usados, os alertas abertos e os níveis de risco dos aplicativos na sua organização. Ele também mostra quem são os principais usuários do aplicativo e fornece um mapa do local da Matriz de Aplicativo. O Painel do Cloud Discovery tem muitas opções para filtrar os dados, para que você possa gerar exibições específicas dependendo do que mais lhe interessa, e gráficos de fácil compreensão para fornecer um panorama completo rápido.

![painel do Cloud Discovery](./media/cloud-discovery-dashboard.png)

A primeira coisa que você deve fazer para obter uma visão geral de seus aplicativos do Cloud Discovery é examinar o Painel do Cloud Discovery e analisar o seguinte:
 
1. Primeiro, examine o uso geral de aplicativos de nuvem em sua organização na **visão geral de alto nível de uso**.

2. Em seguida, aprofunde-se mais para ver quais são as **principais categorias** que estão sendo usadas na sua organização para cada um dos diferentes parâmetros de uso e quanto dessa utilização é de Aplicativos sancionados.

3. Vá ainda mais fundo e veja todos os aplicativos em uma categoria específica no widget de **Aplicativos descobertos**.

4. Você pode ver os **principais usuários e endereços IP** de origem para identificar quais usuários são os mais dominantes nos aplicativos de nuvem na sua organização.
5. Verifique como os aplicativos descobertos se espalham acordo com a localização geográfica (segundo a Matriz) no **mapa de Matriz de Aplicativos**.

6. Por fim, não se esqueça de examinar a pontuação de risco do aplicativo descoberto na **Visão geral de risco de aplicativos** e verificar o **status de alertas de descoberta** para ver quantos alertas abertos você deve investigar.

## <a name="deep-dive-into-discovered-apps"></a>Aprofundar-se nos aplicativos Descobertos
Se você deseja aprofundar-se ainda mais nos dados fornecidos pelo Cloud Discovery, use os filtros para examinar quais aplicativos são arriscados e quais são usados com frequência.


Por exemplo, se você quiser identificar aplicativos de colaboração e de armazenamento de nuvem arriscados usados com frequência, poderá usar a página de aplicativos Descobertos para os aplicativos que você deseja filtrar. Posteriormente, você pode [cancelar a sanção ou bloqueá-los](governance-discovery.md), da seguinte maneira:

Na página **Aplicativos descobertos**, em **Procurar por categoria**, selecione **Armazenamento em nuvem** e **Colaboração**. Em seguida, use os filtros avançados e defina **Fator de risco de conformidade** para **SOC 2** é igual a **False**; **Uso** > **Usuários** como maior que 50 usuários; e **Uso** > **Transações** maior que 100; **Fator de risco de segurança** > **Dados em criptografia rest** é igual a **False** e, em seguida, defina **Pontuação de risco** igual a menos de 6.

![Filtros dos aplicativos descobertos](./media/discovered-app-filters.png)

Depois que os resultados são filtrados, você pode [cancelar a sanção e bloqueá-los](governance-discovery.md) usando a caixa de seleção de ação em massa para cancelar a sanção de todos eles em uma ação só. Depois que eles tiverem a sanção cancelada, você poderá usar um script de bloqueio para impedir que eles sejam usados em seu ambiente.

O Cloud Discovery permite aprofundar ainda mais no uso de nuvem da sua organização e identificar instâncias específicas que estão em uso ao investigar os subdomínios de descoberta.

Por exemplo, você pode diferenciar entre os diferentes sites do SharePoint.

Isso tem suporte apenas em firewalls e proxies que contêm dados de URL de destino. Consulte a lista de dispositivos com suporte em [Proxies e firewalls com suporte](set-up-cloud-discovery.md#supported-firewalls-and-proxies).

![informações de subdomínio](./media/discovery-domains.png)  

## <a name="discovered-app-filters"></a>Filtros dos aplicativos descobertos

Há filtros de aplicativos Descoberto básicos e avançados. Para alcançar um filtro complexo (como no exemplo acima), use a opção avançada, que inclui todos os itens a seguir:

![Aplicativos Descobertos](./media/discovered-apps.png)  


- **Marca de aplicativo**: selecione se o aplicativo foi sancionado, não sancionado ou não está marcado. Além disso, você pode criar uma marca personalizada para seu aplicativo e, em seguida, usá-la para filtrar tipos específicos de aplicativos. 
- **Aplicativos e domínios**: permite que você pesquise aplicativos específicos ou aplicativos usados em domínios específicos. 
- **Categorias**: o filtro de categorias, que está localizado à esquerda da página, permite pesquisar tipos de aplicativos de acordo com as categorias de aplicativo, por exemplo, aplicativos de rede Social, aplicativos de armazenamento em nuvem etc. Você pode selecionar várias categorias por vez ou uma única categoria e, em seguida, aplicar os filtros básicos e avançados sobre eles.
- **Fator de risco de conformidade**: permite que você pesquise padrões específicos, certificação e conformidades com as quais o aplicativo pode cumprir (HIPAA ISO 27001, SOC 2, PCI-DSS etc.).
- **Fator de risco geral**: permite que você pesquise fatores de risco gerais, como a popularidade do consumidor, Data center local etc.
- **Pontuação de risco**: permite que você filtre aplicativos por classificação de risco para que você possa se concentrar, por exemplo, revisando somente os aplicativos muito arriscados. Você também pode substituir a pontuação de risco definida pelo Cloud App Security. Para saber mais, confira [Trabalhando com pontuação de risco](risk-score.md).
- **Fator de risco de segurança**: habilita a filtragem com base em medidas específicas de segurança (como Criptografia em rest, autenticação multifator etc.).
- **Uso**: permite filtrar com base em estatísticas de uso deste aplicativo, como aplicativos com menos de ou mais de uma quantidade especificada de **carregamentos de dados**, aplicativos com maior ou menor que um número especificado de **Usuários**.

## <a name="creating-and-managing-custom-app-tags"></a>Criando e gerenciando marcas de aplicativo personalizadas

Você pode criar uma marca de aplicativo personalizada. Essas marcas podem ser usadas como filtros para aprofundar-se nos tipos específicos de aplicativos que você deseja investigar. Por exemplo, lista de observação personalizada, atribuição a uma unidade de negócios específica ou aprovações personalizadas, como "aprovado pelo departamento jurídico".

Para criar uma marca de aplicativo personalizada:

1. Na engrenagem **Configurações**, selecione **Cloud Discovery** e na guia **Gerenciar marcas de aplicativo**, clique no ícone ![de adição](./media/plus-icon.png). 

![criar marca de aplicativo personalizada](./media/create-app-tag.png)

2. Você pode usar a tabela **Gerenciar marcas de aplicativo** para exibir quais aplicativos atualmente são marcados com cada marca de aplicativo e você pode excluir marcas de aplicativo não utilizados.

3. Para aplicar uma marca de aplicativo, na guia **Aplicativos descobertos**, clique nos três pontos na extremidade direita da tabela e selecione a marca do aplicativo para aplicar. 

> [!NOTE]
>Você também pode criar uma nova marca de aplicativo diretamente na tabela **Aplicativos descobertos** clicando na marca **Criar aplicativo** depois de selecionar os três pontos à direita de qualquer aplicativo selecionado. Você também pode acessar a tela **Gerenciar marcas de aplicativo** clicando no link no canto do pop-up **Criar marca de aplicativo**.

## <a name="exclude-entities"></a>Excluir entidades  
Se você tiver usuários do sistema ou endereços IP que são particularmente ruidosos e não interessantes ou aplicativos que não são relevantes, talvez você deseje excluir os dados deles dos dados do Cloud Discovery que são analisados. Por exemplo, você talvez queira excluir todas as informações provenientes de 127.0.0.1 ou do host local.  
  
Para criar uma exclusão:  
  
1.  No portal, no ícone de configurações, selecione **Configurações de Cloud Discovery**.  
  
2.  Clique na guia **Excluir entidades**.  
  
3.  Escolha a guia **Usuários excluídos** ou **Endereços IP excluídos** e clique no botão **Adicionar usuário** ou **Adicionar endereço IP**.  
  
4.  Adicione um alias do usuário ou endereço IP. É recomendável adicionar informações sobre por que o usuário ou o endereço IP foi excluído.  
  
     ![excluir usuário](./media/exclude-user.png "excluir usuário")  
  
## <a name="manage-continuous-reports"></a>Gerenciar relatórios contínuos  
Relatórios contínuos personalizados fornecem maior granularidade ao monitorar os dados de log do Cloud Discovery da sua organização. Ao criar relatórios personalizados, é possível filtrar por localizações geográficas, redes, sites ou unidades organizacionais específicas. Por padrão, somente os relatórios a seguir aparecem no seu seletor de relatório do Cloud Discovery:  
  
-  O **Relatório global** consolida todas as informações no portal de todas as fontes de dados incluídas em seus logs.  
  
- O **Relatório específico de fonte de dados** mostra apenas informações para uma fonte de dados específica.  
  
Para criar um novo relatório contínuo:  
  
1.  No portal, no ícone de configurações, selecione **Configurações de Cloud Discovery**.  
  
2.  Clique na guia **Gerenciar relatórios contínuos**.  
  
3.  Clique no botão **Criar relatório**.  
  
4.  Insira um nome de relatório.  
  
5.  Selecione as fontes de dados que você deseja incluir.  
  
6.  Defina os filtros que você deseja nos dados, os quais podem ser **Unidades Organizacionais**, **Marcas de endereço IP** ou **Intervalos de endereços IP**. Para obter mais informações sobre como trabalhar com marcas de endereço IP e intervalos de endereço IP, consulte [Organizar os dados de acordo com suas necessidades](ip-tags.md).  
  
    ![criar relatório contínuo personalizado](./media/create-custom-continuous-report.png) 

## <a name="deleting-cloud-discovery-data"></a>Excluindo dados do Cloud Discovery  
Há uma série de motivos pelos quais você pode desejar excluir seus dados do Cloud Discovery. É recomendável exclui-los nos seguintes casos:  
  
-   Se você carregou os arquivos de log manualmente e passou muito tempo antes de atualizar o sistema com novos arquivos de log e você não deseja dados antigos afetando os resultados.  
  
-   Quando você define uma nova exibição de dados personalizada, ela será aplicada somente aos novos dados daquele ponto em diante, então talvez você deseje apagar os dados antigos e carregar os arquivos de log novamente para permitir que a exibição de dados personalizada selecione eventos nos dados de arquivo de log.  
  
-   Se vários usuários ou endereços IP começaram a funcionar novamente recentemente após ficarem um período offline, sua atividade será identificada como anômala e você poderá obter muitas violações falso positivas.  
  
Para excluir os dados do Cloud Discovery:  
  
1.  No portal, no ícone de configurações, selecione **Configurações de Cloud Discovery**.  
  
2.  Clique na guia **Excluir dados**.  
  
     É importante ter certeza de que deseja excluir os dados antes de continuar. Isso não poderá ser desfeito e exclui **todos** os dados do Cloud Discovery no sistema.  
  
3.  Clique no botão **Excluir**.  
  
     ![excluir dados](./media/delete-data.png "excluir dados")  
  
   > [!NOTE]  
   >  O processo de exclusão leva alguns minutos e não é imediato.  




## <a name="see-also"></a>Veja também
 
[Criar instantâneo de relatórios do Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

[Configurar upload de log automático para relatórios contínuos](configure-automatic-log-upload-for-continuous-reports.md)

[Trabalhando com os dados do Cloud Discovery](working-with-cloud-discovery-data.md)


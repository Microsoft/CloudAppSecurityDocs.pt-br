---
title: Usar os dados do Cloud Discovery para detectar comportamentos de risco | Microsoft Docs
description: Este tópico fornece instruções sobre como trabalhar com os dados do Cloud Discovery, incluindo trabalhar com a pontuação de risco do aplicativo.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/22/2018
ms.topic: article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: cf94b290-b7ef-4fee-854e-c8ff8d11dea9
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 38125f5d229e240ee8651448364c0cfebb6b6f4e
ms.sourcegitcommit: 45311f2cafef79483e40d971a4c61c7673834d96
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2018
---
*Aplica-se ao: Microsoft Cloud App Security*


# <a name="discover"></a>Descobrir

## <a name="review-the-cloud-discovery-dashboard"></a>Examinar o Painel do Cloud Discovery

O painel do Cloud Discovery foi projetado para fornecer mais informações sobre como os aplicativos de nuvem estão sendo usados na sua organização. Ele fornece uma visão geral rápida de quais tipos de aplicativos estão sendo usados, os alertas abertos e os níveis de risco dos aplicativos na sua organização. Ele também mostra quem são os principais usuários do aplicativo e fornece um mapa do local da Matriz de Aplicativo. O Painel do Cloud Discovery tem muitas opções para filtrar os dados, para que você possa gerar exibições específicas dependendo do que mais lhe interessa, e gráficos de fácil compreensão para fornecer um panorama completo rápido.

![painel do Cloud Discovery](./media/cloud-discovery-dashboard.png)

A primeira coisa que você deve fazer para obter uma visão geral de seus aplicativos do Cloud Discovery é examinar o Painel do Cloud Discovery e analisar o seguinte:
 
1. Primeiro, examine o uso geral de aplicativos de nuvem em sua organização na visão geral de alto nível de uso.

2. Em seguida, aprofunde-se mais para ver quais são as principais categorias que estão sendo usadas na sua organização para cada um dos diferentes parâmetros de uso e quanto dessa utilização é de Aplicativos sancionados.

3. Vá ainda mais fundo e veja todos os aplicativos em uma categoria específica no widget de Aplicativos descobertos.

4. Você pode ver os principais usuários e endereços IP de origem para identificar quais usuários são os mais dominantes nos aplicativos de nuvem na sua organização.
5. Verifique como os aplicativos descobertos se espalham acordo com a localização geográfica (segundo a Matriz) no mapa de Matriz de Aplicativos.

6. Por fim, não se esqueça de examinar a pontuação de risco do aplicativo descoberto na **Visão geral de risco de aplicativos** e verificar o status de alertas de descoberta para ver quantos alertas abertos você deve investigar.
  
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


> [!NOTE]
> Todos os relatórios personalizados são limitados a no máximo 1 GB de dados não compactados. Se houver mais de 1 GB de dados, o primeiro GB de dados será exportado para o relatório.

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



 
## <a name="see-also"></a>Consulte Também  
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
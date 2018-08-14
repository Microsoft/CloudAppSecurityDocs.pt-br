---
title: Trabalhando com a pontuação de risco | Microsoft Docs
description: Este tópico fornece instruções sobre como usar e personalizar a pontuação de risco do aplicativo Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 8/8/2018
ms.topic: article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 9cb3594e-5007-48be-9b4f-e1d23355d86e
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 30e23682d99613d1bed0fa64f766bf668b60793d
ms.sourcegitcommit: 96f82381a17b89f9aef384f760ebf142695a6051
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39653240"
---
*Aplica-se ao: Microsoft Cloud App Security*


# <a name="working-with-the-risk-score"></a>Trabalhar com a pontuação de risco  

## <a name="the-cloud-app-catalog"></a>O catálogo de Aplicativos de Nuvem

O Catálogo de Aplicativos de Nuvem fornece uma visão completa do que o Cloud Discovery identifica. O Cloud Discovery analisa os logs de tráfego e os compara com o catálogo de mais de 16 mil aplicativos de nuvem do Microsoft Cloud App Security classificados e pontuados com base em mais de 70 fatores de risco, a fim de fornecer visibilidade contínua do uso da nuvem, TI de sombra e o risco que a TI de sombra representa para sua organização.
O **Catálogo de aplicativos de nuvem** classifica o risco para seus aplicativos de nuvem com base em certificações regulatórias, padrões da indústria e práticas recomendadas. Quatro processos complementares são executados no Catálogo de aplicativos de nuvem para mantê-lo atualizado:
1.  Extração de dados automatizada diretamente do aplicativo de nuvem (para atributos como conformidade com SOC 2, termos de serviço, URL de logon, política de privacidade e localização de HQ).
2.  Extração de dados avançada automatizada dos algoritmos do Cloud App Security (para atributos como cabeçalhos de segurança HTTP).
3.  Análise contínua da equipe de analistas de nuvem do Cloud App Security (para atributos como criptografia em repouso).
4.  Solicitações de revisão baseada no cliente, com base nas solicitações de envio de cliente para alterações no Catálogo de aplicativos de nuvem. Todas as solicitações são revisadas por nossa equipe de analistas de nuvem e atualizadas com base em suas descobertas.
  
![Catálogo de aplicativos de nuvem](./media/cloud-app-catalog.png)  

A demanda por unidades de negócios para aplicativos de nuvem como uma solução para suas necessidades de alteração está aumentando. O Catálogo de aplicativos de nuvem permite que você escolha cuidadosamente quais aplicativos se ajustam aos requisitos de segurança da sua organização e a necessidade de atualização com os padrões de segurança mais recentes, além de vulnerabilidades e violações. Por exemplo, se você quiser comparar os aplicativos CRM e verifique se eles estão adequadamente protegidos, você pode usar a página de catálogo do aplicativo de nuvem para filtrar aplicativos relevantes que você deseja: na página **Catálogo de aplicativos de nuvem**, em **Procurar por categoria**, selecione **CRM**. 

Em seguida, use os filtros **Avançado** e defina **Fator de risco de conformidade** > **SOC 2** é igual a **True**; **Fator de risco de conformidade** > **ISO 27001** é igual a **True**; **Fator de risco de segurança** > **Dados em criptografia rest** é igual a **True**; **Fator de risco de segurança** > **Dados em criptografia rest** é igual a **True**; **Fator de risco de segurança** > **trilha de auditoria de administrador** é igual a **True** e **Fator de risco de segurança** > **Trilha de auditoria de usuário** é igual a **True**.

![Filtros do Catálogo de aplicativos de nuvem](./media/cloud-app-catalog-filters.png)

Depois que os resultados são filtrados, você pode examinar os aplicativos relevantes e localizar o que melhor atenda às suas necessidades.

## <a name="cloud-app-catalog-filters"></a>Filtros do Catálogo de Aplicativos de nuvem

Há filtros básicos e avançados do Catálogo de aplicativos de nuvem. Para alcançar um filtro complexo, use a opção avançada que inclui todos os seguintes filtros:

- **Marcas de aplicativo**: marcas permitem personalizar o Catálogo de aplicativos de nuvem. 
  Você pode selecionar **Sancionado**, **Não sancionado** ou você pode criar marcas personalizadas para aplicativos. Essas marcas podem ser usadas como filtros para aprofundar-se nos tipos específicos de aplicativos que você deseja investigar. 
- **Aplicativos e domínios**: permite que você pesquise aplicativos específicos ou aplicativos usados em domínios específicos. 
- **Categorias**: o filtro de categorias, que está localizado à esquerda da página, permite pesquisar tipos de aplicativos de acordo com as categorias de aplicativo, por exemplo, aplicativos de rede Social, aplicativos de armazenamento em nuvem etc. Você pode selecionar várias categorias por vez ou uma única categoria e, em seguida, aplicar os filtros básicos e avançados sobre eles.
- **Fator de risco de conformidade**: permite que você pesquise padrões específicos, certificação e conformidade com os quais o aplicativo pode cumprir (HIPAA, ISO 27001, SOC 2, PCI-DSS etc.).
- **Fator de risco geral**: permite que você pesquise fatores de risco gerais, como a popularidade do consumidor, Data center local etc.
- **Pontuação de risco**: permite que você filtre aplicativos por classificação de risco para que você possa se concentrar, por exemplo, revisando somente os aplicativos muito arriscados.
- **Fator de risco de segurança**: habilita a filtragem com base em medidas específicas de segurança (como Criptografia em rest, autenticação multifator etc.).
- **Fator de risco legal**: permite filtrar com base em todos os regulamentos e políticas que estão em vigor para garantir a proteção de dados e a privacidade dos usuários do aplicativo, como o RGPD, o DMCA e a política de retenção de dados.
 
## <a name="suggesting-a-change"></a>Sugerir uma alteração

Se você encontrar um novo aplicativo no seu ambiente que ainda não foi classificado pelo Cloud App Security, um novo fator de risco ou uma atualização de pontuação ou dados de aplicativo que estão desatualizados, você pode solicitar uma análise do aplicativo:

**Para sugerir um novo aplicativo:**
1. Na parte superior da página **Aplicativos descobertos**, clique nos três pontos e, em seguida, selecione **Sugerir novo aplicativo**. 

   ![Sugerir um aplicativo no Cloud App Security](./media/suggest-new-app.png)

2. No pop-up **Sugerir novo aplicativo de nuvem**, preencha os detalhes sobre o novo aplicativo, incluindo o nome e o domínio do aplicativo. 

   ![Sugerir um pop-up de aplicativo para o Cloud App Security](./media/suggest-new-app-popup.png)

3. É recomendável marcar a caixa de seleção para permitir que os analistas do Cloud App Security entrem em contato com você caso mais informações sobre o aplicativo sejam necessárias e para que você possa ser atualizado quando a análise for concluída.

**Para atualizar um fator de risco, uma pontuação ou para atualizar dados de aplicativo:**

1. Na página **Catálogo de aplicativos de nuvem**, na linha de aplicativos que você deseja atualizar, clique nos três pontos no final da linha e selecione **Solicitar atualização de pontuação**.

   ![Solicitar atualização de pontuação](./media/request-score-update.png)

2. No pop-up **Sugerir um aperfeiçoamento**, selecione se você deseja solicitar uma atualização de pontuação, sugerir um novo fator de risco ou atualizar dados de aplicativo.

   ![sugestão e melhoria ao Cloud App Security](./media/suggest-improvement-popup.png)

3. É recomendável marcar a caixa de seleção para permitir que os analistas do Cloud App Security entrem em contato com você caso mais informações sobre o aplicativo sejam necessárias e para que você possa ser atualizado quando a análise for concluída.
 


## <a name="customizing-the-risk-score"></a>Personalizar a pontuação de risco

O Cloud Discovery oferece dados importantes com relação à credibilidade e à confiabilidade dos aplicativos de nuvem que são usados em todo o ambiente. No portal, cada aplicativo descoberto é exibido juntamente com uma pontuação total, representando a avaliação do Cloud App Security da maturidade desse aplicativo específico do uso para empresas. A pontuação total de qualquer aplicativo em particular é uma média ponderada de três subtotais relacionados a três subcategorias que o Cloud App Security considera ao avaliar a confiabilidade:  
  
-   **Geral** - essa categoria se refere a informações básicas sobre a empresa que produz o aplicativo, incluindo o seu domínio, ano de fundação e popularidade. Esses campos devem apresentar a estabilidade da empresa no nível mais básico.  
  
-   **Segurança** ‑ A categoria de segurança considera todos os padrões que lidam com a segurança física dos dados utilizados pelo aplicativo descoberto. Isso inclui campos como autenticação multifator, criptografia, classificação de dados e propriedade dos dados.  
  
-   **Conformidade** ‑ Essa categoria exibe quais padrões de conformidade de práticas recomendadas comuns são cumpridos pela empresa que produz o aplicativo. A lista de especificações inclui padrões como HIPAA, CSA e PCI-DSS.  

-  **Legal**: esta categoria exibe quais aplicativos têm quais regulamentos e políticas em vigor para garantir a proteção de dados e a privacidade dos usuários do aplicativo, como o RGPD, o DMCA e a política de retenção de dados.
  
Cada uma das categorias é composta por várias propriedades específicas. De acordo com o algoritmo pontuação do Cloud App Security, cada propriedade recebe uma pontuação preliminar entre 0 e 10, dependendo do valor. Valores True/False receberão 10 ou 0 da mesma forma, enquanto propriedades contínuas como a idade do domínio receberão um determinado valor dentro do espectro. A pontuação de cada propriedade é ponderada em relação a todos os outros campos existentes na categoria, para criar o subtotal da categoria. Se você encontrar um aplicativo sem pontuação, isso normalmente indicará um aplicativo cujas propriedades são desconhecidas e, portanto, sem pontuação.  
  
É importante reservar um minuto para examinar e modificar os pesos padrão dados para a configuração de pontuação do Cloud Discovery. Por padrão, todos os vários parâmetros avaliados recebem um peso igual. Se houver determinados parâmetros que são mais ou menos importantes para sua organização, será importante alterá-los da seguinte maneira:  
  
1. No portal, no ícone de configurações, selecione **Configurações de Cloud Discovery**.  
  
2. Em **Métrica de pontuação**, deslize a opção **Importância** para alterar o peso do campo ou da categoria de risco para **Ignorado**, **Baixo**, **Médio**, **Alto** ou **Muito Alto**.  
  
3. Além disso, você pode definir se determinados valores não estão disponíveis ou não são aplicáveis no cálculo da pontuação. Quando incluídos, valores N/A têm uma contribuição negativa para a pontuação calculada.  
  
   ![pontuação](./media/score.png "pontuação")  

Todas as informações necessárias para compreender como as classificações de risco do Cloud App Security se acumulam estão disponíveis no portal do Cloud App Security.
Para melhor compreender o peso de um fator de risco na categoria de risco específico, use o botão "i" à direita de cada nome de campo no perfil do aplicativo. Isso fornece informações sobre exatas como o Cloud App Security pontua um fator de risco específico. A pontuação é o valor do fator de risco em uma escala de 1 a 10 mais o seu peso na categoria de risco:

![cálculo de risco](./media/cac-weight.png)
  
Para compreender o peso de uma categoria risco na pontuação total do aplicativo, passe o mouse sobre a pontuação da categoria de risco:

![peso da categoria de risco](./media/risk-category-weight.png)

## <a name="overriding-the-risk-score"></a>Substituindo a pontuação de risco
Você pode substituir a pontuação de risco de um aplicativo sem alterar a maneira como ele é avaliado para que você obtenha resultados imediatos para sua organização. Por exemplo, se a pontuação de risco de um aplicativo LOB que você usa é 8 e ele é sancionado e incentivado por sua organização, você talvez queira alterar o risco de pontuação para 10. 

Para substituir a pontuação de risco, na tabela **Aplicativos descobertos** ou no **Catálogo de aplicativos de nuvem**, clique nos três pontos à direita de qualquer aplicativo e selecione **Substituir a pontuação de risco**.

![substituir a pontuação de risco do aplicativo descoberto do Cloud App Security](./media/override-risk-score.png)

Depois de atualizar a pontuação, você pode incluir observações do aplicativo para tornar sua justificativa de negócios para modificar esta pontuação de aplicativo clara para outros administradores. 

Você também pode adicionar observações para tornar a justificativa da alteração clara quando qualquer pessoa analisar o aplicativo.


 
## <a name="see-also"></a>Consulte Também  
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   

[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
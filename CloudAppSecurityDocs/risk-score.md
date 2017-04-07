---
title: "Trabalhando com a pontuação de risco | Microsoft Docs"
description: "Este tópico fornece instruções sobre como usar e personalizar a pontuação de risco do aplicativo Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/2/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 9cb3594e-5007-48be-9b4f-e1d23355d86e
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 2fcc085cc53d2d7580640022029b1a528bea416a
ms.sourcegitcommit: 661f4ce41262e8462c90fd2a4f1232e2154d5113
translationtype: HT
---
# <a name="working-with-the-risk-score"></a>Trabalhar com a pontuação de risco  

## <a name="the-cloud-app-catalog"></a>O catálogo de aplicativos de nuvem

Para entender melhor quais aplicativos de nuvem podem ser descobertos pelo Cloud Discovery do Cloud App Security, use o Catálogo de Aplicativos de Nuvem.

O Catálogo de Aplicativos de Nuvem contém mais de 14.000 aplicativos SaaS que podem ser exibidos (filtrados) com base no nome, domínio, pontuação de risco, categoria ou recursos de segurança disponíveis.

![acessar o catálogo de aplicativos de nuvem](./media/risk-cac-dropdown.png)

## <a name="discovery-requests"></a>Solicitações de descoberta

Pontuações de informações e de risco no Catálogo de aplicativos de nuvem são baseadas em várias fontes. A Microsoft se esforça para manter as informações atualizadas, mas não garante a exatidão de todas as fontes de dados. 

Entre em contato conosco se você acredita que as informações sobre um aplicativo estão desatualizadas.

-    Solicitar atualização de pontuação: caso queira que nossa equipe reavalie esse aplicativo de nuvem.
-    Relatar novos dados (por campo geral ou específico): se você acredita que as informações sobre o aplicativo estão desatualizadas.

![atualizar dados de risco](./media/risk-cac-feedback.png)

Além disso, incentivamos você a sugerir a adição de quaisquer aplicativos de nuvem que sua organização usa que atualmente não podem ser descobertos pelo Cloud Discovery.

![sugerir novos aplicativos](./media/risk-suggest-app.png)


## <a name="customizing-the-risk-score"></a>Personalizar a pontuação de risco

O Cloud Discovery oferece dados importantes com relação à credibilidade e à confiabilidade dos aplicativos de nuvem que são usados em todo o ambiente. No portal, cada aplicativo descoberto é exibido juntamente com uma pontuação total, representando a avaliação do Cloud App Security da maturidade desse aplicativo específico do uso para empresas. A pontuação total de qualquer aplicativo em particular é uma média ponderada de três subpontuações relacionadas a três subcategorias que o Cloud App Security considera ao avaliar a confiabilidade:  
  
-   **Geral** ‑ Essa categoria se refere a informações básicas sobre a empresa que produz o aplicativo, incluindo o seu domínio, ano de fundação e popularidade. Esses campos devem apresentar a estabilidade da empresa no nível mais básico.  
  
-   **Segurança** ‑ A categoria de segurança considera todos os padrões que lidam com a segurança física dos dados utilizados pelo aplicativo descoberto. Isso inclui campos como autenticação multifator, criptografia, classificação de dados e propriedade dos dados.  
  
-   **Conformidade** ‑ Essa categoria exibe quais padrões de conformidade de práticas recomendadas comuns são cumpridos pela empresa que produz o aplicativo. A lista de especificações inclui padrões como HIPAA, CSA e PCI-DSS.  
  
Cada uma das categorias é composta por várias propriedades específicas. De acordo com nosso algoritmo pontuação, cada propriedade recebe uma pontuação preliminar entre 0 e 10, dependendo do valor. Valores True/False receberão 10 ou 0 da mesma forma, enquanto propriedades contínuas como a idade do domínio receberão um determinado valor dentro do espectro. A pontuação de cada propriedade é ponderada em relação a todos os outros campos existentes na categoria, para criar a subpontuação da categoria. Se você encontrar um aplicativo sem pontuação, isso normalmente indicará um aplicativo cujas propriedades são desconhecidas e, portanto, sem pontuação.  
  
É importante reservar um minuto para examinar e modificar os pesos padrão dados para a configuração de pontuação do Cloud Discovery. Por padrão, todos os vários parâmetros avaliados recebem um peso igual. Se houver determinados parâmetros que são mais ou menos importantes para sua organização, será importante alterá-los da seguinte maneira:  
  
1.  No portal, no ícone de configurações, selecione **Configurações de Cloud Discovery**.  
  
2.  Em **Configurar métrica de pontuação**, deslize a **Importância** para alterar o peso do campo ou da categoria de risco para **Ignorado**, **Baixo**, **Médio**, **Alto** ou **Muito Alto**.  
  
3.  Além disso, você pode definir se determinados valores não estão disponíveis ou não são aplicáveis no cálculo da pontuação. Quando incluídos, valores N/A têm uma contribuição negativa para a pontuação calculada.  
  
     ![pontuação](./media/score.png "pontuação")  

Todas as informações necessárias para compreender como nossas classificações de risco se acumulam estão disponíveis no portal do Cloud App Security.
Para melhor compreender o peso de um fator de risco na categoria de risco específico, use o botão "i" à direita de cada nome de campo no perfil do aplicativo. Isso fornece informações sobre exatas como o Cloud App Security pontua um fator de risco específico. A pontuação é o valor do fator de risco em uma escala de 1 a 10 mais o seu peso na categoria de risco:

![cálculo de risco](./media/cac-weight.png)
  
Para compreender o peso de uma categoria risco na pontuação total do aplicativo, passe o mouse sobre a pontuação da categoria de risco:

![peso da categoria de risco](./media/risk-category-weight.png)


 
## <a name="see-also"></a>Veja também  
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
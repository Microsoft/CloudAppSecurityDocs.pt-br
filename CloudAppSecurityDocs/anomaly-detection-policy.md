---
title: "Política de detecção de anomalias | Microsoft Docs"
description: "Este tópico fornece uma descrição das Políticas de detecção de anomalias, bem como informações de referência sobre os blocos de construção de uma política de detecção de anomalias."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/6/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: ab9bc377-d2f5-4f4c-a419-f1728a15d1c7
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 002e0b82296162ee13fa378c4641cc8f21547237
ms.openlocfilehash: ca51d36a6d899124d3d4eb84ded1972ad9c8bab4


---

# <a name="anomaly-detection-policy"></a>Política de detecção de anomalias
Este artigo fornece detalhes de referência sobre as políticas, fornecendo explicações sobre cada tipo de política e os campos que podem ser configurados para cada política.  
 
O Cloud App Security tem um período inicial de assimilação de 7 dias, durante o qual ele não sinaliza nenhum novo usuários, atividade, dispositivos ou locais como anormais. Depois disso, cada sessão é comparada à atividade, quando os usuários estavam ativos, endereços IP, dispositivos, etc. detectados ao longo do mês anterior e à pontuação de risco dessas atividades. Use o controle deslizante de sensibilidade na política para definir a pontuação de risco mínimo que disparará os alertas. É recomendável usar o limite de sensibilidade padrão por usa semana ao criar uma política de anomalias, antes de alterá-lo de acordo com o número de alertas recebidos. O Cloud App Security enviará mais ou menos alertas para várias pontuações de risco ao alterar a sensibilidade.
  
![controle deslizante de sensibilidade](./media/sensitivity-slider.png)
## <a name="anomaly-detection-policy-reference"></a>Referência de política de detecção de anomalias  
Uma política de detecção de anomalias permite instalar e configurar o monitoramento contínuo da atividade de usuário quanto a anomalias comportamentais. As anomalias são detectadas pela verificação da atividade do usuário. O risco é avaliado observando mais de 30 indicadores de risco diferentes, agrupados em 6 fatores de risco. Com base nos resultados da política, os alertas de segurança são disparados.   
Cada política é composta pelas seguintes partes:  
  
-   Filtros de atividade – permitem verificar seletivamente somente a atividade de usuário filtrada quanto a anomalias.  
  
-   Fatores de risco – permitem que você escolha quais fatores de risco incluir ao avaliar o risco.  
  
-   Sensibilidade – permite definir quantos alertas a política deve disparar.  
  
### <a name="activity-filters"></a>Filtros de atividade  
Para obter uma lista dos filtros de atividade, consulte [Inserir descrição do link aqui](activity-filters.md).  
  
### <a name="risk-factors"></a>Fatores de risco  
Abaixo está uma lista dos fatores de risco que são considerados ao avaliar o risco da atividade do usuário. Todos os fatores de risco podem ser ativados ou desativados. Para cada fator de risco, há duas opções no campo **Aplicar a**, que determinam se ele deve ser incluído ao avaliar o risco da atividade do usuário:  
  
-   Todas as atividades monitoradas – incluir para todas as atividades do usuário que passam o filtro da atividade de política.  
  
-   Atividade selecionada – incluir para a atividade do usuário que passa os filtros de atividade de política e os filtros de atividade que aparecem sob esse fator de risco. Quando essa opção é selecionada, um seletor de filtro de atividade aparece sob o fator de risco, que funciona exatamente como o filtro de atividade da política.  
  
Cada fator de risco, quando incluído na avaliação de risco, tem seus próprios gatilhos que causam um aumento no risco avaliado da atividade do usuário:  
  
-   Falhas de logon – um grande número de falhas de logon ou uma atividade composta inteiramente de falhas de logon.  
  
-   Atividade administrativa ‑ Atividade administrativa executada por um usuário inesperado ou executada de um IP, ISP ou local novo ou que não foi usado por nenhum outro usuário na organização.  
  
-   Contas inativas ‑ Atividade executada por um usuário que não estava ativo por um longo tempo.  
  
-   Local ‑ Atividade realizada de um IP, ISP ou local que nunca foi usado por nenhum outro usuário, nunca foi usado por esse usuário específico, nunca foi usado ou foi usado apenas para falhas de logon no passado.  
  
-   Viagem impossível ‑ Atividade de locais remotos em um curto período de tempo.  
  
-   Agente de dispositivo e usuário ‑ Atividade realizada por um usuário usando um agente do usuário ou dispositivo que nunca foi usado por outro usuário, nunca foi usado por esse usuário específico ou nunca foi usado.  
  
### <a name="sensitivity"></a>Sensibilidade  
Há duas maneiras de controlar o número de alertas disparados pela política:  
  
-   Controle deslizante de sensibilidade – escolha quantos alertas disparar por 1.000 usuários por semana. Os alertas serão disparados das atividades com o maior risco.  
  
-   Limite diário de alertas – restringir o número de alertas gerados em um único dia.  
  
## <a name="see-also"></a>Veja também  
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  



<!--HONumber=Nov16_HO5-->



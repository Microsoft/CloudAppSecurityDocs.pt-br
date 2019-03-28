---
title: Investigar aplicativos de OAuth arriscados - Cloud App Security | Microsoft Docs
description: Esse artigo fornece informações sobre como investigar os aplicativos de OAuth arriscados no Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: barbkess
ms.date: 3/17/2019
ms.topic: tutorial
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 4118681e-362f-4b10-aa08-39691aa7800a
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 664e2ea3e6ce0414d3d55ca18a89e9bf9d889d94
ms.sourcegitcommit: fe4cd2174f6dc83811a2d484f079e8dfbac5d082
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/26/2019
ms.locfileid: "58476950"
---
# <a name="investigate-risky-oauth-apps"></a>Investigar aplicativos de OAuth arriscados

*Aplica-se a: Microsoft Cloud App Security*

O OAuth é um padrão aberto para autenticação e autorização baseada em token. O OAuth permite que as informações da conta do usuário sejam usadas por serviços de terceiros, sem expor a senha do usuário. O OAuth atua como um intermediário em nome do usuário, fornecendo o serviço com um token de acesso que autoriza o compartilhamento de informações de conta específicas.

Muitos aplicativos de terceiros, que podem ser instalados por usuários corporativos da sua organização, solicitam permissão para acessar dados e informações de usuário e entrar, em nome do usuário, em outros aplicativos de nuvem. Quando os usuários instalam esses aplicativos, eles geralmente clicam em **aceitar** sem examinar atentamente os detalhes na solicitação, incluindo a concessão de permissões para o aplicativo. Aceitar permissões de aplicativos de terceiros é um risco de segurança potencial para sua organização, portanto, o Microsoft Cloud App Security fornece a capacidade de investigar e monitorar as permissões de aplicativo concedidas pelos usuários. Esse artigo destina-se a ajudar você a investigar os aplicativos de OAuth em sua organização, e se concentrar nos aplicativos com maior probabilidade de levantar suspeitas. 

A nossa abordagem recomendada é investigar os aplicativos utilizando as habilidades e informações fornecidas no portal do Cloud App Security para filtrar aplicações com uma baixa probabilidade de ser arriscado e focar nos aplicativos suspeitos. 

## <a name="how-to-investigate"></a>Como investigar 

1.  No portal, acesse **Investigar** e, em seguida **Aplicativos OAuth**. É recomendável que você consulte usando um dos seguintes filtros: 
    - Selecione **Nível de permissão** em gravidade alta e **Uso da comunidade** em não é comum. Usando esse filtro, você pode se concentrar em aplicativos com um alto risco potencial, nos quais os usuários podem ter subestimado o risco. 
    - Em **Permissões**, selecione todas as opções que sejam particularmente arriscadas em um contexto específico, por exemplo, é possível selecionar todos os filtros que fornecem permissões para acesso por email, como **Acesso completo a todas as caixas de correio**  e, em seguida, examine a lista de aplicativos para certificar-se de que eles são todos os aplicativos que realmente precisam de acesso relacionado ao email. Isso pode ajudá-lo a investigar em um contexto específico e encontrar aplicativos que parecem legítimos, mas contêm permissões desnecessárias. Esses aplicativos são mais propensos a serem arriscados. 
    ![Aplicativo OAuth arriscado](./media/risky-oauth1.png) 
    - Use a **Consulta** que permite que você veja os **Aplicativos autorizados por usuários externos**. Ao usar esse filtro, você poderá encontrar aplicativos que talvez não estejam alinhados com os padrões de segurança da sua empresa. 
2.  Depois de filtrar seus aplicativos, você poderá se concentrar nos aplicativos nas consultas que parecem legítimos, mas que na verdade podem ser arriscados, tais como: 
    - Aplicativos que estejam **Autorizado por** um baixo número de usuários. Se você se concentrar nesses aplicativos, poderá procurar por aplicativos arriscados que foram autorizados por um usuário comprometido. 
    - Os aplicativos com permissões que não correspondem ao objetivo do aplicativo, por exemplo, um aplicativo de relógio com acesso total a todas as caixas de correio. 
    - Clique em cada aplicativo para abrir a gaveta de aplicativo e verifique se o aplicativo tem um nome, editor ou site suspeitos.  
    - Examine a lista de aplicativos e aplicativos de destino cuja data em **Última autorização** não seja recente. Pode ser que esses aplicativos não sejam mais necessários. 
    ![Aplicativo OAuth arriscado](./media/risky-oauth2.png) 
 
3. Clique no aplicativo para abrir a gaveta de aplicativo e clique no link em **Atividades relacionadas**. A página do Log de atividades filtrada para as atividades executadas pelo aplicativo será aberta. Lembre-se de que alguns aplicativos realizam atividades que foram registradas como executadas por um usuário. Essas atividades são filtradas automaticamente e excluídas dos resultados no Log de atividades. Para uma investigação adicional usando o log de atividades, confira [Log de atividades](activity-filters.md). 
4. Se um aplicativo parecer suspeito, recomendamos investigar o nome e o editor do aplicativo nas diferentes lojas de aplicativos. Concentre-se nos seguintes aplicativos, que podem levantar suspeitas: 
    - Aplicativos com um número baixo de downloads.
    - Aplicativos com uma classificação ou pontuação baixas ou comentários negativos.
    - Aplicativos com um editor ou website suspeito.
    - Aplicativos cuja última atualização não seja recente. Isso pode indicar um aplicativo que não tem mais suporte. 
    - Aplicativos com permissões irrelevantes. Isso pode indicar que um aplicativo é arriscado. 
5. Se o aplicativo ainda for suspeito, você poderá pesquisar online o editor e a URL do nome do aplicativo. 


 
## <a name="next-steps"></a>Próximas etapas
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md) 

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/) 
 

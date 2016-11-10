---
title: Atividades | Microsoft Docs
description: "Este tópico fornece uma lista de atividades, filtros e parâmetros de correspondência que podem ser aplicados às políticas de atividade."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: f3af2d25-9286-4e9b-b2ad-35653bec72ff
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed4ea71b24767d3602d40894d1cbac7447bcd8a2
ms.openlocfilehash: 401801da8a4439b3dc0cf5c2f150c72e169a6d16


---

# <a name="activities"></a>Atividades
Abaixo está uma lista de filtros de atividades que podem ser aplicados. A maioria dos filtros dá suporte a vários valores, bem como NOT, para fornecer uma ferramenta muito poderosa para a criação de políticas.  
  
-   Atividade – pesquisa apenas atividades específicas, por exemplo, todos os uploads de arquivos, logons de um novo dispositivo e logons com falha  
  
-   ID da Atividade ‑ Pesquisa apenas atividades específicas por sua ID. Esse filtro é muito útil quando você conecta MCAS ao seu SIEM (usando o agente SIEM) e deseja investigar ainda mais os alertas no portal do MCAS.  
  
-   Atividade administrativa – pesquisa apenas atividades administrativas.  
  
-   Atividade representada – pesquisa somente atividades que foram realizadas no nome de outro usuário.  
  
-   Aplicativo – pesquisa apenas atividades em aplicativos específicos.  
  
-   Data – a data em que a atividade ocorreu. O filtro dá suporte a datas antes/depois, bem como a intervalo de datas.  
  
-   Usuário – o usuário que executou a atividade. Para filtrar atividades sem nenhum usuário específico, você pode usar o operador 'não está definido'.  
  
     ![referência de atividade 1](./media/activity-ref1.png "activity ref1")  
  
-   Endereço IP – o endereço IP do qual a atividade foi executada.  
  
-   Categoria de IP – a categoria do endereço IP em que a atividade foi executada, por exemplo, todas as atividades do intervalo de endereços IP administrativo. Para obter mais informações sobre categorias de IP, consulte [Organizar os dados de acordo com suas necessidades](general-setup.md#IPtagsandRanges).  
  
-   Marca de IP ‑ A marca do endereço IP em que a atividade foi executada, por exemplo, todas as atividades de endereços IP de proxy anônimos. Para obter mais informações sobre marcas de IP, consulte [Organizar os dados de acordo com suas necessidades](general-setup.md#IPtagsandRanges).  
  
-   Local – o país do qual a atividade foi executada.  
  
-   ISP Registrado – o ISP do qual a atividade foi executada.  
  
     ![referência de política de atividade 2](./media/activity-policy-ref2.png "activity policy ref2")  
  
-   Tipo de dispositivo ‑ Pesquisa apenas atividades executadas usando um tipo de dispositivo específico, por exemplo, todas as atividades de dispositivos móveis.  
  
-   Agente do usuário – o agente do usuário do qual a atividade foi realizada.  
  
-   Marca de agente do usuário – Marca do agente do usuário interna, por exemplo, todas as atividades de sistemas operacionais desatualizados ou navegador desatualizado.  
  
-   Organização do usuário – A unidade organizacional do usuário que executou a atividade, por exemplo, todas as atividades realizadas pelos usuários de EMEA_marketing.  
  
- Objeto de destino – Permite que você selecione um arquivo específico. 

-   Grupo de usuários – grupos de usuários específicos que são importados automaticamente pelo MCAS do aplicativo de nuvem, por exemplo, todas as atividades realizadas por administradores do Office 365.  
  
-   Descrição – palavra-chave específica na descrição da atividade, por exemplo, todas as atividades que incluem a cadeia de caracteres **usuário** em sua descrição.  
  
-   Política correspondente – pesquisa atividades que corresponderam a uma política específica que foi definida no portal.  
  
     ![Referência de política de atividade 3](./media/activity-policy-ref3.png "Activity policy ref3")  
  
## <a name="activity-match-parameters"></a>Parâmetros de correspondência de atividade  
Especifique o número de repetições de atividade necessário para corresponder à política, por exemplo, definir uma política para alertar quando um usuário executa dez tentativas de logon sem sucesso em um período de dois minutos.  
A configuração padrão, **Parâmetros de correspondência de atividade**, gera uma correspondência para cada atividade que atende a todos os filtros de atividade.   
Usando **Atividade repetida**, você pode definir o número de atividades repetidas, a duração do período em que as atividades são contadas e até mesmo especificar que todas as atividades devem ser executadas pelo mesmo usuário e no mesmo aplicativo de nuvem.  
  
### <a name="actions"></a>Ações  
Notificações  
  
-   Alertas – os alertas podem ser disparados no sistema e propagados por email e mensagem de texto, com base no nível de gravidade.  
  
-   Notificação de email do usuário – mensagens de email podem ser personalizadas e serão enviadas a todos os proprietários do arquivo em violação.  
  
-   Copiar gerente – com base na integração de diretório do usuário, as notificações de email também podem ser enviadas para o gerente da pessoa que violar uma política.  
  
-   Notificar usuários adicionais – lista específica de endereços de email que receberão essas notificações.  
  
Ações de governança em aplicativos  
  
-   Ações granulares podem ser impostas por aplicativo, ações específicas variam dependendo da terminologia do aplicativo.  
  
-   Suspender usuário – suspende o usuário do aplicativo.  
  
-   Revogar senha – revoga a senha do usuário e o força a definir uma nova senha em seu próximo logon.  
  
     ![referência de política de atividade 6](./media/activity-policy-ref6.png "activity policy ref6")  
  
## <a name="see-also"></a>Veja também  
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Oct16_HO4-->



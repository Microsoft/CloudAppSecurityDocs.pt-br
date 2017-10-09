---
title: "Proteger a privacidade do usuário no Cloud App Security anonimizando dados | Microsoft Docs"
description: "Este artigo fornece informações sobre como anonimizar os nomes de usuário nos dados do Cloud Discovery."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 9/24/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: eb250ede-fede-4699-a08b-b8ea4b232f07
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: e6f9377942a969137fe766b4b146662d359b0224
ms.sourcegitcommit: 8759541301241e03784c5ac87b56986f22bd0561
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/28/2017
---
# <a name="cloud-discovery-data-anonymization"></a>Anonimização de dados do Cloud Discovery

A anonimização de dados do Cloud Discovery permite proteger a privacidade do usuário. Após o log de dados ser carregado no portal do Cloud App Security, o log é limpo e todas as informações de nome de usuário são substituídas por nomes de usuário criptografados. Dessa forma, todas as atividades na nuvem são mantidas anônimas. Quando necessário, para uma investigação de segurança específica (por exemplo, devido a uma violação de segurança ou atividade de usuário suspeita), os administradores podem resolver o nome de usuário real. Se um administrador tiver algum motivo para suspeitar de um usuário específico, ele também poderá pesquisar o nome de usuário criptografado de um nome de usuário conhecido e começar a investigação usando o nome de usuário criptografado. Toda conversão de nome de usuário é auditada no **Log de governança** do portal.

Pontos principais:
-   Nenhuma informação particular é armazenada nem exibida. Somente informações criptografadas.
-   Dados particulares são criptografados usando AES-128 com uma chave dedicada por locatário.
-   A resolução de nomes de usuário é realizada ad hoc e por nome de usuário decifrando um determinado nome de usuário criptografado.


Como funciona a anonimização de dados:

1.  Há três maneiras de aplicar a anonimização de dados: 
    
    - Você pode definir que os dados de um arquivo de log específico sejam anonimizados [criando um novo relatório de instantâneo](create-snapshot-cloud-discovery-reports.md) e selecionando **Anonimizar informações particulares**.
 ![Anonimizar dados de instantâneo](./media/anonymize-log.png)

    - Você pode definir a anonimização dos dados de um [upload automatizado para uma nova fonte de dados](configure-automatic-log-upload-for-continuous-reports.md) selecionando **Anonimizar informações particulares** ao adicionar a nova fonte de dados.  
 ![Anonimizar dados de log](./media/anonymize-autolog.png)

    - Você pode definir no Cloud App Security que o padrão seja anonimizar todos os dados de relatórios de instantâneos de arquivos de log carregados e de relatórios contínuos dos coletores de log da seguinte maneira:
     
        1. Na engrenagem Configurações, selecione **Configurações do Cloud Discovery**.
     
        2. Na guia Anonimização, para anonimizar os nomes de usuário por padrão, selecione **Anonimizar informações particulares por padrão em novos relatórios e fontes de dados**.

        3. Em Chave de criptografia, selecione se deseja **Usar a chave dedicada gerada para seu portal** ou **Usar uma chave personalizada**. Se você **Usar uma chave personalizada**, digite uma chave de criptografia UTF8 de 16 bytes.
        4. Clique em **Salvar**.
  ![Anonimização](./media/anonymizer1.png)
  

2.  Quando a Anonimização está selecionada, o Cloud App Security analisa o log de tráfego e extrai atributos específicos de dados.
3.  O Cloud App Security substitui o nome de usuário por um nome de usuário criptografado.
4.  Em seguida, ele analisa os dados de uso de nuvem e gera relatórios do Cloud Discovery com base nos dados anonimizados.
 ![Painel Anonimizar Cloud Discovery](./media/anonymize-dashboard.png)
 

5.  Para uma investigação específica, como ao investigar um alerta de uso anômalo, você poderá resolver o nome de usuário específico no portal e fornecer uma justificativa comercial. Esta página também pode ser usada para pesquisar o nome de usuário criptografado de um nome de usuário conhecido. 

    1. Na engrenagem Configurações, selecione **Configurações do Cloud Discovery**.
    2. Na guia **Anonimização**, em **Anonimizar e resolver nomes de usuário**, insira uma justificativa explicando porque você está executando a resolução.
    3. Em **Inserir nome de usuário a ser resolvido**, selecione **De anonimizado** e insira o nome de usuário anonimizado ou selecione **Para anonimizar** e insira o nome de usuário original a ser resolvido. Clique em **Resolver**. 
![Anonimização](./media/anonymizer.png)

6.  A ação é auditada no **Log de governança** do portal. 
![Anonimização](./media/anonymize-gov-log.png)




  
      
## <a name="see-also"></a>Veja também  
[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
    
      
  

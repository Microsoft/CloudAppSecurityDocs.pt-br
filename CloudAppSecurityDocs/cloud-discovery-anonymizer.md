---
title: Anonimizar dados de usuário no Cloud App Security
description: Este artigo fornece informações sobre como proteger a privacidade do usuário anonimizando os nomes de usuários nos dados do Cloud Discovery.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/10/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: eb250ede-fede-4699-a08b-b8ea4b232f07
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: b1eceacb47e8339bb0b7162d27f13866188d10e7
ms.sourcegitcommit: b86c3afd1093fbc825fec5ba4103e3a95f65758e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53176426"
---
# <a name="cloud-discovery-data-anonymization"></a>Anonimização de dados do Cloud Discovery

*Aplica-se a: Microsoft Cloud App Security*

A anonimização de dados do Cloud Discovery permite proteger a privacidade do usuário. Após o log de dados ser carregado no portal do Microsoft Cloud App Security, o log é limpo e todas as informações de nome de usuário são substituídas por nomes de usuário criptografados. Dessa forma, todas as atividades na nuvem são mantidas anônimas. Quando necessário, para uma investigação de segurança específica (por exemplo, devido a uma violação de segurança ou atividade de usuário suspeita), os administradores podem resolver o nome de usuário real. Se um administrador tiver algum motivo para suspeitar de um usuário específico, ele também poderá pesquisar o nome de usuário criptografado de um nome de usuário conhecido e começar a investigação usando o nome de usuário criptografado. Toda conversão de nome de usuário é auditada no **Log de governança** do portal.

Pontos principais:
-   Nenhuma informação particular é armazenada nem exibida. Somente informações criptografadas.
-   Dados particulares são criptografados usando AES-128 com uma chave dedicada por locatário.
-   A resolução de nomes de usuário é realizada ad hoc e por nome de usuário decifrando um determinado nome de usuário criptografado.


## <a name="how-data-anonymization-works"></a>Como funciona a anonimização de dados

1. Há três maneiras de aplicar a anonimização de dados: 
    
   - Você pode definir que os dados de um arquivo de log específico sejam anonimizados [criando um novo relatório de instantâneo](create-snapshot-cloud-discovery-reports.md) e selecionando **Anonimizar informações particulares**.

     ![Torne anônimos dados de instantâneo](./media/anonymize-log.png)

   - Você pode definir a anonimização dos dados de um [upload automatizado para uma nova fonte de dados](configure-automatic-log-upload-for-continuous-reports.md) selecionando **Anonimizar informações particulares** ao adicionar a nova fonte de dados.  
  
     ![Torne anônimos dados de log](./media/anonymize-autolog.png)

   - Você pode definir no Cloud App Security que o padrão seja anonimizar todos os dados de relatórios de instantâneos de arquivos de log carregados e de relatórios contínuos dos coletores de log da seguinte maneira:
     
     1. Na engrenagem Configurações, selecione **Configurações do Cloud Discovery**.
     
     2. Na guia Anonimização, para anonimizar os nomes de usuário por padrão, selecione **Anonimizar informações particulares por padrão em novos relatórios e fontes de dados**. Você pode selecionar **Anonimizar as informações do computador por padrão no relatório 'Usuários do Ponto de Extremidade do Win10'**.

     3. Em Chave de criptografia, selecione se deseja **Usar a chave dedicada gerada para seu portal** ou **Usar uma chave personalizada**. Se você **Usar uma chave personalizada**, digite uma chave de criptografia UTF8 de 16 bytes.
     4. Clique em **Salvar**.
 
        ![Anonimização](./media/anonymizer1.png)
  

2. Quando a Anonimização está selecionada, o Cloud App Security analisa o log de tráfego e extrai atributos específicos de dados.
3. O Cloud App Security substitui o nome de usuário por um nome de usuário criptografado.
4. Em seguida, ele analisa os dados de uso de nuvem e gera relatórios do Cloud Discovery com base nos dados anonimizados.
 
   ![Torne anônimo o painel do Cloud Discovery](./media/anonymize-dashboard.png)
 
5. Para uma investigação específica, como ao investigar um alerta de uso anômalo, você poderá resolver o nome de usuário específico no portal e fornecer uma justificativa comercial. 
   Esta página também pode ser usada para pesquisar o nome de usuário criptografado de um nome de usuário conhecido. 

   1. Na engrenagem Configurações, selecione **Configurações do Cloud Discovery**.
   2. Na guia **Anonimização**, em **Anonimizar e resolver nomes de usuário**, insira uma justificativa explicando porque você está executando a resolução.
   3. Em **Inserir nome de usuário a ser resolvido**, selecione **De anonimizado** e insira o nome de usuário anonimizado ou selecione **Para anonimizar** e insira o nome de usuário original a ser resolvido. Clique em **Resolver**. 

   ![Anonimização](./media/anonymizer.png)

6. A ação é auditada no **Log de governança** do portal. 

    ![Anonimização](./media/anonymize-gov-log.png)




  
      
## <a name="next-steps"></a>Próximas etapas 
[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)   

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/)  
    
      
  

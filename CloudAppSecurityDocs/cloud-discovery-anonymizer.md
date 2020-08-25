---
title: Anonimizar dados de usuário no Cloud App Security
description: Este artigo fornece informações sobre como proteger a privacidade do usuário anonimizando os nomes de usuários nos dados do Cloud Discovery.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 04/20/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 44bc98ec887b8a2d601961a65115b7d7a50f3128
ms.sourcegitcommit: 29a8e66c665f51d831516924ae4d9d8047b39276
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88781218"
---
# <a name="cloud-discovery-data-anonymization"></a>Anonimização de dados do Cloud Discovery

*Aplica-se a: Microsoft Cloud App Security*

A anonimização de dados do Cloud Discovery permite proteger a privacidade do usuário. Após o log de dados ser carregado no portal do Microsoft Cloud App Security, o log é limpo e todas as informações de nome de usuário são substituídas por nomes de usuário criptografados. Dessa forma, todas as atividades na nuvem são mantidas anônimas. Quando necessário, para uma investigação de segurança específica (por exemplo, devido a uma violação de segurança ou atividade de usuário suspeita), os administradores podem resolver o nome de usuário real. Se um administrador tiver algum motivo para suspeitar de um usuário específico, ele também poderá pesquisar o nome de usuário criptografado de um nome de usuário conhecido e começar a investigação usando o nome de usuário criptografado. Cada conversão de nome de usuário é auditada no **log de governança**do Portal.

Pontos principais:

- Nenhuma informação particular é armazenada nem exibida. Somente informações criptografadas.
- Dados particulares são criptografados usando AES-128 com uma chave dedicada por locatário.
- A resolução de nomes de usuário é realizada ad hoc e por nome de usuário decifrando um determinado nome de usuário criptografado.

## <a name="how-data-anonymization-works"></a>Como funciona a anonimização de dados

1. Há três maneiras de aplicar a anonimização de dados:

    - Você pode definir que os dados de um arquivo de log específico sejam anonimizados [criando um novo relatório de instantâneo](create-snapshot-cloud-discovery-reports.md) e selecionando **Anonimizar informações particulares**.  
    ![Anonimizar dados de instantâneo](media/anonymize-log.png)

    - Você pode definir a anonimização dos dados de um [upload automatizado para uma nova fonte de dados](configure-automatic-log-upload-for-continuous-reports.md) selecionando **Anonimizar informações particulares** ao adicionar a nova fonte de dados.  
    ![Anonimizar dados de log](media/anonymize-autolog.png)

    - Você pode definir no Cloud App Security que o padrão seja anonimizar todos os dados de relatórios de instantâneos de arquivos de log carregados e de relatórios contínuos dos coletores de log da seguinte maneira:

    1. Na engrenagem configurações, selecione **configurações de Cloud Discovery**.

    2. Na guia Anonimização, para anonimizar os nomes de dados por padrão, escolha **Anonimizar informações privadas por padrão em novos relatórios e fontes de dados**. Você também pode selecionar **anônimos informações do computador por padrão no relatório ' usuários do ponto de extremidade Win10 '**.
    3. Clique em **Salvar**.

    ![Página de configurações de anonimato](media/anonymizer1.png)

2. Quando a Anonimização está selecionada, o Cloud App Security analisa o log de tráfego e extrai atributos específicos de dados.
3. O Cloud App Security substitui o nome de usuário por um nome de usuário criptografado.
4. Em seguida, ele analisa os dados de uso de nuvem e gera relatórios do Cloud Discovery com base nos dados anonimizados.

    ![Torne anônimo o painel do Cloud Discovery](media/anonymize-dashboard.png)

5. Para uma investigação específica, como uma investigação de um alerta de uso anormal, você pode resolver o nome de usuário específico no portal e fornecer uma justificativa de negócios.

    > [!NOTE]
    > As etapas a seguir também funcionam para nomes de computador na guia **computadores** .

    **Para resolver um único nome de usuário**

    1. Clique nos três pontos no final da linha do usuário que você deseja resolver e selecione **desanônimos do usuário**.

        ![Tornar a tabela de usuário anônimo](media/anonymize-user-table.png)

    1. No pop-up, insira a justificativa para resolver o nome de usuário e clique em **resolver**. Na linha relevante, o nome de usuário resolvido é exibido.

        > [!NOTE]
        > Esta ação é auditada.

        ![Tornar anônimo resolver pop-up](media/anonymize-resolve-dialog.png)

    A seguinte maneira alternativa de resolver nomes de usuário únicos também pode ser usada para pesquisar o nome de usu Encrypted de um nome de usuário conhecido.

    1. Na engrenagem configurações, selecione **configurações de Cloud Discovery**.

    1. Na guia **Anonimização**, em **Anonimizar e resolver nomes de usuário**, insira uma justificativa explicando porque você está executando a resolução.
    1. Em **Inserir nome de usuário a ser resolvido**, selecione **De anonimizado** e insira o nome de usuário anonimizado ou selecione **Para anonimizar** e insira o nome de usuário original a ser resolvido. Clique em **Resolver**.

        ![Resolver pop-up de anonimato](media/anonymizer.png)

    **Para resolver vários nomes de acessações**

    1. Marque as caixas de seleção que aparecem quando você passa o mouse sobre os ícones de usuário pelos usuários que você deseja resolver ou, no canto superior esquerdo, marque a caixa de seleção **seleção em massa** .

        ![Tornar anônimo a resolução em massa](media/anonymize-bulk-resolve.png)

    1. Clique em **desanônimoize o usuário**.
    1. No pop-up, insira a justificativa para resolver o nome de usuário e clique em **resolver**. Nas linhas relevantes, os nomes de userresolvedos são exibidos.

        > [!NOTE]
        > Esta ação é auditada.

        ![Tornar anônimo resolver pop-up](media/anonymize-resolve-dialog.png)

6. A ação é auditada no **log de governança**do Portal.

    ![Ação de anonimato no log de governança](media/anonymize-gov-log.png)

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]

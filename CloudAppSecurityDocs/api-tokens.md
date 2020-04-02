---
title: Gerenciamento de tokens de API no Cloud App Security
description: Este artigo fornece informações sobre como gerar tokens de API para Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: fcde5b08363a790cf18cf873c0dfde183ec6ddcd
ms.sourcegitcommit: 9165220189564860d74a255a5c0be1ed362ba152
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80522566"
---
# <a name="api-tokens"></a>Tokens de API

*Aplica-se a: Microsoft Cloud App Security*

A API Microsoft Cloud App Security fornece acesso programático a Cloud App Security por meio de pontos de extremidade da API REST. Os aplicativos podem usar a API para executar operações de leitura e atualização em Cloud App Security dados e objetos. Por exemplo, a API Cloud App Security dá suporte às seguintes operações comuns para um objeto de usuário:

- Carregar arquivos de log para Cloud Discovery
- Gerar scripts de bloco
- Listar atividades, alertas e relatórios de política
- Ignorar ou resolver alertas

Para ver a documentação completa da API, no portal do Cloud App Security, acesse ajuda > **documentação da API**.

Para acessar a API, você precisa criar um token de API e usá-lo em seu software para se conectar à API de Cloud App Security.

A guia tokens de API permite que você o ajude a gerenciar todos os tokens de API do seu locatário.

## <a name="generate-a-token"></a>Gerar um token

1. No menu **configurações** , selecione **extensões de segurança** e **tokens de API**.

2. Clique no ícone de adição, **gere novo token** e forneça um nome para identificar o token no futuro e clique em **Avançar**.
  ![Cloud App Security gera um token de API](media/api-token-gen.png)

3. Copie o valor do token e salve-o em algum lugar para recuperação – se você perder, será necessário regenerar o token. O token tem os privilégios do usuário que o emitiu. Por exemplo, um leitor de segurança não pode emitir um token que pode alterar dados.

4. Você pode filtrar os tokens por status: ativo, inativo ou gerado.

    - Gerados são tokens que nunca foram usados.
    - Ativo são tokens que foram gerados e foram usados nos últimos sete dias.
    - Inativos foram usados, mas não havia nenhuma atividade nos últimos sete dias.

5. Depois de gerar um novo token, você receberá uma nova URL a ser usada para acessar o portal de Cloud App Security.

    ![Token de API Cloud App Security](media/generate-api-token.png)

    A URL do portal genérico continua a funcionar, mas é consideravelmente mais lenta do que a URL personalizada fornecida com o token. Se você esquecer a URL a qualquer momento, poderá exibi-la indo para o **?** no menu e selecionando **sobre**.

> [!NOTE]
> Se você estiver usando Azure Active Directory Privileged Identity Management ativação de função, seu token de API só será eficaz quando a função for ativada. Para obter mais informações, consulte [Ativar minhas funções do Azure AD no PIM](https://docs.microsoft.com/azure/active-directory/privileged-identity-management/pim-how-to-activate-role).

## <a name="api-token-management"></a>Gerenciamento de token de API

A página token de API inclui uma tabela de todos os tokens de API que foram gerados.

Administradores completos veem todos os tokens gerados para este locatário. Outros usuários veem apenas os tokens gerados por eles mesmos.

A tabela fornece detalhes sobre quando o token foi gerado e quando foi usado pela última vez e permite revogar o token.

Depois que um token é revogado, ele é removido da tabela e o software que o estava usando falha ao fazer chamadas à API até que um novo token seja fornecido.

> [!NOTE]
>
> - Os conectores SIEM e coletores de log também usam tokens de API. Esses tokens devem ser gerenciados nas seções coletores de logs e agente SIEM e não aparecem nesta tabela.
> - Os tokens de API de usuários desprovisionados são mantidos em Cloud App Security, mas não podem ser usados. Qualquer tentativa de usá-los resultará em uma resposta de permissão negada. No entanto, recomendamos que esses tokens sejam revogados na página **tokens de API** .

## <a name="next-steps"></a>{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}

> [!div class="nextstepaction"]
> [Solucionando problemas de integração do SIEM](troubleshooting-siem.md)

[!INCLUDE [Open support ticket](includes/support.md)]

## <a name="check-out-this-video"></a>Confira este vídeo!

[Microsoft Cloud App Security – APIs REST e tokens](https://channel9.msdn.com/Shows/Microsoft-Security/Microsoft-Cloud-App-Security--REST-APIs-and-Tokens)

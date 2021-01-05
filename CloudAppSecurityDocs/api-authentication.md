---
title: Gerenciando tokens de API
description: Este artigo fornece informações sobre como gerar e gerenciar tokens de API para Cloud App Security.
ms.date: 03/27/2020
ms.topic: reference
ms.openlocfilehash: cd577565cb67b51dd93c649e69cd00a551736789
ms.sourcegitcommit: 421870fac566642809eff0a545ec1981be1c9165
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/20/2020
ms.locfileid: "97705875"
---
# <a name="managing-api-tokens"></a>Gerenciando tokens de API

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Para acessar a API de Cloud App Security, você precisa criar um token de API e usá-lo em seu software para se conectar à API. Esse token será incluído no cabeçalho quando Cloud App Security fizer solicitações de API.

A guia tokens de API permite que você ajude a gerenciar todos os tokens de API do seu locatário.

## <a name="generate-a-token"></a>Gerar um token

1. No menu **Configurações**, selecione **Extensões de segurança** e, em seguida, **Tokens de API**.

2. Clique no ícone de adição, **Gerar novo token** e forneça um nome para identificar o token no futuro e, em seguida, clique em **Avançar**.

    ![O Cloud App Security gera token API](media/api-token-gen.png)

3. Copie o valor do token e salve-o em algum lugar para recuperação – se você perdê-lo, será necessário gerar o token novamente. O token tem os privilégios do usuário que o emitiu. Por exemplo, um leitor de segurança não pode emitir um token que possa alterar os dados.

4. Você pode filtrar os tokens de status: Ativo, Inativo ou Gerado.

    - **Gerado:** Tokens que nunca foram usados.
    - **Ativo:** Tokens que foram gerados e foram usados nos últimos sete dias.
    - **Inativo:** Tokens que foram usados, mas não havia nenhuma atividade nos últimos sete dias.

5. Depois de gerar um novo token, você receberá uma nova URL a ser usada para acessar o portal do Cloud App Security.

    ![Token de API do Cloud App Security](media/generate-api-token.png)

    A URL genérica do portal continuará a funcionar, mas será consideravelmente mais lenta do que a URL personalizada fornecida com o token. Se você esquecer a URL a qualquer momento, você poderá exibi-la indo até o ícone **?** no menu e selecionando **Sobre**.

## <a name="api-token-management"></a>Gerenciamento de token de API

A página de token de API inclui uma tabela de todos os tokens de API que foram gerados.

Administradores completos veem todos os tokens gerados para este locatário. Outros usuários veem apenas os tokens que eles mesmos geraram.

A tabela fornece detalhes sobre quando o token foi gerado e quando ele foi usado pela última vez e permite revogar o token.

Depois que um token é revogado, ele é removido da tabela e o software que ele estava usando não consegue fazer chamadas à API até que um novo token seja fornecido.

> [!NOTE]
>
> - Conectores do SIEM e coletores de log também usam tokens de API. Esses tokens devem ser gerenciados das seções de agente SIEM e coletores de log e não aparecem nessa tabela.
> - Os tokens de API de usuários desprovisionados são mantidos em Cloud App Security, mas não podem ser usados. Qualquer tentativa de usá-los resultará em uma resposta de permissão negada. No entanto, recomendamos que esses tokens sejam revogados na página **tokens de API** .

[!INCLUDE [Open support ticket](includes/support.md)]

## <a name="check-out-this-video"></a>Confira este vídeo!

[Microsoft Cloud App Security – APIs REST e tokens](https://channel9.msdn.com/Shows/Microsoft-Security/Microsoft-Cloud-App-Security--REST-APIs-and-Tokens)

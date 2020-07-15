---
title: Gerenciamento de token de API no Cloud App Security
description: Este artigo fornece informações sobre como gerar tokens de API para o Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 07/14/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 81c44eb4527b19e1f3f42929028791f1ae48715d
ms.sourcegitcommit: b71546236cb97c0a22d0e82742a167f31555b275
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86308234"
---
# <a name="api-tokens"></a>Tokens de API

*Aplica-se a: Microsoft Cloud App Security*

A API do Microsoft Cloud App Security fornece acesso programático ao Cloud App Security por meio de pontos de extremidade API REST. Aplicativos podem usar a API para realizar operações de leitura e atualização nos dados e objetos do Cloud App Security. Por exemplo, a API de segurança do aplicativo de nuvem dá suporte às seguintes operações comuns para um objeto de usuário:

- Carregar arquivos de log para o Cloud Discovery
- Gerar scripts de bloqueio
- Listar atividades, alertas e relatórios da política
- Descartar ou resolver alertas

Para obter mais informações sobre como usar nossa API, consulte [Cloud app Security API REST](api-introduction.md).

Para acessar a API, você precisa criar um token de API e usá-lo em seu software para conectar-se à API do Cloud App Security.

A guia tokens de API permite que você ajude a gerenciar todos os tokens de API do seu locatário.

## <a name="generate-a-token"></a>Gerar um token

1. No menu **Configurações**, selecione **Extensões de segurança** e, em seguida, **Tokens de API**.

2. Clique no ícone de adição, **Gerar novo token** e forneça um nome para identificar o token no futuro e, em seguida, clique em **Avançar**.
  ![O Cloud App Security gera token API](media/api-token-gen.png)

3. Copie o valor do token e salve-o em algum lugar para recuperação – se você perdê-lo, será necessário gerar o token novamente. O token tem os privilégios do usuário que o emitiu. Por exemplo, um leitor de segurança não pode emitir um token que possa alterar os dados.

4. Você pode filtrar os tokens de status: Ativo, Inativo ou Gerado.

    - Tokens com status Gerado são tokens que nunca foram usados.
    - Tokens com status Ativo são tokens que foram gerados e foram usados nos últimos sete dias.
    - Tokens com o status Inativo foram usados, mas não houve atividade nos últimos sete dias.

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

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [API REST do Cloud App Security](api-introduction.md)

> [!div class="nextstepaction"]
> [Solução de problemas de integração de SIEM](troubleshooting-siem.md)

[!INCLUDE [Open support ticket](includes/support.md)]

## <a name="check-out-this-video"></a>Confira este vídeo!

[Microsoft Cloud App Security – APIs REST e tokens](https://channel9.msdn.com/Shows/Microsoft-Security/Microsoft-Cloud-App-Security--REST-APIs-and-Tokens)

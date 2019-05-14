---
title: Gerenciamento de token de API no Cloud App Security
description: Este artigo fornece informações sobre como gerar tokens de API para o Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: rkarlin
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 4f5e6b1e-6b2c-4358-98f0-945e2993d5fe
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: d474035f1d47e7eb6a751bf79c4e3f948638d7b5
ms.sourcegitcommit: 9f0c562322394a3dfac7f1d84286e673276a28b1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65567506"
---
# <a name="api-tokens"></a>Tokens de API

*Aplica-se a: Microsoft Cloud App Security*

A API do Microsoft Cloud App Security fornece acesso programático ao Cloud App Security por meio de pontos de extremidade API REST. Aplicativos podem usar a API para realizar operações de leitura e atualização nos dados e objetos do Cloud App Security. Por exemplo, a API de segurança do aplicativo de nuvem dá suporte às seguintes operações comuns para um objeto de usuário:

- Carregar arquivos de log para o Cloud Discovery
- Gerar scripts de bloqueio
- Listar atividades, alertas e relatórios da política
- Descartar ou resolver alertas

Para ver a documentação completa da API no portal do Cloud App Security, acesse Ajuda > **Documentação da API**.

Para acessar a API, você precisa criar um token de API e usá-lo em seu software para conectar-se à API do Cloud App Security.

A guia tokens de API permite que você ajude a gerenciar todos os tokens de API do seu locatário. 


## <a name="generate-a-token"></a>Gerar um token

1. No menu **Configurações**, selecione **Extensões de segurança** e, em seguida, **Tokens de API**.

2. Clique no ícone de adição, **Gerar novo token** e forneça um nome para identificar o token no futuro e, em seguida, clique em **Avançar**.
   ![O Cloud App Security gera token API](./media/api-token-gen.png)

3. Copie o valor do token e salve-o em algum lugar para recuperação – se você perdê-lo, será necessário gerar o token novamente. O token tem os privilégios do usuário que o emitiu. Por exemplo, um leitor de segurança não pode emitir um token que possa alterar os dados.

4. Filtre os tokens por status: Ativo, Inativo ou Gerado. 

   - Tokens com status Gerado são tokens que nunca foram usados. 
   - Tokens com status Ativo são tokens que foram gerados e foram usados nos últimos sete dias. 
   - Tokens com o status Inativo foram usados, mas não houve atividade nos últimos sete dias.
5. Depois de gerar um novo token, você receberá uma nova URL a ser usada para acessar o portal do Cloud App Security. 

   ![Token de API do Cloud App Security](./media/generate-api-token.png)

A URL genérica do portal continuará a funcionar, mas será consideravelmente mais lenta do que a URL personalizada fornecida com o token. Se você esquecer a URL a qualquer momento, você poderá exibi-la indo até o ícone **?** no menu e selecionando **Sobre**.

## <a name="api-token-management"></a>Gerenciamento de token de API

A página de token de API inclui uma tabela de todos os tokens de API que foram gerados.

Administradores completos veem todos os tokens gerados para este locatário. Outros usuários veem apenas os tokens que eles mesmos geraram.

A tabela fornece detalhes sobre quando o token foi gerado e quando ele foi usado pela última vez e permite revogar o token. 

Depois que um token é revogado, ele é removido da tabela e o software que ele estava usando não consegue fazer chamadas à API até que um novo token seja fornecido. 

> [!NOTE]
> Conectores do SIEM e coletores de log também usam tokens de API. Esses tokens devem ser gerenciados das seções de agente SIEM e coletores de log e não aparecem nessa tabela. 





## <a name="next-steps"></a>Próximas etapas
[Solução de problemas da integração SIEM](troubleshooting-siem.md)   

[Os clientes Premier também podem criar uma nova solicitação de suporte diretamente no Portal Premier.](https://premier.microsoft.com/)  

## <a name="check-out-this-video"></a>Confira este vídeo!
[Microsoft Cloud App Security – API REST e Tokens](https://channel9.msdn.com/Shows/Microsoft-Security/Microsoft-Cloud-App-Security--REST-APIs-and-Tokens)  

---
title: Gerenciamento de token de API no Cloud App Security | Microsoft Docs
description: "Este tópico fornece informações sobre a geração de tokens de API para Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 7/1/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 4f5e6b1e-6b2c-4358-98f0-945e2993d5fe
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 291a9bf9a0c45a7ef2667b5a4266ebb582d3a23b
ms.sourcegitcommit: a0290ac2a662994f7771975ef6c20d0b47e9edd8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/03/2017
---
# <a name="api-tokens"></a>Tokens de API
    
A API do Cloud App Security fornece acesso programático ao Cloud App Security por meio de pontos de extremidade API REST. Aplicativos podem usar a API para realizar operações de leitura e atualização nos dados e objetos do Cloud App Security. Por exemplo, a API de segurança do aplicativo de nuvem dá suporte às seguintes operações comuns para um objeto de usuário:

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
![Token de API de geração do Cloud App Security](./media/api-token-gen.png)

3. Copie o valor do token e salve-o em algum lugar para recuperação – se você perdê-lo, será necessário gerar o token novamente. O token terá os privilégios do usuário que o emitiu. Por exemplo, um leitor de segurança não pode emitir um token que pode alterar os dados.

4. Você pode filtrar os tokens de status: Ativo, Inativo ou Gerado. 

  - Tokens com status Gerado são tokens que nunca foram usados. 
  - Tokens com status Ativo são tokens que foram gerados e foram usados nos últimos 7 dias. 
  - Tokens com o status Inativo foram usados, mas não houve atividade nos últimos 7 dias.


## <a name="api-token-management"></a>Gerenciamento de token de API

A página de token de API inclui uma tabela de todos os tokens de API que foram gerados.

Administradores completos verão todos os tokens gerados para este locatário. Outros usuários verão apenas os tokens que eles mesmos geraram.

A tabela fornece detalhes sobre quando o token foi gerado e quando ele foi usado pela última vez e permite revogar o token. 

Depois que um token é revogado, ele é removido da tabela e o software que ele estava em uso não consegue fazer chamadas à API até que um novo token seja fornecido. 

> [!NOTE]
> Conectores do SIEM e coletores de log também usam tokens de API. Esses tokens devem ser gerenciados das seções de agente SIEM e coletores de log e não aparecerão nessa tabela. 

## <a name="see-also"></a>Veja também  
[Solução de problemas de integração de SIEM](troubleshooting-siem.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
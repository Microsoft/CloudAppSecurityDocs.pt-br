---
title: Solucionar problemas de mensagens de erro do conector do aplicativo
description: Este artigo apresenta uma lista de mensagens de erro do conector do Aplicativo de API, além das recomendações de resolução para cada uma.
ms.date: 01/29/2020
ms.topic: conceptual
ms.openlocfilehash: 5848e0286d6d99ed3699652e3a44ef5fe1cf359b
ms.sourcegitcommit: 40d17309b8729eb914ea91ba5fa7017340231488
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/29/2020
ms.locfileid: "97808990"
---
# <a name="troubleshooting-app-connectors-using-error-messages"></a>Solução de problemas de conectores de aplicativos usando mensagens de erro

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Este artigo apresenta uma lista de mensagens de erro do conector do Aplicativo de API, além das recomendações de resolução para cada erro.

## <a name="troubleshooting"></a>Solução de problemas

Os erros do conector de aplicativos podem ser vistos na caixa de diálogo do conector de aplicativos após a tentativa de conectar um aplicativo de nuvem usando o conector de aplicativos de API.

> [!div class="mx-tableFixed"]
>
> |Mensagem de erro|Aplicativo relevante|Descrição|Resolução|
> |----|----|----|------------|
> |HttpRequestFailure: O servidor retornou: 500 Erro interno do servidor|Todos os aplicativos|Ocorreu um erro no aplicativo.|Verificar o status do aplicativo|
> |Tempo limite do serviço excedido|Todos os aplicativos|Foi detectado um tempo limite excedido de conexão entre o Cloud App Security e o aplicativo. Isso pode ocorrer devido a um problema com o aplicativo.|Tente novamente depois.|
> |NullPointerException|AWS|Erro interno|Contate o suporte|
> |AuthFatalFailureException: com.box.boxjavalibv2.exceptions.BoxServerException: {"error":"invalid_grant","error_description":"Invalid refresh token"}|Box|O token de atualização do Box não é válido|Siga o processo para conectar o Box ao Cloud App Security novamente.|
> |BoxRestException: Falha ao analisar a resposta.|Box|Erro interno|Clique no link “Teste agora” novamente para testar a conexão com o Box.|
> |ContextManagerServiceException: com.adallom.adalib.httputils.exceptions.TokenRefreshException: {"error":"invalid_grant","error_description":"Invalid refresh token"}'|Box|O token de atualização do Box não é válido|Siga o processo para conectar o Box ao Cloud App Security novamente.|
> |BoxServerException: O usuário não pode acessar esse recurso sem ter uma conta enterprise|Box|A conta do Box não é uma conta da empresa.|Atualize sua licença do Box para a versão Enterprise e siga o processo para conectar o Box ao Cloud App Security novamente.|
> |BoxServerException: não autorizado – Não é possível autorizar com este serviço|Box|O Administrador do Box excluiu o aplicativo do Cloud App Security no Box.|Siga o processo para conectar o Box ao Cloud App Security novamente.|
> |HttpRequestFailure: o servidor retornou: 401 não autorizado|Exchange Online|Usuário ou senha incorretos|Verifique se o nome de usuário e a senha estão corretos e siga o processo para conectar o Exchange Online ao Cloud App Security novamente.|
> |HttpRequestFailure: o servidor retornou: 404 não encontrado|Exchange Online|O usuário que você está usando para fazer logon no Exchange Online não tem uma caixa de correio principal no Exchange Online (por exemplo, um usuário que não existe no Azure AD ou um usuário existe no Azure AD, mas não tem uma licença do Exchange Online).|Siga o processo para conectar o Exchange Online ao Cloud App Security novamente usando uma nova conta de administrador.|
> |GoogleJsonResponseException: 401 Não autorizado|Google Workspace|Acesso negado. Você não está autorizado a ler registros de atividade. O usuário que você faz logon no Google Workspace com deve ser um usuário administrador.|Siga o processo para conectar o Google Workspace para Cloud App Security novamente usando uma conta de administrador.|
> |GoogleJsonResponseException: 403 Proibido|Google Workspace|Problema ao executar a API do Google Workspace.|Se você acabou de implantar o conector de aplicativo Cloud App Security para o Google Workspace, verifique o seguinte: se você clicou em ilimitado, verifique se sua conta do Google Workspace é realmente ilimitada. Caso contrário, execute o Conector de Aplicativos novamente e desmarque a opção de conta ilimitada. Verifique se os escopos definidos durante a instalação estão corretos. Se essa não for uma nova implantação e você vir esse erro, talvez seja que você atingiu o limite de API para os eventos atuais e o Google Workspace será renovado amanhã.|
> |TokenResponseException: 400 Solicitação inválida|Google Workspace|A conexão com o Google Workspace não foi concluída ou expirou.|Siga o processo para conectar o Google Workspace para Cloud App Security novamente.|
> |HttpRequestFailure: o servidor retornou: 401 não autorizado|Okta|O token Okta não é válido.|Siga o processo para conectar o Okta ao Cloud App Security novamente.|
> |IOException:|Okta|Erro interno|Contate o suporte|
> |HttpRequestFailure: o servidor retornou: 404 não encontrado|Okta|Erro interno|Contate o suporte|
> |HttpRequestFailure: O servidor retornou: 400 Solicitação inválida: {"error":{"code":"AF20012","message":"A ID de locatário especificada (insira Tenant_ID aqui) está configurada incorretamente no sistema."|Office 365 |Não foi encontrada nenhuma licença atribuída do Office 365. |Atribua pelo menos uma licença do Office 365 ao seu locatário.|
> |Microsoft. Office. Compliance. Audit. DataServiceException: locatário 998cea7e-35cd-46a5-ab3c-8ec88a45d7d5 não existe ou {"erro": "código": "AF20023", "Message": "a assinatura foi desabilitada".|Office 365|O log de auditoria não está habilitado no Office 365|Habilite o log de auditoria no Office 365. [Saiba mais](connect-office-365-to-microsoft-cloud-app-security.md#how-to-connect-office-365-to-cloud-app-security)|
> |HttpRequestFailure: o servidor retornou: 401 não autorizado|Office 365|Problema interno|Clique no link “Testar agora” novamente|
> |TokenRefreshException: {"error":"invalid_grant","error_description":"AADSTS70002: Error ao validar as credenciais. AADSTS70008: O código de autorização ou token de atualização fornecido expirou. Envie uma nova solicitação de autorização interativa para esse usuário e recurso.|Office 365|Token expirado|Siga o processo para conectar o Office 365 ao Cloud App Security novamente.|
> |SocketTimeoutException: tempo limite de leitura excedido|Office 365|Erro interno|Clique no link “Testar agora” novamente|
> |NullPointerException|Office 365|Erro interno|Contate o suporte|
> |IgniteException|Office 365|O domínio ou o usuário não são válidos|Redefina suas configurações e siga o processo para conectar o Office 365 ao Cloud App Security novamente.|
> |ContextManagerServiceException: com.adallom.adalib.httputils.exceptions.TokenRefreshException: {"error":"invalid_grant","error_description":"AADSTS70002: Erro ao validar as credenciais. AADSTS70008: O código de autorização ou token de atualização fornecido expirou. Envie uma nova solicitação de autorização interativa para esse usuário e recurso.|Office 365|O domínio ou o usuário não são válidos|Redefina suas configurações e siga o processo para conectar o Office 365 ao Cloud App Security novamente.|
> |HttpRequestFailure: o servidor retornou: 400 solicitação inválida|Office 365|Erro interno|Clique no link “Teste agora” dentro de alguns minutos; se não funcionar, siga o processo para conectar o Office 365 ao Cloud App Security novamente.|
> |SocketTimeoutException: tempo limite de leitura excedido|Salesforce|Erro interno|Clique no link “Teste agora” novamente para testar a conexão com o Salesforce.|
> |HttpRequestFailure: o servidor retornou: 400 solicitação inválida|Salesforce|A conexão com o Salesforce não foi concluída ou expirou.|Siga o processo para conectar o Salesforce ao Cloud App Security novamente.|
> |Obter permissões: nohttpresponseexception: `*******.salesforce.com:443` falha ao responder|Salesforce|Restrição de IP no Customer ENV.|No portal do Salesforce, em   >  **configurações da sessão** de instalação, desmarque a caixa de seleção **Bloquear sessões para o endereço IP do qual foi originada** .|
> |RuntimeException: com.adallom.adalib.httputils.exceptions.HttpRequestFailure: O servidor retornou: 403 Proibido|ServiceNow|As permissões estão incorretas|Siga o processo para conectar o ServiceNow ao Cloud App Security novamente usando uma conta de administrador.|
> |Obter eventos: {"código": 403, "serverResponse"<br />Obter usuários: {"código": 403, "serverResponse"<br />…<br />"Body": "{" erro ":" permissão negada "}"|Workday|Permissão insuficiente para acessar os logs de auditoria e/ou os pontos de extremidade do usuário|Verifique se todas as permissões estão em vigor. [Saiba mais](connect-workday-to-microsoft-cloud-app-security.md#prerequisites)|
> |"código": 400, "serverResponse"<br />…<br />corpo ":" {"erro": "invalid_grant"}|Workday|Problema de autenticação|A conta usada para configurar a instância pode estar bloqueada ou desabilitada. Para verificar, exiba a conta workday e selecione **Exibir histórico de logon**. Você pode ver uma mensagem de falha de autenticação no relatório especificando que a conta do sistema está desabilitada. [Saiba mais](connect-workday-to-microsoft-cloud-app-security.md#how-to-connect-workday-to-cloud-app-security-using-oauth)|
> |"código": 401, "serverResponse":<br />…<br />corpo ":" {"erro": "invalid_client"} "|Workday|Problema de validade do token de cliente|O token do cliente da API REST do OAuth 2,0 não é válido. O token pode ter expirado ou pode estar incorreto. Gere outro token e atribua-o à instância conectada. [Saiba mais](connect-workday-to-microsoft-cloud-app-security.md#how-to-connect-workday-to-cloud-app-security-using-oauth)|

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]

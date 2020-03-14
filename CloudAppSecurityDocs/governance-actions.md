---
title: Ações de governança para controlar aplicativos conectados-Cloud App Security | Microsoft Docs
description: Este artigo lista e descreve todas as ações de governança que podem ser executadas em Cloud App Security e as mensagens de log que as acompanham.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/03/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 5ae82c1acddf3bbf1ee711a108234d6b69cd8ee4
ms.sourcegitcommit: 4f3883a9e85d0aaf2802b10433b221c3f1838d88
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79285330"
---
# <a name="governing-connected-apps"></a>Controlando aplicativos conectados

*Aplica-se a: Microsoft Cloud App Security*

O controle permite que você controle o que os usuários fazem, em tempo real, entre aplicativos. Para aplicativos conectados, você pode aplicar ações de controle a arquivos ou atividades. Ações de governança são ações integradas que podem ser executadas em arquivos ou atividades diretamente do Microsoft Cloud App Security. As ações de governança controlam o que os usuários fazem, em tempo real, entre os aplicativos conectados.

> [!NOTE]
> Quando Microsoft Cloud App Security tenta executar uma ação de governança em um arquivo, mas falha porque o arquivo está bloqueado, ele repetirá automaticamente a ação de governança.

## <a name="file-governance-actions"></a>Ações de governança de arquivo

As ações de controle a seguir podem ser tomadas para aplicativos conectados em um arquivo, usuário ou política específica.

- **Notificações**

  - **Alertas** – os alertas podem ser disparados no sistema e propagados por email e mensagem de texto, com base no nível de severidade.

  - **Notificação por email do usuário** – as mensagens de email podem ser personalizadas e serão enviadas a todos os proprietários do arquivo que violarem.

  - **Notifique usuários específicos** – lista específica de endereços de email que receberão essas notificações.

  - **Notificar último editor de arquivo** – enviar notificações para a última pessoa que modificou o arquivo.

- **Ações de governança em aplicativos** – ações granulares podem ser impostas por aplicativo, ações específicas variam dependendo da terminologia do aplicativo.

  - **Rotulagem**
    - **Aplicar rótulo** – capacidade de adicionar um rótulo de classificação da proteção de informações do Azure.
    - **Remover rótulo** – capacidade de remover um rótulo de classificação da proteção de informações do Azure.
  - **Alterar compartilhamento**

    - **Remover compartilhamento público** – permitir acesso somente a colaboradores nomeados, por exemplo: remover acesso público para o G Suite e remover link compartilhado direto para Box.

    - **Remover usuários externos** – permitir acesso somente aos usuários da empresa.

    - **Tornar privado** – somente administradores de site podem acessar o arquivo, todos os compartilhamentos são removidos.

    - **Remover um colaborador** – remova um colaborador específico do arquivo.

    - **Reduzir o acesso público** – defina os arquivos publicamente disponíveis para que estejam disponíveis apenas com um link compartilhado. Google

    - Requerer **link compartilhado** – capacidade de definir uma data de experation para um link compartilhado após o qual ele não estará mais ativo. Quadro

    - **Alterar nível de acesso do link de compartilhamento** – capacidade de alterar o nível de acesso do link compartilhado somente entre a empresa, somente colaboradores e público. Quadro

  - **Quarentena**

    - **Colocar em quarentena do usuário** – permitir autoatendimento movendo o arquivo para uma pasta de quarentena controlada pelo usuário

    - **Colocar em quarentena do administrador** – o arquivo é movido para quarentena na unidade do administrador e o administrador precisa aprová-lo.

  - **Herdar permissões do pai** – essa ação de governança permite remover permissões específicas definidas para um arquivo ou pasta no Office 365. Em seguida, reverta para quaisquer permissões definidas para a pasta pai.

  - **Lixeira** – mova o arquivo para a pasta da lixeira. (Box, Dropbox, Google Drive, OneDrive, SharePoint)

   ![alertas de policy_create](media/policy_create-alerts.png "alertas de policy_create")

## <a name="activity-governance-actions"></a>Ações de governança de atividade

- **Notificações**

  - **Alertas** – os alertas podem ser disparados no sistema e propagados por email e mensagem de texto, com base no nível de severidade.

  - **Notificação por email do usuário** – as mensagens de email podem ser personalizadas e serão enviadas a todos os proprietários do arquivo que violarem.

  - **Notifique usuários adicionais** – lista específica de endereços de email que receberão essas notificações.

- **Ações de governança em aplicativos** – ações granulares podem ser impostas por aplicativo, ações específicas variam dependendo da terminologia do aplicativo.

  - **Suspender usuário** – suspender o usuário do aplicativo.
    > [!NOTE]
    > Se seu Azure Active Directory (AD do Azure) estiver definido para sincronizar automaticamente com os usuários em seu ambiente do Active Directory local, as configurações no ambiente local substituirão as configurações do Azure AD e essa ação de governança será revertida.

  - **Exigir que o usuário entre novamente** – desconecta o usuário e exige que ele entre novamente.

  - **Confirmar usuário comprometido** – defina o nível de risco do usuário como alto. Isso faz com que as ações de política relevantes definidas no Azure AD sejam impostas. Para obter mais informações sobre como o Azure AD funciona com níveis de risco, consulte [como o AD do Azure usa meus comentários de risco](https://docs.microsoft.com/azure/active-directory/identity-protection/howto-identity-protection-risk-feedback#how-does-azure-ad-use-my-risk-feedback).

  ![Ações de governança de política de atividade de Cloud App Security](media/activity-policy-ref6.png "ref6 de política de atividade")

## <a name="governance-conflicts"></a>Conflitos de governança

Após a criação de várias políticas, pode surgir uma situação na qual as ações de governança em várias políticas se sobreponham. Nesse caso, o Cloud App Security processará as ações de governança da seguinte maneira:

### <a name="conflicts-between-policies"></a>Conflitos entre políticas

- Se duas políticas contiverem ações contidas umas nas outras (por exemplo, **Remover compartilhamentos externos** incluída em **Tornar particular**), o Cloud App Security resolverá o conflito e a ação mais forte será imposta.
- Se as ações não estiverem relacionadas (por exemplo, **notificar proprietário** e **tornar particular**). Ambas as ações serão executadas.
- Se as ações entrarem em conflito (por exemplo, **alterar o proprietário para o usuário a** e **alterar o proprietário para o usuário B**), poderão ocorrer resultados diferentes de cada correspondência. É importante alterar suas políticas para evitar conflitos, pois podem resultar em alterações indesejadas na unidade que serão difíceis de detectar.

### <a name="conflicts-in-user-sync"></a>Conflitos na sincronização de usuário

- Se o Azure AD estiver configurado para sincronizar automaticamente com os usuários em seu ambiente de Active Directory local, as configurações no ambiente local substituirão as configurações do Azure AD e essa ação de governança será revertida.

## <a name="governance-log"></a>Log de governança

O log de governança fornece um registro de status de cada tarefa que você definir no Cloud App Security para execução, incluindo tarefas manuais e automáticas. Essas tarefas incluem aquelas que você definiu em políticas, ações de governança que você define em arquivos e usuários e qualquer outra ação definida Cloud App Security a ser tomada. O Log de governança também fornece informações sobre o êxito ou falha dessas ações. Você pode optar por repetir ou reverter algumas das ações de governança do log de governança.

A tabela a seguir é a lista completa de ações que o portal Cloud App Security permite que você execute. Essas ações são habilitadas em vários locais em todo o console, conforme descrito na coluna **local** . Cada ação de governança realizada é relacionada no Log de Governança.
Para obter informações sobre como as ações de governança são tratadas quando há conflitos de política, consulte [Conflitos de política](control-cloud-apps-with-policies.md).

| Local | Tipo de objeto de destino | Ação de governança |Descrição| Conectores relacionados|
|-------------------|---------|-----|--------|-------|
|Contas |Arquivo |Remover colaborações do usuário | Remove todas as colaborações de um usuário específico para todos os arquivos - bom para as pessoas que estão saindo da empresa. |Box, G Suite|
|Contas | Conta | Cancelar suspensão de usuário |Cancela a suspensão do usuário |G Suite, Box, Office, Salesforce|
|Contas | Conta |Configurações de conta | Leva você para a página de configurações de conta no aplicativo específico (por exemplo, dentro do Salesforce). | Todas as configurações dos aplicativos One Drive e SharePoint são feitas no Office. |
|Contas |Arquivo |Transferir a propriedade de todos os arquivos | Em uma conta, você transfere os arquivos de um usuário para que a propriedade deles seja concedida a uma nova pessoa que você selecionar. O proprietário anterior se torna um editor e não pode mais alterar as configurações de compartilhamento. O novo proprietário receberá uma notificação por email sobre a alteração de propriedade. | G Suite|
|Contas, Política de atividade | Conta | Suspender um usuário| Define que o usuário não tem acesso nem capacidade de entrar. Se eles estiverem conectados quando você definir essa ação, eles serão bloqueados imediatamente. |G Suite, Box, Office, Salesforce|
|Política de atividade, Contas | Conta |Exigir que o usuário entre novamente|Revoga todos os tokens de atualização e os problemas de cookies de sessão para aplicativos pelo usuário. Essa ação impedirá o acesso a qualquer um dos dados da organização e forçará o usuário a entrar em todos os aplicativos novamente.| G Suite, Office|
|Política de atividade, Contas | Conta |Confirmar o usuário comprometido|Defina o nível de risco do usuário como alto. Isso faz com que as ações de política relevantes definidas no Azure AD sejam impostas. | Office |
|Política de atividade, Contas | Conta | Revogar privilégios de administrador |Revoga os privilégios de uma conta de administrador. Por exemplo, definir uma política de atividade que revoga privilégios de administrador após 10 tentativas de logon com falha. | G Suite|
|Painel do aplicativo > Permissões de aplicativo |Permissões|Aplicativo veto| No Google e Salesforce: Remova a proibição do aplicativo e permita que os usuários forneçam permissões para o aplicativo de terceiros com seu Google ou Salesforce. No Office 365: restaura as permissões do aplicativo de terceiros para o Office. |G Suite, Salesforce, Office |
|Painel do aplicativo > Permissões de aplicativo |Permissões| Desabilitar permissões de aplicativo | Revogar as permissões de um aplicativo de terceiros para o Google, Salesforce ou Office. Essa é uma ação única que ocorrerá em todas as permissões existentes, mas não impedirá conexões futuras.|G Suite, Salesforce, Office |
|Painel do aplicativo > Permissões de aplicativo |Permissões| Habilitar permissões de aplicativo |Conceda permissões de um aplicativo de terceiros ao Google, Salesforce ou Office. Essa é uma ação única que ocorrerá em todas as permissões existentes, mas não impedirá conexões futuras.|G Suite, Salesforce, Office |
|Painel do aplicativo > Permissões de aplicativo |Permissões| Vetar aplicativo | No Google e Salesforce: revoga as permissões de um aplicativo de terceiros para o Google ou Salesforce e impede que ele receba permissões no futuro. No Office 365: o não permite a permissão de aplicativos de terceiros para acessar o Office, mas não os revoga. |G Suite, Salesforce, Office |
|Painel do aplicativo > Permissões de aplicativo |Permissões|Revogar o aplicativo|Revogue as permissões de um aplicativo de terceiros para o Google ou Salesforce. Essa é uma ação única que ocorrerá em todas as permissões existentes, mas não impedirá conexões futuras. | G Suite, Salesforce|
|Painel do aplicativo > Permissões de aplicativo | Conta | Revogar o usuário do aplicativo|Você pode revogar usuários específicos ao clicar no número em Usuários. A tela exibirá os usuários específicos e você poderá usar o X para excluir permissões para qualquer usuário.| G Suite, Salesforce|
|Descobrir > Aplicativos descobertos/Endereços IP/Usuários| Cloud Discovery | Exportar dados de descoberta | Cria um CSV dos dados de descoberta. | Descoberta |
|Política de arquivos|Arquivo |Lixeira|Move o arquivo na lixeira do usuário.| Box, Dropbox, Google Drive, OneDrive, SharePoint |
|Política de Arquivos|Arquivo | Notificar o último editor de arquivo |Envia um email para notificar a última pessoa que editou o arquivo que ele viola uma política. |G Suite, Box|
|Política de Arquivos|Arquivo |Notificar o proprietário do arquivo|Envia um email para o proprietário do arquivo, quando um arquivo viola uma política. No Dropbox, se nenhum proprietário estiver associado um arquivo, a notificação será enviada para o usuário específico que você definir. | Todos os aplicativos |
|Política de arquivos, Atividade de política | Arquivo, Atividade | Notificar usuários específicos |Envia um email para notificar usuários específicos sobre um arquivo que viola uma política.| Todos os aplicativos |
|Política de arquivo e Política de atividade | Arquivo, Atividade |Notificar o usuário|Envia um email aos usuários para notificá-los de que algo que eles fizeram ou um arquivo que têm viola uma política. Você pode adicionar uma notificação personalizada para que ele saiba qual foi a violação. |Tudo |
|Política de arquivo e Arquivos|Arquivo | Remover a capacidade do editor de compartilhar|No Google Drive, as permissões de editor padrão de um arquivo permitem o compartilhamento também. Esta ação de governança restringe essa opção e também o compartilhamento de arquivos com o proprietário.| G Suite|
|Política de arquivo e Arquivos|Arquivo | [Colocar em quarentena do administrador](use-case-admin-quarantine.md) |Remove todas as permissões do arquivo e move o arquivo para uma pasta de quarentena em um local para o administrador. Essa ação permite que o administrador examine o arquivo e remova-o.| Office 365 SharePoint, OneDrive for Business, Box|
|Política de arquivo e Arquivos|Arquivo | Aplicar rótulo de classificação|Aplica um rótulo de classificação da proteção de informações do Azure aos arquivos automaticamente com base nas condições definidas na política.| Box, uma unidade, G Suite, SharePoint |
|Política de arquivo e Arquivos|Arquivo | Remover rótulo de classificação | Remove um rótulo de classificação da proteção de informações do Azure dos arquivos automaticamente com base nas condições definidas na política. Você pode remover rótulos somente se eles não incluírem proteção e se eles foram aplicados no Cloud App Security, não rótulos aplicados diretamente na proteção de informações.| Box, uma unidade, G Suite, SharePoint |
|Política de arquivos, Política de atividade, Alertas | Aplicativo |Exigir que os usuários entrem novamente| Você pode exigir que os usuários entrem novamente no Office 365 e em todos os aplicativos do Azure AD como uma correção rápida e eficaz para alertas de atividade do usuário suspeita e contas comprometidas. Você pode encontrar a nova governança nas configurações de política e nas páginas de alertas, ao lado da opção Suspender usuário. | Office 365, Azure AD |
|Arquivos |Arquivo |Restaurar da quarentena do usuário |Restaura um usuário de ser colocado em quarentena. |Caixa |
|Arquivos |Arquivo | Conceder permissões de leitura para mim| Concede permissões de leitura do arquivo para você mesmo, de forma que você possa acessar o arquivo e entender se ele tem uma violação ou não.| G Suite|
|Arquivos |Arquivo | Permitir que os editores compartilhem | No Google Drive, a permissão de editor padrão de um arquivo também permite o compartilhamento. Esta ação de governança é o oposto da ação Remover a capacidade do editor de compartilhar, e permite que o editor compartilhe o arquivo. | G Suite|
|Arquivos |Arquivo | Proteger | Proteger um arquivo com a proteção de informações do Azure aplicando um modelo de organização. | Office 365 (SharePoint e OneDrive) |
|Arquivos |Arquivo | Revogar formulário de permissões de leitura para mim | Revoga permissões de leitura do arquivo para você mesmo, útil após conceder permissão a si próprio para entender se um arquivo tem uma violação ou não.| G Suite|
|Arquivos, Política de arquivo|Arquivo | Transferir a propriedade do arquivo | Altera o proprietário - na política em que você escolher um proprietário específico. | G Suite|
|Arquivos, Política de arquivo|Arquivo | Reduzir o acesso público|Essa ação permite que você defina arquivos disponíveis publicamente para que estejam disponíveis somente com um link compartilhado.| G Suite|
|Arquivos, Política de arquivo|Arquivo | Remover um parceiro | Remove um parceiro específico de um arquivo. | G Suite, Box, One Drive, SharePoint|
|Arquivos, Política de arquivo|Arquivo | Tornar privado| Somente os administradores do site podem acessar o arquivo, todos os compartilhamentos são removidos. | G Suite, One Drive, SharePoint |
|Arquivos, Política de arquivo|Arquivo | Remover usuários externos | Remove todos os parceiros externos - fora dos domínios configurados como internos nas Configurações. |G Suite, Box, One Drive, SharePoint|
|Arquivos, Política de arquivo|Arquivo |Conceder permissão de leitura ao domínio|Concede permissões de leitura do arquivo no domínio especificado para todo o seu domínio ou para um domínio específico. Essa ação será útil se você quiser remover o acesso público depois de conceder acesso ao domínio de pessoas que precisam trabalhar nele.| G Suite|
|Arquivos, Política de arquivo|Arquivo | Colocar em quarentena do usuário | Remove todas as permissões do arquivo e o move para uma pasta de quarentena na unidade de raiz do usuário. Essa ação permite que o usuário examine o arquivo e mova-o. Se for removida manualmente, o compartilhamento de arquivos não será restaurado. | Box, One Drive, SharePoint |
|Arquivos|Arquivo|Expirar link compartilhado| Defina uma data de validade para um link compartilhado após o qual ele não estará mais ativo.|Caixa|
|Arquivos|Arquivo|Alterar o nível de acesso do link de compartilhamento|Altera o nível de acesso do link compartilhado somente entre a empresa, os colaboradores e o público.| Caixa|
|Arquivos, Política de arquivo|Arquivo | Remover acesso público| Se um arquivo foi seu e você o colocou no acesso público, ele se tornará acessível a qualquer outra pessoa configurada com acesso ao arquivo (dependendo do tipo de acesso que o arquivo tinha). | G Suite|
|Arquivos, Política de arquivo|Arquivo |Remover link compartilhado direto| Remove um link que é criado para o arquivo que é público, mas só é compartilhado com pessoas específicas.|Caixa |
|Configurações > Configurações do Cloud Discovery| Cloud Discovery | Recalcular pontuações de Cloud Discovery |Recalcula as pontuações no catálogo de aplicativos de Nuvem após alterar uma métrica de pontuação.| Descoberta |
|Configurações > Configurações do Cloud Discovery > Gerenciar exibições de dados| Cloud Discovery | Criar exibição personalizada de dados de filtro do Cloud Discovery|Cria uma nova exibição de dados para uma exibição mais detalhada dos resultados da descoberta. Por exemplo, intervalos de IP específicos. | Descoberta |
|Configurações > Configurações do Cloud Discovery > Excluir dados| Cloud Discovery | Excluir os dados do Cloud Discovery |Exclui todos os dados coletados de fontes de descoberta.| Descoberta |
|Configurações > Configurações do Cloud Discovery > Carregar logs manualmente/Carregar logs automaticamente | Cloud Discovery | Analisar dados do Cloud Discovery| Notificação de que todos os dados de log foram analisados. | Descoberta |

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]

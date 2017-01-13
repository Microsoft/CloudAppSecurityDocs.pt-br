---
title: "Governança | Microsoft Docs"
description: "Este tópico lista e descreve todas as ações de governança que podem ser executadas no Cloud App Security e as mensagens de log que as rastreiam."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/26/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 3536c0a5-fa56-4931-9534-cc7cc4b4dfb0
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 89f533e3b9c8397818e5aaa108dca168fda64db7
ms.openlocfilehash: f5107adbe61a9dff00754e39134a35b8f620fa4c


---

# <a name="govern"></a>Governança

## <a name="file-governance-actions"></a>Ações de governança de arquivo  
As seguintes ações de governança podem ser executadas em um usuário, arquivo específico ou a partir uma política específica.
  
-   Notificações  
  
    -   Alertas – os alertas podem ser disparados no sistema e propagados por email e mensagem de texto, com base no nível de gravidade.  
  
    -   Notificação de email do usuário – mensagens de email podem ser personalizadas e serão enviadas a todos os proprietários do arquivo em violação.  
  
    -   Copiar gerente – com base na integração de diretório do usuário, as notificações de email também podem ser enviadas para o gerente da pessoa que violar uma política.  
  
-   Notificar usuários específicos – lista específica de endereços de email que receberão essas notificações.  
  
-   Notificar último editor do arquivo – envia notificações para a última pessoa que modificou o arquivo.  
  
-   Ações de governança em aplicativos  
  
     Ações granulares podem ser impostas por aplicativo, ações específicas variam dependendo da terminologia do aplicativo.  
  
    -   Alterar o compartilhamento  
  
        -   Remover o compartilhamento público – permite o acesso apenas aos parceiros nomeados, por exemplo: remover acesso público para Google Apps e Remover o link compartilhado direto para o Box.  
  
        -   Remover usuários externos – permite o acesso somente aos usuários da empresa.  
  
        -   Tornar privado – somente o proprietário pode acessar o arquivo, todos os compartilhamentos são removidos.  
  
        -   Remover um parceiro – remove um parceiro específico do arquivo.  
  
    -   Quarentena  
  
        -   Colocar em quarentena do usuário – Permite o autoatendimento movendo o arquivo para uma pasta de quarentena controlada pelo usuário  
  
        -   Colocar em quarentena do administrador – o arquivo é movido para a quarentena na unidade do administrador e o administrador precisa aprová-lo.  
  
-   Herdar permissões do pai – essa ação de governança permite remover o conjunto de permissões específicas para um arquivo ou pasta e revertê-los em quaisquer permissões que estejam definidas para a pasta pai.
-   Lixeira – move o arquivo para a pasta da lixeira.
  
![alertas policy_create](./media/policy_create-alerts.png "alertas policy_create")  
  
 
## <a name="activity-governance-actions"></a>Ações de governança de atividade  

- Notificações  
  
    -   Alertas – os alertas podem ser disparados no sistema e propagados por email e mensagem de texto, com base no nível de gravidade.  
  
    -   Notificação de email do usuário – mensagens de email podem ser personalizadas e serão enviadas a todos os proprietários do arquivo em violação.  
  
    -   Copiar gerente – com base na integração de diretório do usuário, as notificações de email também podem ser enviadas para o gerente da pessoa que violar uma política.  
  
    -   Notificar usuários adicionais – lista específica de endereços de email que receberão essas notificações.  
  
- Ações de governança em aplicativos  
  
    -   Ações granulares podem ser impostas por aplicativo, ações específicas variam dependendo da terminologia do aplicativo.  
  
    -   Suspender usuário – suspende o usuário do aplicativo.  
  
    -   Revogar senha – revoga a senha do usuário e o força a definir uma nova senha em seu próximo logon.  
  
     ![referência de política de atividade 6](./media/activity-policy-ref6.png "referência de política de atividade 6")  
  

## <a name="governance-conflicts"></a>Conflitos de governança

Após a criação de várias políticas, pode surgir uma situação na qual as ações de governança em várias políticas se sobreponham. Nesse caso, o Cloud App Security processará as ações de governança da seguinte maneira:

- Se duas políticas contiverem ações contidas umas nas outras (por exemplo, **Remover compartilhamentos externos** incluída em **Tornar particular**), o Cloud App Security resolverá o conflito e a ação mais forte será imposta.
- Se as ações forem completamente não relacionadas (por exemplo, **Notificar proprietário** e **Tornar particular**). Ambas as ações serão executadas.
- Se houver conflito entre as ações, (por exemplo **Alterar o proprietário para o usuário A** e **Alterar o proprietário para o usuário B**), resultados diferentes poderão ocorrer em cada correspondência. É importante alterar suas políticas para evitar conflitos, pois eles podem resultar em alterações indesejadas na unidade que serão difíceis de detectar.

## <a name="governance-log"></a>Log de governança
O log de governança fornece um registro de status de cada tarefa que você definir no Cloud App Security para execução, incluindo tarefas manuais e automáticas. Essas tarefas incluem aquelas que podem ser definidas em políticas, as ações de governança que definidas em arquivos e usuários e qualquer outra ação definida para execução no Cloud App Security. O Log de governança também fornece informações sobre o êxito ou falha dessas ações. Você pode optar por repetir ou reverter algumas das ações de governança do log de governança. 

Veja a seguir a lista completa de ações que o portal do Cloud App Security permite que você execute. Elas são habilitadas em vários locais por todo o console, conforme descrito na coluna **Localização**. Cada ação de governança realizada é relacionada no Log de Governança.
Para obter informações sobre como as ações de governança são tratadas quando há conflitos de política, consulte [Conflitos de política](control-cloud-apps-with-policies.md).

**Local**|**Tipo de objeto de destino**|**Ação de governança**|**Descrição**|**Conectores relacionados** 
---------|---------|---------|---------|---------
|Contas|Arquivo|Remover colaborações do usuário|Remove todas as colaborações de um usuário específico para todos os arquivos - bom para as pessoas que estão saindo da empresa.|Box, Google Apps|
|Contas|Conta|Cancelar suspensão de usuário|Cancela a suspensão do usuário|Google Apps, Box, Office|
|Contas|Conta|Configurações de conta|Leva você para a página de configurações de conta no aplicativo específico (por exemplo, dentro do Salesforce).|Todas as configurações dos aplicativos One Drive e SharePoint são feitas no Office.|
|Contas |Arquivo|Transferir a propriedade de todos os arquivos|Em uma conta, você transfere os arquivos de um usuário para que a propriedade deles seja concedida a uma nova pessoa que você selecionar. O proprietário anterior se torna um editor. Depois de transferir a propriedade, o admin@gtest1.adallom.com se tornará um editor e não será mais possível alterar as configurações de compartilhamento. O novo proprietário receberá uma notificação por email sobre a alteração de propriedade.|Google Apps|
|Contas, Política de atividade|Conta|Suspender um usuário|Define que o usuário não terá nenhum acesso e capacidade para fazer logon - se o usuário estiver conectado quando você definir esta opção, ele será bloqueado imediatamente.|Google Apps, Box, Office|
|Política de atividade, Contas|Conta|Revogar a senha|Revoga a senha de uma conta de usuário - por exemplo, configurando uma política de atividade que revogue uma senha após 10 tentativas de logon mal sucedidas.|Google Apps|
|Política de atividade, Contas|Conta|Revogar privilégios de administrador|Revoga privilégios para uma conta de administrador - por exemplo, configurando uma política de atividade que revogue os privilégios de administrador depois de 10 tentativas de logon mal sucedidas.|Google Apps|
|Painel do aplicativo > Permissões de aplicativo|Permissões|Cancelar veto do aplicativo|No Google e Salesforce: remove o veto do aplicativo e permite que os usuários concedam permissões para o aplicativo de terceiros com a conta do Google ou Salesforce. No Office 365: restaura as permissões do aplicativo de terceiros para o Office.|Google Apps, Salesforce, Office|
|Painel do aplicativo > Permissões de aplicativo|Permissões|Desabilitar permissões de aplicativo|Revoga as permissões de um aplicativo de terceiros para o Google, Salesforce ou Office. Esta é uma ação única que ocorrerá em todas as permissões existentes, mas não evitará futuras conexões. |Google Apps, Salesforce, Office|
|Painel do aplicativo > Permissões de aplicativo|Permissões|Habilitar permissões de aplicativo|Conceda as permissões de um aplicativo de terceiros para o Google, Salesforce ou Office. Esta é uma ação única que ocorrerá em todas as permissões existentes, mas não evitará futuras conexões. |Google Apps, Salesforce, Office|
|Painel do aplicativo > Permissões de aplicativo|Permissões|Vetar aplicativo|No Google e Salesforce: revoga as permissões de um aplicativo de terceiros para o Google ou Salesforce e impede que ele receba permissões no futuro. No Office 365: não permite que aplicativos de terceiros recebam permissão para acessar o Office, mas não as revoga.|Google Apps, Salesforce, Office|Política de Arquivos|Arquivo|Restringir somente para parceiros|Somente os parceiros nomeados podem acessar o arquivo.|Caixa|
|Painel do aplicativo > Permissões de aplicativo|Permissões|Revogar o aplicativo|Revogue as permissões de um aplicativo de terceiros para o Google ou Salesforce. Esta é uma ação única que ocorrerá em todas as permissões existentes, mas não evitará futuras conexões.|Google Apps, Salesforce|
|Painel do aplicativo > Permissões de aplicativo|Conta|Revogar o usuário do aplicativo|Você pode revogar usuários específicos ao clicar no número em Usuários. A tela exibirá os usuários específicos e você poderá usar o X para excluir permissões para qualquer usuário.|Google Apps, Salesforce|
|Descobrir > Aplicativos descobertos/Endereços IP/Usuários|Cloud Discovery|Exportar dados de descoberta|Cria um CSV dos dados de descoberta.|Descoberta|
|Política de arquivos|Arquivo|Lixeira|Coloca o arquivo na lixeira do usuário.|One Drive, SharePoint|
|Política de Arquivos|Arquivo|Notificar o último editor de arquivo|Envia um email para notificar a última pessoa que editou o arquivo que ele viola uma política.|Google Apps, Box|
|Política de Arquivos|Arquivo|Notificar o proprietário do arquivo|Envia um email para o proprietário do arquivo com a opção de cc para o gerente quando um arquivo viola uma política. No Dropbox, se nenhum proprietário estiver associado um arquivo, a notificação será enviada para o usuário específico que você definir.|Todos os aplicativos|
|Política de arquivos, Atividade de política|Arquivo, Atividade|cc para gerente do proprietário/usuário|Quando o proprietário do arquivo recebe uma notificação por email de que o arquivo está violando uma política, essa ação, se desejado, notifica o gerente do proprietário/usuário do arquivo.|Todos os aplicativos, exceto o Service Now|
|Política de arquivos, Atividade de política|Arquivo, Atividade|Notificar usuários específicos|Envia um email para notificar usuários específicos sobre um arquivo que viola uma política.|Todos os aplicativos|
|Política de arquivo e Política de atividade|Arquivo, Atividade|Notificar o usuário|Envia um email aos usuários para notificá-los de que algo que eles fizeram ou um arquivo que têm viola uma política. Você pode adicionar uma notificação personalizada para que ele saiba qual foi a violação.|Tudo|
|Política de arquivo e Arquivos|Arquivo|Remover a capacidade do editor de compartilhar|No Google Drive, as permissões de editor padrão de um arquivo permitem o compartilhamento também. Esta ação de governança restringe essa opção e também o compartilhamento de arquivos com o proprietário.|Google Apps|
|Política de arquivo e Arquivos|Arquivo|Colocar em quarentena do administrador|Remove qualquer permissão do arquivo e o move para uma pasta de quarentena na unidade raiz do usuário. Isso permite que o administrador examine o arquivo e o mova.|Caixa|
|Arquivos|Arquivo|Restaurar da quarentena do usuário|Restaura um usuário de ser colocado em quarentena.|Caixa|
|Arquivos|Arquivo|Conceder permissões de leitura para mim|Concede permissões de leitura do arquivo para você mesmo, de forma que você possa acessar o arquivo e entender se ele tem uma violação ou não.|Google Apps|
|Arquivos|Arquivo|Permitir que os editores compartilhem|No Google Drive, as permissões de editor padrão de um arquivo permitem o compartilhamento também. Esta ação de governança é o oposto da ação Remover a capacidade do editor de compartilhar, e permite que o editor compartilhe o arquivo.|Google Apps|
|Arquivos|Arquivo|Revogar formulário de permissões de leitura para mim|Revoga permissões de leitura do arquivo para você mesmo, útil após conceder permissão a si próprio para entender se um arquivo tem uma violação ou não.|Google Apps|
|Arquivos, Política de arquivo|Arquivo|Transferir a propriedade do arquivo|Altera o proprietário - na política em que você escolher um proprietário específico.|Google Apps|
|Arquivos, Política de arquivo|Arquivo|Remover um parceiro|Remove um parceiro específico de um arquivo.|Google Apps, Box, One Drive, SharePoint|
|Arquivos, Política de arquivo|Arquivo|Tornar privado|Torna o arquivo privado - não há mais parceiros ou links públicos, não compartilhados com qualquer pessoa.|Google Apps, One Drive, SharePoint|
|Arquivos, Política de arquivo|Arquivo|Remover usuários externos|Remove todos os parceiros externos - fora dos domínios configurados como internos nas Configurações.|Google Apps, Box |
|Arquivos, Política de arquivo|Arquivo|Conceder permissão de leitura ao domínio|Concede permissões de leitura do arquivo no domínio especificado para todo o seu domínio ou para um domínio específico. Isso pode ser útil se você quiser remover o acesso público depois de conceder acesso ao domínio de pessoas que precisam trabalhar nele.|Google Apps|
|Arquivos, Política de arquivo|Arquivo|Colocar em quarentena do usuário|Remove todas as permissões do arquivo e o move para uma pasta de quarentena na unidade de raiz do usuário. Isso permite que o usuário examine o arquivo e o mova. Se ele for retornado manualmente, o compartilhamento de arquivo não será restaurado.|Box, One Drive, SharePoint|
|Arquivos, Política de arquivo|Arquivo|Remover acesso público|Se um arquivo era seu e você o colocou no acesso público, ele se tornará acessível somente para quem tiver sido configurado com acesso ao arquivo - dependendo do tipo de acesso que o arquivo tinha. |Google Apps|
|Arquivos, Política de arquivo|Arquivo|Remover link compartilhado direto|Remove um link que foi criado para o arquivo que é público, mas só é compartilhado com pessoas específicas.|Caixa|
|Configurações > Configurações do Cloud Discovery |Cloud Discovery|Recalcular pontuações do Cloud Discovery|Recalcula as pontuações no catálogo de aplicativos de Nuvem após alterar uma métrica de pontuação.|Descoberta|
|Configurações > Configurações do Cloud Discovery > Gerenciar exibições de dados|Cloud Discovery|Criar exibição personalizada de dados de filtro do Cloud Discovery|Cria uma nova exibição de dados para uma exibição mais detalhada dos resultados da descoberta. Por exemplo, intervalos de IP específicos.|Descoberta|
|Configurações > Configurações do Cloud Discovery > Excluir dados|Cloud Discovery|Excluir os dados do Cloud Discovery|Exclui todos os dados coletados de fontes de descoberta.|Descoberta|
|Configurações > Configurações do Cloud Discovery > Carregar logs manualmente/Carregar logs automaticamente|Cloud Discovery|Analisar dados do Cloud Discovery|Notificação de que todos os dados de log foram analisados.|Descoberta|


## <a name="see-also"></a>Veja também  
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Dec16_HO4-->



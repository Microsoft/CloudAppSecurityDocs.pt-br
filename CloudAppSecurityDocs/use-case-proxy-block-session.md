---
title: "Como bloquear downloads de dados confidenciais em dispositivos não gerenciados | Microsoft Docs"
description: "Este tópico descreve o cenário para proteger sua organização contra downloads de dados confidenciais por dispositivos não gerenciados."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 8/15/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: d1861218-a16f-4058-bd0e-34cc4a9413d6
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 4936805c3777ce4ff82735637941cbe528315eb4
ms.sourcegitcommit: 84f358a5dd0ab7f362dd3a2cf9999a6184fba856
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/14/2017
---
# <a name="blocking-downloads-on-unmanaged-devices"></a>Bloqueio de downloads em dispositivos não gerenciados

O administrador de TI atual está entre a cruz e a espada: por um lado, você deseja permitir que seus funcionários sejam produtivos, e isso significa acesso e capacidade de trabalhar o tempo todo, em qualquer dispositivo. Por outro lado, você deseja proteger os ativos da empresa, e que incluem informações proprietárias e privilegiadas. Como você pode permitir que seus funcionários acessem seus aplicativos de nuvem, mas protejam seus dados? O proxy do Cloud App Security oferece a você um alto nível de controle sobre o que você permite e não permite em seus aplicativos de nuvem. 

## <a name="how-does-cloud-app-security-detect-unmanaged-devices"></a>Como o Cloud App Security detecta dispositivos não gerenciados?
.

>[!NOTE]
> Esse caso de uso é aplicável a .

## <a name="the-threat"></a>A AMEAÇA
Um gerente de conta na sua organização quer verificar algo no Salesforce em casa durante o fim de semana, em seu telefone celular pessoal. Talvez a conta inclua informações pessoais ou de cartão de crédito do cliente. O telefone é não gerenciado, o que significa que, se ele baixar documentos do Salesforce para o seu telefone, talvez ele esteja infectado com Malware ou, se o dispositivo for extraviado ou roubado, talvez ele não esteja protegido por senha e qualquer pessoa que o encontrar terá acesso a informações confidenciais.

## <a name="the-solution"></a>A SOLUÇÃO
Proteja sua organização monitorando o uso do aplicativo de nuvem no Cloud App Security e criando uma política de proxy para controlar e bloquear atividades em dispositivos não gerenciados.

## <a name="prerequisites"></a>Pré-requisitos

[Implante](proxy-deployment.md) o proxy do Cloud App Security para o Salesforce.

## <a name="set-up-unmanaged-device-detection"></a>Configurar a detecção de dispositivos não gerenciados


## <a name="create-a-session-policy"></a>Criar uma Política de sessão
As Políticas de sessão permitem que você monitore tudo que um usuário faz dentro de uma sessão e dão a você recursos de controle para que você possa bloquear e proteger o download de arquivos.


1.  No console, clique em **Controlar** seguido por **Políticas**.  
  
2.  Clique em **Criar política** e selecione **Política de sessão**.  
  
3.  Dê à sua política um nome e uma descrição, como **Bloquear downloads do SF em dispositivos não gerenciados**.  
  
3. Forneça uma **Gravidade de política** à sua política. Se você tiver configurado a Cloud App Security para enviar notificações em correspondências de política para um nível de severidade de política específicas, isso será usado para determinar se correspondências ela disparará uma notificação.

4.  É possível deixar a configuração **Categoria** como **DLP**.  
  
6. Em **Tipo de controle de sessão**, selecione **Monitorar todas as atividades e controlar o download de arquivos**. Isso dará a você a capacidade de monitorar tudo que seus usuários fazem dentro de uma sessão do Salesforce e dará a você o controle para bloquear e proteger downloads em tempo real. Também será possível filtrar o conteúdo do arquivo com base no DLP interno do Cloud App Security ou em um DLP externo.
 
7. Em **Origem da atividade**, clique em **Selecione aplicativos da lista abaixo** e selecione **Salesforce**.

8. Na seção de filtros de atividade, selecione **Tipo de dispositivo** e, em seguida, **não é igual a** e selecione **Em conformidade**, **Ingressado no domínio** e **Certificado de cliente válido**.
  
8. Defina o Cloud App Security para reconhecer quais arquivos e dados você considera privados:

    - Na seção de filtros de arquivo, selecione os arquivos confidenciais. Se você trabalha com a Proteção de Informações do Azure, é possível selecionar **Rótulo de classificação** e, em seguida, selecionar os rótulos usados para arquivos confidenciais.
    
    -  Habilite **Inspeção de conteúdo** para permitir que o Cloud App Security interno examine o conteúdo classificado dos arquivos, por exemplo, é possível selecionar **Incluir arquivos que correspondem a uma expressão predefinida** e, em seguida, selecione **Todos os países: finanças: número do cartão de crédito**.

10. Nessa etapa, em **Ações** a serem executadas quando a política é correspondida, selecione:
    - Permitir: se você selecionar Permitir, os usuários terão permissão para baixar os arquivos. 
    ou o
    - Proteger: se você selecionar **Proteger**, o usuário poderá baixar os arquivos, mas eles serão criptografados com o Azure RMS. Também será possível definir uma ação padrão a ser executada se a criptografia falhar (bloquear ou permitir o download).
 
 >[!WARNING]
 >Recomenda-se que você não **Bloqueie** os downloads antes de primeiro executar a política no modo de **permissão** e verificar se os resultados são os esperados. Somente depois de determinar que a política não bloqueie ninguém indesejado, mude a política para **Bloquear** downloads.
 
 9. Defina os alertas que você deseja receber quando a política é correspondida. É possível definir um limite para que você não receba um número excessivo de alertas, e é possível selecionar se você deseja receber os alertas como uma mensagem de email ou como uma mensagem de texto ou ambos.

10. Para exibir as correspondências de política de sessão, clique em **Controle** e, em seguida, **Políticas**. Filtre os resultados para exibir somente as Políticas de sessão que usam o filtro **Tipo** na parte superior. Para obter mais informações sobre as correspondências para cada política, clique em uma política. Clique na guia **Histórico** para ver um histórico de até 6 meses de correspondências de política.     
  
## <a name="validate-your-policy"></a>Validar sua política

1. Para simular um alerta, em um dispositivo não gerenciado, faça logon no Salesforce e tentar baixar um arquivo.
3. Vá para o relatório de políticas. Uma correspondência de política de sessão deve ser exibida em breve. 
4. Você pode clicar na correspondência para ver quais arquivos foram baixados. A correspondência em si será mascarada para proteger os dados confidenciais. 

## <a name="blocking-and-protecting-your-sensitive-information"></a>Bloqueio e proteção de suas informações confidenciais

Após você ter validado e ajustado a política, remova eventuais falsos positivos que possam ter correspondido à sua política. Em seguida, faça o seguinte: 

1. Quando uma política de sessão é correspondida, é possível corrigi-la definindo [ações de governança](governance-actions.md) automatizadas.

2. Para fazer isso, edite a política criada acima e defina **Ações** para **Bloquear** downloads quando a política é correspondida. O usuário não poderá baixar os arquivos e receberá uma mensagem de que ele não tem permissão para baixar os arquivos.
  
 
 ## <a name="see-also"></a>Veja também  
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
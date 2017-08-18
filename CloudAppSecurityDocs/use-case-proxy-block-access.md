---
title: "Como bloquear o acesso aos aplicativos de nuvem de dispositivos não gerenciados | Microsoft Docs"
description: "Este tópico descreve o cenário para proteger sua organização contra o acesso a aplicativos de nuvem de dispositivos não gerenciados."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 8/15/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 9aec9c6f-c9e2-4a4b-8b6a-2f8e4465ee3f
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: b12fabca53c6174fb674f9de260eadb2c1311775
ms.sourcegitcommit: 84f358a5dd0ab7f362dd3a2cf9999a6184fba856
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/14/2017
---
# <a name="blocking-access-to-cloud-apps-from-unmanaged-devices"></a>Bloqueio do acesso a aplicativos de nuvem de dispositivos não gerenciados

No mundo corporativo, Traga seu próprio dispositivo é ótimo para os funcionários que desejam aproveitar ao máximo seus telefones pessoais e tablets no local de trabalho. No entanto, muitos administradores de TI, cientes das ameaças que isso representa aos dados e à rede de uma organização, desejam poder bloquear o acesso desses dispositivos não gerenciados a alguns ou a todos os aplicativos de nuvem da empresa. 

## <a name="how-does-cloud-app-security-detect-unmanaged-devices"></a>Como o Cloud App Security detecta dispositivos não gerenciados?
.

>[!NOTE]
> Esse caso de uso é aplicável a .

## <a name="the-threat"></a>A AMEAÇA
Uma gerente de vendas em sua organização tem um dispositivo gerenciado que ela usa regularmente, mas, às vezes, ela deseja verificar algo no Salesforce em seu celular pessoal. O celular não é gerenciado por sua organização, o que significa que talvez esteja infectado por vírus, por malware ou talvez não seja protegido por senha, e qualquer um que o pegue poderá acessar sua conta do Salesforce.

## <a name="the-solution"></a>A SOLUÇÃO
Proteja sua organização monitorando o uso do aplicativo de nuvem no Cloud App Security e criando uma Política de acesso para controlar e bloquear atividades em dispositivos não gerenciados.

## <a name="prerequisites"></a>Pré-requisitos

[Implante](proxy-deployment.md) o proxy do Cloud App Security para o Salesforce.

## <a name="set-up-unmanaged-device-detection"></a>Configurar a detecção de dispositivos não gerenciados


## <a name="create-an-access-policy"></a>Criar uma Política de acesso
As políticas de acesso permitem monitorar tentativas feitas por seus usuários de fazer logon em aplicativos de nuvem e, se necessário, bloqueá-los de acessar o aplicativo.


1.  No console, clique em **Controlar** seguido por **Políticas**.  
  
2.  Clique em **Criar política** e selecione **Política de acesso**.  
  
3.  Dê à sua política um nome e uma descrição, como **Bloquear o acesso ao Salesforce de dispositivos não gerenciados**.  
  
3. Forneça uma **Gravidade de política** à sua política. Se você tiver configurado a Cloud App Security para enviar notificações em correspondências de política para um nível de severidade de política específicas, isso será usado para determinar se correspondências ela disparará uma notificação.

4.  É possível deixar a configuração **Categoria** como **Controle de acesso**.  
  
7. Em **Origem da atividade**, clique em **Selecione aplicativos da lista abaixo** e selecione **Salesforce**.

8. Na seção de filtros de atividade, selecione **Tipo de dispositivo** e, em seguida, **não é igual a** e selecione **Em conformidade**, **Ingressado no domínio** e **Certificado de cliente válido**.
  
10. Nessa etapa, em **Ações** a serem executadas quando a política é correspondida, selecione:
    - Permitir: se você selecionar Permitir, os usuários terão permissão para baixar os arquivos. 
    ou o
    
 
 >[!WARNING]
 >Recomenda-se que você não **Bloqueie** os downloads antes de primeiro executar a política no modo de **permissão** e verificar se os resultados são os esperados. Somente depois de determinar que a política não bloqueie ninguém indesejado, mude a política para **Bloquear** downloads.
 
 9. Defina os alertas que você deseja receber quando a política é correspondida. É possível definir um limite para que você não receba um número excessivo de alertas, e é possível selecionar se você deseja receber os alertas como uma mensagem de email ou como uma mensagem de texto ou ambos.

10. Para exibir as Correspondências de política de acesso, clique em **Controle** e, em seguida, **Políticas**. Filtre os resultados para exibir somente as Políticas de acesso que usam o filtro **Tipo** na parte superior. Para obter mais informações sobre as correspondências para cada política, clique em uma política. Clique na guia **Histórico** para ver um histórico de até 6 meses de correspondências de política.     
  
## <a name="validate-your-policy"></a>Validar sua política

1. Para simular um alerta, em um dispositivo não gerenciado, tente fazer logon no Salesforce.
3. Vá para o relatório de políticas. Uma Correspondência de política de acesso deve ser exibida em breve. 
4. É possível clicar na correspondência para ver quem tentou fazer logon no Salesforce e de qual dispositivo. 

## <a name="blocking-access"></a>Bloqueio do acesso

Após você ter validado e ajustado a política, remova eventuais falsos positivos que possam ter correspondido à sua política. Em seguida, faça o seguinte: 

1. Quando uma Política de acesso é correspondida, é possível corrigi-la definindo [ações de governança](governance-actions.md) automatizadas.

2. Para fazer isso, edite a política criada acima e defina **Ações** para **Bloquear** downloads quando a política é correspondida. O usuário não conseguirá acessar o Salesforce de nenhum dispositivo que não esteja gerenciado.
  
 
 ## <a name="see-also"></a>Veja também  
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
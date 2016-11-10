---
title: Conectar o Box ao Microsoft Cloud App Security | Microsoft Docs
description: "Este tópico fornece informações sobre como conectar seu aplicativo do Box ao Cloud App Security usando o conector de API."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: b3e4713e-986f-4a5e-9fcc-f8de94dd0df7
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed4ea71b24767d3602d40894d1cbac7447bcd8a2
ms.openlocfilehash: 849408f84e2a80022623c11f7951e921a95625b6


---

# <a name="connect-box-to-microsoft-cloud-app-security"></a>Conectar o Box ao Microsoft Cloud App Security
Esta seção fornece instruções para conectar o Cloud App Security à sua conta do Box existente usando as APIs do Conector de Aplicativos.  
  
## <a name="how-to-connect-box-to-cloud-app-security"></a>Como conectar o Box ao Cloud App Security  
  
> [!NOTE]  
>  A implantação com uma conta que não seja uma conta de administrador levará a uma falha no teste da API e não permitirá que Cloud App Security verifique todos os arquivos no Box. Se isso for um problema para você, é possível realizar a implantação com um coadministrador que tenha todos os privilégios selecionados, mas o teste da API continuará a falhar e os arquivos pertencentes a outros administradores no Box não forem verificados.  
  
1.  Se você restringir o acesso de permissão do aplicativo, siga esta etapa. Caso contrário, pule para a etapa 2.  
  
    -   No console de administração do Box, clique no ícone de configurações seguido por **Business settings (Configurações de negócios)**.  
  
         ![configurações de negócios do box](./media/box-business-settings.png "box business settings")  
  
    -   Clique na guia **Aplicativos**.  
  
         ![aplicativos do box](./media/box-apps.png "box apps")  
  
    -   Se **Aplicativos não Publicados** for selecionado, na caixa de texto **Exceto para**, adicione o número de série do aplicativo do Cloud App Security: `nduj1o3yavu30dii7e03c3n7p49cj2qh` e clique em **Salvar**.  
  
         ![configurações do box exceto para](./media/box-settings-except-for.png "box settings except for")  
  
    > [!NOTE]  
    >  Se você for um cliente Adallom existente e a URL do seu console for para o Adallom e não para o Cloud App Security, use este número de série do aplicativo: bwahmilhdlpbqy2ongkl119o3lrkoshc.  
  
2.  No portal do Cloud App Security, clique em **Investigar** e em **Aplicativos sancionados**.  
  
3.  Na linha Box, clique em **Conectar** na coluna **Status do Conector de Aplicativos** ou clique no botão **Conectar um Aplicativo** e selecione **Box**.  
  
     ![conectar o box](./media/connect-box.png "connect box")  
  
4.  Na página **Configurações do Box**, na guia **API**, clique em **Seguir esse link**.  
  
5.  Isso abre a página de logon do Box. Insira suas credenciais para permitir que o Cloud App Security acesse o aplicativo do Box da sua equipe.  
  
6.  O Box perguntará se você deseja permitir que o Cloud App Security acesse o log de atividades e as informações da sua equipe e realize quaisquer atividades como qualquer membro da equipe. Para continuar, clique em **Permitir**.  
  
7.  De volta ao portal do Cloud App Security, você deve receber uma mensagem dizendo que o Box foi conectado com êxito.  
  
8.  Certifique-se de que a conexão foi bem-sucedida clicando em **Testar API**.  
  
     O teste pode levar alguns minutos. Depois de receber uma notificação de êxito, clique em **Fechar**.  
  
O Box agora está conectado ao Cloud App Security.  
 
Depois de conectar o Box, você receberá eventos por 60 dias antes da conexão.
  
Após conectar o Box, o Cloud App Security realizará uma verificação completa. Dependendo de quantos arquivos e usuários você tiver, a verificação completa poderá levar algum tempo. Para habilitar a verificação quase em tempo real, os arquivos nos quais atividades são detectadas movidos para o início da fila de verificação, como por exemplo um arquivo que é editado, atualizado ou compartilhado é examinado imediatamente e não aguarda até ser alcançado pelo processo de verificação regular. Isso não se aplica a arquivos que não são inerentemente modificados, como arquivos que são exibidos, visualizados, impressos ou exportados.
  
## <a name="see-also"></a>Veja também  
[Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Oct16_HO4-->



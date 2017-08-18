---
title: "Criar políticas de acesso para monitorar e bloquear o acesso aos seus aplicativos de nuvem | Microsoft Docs"
description: "Este tópico descreve o procedimento para configurar uma política de acesso para monitorar e bloquear o acesso aos seus aplicativos de nuvem."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 8/8/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: ddeabd1d-f017-4756-94b2-194292e60c07
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: b070c4f6364f8beccd397102fa00642560414326
ms.sourcegitcommit: 4cf65f627f2d370ee4a4decae1acbb9658874056
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2017
---
# <a name="access-policies"></a>Políticas de acesso  
As políticas de acesso permitem monitorar e bloquear o acesso a aplicativos específicos com base no usuário, no local ou no dispositivo.

Antes de poder criar uma política de acesso, é necessário [Implantar o proxy](proxy-deployment.md). As políticas de acesso permitem que você estabeleça regras que definem como você gerencia e monitora o acesso dos usuários aos seus aplicativos de nuvem.
Por exemplo, é possível definir uma política para:
- Bloquear o acesso a todos os aplicativos de nuvem de dispositivos não gerenciados.
- Bloquear o acesso de países específicos, como todos os países que não são a Inglaterra.
- Bloquear o acesso para todos os grupos de usuários que não são de Vendas nem Administradores do Salesforce.
- Permitir o acesso, mas monitorar todas as tentativas de logon e o alerta quando alguém tenta fazer logon de quem não é de um grupo de usuário específico.

Para criar uma nova política de acesso, siga este procedimento:  
  
1.  No console, clique em **Controlar** seguido por **Políticas**.  
  
2.  Clique em **Criar política** e selecione **Política de acesso**.  
  
3.  Atribua um nome e uma descrição à sua política. Se desejar, poderá baseá-la em um modelo. Para obter mais informações sobre modelos de política, consulte [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md).  
  
3. Forneça uma **Gravidade de política** à sua política. Se você tiver configurado a Cloud App Security para enviar notificações em correspondências de política para um nível de severidade de política específicas, isso será usado para determinar se correspondências ela disparará uma notificação.

4.  Em **Categoria**, vincule a política ao tipo de risco mais apropriado. Este campo é somente informativo e ajuda você a pesquisar políticas e alertas específicos posteriormente, com base no tipo de risco.  O risco já pode estar pré-selecionado de acordo com a categoria para a qual você optou por criar a política. Por padrão, as Políticas de acesso são definidas como **Controle de acesso**.  
  
5.  Para definir quais aplicativos descobertos dispararão uma política, **Crie um filtro para os arquivos em que esta política atuará**. 

 > [!NOTE] 
 > Ao usar os filtros de política, **contém** pesquisará somente palavras inteiras: separadas por vírgulas, pontos, espaços ou sublinhados. Por exemplo, se você pesquisar **malware** ou **virus**, ele localizará virus_malware_file.exe, mas não localizará malwarevirusfile.exe. Se você pesquisar **malware.exe**, localizará TODOS os arquivos com malware ou exe em seu nome de arquivo, enquanto se pesquisar **"malware.exe"** (com as aspas), localizará apenas arquivos que contêm exatamente "malware.exe". **É igual a** pesquisará apenas a cadeia de caracteres completa, por exemplo, se você pesquisar **malware.exe**, ele localizará malware.exe, mas não malware.exe.txt.  

6.   Em **Origem da atividade**, selecione a quais aplicativos a política será aplicada, todos os aplicativos ou aplicativos específicos.

7. Use os filtros para selecionar quais usuários, aplicativos e dispositivos você deseja que disparem uma correspondência de política. Para obter uma lista completa de filtros, consulte [Access policy filters](#access-policy-filters) (Filtros da política de acesso).

8.  Escolha as **Ações** que você deseja que o Cloud App Security execute quando uma correspondência for detectada:
    - Permitir e alertar: se você selecionar Permitir, o acesso dos aplicativos será monitorado, mas não bloqueado. Por padrão, se **Permitir** estiver selecionado, os alertas serão enviados automaticamente ao portal do Cloud App Security. 
    - Bloquear: se você selecionar **Bloquear**, quando os requisitos da política corresponderem, o usuário ou o dispositivo não poderá acessar o aplicativo de nuvem. O usuário receberá uma mensagem de que eles não têm acesso ao aplicativo.
  
>[!WARNING]
>Recomenda-se primeiro criar a política usando a ação **Permitir** e verificar os resultados e, somente depois de determinar que a política não bloqueie ninguém indesejado, mudar a política para **Bloquear** o acesso.
  
9. Defina os alertas que você deseja receber quando a política é correspondida. É possível definir um limite para que você não receba um número excessivo de alertas, e é possível selecionar se você deseja receber os alertas como uma mensagem de email ou como uma mensagem de texto ou ambos.

10. Para exibir as correspondências de política de acesso, clique em **Controle** e, em seguida, **Políticas**. Filtre os resultados para exibir somente as Políticas de acesso que usam o filtro **Tipo** na parte superior. Para obter mais informações sobre as correspondências para cada política, clique em uma política. Clique na guia **Histórico** para ver um histórico de até 6 meses de correspondências de política.     
  
## Referência de política de acesso <a name="access-policy-filters"></a>

Esta seção fornece detalhes de referência sobre filtros de política de acesso. 

- Marca Dispositivo – a marca Dispositivo permite filtrar os dispositivos gerenciados selecionando **Em conformidade**, **Ingressado no domínio** e **Certificado de cliente válido**.
- Tipo de dispositivo: nenhum valor, computador, celular, tablet, outro
-   Endereço IP – o endereço IP bruto, a categoria ou a marca do(a) qual a atividade foi executada.  
    - Endereço IP bruto — permite que você pesquise as atividades que foram realizadas nos endereços IP brutos, ou por eles, que sejam iguais, diferentes, comecem com ou não comecem com uma sequência específica, ou endereços IP brutos que estão ou não estão definidos. 
    - Categoria de IP – a categoria do endereço IP em que a atividade foi executada, por exemplo, todas as atividades do intervalo de endereços IP administrativo. As categorias precisam ser configuradas para incluir os endereços IP relevantes, exceto para a categoria "Arriscado", que é pré-configurada e inclui duas marcações de IP: proxy anônimo e Tor. Para saber como configurar as categorias de IP, consulte [Organizar os dados de acordo com suas necessidades](ip-tags.md).  
    - Marca de IP ‑ A marca do endereço IP em que a atividade foi executada, por exemplo, todas as atividades de endereços IP de proxy anônimos. O Cloud App Security cria um conjunto de marcações internas de IP que não são configuráveis. Além disso, você pode configurar suas próprias marcações de IP. Para obter mais informações sobre como configurar as suas próprias marcações de IP, consulte [Organizar os dados de acordo com as suas necessidades](ip-tags.md).
   As marcações internas de IP incluem:
    - Aplicativos Microsoft (14 deles)
    - Proxy anônimo
    - Botnet (você verá que a atividade foi executada por um botnet com um link para saber mais sobre o botnet específico)
    - IP de verificação de Darknet
    - Servidor C&C de malware
    - Analisador de conectividade remota
    - Provedores satélite
    - Proxy inteligente e de acesso (deixados de fora de propósito)
    - Nós de saída do Tor
    - Zscaler

-   Local – o país do qual a solicitação de acesso foi feita.    

- ISP registrado: 

-   Usuário — o usuário que executou a atividade, que pode ser filtrado no domínio, grupo, nome ou na organização. Para filtrar atividades sem nenhum usuário específico, você pode usar o operador 'não está definido'.  
    -   Organização do usuário – A unidade organizacional do usuário que executou a atividade, por exemplo, todas as atividades realizadas pelos usuários de EMEA_marketing.  
    -   Grupo de usuários – Grupos de usuários específicos que você pode importar de aplicativos conectados, por exemplo, administradores do Office 365.  
    -   Nome de usuário — pesquise por um nome de usuário específico. Para ver uma lista de usuários em um grupo de usuários específico, clique no nome do grupo de usuários na **Gaveta de atividade**. Você será levado para a página de Contas, que lista todos os usuários no grupo. Dali você pode analisar os detalhes das contas de usuários específicos do grupo.
       -  Os filtros **Grupo de usuários** e **Nome de usuário** podem passar por filtragem adicional, usando o filtro **Como** e selecionando a função do usuário, que pode ser qualquer uma das seguintes:
            - Apenas objeto de atividade – isso significa que o usuário ou o grupo de usuários selecionado não executou a atividade em questão, eles eram o objeto da atividade
            - Apenas ator – isso significa que o usuário ou o grupo de usuários realizou a atividade
            - Qualquer função – isso significa que o usuário ou o grupo de usuários foi envolvido na atividade, seja como a pessoa que realizou a atividade ou como o objeto da atividade

-   Agente do usuário – o agente do usuário do qual a atividade foi realizada.  
  
-   Marca de agente do usuário — marca de agente do usuário interna, por exemplo, todas as atividades de sistemas operacionais desatualizados ou navegador desatualizado.  
    
>[!NOTE]
> Se em algum momento você desejar limpar os filtros, poderá fazê-lo ao clicar no ícone ![Limpar filtros](./media/clear-filters.png).


## <a name="see-also"></a>Veja também  
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
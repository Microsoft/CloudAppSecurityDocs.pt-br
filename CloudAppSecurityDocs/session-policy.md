---
title: "Criar políticas de sessão para obter visibilidade profunda sobre as atividades de sessão de usuário e bloquear downloads | Microsoft Docs"
description: "Este tópico descreve o procedimento para configurar uma política de sessão do proxy do Cloud App Security a fim de obter visibilidade profunda sobre atividades de sessão de usuário e bloquear downloads."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 8/8/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 745df28a-654c-4abf-9c90-203841169f90
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 4b12d52703aa6b81a76e54626f06e5732fb3a6bf
ms.sourcegitcommit: 84f358a5dd0ab7f362dd3a2cf9999a6184fba856
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/14/2017
---
# <a name="session-policies"></a>Políticas de sessão  
As políticas de sessão permitem a você monitorar tudo que um usuário faz dentro de uma sessão e lhe oferecem recursos de controle para bloquear atividades específicas que os usuários realizam dentro dessas sessões, como baixar arquivos.

Antes de poder criar uma política de sessão, é necessário [Implantar o proxy](proxy-deployment.md). As políticas de sessão permitem a você estabelecer regras que definem como você controla e monitora as sessões dos seus usuários.
Por exemplo, é possível definir uma política para:
- Bloqueie downloads de qualquer arquivo com o rótulo de classificação “classificado” da Proteção de Informações do Azure em dispositivos não gerenciados.
- Proteja downloads de todos os arquivos para dispositivos não gerenciados, com criptografia do Azure RMS.
- 

Para criar uma nova política de sessão, siga este procedimento:  
  
1.  No console, clique em **Controlar** seguido por **Políticas**.  
  
2.  Clique em **Criar política** e selecione **Política de sessão**.  
  
3.  Atribua um nome e uma descrição à sua política. Se desejar, poderá baseá-la em um modelo. Para obter mais informações sobre modelos de política, consulte [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md).  
  
3. Forneça uma **Gravidade de política** à sua política. Se você tiver configurado a Cloud App Security para enviar notificações em correspondências de política para um nível de severidade de política específicas, isso será usado para determinar se correspondências ela disparará uma notificação.

4.  Em **Categoria**, vincule a política ao tipo de risco mais apropriado. Este campo é somente informativo e ajuda você a pesquisar políticas e alertas específicos posteriormente, com base no tipo de risco.  O risco já pode estar pré-selecionado de acordo com a categoria para a qual você optou por criar a política. Por padrão, as Políticas de sessão são definidas como **DLP**.  
  
5.  Para definir quais aplicativos descobertos dispararão uma política, **Crie um filtro para os arquivos em que esta política atuará**. 

 > [!NOTE] 
 > Ao usar os filtros de política, **contém** pesquisará somente palavras inteiras: separadas por vírgulas, pontos, espaços ou sublinhados. Por exemplo, se você pesquisar **malware** ou **virus**, ele localizará virus_malware_file.exe, mas não localizará malwarevirusfile.exe. Se você pesquisar **malware.exe**, localizará TODOS os arquivos com malware ou exe em seu nome de arquivo, enquanto se pesquisar **"malware.exe"** (com as aspas), localizará apenas arquivos que contêm exatamente "malware.exe". **É igual a** pesquisará apenas a cadeia de caracteres completa, por exemplo, se você pesquisar **malware.exe**, ele localizará malware.exe, mas não malware.exe.txt.  

6. Selecione o **Tipo de controle de sessão**.
    - Monitorar todas as atividades: se você selecionar Monitorar, as atividades de sessão dos aplicativos serão monitoradas, mas não bloqueadas. Será possível monitorar cada página interna específica com o aplicativo de nuvem que foi acessado e todo download realizado em cada aplicativo específico. Por padrão, os alertas são enviados automaticamente ao Portal do Cloud App Security. Isso também permite a você [Exportar todo o log de auditoria](#export-the-audit-log) para atividades de sessão da guia Proxy.
    - Monitorar todas as atividades e controlar o download de arquivos: selecionar Monitorar e controlar dará a você todos os recursos listados acima em **Monitorar todas as atividades** com a camada adicional de controle que permite a você bloquear atividades específicas, como o download de arquivos, em tempo real. Também será possível filtrar o conteúdo do arquivo com base no DLP interno do Cloud App Security ou em um DLP externo.
 
7. Em **Origem da atividade**, selecione a quais aplicativos a política será aplicada, todos os aplicativos ou aplicativos específicos.

8. Use os filtros para selecionar quais usuários, aplicativos e dispositivos você deseja que disparem uma correspondência de política. Para obter uma lista completa de filtros, consulte [session policy filters](#session-policy-filters) (filtros da política de sessão).
  
9. Se você optou por **Monitorar todas as atividades e controlar o download de arquivos**, também é possível definir [filtros de arquivo](#session-file-filters)

10. Se você optou por **Monitorar todas as atividades e controlar o download de arquivos**, também é possível definir opções **Inspeção de conteúdo**. O DLP interno permite filtrar os arquivos pelo conteúdo. Para examinar o conteúdo dos arquivos, selecione, em seguida, DLP interno. Depois que a inspeção estiver habilitada, você poderá optar por usar expressões predefinidas ou pesquisar outras expressões personalizadas, seja com uma subcadeia de caracteres ou uma expressão regular própria.
Além disso, você pode especificar uma expressão regular para excluir um arquivo dos resultados. Isso será muito útil se você tiver um padrão de palavra-chave de classificação interno que você deseja excluir da política.
Você pode definir o número mínimo de violações de conteúdo que deseja corresponder antes de o arquivo ser considerado uma violação. Por exemplo, você poderá escolher 10 se quiser ser alertado sobre arquivos com pelo menos 10 números de cartão de crédito encontrados em seu conteúdo.
Quando o conteúdo for comparado com a expressão selecionada, o texto de violação será substituído por caracteres "X". Por padrão, as violações são completamente mascaradas e mostradas em seu contexto exibindo 40 caracteres antes e após a violação. Os números no contexto da expressão são substituídos por caracteres "#" e nunca são armazenados no Cloud App Security. É possível selecionar a opção para Remover máscara dos últimos quatro caracteres de uma violação para remover a máscara dos últimos quatro caracteres da própria violação.

10. Se você optou por **Monitorar todas as atividades e controlar o download de arquivos**, também é possível definir **Ações** a serem executadas quando a política é correspondida:
    - Permitir: se você selecionar Permitir, os usuários terão permissão para baixar os arquivos. 
    - Bloquear: se você selecionar **Bloquear**, quando os requisitos da política corresponderem, o usuário não poderá baixar os arquivos. O usuário receberá uma mensagem de que ele não tem permissão para baixar os arquivos.
    - Proteger: se você selecionar **Proteger**, o usuário poderá baixar os arquivos, mas eles serão criptografados com o Azure RMS. Também será possível definir uma ação padrão a ser executada se a criptografia falhar (bloquear ou permitir o download).
 >[!WARNING]
 >Recomenda-se primeiro criar a política usando a ação **Permitir** e verificar os resultados e, somente depois de determinar que a política não bloqueie ninguém indesejado, mudar a política para **Bloquear** os downloads.
 
 9. Defina os alertas que você deseja receber quando a política é correspondida. É possível definir um limite para que você não receba um número excessivo de alertas, e é possível selecionar se você deseja receber os alertas como uma mensagem de email ou como uma mensagem de texto ou ambos.

10. Para exibir as correspondências de política de sessão, clique em **Controle** e, em seguida, **Políticas**. Filtre os resultados para exibir somente as Políticas de sessão que usam o filtro **Tipo** na parte superior. Para obter mais informações sobre as correspondências para cada política, clique em uma política. Clique na guia **Histórico** para ver um histórico de até 6 meses de correspondências de política.     
  
## <a name="session-policy-reference"></a>Referência de política de sessão  

Esta seção fornece detalhes de referência sobre filtros de política de sessão. 

### Filtros de sessão <a name="session-policy-filters"></a>

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

### Filtros de arquivo de sessão <a name="session-file-filters"></a>

-   Rótulo de classificação – pesquise arquivos com conjunto de marcas específicas. Esses são:
    - Marcas de Habilitar a Proteção de Informações do Azure. Isso exige integração à Proteção de Informações do Azure.
    - Marcas do Cloud App Security. agora fornece mais informações sobre os arquivos verificados. Para cada arquivo verificado pelo DLP do Cloud App Security, você poderá saber se os arquivos foram bloqueados de serem inspecionados porque foram criptografados ou corrompidos. Por exemplo, você pode configurar políticas para alertá- e arquivos protegidos por senha em quarentena que são compartilhados externamente, da seguinte maneira: 
        - Azure RMS criptografado – arquivos cujo conteúdo não foi inspecionado porque eles têm um conjunto de criptografia do RMS do Azure.
        - Criptografado por senha – arquivos cujo conteúdo não foi inspecionado porque eles são protegidos por senha pelo usuário.
        - Arquivo corrompido – arquivos cujo conteúdo não foi inspecionado porque seu conteúdo não pôde ser lido.

-   Tipo de arquivo – O Cloud App Security usa o tipo MIME recebido do serviço e examina o arquivo para determinar o verdadeiro tipo de arquivo. Observe que se essa verificação destina-se a arquivos que são relevantes para a verificação de dados (documentos, imagens, apresentações, planilhas, arquivos de texto e zip/arquivo morto). O filtro funciona por tipo de arquivo/pasta, por exemplo, todas as pastas que são... ou todos os arquivos de planilha que são...
-   Extensão – Foco em extensões de arquivo específicas, como por exemplo, todos os arquivos que são executáveis (exe).  
  
-   Nome do arquivo – nome do arquivo ou subcadeia de caracteres do nome conforme definido no aplicativo de nuvem, por exemplo, todos os arquivos com uma senha em seu nome.   
  
-   Tamanho do arquivo – Tamanho do arquivo em MB – maior do que um determinado tamanho, menor do que um determinado tamanho ou entre um intervalo.    


>[!NOTE]
> Se em algum momento você desejar limpar os filtros, poderá fazê-lo ao clicar no ícone ![Limpar filtros](./media/clear-filters.png).

  
## <a name="see-also"></a>Veja também  
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
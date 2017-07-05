---
title: "Criar políticas de detecção de anomalias no Cloud App Security | Microsoft Docs"
description: "Este tópico fornece uma descrição das Políticas de detecção de anomalias, bem como informações de referência sobre os blocos de construção de uma política de detecção de anomalias."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 2/19/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: ab9bc377-d2f5-4f4c-a419-f1728a15d1c7
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: d6c1851b1903159d40c0daa256fbb28bdb1268bd
ms.sourcegitcommit: 2f4474084c7e07ac4853945ab5aa1ea78950675d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/28/2017
---
# <a name="anomaly-detection-policy"></a>Política de detecção de anomalias
Este artigo fornece detalhes de referência sobre as políticas, fornecendo explicações sobre cada tipo de política e os campos que podem ser configurados para cada política.  

Depois que sua organização estiver protegida pelo Cloud App Security, todas as atividades de nuvem serão pontuadas de acordo com vários fatores de risco predefinidos. O Cloud App Security examina cada sessão do usuário na nuvem e, em seguida, considera os fatores de risco definidos aqui para alertar você quando acontecer algo que seja diferente da linha de base da sua organização ou da atividade regular do usuário. A página de política de detecção de anomalias permite configurar e personalizar quais famílias de fatores de risco serão consideradas no processo de pontuação de risco. As políticas podem ser aplicadas de forma diferente para diferentes usuários, locais e setores organizacionais. Por exemplo, você pode criar uma política que o alerta quando os membros da sua equipe de TI estão ativos de fora do escritório.  

O Cloud App Security tem um período inicial de assimilação de 7 dias, durante o qual ele não sinaliza nenhum novo usuários, atividade, dispositivos ou locais como anormais. Depois disso, cada sessão é comparada à atividade, quando os usuários estavam ativos, endereços IP, dispositivos, etc. detectados ao longo do mês anterior e à pontuação de risco dessas atividades. Use o controle deslizante de sensibilidade na política para definir a pontuação de risco mínimo que disparará os alertas. É recomendável usar o limite de sensibilidade padrão por usa semana ao criar uma política de anomalias, antes de alterá-lo de acordo com o número de alertas recebidos. O Cloud App Security enviará mais ou menos alertas para várias pontuações de risco ao alterar a sensibilidade.
  
![controle deslizante de sensibilidade](./media/sensitivity-slider.png)

Para configurar uma política de detecção de anomalias:  
  
1.  No console, clique em **Controlar** seguido por **Políticas**.  
  
2.  Clique em **Criar política** e selecione a política de **Detecção de anomalias**.  
  
     ![Menu de política de detecção de anomalias](./media/anomaly-detection-policy-menu.png "Menu de política de detecção de anomalias")  
  
3.  Preencha o nome e a descrição da política e continue para o campo **Filtros de atividade**, no qual é possível escolher a atividade à qual deseja aplicar a política.  
  
4.  Atribua um nome e uma descrição à sua política. Se desejar, poderá baseá-la em um modelo. Para obter mais informações sobre modelos de política, consulte [Controlar aplicativos de nuvem com políticas](control-cloud-apps-with-policies.md).  
  
5.  Para aplicar a política a todas as atividades em seu ambiente de nuvem, selecione **Todas as atividades monitoradas**. Para limitar a política a tipos específicos de atividades, escolha **Atividade selecionada**. Clique em **Adicionar filtros** e defina os parâmetros apropriados pelos quais filtrar a atividade. Por exemplo, para impor a política somente em atividades realizadas por administradores do Salesforce, selecione essa marca.  
  
6.  Sob esse campo, defina os **Fatores de risco**. Você pode escolher quais famílias de risco deseja considerar ao calcular a pontuação de risco. À direita da linha, você pode usar o botão Ativar/Desativar para habilitar e desabilitar os vários riscos. Além disso, para maior granularidade, você pode escolher a atividade na qual habilitar cada família de risco específica.  
  
     Os fatores de risco são os seguintes:  
  
    -   **Falhas de logon**: os usuários estão tentando fazer logon e falhando várias vezes em um curto período?  
  
    -   **Atividade do administrador**: os administradores estão usando suas contas com privilégios para fazer logon de locais incomuns ou em horários estranhos?  
  
    -   **Contas inativas**: repentinamente há atividade em uma conta que não estava sendo usada há algum tempo?  
  
    -   **Local**: há atividade em um local novo, incomuns ou suspeito?  
  
    -   **Viagem impossível**: um usuário está fazendo logon de Denver e dez minutos depois de Paris?  
  
    -   **Agente de dispositivo e usuário**: há atividade de um dispositivo não reconhecido ou não gerenciado?  

    -   **Taxa de atividade**: há repentinamente muita atividade em um aplicativo específico? Há downloads ou exclusões grandes, número em massa de arquivos compartilhados ou muita atividade de administrador inesperada?
  
     Você pode usar esses parâmetros para definir cenários complexos, por exemplo, para excluir o intervalo IP do seu escritório dos fatores de risco considerados para a detecção de anomalias, criar uma marca de “IP do escritório” específica e filtrar o intervalo sem os parâmetros considerados. Para então excluir o intervalo que você criou da detecção de anomalias da atividade do administrador:  
  
    -   Em **Tipo de risco**, localize **Atividade do Administrador**.  
  
    -   Altere **Aplicar a** para **Atividade Selecionada**.  
  
    -   Em **Filtros de atividade**, defina **Aplicar a** como **Atividade selecionada** e em **Activities matching all of the following (Atividades que correspondem a todas as a seguir)**, escolha **Atividade administrativa** é **True**.  
  
    -   Clique no ícone **+** e selecione **IP tag does not equal (Marca do IP diferente de)** e selecione a marca de IP do escritório.  
  
7.  Em **Sensibilidade**, selecione com que frequência você deseja receber alertas.  
  
     O valor de sensibilidade determinará quantos alertas semanais serão disparados em média para cada 1.000 usuários.  
  
     ![IPs de detecção de anomalias](./media/anomaly-detection-ips.png "IPs de detecção de anomalias")  
  
8.  Clique em **Criar**.  
 

## <a name="anomaly-detection-policy-reference"></a>Referência de política de detecção de anomalias  
Uma política de detecção de anomalias permite instalar e configurar o monitoramento contínuo da atividade de usuário quanto a anomalias comportamentais. As anomalias são detectadas pela verificação da atividade do usuário. O risco é avaliado observando mais de 30 indicadores de risco diferentes, agrupados em 6 fatores de risco. Com base nos resultados da política, os alertas de segurança são disparados.   
Cada política é composta pelas seguintes partes:  
  
-   Filtros de atividade – permitem verificar seletivamente somente a atividade de usuário filtrada quanto a anomalias.  
  
-   Fatores de risco – permitem que você escolha quais fatores de risco incluir ao avaliar o risco.  
  
-   Sensibilidade – permite definir quantos alertas a política deve disparar.  
  
### <a name="activity-filters"></a>Filtros de atividade  
Para obter uma lista dos filtros de atividade, consulte [Inserir descrição do link aqui](activity-filters.md).  
  
### <a name="risk-factors"></a>Fatores de risco  
Abaixo está uma lista dos fatores de risco que são considerados ao avaliar o risco da atividade do usuário. Todos os fatores de risco podem ser ativados ou desativados. Para cada fator de risco, há duas opções no campo **Aplicar a**, que determinam se ele deve ser incluído ao avaliar o risco da atividade do usuário:  
  
-   Todas as atividades monitoradas – incluir para todas as atividades do usuário que passam o filtro da atividade de política.  
  
-   Atividade selecionada – incluir para a atividade do usuário que passa os filtros de atividade de política e os filtros de atividade que aparecem sob esse fator de risco. Quando essa opção é selecionada, um seletor de filtro de atividade aparece sob o fator de risco, que funciona exatamente como o filtro de atividade da política.  
  
Cada fator de risco, quando incluído na avaliação de risco, tem seus próprios gatilhos que causam um aumento no risco avaliado da atividade do usuário:  
  
-   Falhas de logon – um grande número de falhas de logon ou uma atividade composta inteiramente de falhas de logon.  
  
-   Atividade administrativa ‑ Atividade administrativa executada por um usuário inesperado ou executada de um IP, ISP ou local novo ou que não foi usado por nenhum outro usuário na organização.  
  
-   Contas inativas ‑ Atividade executada por um usuário que não estava ativo por um longo tempo.  
  
-   Local ‑ Atividade realizada de um IP, ISP ou local que nunca foi usado por nenhum outro usuário, nunca foi usado por esse usuário específico, nunca foi usado ou foi usado apenas para falhas de logon no passado.  
  
-   Viagem impossível ‑ Atividade de locais remotos em um curto período de tempo.  
  
-   Agente de dispositivo e usuário ‑ Atividade realizada por um usuário usando um agente do usuário ou dispositivo que nunca foi usado por outro usuário, nunca foi usado por esse usuário específico ou nunca foi usado.  
  
-   Taxa de atividade – atividades repetidas executadas por um usuário em um curto período. 

### <a name="sensitivity"></a>Sensibilidade  
Há duas maneiras de controlar o número de alertas disparados pela política:  
  
-   Controle deslizante de sensibilidade – escolha quantos alertas disparar por 1.000 usuários por semana. Os alertas serão disparados das atividades com o maior risco.  
  
-   Limite diário de alertas – restringir o número de alertas gerados em um único dia.  
  
## <a name="see-also"></a>Veja também  
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  

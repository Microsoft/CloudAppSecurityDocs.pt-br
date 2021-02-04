---
title: Solução de problemas de controles de acesso e de sessão
description: Este artigo fornece aos administradores diretrizes sobre como investigar e resolver o acesso comum e os controles de sessão.
ms.date: 07/15/2020
ms.topic: conceptual
ms.openlocfilehash: 3dc2826de9e46eae43d3d4a2200f0a56ae3ee9da
ms.sourcegitcommit: 2cb91556060d61fa378047aebf81b71dff5ff19d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/04/2021
ms.locfileid: "99551718"
---
# <a name="troubleshooting-access-and-session-controls"></a>Solução de problemas de controles de acesso e de sessão

Este artigo fornece aos administradores diretrizes sobre como investigar e resolver problemas comuns de controle de acesso e sessão como experientes por [Administradores](#issues-experienced-by-admins) e [usuários finais](#issues-experienced-by-end-users).

Antes de prosseguir, verifique se seu ambiente atende aos seguintes requisitos gerais mínimos para controles de acesso e sessão.

- **Licenciamento**: Verifique se você tem uma [licença](https://aka.ms/mcaslicensing)válida.
- **SSO (Sign-On único)**: os aplicativos devem ser configurados com uma das soluções de SSO com suporte.
  - Azure Active Directory (AD do Azure) usando SAML 2,0 ou OpenID Connect 2,0
  - IdP de terceiros usando SAML 2,0
- **Suporte a navegador**: os controles de sessão estão disponíveis para sessões baseadas em navegador nesses navegadores com suporte: Microsoft Edge (mais recente), Google Chrome (mais recente), Mozilla Firefox (mais recente) ou Apple Safari (mais recente)
- **Tempo de inatividade**: Cloud app Security permite que você defina o comportamento padrão a ser aplicado no caso de uma interrupção do serviço, como um componente que não está funcionando corretamente. Você pode optar por proteger (bloquear) ou ignorar (permitir) que os usuários façam ações em conteúdo potencialmente confidencial quando os controles de política normais não puderem ser impostos. Esse comportamento padrão durante o tempo de inatividade do sistema pode ser configurado no portal de Cloud app Security, da seguinte maneira: **configurações**  >  **controle de aplicativos de acesso condicional**  >  **comportamento padrão**  >  **permitir** ou **Bloquear** o acesso.

## <a name="issues-experienced-by-admins"></a>Problemas experientes por administradores

Esta seção é para administradores que configuram controles de acesso e sessão com Cloud App Security e ajuda a identificar situações comuns que podem surgir nas seguintes áreas:

|Seção|Problemas|
|---|---|
|[Condições da rede](#network-conditions)|- [Erros de rede ao navegar para uma página do navegador](#network-errors-when-navigating-to-a-browser-page)<br />- [Logon lento](#slow-login)<br />- [Considerações adicionais](#network-conditions-additional-considerations)|
|[Identificação de dispositivo](#device-identification)|- [Dispositivos ingressados no Azure AD ou em conformidade com o Intune indeterminado](#misidentified-intune-compliant-or-hybrid-azure-ad-joined-devices)<br />- [Os certificados do cliente não estão solicitando quando esperado](#client-certificates-are-not-prompting-when-expected)<br />- [Certificados de cliente estão solicitando a cada logon](#client-certificates-are-prompting-at-every-login)<br />- [Considerações adicionais](#device-identification-additional-considerations)|
|[Integração de um aplicativo](#onboarding-an-app)|- [O aplicativo não aparece na página de **aplicativos controle de aplicativos de acesso condicional**](#app-does-not-appear-on-the-conditional-access-app-control-apps-page)<br />- [Status do aplicativo: continuar a instalação](#app-status-continue-setup)<br />- [Não é possível configurar controles para aplicativos nativos](#cannot-configure-controls-for-native-apps)<br />- [A página **aplicativo não reconhecido é** exibida](#something-went-wrong-page-appears)<br />- [A opção **solicitar controle de sessão** é exibida](#request-session-control-option-appears)<br />- [Considerações adicionais](#onboarding-apps-additional-considerations)|
|[Criando políticas de acesso e sessão](#creating-access-and-session-policies)|- [Em políticas de acesso condicional, você não pode ver a opção **controle de aplicativos de acesso condicional**](#in-conditional-access-policies-you-cannot-see-the-conditional-access-app-control-option)<br />- [Mensagem de erro ao criar uma política: você não tem nenhum aplicativo implantado com Controle de Aplicativos de Acesso Condicional](#error-message-when-creating-a-policy-you-dont-have-any-apps-deployed-with-conditional-access-app-control)<br />- [Não é possível criar políticas de sessão para um aplicativo](#cannot-create-session-policies-for-an-app)<br />- [Não é possível escolher o **método de inspeção**: serviço de **classificação de dados**](#cannot-choose-inspection-method-data-classification-service)<br />- [Não é possível escolher a **ação**: **proteger**](#cannot-choose-action-protect)<br />- [Considerações adicionais](#policies-additional-considerations)|

### <a name="network-conditions"></a>Condições da rede

Os problemas comuns de condição de rede que você pode encontrar incluem:

- [Erros de rede ao navegar para uma página do navegador](#network-errors-when-navigating-to-a-browser-page)
- [Logon lento](#slow-login)
- [Considerações adicionais](#network-conditions-additional-considerations)

#### <a name="network-errors-when-navigating-to-a-browser-page"></a>Erros de rede ao navegar para uma página do navegador

Quando você está primeiro Configurando Cloud App Security acesso e controles de sessão para um aplicativo, os erros de rede comuns que podem surgir incluem: "este site não é seguro" e "não há conexão com a Internet". Essas mensagens podem indicar um erro de configuração de rede geral.

**Etapas recomendadas**

1. Configure o firewall para trabalhar com Cloud App Security usando os endereços IP e nomes DNS do Azure relevantes para seu ambiente.
    1. Adicione a **porta de saída 443** para os seguintes endereços IP e nomes DNS para seu [Cloud app Security Data Center](network-requirements.md#access-and-session-controls).
    1. Reiniciar o dispositivo e a sessão do navegador
    1. Verifique se o logon está funcionando conforme o esperado
1. Habilite o TLS 1,2 nas opções de Internet do seu navegador.

    > [!NOTE]
    >
    > - Cloud App Security aproveita os protocolos de protocolo TLS 1.2 + para fornecer a melhor criptografia de classe. Aplicativos cliente nativos e navegadores que não dão suporte a TLS 1.2 + não estarão acessíveis quando configurados com controle de sessão. No entanto, aplicativos SaaS que usam TLS 1.1 ou inferior aparecerão no navegador como usando TLS 1.2+ quando configurados com o Cloud App Security.
    > - Embora os controles de sessão sejam criados para funcionar com qualquer navegador em qualquer plataforma principal em qualquer sistema operacional, damos suporte ao Microsoft Edge (mais recente), ao Google Chrome (mais recente), ao Mozilla Firefox (mais recente) ou ao Apple Safari (mais recente). O acesso a aplicativos móveis e de área de trabalho também pode ser bloqueado ou permitido.

    | Navegador | Etapas |
    |---|---|
    | Microsoft Internet Explorer | 1. Abra o Internet Explorer<br />2. Selecione **ferramentas**  >  **Opções da Internet**  >  guia **Avançar**<br />3. em **segurança**, selecione **TLS 1,2**<br />4. Selecione **aplicar** e, em seguida, selecione **OK**<br />5. Reinicie o navegador e verifique se você pode acessar o aplicativo |
    | Chromium de borda/borda da Microsoft | 1. Abra a pesquisa na barra de tarefas e procure "opções da Internet"<br />2. Selecione **Opções da Internet**<br />3. em **segurança**, selecione **TLS 1,2**<br />4. Selecione **aplicar** e, em seguida, selecione **OK**<br />5. Reinicie o navegador e verifique se você pode acessar o aplicativo |
    | Google Chrome | 1. abrir Google Chrome<br />2. na parte superior direita, clique em **mais** (3 pontos verticais) > **configurações**<br />3. na parte inferior, clique em **avançado**<br />4. em **sistema**, clique em **abrir configurações de proxy**<br />5. na guia **avançado** , em **segurança**, selecione **TLS 1,2**<br />6. clique em **OK**<br />7. Reinicie o navegador e verifique se você consegue acessar o aplicativo |
    | Mozilla Firefox | 1. abrir o Mozilla Firefox<br />2. na barra de endereços e procure "About: config"<br />3. na caixa de pesquisa, pesquise "TLS"<br />4. Clique duas vezes na entrada para **Security. TLS. Version. min**<br />5. defina o valor inteiro como 3 para forçar o TLS 1,2 como a versão mínima necessária<br />6. clique em **salvar** (marca de seleção à direita da caixa valor)<br />7. Reinicie o navegador e verifique se você consegue acessar o aplicativo |
    | Safari | Se você estiver usando o Safari versão 7 ou superior, o TLS 1,2 será habilitado automaticamente |

#### <a name="slow-login"></a>Logon lento

O encadeamento de proxy e o processamento de nonce são alguns dos problemas comuns que podem resultar em um desempenho de logon lento.

**Etapas recomendadas**

1. Configure seu ambiente para remover o firewall e encaminhar o encadeamento de proxy, conectando dois ou mais servidores proxy para navegar até a página desejada e outros fatores externos que podem causar lentidão no processo de logon.
    1. Identificar se o encadeamento de proxy está ocorrendo em seu ambiente
    1. Remover proxies de encaminhamento adicionais sempre que possível
1. Desative o tratamento de nonce para seus aplicativos que não usam nonce.

    > [!NOTE]
    > Alguns aplicativos usam um hash nonce durante a autenticação para evitar ataques de repetição. Por padrão, Cloud App Security pressupõe que um aplicativo usa um nonce. Se o aplicativo com o qual você está trabalhando não usar nonce, você poderá desabilitar o tratamento de nonce para esse aplicativo no Cloud App Security.

    1. No Cloud App Security, na barra de menus, clique nas configurações engrenagem e, em seguida, selecione **controle de aplicativos de acesso condicional**.
    1. Na lista de aplicativos, na linha na qual o aplicativo que você está configurando aparece, escolha os três pontos no final da linha e escolha **Editar** aplicativo.
    1. Clique em **tratamento de nonce** para expandir a seção e, em seguida, desmarque **habilitar manipulação de nonce**.
    1. Faça logoff do aplicativo e feche todas as sessões do navegador.
    1. Reinicie o navegador e faça logon no aplicativo e verifique se o logon está funcionando conforme o esperado.

<a name="network-conditions-additional-considerations"></a>

#### <a name="additional-considerations"></a>Considerações adicionais

Ao solucionar problemas de condições de rede, há algumas coisas adicionais a serem consideradas sobre o proxy de Cloud App Security.

- **A sessão está sendo roteada para outro data center**

    O Cloud App Security aproveita os data centers do Azure em todo o mundo para otimizar o desempenho por meio de localização geográfica. Isso significa que a sessão de um usuário pode ser hospedada fora de uma região, dependendo dos padrões de tráfego e de sua localização. No entanto, para proteger sua privacidade, nenhum dado de sessão é armazenado nesses data centers.

- **Desempenho do proxy**

    A derivação de uma linha de base de desempenho depende de muitos fatores fora do proxy do Cloud App Security, como:

    - Quais outros proxies ou gateways ficam em série com esse proxy
    - De onde o usuário vem
    - Onde reside o recurso de destino
    - Solicitações específicas na página

    Em geral, qualquer proxy adicionará latência. As vantagens do proxy de Cloud App Security são:

    - Aproveitando a disponibilidade global dos controladores de domínio do Azure para alocar usuários ao nó mais próximo e reduzir sua distância de viagem de ida e volta, em uma escala que poucos serviços em todo o mundo têm.
    - Aproveitando a integração com o acesso condicional do Azure AD para rotear apenas as sessões que você deseja fazer proxy para nosso serviço, em vez de todos os usuários em todas as situações.

### <a name="device-identification"></a>Identificação de dispositivo

Cloud App Security fornece as seguintes opções para identificar o estado de gerenciamento de um dispositivo.

1. Conformidade de Microsoft Intune
1. Ingressado no domínio do Azure AD híbrido
1. Certificados do cliente

Para obter mais informações sobre a identificação do dispositivo, consulte [identificação do dispositivo gerenciado](proxy-intro-aad.md#managed-device-identification).

Os problemas comuns de identificação de dispositivo que você pode encontrar incluem

- [Dispositivos ingressados no Azure AD ou em conformidade com o Intune indeterminado](#misidentified-intune-compliant-or-hybrid-azure-ad-joined-devices)
- [Os certificados do cliente não estão solicitando quando esperado](#client-certificates-are-not-prompting-when-expected)
- [Certificados de cliente estão solicitando a cada logon](#client-certificates-are-prompting-at-every-login)
- [Considerações adicionais](#device-identification-additional-considerations)

#### <a name="misidentified-intune-compliant-or-hybrid-azure-ad-joined-devices"></a>Dispositivos ingressados no Azure AD ou em conformidade com o Intune indeterminado

O acesso condicional do Azure AD permite que as informações do dispositivo associado ao Azure AD híbrido e em conformidade com o Intune sejam passadas diretamente para Cloud App Security, em que o estado do dispositivo pode ser usado como um filtro para políticas de acesso ou sessão. Para obter mais informações, confira [Introdução ao gerenciamento de dispositivos no Azure Active Directory](/azure/active-directory/devices/overview).

**Etapas recomendadas**

1. No Cloud App Security, na barra de menus, clique nas configurações engrenagem e selecione **configurações**.
1. Em **controle de aplicativos de acesso condicional**, selecione **identificação do dispositivo**. Esta página mostra as opções de identificação de dispositivo disponíveis em Cloud App Security.
1. Para **identificação de dispositivo compatível com o Intune** e **identificação de ingresso do Azure ad híbrido** , respectivamente, clique em **Exibir configuração** e verifique se os serviços estão configurados.

    > [!NOTE]
    > Eles são sincronizados automaticamente do Azure AD e do Intune, respectivamente.
1. Crie uma política de acesso ou de sessão com o filtro de **marca de dispositivo** igual a **ingressado no Azure ad híbrido**, em **conformidade com o Intune** ou ambos.
1. Em um navegador, faça logon em um dispositivo que seja associado ao Azure AD híbrido ou em conformidade com o Intune com base em seu filtro de política.
1. Verifique se as atividades desses dispositivos estão preenchendo o log. No Cloud App Security, na página **log de atividades** , [filtre](activity-filters.md) na **marca do dispositivo** o mesmo que o **Azure ad híbrido ingressado**, **compatível com o Intune** ou ambos, com base nos filtros de política.
1. Se as atividades não estiverem sendo populadas no log de atividades Cloud App Security, vá para Azure AD e faça o seguinte:
    1. Em **monitoramento** de  >  **entradas**, verifique se há atividades de entrada nos logs.
    1. Selecione a entrada de log relevante para o dispositivo no qual você fez logon.
    1. No painel **Detalhes**, na guia **Informações do dispositivo**, verifique se o dispositivo é **Gerenciado** (adicionado ao Azure Active Directory híbrido) ou **Em conformidade** (em conformidade com o Intune). Se você não puder verificar o estado, tente outra entrada de registro ou verifique se os dados do dispositivo estão configurados corretamente no Azure Active Directory.
    1. Para acesso condicional, alguns navegadores podem exigir configuração adicional, como a instalação de uma extensão. Use as informações no guia de [suporte do navegador de acesso condicional](/azure/active-directory/conditional-access/concept-conditional-access-conditions#supported-browsers) para configurar seu navegador.
    1. Se você ainda não vir as informações do dispositivo na página **entradas** , abra um tíquete de suporte para o Azure AD.

#### <a name="client-certificates-are-not-prompting-when-expected"></a>Os certificados do cliente não estão solicitando quando esperado

O mecanismo de identificação de dispositivos pode solicitar autenticação de dispositivos relevantes usando certificados do cliente. Você pode carregar uma raiz do X. 509 ou AC (autoridade de certificação) intermediária formatada no formato de certificado PEM. Esses certificados devem conter a chave pública da autoridade de certificação, que é usada para assinar os certificados de cliente apresentados durante uma sessão. Para obter mais informações sobre certificados de cliente, consulte [dispositivos autenticados no certificado do cliente](proxy-intro-aad.md#client-certificate-authenticated-devices).

**Etapas recomendadas**

1. No Cloud App Security, na barra de menus, clique nas configurações engrenagem e selecione **configurações**.
1. Em **controle de aplicativos de acesso condicional**, selecione **identificação do dispositivo**. Esta página mostra as opções de identificação de dispositivo disponíveis em Cloud App Security.
1. Verifique se você carregou uma raiz X. 509 ou uma AC intermediária. Você deve carregar a AC que é usada para assinar sua autoridade de certificação relevante.
1. Crie uma política de acesso ou de sessão com o filtro de **marca de dispositivo** igual a um **certificado de cliente válido**.
1. Verifique se o seu certificado de cliente é:
    - implantado usando o formato de arquivo PKCS #12, normalmente uma extensão de arquivo. p12 ou. pfx
    - instalado no armazenamento do usuário, não no armazenamento do dispositivo, do dispositivo que você está usando para teste
1. Reiniciar a sessão do navegador
1. Ao fazer logon no aplicativo protegido
    - Verifique se você é redirecionado para a URL `<https://*.managed.access-control.cas.ms/aad_login>`
    - Se você estiver usando o iOS, verifique se está usando o navegador Safari
    - Se você estiver usando o Firefox, também deverá adicionar o certificado ao repositório de certificados do próprio Firefox. Todos os outros navegadores usam o mesmo repositório de certificados padrão. Saiba [como adicionar um certificado ao repositório de certificados do Firefox](http://www.jscape.com/blog/firefox-client-certificate).
1. Valide se o certificado do cliente foi solicitado no navegador.
    - Se não aparecer, tente um navegador diferente. A maioria dos principais navegadores dá suporte à execução de uma verificação de certificado de cliente. No entanto, os aplicativos móveis e de desktop geralmente aproveitam os navegadores internos que podem não dar suporte a essa verificação e, portanto, afetam a autenticação para esses aplicativos.
1. Verifique se as atividades desses dispositivos estão preenchendo o log. No Cloud App Security, na página **log de atividades** , [filtre](activity-filters.md) a **marca do dispositivo** como igual ao **certificado válido do cliente**.
1. Se você ainda não vir o prompt, abra um [tíquete de suporte](support-and-ts.md) e inclua as seguintes informações:
    - Os detalhes do navegador ou do aplicativo nativo onde você enfrentou o problema
    - A versão do sistema operacional (por exemplo, iOS/Android/Windows 10)
    - Mencione se o prompt está funcionando no Edge Chromium

#### <a name="client-certificates-are-prompting-at-every-login"></a>Certificados de cliente estão solicitando a cada logon

Se você estiver enfrentando o certificado do cliente aparecendo depois de abrir uma nova guia, isso pode ser devido às configurações ocultas nas **Opções da Internet**.

| Navegador | Etapas |
|---|---|
| Microsoft Internet Explorer | 1. Abra o Internet Explorer<br />2. Selecione **ferramentas**  >  **Opções da Internet**  >  guia **Avançar**<br />3. em **segurança**, selecione **não solicitar a seleção de certificado de cliente quando apenas um certificado existir**<br />4. Selecione **aplicar** e, em seguida, selecione **OK**<br />5. Reinicie o navegador e verifique se você pode acessar o aplicativo sem os prompts adicionais |
| Chromium de borda/borda da Microsoft | 1. Abra a pesquisa na barra de tarefas e procure "opções da Internet"<br />2. Selecione **Opções da Internet**<br />3. Selecione **segurança**, selecione **intranet local** e clique em **nível personalizado**<br />4. em **diversos**  >  **não solicitar a seleção de certificado do cliente quando apenas um certificado existir**, selecione **desabilitar**<br />5. clique em **OK** para fechar a caixa de diálogo nível personalizado<br />6. clique em **aplicar** e selecione **OK** para fechar as opções da Internet<br />7. Reinicie o navegador e verifique se você pode acessar o aplicativo sem os prompts adicionais |

<a name="device-identification-additional-considerations"></a>

#### <a name="additional-considerations"></a>Considerações adicionais

Durante a solução de problemas de identificação do dispositivo, há algumas coisas adicionais a serem consideradas.

- **Protocolo de revogação de certificado de cliente**

    Você pode exigir revogação de certificado para certificados de cliente. Certificados que foram revogados pela autoridade de certificação não são mais confiáveis. A seleção dessa opção exigirá que todos os certificados passem pelo protocolo CRL. Se o seu certificado de cliente não contiver um ponto de extremidade de CRL, você não poderá se conectar a partir do dispositivo gerenciado.

### <a name="onboarding-an-app"></a>Integração de um aplicativo

Você pode carregar os seguintes tipos de aplicativos para controles de acesso e de sessão:

- Aplicativos em destaque: aplicativos que vêm com controles de sessão prontos para uso, conforme indicado pelo rótulo de **controle de sessão**

- Qualquer aplicativo (personalizado): aplicativos de linha de negócios (LOB) ou locais personalizados podem ser integrados a controles de sessão por um administrador

![Lista de proxies mostrando aplicativos em destaque e quaisquer (personalizados)](media/troubleshooting-onboarding.png)

Ao integrar um aplicativo, é crucial garantir que você siga cada etapa nos guias de implantação de proxy:

1. [Implantar aplicativos em destaque com controles de sessão](proxy-deployment-aad.md)
1. [Implantar aplicativos LOB personalizados, aplicativos SaaS sem recursos e aplicativos locais hospedados por meio do proxy de aplicativo do Azure AD com controles de sessão](proxy-deployment-any-app.md)

Os cenários comuns que você pode encontrar durante a integração de um aplicativo incluem:

- [O aplicativo não aparece na página de **aplicativos controle de aplicativos de acesso condicional**](#app-does-not-appear-on-the-conditional-access-app-control-apps-page)
- [Status do aplicativo: continuar a instalação](#app-status-continue-setup)
- [Não é possível configurar controles para aplicativos nativos](#cannot-configure-controls-for-native-apps)
- [A página **aplicativo não reconhecido é** exibida](#something-went-wrong-page-appears)
- [A opção **solicitar controle de sessão** é exibida](#request-session-control-option-appears)
- [Considerações adicionais](#onboarding-apps-additional-considerations)

#### <a name="app-does-not-appear-on-the-conditional-access-app-control-apps-page"></a>O aplicativo não aparece na página de aplicativos Controle de Aplicativos de Acesso Condicional

Ao integrar um aplicativo ao Controle de Aplicativos de Acesso Condicional, a etapa final nos guias de implantação é fazer com que o usuário final navegue até o aplicativo. As recomendações listadas abaixo são etapas que podem ser feitas se o aplicativo não aparecer depois de ter passado pelos guias.

**Etapas recomendadas**

1. Verifique se seu aplicativo atende aos pré-requisitos do aplicativo de acesso condicional

| Provedor de identidade | Validações |
|---|---|
| Azure AD | 1. Verifique se você tem uma licença válida para Azure AD Premium P1, além de uma licença de Cloud App Security<br />2. Certifique-se de que o aplicativo usa o SAML 2,0 ou o protocolo OpenID Connect<br />3. Verifique se o SSO do aplicativo no Azure AD |
| Terceiros | 1. Verifique se você tem uma licença de Cloud App Security válida<br />2. criar um aplicativo duplicado<br />3. Verifique se o aplicativo usa o protocolo SAML<br />4. valide se você integrou totalmente o aplicativo e se o status do aplicativo está **conectado** |

1. Na política do Azure AD, na **sessão**, verifique se a sessão é forçada a rotear para Cloud app Security, o que, por sua vez, permitirá que o aplicativo apareça na página **aplicativos controle de aplicativos de acesso condicional** , da seguinte maneira:
    1. Controle de Aplicativos de Acesso Condicional está selecionado
    1. No menu suspenso políticas internas, verifique se **somente monitor** está selecionado
1. Certifique-se de navegar até o aplicativo em uma nova sessão do navegador usando um novo modo Incognito ou entrando novamente.

#### <a name="app-status-continue-setup"></a>Status do aplicativo: continuar a instalação

O status de um aplicativo pode variar de **continuar a instalação**, **conectada** e **nenhuma atividade**.

Para aplicativos conectados por meio de IdP (provedores de identidade de terceiros), se a instalação não for concluída, ao acessar o aplicativo, você verá uma página com o status de **continuar a instalação**. Use as etapas a seguir para concluir a instalação.

**Etapas recomendadas**

1. Clique em **continuar configuração**.
1. Acesse o [Guia de implantação](proxy-deployment-any-app.md#conf-app) e verifique se você concluiu todas as etapas. Preste atenção especial ao seguinte:
    1. Certifique-se de criar um novo aplicativo SAML personalizado. Você precisa disso para alterar as URLs e os atributos SAML que podem não estar disponíveis nos aplicativos da galeria.
    1. Se seu provedor de identidade não permitir a reutilização do mesmo identificador (também conhecido como ID de entidade ou público-alvo), altere o identificador do aplicativo original.

#### <a name="cannot-configure-controls-for-native-apps"></a>Não é possível configurar controles para aplicativos nativos

Aplicativos nativos podem ser detectados de forma heurística e você pode usar políticas de acesso para monitorá-los ou bloqueá-los. Use as etapas a seguir para configurar controles para aplicativos nativos.

**Etapas recomendadas**

1. Em uma política de acesso, adicione um filtro de **aplicativo cliente** e defina-o como **móvel e área de trabalho**.
1. Em ações, selecione **Bloquear**.
1. Opcionalmente, personalize a mensagem de bloqueio que os usuários recebem quando não conseguem baixar arquivos, por exemplo, "você deve usar um navegador da Web para acessar este aplicativo".
1. Teste e valide se o controle está funcionando conforme o esperado.

#### <a name="app-is-not-recognized-page-appears"></a>A página aplicativo não reconhecido é exibida

Cloud app Security pode reconhecer mais de 16.000 aplicativos por meio do catálogo de aplicativos de nuvem (**descobrir**  ->  **Catálogo de aplicativos de nuvem**). Se você estiver usando um aplicativo personalizado configurado por meio do SSO do Azure AD que não seja um dos aplicativos 16.000, você entrará em uma página de **aplicativo não reconhecida** . Para resolver o problema, você deve configurar o aplicativo no Controle de Aplicativos de Acesso Condicional.

**Etapas recomendadas**

1. No Cloud App Security, na barra de menus, clique nas configurações engrenagem e, em seguida, selecione **controle de aplicativos de acesso condicional**.
1. Na faixa, clique em **Exibir novos aplicativos**.
1. Na lista de novos aplicativos, localize o aplicativo que está sendo integrado, clique no **+** sinal e, em seguida, clique em **Adicionar**.
    1. Selecione se o aplicativo é um aplicativo **personalizado** ou **padrão** .
    1. Continue com o assistente, verifique se os **domínios especificados definidos pelo usuário** estão corretos para o aplicativo que você está configurando.
1. Verifique se o aplicativo aparece na página **controle de aplicativos de acesso condicional aplicativos** .

#### <a name="request-session-control-option-appears"></a>A opção solicitar controle de sessão é exibida

Depois de adicionar um aplicativo, você poderá ver a opção **solicitar controle de sessão** . Isso ocorre porque apenas aplicativos em destaque têm controles de sessão prontos para uso. Para qualquer outro aplicativo, você deve passar por um processo de autointegração.

**Etapas recomendadas**

1. No Cloud App Security, na barra de menus, clique nas configurações engrenagem e selecione **configurações**.
1. Em **controle de aplicativos de acesso condicional**, selecione **integração do aplicativo/manutenção**.
1. Insira o nome principal do usuário ou o email para os usuários que estarão integrando o aplicativo e clique em **salvar**.
1. Vá para o aplicativo que você está implantando. A página que você vê depende se o aplicativo é reconhecido. Realize um dos seguintes procedimentos:

    | Status do aplicativo | Descrição | Etapas |
    | --- | --- | --- |
    | Não reconhecido | Você verá uma página aplicativo não reconhecido solicitando que você configure seu aplicativo. | 1. [adicione o aplicativo ao controle de aplicativos de acesso condicional](proxy-deployment-any-app.md#add-app).<br /> 2. [adicione os domínios para o aplicativo](proxy-deployment-any-app.md#add-domains)e, em seguida, retorne ao aplicativo e atualize a página.<br /> 3. [Instale os certificados para o aplicativo](proxy-deployment-any-app.md#install-certs). |
    | Reconhecido | Você verá uma página de integração solicitando que você continue o processo de configuração do aplicativo. | - [Instale os certificados para o aplicativo](proxy-deployment-any-app.md#install-certs). <br /><br /> **Observação:** Verifique se o aplicativo está configurado com todos os domínios necessários para que o aplicativo funcione corretamente. Para configurar domínios adicionais, vá para [adicionar os domínios do aplicativo](proxy-deployment-any-app.md#add-domains)e, em seguida, retorne à página do aplicativo. |

<a name="onboarding-apps-additional-considerations"></a>

#### <a name="additional-considerations"></a>Considerações adicionais

Durante a solução de problemas de aplicativos de integração, há algumas coisas adicionais a serem consideradas.

- **Os aplicativos no Controle de Aplicativos de Acesso Condicional não se alinham com os aplicativos do Azure AD**

    Os nomes de aplicativo no Azure AD e Cloud App Security podem ser diferentes com base nas maneiras como os produtos identificam aplicativos. Cloud App Security identifica os aplicativos que usam os domínios do aplicativo e os adiciona ao [Catálogo de aplicativos de nuvem](risk-score.md#the-cloud-app-catalog), onde temos mais de 16.000 aplicativos. Em cada aplicativo, você pode exibir ou adicionar ao subconjunto de domínios. Por outro lado, o Azure AD identifica aplicativos usando entidades de serviço. Para obter mais informações, consulte [objetos de entidade de serviço e de aplicativo no Azure ad](/azure/active-directory/develop/app-objects-and-service-principals).

    Na prática, isso significa que a seleção **do SharePoint Online** no Azure AD é equivalente a selecionar aplicativos, como o Word online e as equipes, em Cloud app Security porque os aplicativos usam o `sharepoint.com` domínio.

### <a name="creating-access-and-session-policies"></a>Criando políticas de acesso e sessão

Cloud App Security fornece as seguintes políticas configuráveis:

1. [Políticas de acesso](access-policy-aad.md): para monitorar ou bloquear o acesso a aplicativos de navegador, móveis e/ou desktop
1. [Políticas de sessão](session-policy-aad.md). Para monitorar, bloquear e executar ações específicas para evitar cenários de pós-infiltração e vazamento de dados no navegador

Para usar essas políticas no Cloud App Security, você deve primeiro configurar uma política no acesso condicional do Azure AD para estender controles de sessão, da seguinte maneira: na política do Azure AD, em **controles de acesso**, clique em **sessão**, selecione **usar controle de aplicativos de acesso condicional** e escolha uma política interna (**monitorar somente** ou **bloquear downloads**) ou **use a política personalizada** para definir uma política avançada no Cloud app Security e clique em **selecionar**.

Os cenários comuns que você pode encontrar ao configurar essas políticas incluem:

- [Em políticas de acesso condicional, você não pode ver a opção **controle de aplicativos de acesso condicional**](#in-conditional-access-policies-you-cannot-see-the-conditional-access-app-control-option)
- [Mensagem de erro ao criar uma política: você não tem nenhum aplicativo implantado com Controle de Aplicativos de Acesso Condicional](#error-message-when-creating-a-policy-you-dont-have-any-apps-deployed-with-conditional-access-app-control)
- [Não é possível criar políticas de sessão para um aplicativo](#cannot-create-session-policies-for-an-app)
- [Não é possível escolher o **método de inspeção**: serviço de **classificação de dados**](#cannot-choose-inspection-method-data-classification-service)
- [Não é possível escolher a **ação**: **proteger**](#cannot-choose-action-protect)
- [Considerações adicionais](#policies-additional-considerations)

#### <a name="in-conditional-access-policies-you-cannot-see-the-conditional-access-app-control-option"></a>Em políticas de acesso condicional, você não pode ver a opção Controle de Aplicativos de Acesso Condicional

Para rotear sessões para Cloud App Security, as políticas de acesso condicional do Azure AD devem ser configuradas para incluir Controle de Aplicativos de Acesso Condicional controles de sessão.

**Etapas recomendadas**

- Se você não vir a opção **controle de aplicativos de acesso condicional** em sua política de acesso condicional, certifique-se de que você tenha uma licença válida para Azure ad Premium P1, bem como uma licença de Cloud app Security válida.

#### <a name="error-message-when-creating-a-policy-you-dont-have-any-apps-deployed-with-conditional-access-app-control"></a>Mensagem de erro ao criar uma política: você não tem nenhum aplicativo implantado com Controle de Aplicativos de Acesso Condicional

Ao criar uma política de acesso ou de sessão, você poderá ver a seguinte mensagem de erro: "você não tem aplicativos implantados com Controle de Aplicativos de Acesso Condicional". Esse erro indica que o aplicativo não foi implantado.

**Etapas recomendadas**

1. No Cloud App Security, na barra de menus, clique nas configurações engrenagem e, em seguida, selecione **controle de aplicativos de acesso condicional**.
1. Se você vir a mensagem **nenhum aplicativo conectado**, use o seguinte guia para implantar aplicativos:

    - [Implantar aplicativos em destaque que têm controle de sessão habilitado](proxy-deployment-aad.md)
    - [Implantar aplicativos de linha de negócios personalizados, aplicativos SaaS sem recursos e aplicativos locais](proxy-deployment-any-app.md) hospedados por meio do proxy de aplicativo Azure Active Directory (AD do Azure) com controles de sessão
1. Se você tiver problemas ao implantar o aplicativo, consulte [integração de um aplicativo](#onboarding-an-app).

#### <a name="cannot-create-session-policies-for-an-app"></a>Não é possível criar políticas de sessão para um aplicativo

Depois de adicionar um aplicativo personalizado, na página **aplicativos controle de aplicativos de acesso condicional** , você poderá ver a opção: **solicitar controle de sessão**.

> [!NOTE]
> [Aplicativos em destaque](proxy-intro-aad.md#session-controls) têm controles de sessão prontos para uso. Para qualquer outro aplicativo, você deve passar por um processo de autointegração.

**Etapas recomendadas**

1. Use o seguinte guia de autointegração para implantar qualquer aplicativo no controle de sessão: [implantar aplicativos de linha de negócios personalizados, aplicativos SaaS sem recursos e aplicativos locais](proxy-deployment-any-app.md) hospedados por meio do proxy de aplicativo Azure Active Directory (AD do Azure) com controles de sessão.
1. Crie uma política de sessão, selecione o filtro de **aplicativo** , verifique se seu aplicativo agora está listado na lista suspensa.

#### <a name="cannot-choose-inspection-method-data-classification-service"></a>Não é possível escolher o **método de inspeção**: serviço de **classificação de dados**

Em políticas de sessão, ao usar o tipo de controle de sessão de **download do arquivo de controle (com inspeção)** , você pode usar o método de inspeção do **serviço de classificação de dados** para verificar os arquivos em tempo real e detectar o conteúdo confidencial que corresponde a qualquer um dos critérios configurados. Se o método de inspeção do **serviço de classificação de dados** não estiver disponível, use as etapas a seguir para investigar o problema.

**Etapas recomendadas**

1. Verifique se o **tipo de controle da sessão** está definido para **controlar o download do arquivo (com inspeção)**.

    > [!NOTE]
    > O método de inspeção do **serviço de classificação de dados** só está disponível para a opção baixar o arquivo de **controle (com inspeção)** .

1. Determine se o recurso de **serviço de classificação de dados** está disponível em sua [região](dcs-inspection.md).
    1. Se o recurso não estiver disponível em sua região, use o método de inspeção de **DLP interno** .
    1. Se o recurso estiver disponível em sua região, mas você ainda não conseguir ver o método de inspeção do **serviço de classificação de dados** , abra um tíquete de [suporte](support-and-ts.md).

#### <a name="cannot-choose-action-protect"></a>Não é possível escolher a ação: proteger

Em políticas de sessão, ao usar o tipo de controle de sessão **baixar arquivo de controle (com inspeção)** , além das ações **monitorar** e **Bloquear** , você pode especificar a ação **proteger** . Essa ação permite que você permita downloads de arquivo com a opção de criptografar ou aplicar permissões ao arquivo com base em condições, inspeção de conteúdo ou ambos. Se a ação **proteger** não estiver disponível, use as etapas a seguir para investigar o problema.

**Etapas recomendadas**

1. Se a ação **proteger** não estiver disponível ou estiver esmaecida, verifique se você tem a licença da proteção de informações do Azure (AIP) Premium P1. Confira mais informações em [Integração da Proteção de Informações do Azure](azip-integration.md).
1. Se a ação **proteger** estiver disponível, mas não estiver vendo os rótulos apropriados.
    1. No Cloud App Security, na barra de menus, clique nas configurações engrenagem, selecione **proteção de informações do Azure** e verifique se a integração do AIP está habilitada.
    1. Para rótulos do Office, no portal do AIP, verifique se a seleção de **rótulo unificado** está selecionada.

<a name="policies-additional-considerations"></a>

#### <a name="additional-considerations"></a>Considerações adicionais

Durante a solução de problemas de aplicativos de integração, há algumas coisas adicionais a serem consideradas.

- **Compreendendo a diferença entre as configurações de política de acesso condicional do Azure AD: "monitorar somente", "bloquear downloads" e "usar política personalizada"**

    Nas políticas de acesso condicional do Azure AD, você pode configurar os seguintes controles de Cloud App Security internos: **monitorar apenas** e **bloquear downloads**. Isso se aplica e impõe o Cloud App Security recurso de proxy para aplicativos de nuvem e condições configuradas no Azure AD. Para políticas mais complexas, selecione **usar política personalizada**, que permite configurar políticas de acesso e sessão no Cloud app Security.

- **Compreendendo a opção de filtro de aplicativo cliente "móvel e desktop" nas políticas de acesso**

    Em políticas de acesso Cloud App Security, a menos que o filtro de **aplicativo cliente** seja definido especificamente como **móvel e área de trabalho**, a política de acesso resultante só se aplicará a sessões de navegador. O motivo disso é evitar a proxy inadvertidamente de sessões de usuário, o que pode ser um subproduto do uso desse filtro.

## <a name="issues-experienced-by-end-users"></a>Problemas experientes pelos usuários finais

Esta seção é para usuários finais que usam aplicativos protegidos pelo Cloud App Security e ajuda a identificar situações comuns que podem surgir nas seguintes áreas:

- [A página de monitoramento do usuário não está aparecendo](#user-monitoring-page-is-not-appearing)
- [Não é possível acessar o aplicativo de um provedor de identidade de terceiros](#not-able-to-access-app-from-a-third-party-identity-provider)
- [Aparece uma página **incorreta**](#something-went-wrong-page-appears)
- [As ações da área de transferência ou os controles de arquivo não estão sendo bloqueados](#clipboard-actions-or-file-controls-are-not-being-blocked)
- [Os downloads não estão sendo protegidos](#downloads-are-not-being-protected)
- [Navegando para uma URL específica de um aplicativo sufixado e o pouso em uma página genérica](#navigating-to-a-particular-url-of-a-suffixed-app-and-landing-on-a-generic-page)
- [Considerações adicionais](#app-additional-considerations)

### <a name="user-monitoring-page-is-not-appearing"></a>A página de monitoramento do usuário não está aparecendo

Ao rotear um usuário por meio do Cloud App Security, você pode notificar o usuário de que sua sessão será monitorada. Por padrão, a página monitoramento de usuário está habilitada.

**Etapas recomendadas**

1. No Cloud App Security, na barra de menus, clique nas configurações engrenagem e selecione **configurações**.
1. Em **controle de aplicativos de acesso condicional**, selecione **monitoramento de usuário**. Esta página mostra as opções de monitoramento de usuário disponíveis em Cloud App Security.

    ![Captura de tela mostrando opções de monitoramento de usuário](media/proxy-user-monitoring.png)

1. Verifique se a opção **notificar os usuários de que sua atividade está sendo monitorada** está selecionada.
1. Escolha se deseja usar a mensagem padrão ou fornecer uma mensagem personalizada.

    | Tipo de mensagem | Detalhes |
    | --- | --- |
    | Padrão | **Cabeçalho**:<br />O acesso a [nome do aplicativo aparecerá aqui] é monitorado<br />**Corpo**:<br />Para maior segurança, sua organização permite o acesso ao [o nome do aplicativo aparecerá aqui] no modo de monitor. O acesso só está disponível em um navegador da Web. |
    | Personalizado | **Cabeçalho**:<br />Use esta caixa para fornecer um título personalizado para informar os usuários que estão sendo monitorados.<br />**Corpo**:<br />Use esta caixa para adicionar informações personalizadas adicionais ao usuário, como a quem deve entrar em contato com perguntas e dá suporte às seguintes entradas: texto sem formatação, Rich Text, hiperlinks. |
1. Clique em **Visualizar** para verificar a página de monitoramento de usuário que aparece antes de acessar um aplicativo.
1. Clique em **Save** (Salvar).

### <a name="not-able-to-access-app-from-a-third-party-identity-provider"></a>Não é possível acessar o aplicativo de um provedor de identidade de terceiros

Se um usuário final estiver recebendo uma falha geral depois de fazer logon em um aplicativo de um provedor de identidade de terceiros, valide a configuração de IdP de terceiros.

**Etapas recomendadas**

1. No Cloud App Security, na barra de menus, clique nas configurações engrenagem e, em seguida, selecione **controle de aplicativos de acesso condicional**.
1. Na lista de aplicativos, na linha na qual o aplicativo que você não consegue acessar aparece, escolha os três pontos no final da linha e escolha **Editar** aplicativo.
    1. Validar se o certificado SAML que foi carregado está correto
    1. Verifique se as URLs de SSO válidas foram fornecidas na configuração do aplicativo
    1. Valide se os atributos e valores no aplicativo personalizado são refletidos na captura de tela Configurações do provedor de identidade  ![ mostrando a página coletar informações do SAML dos provedores de identidade](media/proxy-deploy-add-idp-ext-conf.png)
1. Se você ainda não conseguir acessar o aplicativo, abra um [tíquete de suporte](support-and-ts.md).

### <a name="something-went-wrong-page-appears"></a>Aparece uma página incorreta

Às vezes, durante uma sessão de proxy, a página **algo deu errado** pode aparecer. Isso pode ocorrer quando:

1. Um usuário faz logon depois de ficar ocioso por um tempo
1. A atualização do navegador e a carga da página demoram mais do que o esperado
1. O aplicativo IdP de terceiros não está configurado corretamente

**Etapas recomendadas**

1. Se o usuário final estiver tentando acessar um aplicativo que está configurado usando um IdP de terceiros, consulte não é [possível acessar o aplicativo de um IDP de](#not-able-to-access-app-from-a-third-party-identity-provider) terceiros e o [status do aplicativo: Continue a instalação](#app-status-continue-setup).
1. Se o usuário final tiver alcançado essa página inesperadamente, faça o seguinte:
    1. Reiniciar a sessão do navegador
    1. Limpar o histórico, os cookies e o cache do navegador

### <a name="clipboard-actions-or-file-controls-are-not-being-blocked"></a>As ações da área de transferência ou os controles de arquivo não estão sendo bloqueados

É necessária a capacidade de bloquear ações da área de transferência como recortar, copiar, colar e controlar arquivos, como baixar, carregar e imprimir, para evitar cenários de vazamento e pós-infiltração de dados. Essa capacidade permite que as empresas equilibrem a segurança e a produtividade para os usuários finais. Se você estiver enfrentando problemas com esses recursos, use as etapas a seguir para investigar o problema.

**Etapas recomendadas**

Se a sessão estiver sendo proxyada, use as seguintes etapas para verificar a política:

1. Em Cloud App Security, em **investigar**, selecione **log de atividades**.
1. Use o filtro avançado, selecione **ação aplicada** e defina seu valor igual a **bloqueado**.
1. Verifique se há atividades de arquivo bloqueado.
    1. Se houver uma atividade, expanda a gaveta de atividades clicando na atividade
    1. Na guia **geral** da gaveta de atividades, clique no link políticas correspondentes para verificar se a política imposta está presente.
    1. Se você não vir sua política, consulte [criando políticas de acesso e sessão](#creating-access-and-session-policies).
    1. Se você vir o **acesso bloqueado/permitido devido ao comportamento padrão**, isso indica que o sistema estava inoperante e o comportamento padrão foi aplicado.
        1. Para alterar o comportamento padrão, em Cloud App Security, na barra de menus, clique nas configurações engrenagem e selecione **configurações**. Em seguida, em **controle de aplicativos de acesso condicional**, selecione **comportamento padrão** e defina o comportamento padrão para **permitir** ou **Bloquear** o acesso.
        1. Acesse `https://status.cloudappsecurity.com/` e monitore notificações sobre o tempo de inatividade do sistema.
1. Se você ainda não conseguir ver a atividade bloqueada, abra um [tíquete de suporte](support-and-ts.md).

### <a name="downloads-are-not-being-protected"></a>Os downloads não estão sendo protegidos

Como um usuário final, o download de dados confidenciais em um dispositivo não gerenciado pode ser necessário. Nesses cenários, você pode proteger documentos com a proteção de informações do Azure. Se o usuário final não conseguiu criptografar o documento com êxito, use as etapas a seguir para investigar o problema.

**Etapas recomendadas**

1. Em Cloud App Security, em **investigar**, selecione **log de atividades**.
1. Use o filtro avançado, selecione **ação aplicada** e defina seu valor igual a **protegido**.
1. Verifique se há atividades de arquivo bloqueado.
    1. Se houver uma atividade, expanda a gaveta de atividades clicando na atividade
    1. Na guia **geral** da gaveta de atividades, clique no link políticas correspondentes para verificar se a política imposta está presente.
    1. Se você não vir sua política, consulte [criando políticas de acesso e sessão](#creating-access-and-session-policies).
    1. Se você vir o **acesso bloqueado/permitido devido ao comportamento padrão**, isso indica que o sistema estava inoperante e o comportamento padrão foi aplicado.
        1. Para alterar o comportamento padrão, em Cloud App Security, na barra de menus, clique nas configurações engrenagem e selecione **configurações**. Em seguida, em **controle de aplicativos de acesso condicional**, selecione **comportamento padrão** e defina o comportamento padrão para **permitir** ou **Bloquear** o acesso.
        1. Acesse `https://status.cloudappsecurity.com/` e monitore notificações sobre o tempo de inatividade do sistema.
    1. Se você estiver protegendo o arquivo com um rótulo de AIP ou permissões personalizadas, na **Descrição da atividade**, verifique se a extensão de arquivo é um dos seguintes tipos de arquivo com suporte:
        - Word: docm, docx, dotm, dotx
        - Excel: xlam, xlsm, xlsx, xltx
        - PowerPoint: potm, potx, ppsx, ppsm, pptm, pptx
        - PDF * se a rotulagem unificada estiver habilitada
    - Se não houver suporte para o tipo de arquivo, na política de sessão, você poderá selecionar **Bloquear download de qualquer arquivo que não tenha suporte pela proteção nativa ou onde a proteção nativa não for bem-sucedida**.
1. Se você ainda não conseguir ver a atividade bloqueada, abra um [tíquete de suporte](support-and-ts.md).

### <a name="navigating-to-a-particular-url-of-a-suffixed-app-and-landing-on-a-generic-page"></a>Navegando para uma URL específica de um aplicativo sufixado e o pouso em uma página genérica

Todos os proxies que as URLs de sufixo são suscetíveis à perda de contexto, um problema em que navegar até um link perde o caminho completo do link e normalmente atinge o home page do aplicativo. Cloud App Security está posicionado exclusivamente para resolver essa limitação e resolver a perda de contexto por meio de parceria com fornecedores da Microsoft e não Microsoft.

Os aplicativos em nossa página de aplicativos em destaque marcados como **(versão prévia)** podem sofrer a perda de contexto. Da mesma forma, a perda de contexto pode ser causada por políticas globais que bloqueiam cookies de terceiros ou rastreamento entre sites. Você pode corrigir o problema Desabilitando essas opções. Para aplicativos que não estão em destaque experimentando perda de contexto, envie um tíquete de suporte. Estamos trabalhando com cada provedor de aplicativo individualmente para corrigir esses problemas principais.

Como uma mitigação temporária, você pode solucionar problemas de perda de contexto da seguinte maneira:

1. Navegue até uma URL na qual ocorra a perda de contexto.
1. Anote o domínio da URL sufixada, incluindo o sufixo adicionado por Cloud App Security, por exemplo `https://www.yammer.com.mcas.ms` .
1. Copie o caminho da URL original, por exemplo, se a URL específica original era `https://www.yammer.com/organization/threads/threadnumber` , copie `/organization/threads/threadnumber` .
1. Acrescente o caminho copiado para o domínio com sufixo, por exemplo `https://www.yammer.com.mcas.ms/organization/threads/threadnumber` .
1. Navegue até a nova URL sufixada.

<a name="app-additional-considerations"></a>

### <a name="additional-considerations"></a>Considerações adicionais

Durante a solução de problemas de aplicativos, há algumas coisas adicionais a serem consideradas.

- **Suporte a controles de sessão para navegadores modernos**

    Agora os controles de sessão do Cloud App Security incluem suporte para o novo navegador Microsoft Edge baseado no Chromium. Apesar de continuarmos a dar suporte às versões mais recentes do Internet Explorer e à versão herdada do Microsoft Edge, o suporte será limitado, e recomendamos usar o novo navegador Microsoft Edge.

- **Logon duplo**

    Um logon duplo ocorre devido ao uso presumido de um nonce, um token criptográfico usado por aplicativos para evitar ataques de repetição. Por padrão, Cloud App Security pressupõe que um aplicativo usa um nonce. Se você tiver certeza de que o aplicativo não usa um nonce, poderá desabilitá-lo editando o aplicativo no Cloud App Security e o problema será resolvido. Para obter as etapas para desabilitar o nonce, consulte [logon lento](#slow-login).

    Se o aplicativo usar um nonce e esse recurso não puder ser desabilitado, o segundo logon poderá ser transparente para os usuários ou poderá ser solicitado a fazer logon novamente.

- **A visualização ou impressão de arquivos PDF pode estar bloqueada**

    Esse comportamento é normal quando você tem uma política configurada para bloquear downloads. Ocasionalmente, ao visualizar ou imprimir arquivos PDF, os aplicativos iniciam um download do arquivo, fazendo com que Cloud App Security intervir para garantir que o download seja bloqueado e que os dados não sejam vazados do seu ambiente.

    Se você quiser permitir downloads de arquivo PDF, poderá excluir arquivos PDF com base em sua extensão de arquivo na política de sessão relevante.

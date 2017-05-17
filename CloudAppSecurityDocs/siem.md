---
title: "Integração do SIEM ao Cloud App Security | Microsoft Docs"
description: "Este tópico fornece informações a respeito da integração do SIEM ao Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/9/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 4649423b-9289-49b7-8b60-04b61eca1364
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 5880ea404d6830c5d8f12534c04f123d8c517946
ms.sourcegitcommit: ea8207f412f31127beafd18a0bd028052fbadf90
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/09/2017
---
# <a name="siem-integration"></a>Integração ao SIEM
    
Agora você pode integrar o Cloud App Security ao seu servidor SIEM para habilitar o monitoramento centralizado de alertas e de atividades. A integração a um serviço SIEM permite que você proteja melhor seus aplicativos na nuvem e, ao mesmo tempo, mantém seu fluxo de trabalho de segurança comum, automatiza os procedimentos de segurança e correlaciona os eventos baseados em nuvem e locais. O agente SIEM do Cloud App Security é executado no servidor e efetua pull de alertas e de atividades do Cloud App Security e transmite-os para o servidor SIEM.

Ao integrar o SIEM primeiro com o Cloud App Security, atividades e alertas dos últimos dois dias serão encaminhadas para o SIEM e todos os alertas e atividades (com base no filtro que você selecionar) daquele momento em diante. Além disso, se você desabilitar esse recurso por um longo período, quando você habilita-o novamente ele encaminhará os últimos dois dias de alertas e atividades e, em seguida, todos os alertas e atividades daquele momento em diante.

A integração ao SIEM é realizada em três etapas:
1. Configurar no portal do Cloud App Security. 
2. Baixar o arquivo JAR e executá-lo no servidor.
3. Valide se o agente SIEM está funcionando.

## <a name="prerequisites"></a>Pré-requisitos

- Um servidor Windows ou Linux padrão (pode ser uma máquina virtual).
- O servidor deve executar o Java 8. Não há suporte para versões anteriores.

## <a name="integrating-with-your-siem"></a>Integrando ao seu SIEM

### <a name="step-1-set-it-up-in-the-cloud-app-security-portal"></a>Etapa 1: configurar no portal do Cloud App Security

1. No portal do Cloud App Security, na engrenagem Configurações, clique em **Agentes SIEM**.

2. Clique em Adicionar agente SIEM para iniciar o assistente.
3. No assistente, clique em **Adicionar agente SIEM**.    
4. No assistente, preencha um nome, **Selecione o formato do seu SIEM** e defina as **Configurações avançadas** relevantes do formato. Clique em **Avançar**.

   ![Configurações gerais do SIEM](./media/siem1.png)

5. Digite o endereço IP do **Host do syslog remoto** e o **Número da porta do syslog**. Selecione TCP ou UDP como o protocolo do Syslog Remoto.
Você pode consultar seu administrador de segurança para obter esses detalhes caso ainda não os tenha.
Clique em **Avançar**.
  ![Configurações do Syslog Remoto](./media/siem2.png)

6. Selecione quais tipos de dados, **Alertas** e **Atividades** você deseja exportar para o servidor SIEM. Use o controle deslizante para habilitar e desabilitá-los. Por padrão, todas as opções estão marcadas. Você pode usar a lista suspensa **Aplicar a** para definir os filtros para enviarem atividades e alertas específicos ao servidor SIEM.
Você pode clicar em **Editar e visualizar resultados** para verificar se o filtro funciona conforme o esperado. Clique em **Avançar**. 

  ![Configurações de tipos de dados](./media/siem3.png)

7. Copie o token e salve-o para mais tarde. Depois de clicar em Concluir e sair do Assistente, de volta à página SIEM, você poderá ver o agente SIEM adicionado na tabela. Ele exibirá que foi **Criado** até ser conectado posteriormente.

### <a name="step-2-download-the-jar-file-and-run-it-on-your-server"></a>Etapa 2: baixar o arquivo JAR e executá-lo no servidor

1. [Baixe o arquivo .zip no Centro de Download da Microsoft](https://go.microsoft.com/fwlink/?linkid=838596) e descompacte-o.

2. Extraia o arquivo .jar do arquivo zip e execute-o no servidor.
 Depois de executar o arquivo, execute o seguinte:
    
      java -jar mcas-siemagent-0.87.20-signed.jar [--logsDirectory DIRNAME] [--proxy ADDRESS[:PORT]] --token TOKEN
> [!NOTE]
> - O nome do arquivo pode ser diferente dependendo da versão do agente SIEM.
> - Parâmetros em colchetes [] são opcionais e devem ser usados somente se relevantes.

Quando as seguintes variáveis são usadas:
- DIRNAME é o caminho para o diretório que você deseja usar para os logs locais de depuração do agente.
- ADDRESS[:PORT] é o endereço do servidor proxy e a porta que o servidor usa para se conectar à Internet.
- TOKEN é o token do agente SIEM copiado na etapa anterior.

Você pode digitar -h a qualquer momento para obter ajuda.



### <a name="step-3-validate-that-the-siem-agent-is-working"></a>Etapa 3: validar se o agente SIEM está funcionando

1. Verifique se o status do agente SIEM no portal do Cloud App Security não está como **Erro de Conexão** ou **Desconectado** e se não há nenhuma notificação do agente. Ele será exibido como **Erro de Conexão** se a conexão estiver inativa por mais de duas horas e como **Desconectado**, se a conexão estiver inativa por mais de 12 horas.
 ![SIEM desconectado](./media/siem-not-connected.png)
 
   Em vez disso, o status deve ser conectado, conforme visto aqui:  ![SIEM conectado](./media/siem-connected.png)

2. No servidor Syslog/SIEM, verifique se você pode ver os alertas e as atividades que chegam do Cloud App Security.


## <a name="regenerating-your-token"></a>Regenerando o token
Se você perder o token, sempre será possível regenerá-lo clicando nos três pontos ao final da linha do agente SIEM na tabela e selecionando **Regenerar token**.

 ![SIEM – regenerar token](./media/siem-regenerate-token.png)

## <a name="editing-your-siem-agent"></a>Editando o agente SIEM 
Se precisar editar o agente SIEM no futuro, você poderá clicar nos três pontos ao final da linha do agente SIEM na tabela e selecionar **Editar**. Se você editar o agente SIEM, não será necessário executar novamente o arquivo .jar; ele será atualizado automaticamente.

![SIEM – editar](./media/siem-edit.png)

## <a name="deleting-your-siem-agent"></a>Excluindo o agente SIEM
Se precisar excluir o agente SIEM no futuro, você poderá clicar nos três pontos ao final da linha do agente SIEM na tabela e selecionar **Excluir**.

![SIEM – excluir](./media/siem-delete.png)

> [!NOTE]
> Esse recurso está em visualização pública.

## <a name="see-also"></a>Veja também  
[Solução de problemas de integração de SIEM](troubleshooting-siem.md)   
[Para obter suporte técnico, visite a página de suporte assistido do Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Os clientes Premier também podem escolher o Cloud App Security diretamente no Portal Premier.](https://premier.microsoft.com/)  
  
  
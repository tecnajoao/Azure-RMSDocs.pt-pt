---
title: Monitorizar o conector Rights Management – AIP
description: Informações para ajudá-lo a monitorizar o conector e a utilização da organização do serviço Azure Rights Management do Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 12/12/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 8a1b3e54-f788-4f84-b9d7-5d5079e50b4e
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 2d4c03a168f3add9778372a890ea9dd2c7be68bf
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56253868"
---
# <a name="monitor-the-azure-rights-management-connector"></a>Monitorizar o conector Azure Rights Management

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

Após instalar e configurar o conector RMS, pode utilizar os seguintes métodos e as informações para ajudar a monitorizar o conector e a utilização da organização do serviço Azure Rights Management do Azure Information Protection.

## <a name="application-event-log-entries"></a>Registo de eventos da aplicação

O conector RMS utiliza o registo de eventos de Aplicações para registar as entradas para o **conector do Microsoft RMS**. 

Por exemplo, eventos de Informação tais como:

- ID 1000 para confirmar que o serviço do conector foi iniciado

- ID 1002 quando um servidor estabelece corretamente ligação ao conector RMS

- ID 1004 para cada vez que a lista de contas autorizadas (cada conta é listada) é transferida para o conector 

Se não tiver configurado o conector para utilizar HTTPS, espere ver um Aviso de ID 2002, que informa que um cliente está a utilizar uma ligação (HTTP) não segura.

Se houver uma falha na ligação do conector ao serviço Azure Rights Management, é provável que lhe seja apresentado o Erro 3001. Por exemplo, esta falha na ligação poderá dever-se a um problema DNS ou à falta de acesso à Internet para um ou mais servidores que executem o conector RMS. 

> [!TIP]
> Quando os servidores do conector RMS não conseguem ligar ao serviço Azure Rights Management, as configurações de proxy Web são muitas vezes o motivo.

Tal como acontece com todas as entradas de registo de eventos, explore a mensagem para mais detalhes.

Para além de verificar o registo de eventos quando implementa o conector pela primeira vez, verifique a existência de avisos e de erros continuamente. O conector pode funcionar como esperado inicialmente, mas outros administradores poderão alterar as configurações dependentes. Por exemplo, outro administrador altera a configuração de servidor de proxy web para que os servidores do conector RMS já não possam aceder à Internet (Erro 3001), ou remove uma conta de computador a partir de um grupo que especificou como autorizado para utilizar o conector (Aviso 2001).

### <a name="event-log-ids-and-descriptions"></a>IDs e descrições do registo de eventos

Utilize as secções seguintes para identificar os IDs de eventos possíveis, as descrições e qualquer informação adicional.

-----

Informações **1000**

**O serviço Web do conector do Microsoft RMS foi iniciado.**

Este evento é registado quando o conector do RMS tenta primeiro iniciar.

----

Informações **1001**

**O serviço Web do conector do Microsoft RMS foi parado.**

Este evento é registado quando o conector do RMS para como resultado do funcionamento normal. Por exemplo, o IIS é reiniciado ou o computador é encerrado. 

----

Informações **1002**

**O acesso ao conector do Microsoft RMS foi permitido para um servidor autorizado.**

Este evento é registado quando uma conta de um servidor no local se liga ao conector do RMS pela primeira vez, depois de a conta ser autorizada pelo administrador do Azure RMS na ferramenta de administrador do conector do RMS. O SID, o nome de conta e o nome do computador que faz a ligação são incluídos na mensagem do evento.

----

Informações **1003**

**A ligação do cliente listado abaixo mudou de uma ligação de não segura (HTTP) para uma ligação segura (HTTPS).**

Este evento é registado quando um servidor no local muda a ligação do conector do RMS de HTTP (menos seguro) para HTTPS (mais seguro). O SID, o nome de conta e o nome do computador que faz a ligação são incluídos na mensagem do evento.

----

Informações **1004**

**A lista de contas autorizadas foi atualizada.**

Este evento é registado quando o conector do RMS transferiu a lista mais recente de contas (contas existentes e quaisquer alterações) que estão autorizadas a utilizar o conector do RMS. Esta lista é transferida a cada 15 minutos, desde que o conector RMS consiga comunicar com o serviço Azure Rights Management.

----

Aviso **2000**

**O principal de utilizador no contexto HTTP está em falta ou é inválido; verifique se o site do conector do Microsoft RMS tem a Autenticação Anónima desativada no IIS e apenas a Autenticação do Windows está ativada.**

Este evento é registado quando o conector do RMS não consegue identificar exclusivamente a conta que está a tentar ligar ao conector do RMS. Isto poderá ocorrer devido a uma configuração incorreta da autenticação para o IIS ou quando a conta está numa floresta não fidedigna.

----

Aviso **2001**

**Tentativa de acesso não autorizado ao conector do Microsoft RMS.**

Este evento é registado quando uma conta tenta ligar ao conector do RMS, mas falha. Normalmente, este aviso ocorre porque a conta que faz a ligação não está na lista transferida de contas autorizadas que o conector RMS transfere a partir do serviço Azure Rights Management. Por exemplo, a lista mais recente ainda não foi transferida (este evento ocorre a cada 15 minutos) ou a conta está em falta na lista. 

Outra razão pode indicar que o conector do RMS foi instalado no mesmo servidor configurado para utilizar o conector. Por exemplo, instala o conector do RMS num servidor que executa o Exchange Server e está a autorizar a uma conta do Exchange para utilizar o conector. Esta configuração não é suportada porque o conector RMS não consegue identificar corretamente a conta quando tenta ligar.

A mensagem de evento contém informações sobre a conta e o computador que está a tentar ligar ao conector do RMS:

- Se a conta que está a tentar ligar ao conector do RMS for uma conta válida, utilize a ferramenta de administrador do conector do RMS para adicionar a conta à lista de contas autorizadas. Para obter mais informações sobre as contas que devem estar autorizadas, consulte [Adicionar um servidor à lista de servidores permitidos](install-configure-rms-connector.md#add-a-server-to-the-list-of-allowed-servers). 

- Se a conta que está a tentar ligar ao conector do RMS pertencer ao mesmo computador que o servidor do conector do RMS, instale o conector num servidor separado. Para obter mais informações sobre os pré-requisitos para o conector, consulte [Pré-requisitos para o conector do RMS]( deploy-rms-connector.md#prerequisites-for-the-rms-connector).

----

Aviso **2002**

**A ligação do cliente listada abaixo está a utilizar uma ligação (HTTP) não segura.**

Este evento é registado quando um servidor no local liga com êxito ao conector do RMS, mas a ligação utiliza HTTP (menos seguro) em vez de HTTPS (mais seguro). É registado um evento por conta, em vez de por ligação. Este evento é acionado novamente se a conta mudar com êxito para utilização de HTTPS, mas reverte para HTTP.

A mensagem de evento contém a conta de SID, o nome de conta e o nome do computador liga ao conector do RMS.

Para obter informações sobre como configurar o conector do RMS para ligações HTTPS, consulte o [Configurar o conector do RMS para utilizar HTTPS](install-configure-rms-connector.md#configuring-the-rms-connector-to-use-https).

----

Aviso **2003**

**A lista de autorizações está vazia. O serviço só poderá ser utilizado depois de a lista de utilizadores e grupos autorizados do conector ser povoada.**

Este evento é registado quando o conector do RMS não tem uma lista de contas autorizadas, pelo que os servidores no local não podem ligar à mesma. O conector do RMS transfere a lista a cada 15 minutos a partir do Azure RMS. 

Para especificar as contas, utilize a ferramenta de administrador de conector do RMS. Para obter mais informações, consulte [Autorizar os servidores a utilizar o conector do RMS]( install-configure-rms-connector.md#authorizing-servers-to-use-the-rms-connector). 

----

Erro **3000**

**Ocorreu uma exceção não processada no conector do Microsoft RMS.**

Este evento é registado sempre que o conector do RMS encontra um erro inesperado com os detalhes do erro na mensagem de evento.

Uma causa possível pode ser identificada pelo texto **O pedido falhou com uma resposta vazia** na mensagem de evento. Se vir este texto, poderá ser porque tem um dispositivo de rede que está a fazer inspeção de SSL nos pacotes entre os servidores no local e o servidor do conector RMS. O serviço Azure Rights Management não suporta esta configuração, o que resulta numa falha na comunicação e nesta mensagem de registo de eventos.

----

Erro **3001**

**Ocorreu uma exceção ao transferir as informações de autorização.**

Este evento é registado se o conector do RMS não conseguir transferir a lista mais recente de contas que estão autorizadas a utilizar o conector RMS. Os detalhes do erro encontram-se na mensagem de evento.



----

## <a name="performance-counters"></a>Contadores de desempenho

Ao instalar o conector RMS, este cria automaticamente contadores de desempenho do **conector Microsoft Rights Management** que poderão ser úteis para ajudar a monitorizar e a melhorar o desempenho de utilização do serviço Azure Rights Management. 

Por exemplo, ocorrem regularmente atrasos quando os documentos ou os e-mails estão protegidos. Ou ocorrem atrasos quando os documentos ou os e-mails protegidos são abertos. Nestes casos, os contadores de desempenho podem ajudá-lo a determinar se os atrasos são devidos ao tempo de processamento do conector, ao tempo de processamento do serviço Azure Rights Management ou a atrasos da rede. 

Para ajudar a identificar onde está a ocorrer o atraso, procure contadores que incluam contagens de média para o **Tempo de Processamento do Conector**, para o **Tempo de Resposta do Serviço**, e para o **Tempo de Resposta do Conector**. Por exemplo: **Licenciamento com êxito em lotes de tempo de resposta do conector de média de pedido**.

Se tiver adicionado recentemente novas contas de servidor para utilizar o conector, um com contador para verificar é o **Tempo desde a última atualização da política de autorização**, para confirmar que o conector transferiu a lista desde que a atualizou, ou se terá de aguardar um pouco mais (até 15 minutos).

## <a name="logging"></a>Registo

O registo de utilização ajuda-o a identificar quando os e-mails e os documentos são protegidos e consumidos. Quando o conector RMS serve para proteger e consumir conteúdo, o campo de ID de utilizador nos registos contém o nome do principal do serviço de **Aadrm_S-1-7-0**. Este nome é automaticamente criado para o conector RMS.

Para obter mais informações sobre o registo de utilização, consulte [Registar e analisar a utilização do serviço Azure Rights Management](log-analyze-usage.md).

Caso precise de um registo mais detalhado para fins de diagnóstico, pode utilizar o [Debugview](https://go.microsoft.com/fwlink/?LinkID=309277) do Windows Sysinternals. Ative o rastreio para o conector RMS modificando o ficheiro web.config para o Site predefinido no IIS:

1. Localize o ficheiro web.config em **%programfiles%\Microsoft Rights Management connector\Web Service**.

2. Localize a seguinte linha:

        <trace enabled="false" requestLimit="10" pageOutput="false" traceMode="SortByTime" localOnly="true"/>

3. Substitua essa linha com o seguinte texto:

        <trace enabled="true" requestLimit="10" pageOutput="false" traceMode="SortByTime" localOnly="true"/>

4.  Pare e inicie o IIS para ativar o rastreio. 

5.  Quando tiver capturado os rastreios que necessita, reverta a linha do passo 3, e pare e iniciar o IIS novamente.


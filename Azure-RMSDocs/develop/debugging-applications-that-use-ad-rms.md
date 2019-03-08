---
title: Procedimentos sobre como depurar uma aplicação com capacidade para direitos | Azure RMS
description: O tópico seguinte mostra como depurar a aplicação e utilizar o Registo de Eventos do Windows.
keywords: ''
author: msmbaldwin
ms.author: mbaldwin
manager: barbkess
ms.date: 02/23/2017
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 6F6C7651-6A6E-45DD-A0C5-F036F803249B
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 58791e2ac3070a8cde1ee9307544d9bc35ab2f40
ms.sourcegitcommit: 471b3683367d93f0673c1cf276a15f83572aa80e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57329884"
---
# <a name="how-to-debug-a-rights-enabled-application"></a>Procedimentos: depurar uma aplicação com permissão para direitos

O tópico seguinte mostra como depurar a aplicação e utilizar o Registo de Eventos do Windows.

## <a name="debugging-your-application"></a>Depurar a aplicação

No SDK Rights Management Services 2.1, as verificações antidepuração na versão de programador do nosso tempo de execução estão desativadas.

Pode ativar o rastreio de depuração utilizando a seguinte chave de registo. (Para desativar o rastreio de depuração, altere o valor para 0.) Não é necessário mais nada para a depuração nesta versão.


```
HKEY_LOCAL_MACHINE
   SOFTWARE
      Microsoft
         MSIPC
            "Trace" = 00000001
            Data type
            dword
```

### <a name="application-logging-by-using-the-windows-event-log"></a>Registo de aplicações ao utilizar o Registo de Eventos do Windows

O nome do registo de eventos é “Microsoft-RMS-MSIPC/Depuração”. Isto significa que, no Visualizador de Eventos do Windows, o seu registo aparece como “Registos de Aplicações e Serviços\\Microsoft\\RMS\\MSIPC\\Depuração”.

**Tenha em atenção**  o registo está ativado por predefinição e definido para verbosidade de nível 3.

 

Para alterar as definições da funcionalidade de registo, pode utilizar a IU do Visualizador de Eventos do Windows ou o Wevtutil, uma ferramenta de linha de comandos incorporada no Windows.

Através da interface do Wevtutil, pode controlar o nível de verbosidade do seu registo.

De momento, suportamos 3 níveis de registo:

-   Nível 2 – Erro
-   Nível 3 – Aviso
-   Nível 4 – Informações

Por exemplo, o comando seguinte ativa o registo de eventos MSIPC e define o nível de verbosidade para informações.

**wevtutil sl Microsoft-RMS-MSIPC/Debug /e:true /l:4**

**Tenha em atenção**  no the Windows Visualizador de eventos no **vista** menu, selecione **Mostrar depurar registos analíticos e** para tornar o registo de depuração MSIPC visíveis.

---
title: "Procedimentos sobre como depurar uma aplicação com capacidade para direitos | Azure RMS"
description: "O tópico seguinte mostra como depurar a aplicação e utilizar o Registo de Eventos do Windows."
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 6F6C7651-6A6E-45DD-A0C5-F036F803249B
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: adab957779dac2baec22cb73b060f9a8a0075a1a
ms.sourcegitcommit: 93124ef58e471277c7793130f1a82af33dabcea9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/11/2018
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

**Nota** O registo está ativado por predefinição e definido para verbosidade de nível 3.

 

Para alterar as definições da funcionalidade de registo, pode utilizar a IU do Visualizador de Eventos do Windows ou o Wevtutil, uma ferramenta de linha de comandos incorporada no Windows.

Através da interface do Wevtutil, pode controlar o nível de verbosidade do seu registo.

De momento, suportamos 3 níveis de registo:

-   Nível 2 – Erro
-   Nível 3 – Aviso
-   Nível 4 – Informações

Por exemplo, o comando seguinte ativa o registo de eventos MSIPC e define o nível de verbosidade para informações.

**wevtutil sl Microsoft-RMS-MSIPC/Debug /e:true /l:4**

**Nota** No Visualizador de Eventos do Windows, no menu **Ver**, selecione **Mostrar Registos Analíticos e de Depuração** para tornar visível o registo de depuração MSIPC.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
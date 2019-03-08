---
title: Como&#58; ativar registo de erros e de desempenho | Azure RMS
description: O Microsoft Rights Management SDK 4.2 gere o diagnóstico e de desempenho o carregamento de registos através de uma propriedade de único dispositivo.
keywords: ''
author: msmbaldwin
ms.author: mbaldwin
manager: barbkess
ms.date: 02/23/2017
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: F5AD3826-2292-4A25-AF5C-D17D083F5742
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 93975ad0f2113fc10bff3f54f0b6729dfa33bad3
ms.sourcegitcommit: 471b3683367d93f0673c1cf276a15f83572aa80e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57331856"
---
# <a name="how-to-enable-error-and-performance-logging"></a>Como: Ativar o registo de desempenho e de erro
O Microsoft Rights Management SDK 4.2 gere o diagnóstico e de desempenho o carregamento de registos através de uma propriedade de único dispositivo.

## <a name="overview"></a>Descrição geral ##
Pode melhorar a experiência e resolução de problemas dos utilizadores ao permitir o carregamento de diagnósticos automáticos, registos de telemetria e desempenho para a Microsoft. 

> [!IMPORTANT] 
> Para honrar a privacidade do utilizador, na qualidade de programador da aplicação, deve pedir consentimento ao utilizador antes de ativar o registo automático.

> [!NOTE]
> Como exemplo, eis uma mensagem padrão que a Microsoft utiliza para notificações de registos: 
>
> *Ao ativar os Registos de Desempenho e de Erros, está a concordar em enviar Dados de Desempenho e de Erros para a Microsoft.  A Microsoft irá recolher dados de desempenho e de erros através da Internet ("Dados").  A Microsoft utiliza estes Dados para fornecer e melhorar a qualidade, segurança e integridade dos produtos e serviços da Microsoft.  Por exemplo, analisamos o desempenho e a fiabilidade, como as funcionalidades que utiliza, o tempo de resposta das funcionalidades, o desempenho do dispositivo, as interações de interface de utilizador e os problemas que possa ter com o produto.  Os Dados também incluirão informações acerca da configuração do seu software, como o software que está a utilizar atualmente e o endereço IP.*  

Irá gerir o controlo de registo através de duas propriedades.

-   Ative o registo através da propriedade **IpcCustomerExperienceDataCollectionEnabled**. A definição resiste às reposições do dispositivo.
-   Controle o nível de registo através da propriedade **IpcLogLevel** ao utilizar as seguintes definições.

    * 1 – Verboso
    * 2 – Informativo
    * 3 – Aviso
    * 4 – Erro
    * 5 – Crítico

Em cada um dos fragmentos de código de exemplo que se seguem, a aplicação de chamada pode definir ou consultar a propriedade.

### <a name="android"></a>Android ###
Ativar o registo automático

    SharedPreferences preferences = PreferenceManager.getDefaultSharedPreferences(context);
    SharedPreferences.Editor editor = preferences.edit();
    editor.putBoolean(&quot;IpcCustomerExperienceDataCollectionEnabled&quot;, true);
    editor.commit();

Obter a definição atual do sinalizador de controlo de registo

    SharedPreferences preferences = PreferenceManager.getDefaultSharedPreferences(context);
    Boolean isLogUploadEnabled = preferences.getBoolean(&quot;IpcCustomerExperienceDataCollectionEnabled&quot;, false);

## <a name="ios"></a>iOS ##
Ativar o registo automático

    NSUserDefaults \*prefs = [NSUserDefaults standardUserDefaults];
        [prefs setBool:FALSE forKey:@&quot;IpcCustomerExperienceDataCollectionEnabled”];
        [[NSUserDefaults standardUserDefaults] synchronize];

Obter a definição atual do sinalizador de controlo de registo

    [[NSUserDefaults standardUserDefaults] boolForKey:@&quot;IpcCustomerExperienceDataCollectionEnabled&quot;];

Definir o controlo do nível de registo

    NSUserDefaults \*prefs = [NSUserDefaults standardUserDefaults];
      [prefs setInteger:1 forKey:@&quot;IpcLogLevel”];
      [[NSUserDefaults standardUserDefaults] synchronize];

Obter a definição de controlo do nível de registo

    [[NSUserDefaults standardUserDefaults] boolForKey:@&quot;IpcLogLevel&quot;];
 

## <a name="windows"></a>Windows ##
Ativar o registo automático

    CustomerExperienceConfiguration::Option = CustomerExperienceOptions::LoggingEnabledNow;

Para obter mais informações sobre definições opcionais, consulte [CustomerExperienceOptions](https://msdn.microsoft.com/library/microsoft.rightsmanagement.customerexperienceoptions.aspx).

Obter a definição atual do sinalizador de controlo de registo

    CustomerExperienceOptions loggingOption = CustomerExperienceConfiguration::Option;


**Nota** – Os recortes de código Windows acima são em C++. Para C\#, atualize a sintaxe com ‘.’ em vez de ‘::’.

**Linux/C++** – Este SDK possui algum registo básico que não é tão extensivo como o de outras plataformas. Para mais informações, consulte a secção **Resolução de problemas** do "LEIAME.md" em [SDK RMS para Portable C++](https://github.com/AzureAD/rms-sdk-for-cpp#troubleshooting).

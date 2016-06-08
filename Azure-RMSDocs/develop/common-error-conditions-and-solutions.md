---
# required metadata

title: Condições de erro comuns e soluções | Azure RMS
description: Este tópico inclui as mensagens de erro mais comuns que poderá encontrar ao utilizar as ferramentas de programador do SDK RMS 2.1.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: A5B95EB8-3528-4CFF-86FC-166613A5F4A3
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---
** Este conteúdo do SDK não está atualizado. Durante um curto período de tempo, pode encontrar a [versão atual](https://msdn.microsoft.com/library/windows/desktop/hh535290(v=vs.85).aspx) da documentação no MSDN. **
# Condições de erro comuns e soluções
Este tópico inclui as mensagens de erro mais comuns que poderá encontrar ao utilizar as ferramentas de programador do SDK Rights Management Services 2.1. Também inclui uma ação recomendada para corrigir o erro, quando aplicável.

**Importante** – Para o processamento da condição de erro, utilize sempre uma chamada para [IpcGetErrorMessageText](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgeterrormessagetext) imediatamente após a falha de uma chamada da API do SDK, para poder obter informações completas acerca da natureza do erro.

 

## Erro e a ação ##
A lista abaixo contém uma lista de constantes de erros, a respetiva descrição associada e uma ação sugerida para resolver a condição de erro.

**ERRO** - *IPCERROR_DEBUGGER_DETECTED* - Um depurador foi detetado pelo RMS SDK 2.1

**AÇÃO** – A versão do programador do SDK RMS 2.1 não verifica a presença de um depurador. Se for possível, depure a aplicação ao utilizar esta versão do SDK RMS 2.1.
Se tiver de depurar a versão de produção do SDK RMS 2.1, utilize as seguintes orientações.

Algumas funções do SDK RMS 2.1 foram concebidas para falhar com um depurador:
- [IpcGetKey</strong>](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgetkey)
- [IpcGetTemplateList](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgettemplatelist)
- [IpcGetTemplateIssuerList](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgettemplateissuerlist)

Para depurar código no seguimento destas chamadas de função, tem de aceder ao processo e anexar um depurador após a conclusão das chamadas de função. Uma forma de o fazer é utilizar uma instrução de asserção para aceder ao depurador. A macro ASSERTE está incluída no cabeçalho *Crtdbg.h*.
Para mais informações acerca de \_ASSERTE, consulte [\_Macros ASSERT, \_ASSERTE](https://msdn.microsoft.com/en-us/library/ezb1wyez.aspx)

**ERRO** - *IPCERROR_BROKEN_CERT_CHAIN* - A cadeia de certificados não coincide.

**AÇÃO** – Certifique-se de que a chave de hierarquia contém o valor correto com base na chave utilizada para assinar o manifesto da aplicação AD RMS.
Estas são as chaves de assinatura e os respetivos valores associados (hierarquia **DWORD**):
- ISV—1
- Produção—0 ou não presente

**ERRO** - *IPCERROR_MACHINE_CERT_NOT_TRUSTED* - Está a utilizar uma aplicação assinada com a chave de assinatura de ISV, mas está a tentar comunicar com um servidor do AD RMS de produção ou vice-versa.

- Se estiver a utilizar a versão do programador do servidor AD RMS, certifique-se de que está a utilizar a chave de assinatura de ISV para assinar a aplicação.
- Se estiver a utilizar a versão de produção do servidor AD RMS, certifique-se de que está a utilizar a chave de assinatura de produção para assinar a aplicação.

**ERRO** - *IPCERROR_APPLICATION_AUTH_ERROR_MANIFEST* - O manifesto da aplicação não é válido. Isto pode acontecer quando o binário (aplicação) foi reconstruído e o manifesto não foi regenerado.

**AÇÃO** – Certifique-se de que regenera o manifesto da aplicação sempre que reconstruir a aplicação.

## Tópicos relacionados ##
* [Notas do programador](developer-notes.md)
* [IpcGetKey](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgetkey)
* [IpcGetTemplateList](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgettemplatelist)
* [IpcGetTemplateIssuerList](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgettemplateissuerlist)
* [\_Macros ASSERT, \_ASSERTE](https://msdn.microsoft.com/en-us/library/ezb1wyez.aspx)
 

 


<!--HONumber=Jun16_HO1-->



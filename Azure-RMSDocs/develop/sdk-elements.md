---
title: Ficheiros do ambiente de desenvolvimento | Azure RMS
description: "Este tópico mostra os ficheiros do ambiente de desenvolvimento e as respetivas localizações de instalação no computador."
keywords: 
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: B57AC6F3-733C-42A8-AF83-0E15FBF27C99
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7068e0529409eb783f16bc207a17be27cd5d82a8
ms.openlocfilehash: 6443c1955db5ab25caea349575cb376a6ce8dac2


---

# <a name="development-environment-files"></a>Ficheiros do ambiente de desenvolvimento

Este tópico mostra os ficheiros do ambiente de desenvolvimento e as respetivas localizações de instalação no computador.

O SDK Rights Management Services 2.1 inclui os seguintes ficheiros, instalados no computador na localização predefinida ou na localização que especificou: %MsipcSDKDir%.

|Ficheiro|Caminho|Descrição|
|----|----|-----------|
|Leiame.htm| \ | Contém uma ligação para a ajuda e as [Notas de versão](release-notes-rtm.md) do RMS.|
|Isvtier5appsigningprivkey.dat|\bin|Contém a chave privada utilizada para gerar um manifesto para utilização durante o desenvolvimento de uma aplicação com capacidade para RMS.|
|Isvtier5appsigningpubkey.dat|\bin|Contém a chave pública utilizada para gerar um manifesto para utilização durante o desenvolvimento de uma aplicação com capacidade para RMS.|
|Isvtier5appsignsdk_client.xml|\bin|Usado para gerar um manifesto para utilização durante o desenvolvimento de uma aplicação com capacidade para RMS.|
|NomeDaAplicação.isv.mcf|\bin|Um ficheiro de configuração de manifesto automático que pode utilizar para gerar um manifesto durante o desenvolvimento de uma aplicação com capacidade para RMS.|
|Ipcsecproc_isv.dll|\bin\x86|DLL utilizado internamente, para aplicações x86, pelo Cliente dos Serviços de Gestão de Direitos do Active Directory 2.1 quando funciona na hierarquia de ISV.|
|Ipcsecproc_ssp_isv.dll|\bin\x86|DLL utilizado internamente, para aplicações x86, pelo AD RMS 2.1 quando funciona na hierarquia de ISV.|
|Ipcsecproc_isv.dll|\bin\x64|DLL utilizado internamente, para aplicações x64, pelo Cliente de AD RMS 2.1 quando funciona na hierarquia de ISV.|
|Ipcsecproc_ssp_isv.dll|\bin\x64|DLL utilizado internamente, para aplicações x64, pelo Cliente de AD RMS 2.1 quando funciona na hierarquia de ISV.|
|Msipc.h|\inc|Ficheiro de inclusão principal do SDK RMS 2.1.|
|Ipcprot.h|\inc|Contém a interface pública exportada pelo SDK RMS 2.1.|
|Ipcbase.h|\inc|Contém tipos básicos e funções de programa auxiliar exportados pelo SDK RMS 2.1.|
|Ipcerror.h|\inc|Contém os códigos de erro públicos exportados pelo SDK RMS 2.1.|
|Ipcfile.h|\inc|Contém as interfaces da API de Ficheiros exportadas pelo SDK RMS 2.1.|
|Msipc.lib|\lib|Biblioteca de ligação ao utilizar o SDK RMS 2.1 para criar aplicações x86.|
|Msipc_s.lib|\lib|Fornece o ponto de entrada de [IpcInitialize](https://msdn.microsoft.com/library/jj127295.aspx) para aplicações x86.|
|Msipc.lib|\lib\x64|Biblioteca de ligação ao utilizar o SDK RMS 2.1 para criar aplicações x64.|
|Msipc_s.lib|\lib\x64|Fornece o ponto de entrada de [IpcInitialize](https://msdn.microsoft.com/library/jj127295.aspx) para aplicações x64.|
|Genmanifest.exe|\tools|Gera um manifesto para utilização durante o desenvolvimento de uma aplicação com capacidade para RMS.|

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


<!--HONumber=Jan17_HO1-->



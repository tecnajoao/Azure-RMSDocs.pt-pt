---
title: Formatos de ficheiro suportados | Azure RMS
description: "A versão atual da API de Ficheiros suporta a proteção nativa para ficheiros do MS Office e PDF e a proteção PFile para todos os outros formatos de ficheiro."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 08/24/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: EC831494-7F2C-4C70-9063-B02CDDEA14EE
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 024a29d7c7db2e4c0578a95c93e22f8e7a5b173e
ms.openlocfilehash: e41d8d697d7c35beef84277bc5b9fd497d79cc10


---

# Formatos de ficheiro suportados

A API de Ficheiros suporta formatos nativos e Pfile.

## Formatos de Ficheiro Suportados

A versão atual da API de Ficheiros suporta a proteção nativa para ficheiros do Microsoft Office e PDF (Portable Document Files) e a proteção PFile para todos os outros formatos de ficheiro. Os ficheiros PDF podem, opcionalmente, ter a proteção PFile aplicada.

-   **Proteção nativa**. Na proteção nativa, o ficheiro é encriptado para um formato de ficheiro do AD RMS que é baseado no respetivo tipo de MIME (extensão de nome de ficheiro). Os ficheiros que estão protegidos nativamente através da API de Ficheiros estão em conformidade com o formato esperado pelas aplicações com suporte AD RMS que utilizam a proteção nativa; por exemplo, Office 2013, Office 2010 e o leitor de PDF FoxIt. A proteção nativa é suportada apenas em ficheiros do Office, ficheiros PDF e num número selecionado de outros tipos de ficheiro. Para obter mais informações acerca dos tipos de ficheiro nos quais é suportada a proteção nativa, consulte [Configuração da API de Ficheiros](file-api-configuration.md).
-   **Proteção PFile**. Na proteção PFile, os ficheiros são encriptados através do formato de Ficheiro Protegido (PFile) do AD RMS. O ficheiro é encriptado para um ficheiro com uma extensão .pfile. A proteção PFile é suportada para todos os formatos de ficheiro, exceto ficheiros do Office.

Os administradores podem definir chaves de registo para configurar se e como os ficheiros devem ser protegidos com base na respetiva extensão do nome do ficheiro. Para obter mais informações sobre como configurar a proteção de ficheiros quando utilizar a API de Ficheiros, consulte [Configuração da API de Ficheiros](file-api-configuration.md).

## Tópicos relacionados

* [Notas do programador](developer-notes.md)
* [Configuração da API de Ficheiros](file-api-configuration.md)
 

 



<!--HONumber=Aug16_HO4-->



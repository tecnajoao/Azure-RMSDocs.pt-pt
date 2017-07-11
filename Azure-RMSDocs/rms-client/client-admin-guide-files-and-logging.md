---
title: "Registo de utilização e de ficheiros do cliente do Azure Information Protection"
description: "Informações sobre o registo de utilização e ficheiros do cliente do Azure Information Protection para Windows."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 5a34ab85-773f-4782-ba09-c321cddf5bc0
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: bf695772d545daca602903e156903da2aadaae7a
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/30/2017
---
<a id="azure-information-protection-client-files-and-client-usage-logging" class="xliff"></a>

# Registo de utilização do cliente e de ficheiros do cliente do Azure Information Protection

>*Aplica-se a: Serviços de Gestão de Direitos do Active Directory, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 with SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012*

Depois de instalar o cliente do Azure Information Protection, poderá precisar de saber onde estão localizados os ficheiros e monitorizar a forma como o cliente está a ser utilizado.

<a id="file-locations-for-the-azure-information-protection-client" class="xliff"></a>

## Localizações dos ficheiros do cliente do Azure Information Protection

Ficheiros de cliente:   

- Para sistemas operativos de 64 bits: **\ProgramFiles (x86)\Microsoft Azure Information Protection**

- Para sistemas operativos de 32 bits: **\Program Files\Microsoft Azure Information Protection**

Ficheiros de registo de cliente e ficheiro da política atualmente instalada:

- Sistemas operativos de 64 bits e de 32 bits: **%localappdata%\Microsoft\MSIP**

<a id="usage-logging-for-the-azure-information-protection-client" class="xliff"></a>

## Registo de utilização do cliente do Azure Information Protection

O cliente regista a atividade do utilizador no registo de eventos locais **Aplicações e Serviços** do Windows, **Azure Information Protection**. Os eventos incluem as seguintes informações:

- Data, versão do cliente, ID de política

- Nome de utilizador da sessão iniciada, nome do computador

- Nome e localização do ficheiro

- Ação:

    - Definir Etiqueta: ID de Informações 101
    
    - Definir Etiqueta (inferior): ID de Informações 102
    
    - Definir Etiqueta (superior): ID de Informações 103
    
    - Remover etiqueta: ID de Informações 104
   
    - Sugestão recomendada: Informações 105
    
    - Aplicar proteção personalizada: ID de Informações 201
    
    - Remover proteção personalizada: ID de Informações 202
    
    - Início de Sessão (operacional): ID de informações 902
    
    - Transferir política (operacional): ID de informações 901
    
- Origem da ação:
    
    - Manual 
    
    - Recomendado
    
    - Automático  
    
    - Sistema (para iniciar sessão e transferir a política)
    
- Etiqueta antes e depois da ação 
    
- Proteção antes e depois da ação
    
- Justificação do utilizador (quando aplicável)
    

Para obter mais informações sobre o registo de utilização do serviço Azure Rights Management, veja [Registar e analisar a utilização do serviço Azure Rights Management](../deploy-use/log-analyze-usage.md)



<a id="next-steps" class="xliff"></a>

## Passos seguintes
Agora que identificou todos os ficheiros de registo associados ao cliente do Azure Information Protection, veja o seguinte para obter informações adicionais que poderá precisar para suportar este cliente:

- [Personalizações](client-admin-guide-customizations.md)

- [Controlo de documentos](client-admin-guide-document-tracking.md)

- [Tipos de ficheiro suportados](client-admin-guide-file-types.md)

- [Comandos do PowerShell](client-admin-guide-powershell.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

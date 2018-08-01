---
title: Registo de utilização e de ficheiros do cliente do Azure Information Protection
description: Informações sobre o registo de utilização e ficheiros do cliente do Azure Information Protection para Windows.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/29/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 5a34ab85-773f-4782-ba09-c321cddf5bc0
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 74cd50008213b9a78745a14e7753d252b1adcf53
ms.sourcegitcommit: 44ff610dec678604c449d42cc0b0863ca8224009
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/31/2018
ms.locfileid: "39374642"
---
# <a name="admin-guide-azure-information-protection-client-files-and-client-usage-logging"></a>Guia do administrador: Ficheiros de cliente do Azure Information Protection e o registo de utilização do cliente

>*Aplica-se a: serviços de gestão de direitos do Active Directory [do Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 com SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

Depois de instalar o cliente do Azure Information Protection, poderá precisar de saber onde estão localizados os ficheiros e monitorizar a forma como o cliente está a ser utilizado.

## <a name="file-locations-for-the-azure-information-protection-client"></a>Localizações dos ficheiros do cliente do Azure Information Protection

Ficheiros de cliente:   

- Para sistemas operativos de 64 bits: **\ProgramFiles (x86)\Microsoft Azure Information Protection**

- Para sistemas operativos de 32 bits: **\Program Files\Microsoft Azure Information Protection**

Ficheiros de registo de cliente e ficheiro da política atualmente instalada:

- Sistemas operativos de 64 bits e de 32 bits: **%localappdata%\Microsoft\MSIP**

## <a name="usage-logging-for-the-azure-information-protection-client"></a>Registo de utilização do cliente do Azure Information Protection

O cliente regista a atividade do utilizador para o registo de eventos do Windows local **Applications and Services Logs** > **do Azure Information Protection**. Os eventos incluem as seguintes informações:

- Versão do cliente, ID de política

- Endereços IP do utilizador com sessão iniciada

- Nome e localização do ficheiro

- Ação:

    - Definir Etiqueta: ID de Informações 101
    
    - Definir etiqueta (inferior): 101 de ID de informações
    
    - Definir etiqueta (superior): 101 de ID de informações
    
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
    
    - Predefinido
    
- Etiqueta antes e depois da ação 
    
- Proteção antes e depois da ação
    
- Justificação do utilizador (quando aplicável)

- Permissões personalizadas (quando aplicável) que inclui a [direitos de utilização pelo respetivo nome de codificação](../deploy-use/configure-usage-rights.md#usage-rights-and-descriptions) para os utilizadores especificados, grupos ou organizações
    
Para obter informações sobre o registo de utilização para o serviço de proteção, consulte [registar e analisar a utilização do serviço Azure Rights Management](../deploy-use/log-analyze-usage.md)



## <a name="next-steps"></a>Passos Seguintes
Agora que identificou todos os ficheiros de registo associados ao cliente do Azure Information Protection, veja o seguinte para obter informações adicionais que poderá precisar para suportar este cliente:

- [Personalizações](client-admin-guide-customizations.md)

- [Controlo de documentos](client-admin-guide-document-tracking.md)

- [Tipos de ficheiro suportados](client-admin-guide-file-types.md)

- [Comandos do PowerShell](client-admin-guide-powershell.md)


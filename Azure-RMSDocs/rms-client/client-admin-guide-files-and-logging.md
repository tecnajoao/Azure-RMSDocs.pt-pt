---
title: Registo de utilização e de ficheiros do cliente do Azure Information Protection
description: Informações sobre o registo de utilização e ficheiros do cliente do Azure Information Protection para Windows.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 03/11/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 5a34ab85-773f-4782-ba09-c321cddf5bc0
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 72e29d19ddbfc3189d498724fc8353829820ab4e
ms.sourcegitcommit: f4fe64474999954e0c013c3901edbb3048670935
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/10/2019
ms.locfileid: "57725754"
---
# <a name="admin-guide-azure-information-protection-client-files-and-client-usage-logging"></a>Guia do administrador: Registo de utilização do cliente e de ficheiros do cliente do Azure Information Protection

>*Aplica-se a: Serviços de gestão de direitos do Active Directory [do Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 com SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

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

    - Definir etiqueta: ID de informações 101
    
    - Definir etiqueta (inferior): ID de informações 101
    
    - Definir etiqueta (superior): ID de informações 101
    
    - Remova etiqueta: ID de informações 104
    
    - Descrição da etiqueta recomendada: Informações 105
    
    - Aplica proteção personalizada: ID de informações 201
    
    - Remova proteção personalizada: ID de informações 202
    
    - Outlook avisar a mensagem: ID de informações 301
    
    - Outlook justificar a mensagem: ID de informações 302
    
    - Mensagem de bloqueio do Outlook: ID de informações 303
    
    - Início de sessão (operacional): ID de informações 902
    
    - Transferir política (operacional): ID de informações 901
    
- Origem da ação:
    
    - Manual 
    
    - Recomendado
    
    - Automático  
    
    - Sistema (para iniciar sessão e transferir a política)
    
    - Predefinição
    
- Etiqueta antes e depois da ação 
    
- Proteção antes e depois da ação
    
- Justificação do utilizador (quando aplicável)

- Permissões personalizadas (quando aplicável) que inclui a [direitos de utilização pelo respetivo nome de codificação](../configure-usage-rights.md#usage-rights-and-descriptions) para os utilizadores especificados, grupos ou organizações

Os eventos para o Outlook avisar justificar e bloquear mensagens requer que o cliente de pré-visualização e definições de cliente avançadas. Para obter mais informações, consulte [implementar mensagens pop-up no Outlook que avisar, justificar ou bloquear mensagens de e-mail a ser enviadas](client-admin-guide-customizations.md#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent).

Para obter informações sobre o registo de utilização para o serviço de proteção, consulte [registar e analisar a utilização do serviço Azure Rights Management](../log-analyze-usage.md).

## <a name="next-steps"></a>Passos Seguintes
Agora que identificou todos os ficheiros de registo associados ao cliente do Azure Information Protection, veja o seguinte para obter informações adicionais que poderá precisar para suportar este cliente:

- [Personalizações](client-admin-guide-customizations.md)

- [Controlo de documentos](client-admin-guide-document-tracking.md)

- [Tipos de ficheiro suportados](client-admin-guide-file-types.md)

- [Comandos do PowerShell](client-admin-guide-powershell.md)


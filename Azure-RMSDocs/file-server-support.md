---
title: Como servidores de ficheiros que utilizam FCI suportam o Azure RMS do AIP
description: Como a Infraestrutura de Classificação de Ficheiros do Windows Server pode ser utilizada com o Azure RMS quando implementar o conector RMS para proteger automaticamente documentos do Office.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/28/2018
ms.topic: article
ms.service: information-protection
ms.assetid: 8fdad425-5daf-4ce1-822f-9d2fb0b87df1
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 5df573af6350e26300569b9e7952de2d78bce081
ms.sourcegitcommit: b0c4fe8c522987a7863958ffdc6866a91ebabf86
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/29/2018
ms.locfileid: "43242147"
---
# <a name="how-file-servers-that-run-windows-server-and-use-file-classification-infrastructure-fci-support-azure-rights-management"></a>Como os servidores de ficheiros que executam o Windows Server e utilizam a infraestrutura de classificação de ficheiros (FCI) suportam o Azure Rights Management

>*Aplica-se a: [do Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*


Quando configura o Windows Server para utilizar a Infraestrutura de Classificação de Ficheiros, esta funcionalidade do Gestor de Recursos de Servidor de Ficheiros pode analisar ficheiros locais e determinar se contêm dados sensíveis. Os ficheiros que obedecem a estes critérios são etiquetados com propriedades de classificação definidas por um administrador. A Infraestrutura de Classificação de Ficheiros pode então tomar uma ação automática, de acordo com a classificação. Uma destas ações inclui aplicar a proteção de dados com o Azure Rights Management e a implementação do conector Rights Management (também conhecido como conector RMS). Os ficheiros do Office são então automaticamente protegidos pelo Azure RMS.

Para proteger todos os tipos de ficheiro, não utilize o conector RMS, mas em vez disso, executar um script de Windows PowerShell que utiliza os cmdlets dos [módulo do Azure Information Protection](./rms-client/client-admin-guide-powershell.md).

As políticas de classificação são totalmente configuráveis e altamente extensíveis para que possa impedir potenciais fugas de dados de utilizadores autorizados e não autorizados. Podem inclusivamente ajudar a reduzir o risco de fuga de dados por administradores de rede, porque pode configurar políticas que não exijam que estes administradores tenham acesso aos ficheiros.

Para obter instruções para implementar e configurar o conector RMS para ficheiros do Office, consulte [Implementar o conector Azure Rights Management](deploy-rms-connector.md).

Para obter instruções para utilizar o script do Windows PowerShell para todos os tipos de ficheiros, consulte [Proteção RMS com Infraestrutura de Classificação de Ficheiros &#40;FCI&#41; do Windows Server](./rms-client/configure-fci.md).



## <a name="next-steps"></a>Passos Seguintes
Agora que compreende como as aplicações e os serviços suportam o Azure RMS, pode estar interessado em comparar o Azure RMS com a versão no local do Rights Management, os Serviços de Gestão de Direitos do Active Directory (AD RMS). Para obter uma comparação de funcionalidades, requisitos e controlos de segurança, consulte [Comparar o Azure Rights Management e o AD RMS](compare-on-premise.md).



---
title: "Servidores de ficheiros que utilizam FCI –AIP"
description: "Como a Infraestrutura de Classificação de Ficheiros do Windows Server pode ser utilizada com o Azure RMS quando implementar o conector RMS para proteger automaticamente documentos do Office."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/17/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 8fdad425-5daf-4ce1-822f-9d2fb0b87df1
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 7f49fc1613afcfdbad1f1f13e827a866b8ebe6f9
ms.sourcegitcommit: 0fd2e63822280ec96ab957e22868c63de9ef3d47
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/18/2017
---
# <a name="file-servers-that-run-windows-server-and-use-file-classification-infrastructure-fci"></a>Servidores de ficheiros que executam o Windows Server e utilizam a Infraestrutura de Classificação de Ficheiros (FCI)

>*Aplica-se a: Azure Information Protection, Office 365*


Quando configura o Windows Server para utilizar a Infraestrutura de Classificação de Ficheiros, esta funcionalidade do Gestor de Recursos de Servidor de Ficheiros pode analisar ficheiros locais e determinar se contêm dados sensíveis. Os ficheiros que obedecem a estes critérios são etiquetados com propriedades de classificação definidas por um administrador. A Infraestrutura de Classificação de Ficheiros pode então tomar uma ação automática, de acordo com a classificação. Uma destas ações inclui aplicar proteção de informações ao utilizar o [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] e a implementação do conector Rights Management (também conhecido como conector RMS). Os ficheiros do Office são então automaticamente protegidos pelo Azure RMS.

Para proteger todos os tipos de ficheiros, não deverá utilizar o conector RMS, mas, em vez disso, deverá executar um script do Windows PowerShell que utilize os cmdlets do [módulo do Azure Information Protection](../rms-client/client-admin-guide-powershell.md).

As políticas de classificação são totalmente configuráveis e altamente extensíveis para que possa impedir potenciais fugas de dados de utilizadores autorizados e não autorizados. Podem inclusivamente ajudar a reduzir o risco de fuga de dados por administradores de rede, porque pode configurar políticas que não exijam que estes administradores tenham acesso aos ficheiros.

Para obter instruções para implementar e configurar o conector RMS para ficheiros do Office, consulte [Implementar o conector Azure Rights Management](../deploy-use/deploy-rms-connector.md).

Para obter instruções para utilizar o script do Windows PowerShell para todos os tipos de ficheiros, consulte [Proteção RMS com Infraestrutura de Classificação de Ficheiros &#40;FCI&#41; do Windows Server](../rms-client/configure-fci.md).



## <a name="next-steps"></a>Próximos passos
Agora que compreende como as aplicações e os serviços suportam o Azure RMS, pode estar interessado em comparar o Azure RMS com a versão no local do Rights Management, os Serviços de Gestão de Direitos do Active Directory (AD RMS). Para obter uma comparação de funcionalidades, requisitos e controlos de segurança, consulte [Comparar o Azure Rights Management e o AD RMS](compare-azure-rms-ad-rms.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


---
title: "Saber se os utilizadores se inscreveram no RMS para indivíduos – AIP"
description: "Como administrador, como sabe se os seus utilizadores se inscreveram no RMS para indivíduos? Pode utilizar qualquer um ou uma combinação dos métodos descritos neste artigo."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: a36c3d99-a794-4f7a-aafb-64a950f1fcf9
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: e696bf596255b5e28aa5589cfc18715f100c5b07
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/30/2017
---
# <a name="how-to-find-out-if-your-users-have-signed-up-for-rms-for-individuals"></a>Como saber se os utilizadores se inscreveram no RMS para indivíduos

>*Aplica-se a: Azure Information Protection*

Como administrador, como sabe se os seus utilizadores se inscreveram no RMS para indivíduos? Pode utilizar qualquer um ou uma combinação dos seguintes métodos:

-   Pergunte aos utilizadores como protegem os ficheiros altamente confidenciais, especialmente quando estão a colaborar com outras pessoas fora da organização.

-   Quando tiver uma subscrição do Azure para a sua organização, utilize o cmdlet [Get-MsolAccountSku](https://msdn.microsoft.com/library/azure/dn194118.aspx) para ver se a licença **RIGHTSMANAGEMENT_ADHOC** é atribuída a algum utilizador. Esta licença é proveniente da subscrição do RMS para indivíduos que foi concedida à organização, com um conjunto de unidades ativas disponíveis para os utilizadores utilizarem o processo de inscrição self-service.

-   Utilize uma solução de gestão do sistema, tal como o System Center Configuration Manager, para o software de inventário instalado e o software em utilização. Por exemplo, procure **MSIP.App.exe**, que é utilizado pelo cliente do Azure Information Protection, e **ipviewer.exe** para a aplicação de partilha Rights Management. Pode transferir e instalar este cliente e a aplicação gratuitamente para identificar outras caraterísticas que utiliza para o inventário de software.

-   Esteja atento às extensões dos nomes dos ficheiros que são criadas pelo cliente do Azure Information Protection ou pela aplicação de partilha Rights Management. As extensões de nome de ficheiro .pfile e .ppdf são os exemplos mais óbvios, mas existem outros ficheiros cuja extensão de nome de ficheiro é alterada quando são nativamente protegidos pelo serviço Rights Management. Para obter mais informações, veja a secção [Tipos de ficheiros suportados para proteção](../rms-client/client-admin-guide-file-types.md#file-types-supported-for-protection) no guia do administrador do cliente do Azure Information Protection.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
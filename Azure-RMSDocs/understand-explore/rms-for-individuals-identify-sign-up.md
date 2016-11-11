---
title: "Como saber se os utilizadores se inscreveram no RMS para indivíduos | Azure Information Protection"
description: "Como administrador, como sabe se os seus utilizadores se inscreveram no RMS para indivíduos? Pode utilizar qualquer um ou uma combinação dos métodos descritos neste artigo."
author: cabailey
manager: mbaldwin
ms.date: 10/24/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: a36c3d99-a794-4f7a-aafb-64a950f1fcf9
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c1a9de2d0ef3021335e94cde86a7e6b844b15908
ms.openlocfilehash: 70909cfa78800eabb798aec34264770104f7c47b


---


# Como saber se os utilizadores se inscreveram no RMS para indivíduos

>*Aplica-se a: Azure Information Protection*

Como administrador, como sabe se os seus utilizadores se inscreveram no RMS para indivíduos? Pode utilizar qualquer um ou uma combinação dos seguintes métodos:

-   Pergunte aos utilizadores como protegem os ficheiros altamente confidenciais, especialmente quando estão a colaborar com outras pessoas fora da organização.

-   Quando tiver uma subscrição do Azure para a sua organização, utilize o cmdlet [Get-MsolAccountSku](https://msdn.microsoft.com/library/azure/dn194118.aspx) para ver se **RIGHTSMANAGEMENT_ADHOC** é devolvido como uma das subscrições. Em caso afirmativo, esta é a subscrição do RMS para indivíduos que foi concedida à organização, com um conjunto de unidades ativas disponíveis para os utilizadores utilizarem o processo de inscrição self-service.

-   Utilize uma solução de gestão do sistema, tal como o System Center Configuration Manager, para o software de inventário instalado e o software em utilização. A aplicação de partilha Rights Management é executada através do programa **ipviewer.exe** e pode [transferir e instalar a aplicação](http://go.microsoft.com/fwlink/?LinkId=303970) gratuitamente para identificar outras caraterísticas sobre esta aplicação que utiliza, em seguida, para o inventário de software.

-   Esteja atento às extensões dos nomes dos ficheiros que são criadas pela aplicação de partilha Rights Management. As extensões de nome de ficheiro .pfile e .ppdf são os exemplos mais óbvios, mas existem outros ficheiros cuja extensão de nome de ficheiro é alterada quando são nativamente protegidos pelo serviço Rights Management. Para obter mais informações, consulte a secção [Tipos de ficheiros e extensões dos nomes dos ficheiros suportados](../rms-client/sharing-app-admin-guide-technical.md#supported-file-types-and-file-name-extensions) do [Guia do administrador da aplicação de partilha Rights Management](http://technet.microsoft.com/library/dn339003.aspx).




<!--HONumber=Oct16_HO4-->



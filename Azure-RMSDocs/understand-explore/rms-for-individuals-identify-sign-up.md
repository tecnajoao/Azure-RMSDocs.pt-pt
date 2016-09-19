---
title: "Como saber se os utilizadores se inscreveram no RMS para indivíduos | Azure RMS"
description: "Enquanto administrador, poderá utilizar todos os métodos descritos neste artigo ou uma combinação dos mesmos para verificar se os seus utilizadores se inscreveram ou não no RMS para indivíduos."
author: cabailey
manager: mbaldwin
ms.date: 09/01/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: a36c3d99-a794-4f7a-aafb-64a950f1fcf9
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 79d098e47cdfe608bc62ed385a5c8236fb7c6d3c
ms.openlocfilehash: 6a8a6ac7aae7c8e370af47e1d39a9f69acc1e12c


---


# Como saber se os utilizadores se inscreveram no RMS para indivíduos

>*Aplica-se a: Azure Rights Management*

Como administrador, como sabe se os seus utilizadores se inscreveram no RMS para indivíduos? Pode utilizar qualquer um ou uma combinação dos seguintes métodos:

-   Pergunte aos utilizadores como protegem os ficheiros altamente confidenciais, especialmente quando estão a colaborar com outras pessoas fora da organização.

-   Quando tiver uma subscrição do Azure para a sua organização, utilize o cmdlet [Get-MsolAccountSku](https://msdn.microsoft.com/library/azure/dn194118.aspx) para ver se **RIGHTSMANAGEMENT_ADHOC** é devolvido como uma das subscrições. Em caso afirmativo, esta é a subscrição do RMS para indivíduos que foi concedida à organização, com um conjunto de unidades ativas disponíveis para os utilizadores utilizarem o processo de inscrição self-service.

-   Utilize uma solução de gestão do sistema, tal como o System Center Configuration Manager, para o software de inventário instalado e o software em utilização. A aplicação de partilha Rights Management é executada através do programa **ipviewer.exe** e pode [transferir e instalar a aplicação](http://go.microsoft.com/fwlink/?LinkId=303970) gratuitamente para identificar outras caraterísticas sobre esta aplicação que utiliza, em seguida, para o inventário de software.

-   Esteja atento às extensões dos nomes dos ficheiros que são criadas pela aplicação de partilha Rights Management. As extensões dos nomes dos ficheiros .pfile e .ppdf são os exemplos mais óbvios, mas existem outros ficheiros que alteram as respetivas extensões dos nomes dos ficheiros quando estes estão protegidos nativamente pelo Rights Management. Para obter mais informações, consulte a secção [Tipos de ficheiros e extensões dos nomes dos ficheiros suportados](../rms-client/sharing-app-admin-guide-technical.md#supported-file-types-and-file-name-extensions) do [Guia do administrador da aplicação de partilha Rights Management](http://technet.microsoft.com/library/dn339003.aspx).




<!--HONumber=Sep16_HO1-->



---
title: Como utilizar o controlo de documentos | Azure RMS
description: "A funcionalidade de controlo de documentos requer alguns conhecimentos simples sobre a gestão dos metadados associados e o registo do serviço."
keywords: 
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 70E10936-7953-49B0-B0DC-A5E7C4772E60
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 798d8e5ca7aa22b236a42c8c4e344e6b735c4b75
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/30/2017
---
# <a name="how-to-use-document-tracking"></a>Como: utilizar o controlo de documentos

A utilização da funcionalidade de controlo de documentos requer alguns conhecimentos simples sobre a gestão dos metadados associados e o registo do serviço.

## <a name="managing-document-tracking-metadata"></a>Gerir metadados de controlo de documentos

Todos os sistemas operativos que suportam o controlo de documentos têm implementações semelhantes. Estes incluem um conjunto de propriedades que representam os metadados, um novo parâmetro adicionado aos métodos de criação de políticas de utilizador e um método para registar a política a controlar com o serviço de controlo de documentos.

Operacionalmente, apenas as propriedades **nome do conteúdo** e **tipo de notificação** são necessárias para o controlo de documentos.

A sequência de passos que irá utilizar para configurar o controlo de documentos para um determinado conteúdo é a seguinte:

-   Crie um objeto de **metadados de licença** e defina o **nome de conteúdo** e o **tipo de notificação**. Estas são as únicas propriedades necessárias.
   - Android – [LicenseMetadata](https://msdn.microsoft.com/library/mt573675.aspx)
   -  iOS – [MSLicenseMetadata](https://msdn.microsoft.com/library/mt573683.aspx)

Selecione o tipo de política (modelo ou ad-hoc):
- Para o controlo de documentos com base em modelos, crie um objeto **política de utilizador** passando os metadados de licença como um parâmetro.
  - Android – [UserPolicy.create](https://msdn.microsoft.com/library/dn790887.aspx)
  - iOS – [MSUserPolicy.userPolicyWithTemplateDescriptor](https://msdn.microsoft.com/library/dn790808.aspx)

- Para o controlo de documentos com base em ad hoc, defina a propriedade **metadados de licença** no objeto **descritor de política**.
  - Android – [PolicyDescriptor.setLicenseMetadata](https://msdn.microsoft.com/library/mt573698.aspx)
  - iOS – [MSPolicyDescriptor.licenseMetadata](https://msdn.microsoft.com/library/mt573693.aspx).

    **Nota:** o objeto de metadados de licença só é acessível diretamente durante o processo de configuração do controlo de documentos da política de utilizador especificada. Quando o objeto de política de utilizador tiver sido criado, os metadados de licença associados não estão acessíveis, ou seja, alterar os valores dos metadados de licença não tem qualquer efeito.

     

-   Por fim, chame o método de registo de plataforma para o controlo de documentos
  - Android – [UserPolicy.registerForDocTracking assíncrono](https://msdn.microsoft.com/library/mt573699.aspx) ou [UserPolicy.registerForDocTracking síncrono](https://msdn.microsoft.com/library/mt631387.aspx)
  - iOS – [MSUserPolicy.registerForDocTracking](https://msdn.microsoft.com/library/mt573694.aspx)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
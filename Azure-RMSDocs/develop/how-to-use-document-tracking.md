---
title: Como utilizar o controlo de documentos | Azure RMS
description: "A funcionalidade de controlo de documentos requer alguns conhecimentos simples sobre a gestão dos metadados associados e o registo do serviço."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 70E10936-7953-49B0-B0DC-A5E7C4772E60
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4abffcbe6e49ea25f3cf493a1e68fcd6ea25b26
ms.openlocfilehash: 3d5d920f628bc39c4c280afa53be0b7199433803


---

# Como: utilizar o controlo de documentos

A utilização da funcionalidade de controlo de documentos requer alguns conhecimentos simples sobre a gestão dos metadados associados e o registo do serviço.

## Gerir metadados de controlo de documentos

Todos os sistemas operativos que suportam o controlo de documentos têm implementações semelhantes. Estes incluem um conjunto de propriedades que representam os metadados, um novo parâmetro adicionado aos métodos de criação de políticas de utilizador e um método para registar a política a controlar com o serviço de controlo de documentos.

Operacionalmente, apenas as propriedades **nome do conteúdo** e **tipo de notificação** são necessárias para o controlo de documentos.

A sequência de passos que irá utilizar para configurar o controlo de documentos para um determinado conteúdo é a seguinte:

-   Crie um objeto **metadados de licença**.

    Consulte [**LicenseMetadata**](/information-protection/sdk/4.2/api/android/com.microsoft.rightsmanagement#msipcthin2_licensemetadata_interface_java) ou [**MSLicenseMetadata**](/information-protection/sdk/4.2/api/iOS/mslicensemetadata#msipcthin2_mslicensemetadata_class_objc) para obter mais informações.

-   Defina o **nome do conteúdo** e o **tipo de notificação**. Estas são as únicas propriedades necessárias.

    Para obter mais informações, consulte os métodos de acesso às propriedades da classe de metadados de licença adequada da plataforma, seja [**LicenseMetadata**](/information-protection/sdk/4.2/api/android/com.microsoft.rightsmanagement#msipcthin2_licensemetadata_interface_java) ou [**MSLicenseMetadata**](/information-protection/sdk/4.2/api/iOS/mslicensemetadata#msipcthin2_mslicensemetadata_class_objc).

-   Por tipo de política, modelo ou ad hoc:

    -   Para o controlo de documentos com base em modelos, crie um objeto **política de utilizador** passando os metadados de licença como um parâmetro.

        Para obter mais informações, consulte [**UserPolicy.create**](/information-protection/sdk/4.2/api/android/userpolicy#msipcthin2_userpolicy_class_java) e [**MSUserPolicy.userPolicyWithTemplateDescriptor**](/information-protection/sdk/4.2/api/iOS/msuserpolicy#msipcthin2_msuserpolicy_templatedescriptor_property_objc).

    -   Para o controlo de documentos com base em ad hoc, defina a propriedade **metadados de licença** no objeto **descritor de política**.

        Para obter mais informações, consulte [**PolicyDescriptor.getLicenseMetadata**](/information-protection/sdk/4.2/api/android/policydescriptor#msipcthin2_policydescriptor_interface_java), [**PolicyDescriptor.setLicenseMetadata**](/information-protection/sdk/4.2/api/android/policydescriptor#msipcthin2_policydescriptor_setlicensemetadata_java) e [**MSPolicyDescriptor.licenseMetadata**](/information-protection/sdk/4.2/api/iOS/mspolicydescriptor#msipcthin2_mspolicydescriptor_licensemetadata_property_objc).

    **Nota** O objeto de metadados de licença só é acessível diretamente durante o processo de configuração do controlo de documentos da política de utilizador especificada. Quando o objeto de política de utilizador tiver sido criado, os metadados de licença associados não estão acessíveis, ou seja, alterar os valores dos metadados de licença não tem qualquer efeito.

     

-   Chame o método de registo de plataforma para o controlo de documentos.

    Consulte [**MSUserPolicy.registerForDocTracking**](/information-protection/sdk/4.2/api/iOS/msuserpolicy#msipcthin2_msuserpolicy_registerfordoctracking_userid_authenticationcallback_completionblock_method_objc) ou [**UserPolicy.registerForDocTracking**](/information-protection/sdk/4.2/api/iOS/msuserpolicy#msipcthin2_msuserpolicy_registerfordoctracking_userid_authenticationcallback_completionblock_method_objc).

 

 



<!--HONumber=Oct16_HO1-->



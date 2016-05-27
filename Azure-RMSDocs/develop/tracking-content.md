---
# required metadata

title: Controlar conteúdo | Azure RMS
description: Orientações básicas para implementar o controlo de documentos
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: F5089765-9D94-452B-85E0-00D22675D847
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Controlar conteúdo

Este tópico abrange orientações básicas para implementar o controlo de documentos de conteúdo protegido com o SDK Rights Management Services 2.1.

O controlo de documentos é uma funcionalidade do sistema Rights Management. Ao adicionar metadados específicos durante o processo de proteção de documentos, um documento pode ser registado com o portal do serviço de controlo que fornece várias opções de controlo.

Utilize estas APIs para adicionar/atualizar uma licença de conteúdo com os metadados de controlo de documentos.

-   [**IpcCreateLicenseMetadataHandle**](/rights-management/sdk/2.1/api/win/functions#msipc_ipccreatelicensemetadatahandle)
-   [**IpcSetLicenseMetadataProperty**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetlicensemetadataproperty)

    Esperamos que defina todas as propriedades de metadados. Aqui estão, listadas por tipo.

    Para obter mais informações, consulte [**Tipos de propriedade de metadados de licença**](/rights-management/sdk/2.1/api/win/license%20metadata%20property%20types#msipc_license_metadata_property_types).

    -   **IPC\_MD\_CONTENT\_PATH**

        Utilize esta opção para identificar o documento controlado. Nos casos em que um caminho completo não seja possível, basta indicar o nome do ficheiro.

    -   **IPC\_MD\_CONTENT\_NAME**

        Utilize esta opção para identificar o nome do documento controlado.

    -   **IPC\_MD\_NOTIFICATION\_TYPE**

        Utilize para especificar quando a notificação será enviada. Para obter mais informações, consulte [**Tipo de notificação**](/rights-management/sdk/2.1/api/win/notification%20type#msipc_notification_type).

    -   **IPC\_MD\_NOTIFICATION\_PREFERENCE**

        Utilize para especificar o tipo de notificação. Para obter mais informações, consulte [**Preferência de notificação**](/rights-management/sdk/2.1/api/win/constants#msipc_notification_preference).

    -   **IPC\_MD\_DATE\_MODIFIED**

        Sugerimos que defina esta data sempre que o utilizador clica em **Guardar**.

    -   **IPC\_MD\_DATE\_CREATED**

        A data de origem do ficheiro.

-   [**IpcSerializeLicenseWithMetadata**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcserializelicensemetadata)

Utilize a API adequada das apresentadas para adicionar os metadados ao seu ficheiro ou fluxo.

-   [**IpcfEncryptFileWithMetadata**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfencryptfilewithmetadata)
-   [**IpcfEncryptFileStreamWithMetadata**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfencryptfilestreamwithmetadata)

Por último, utilize esta API para registar o documento controlado com o sistema de controlo.

-   [**IpcRegisterLicense**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcregisterlicense)

Veja a seguir um fragmento de código que mostra um exemplo de definição de metadados de controlo de documentos e a chamada para registar com o sistema de controlo.



    HRESULT hr = S_OK;
    LPCWSTR wszOutputFile = NULL;
    wstring wszWorkingFile;
    IPC_LICENSE_METADATA md = {0};

    md.cbSize = sizeof(IPC_LICENSE_METADATA);
    md.dwNotificationType = IPCD_CT_NOTIFICATION_TYPE_ENABLED;
    md.dwNotificationPreference = IPCD_CT_NOTIFICATION_PREF_DIGEST;
    //file origination date, current time for this example
    md.ftDateCreated = GetCurrentTime();
    md.ftDateModified = GetCurrentTime();

    LOGSTATUS_EX(L&quot;Encrypt file with official template...&quot;);

    hr =IpcfEncryptFileWithMetadata(  wszWorkingFile.c_str(),
                                       m_wszTestTemplateID.c_str(),
                                       IPCF_EF_TEMPLATE_ID,
                                       0,
                                       NULL,
                                       NULL,
                                       &amp;md,
                                       &amp;wszOutputFile);

    /* This will contain the serialized license */
    PIPC_BUFFER pSerializedLicense;

    /* the context to use for the call */
    PCIPC_PROMPT_CTX pContext;

    wstring wstrContentName(“MyDocument.txt”);
    bool sendLicenseRegistrationNotificationEmail = FALSE;

    hr = IpcRegisterLicense( pSerializedLicense,
                              0,
                              pContext,
                              wstrContentName.c_str(),
                              sendLicenseRegistrationNotificationEmail);


## Tópicos relacionados


* [**Tipos de propriedade de metadados de licença**](/rights-management/sdk/2.1/api/win/license%20metadata%20property%20types#msipc_license_metadata_property_types)
* [**Preferência de notificação**](/rights-management/sdk/2.1/api/win/constants#msipc_notification_preference)
* [**Tipo de notificação**](/rights-management/sdk/2.1/api/win/notification%20type#msipc_notification_type)
* [**IpcCreateLicenseMetadataHandle**](/rights-management/sdk/2.1/api/win/functions#msipc_ipccreatelicensemetadatahandle)
* [**IpcSetLicenseMetadataProperty**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetlicensemetadataproperty)
* [**IpcSerializeLicenseWithMetadata**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcserializelicensemetadata)
* [**IpcfEncryptFileWithMetadata**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfencryptfilewithmetadata)
* [**IpcfEncryptFileStreamWithMetadata**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfencryptfilestreamwithmetadata)
* [**IpcRegisterLicense**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcregisterlicense)
 

 


<!--HONumber=May16_HO2-->



---
title: Como ativar o controlo e a revogação de documentos | Azure RMS
description: Orientação básica para a implementação do controlo de documento dos conteúdos, bem como código de exemplo para atualizações de metadados e um botão Controlar Utilização para a sua aplicação.
keywords: ''
author: bryanla
ms.author: bryanla
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: conceptual
ms.service: information-protection
ms.assetid: F5089765-9D94-452B-85E0-00D22675D847
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 8794d0f7413941573484c7f9509f5be5e2aa2414
ms.sourcegitcommit: bd2b31dd97c8ae08c28b0f5688517110a726e3a1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54071697"
---
# <a name="how-to-enable-document-tracking-and-revocation"></a>Procedimentos: ativar o controlo e a revogação de documentos

Este tópico inclui a documentação de orientação básica para implementação do controlo de documento do conteúdo, bem como código de exemplo para atualizações de metadados e criação de um botão **Controlar Utilização** para a sua aplicação.

## <a name="steps-to-implement-document-tracking"></a>Passos para implementar o controlo de documento

Os passos 1 e 2 ativam o controlo de documento. O passo 3 permite que os utilizadores de aplicação acedam ao site de controlo de documentos para controlarem e revogarem os seus documentos protegidos.

1. Adicionar metadados de controlo de documento
2. Registar o documento no serviço RMS
3. Adicionar o botão Controlar Utilização à sua aplicação

Os detalhes de implementação para estes passos são descritos em seguida.

## <a name="1-add-document-tracking-metadata"></a>1. Adicionar metadados de controlo de documento

O controlo de documentos é uma funcionalidade do sistema Rights Management. Ao adicionar metadados específicos durante o processo de proteção de documentos, um documento pode ser registado com o portal do serviço de controlo que fornece várias opções de controlo.

Utilize estas APIs para adicionar/atualizar uma licença de conteúdo com os metadados de controlo de documentos.


Operacionalmente, apenas as propriedades **nome do conteúdo** e **tipo de notificação** são necessárias para o controlo de documentos.


- [IpcCreateLicenseMetadataHandle](https://msdn.microsoft.com/library/dn974050.aspx)
- [IpcSetLicenseMetadataProperty](https://msdn.microsoft.com/library/dn974059.aspx)

  Esperamos que defina todas as propriedades de metadados. Aqui estão, listadas por tipo.

  Para obter mais informações, consulte [Tipos de propriedade de metadados de licença](https://msdn.microsoft.com/library/dn974062.aspx).

  - **IPC_MD_CONTENT_PATH**

    Utilize para identificar o documento controlado. Nos casos em que um caminho completo não seja possível, basta indicar o nome do ficheiro.

  - **IPC_MD_CONTENT_NAME**

    Utilize para identificar o nome do documento controlado.

  - **IPC_MD_NOTIFICATION_TYPE**

    Utilize para especificar quando a notificação será enviada. Para obter mais informações, consulte Tipo de notificação.

  - **IPC_MD_NOTIFICATION_PREFERENCE**

    Utilize para especificar o tipo de notificação. Para obter mais informações, consulte Preferência de notificação.

  - **IPC_MD_DATE_MODIFIED**

    Sugerimos que defina esta data sempre que o utilizador clicar em Guardar.

  - **IPC_MD_DATE_CREATED**

    Utilize para definir a data de origem do ficheiro

- [IpcSerializeLicenseWithMetadata](https://msdn.microsoft.com/library/dn974058.aspx)

Utilize a API adequada das apresentadas para adicionar os metadados ao seu ficheiro ou fluxo.

- [IpcfEncryptFileWithMetadata](https://msdn.microsoft.com/library/dn974052.aspx)
- [IpcfEncryptFileStreamWithMetadata](https://msdn.microsoft.com/library/dn974051.aspx)

Por último, utilize esta API para registar o documento controlado com o sistema de controlo.

- [IpcRegisterLicense](https://msdn.microsoft.com/library/dn974057.aspx)


## <a name="2-register-the-document-with-the-rms-service"></a>2. Registar o documento no serviço RMS

Veja a seguir um fragmento de código que mostra um exemplo de definição de metadados de controlo de documentos e a chamada para registar com o sistema de controlo.

      C++
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

      LOGSTATUS_EX(L"Encrypt file with official template...");

      hr =IpcfEncryptFileWithMetadata( wszWorkingFile.c_str(),
                               m_wszTestTemplateID.c_str(),
                               IPCF_EF_TEMPLATE_ID,
                               0,
                               NULL,
                               NULL,
                               &md,
                               &wszOutputFile);

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

## <a name="add-a-track-usage-button-to-your-app"></a>Adicionar um botão **Controlar Utilização** à sua aplicação

Adicionar um item de IU **Controlar Utilização** à sua aplicação é tão simples quanto utilizar um dos seguintes formatos de URL:

- Utilizar ID de Conteúdo
  - Obtenha o ID de conteúdo utilizando [IpcGetLicenseProperty](https://msdn.microsoft.com/library/hh535265.aspx) ou [IpcGetSerializedLicenseProperty](https://msdn.microsoft.com/library/hh995038.aspx), se a licença for serializada e utilize a propriedade de licença **IPC_LI_CONTENT_ID**. Para obter mais informações, consulte [Tipos de propriedade de licença](https://msdn.microsoft.com/library/hh535287.aspx).
  - Com os metadados **ContentId** e **Issuer**, utilize o seguinte formato: `https://track.azurerms.com/#/{ContentId}/{Issuer}`

    Exemplo – `https://track.azurerms.com/#/summary/05405df5-8ad6-4905-9f15-fc2ecbd8d0f7/janedoe@microsoft.com`

- Se não tiver acesso a esses metadados (ou seja, está a examinar a versão não protegida do documento), pode utilizar **Content_Name** no seguinte formato: `https://track.azurerms.com/#/?q={ContentName}`

  Exemplo - https://track.azurerms.com/#/?q=Secret!. txt

O cliente só tem de abrir um browser com o URL adequado. O portal de Controlo de Documento RMS processará a autenticação e qualquer redirecionamento necessário.

## <a name="related-topics"></a>Tópicos relacionados

* [Tipos de propriedade de metadados de licença](https://msdn.microsoft.com/library/dn974062.aspx)
* [Preferência de notificação](https://msdn.microsoft.com/library/dn974063.aspx)
* [Tipo de notificação](https://msdn.microsoft.com/library/dn974064.aspx)
* [IpcCreateLicenseMetadataHandle](https://msdn.microsoft.com/library/dn974050.aspx)
* [IpcSetLicenseMetadataProperty](https://msdn.microsoft.com/library/dn974059.aspx)
* [IpcSerializeLicenseWithMetadata](https://msdn.microsoft.com/library/dn974058.aspx)
* [IpcfEncryptFileWithMetadata](https://msdn.microsoft.com/library/dn974052.aspx)
* [IpcfEncryptFileStreamWithMetadata](https://msdn.microsoft.com/library/dn974051.aspx)
* [IpcRegisterLicense](https://msdn.microsoft.com/library/dn974057.aspx)


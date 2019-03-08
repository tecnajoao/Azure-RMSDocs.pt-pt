---
title: Procedimentos sobre como adicionar direitos de proprietário explícitos | Azure RMS
description: A aplicação deve adicionar explicitamente direitos de “Proprietário” quando criar uma licença a partir do zero.
keywords: ''
author: msmbaldwin
ms.author: mbaldwin
manager: barbkess
ms.date: 02/23/2017
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: EF43FAC4-ABB4-459D-B173-972B5716F816
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 925d1fa7e55e8d58da904e8811f530f2524a1658
ms.sourcegitcommit: 471b3683367d93f0673c1cf276a15f83572aa80e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57330523"
---
# <a name="how-to-add-explicit-owner-rights"></a>Procedimentos: adicionar direitos de proprietário explícitos

A aplicação deve adicionar explicitamente direitos de "Proprietário" quando criar uma licença a partir do zero com [IpcCreateLicenseFromScratch](https://msdn.microsoft.com/library/hh535256.aspx).

## <a name="prerequisites"></a>Pré-requisitos

Quando a aplicação estiver a criar um identificador de licença através de [IpcCreateLicenseFromScratch](https://msdn.microsoft.com/library/hh535256.aspx), tem também de conceder ao proprietário direitos completos (permissões) explicitamente.

> [!NOTE]
> Definir um utilizador como "proprietário" através de [IpcSetLicenseProperty](https://msdn.microsoft.com/library/hh535271.aspx) com a propriedade **IPC\_LI\_OWNER** não concede ao proprietário permissões completas.

O código de exemplo seguinte mostra apenas os passos envolvidos na criação e adição de direitos específicos a uma determinada licença.

## <a name="instructions"></a>Instruções
 
## <a name="step-1-example-scenario"></a>Passo 1: Cenário de exemplo

Neste exemplo, os direitos necessários são adicionados a uma licença criada com [IpcCreateLicenseFromScratch](https://msdn.microsoft.com/library/hh535256.aspx). O exemplo mostra a criação e a atribuição de direitos à licença através de uma lista de direitos.

Os dois direitos seguintes são adicionados a estes utilizadores:

- Permissões de *leitura* atribuídas a joe@contoso.com
- Permissões *completas* atribuídas a Mariana\_kay@contoso.com

      // Create User Rights structure
      IPC_USER_RIGHTS ownerRightForOwner = {0};

      // Create rights
      LPCWSTR rgwszOwnerRights[1] = {IPC_GENERIC_ALL};

      // Assign values to members of Rights structure
      ownerRightForOwner.User.dwType = IPC_USER_TYPE_IPC;
      ownerRightForOwner.User.wszID = IPC_USER_ID_OWNER;
      ownerRightForOwner.rgwszRights = rgwszOwnerRights;
      ownerRightForOwner.cRights = 1;

      // Create User Rights structure for Joe with Read permissions
      IPC_USER_RIGHTS joeReadRight = {0};
      LPCWSTR rgwszReadRights[1] = {IPC_GENERIC_READ};

      // Assign values to members of Rights structure for Joe
      joeReadRight.User.dwType = IPC_USER_TYPE_EMAIL;
      joeReadRight.User.wszID = "joe@contoso.com";
      joeReadRight.rgwszRights = rgwszReadRights;
      joeReadRight.cRights = 1;

      // Create User Rights structure for Mary Kay with Full permissions
      IPC_USER_RIGHTS mary_kayFullRight = {0};
      LPCWSTR rgwszFullRights[1] = {IPC_GENERIC_ALL};

      // Assign values to members of Rights structure for Mary Kay
      mary_kayFullRight.User.dwType = IPC_USER_TYPE_EMAIL;
      mary_kayFullRight.User.wszID = L"mary_kay@contoso.com";
      mary_kayFullRight.rgwszRights = rgwszFullRights;
      mary_kayFullRight.cRights = 1;

      // Create User Rights List and assign the above rights
      size_t uNoOfUserRights = 3;
      PIPC_USER_RIGHTS_LIST pUserRightsList = NULL;
      pUserRightsList = reinterpret_cast<PIPC_USER_RIGHTS_LIST>
      (new BYTE[ sizeof(IPC_USER_RIGHTS_LIST) + uNoOfUserRights * sizeof(IPC_USER_RIGHTS)]);

      if(pUserRightsList == NULL)
      {
        // Handle error
      }

      // Assign values to members of Rights List structure for Joe and Mary Kay
      (*pUserRightsList).cbSize = sizeof(IPC_USER_RIGHTS_LIST);
      (*pUserRightsList).cUserRights = uNoOfUserRights;
      (*pUserRightsList).rgUserRights[0] = ownerRightForOwner;
      (*pUserRightsList).rgUserRights[1] = joeReadRight;
      (*pUserRightsList).rgUserRights[2] = mary_kayFullRight;

      // Set the Rights List property on the license via its handle
      // hLicense is a license handle created with IpcCreateLicenseFromScratch
      hr = IpcSetLicenseProperty(hLicense, FALSE, IPC_LI_USER_RIGHTS_LIST, pUserRightsList);

      if(FAILED(hr))
      {
        // Handle the error
      }



## <a name="related-topics"></a>Tópicos relacionados

- [Notas do programador](developer-notes.md)
- [IpcSetLicenseProperty](https://msdn.microsoft.com/library/hh535271.aspx)
- [IpcCreateLicenseFromScratch](https://msdn.microsoft.com/library/hh535256.aspx)

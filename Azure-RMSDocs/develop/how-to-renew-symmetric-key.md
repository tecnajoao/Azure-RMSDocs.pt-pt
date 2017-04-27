---
title: "Como renovar a chave simétrica no Azure Information Protection"
description: "Este artigo descreve o processo de renovar uma chave simétrica no Azure Information Protection."
keywords: 
author: kkanakas
manager: mbaldwin
ms.author: kartikk
ms.date: 03/27/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: a0b8c8f0-6ed5-48bb-8155-ac4f319ec178
ms.openlocfilehash: eeda64a5b882cd6785eb9d933858bf1a0d37ef37
ms.sourcegitcommit: bf103c02966357eccad0a4912851ceae6937c7b3
translationtype: HT
---
# <a name="how-to-renew-the-symmetric-key-in-azure-information-protection"></a>Procedimentos: como renovar a chave simétrica no Azure Information Protection

Uma **chave simétrica** é um segredo que encripta e desencripta uma mensagem na criptografia de chave simétrica.  

No Azure Active Directory (Azure AD), quando cria um objeto do principal de serviço para representar uma aplicação, o processo também gera uma chave simétrica de 256 bits para verificar a aplicação. Por predefinição, esta chave simétrica é válida durante um ano. 

Os passos abaixo indicam como renovar a chave simétrica. 

## <a name="prerequisites"></a>Pré-requisitos

* O módulo do PowerShell do Azure Active Directory (Azure AD) tem de estar instalado conforme indicado na [Referência do PowerShell do Azure AD](https://docs.microsoft.com/powershell/msonline/).


## <a name="renewing-the-symmetric-key-after-expiry"></a>Renovar a chave simétrica depois da expiração

Não precisa de criar um novo principal de serviço quando a chave simétrica associada à sua aplicação tiver expirado. Em alternativa, pode utilizar os [cmdlets do PowerShell](https://docs.microsoft.com/powershell/module/msonline) fornecidos pelo Microsoft Online Services (MSol) para emitir uma nova chave simétrica para um principal de serviço existente.

Para ilustrar este processo, vamos partir do princípio que já criou um novo principal de serviço com o comando [`New-MsolServicePrincipal`](https://docs.microsoft.com/powershell/msonline/v1/new-msolserviceprincipalcredential).

```
New-MsolServicePrincipalCredential -ServicePrincipalName "SupportExampleApp"
```

O processo de criação cria uma chave simétrica e um **AppPrincipalId** conforme apresentado.

```
The following symmetric key was created as one was not supplied
ZYbF/lTtwE28qplQofCpi2syWd11D83+A3DRlb2Jnv8=

DisplayName : SupportExampleApp
ServicePrincipalNames : {7d9c1f38-600c-4b4d-8249-22427f016963}
ObjectId : 0ee53770-ec86-409e-8939-6d8239880518
AppPrincipalId : 7d9c1f38-600c-4b4d-8249-22427f016963
TrustedForDelegation : False
AccountEnabled : True
Addresses : []
KeyType : Symmetric
KeyId : acb9ad1b-36ce-4a7d-956c-40e5ac29dcbe
StartDate : 3/22/2017 3:27:53 PM
EndDate : 3/22/2018 3:27:53 PM
Usage : Verify
```

A chave simétrica criada no exemplo acima expira a 22/03/2018 às 15:27:53. Para continuar a utilizar o principal de serviço para além desse tempo, teria de renovar a chave simétrica. Pode fazê-lo com o comando [`New-MsolServicePrincipalCredential`](https://docs.microsoft.com/powershell/msonline/v1/new-msolserviceprincipalcredential). 

```
New-MsolServicePrincipalCredential -AppPrincipalId 7d9c1f38-600c-4b4d-8249-22427f016963
```

Esta ação cria uma nova chave simétrica para o **AppPrincipalId** especificado.

```
The following symmetric key was created as one was not supplied ON8YYaMYNmwSfMX625Ei4eC6N1zaeCxbc219W090v28-
```
Pode utilizar o comando [`GetMsolServicePrincipalCredential`](https://docs.microsoft.com/powershell/msonline/v1/get-msolserviceprincipalcredential) para verificar se a nova chave simétrica está associada ao principal de serviço correto conforme apresentado. Tenha em atenção que o comando indica todas as chaves que estão atualmente associadas ao principal de serviço.

```
Get-MsolServicePrincipalCredential -AppPrincipalId 7d9c1f38-600c-4b4d-8249-22427f016963 -ReturnKeyValues true

Type : Symmetric
Value :
KeyId : c1ac145f-e899-4c90-8a02-2cef40054fc5
StartDate : 3/24/2017 10:11:07 PM
EndDate : 3/24/2018 10:11:07 PM
Usage : Verify

Type : Symmetric
Value :
KeyId : acb9ad1b-36ce-4a7d-956c-40e5ac29dcbe
StartDate : 3/22/2017 3:27:53 PM
EndDate : 3/22/2018 3:27:53 PM
Usage : Verify
```

Assim que tiver verificado que a chave simétrica está associada ao principal de serviço correto, pode atualizar os parâmetros de autenticação do principal de serviço com a nova chave. 

Em seguida, pode remover a chave simétrica antiga com o comando [`Remove-MsolServicePrincipalCredential`](https://docs.microsoft.com/powershell/msonline/v1/remove-msolserviceprincipalcredential) e verificar se a chave foi removida com o comando `Get-MsolServicePrincipalCredential`.

```
Remove-MsolServicePrincipalCredential -KeyId acb9ad1b-36ce-4a7d-956c-40e5ac29dcbe -ObjectId 0ee53770-ec86-409e-8939-6d8239880518
```

## <a name="related-topics"></a>Tópicos relacionados

* [Procedimentos: permitir que a aplicação de serviço funcione com o RMS baseado na cloud](how-to-use-file-api-with-aadrm-cloud.md)
* [Referência do MSOnline Powershell do Azure Active Directory](https://docs.microsoft.com/powershell/msonline/)

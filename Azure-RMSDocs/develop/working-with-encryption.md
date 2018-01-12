---
title: "Procedimentos sobre como trabalhar com definições de encriptação | Azure RMS"
description: "Orientação para os pacotes de encriptação do Azure RMS e recortes de código para a respetiva utilização."
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: B1D2C227-F43D-4B18-9956-767B35145792
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 9c6f24491a23af8b7123ccdee7762111f14749f4
ms.sourcegitcommit: 93124ef58e471277c7793130f1a82af33dabcea9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/11/2018
---
# <a name="how-to-work-with-encryption-settings"></a>Procedimentos: trabalhar com definições de encriptação

Este tópico descreve os nossos pacotes de encriptação e mostra como é possível utilizar alguns recortes de código.

## <a name="support-for-aes-256-the-new-default"></a>Suporte para AES 256, a nova predefinição

Nenhum código adicional é necessário para utilizar a encriptação baseada em *AES 256*, dado que se trata da nova predefinição, partindo do princípio de que compila com o SDK RMS 2.1, atualização de março de 2015, ou posterior. Aconselhamo-lo a considerar a atualização das suas aplicações com esta versão devido às vantagens de segurança adicionais da *AES 256*.

> [!IMPORTANT]
> O suporte para consumo de ficheiros protegidos por *AES 256* já existia desde a [versão de outubro de 2014](release-notes-rtm.md). Se estiver a executar aplicações criadas com uma versão do SDK anterior à de outubro de 2014, esta atualização irá interromper a sua aplicação. Certifique-se de que os clientes das aplicações que está a criar estão a utilizar o SDK atualizado ou estão dispostos a atualizar imediatamente para a versão mais recente da aplicação.

 
## <a name="api-encryption-support"></a>Suporte de encriptação de API

A partir da [atualização de março de 2015](release-notes-rtm.md), incorporamos os três sinalizadores seguintes na nossa API e nos respetivos pacotes de encriptação associados:

-   IPC\_ENCRYPTION\_PACKAGE\_AES256\_CBC4K
-   IPC\_ENCRYPTION\_PACKAGE \_AES128\_CBC4K
-   IPC\_ENCRYPTION\_PACKAGE \_AES128\_ECB (também conhecido como Algoritmos Preteridos)

Os sinalizadores de pacote de encriptação (consulte [Encriptação preferencial](https://msdn.microsoft.com/library/dn974065.aspx)) podem ser utilizados em conjunto com o sinalizador Propriedade da Licença – *IPC\_LI\_PREFERRED\_ENCRYPTION\_PACKAGE*.

Seguem-se alguns fragmentos de código simples que demonstram como utilizar a nova propriedade de licença.

## <a name="deprecated-algorithms"></a>Algoritmos Preteridos

Já não expomos o sinalizador *IPC\_LI\_DEPRECATED\_ENCRYPTION\_ALGORITHMS* na nossa API. Isto significa que as aplicações futuras vão deixar de compilar se fizerem referência a este sinalizador, mas as aplicações já criadas que o utilizam vão continuar a funcionar, uma vez que respeitamos o sinalizador em privado no código de API.

Para aproveitar ainda as vantagens do sinalizador de algoritmos de encriptação preterido antigo, basta alterar um sinalizador. Consulte os seguintes fragmentos de código para obter exemplos.

## <a name="protect-files-with-aes-256-cbc4k"></a>Proteger Ficheiros com AES 256 CBC4K

Não são necessárias alterações no código, *AES 256* CBC4K é a predefinição.

    C++

    hr = IpcCreateLicenseFromTemplateID(pcTil-&gt;aTi[0].wszID,
                                    0,
                                    NULL,
                                    &amp;pLicenseHandle);


## <a name="protect-files-with-aes-128-cbc4k"></a>Proteger Ficheiros com AES 128 CBC4K

    C++

    hr = IpcCreateLicenseFromTemplateID(pcTil-&gt;aTi[0].wszID,
                                    0,
                                    NULL,
                                    &amp;pLicenseHandle);

    DWORD dwEncryptionMode = IPC_ENCRYPTION_PACKAGE_AES128_CBC4K;

    hr = IpcSetLicenseProperty(pLicenseHandle,
                           false,
                           IPC_LI_PREFERRED_ENCRYPTION_PACKAGE,
                           &amp;dwEncryptionMode);


## <a name="protect-files-with-aes-128-ecb-deprecated-algorithms"></a>Proteger Ficheiros com AES-128 ECB (Algoritmos Preteridos)

Este exemplo mostra também a nova forma de suportar *algoritmos preteridos*.

    C++

    hr = IpcCreateLicenseFromTemplateID(pcTil-&gt;aTi[0].wszID,
                                    0,
                                    NULL,
                                    &amp;pLicenseHandle);

    DWORD dwEncryptionMode = IPC_ENCRYPTION_PACKAGE_AES128_ECB;

    hr = IpcSetLicenseProperty(pLicenseHandle,
                           false,
                           IPC_LI_PREFERRED_ENCRYPTION_PACKAGE,
                           &amp;dwEncryptionMode);


[!INCLUDE[Commenting house rules](../includes/houserules.md)]
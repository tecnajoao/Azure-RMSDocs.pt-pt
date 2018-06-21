---
title: PowerShell para modelos de proteção - Azure Information Protection
description: Tudo o que pode fazer no portal do Azure para criar e gerir modelos de proteção, pode fazer a partir da linha de comandos, utilizando o PowerShell. Além disso, pode exportar e importar modelos para poder copiar modelos entre inquilinos ou fazer edições em volume de propriedades complexas nos modelos, como nomes e descrições multilingues.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/23/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 30ee2f77-ce16-4113-bcda-6089131849ec
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 30dbfbe2cd9ef7d8acd89a9a76cd1108d7c03ab2
ms.sourcegitcommit: dbbfadc72f4005f81c9f28c515119bc3098201ce
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/28/2018
ms.locfileid: "30205725"
---
# <a name="powershell-reference-for-protection-templates"></a>Referência do PowerShell para modelos de proteção

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

As definições de proteção do Azure Information Protection são guardadas em modelos de proteção. Tudo o que pode fazer no portal do Azure para criar e gerir as definições de proteção, pode efetuar na linha de comandos, utilizando o PowerShell. 

Além disso, pode exportar e importar modelos de proteção. Estas duas ações permitem-lhe proteção copiar modelos entre inquilinos ou em massa edições de propriedades complexas, tais como nomes e descrições multilingues.

Também pode utilizar a exportação e importação para criar cópias de segurança e restaurar os modelos de proteção. Como melhor prática, regularmente cópia de segurança de modelos. Em seguida, se fizer uma alteração às definições de proteção que não foi concebida, pode facilmente reverter para uma versão anterior.

Para obter instruções de instalação, consulte [instalar o módulo do AADRM PowerShell](install-powershell.md).

Os cmdlets que suportam a criar e gerir modelos de proteção:

- [Add-AadrmTemplate](/powershell/module/aadrm/add-aadrmtemplate)

- [Export-AadrmTemplate](/powershell/module/aadrm/export-aadrmtemplate)

- [Get-AadrmTemplate](/powershell/module/aadrm/get-aadrmtemplate)

- [Get-AadrmTemplateProperty](/powershell/module/aadrm/get-aadrmtemplateproperty)

- [Import-AadrmTemplate](/powershell/module/aadrm/import-aadrmtemplate)

- [New-AadrmRightsDefinition](/powershell/module/aadrm/new-aadrmrightsdefinition)

- [Remove-AadrmTemplate](/powershell/module/aadrm/remove-aadrmtemplate)

- [Set-AadrmTemplateProperty](/powershell/module/aadrm/set-aadrmtemplateproperty)



## <a name="see-also"></a>Consulte Também
[Configurar e gerir modelos do Azure Information Protection](configure-policy-templates.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

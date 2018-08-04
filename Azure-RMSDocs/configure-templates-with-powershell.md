---
title: PowerShell para modelos de proteção - Azure Information Protection
description: Tudo o que pode fazer no portal do Azure para criar e gerir modelos de proteção, pode fazer da linha de comando, com o PowerShell. Além disso, pode exportar e importar modelos para poder copiar modelos entre inquilinos ou fazer edições em volume de propriedades complexas nos modelos, como nomes e descrições multilingues.
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
ms.openlocfilehash: aad2683fb5c30eda8b94f2208a1c72f46d4a0e13
ms.sourcegitcommit: 5fdf013fe05b65517b56245e1807875d80be6e70
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/03/2018
ms.locfileid: "39491327"
---
# <a name="powershell-reference-for-protection-templates"></a>Referência do PowerShell para modelos de proteção

>*Aplica-se a: [do Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Definições de proteção do Azure Information Protection são guardadas em modelos de proteção. Tudo o que pode fazer no portal do Azure para criar e gerir as definições de proteção, pode fazer na linha de comando, com o PowerShell. 

Além disso, pode exportar e importar modelos de proteção. Essas duas ações permitem-lhe modelos de proteção contra cópia entre inquilinos ou em massa as edições de propriedades complexas, tais como nomes e descrições multilingues.

Também pode utilizar a exportação e importação para criar cópias de segurança e restaurar seus modelos de proteção. Como melhor prática, faça regularmente backup de seus modelos. Em seguida, se fizer uma alteração às definições de proteção que não era destinada, pode facilmente reverter para uma versão anterior.

Para obter instruções de instalação, consulte [instalar o módulo do PowerShell do AADRM](install-powershell.md).

Os cmdlets que suportam a criação e gestão de modelos de proteção:

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


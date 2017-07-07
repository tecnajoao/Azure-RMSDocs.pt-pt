---
title: "Controlar as contas criadas para o RMS para utilizadores individuais – AIP"
description: "Como pode controlar as contas de utilizador no Azure Active Directory se não pretender converter a subscrição do RMS para indivíduos da sua organização para uma subscrição paga."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: a83880d0-f0f9-4a32-9e00-2f6635d7cc8d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: ff8cd150ce438a7b9ad5203dfb6d9d01c1a0d85a
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/30/2017
---
# <a name="how-administrators-can-control-the-accounts-created-for-rms-for-individuals"></a>Como os administradores podem controlar as contas criadas para o RMS para indivíduos

>*Aplica-se a: Azure Information Protection*


Se não pretender converter a subscrição do RMS para indivíduos da sua organização para uma subscrição paga, pode continuar a controlar as contas de utilizadores no diretório do Azure que foi criado para a sua organização das seguintes formas:

-   Implemente soluções de integração de diretórios para o Azure Active Directory e a sua infraestrutura dos Serviços de Domínio do Active Directory. Pode sincronizar as contas e as palavras-passe para que os utilizadores não tenham de criar novas contas para utilizar o Rights Management e as políticas de palavra-passe no local serão aplicadas às novas contas de utilizadores do Azure. De igual modo, pode sincronizar as palavras-passe para que os utilizadores não tenham de memorizar uma palavra-passe diferente para utilizar o Rights Management.

-   Pode impedir que os utilizadores se inscrevam para utilizar o Azure Rights Management com a subscrição do RMS para indivíduos. Na maioria dos casos, esta ação não traz grandes vantagens porque os utilizadores partilharão ficheiros sem proteção (o que pode colocar a sua empresa em risco) ou utilizarão outro mecanismo de proteção de ficheiros que não proporciona ao departamento de TI a opção de aceder aos dados. No entanto, se pretender impedir que os utilizadores se inscrevam para utilizar o RMS para indivíduos, efetue uma das seguintes ações depois de se tornar o proprietário do diretório da sua organização no Azure:

    -   Impeça todos os utilizadores de se inscreverem em subscrições self-service, incluindo o RMS para indivíduos.  Atualmente, não é possível configurar esta opção por serviço; a definição aplica-se a todas as subscrições do Azure que utilizam o processo self-service. Para fazê-lo, defina o parâmetro **AllowAdHocSubscriptions** como false com o cmdlet [Set-MsolCompanySettings](http://technet.microsoft.com/library/dn194127.aspx) do módulo PowerShell para Azure Active Directory. Por exemplo: **Set-MsolCompanySettings -AllowAdHocSubscriptions $false**

    -   Impeça que os utilizadores criem uma nova conta no Azure, o que significa que apenas os utilizadores que já têm uma conta no Azure podem inscrever-se em subscrições self-service, incluindo o RMS para indivíduos.  Para fazê-lo, defina o parâmetro **AllowEmailVerifiedUsers** como false com o cmdlet [Set-MsolCompanySettings](http://technet.microsoft.com/library/dn194127.aspx) do módulo PowerShell para Azure Active Directory. Por exemplo: **Set-MsolCompanySettings -AllowEmailVerifiedUsers $false -AllowAdHocSubscriptions $true**

    -   Sincronize a sua infraestrutura dos Serviços de Domínio do Active Directory com o Azure Active Directory. Esta ação impede que novas contas sejam criadas quando os utilizadores se inscrevem em subscrições self-service, tais como o RMS para indivíduos, e pode eliminar ou desativar contas que foram anteriormente criadas no diretório do Azure.

Para controlar as contas de utilizador no diretório do Azure ou impedir que os utilizadores se inscrevam no RMS para indivíduos, tem de ter uma subscrição do Azure e ser o proprietário do diretório. Se ainda não tiver uma subscrição do Azure, pode obter uma gratuitamente. Se um diretório foi criado automaticamente durante o processo self-service, torne-se o proprietário do domínio que foi sido utilizado para o criar. Se já possui um diretório no Azure, mas os utilizadores especificaram um novo domínio que utiliza na sua organização, intercale esse domínio com o seu diretório existente. Para obter mais informações, consulte as instruções em [O que é a Inscrição Self-Service para o Azure?](https://azure.microsoft.com/documentation/articles/active-directory-self-service-signup/)


## <a name="next-steps"></a>Passos seguintes

Se os utilizadores, em vez dos administradores, puderem criar as respetivas contas no Azure Active Directory para o RMS para indivíduos, como pode descobrir se fizeram isto?  Consulte [Como saber se os utilizadores se inscreveram no RMS para indivíduos](rms-for-individuals-identify-sign-up.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
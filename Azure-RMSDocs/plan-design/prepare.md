---
title: "Preparar-se para a solução de proteção Azure Rights Management| Azure Information Protection"
description: "Verifique se preparou tudo para utilizar o Azure Rights Management, para que a sua organização possa proteger documentos e e-mails."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: afbca2d6-32a7-4bda-8aaf-9f93f5da5abc
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7068e0529409eb783f16bc207a17be27cd5d82a8
ms.openlocfilehash: b0c5596feec3f61ad25fe47416a1383f453bdc6b


---

# <a name="preparing-for-azure-information-protection"></a>Preparação para o Azure Information Protection

>*Aplica-se a: Azure Information Protection, Office 365*

Antes de implementar o Azure Information Protection na sua organização, certifique-se de que preparou o seguinte:

-   Grupos e contas de utilizadores na nuvem que pode criar manualmente ou que são automaticamente criados e sincronizados nos Serviços de Domínio do Active Directory (AD DS).

    Quando sincroniza os seus grupos e contas no local, não é necessário sincronizar todos os atributos. Para obter uma lista dos atributos utilizados pelo Azure Information Protection que têm de ser sincronizados com o serviço Azure Rights Management, consulte a [secção Azure RMS](/active-directory/active-directory-aadconnectsync-attributes-synchronized#azure-rms) na documentação do Azure Active Directory. Para facilitar a implementação, recomendamos que utilize o [Azure AD Connect](/active-directory/active-directory-aadconnectsync-whatis) para ligar os seus diretórios no local ao Azure Active Directory, mas pode utilizar qualquer método de sincronização de diretórios que alcance o mesmo resultado.

-   Os grupos com capacidade de correio na nuvem que irá utilizar com o Azure Information Protection. Estes podem ser grupos incorporados ou grupos criados manualmente que contêm utilizadores que irão utilizar documentos e e-mails protegidos.

    Se tiver o Exchange Online, pode criar e utilizar grupos com capacidade de correio utilizando o centro de administração do Exchange. Se tiver o AD DS no local e estiver a sincronizar com o Azure AD, pode criar e utilizar grupos com capacidade de correio que são grupos de segurança ou grupos de distribuição.

## <a name="activate-the-rights-management-service-for-data-protection"></a>Ativar o serviço Rights Management para a proteção de dados
Quando estiver pronto para começar a proteger documentos e e-mails, ative o serviço Rights Management para ativar esta tecnologia. Para obter mais informações, consulte [Ativar o Azure Rights Management](../deploy-use/activate-service.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]





<!--HONumber=Jan17_HO4-->



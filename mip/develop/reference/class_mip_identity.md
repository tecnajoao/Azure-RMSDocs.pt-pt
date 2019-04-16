---
title: classe mip::Identity
description: Documenta a classe mip::identity da Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 75d11fae7d79cadc4dd8909be371cbde2e87f289
ms.sourcegitcommit: ea76aade54134afaf5023145fcb755e40c7b84b7
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/15/2019
ms.locfileid: "59573620"
---
# <a name="class-mipidentity"></a>classe mip::Identity 
Abstração para a identidade.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
Identity() pública  |  Predefinido [identidade](class_mip_identity.md) construtor utilizado quando um endereço de e-mail do utilizador não é conhecido.
pública identidade (identidade const e outros)  |  [Identidade](class_mip_identity.md) construtor de cópia.
Identidade explícita pública (const Std:: String e e-mail)  |  [Identidade](class_mip_identity.md) construtor utilizado quando um endereço de e-mail do utilizador é conhecido.
public const std::string& GetEmail() const  |  Obter a mensagem de e-mail.
SetDelegatedEmail void pública (const Std:: String & delegatedEmail)  |  Conjuntos de e-mail delegado, um endereço de e-mail delegado é um nome de utilizador para o qual os opertations são executadas.
public const std::string& GetDelegatedEmail() const  |  Recebeu o e-mail de delegados, um endereço de e-mail de delegado é um nome de utilizador para o qual os opertations são executadas.
  
## <a name="members"></a>Membros
  
### <a name="identity-function"></a>Função de identidade
Predefinido [identidade](class_mip_identity.md) construtor utilizado quando um endereço de e-mail do utilizador não é conhecido.
  
### <a name="identity-function"></a>Função de identidade
[Identidade](class_mip_identity.md) construtor de cópia.

Parâmetros:  
* **[Identidade](class_mip_identity.md)**: utilizado para criar a cópia.


  
### <a name="identity-function"></a>Função de identidade
[Identidade](class_mip_identity.md) construtor utilizado quando um endereço de e-mail do utilizador é conhecido.

Parâmetros:  
* **e-mail**: endereço de e-mail do utilizador.


  
### <a name="getemail-function"></a>Função de GetEmail
Obter a mensagem de e-mail.

  
**Devolve**: O e-mail.
  
### <a name="setdelegatedemail-function"></a>Função de SetDelegatedEmail
Conjuntos de e-mail delegado, um endereço de e-mail delegado é um nome de utilizador para o qual os opertations são executadas.

Parâmetros:  
* **delegatedEmail**: a mensagem de e-mail de delegação.


  
### <a name="getdelegatedemail-function"></a>Função de GetDelegatedEmail
Recebeu o e-mail de delegados, um endereço de e-mail de delegado é um nome de utilizador para o qual os opertations são executadas.

  
**Devolve**: O e-mail de delegado.
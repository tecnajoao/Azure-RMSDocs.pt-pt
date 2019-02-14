---
title: classe mip::Identity
description: Documenta a classe mip::identity da Microsoft Information Protection (MIP) SDK.
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: b315dd23ee6dddfc20b2c4d9febdbfabd0ecb3b3
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56255109"
---
# <a name="class-mipidentity"></a>classe mip::Identity 
Abstração para a identidade.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
Identity() pública  |  Predefinido [identidade](class_mip_identity.md) construtor utilizado quando um endereço de e-mail do utilizador não é conhecido.
Identidade explícita pública (const Std:: String e e-mail)  |  [Identidade](class_mip_identity.md) construtor utilizado quando um endereço de e-mail do utilizador é conhecido.
public const std::string& GetEmail() const  |  Obter a mensagem de e-mail.
SetDelegatedEmail void pública (const Std:: String & delegatedEmail)  |  Conjuntos de e-mail delegado, um endereço de e-mail delegado é um nome de utilizador para o qual os opertations são executadas.
public const std::string& GetDelegatedEmail() const  |  Recebeu o e-mail de delegados, um endereço de e-mail de delegado é um nome de utilizador para o qual os opertations são executadas.
  
## <a name="members"></a>Membros
  
### <a name="identity-function"></a>Função de identidade
Predefinido [identidade](class_mip_identity.md) construtor utilizado quando um endereço de e-mail do utilizador não é conhecido.
  
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

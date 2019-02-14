---
title: classe mip::ProtectionDescriptorBuilder
description: Documenta a classe mip::protectiondescriptorbuilder da Microsoft Information Protection (MIP) SDK.
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: e704dde11ab210638c4e1fd273bc0b1407817813
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56252219"
---
# <a name="class-mipprotectiondescriptorbuilder"></a>classe mip::ProtectionDescriptorBuilder 
Constrói uma [ProtectionDescriptor](class_mip_protectiondescriptor.md) que descreve a proteção associada a uma parte do conteúdo.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
público MIP_API std::shared_ptr\<ProtectionDescriptor\> Build()  |  Cria um [ProtectionDescriptor](class_mip_protectiondescriptor.md) cujas permissões de acesso são definidas por este [ProtectionDescriptorBuilder](class_mip_protectiondescriptorbuilder.md) instância.
SetName void pública (const Std:: String & valor)  |  Nome da política de proteção conjuntos.
SetDescription void pública (const Std:: String & valor)  |  Define a descrição da política de proteção.
SetContentValidUntil void pública (const std::chrono::time_point\<std::chrono::system_clock\>& valor)  |  Define a hora de expiração de política de proteção.
SetAllowOfflineAccess void pública (valor bool)  |  Conjuntos de se permite offline a política de proteção de acesso ao conteúdo ou não.
public void SetReferrer(const std::string& uri)  |  Define o endereço de referência de política de proteção.
public void SetEncryptedAppData(const std::map\<std::string, std::string\>& value)  |  Conjuntos de dados de aplicação específicos que devem ser encriptados.
SetSignedAppData void pública (const std::map\<Std:: String, Std:: String\>& valor)  |  Conjuntos de dados específicos da aplicação que devem ser assinados.
public virtual ~ProtectionDescriptorBuilder()  | _Ainda não documentado._
  
## <a name="members"></a>Membros
  
### <a name="build-function"></a>Criar função
Cria um [ProtectionDescriptor](class_mip_protectiondescriptor.md) cujas permissões de acesso são definidas por este [ProtectionDescriptorBuilder](class_mip_protectiondescriptorbuilder.md) instância.

  
**Devolve**: Novos [ProtectionDescriptor](class_mip_protectiondescriptor.md) instância
  
### <a name="setname-function"></a>Função de SetName
Nome da política de proteção conjuntos.

Parâmetros:  
* **Valor**: Nome da política de proteção


  
### <a name="setdescription-function"></a>Função de SetDescription
Define a descrição da política de proteção.

Parâmetros:  
* **Valor**: Descrição da política


  
### <a name="setcontentvaliduntil-function"></a>Função de SetContentValidUntil
Define a hora de expiração de política de proteção.

Parâmetros:  
* **Valor**: Hora de expiração de política


  
### <a name="setallowofflineaccess-function"></a>Função de SetAllowOfflineAccess
Conjuntos de se permite offline a política de proteção de acesso ao conteúdo ou não.

Parâmetros:  
* **Valor**: Se a política permitir acesso ao conteúdo offline ou não


  
### <a name="setreferrer-function"></a>Função de SetReferrer
Define o endereço de referência de política de proteção.

Parâmetros:  
* **uri**: Endereço do referenciador de política


O Referenciador for um URI que pode ser apresentado ao utilizador após a aquisição de política de proteção com falhas que contém informações sobre como esse utilizador pode obter a permissão para aceder ao conteúdo.
  
### <a name="setencryptedappdata-function"></a>Função de SetEncryptedAppData
Conjuntos de dados de aplicação específicos que devem ser encriptados.

Parâmetros:  
* **Valor**: Dados específicos da aplicação


Um aplicativo pode especificar um dicionário de dados específicos da aplicação serão encriptados pelo serviço de proteção. Estes dados encriptados são independentes do conjunto de dados assinado pelo SetSignedAppData.
  
### <a name="setsignedappdata-function"></a>Função de SetSignedAppData
Conjuntos de dados específicos da aplicação que devem ser assinados.

Parâmetros:  
* **Valor**: Dados específicos da aplicação


Um aplicativo pode especificar um dicionário de dados específicos da aplicação que irão ser assinados pelo serviço de proteção. Estes dados assinados são independentes do conjunto de dados criptografado por SetEncryptedAppData.
  
### <a name="protectiondescriptorbuilder-function"></a>~ Função de ProtectionDescriptorBuilder
_Não documentados ainda._

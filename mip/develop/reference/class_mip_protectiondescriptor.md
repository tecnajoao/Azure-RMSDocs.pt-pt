---
title: classe mip::ProtectionDescriptor
description: Documenta a classe mip::protectiondescriptor da Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 6f4bb83950a4745739a1663950a52d05c51f7f4d
ms.sourcegitcommit: ea76aade54134afaf5023145fcb755e40c7b84b7
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/15/2019
ms.locfileid: "59573297"
---
# <a name="class-mipprotectiondescriptor"></a>classe mip::ProtectionDescriptor 
Descrição de proteção associada a uma parte do conteúdo.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
público GetProtectionType() de ProtectionType const  |  Obtém o tipo de proteção, se foi gerado a partir de modelo do SDK de proteção ou não.
public std::string GetOwner() const  |  Obtém o proprietário para a proteção.
public std::string GetName() const  |  Obtém o nome de proteção.
público Std:: String GetDescription() const  |  Obtém a descrição de proteção.
public std::string GetTemplateId() const  |  Obtém o ID do modelo de proteção, se aplicável.
public std::string GetLabelId() const  |  Obtém o ID de etiqueta, caso existam.
public std::string GetContentId() const  |  Obtém o ID de conteúdo, se aplicável.
público Std:: vector\<UserRights\> GetUserRights() const  |  Obtém a coleção de mapeamentos de direitos de usuários.
público Std:: vector\<funções de utilizador\> GetUserRoles() const  |  Obtém a coleção de mapeamentos de funções de utilizadores.
bool pública DoesContentExpire() const  |  Verifica se o conteúdo tem um prazo de expiração ou não.
público std::chrono::time_point\<std::chrono::system_clock\> GetContentValidUntil() const  |  Obtém a hora de expiração de proteção.
bool pública DoesAllowOfflineAccess() const  |  Obtém se permite offline a proteção de acesso ao conteúdo ou não.
public std::string GetReferrer() const  |  Obtém o endereço do referenciador de proteção.
public std::map\<std::string, std::string\> GetEncryptedAppData() const  |  Obtém dados específicos da aplicação que foi encriptados.
public std::map\<std::string, std::string\> GetSignedAppData() const  |  Obtém os dados específicos da aplicação que foi assinados.
  
## <a name="members"></a>Membros
  
### <a name="getprotectiontype-function"></a>Função de GetProtectionType
Obtém o tipo de proteção, se foi gerado a partir de modelo do SDK de proteção ou não.

  
**Devolve**: Tipo de proteção
  
### <a name="getowner-function"></a>Função de GetOwner
Obtém o proprietário para a proteção.

  
**Devolve**: Proprietário de proteção
  
### <a name="getname-function"></a>Função de GetName
Obtém o nome de proteção.

  
**Devolve**: Nome de proteção
  
### <a name="getdescription-function"></a>Função de GetDescription
Obtém a descrição de proteção.

  
**Devolve**: Descrição de proteção
  
### <a name="gettemplateid-function"></a>Função de GetTemplateId
Obtém o ID do modelo de proteção, se aplicável.

  
**Devolve**: ID do modelo
  
### <a name="getlabelid-function"></a>Função de GetLabelId
Obtém o ID de etiqueta, caso existam.

  
**Devolve**: [Etiqueta](class_mip_label.md) esta propriedade só irá ser preenchida no ProtectionDescriptors para preexistente de ID de conteúdo protegido. É um campo preenchido pelo servidor neste momento é consumido conteúdo protegido.
  
### <a name="getcontentid-function"></a>GetContentId function
Obtém o ID de conteúdo, se aplicável.

  
**Devolve**: ID de conteúdo
  
### <a name="getuserrights-function"></a>Função de GetUserRights
Obtém a coleção de mapeamentos de direitos de usuários.

  
**Devolve**: Coleção de mapeamentos de direitos de usuários o valor do [UserRights](class_mip_userrights.md) propriedade estará vazia se o utilizador atual não tem acesso a essas informações (ou seja, se o utilizador não é o proprietário e não tem direito a VIEWRIGHTSDATA).
  
### <a name="getuserroles-function"></a>Função de GetUserRoles
Obtém a coleção de mapeamentos de funções de utilizadores.

  
**Devolve**: Coleção de mapeamentos de funções de utilizadores
  
### <a name="doescontentexpire-function"></a>Função de DoesContentExpire
Verifica se o conteúdo tem um prazo de expiração ou não.

  
**Devolve**: VERDADEIRO se o conteúdo podem expirar, outra false
  
### <a name="getcontentvaliduntil-function"></a>Função de GetContentValidUntil
Obtém a hora de expiração de proteção.

  
**Devolve**: Hora de expiração de proteção
  
### <a name="doesallowofflineaccess-function"></a>Função de DoesAllowOfflineAccess
Obtém se permite offline a proteção de acesso ao conteúdo ou não.

  
**Devolve**: Se a proteção permite o acesso ao conteúdo offline ou não (predefinição = true)
  
### <a name="getreferrer-function"></a>Função de GetReferrer
Obtém o endereço do referenciador de proteção.

  
**Devolve**: Endereço do referenciador de proteção o Referenciador for um URI que é visualizáveis ao usuário se eles não podem desproteger o conteúdo. Contém informações sobre como esse utilizador pode obter a permissão para aceder ao conteúdo.
  
### <a name="getencryptedappdata-function"></a>Função de GetEncryptedAppData
Obtém dados específicos da aplicação que foi encriptados.

  
**Devolve**: Dados de aplicação específicos A [ProtectionHandler](class_mip_protectionhandler.md) pode manter um dicionário de dados específicos da aplicação que foi encriptados pelo serviço de proteção. Estes dados encriptados são independentes dos dados assinados podem ser acedidos através de ProtectionDescriptor::GetSignedAppData.
  
### <a name="getsignedappdata-function"></a>Função de GetSignedAppData
Obtém os dados específicos da aplicação que foi assinados.

  
**Devolve**: Dados de aplicação específicos A [ProtectionHandler](class_mip_protectionhandler.md) pode manter um dicionário de dados específicos da aplicação que foi assinados pelo serviço de proteção. Estes dados assinados são independentes dos dados encriptados podem ser acedidos através de [ProtectionDescriptor::GetEncryptedAppData](class_mip_protectiondescriptor.md#getencryptedappdata-function)
---
title: classe mip ProtectionDescriptor
description: Referência para a classe mip ProtectionDescriptor
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: e723041af1eec7be7a839bf36f6d3db67b32447f
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446554"
---
# <a name="class-mipprotectiondescriptor"></a>classe mip::ProtectionDescriptor 
Descrição de proteção associada a uma parte do conteúdo.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 público GetProtectionType() de ProtectionType const  |  Obtém o tipo de proteção, se foi gerado a partir de modelo do SDK de proteção ou não.
 público Std:: String GetOwner() const  |  Obtém o proprietário para a proteção.
 público Std:: String GetName() const  |  Obtém o nome de proteção.
 público Std:: String GetDescription() const  |  Obtém a descrição de proteção.
 público Std:: String GetTemplateId() const  |  Obtém o ID do modelo de proteção, se aplicável.
 público Std:: String GetLabelId() const  |  Obtém o ID de etiqueta, caso existam.
público Std:: vector<UserRights> GetUserRights() const  |  Obtém a coleção de mapeamentos de direitos de usuários.
público Std:: vector<UserRoles> GetUserRoles() const  |  Obtém a coleção de mapeamentos de funções de utilizadores.
std::chrono::time_point público < std::chrono::system_clock > GetContentValidUntil() const  |  Obtém a hora de expiração de proteção.
 bool pública DoesAllowOfflineAccess() const  |  Obtém se permite offline a proteção de acesso ao conteúdo ou não.
 público Std:: String GetReferrer() const  |  Obtém o endereço do referenciador de proteção.
std::map público < Std:: String, Std:: String > GetEncryptedAppData() const  |  Obtém dados específicos da aplicação que foi encriptados.
std::map público < Std:: String, Std:: String > GetSignedAppData() const  |  Obtém os dados específicos da aplicação que foi assinados.
  
## <a name="members"></a>Membros
  
### <a name="protectiontype"></a>ProtectionType
Obtém o tipo de proteção, se foi gerado a partir de modelo do SDK de proteção ou não.

  
**Devolve**: tipo de proteção
  
### <a name="getowner"></a>GetOwner
Obtém o proprietário para a proteção.

  
**Devolve**: proprietário de proteção
  
### <a name="getname"></a>GetName
Obtém o nome de proteção.

  
**Devolve**: nome de proteção
  
### <a name="getdescription"></a>GetDescription
Obtém a descrição de proteção.

  
**Devolve**: descrição de proteção
  
### <a name="gettemplateid"></a>GetTemplateId
Obtém o ID do modelo de proteção, se aplicável.

  
**Devolve**: ID do modelo
  
### <a name="getlabelid"></a>GetLabelId
Obtém o ID de etiqueta, caso existam.

  
**Devolve**: [etiqueta](class_mip_label.md) esta propriedade só irá ser preenchida no ProtectionDescriptors para preexistente de ID de conteúdo protegido. É um campo preenchido pelo servidor neste momento é consumido conteúdo protegido.
  
### <a name="userrights"></a>UserRights
Obtém a coleção de mapeamentos de direitos de usuários.

  
**Devolve**: a coleção de mapeamentos de direitos de usuários o valor da [UserRights](class_mip_userrights.md) propriedade estará vazia se o utilizador atual não tem acesso a essas informações (ou seja, se o utilizador não é o proprietário e não tem o Direito VIEWRIGHTSDATA).
  
### <a name="userroles"></a>Funções de utilizador
Obtém a coleção de mapeamentos de funções de utilizadores.

  
**Devolve**: coleção de mapeamentos de funções de utilizadores
  
### <a name="getcontentvaliduntil"></a>GetContentValidUntil
Obtém a hora de expiração de proteção.

  
**Devolve**: hora de expiração de proteção
  
### <a name="doesallowofflineaccess"></a>DoesAllowOfflineAccess
Obtém se permite offline a proteção de acesso ao conteúdo ou não.

  
**Devolve**: se a proteção permite o acesso ao conteúdo offline ou não (predefinição = true)
  
### <a name="getreferrer"></a>GetReferrer
Obtém o endereço do referenciador de proteção.

  
**Devolve**: endereço do referenciador de proteção do referenciador é um URI que é visualizáveis ao usuário se eles não podem desproteger o conteúdo. Contém informações sobre como esse utilizador pode obter a permissão para aceder ao conteúdo.
  
### <a name="getencryptedappdata"></a>GetEncryptedAppData
Obtém dados específicos da aplicação que foi encriptados.

  
**Devolve**: A de dados de aplicação específicos [ProtectionHandler](class_mip_protectionhandler.md) pode manter um dicionário de dados específicos da aplicação que foi encriptados pelo serviço de proteção. Estes dados encriptados são independentes dos dados assinados podem ser acedidos através de [ProtectionDescriptor::GetSignedAppData](class_mip_protectiondescriptor.md#getsignedappdata)
  
### <a name="getsignedappdata"></a>GetSignedAppData
Obtém os dados específicos da aplicação que foi assinados.

  
**Devolve**: A de dados de aplicação específicos [ProtectionHandler](class_mip_protectionhandler.md) pode manter um dicionário de dados específicos da aplicação que foi assinados pelo serviço de proteção. Estes dados assinados são independentes dos dados encriptados podem ser acedidos através de [ProtectionDescriptor::GetEncryptedAppData](class_mip_protectiondescriptor.md#getencryptedappdata)
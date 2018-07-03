# <a name="class-mipprotectiondescriptorbuilder"></a>classe mip::ProtectionDescriptorBuilder 
Representa uma política ad-hoc associada com conteúdo protegido.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
público MIP_API std::shared_ptr<ProtectionDescriptor> Build()  |  Cria um [ProtectionDescriptor](class_mip_protectiondescriptor.md) cujas permissões de acesso são definidas por este [ProtectionDescriptorBuilder](class_mip_protectiondescriptorbuilder.md) instância.
 SetName void pública (const Std:: String & valor)  |  Nome da política de proteção conjuntos.
 SetDescription void pública (const Std:: String & valor)  |  Define a descrição da política de proteção.
SetContentValidUntil void pública (const std::chrono::time_point < std::chrono::system_clock > & valor)  |  Define a hora de expiração de política de proteção.
 SetAllowOfflineAccess void pública (valor bool)  |  Define se é ou não permite offline a política de proteção de acesso ao conteúdo.
 SetReferrer void pública (const Std:: String & uri)  |  Define o endereço de referência de política de proteção.
SetEncryptedAppData void pública (std::map const < Std:: String, Std:: String > & valor)  |  Conjuntos de dados de aplicação específicos que devem ser encriptados.
SetSignedAppData void pública (std::map const < Std:: String, Std:: String > & valor)  |  Conjuntos de dados específicos da aplicação que devem ser assinados.
 público ~ProtectionDescriptorBuilder() virtual  | _Ainda não documentado._
  
## <a name="members"></a>Membros
  
### <a name="protectiondescriptor"></a>ProtectionDescriptor
Cria um [ProtectionDescriptor](class_mip_protectiondescriptor.md) cujas permissões de acesso são definidas por este [ProtectionDescriptorBuilder](class_mip_protectiondescriptorbuilder.md) instância.

  
**Devolve**: nova [ProtectionDescriptor](class_mip_protectiondescriptor.md) instância
  
### <a name="setname"></a>SetName
Nome da política de proteção conjuntos.

Parâmetros:  
* **valor**: nome da política de proteção


  
### <a name="setdescription"></a>SetDescription
Define a descrição da política de proteção.

Parâmetros:  
* **valor**: descrição de política


  
### <a name="setcontentvaliduntil"></a>SetContentValidUntil
Define a hora de expiração de política de proteção.

Parâmetros:  
* **valor**: hora de expiração de política


  
### <a name="setallowofflineaccess"></a>SetAllowOfflineAccess
Define se é ou não permite offline a política de proteção de acesso ao conteúdo.

Parâmetros:  
* **valor**: ou não a diretiva permite acesso ao conteúdo offline


  
### <a name="setreferrer"></a>SetReferrer
Define o endereço de referência de política de proteção.

Parâmetros:  
* **URI**: endereço do referenciador de política


O Referenciador for um URI que pode ser apresentado ao utilizador após a aquisição de política de proteção com falhas que contém informações sobre como esse utilizador pode obter a permissão para aceder ao conteúdo.
  
### <a name="setencryptedappdata"></a>SetEncryptedAppData
Conjuntos de dados de aplicação específicos que devem ser encriptados.

Parâmetros:  
* **valor**: dados específicos da aplicação


Um aplicativo pode especificar um dicionário de dados específicos da aplicação serão encriptados pelo serviço de proteção. Estes dados encriptados são independentes do conjunto de dados assinado pelo SetSignedAppData.
  
### <a name="setsignedappdata"></a>SetSignedAppData
Conjuntos de dados específicos da aplicação que devem ser assinados.

Parâmetros:  
* **valor**: dados específicos da aplicação


Um aplicativo pode especificar um dicionário de dados específicos da aplicação que irão ser assinados pelo serviço de proteção. Estes dados assinados são independentes do conjunto de dados criptografado por SetEncryptedAppData.
  
### <a name="protectiondescriptorbuilder"></a>~ ProtectionDescriptorBuilder
_Não documentados ainda._

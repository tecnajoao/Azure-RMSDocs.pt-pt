# <a name="class-mipcontentlabel"></a>classe mip::ContentLabel 
Abstração para uma etiqueta do Microsoft Information Protection que é aplicada a uma parte do conteúdo, normalmente, um documento.
Além das informações de etiqueta, ele contém propriedades para uma etiqueta aplicada específica.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 público const Std:: String & GetCreationTime() const  |  Obter a hora de criação da etiqueta.
 público GetAssignmentMethod() de AssignmentMethod const  |  Obtenha o método de atribuição da etiqueta.
público const Std:: vector < std::pair < Std:: String, Std:: String >> & GetExtendedProperties() const  |  Devolve se ou não a proteção foi aplicada por etiqueta.
 bool pública IsProtectionAppliedFromLabel() const  |  Devolve se ou não a proteção foi aplicada por etiqueta.
público std::shared_ptr<Label> const getlabel)  |  Obtenha o objeto de rótulo real aplicadas no conteúdo.
  
## <a name="members"></a>Membros
  
### <a name="getcreationtime"></a>GetCreationTime
Obter a hora de criação da etiqueta.

  
**Devolve**: hora de criação como uma cadeia de gmt.
  
### <a name="getassignmentmethod"></a>GetAssignmentMethod
Obtenha o método de atribuição da etiqueta.

  
**Devolve**: AssignmentMethod STANDARD | PRIVILEGED | AUTOMÁTICA. 
  
**Consulte também**: mip::AssignmentMethod
  
### <a name="getextendedproperties"></a>GetExtendedProperties
Devolve se ou não a proteção foi aplicada por etiqueta.

  
**Devolve**: True se existir proteção de modelo e era por esta etiqueta, caso contrário falsa.
  
### <a name="isprotectionappliedfromlabel"></a>IsProtectionAppliedFromLabel
Devolve se ou não a proteção foi aplicada por etiqueta.

  
**Devolve**: True se existir proteção de modelo e era por esta etiqueta, caso contrário falsa.
  
### <a name="label"></a>Etiqueta
Obtenha o objeto de rótulo real aplicadas no conteúdo.

  
**Devolve**: O objeto de etiqueta aplicado no conteúdo. 
  
**Consulte também**: [mip::Label](class_mip_label.md)
# <a name="class-mipcontentlabel"></a>classe mip::ContentLabel 
Abstração para uma etiqueta de Microsoft Information Protection, que é aplicada a um conjunto de conteúdo, normalmente, um documento.
Além das informações de etiqueta, realiza as propriedades de uma etiqueta aplicada específica.
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
pública std::string const & GetCreationTime | Obter a hora de criação da etiqueta.
pública AssignmentMethod GetAssignmentMethod | Obter o método de atribuição da etiqueta.
std::shared_ptr pública < etiqueta > GetLabel | Obter o objeto da etiqueta real aplicado no conteúdo.
## <a name="members"></a>Membros
### <a name="getcreationtime"></a>GetCreationTime
Obter a hora de criação da etiqueta.
#### <a name="returns"></a>Devolve
Hora de criação como uma cadeia de gmt.
### <a name="getassignmentmethod"></a>GetAssignmentMethod
Obter o método de atribuição da etiqueta.
#### <a name="returns"></a>Devolve
AssignmentMethod padrão | PRIVILEGED | AUTOMÁTICA. 
**Consulte também**: mip::AssignmentMethod
### <a name="label"></a>Etiqueta
Obter o objeto da etiqueta real aplicado no conteúdo.
#### <a name="returns"></a>Devolve
o objeto da etiqueta aplicado no conteúdo. 
**Consulte também**: [mip::Label](#classmip_1_1_label)
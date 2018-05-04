# <a name="class-mipfilehandlerobserver"></a>classe mip::FileHandler::Observer 
[Observador](#classmip_1_1_file_handler_1_1_observer) interface para os clientes receber notificações para o ficheiro de processador de eventos relacionados.
Se um * evento de erro ocorre, o objeto erro contém dentro [mip::Error](#classmip_1_1_error) classe. Cliente deve não chamar o motor de volta no thread que chama o observador.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
~Observer() virtual inline público  |  
OnGetLabelSuccess void público (const std::shared_ptr<ContentLabel>& etiqueta, const std::shared_ptr<void>& contexto)  |  Chamado quando a etiqueta é obtida com êxito (a partir do ficheiro).
OnGetLabelFailure void público (const std::exception_ptr & erro, const std::shared_ptr<void>& contexto)  |  Chamado quando a falha ao obter a etiqueta (a partir do ficheiro) devido a um erro.
OnGetProtectionSuccess void público (const std::shared_ptr<UserPolicy>& userPolicy, const std::shared_ptr<void>& contexto)  |  Chamado quando a política de proteção é obtida com êxito (a partir do ficheiro).
OnGetProtectionFailure void público (const std::exception_ptr & erro, const std::shared_ptr<void>& contexto)  |  Chamado quando a falha ao obter a política de proteção (a partir do ficheiro) devido a um erro.
OnCommitSuccess void público (bool consolidado, const std::shared_ptr<void>& contexto)  |  Chamado quando a consolidar as alterações para o ficheiro foi concluída com êxito.
OnCommitFailure void público (const std::exception_ptr & erro, const std::shared_ptr<void>& contexto)  |  Chamado quando a consolidar as alterações ao ficheiro falhou devido a um erro.
inline protegido Observer()  |  
  
## <a name="members"></a>Membros
  
### <a name="observer"></a>~ Observador
  
### <a name="ongetlabelsuccess"></a>OnGetLabelSuccess
Chamado quando a etiqueta é obtida com êxito (a partir do ficheiro).
  
### <a name="ongetlabelfailure"></a>OnGetLabelFailure
Chamado quando a falha ao obter a etiqueta (a partir do ficheiro) devido a um erro.
  
### <a name="ongetprotectionsuccess"></a>OnGetProtectionSuccess
Chamado quando a política de proteção é obtida com êxito (a partir do ficheiro).
  
### <a name="ongetprotectionfailure"></a>OnGetProtectionFailure
Chamado quando a falha ao obter a política de proteção (a partir do ficheiro) devido a um erro.
  
### <a name="oncommitsuccess"></a>OnCommitSuccess
Chamado quando a consolidar as alterações para o ficheiro foi concluída com êxito.
  
### <a name="oncommitfailure"></a>OnCommitFailure
Chamado quando a consolidar as alterações ao ficheiro falhou devido a um erro.
  
### <a name="observer"></a>Observador
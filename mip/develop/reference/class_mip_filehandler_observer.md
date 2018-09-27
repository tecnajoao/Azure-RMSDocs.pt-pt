# <a name="class-mipfilehandlerobserver"></a>classe mip::FileHandler::Observer 
[Observador](class_mip_filehandler_observer.md) interface para os clientes obter notificações para ficheiros relacionados com o manipulador de eventos.
Se um * eventos de erro ocorrer, o objeto de erro contém dentro [mip::Error](class_mip_error.md) classe. Cliente não deve chamar o mecanismo de volta no thread que chama o observador.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
OnCreateFileHandlerSuccess de void virtual público (const std::shared_ptr<FileHandler>& fileHandler, const std::shared_ptr<void>& contexto)  |  Chamado quando o manipulador é criado com êxito.
OnCreateFileHandlerFailure de void virtual público (const std::exception_ptr e erro, const std::shared_ptr<void>& contexto)  |  Chamado quando a falha ao criar o manipulador devido a um erro.
OnGetLabelSuccess de void virtual público (const std::shared_ptr<ContentLabel>& etiqueta, const std::shared_ptr<void>& contexto)  |  Chamado quando a etiqueta é recuperada com êxito.
OnGetLabelFailure de void virtual público (const std::exception_ptr e erro, const std::shared_ptr<void>& contexto)  |  Chamado quando a falha ao obter a etiqueta devido a um erro.
OnGetProtectionSuccess de void virtual público (const std::shared_ptr<ProtectionHandler>& protectionHandler, const std::shared_ptr<void>& contexto)  |  Chamado quando a política de proteção é obtida com êxito.
OnGetProtectionFailure de void virtual público (const std::exception_ptr e erro, const std::shared_ptr<void>& contexto)  |  Chamado quando a obter a política de proteção falhou devido a um erro.
OnCommitSuccess de void virtual público (bool confirmada, const std::shared_ptr<void>& contexto)  |  Chamado quando a consolidar as alterações no ficheiro foram bem-sucedidas.
OnCommitFailure de void virtual público (const std::exception_ptr e erro, const std::shared_ptr<void>& contexto)  |  Chamado quando a consolidar as alterações para o ficheiro falhou devido a um erro.
  
## <a name="members"></a>Membros
  
### <a name="oncreatefilehandlersuccess"></a>OnCreateFileHandlerSuccess
Chamado quando o manipulador é criado com êxito.
  
### <a name="oncreatefilehandlerfailure"></a>OnCreateFileHandlerFailure
Chamado quando a falha ao criar o manipulador devido a um erro.
  
### <a name="ongetlabelsuccess"></a>OnGetLabelSuccess
Chamado quando a etiqueta é recuperada com êxito.
  
### <a name="ongetlabelfailure"></a>OnGetLabelFailure
Chamado quando a falha ao obter a etiqueta devido a um erro.
  
### <a name="ongetprotectionsuccess"></a>OnGetProtectionSuccess
Chamado quando a política de proteção é obtida com êxito.
  
### <a name="ongetprotectionfailure"></a>OnGetProtectionFailure
Chamado quando a obter a política de proteção falhou devido a um erro.
  
### <a name="oncommitsuccess"></a>OnCommitSuccess
Chamado quando a consolidar as alterações no ficheiro foram bem-sucedidas.
  
### <a name="oncommitfailure"></a>OnCommitFailure
Chamado quando a consolidar as alterações para o ficheiro falhou devido a um erro.
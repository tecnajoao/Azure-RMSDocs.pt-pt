# <a name="class-mipprotectionprofile"></a>classe mip::ProtectionProfile 
[ProtectionProfile](class_mip_protectionprofile.md) é a classe de raiz para efetuar operações de proteção.
Uma aplicação tem de criar um [ProtectionProfile](class_mip_protectionprofile.md) antes de efetuar quaisquer operações de proteção
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 Definições de const público & GetSettings() const  |  Obtém as definições utilizadas pelo [ProtectionProfile](class_mip_protectionprofile.md) durante a inicialização e ao longo da respetiva duração.
 ClearCaches() void público  |  Elimina caches (por exemplo, consentimento bases de dados, etc.)
  
## <a name="members"></a>Membros
  
### <a name="settings"></a>Definições
Obtém as definições utilizadas pelo [ProtectionProfile](class_mip_protectionprofile.md) durante a inicialização e ao longo da respetiva duração.

  
**Devolve**: [definições](class_mip_protectionprofile_settings.md) utilizado pelo [ProtectionProfile](class_mip_protectionprofile.md) durante a inicialização e ao longo da respetiva duração
  
### <a name="clearcaches"></a>ClearCaches
Elimina caches (por exemplo, consentimento bases de dados, etc.) Útil para fins de teste e depuração
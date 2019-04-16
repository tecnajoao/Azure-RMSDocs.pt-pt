---
title: classe mip::FileProfile
description: Documenta a classe mip::fileprofile da Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: b9f5fba87246d0ce89c3e34733bf311b23478334
ms.sourcegitcommit: ea76aade54134afaf5023145fcb755e40c7b84b7
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/15/2019
ms.locfileid: "59572957"
---
# <a name="class-mipfileprofile"></a>classe mip::FileProfile 
[FileProfile](class_mip_fileprofile.md) classe é a classe de raiz para as operações do Microsoft Information Protection a utilizar.
Um aplicativo típico apenas terá um perfil.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
Definições de const públicas & GetSettings() const  |  Devolve as definições de perfil.
public void ListEnginesAsync(const std::shared_ptr\<void\>& context)  |  Começa a lista a operação de mecanismos.
public void UnloadEngineAsync(const std::string& id, const std::shared_ptr\<void\>& context)  |  É iniciado, descarregando o mecanismo de ficheiro com o ID especificado.
AddEngineAsync void pública (const FileEngine::Settings e definições, const std::shared_ptr\<void\>& contexto)  |  Inicia a adicionar um novo mecanismo de ficheiro para o perfil.
public void DeleteEngineAsync(const std::string& id, const std::shared_ptr\<void\>& context)  |  Começa a eliminar o mecanismo de ficheiro com o ID especificado. Todos os dados para o perfil de determinado serão eliminados.
  
## <a name="members"></a>Membros
  
### <a name="getsettings-function"></a>Função de GetSettings
Devolve as definições de perfil.
  
### <a name="listenginesasync-function"></a>Função de ListEnginesAsync
Começa a lista a operação de mecanismos.
[FileProfile::Observer](class_mip_fileprofile_observer.md) será chamado após o êxito ou falha.
  
### <a name="unloadengineasync-function"></a>Função de UnloadEngineAsync
É iniciado, descarregando o mecanismo de ficheiro com o ID especificado.
[FileProfile::Observer](class_mip_fileprofile_observer.md) será chamado após o êxito ou falha.
  
### <a name="addengineasync-function"></a>Função de AddEngineAsync
Inicia a adicionar um novo mecanismo de ficheiro para o perfil.
[FileProfile::Observer](class_mip_fileprofile_observer.md) será chamado após o êxito ou falha.
  
### <a name="deleteengineasync-function"></a>Função de DeleteEngineAsync
Começa a eliminar o mecanismo de ficheiro com o ID especificado. Todos os dados para o perfil de determinado serão eliminados.
[FileProfile::Observer](class_mip_fileprofile_observer.md) será chamado após o êxito ou falha.
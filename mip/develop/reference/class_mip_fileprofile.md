---
title: classe mip FileProfile
description: Referência para a classe mip FileProfile
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: f317f1eff0266db1da211e164ec5e427ba7ce17d
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445891"
---
# <a name="class-mipfileprofile"></a>classe mip::FileProfile 
[FileProfile](class_mip_fileprofile.md) classe é a classe de raiz para as operações do Microsoft Information Protection a utilizar.
Um aplicativo típico apenas terá um perfil.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 Definições de const públicas & GetSettings() const  |  Devolve as definições de perfil.
ListEnginesAsync void pública (const std::shared_ptr<void>& contexto)  |  Começa a lista a operação de mecanismos.
UnloadEngineAsync void pública (Std:: String const & id, const std::shared_ptr<void>& contexto)  |  É iniciado, descarregando o mecanismo de ficheiro com o ID especificado.
AddEngineAsync void pública (const FileEngine::Settings e definições, const std::shared_ptr<void>& contexto)  |  Inicia a adicionar um novo mecanismo de ficheiro para o perfil.
DeleteEngineAsync void pública (Std:: String const & id, const std::shared_ptr<void>& contexto)  |  Começa a eliminar o mecanismo de ficheiro com o ID especificado. Todos os dados para o perfil de determinado serão eliminados.
  
## <a name="members"></a>Membros
  
### <a name="settings"></a>Definições
Devolve as definições de perfil.
  
### <a name="listenginesasync"></a>ListEnginesAsync
Começa a lista a operação de mecanismos.
[FileProfile::Observer](class_mip_fileprofile_observer.md) será chamado após o êxito ou falha.
  
### <a name="unloadengineasync"></a>UnloadEngineAsync
É iniciado, descarregando o mecanismo de ficheiro com o ID especificado.
[FileProfile::Observer](class_mip_fileprofile_observer.md) será chamado após o êxito ou falha.
  
### <a name="addengineasync"></a>AddEngineAsync
Inicia a adicionar um novo mecanismo de ficheiro para o perfil.
[FileProfile::Observer](class_mip_fileprofile_observer.md) será chamado após o êxito ou falha.
  
### <a name="deleteengineasync"></a>DeleteEngineAsync
Começa a eliminar o mecanismo de ficheiro com o ID especificado. Todos os dados para o perfil de determinado serão eliminados.
[FileProfile::Observer](class_mip_fileprofile_observer.md) será chamado após o êxito ou falha.
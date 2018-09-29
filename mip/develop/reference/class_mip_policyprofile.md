---
title: classe mip PolicyProfile
description: Referência para a classe mip PolicyProfile
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 387e28780cb0ef02d56050f534d4783fdebc286e
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446961"
---
# <a name="class-mippolicyprofile"></a>classe mip::PolicyProfile 
[PolicyProfile](class_mip_policyprofile.md) classe é a classe de raiz para as operações do Microsoft Information Protection a utilizar. Um aplicativo típico irá apenas precisa de um [PolicyProfile](class_mip_policyprofile.md) , mas ele pode criar vários perfis, se for necessário.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 Definições de const públicas & GetSettings() const  |  Obtenha as configurações definidas no perfil.
ListEnginesAsync void pública (const std::shared_ptr<void>& contexto)  |  Começa a lista a operação de mecanismos.
UnloadEngineAsync void pública (Std:: String const & id, const std::shared_ptr<void>& contexto)  |  É iniciado, descarregando o motor de política com o ID especificado.
AddEngineAsync void pública (const PolicyEngine::Settings e definições, const std::shared_ptr<void>& contexto)  |  Inicia a adicionar um novo mecanismo de política para o perfil.
DeleteEngineAsync void pública (Std:: String const & id, const std::shared_ptr<void>& contexto)  |  Começa a eliminar o motor de política com o ID especificado. Todos os dados para o perfil de determinado serão eliminados.
  
## <a name="members"></a>Membros
  
### <a name="settings"></a>Definições
Obtenha as configurações definidas no perfil.

  
**Devolve**: configurar as definições no perfil.
  
### <a name="listenginesasync"></a>ListEnginesAsync
Começa a lista a operação de mecanismos.

Parâmetros:  
* **contexto**: um parâmetro que será passado para as funções de observador. 


[PolicyProfile::Observer](class_mip_policyprofile_observer.md) será chamado após o êxito ou falha.
  
### <a name="unloadengineasync"></a>UnloadEngineAsync
É iniciado, descarregando o motor de política com o ID especificado.

Parâmetros:  
* **ID**: o ID exclusivo do motor. 


* **contexto**: um parâmetro que será reencaminhado forma opaca para as funções de observador. 


[PolicyProfile::Observer](class_mip_policyprofile_observer.md) será chamado após o êxito ou falha.
  
### <a name="addengineasync"></a>AddEngineAsync
Inicia a adicionar um novo mecanismo de política para o perfil.

Parâmetros:  
* **as definições**: a [mip::PolicyEngine::Settings](class_mip_policyengine_settings.md) objeto que especifica as definições do mecanismo. 


* **contexto**: um parâmetro que serão fowarded forma opaca para as funções de observador. 


[PolicyProfile::Observer](class_mip_policyprofile_observer.md) será chamado após o êxito ou falha.
  
### <a name="deleteengineasync"></a>DeleteEngineAsync
Começa a eliminar o motor de política com o ID especificado. Todos os dados para o perfil de determinado serão eliminados.

Parâmetros:  
* **ID**: o ID exclusivo do motor. 


* **contexto**: um parâmetro que será passado para as funções de observador. 


[PolicyProfile::Observer](class_mip_policyprofile_observer.md) será chamado após o êxito ou falha.
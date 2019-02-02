---
title: classe mip::PolicyProfile
description: Documenta a classe mip::policyprofile da Microsoft Information Protection (MIP) SDK.
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: c97f6335159f99c97ff68e233ed7d357242bedb3
ms.sourcegitcommit: be05adc7750e22c110b261882de0389b9dfb2726
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/02/2019
ms.locfileid: "55651161"
---
# <a name="class-mippolicyprofile"></a>classe mip::PolicyProfile 
[PolicyProfile](class_mip_policyprofile.md) classe é a classe de raiz para as operações do Microsoft Information Protection a utilizar. Um aplicativo típico irá apenas precisa de um [PolicyProfile](class_mip_policyprofile.md) , mas ele pode criar vários perfis, se for necessário.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
Definições de const públicas & GetSettings() const  |  Obtenha as configurações definidas no perfil.
public void ListEnginesAsync(const std::shared_ptr\<void\>& context)  |  Começa a lista a operação de mecanismos.
public void UnloadEngineAsync(const std::string& id, const std::shared_ptr\<void\>& context)  |  É iniciado, descarregando o motor de política com o ID especificado.
public void AddEngineAsync(const PolicyEngine::Settings& settings, const std::shared_ptr\<void\>& context)  |  Inicia a adicionar um novo mecanismo de política para o perfil.
public void DeleteEngineAsync(const std::string& id, const std::shared_ptr\<void\>& context)  |  Começa a eliminar o motor de política com o ID especificado. Todos os dados para o perfil de determinado serão eliminados.
  
## <a name="members"></a>Membros
  
### <a name="getsettings-function"></a>Função de GetSettings
Obtenha as configurações definidas no perfil.

  
**Devolve**: Configurar as definições no perfil.
  
### <a name="listenginesasync-function"></a>Função de ListEnginesAsync
Começa a lista a operação de mecanismos.

Parâmetros:  
* **contexto**: um parâmetro que será passado para as funções de observador. 


[PolicyProfile::Observer](class_mip_policyprofile_observer.md) será chamado após o êxito ou falha.
  
### <a name="unloadengineasync-function"></a>Função de UnloadEngineAsync
É iniciado, descarregando o motor de política com o ID especificado.

Parâmetros:  
* **ID**: o ID exclusivo do motor. 


* **contexto**: um parâmetro que será reencaminhado forma opaca para as funções de observador. 


[PolicyProfile::Observer](class_mip_policyprofile_observer.md) será chamado após o êxito ou falha.
  
### <a name="addengineasync-function"></a>Função de AddEngineAsync
Inicia a adicionar um novo mecanismo de política para o perfil.

Parâmetros:  
* **as definições**: a [mip::PolicyEngine::Settings](class_mip_policyengine_settings.md) objeto que especifica as definições do mecanismo. 


* **contexto**: um parâmetro que serão fowarded forma opaca para as funções de observador. 


[PolicyProfile::Observer](class_mip_policyprofile_observer.md) será chamado após o êxito ou falha.
  
### <a name="deleteengineasync-function"></a>Função de DeleteEngineAsync
Começa a eliminar o motor de política com o ID especificado. Todos os dados para o perfil de determinado serão eliminados.

Parâmetros:  
* **ID**: o ID exclusivo do motor. 


* **contexto**: um parâmetro que será passado para as funções de observador. 


[PolicyProfile::Observer](class_mip_policyprofile_observer.md) será chamado após o êxito ou falha.
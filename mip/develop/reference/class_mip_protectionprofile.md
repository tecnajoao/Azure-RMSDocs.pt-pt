---
title: classe mip::ProtectionProfile
description: Documenta a classe mip::protectionprofile da Microsoft Information Protection (MIP) SDK.
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: 4b7e5ecc3006ab44b1c5f55cd658a0e0b33748d3
ms.sourcegitcommit: be05adc7750e22c110b261882de0389b9dfb2726
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/02/2019
ms.locfileid: "55650957"
---
# <a name="class-mipprotectionprofile"></a>classe mip::ProtectionProfile 
[ProtectionProfile](class_mip_protectionprofile.md) é a classe de raiz para a execução de operações de proteção.
Um aplicativo precisa criar uma [ProtectionProfile](class_mip_protectionprofile.md) antes de realizar quaisquer operações de proteção
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
Definições de const públicas & GetSettings() const  |  Obtém as definições utilizadas pelo [ProtectionProfile](class_mip_protectionprofile.md) durante a inicialização e ao longo de seu ciclo de vida.
public void ListEnginesAsync(const std::shared_ptr\<void\>& context)  |  Começa a lista a operação de mecanismos.
public std::vector\<std::string\> ListEngines()  |  Mecanismos de lista.
public void AddEngineAsync(const ProtectionEngine::Settings& settings, const std::shared_ptr\<void\>& context)  |  Inicia a adicionar um novo mecanismo de proteção para o perfil.
público std::shared_ptr\<ProtectionEngine\> AddEngine (const ProtectionEngine::Settings e definições)  |  Adicione um novo mecanismo de proteção para o perfil.
public void DeleteEngineAsync(const std::string& engineId, const std::shared_ptr\<void\>& context)  |  Começa a eliminar o mecanismo de proteção com o ID especificado. Todos os dados para o mecanismo de determinado serão eliminados.
DeleteEngine void pública (const Std:: String & engineId)  |  Eliminar o mecanismo de proteção com o ID especificado. Todos os dados para o mecanismo de determinado serão eliminados.
  
## <a name="members"></a>Membros
  
### <a name="getsettings-function"></a>Função de GetSettings
Obtém as definições utilizadas pelo [ProtectionProfile](class_mip_protectionprofile.md) durante a inicialização e ao longo de seu ciclo de vida.

  
**Devolve**: [As definições](class_mip_protectionprofile_settings.md) utilizada pelo [ProtectionProfile](class_mip_protectionprofile.md) durante a inicialização e ao longo de seu ciclo de vida
  
### <a name="listenginesasync-function"></a>Função de ListEnginesAsync
Começa a lista a operação de mecanismos.

Parâmetros:  
* **context**: Contexto de cliente que irá ser transmitido de forma opaca para observadores


[ProtectionProfile::Observer](class_mip_protectionprofile_observer.md) será chamado após o êxito ou falha.
  
### <a name="listengines-function"></a>Função de ListEngines
Mecanismos de lista.

  
**Devolve**: IDs de motor em cache
  
### <a name="addengineasync-function"></a>Função de AddEngineAsync
Inicia a adicionar um novo mecanismo de proteção para o perfil.

Parâmetros:  
* **as definições**: a [mip::ProtectionEngine::Settings](class_mip_protectionengine_settings.md) objeto que especifica as definições do mecanismo. 


* **context**: Contexto de cliente que irá ser transmitido de forma opaca para observadores


[ProtectionProfile::Observer](class_mip_protectionprofile_observer.md) será chamado após o êxito ou falha.
  
### <a name="addengine-function"></a>Função de AddEngine
Adicione um novo mecanismo de proteção para o perfil.

Parâmetros:  
* **as definições**: a [mip::ProtectionEngine::Settings](class_mip_protectionengine_settings.md) objeto que especifica as definições do mecanismo.



  
**Devolve**: Criado recentemente [ProtectionEngine](class_mip_protectionengine.md)
  
### <a name="deleteengineasync-function"></a>Função de DeleteEngineAsync
Começa a eliminar o mecanismo de proteção com o ID especificado. Todos os dados para o mecanismo de determinado serão eliminados.

Parâmetros:  
* **ID**: o ID exclusivo do motor. 


* **context**: Contexto de cliente que irá ser transmitido de forma opaca para observadores


[ProtectionProfile::Observer](class_mip_protectionprofile_observer.md) será chamado após o êxito ou falha.
  
### <a name="deleteengine-function"></a>Função de DeleteEngine
Eliminar o mecanismo de proteção com o ID especificado. Todos os dados para o mecanismo de determinado serão eliminados.

Parâmetros:  
* **ID**: o ID exclusivo do motor.


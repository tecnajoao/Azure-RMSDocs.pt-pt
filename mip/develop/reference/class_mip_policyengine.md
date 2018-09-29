---
title: classe mip PolicyEngine
description: Referência para a classe mip PolicyEngine
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 57dd325e9c00a3cb2a4056f7ef0b522efef5d0c4
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446044"
---
# <a name="class-mippolicyengine"></a>classe mip::PolicyEngine 
Essa classe fornece uma interface para todas as funções de motor.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 Definições de const públicas & GetSettings() const  |  Obter o mecanismo da diretiva [definições](class_mip_policyengine_settings.md).
Std:: vector const público < std::shared_ptr<Label>> & ListSensitivityLabels()  |  Liste as etiquetas de sensibilidade associadas com o mecanismo da diretiva.
 público const Std:: String & GetMoreInfoUrl() const  |  Forneça um url para buscar mais informações sobre as política/etiquetas.
 bool pública IsLabelingRequired() const  |  Verifica se a política determina que um documento deve ser etiquetado ou não.
público std::shared_ptr<Label> GetDefaultSensitivityLabel()  |  Obtenha a etiqueta de sensibilidade predefinido.
público std::shared_ptr<PolicyHandler> CreatePolicyHandler (const Std:: String & contentIdentifier)  |  Crie um manipulador de política para executar funções relacionadas com a política no estado de execução de um ficheiro.
 SendApplicationAuditEvent void pública (Std:: String const e nível, Std:: String const & eventType, Std:: String const e eventData)  |  Regista um evento específico do aplicativo para o pipeline de auditoria.
  
## <a name="members"></a>Membros
  
### <a name="settings"></a>Definições
Obter o mecanismo da diretiva [definições](class_mip_policyengine_settings.md).

  
**Devolve**: definições de motor de política. 
  
**Consulte também**: [mip::PolicyEngine::Settings](class_mip_policyengine_settings.md)
  
### <a name="label"></a>Etiqueta
Liste as etiquetas de sensibilidade associadas com o mecanismo da diretiva.

  
**Devolve**: uma lista de etiquetas de sensibilidade.
  
### <a name="getmoreinfourl"></a>GetMoreInfoUrl
Forneça um url para buscar mais informações sobre as política/etiquetas.

  
**Devolve**: um url no formato de cadeia de caracteres.
  
### <a name="islabelingrequired"></a>IsLabelingRequired
Verifica se a política determina que um documento deve ser etiquetado ou não.

  
**Devolve**: VERDADEIRO se a etiquetagem é obrigatório, caso contrário FALSO.
  
### <a name="label"></a>Etiqueta
Obtenha a etiqueta de sensibilidade predefinido.

  
**Devolve**: etiqueta de sensibilidade a predefinição se existir, nullptr se não houver nenhum conjunto de etiqueta predefinida.
  
### <a name="policyhandler"></a>PolicyHandler
Crie um manipulador de política para executar funções relacionadas com a política no estado de execução de um ficheiro.

Parâmetros:  
* **contentIdentifier**: um dentifier legível por humanos para o conteúdo. exemplo de um ficheiro: "C:\mip-sdk-for-cpp\files\audit.docx" [caminho] de exemplo para uma mensagem de e-mail: "RE: auditoria design:user1@contoso.com" [assunto: remetente]



  
**Devolve**: o processador de política.
  
### <a name="sendapplicationauditevent"></a>SendApplicationAuditEvent
Regista um evento específico do aplicativo para o pipeline de auditoria.

Parâmetros:  
* **Descrição**: do nível de registo: informações/erro/aviso 


* **eventType**: uma descrição do tipo de evento 


* **eventData**: os dados associados ao evento


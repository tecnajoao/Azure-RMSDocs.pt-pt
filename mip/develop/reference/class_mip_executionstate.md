---
title: classe mip ExecutionState
description: Referência para a classe mip ExecutionState
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 976bca60f3f494a0fbf196e6512b00bdcdd63992
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446316"
---
# <a name="class-mipexecutionstate"></a>classe mip::ExecutionState 
Interface para todos os Estados necessários para executar o motor.
Os clientes só devem chamar os métodos para obter o estado em que é necessária. Por conseguinte, para uma eficiência, clientes talvez queira implementar essa interface, de modo a que o estado correspondente é calculado dinamicamente em vez de computar com antecedência.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 público Std:: String GetNewLabelId() const  |  Obtém o ID de etiqueta de sensibilidade que deve ser aplicado no documento.
 público GetNewLabelActionSource() de ActionSource const  |  Obtém a origem para uma nova ação de etiqueta.
 público Std:: String GetContentIdentifier() const  |  Obtém o identificador de conteúdo que descreve o documento. exemplo de um ficheiro: exemplo de [caminho] para uma mensagem de e-mail: [assunto: remetente].
 público GetContentState() de ContentState const  |  Obtém o estado do conteúdo enquanto a aplicação está a interagir com ele.
std::pair público < bool, Std:: String > IsDowngradeJustified() const  |  Implementação deve passar se foi indicada justificação para alterar uma etiqueta existente.
 público GetNewLabelAssignmentMethod() de AssignmentMethod const  |  Obtenha o método de atribuição a nova etiqueta.
público Std:: vector < std::pair < Std:: String, Std:: String >> GetNewLabelExtendedProperties() const  |  Devolva propriedades expandidas da nova etiqueta.
público Std:: vector < std::pair < Std:: String, Std:: String >> GetContentMetadata (const Std:: vector < Std:: String > e nomes de contas, const Std:: vector < Std:: String > e namePrefixes) const  |  Obter os itens de metadados do conteúdo.
público std::shared_ptr<ProtectionDescriptor> GetProtectionDescriptor() const  |  Obter o descritor de proteção.
 público GetContentFormat() de ContentFormat const  |  Obtém o formato de conteúdo.
 público GetSupportedActions() de ActionType const  |  Obtém um enum mascarado, que descreve todos os tipos de ação suportados.
público std::map virtual < Std:: String, std::shared_ptr<ClassificationResult>> GetClassificationResults (Std:: vector const < Std:: String > &) const  |  Devolva um mapa dos resultados de classificação.
  
## <a name="members"></a>Membros
  
### <a name="getnewlabelid"></a>GetNewLabelId
Obtém o ID de etiqueta de sensibilidade que deve ser aplicado no documento.

  
**Devolve**: ID de etiqueta de sensibilidade a ser aplicado para o conteúdo se existe outro vazia de forma remover etiqueta.
  
### <a name="getnewlabelactionsource"></a>GetNewLabelActionSource
Obtém a origem para uma nova ação de etiqueta.

  
**Devolve**: origem de ação.
  
### <a name="getcontentidentifier"></a>GetContentIdentifier
Obtém o identificador de conteúdo que descreve o documento. exemplo de um ficheiro: exemplo de [caminho] para uma mensagem de e-mail: [assunto: remetente].

  
**Devolve**: identificador de conteúdo a ser aplicado ao conteúdo.
Este valor é utilizado ao auditar como uma descrição legível do conteúdo
  
### <a name="getcontentstate"></a>GetContentState
Obtém o estado do conteúdo enquanto a aplicação está a interagir com ele.

  
**Devolve**: estado dos dados do conteúdo
  
### <a name="isdowngradejustified"></a>IsDowngradeJustified
Implementação deve passar se foi indicada justificação para alterar uma etiqueta existente.

  
**Devolve**: VERDADEIRO se a mudança para versão anterior é justifiedalong com false de messageelse justificação 
  
**Consulte também**: [mip::JustifyAction](class_mip_justifyaction.md)
  
### <a name="getnewlabelassignmentmethod"></a>GetNewLabelAssignmentMethod
Obtenha o método de atribuição a nova etiqueta.

  
**Devolve**: O método de atribuição STANDARD, PRIVILEGIADO, AUTOMATICAMENTE. 
  
**Consulte também**: mip::AssignmentMethod
  
### <a name="getnewlabelextendedproperties"></a>GetNewLabelExtendedProperties
Devolva propriedades expandidas da nova etiqueta.

  
**Devolve**: as propriedades expandidas aplicadas ao conteúdo.
  
### <a name="getcontentmetadata"></a>GetContentMetadata
Obter os itens de metadados do conteúdo.

  
**Devolve**: os metadados aplicado ao conteúdo. Cada item de metadados é um par de nome e valor.
  
### <a name="protectiondescriptor"></a>ProtectionDescriptor
Obter o descritor de proteção.

  
**Devolve**: O descritor de proteção
  
### <a name="getcontentformat"></a>GetContentFormat
Obtém o formato de conteúdo.

  
**Devolve**: predefinido, o E-Mail 
  
**Consulte também**: mip::ContentFormat
  
### <a name="actiontype"></a>ActionType
Obtém um enum mascarado, que descreve todos os tipos de ação suportados.

  
**Devolve**: um enum mascarado, que descreve todos os tipos de ação suportados.
ActionType::Justify têm de ser suportadas. Quando uma alteração de política e a etiqueta requer uma justificação, uma ação de justificação sempre será retornada.
  
### <a name="classificationresult"></a>ClassificationResult
Devolva um mapa dos resultados de classificação.

Parâmetros:  
* **classificationId**: uma lista de IDs de classificação. 



  
**Devolve**: uma lista de resultados de classificação.
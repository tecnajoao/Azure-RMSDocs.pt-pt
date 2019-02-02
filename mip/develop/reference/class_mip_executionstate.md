---
title: classe mip::ExecutionState
description: Documenta a classe mip::executionstate da Microsoft Information Protection (MIP) SDK.
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: 86f06a8fab5600f0bc72f60272864a2ce2fab15e
ms.sourcegitcommit: be05adc7750e22c110b261882de0389b9dfb2726
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/02/2019
ms.locfileid: "55650719"
---
# <a name="class-mipexecutionstate"></a>classe mip::ExecutionState 
Interface para todos os Estados necessários para executar o motor.
Os clientes só devem chamar os métodos para obter o estado em que é necessária. Por conseguinte, para uma eficiência, clientes talvez queira implementar essa interface, de modo a que o estado correspondente é calculado dinamicamente em vez de computar com antecedência.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
public std::string GetNewLabelId() const  |  Obtém o ID de etiqueta de sensibilidade que deve ser aplicado no documento.
público GetNewLabelActionSource() de ActionSource const  |  Obtém a origem para uma nova ação de etiqueta.
public std::string GetContentIdentifier() const  |  Obtém o identificador de conteúdo que descreve o documento. exemplo de um ficheiro: [path\filename] de exemplo para uma mensagem de e-mail: [assunto: remetente].
público GetContentState() de ContentState const  |  Obtém o estado do conteúdo enquanto a aplicação está a interagir com ele.
public std::pair\<bool, std::string\> IsDowngradeJustified() const  |  Implementação deve passar se foi indicada justificação para alterar uma etiqueta existente.
público GetNewLabelAssignmentMethod() de AssignmentMethod const  |  Obtenha o método de atribuição a nova etiqueta.
public std::vector\<std::pair\<std::string, std::string\>\> GetNewLabelExtendedProperties() const  |  Devolva propriedades expandidas da nova etiqueta.
public std::vector\<std::pair\<std::string, std::string\>\> GetContentMetadata(const std::vector\<std::string\>& names, const std::vector\<std::string\>& namePrefixes) const  |  Obter os itens de metadados do conteúdo.
público std::shared_ptr\<ProtectionDescriptor\> GetProtectionDescriptor() const  |  Obter o descritor de proteção.
public ContentFormat GetContentFormat() const  |  Obtém o formato de conteúdo.
público GetSupportedActions() de ActionType const  |  Obtém um enum mascarado, que descreve todos os tipos de ação suportados.
std::map virtual pública\<Std:: String, std::shared_ptr\<ClassificationResult\> \> GetClassificationResults (Std:: vector const\<std::shared_ptr\< ClassificationRequest\> \> &) const  |  Devolva um mapa dos resultados de classificação.
public virtual std::map\<std::string, std::string\> GetAuditMetadata() const  |  Devolva um mapa de pares de chave-valor de auditoria específicos de aplicativo.
  
## <a name="members"></a>Membros
  
### <a name="getnewlabelid-function"></a>Função de GetNewLabelId
Obtém o ID de etiqueta de sensibilidade que deve ser aplicado no documento.

  
**Devolve**: ID de etiqueta de sensibilidade para ser aplicada ao conteúdo se existe outro vazia de forma remover etiqueta.
  
### <a name="getnewlabelactionsource-function"></a>Função de GetNewLabelActionSource
Obtém a origem para uma nova ação de etiqueta.

  
**Devolve**: Origem da ação.
  
### <a name="getcontentidentifier-function"></a>Função de GetContentIdentifier
Obtém o identificador de conteúdo que descreve o documento. exemplo de um ficheiro: [path\filename] de exemplo para uma mensagem de e-mail: [assunto: remetente].

  
**Devolve**: Identificador de conteúdo a ser aplicado ao conteúdo.
Este valor é utilizado ao auditar como uma descrição legível do conteúdo
  
### <a name="getcontentstate-function"></a>Função de GetContentState
Obtém o estado do conteúdo enquanto a aplicação está a interagir com ele.

  
**Devolve**: Estado dos dados do conteúdo
  
### <a name="isdowngradejustified-function"></a>Função de IsDowngradeJustified
Implementação deve passar se foi indicada justificação para alterar uma etiqueta existente.

  
**Devolve**: VERDADEIRO se a mudança para versão anterior é justifiedalong com false de messageelse justificação 
  
**Consulte também**: [mip::JustifyAction](class_mip_justifyaction.md)
  
### <a name="getnewlabelassignmentmethod-function"></a>Função de GetNewLabelAssignmentMethod
Obtenha o método de atribuição a nova etiqueta.

  
**Devolve**: O método de atribuição STANDARD, PRIVILEGIADO, AUTOMATICAMENTE. 
  
**Consulte também**: [mip::AssignmentMethod](mip-enums-and-structs.md#assignmentmethod-enum)
  
### <a name="getnewlabelextendedproperties-function"></a>Função de GetNewLabelExtendedProperties
Devolva propriedades expandidas da nova etiqueta.

  
**Devolve**: As propriedades expandidas aplicadas ao conteúdo.
  
### <a name="getcontentmetadata-function"></a>Função de GetContentMetadata
Obter os itens de metadados do conteúdo.

  
**Devolve**: Os metadados aplicado ao conteúdo. Cada item de metadados é um par de nome e valor.
  
### <a name="getprotectiondescriptor-function"></a>Função de GetProtectionDescriptor
Obter o descritor de proteção.

  
**Devolve**: O descritor de proteção
  
### <a name="getcontentformat-function"></a>Função de GetContentFormat
Obtém o formato de conteúdo.

  
**Devolve**: PREDEFINIÇÃO, O E-MAIL 
  
**Consulte também**: [mip::ContentFormat](mip-enums-and-structs.md#contentformat-enum)
  
### <a name="getsupportedactions-function"></a>Função de GetSupportedActions
Obtém um enum mascarado, que descreve todos os tipos de ação suportados.

  
**Devolve**: Um enum mascarado, que descreve todos os tipos de ação suportados.
ActionType::Justify têm de ser suportadas. Quando uma alteração de política e a etiqueta requer uma justificação, uma ação de justificação sempre será retornada.
  
### <a name="getclassificationresults-function"></a>Função de GetClassificationResults
Devolva um mapa dos resultados de classificação.

Parâmetros:  
* **classificationId**: uma lista de IDs de classificação. 



  
**Devolve**: Uma lista de resultados de classificação.
  
### <a name="getauditmetadata-function"></a>Função de GetAuditMetadata
Devolva um mapa de pares de chave-valor de auditoria específicos de aplicativo.

  
**Devolve**: Uma lista de pares de chave: valor registado de metadados do aplicativo específico de auditoria remetente: Id de e-mail para o remetente de destinatários: Representa uma matriz JSON de destinatários para um e-mail LastModifiedBy: Id de e-mail para o utilizador que o conteúdo LastModifiedDate da última modificação: Data que o conteúdo foi modificado pela última vez.
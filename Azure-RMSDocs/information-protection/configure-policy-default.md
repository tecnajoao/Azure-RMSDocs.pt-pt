---
title: "Política do Azure Information Protection predefinida | Azure Rights Management"
description: 
author: cabailey
manager: mbaldwin
ms.date: 07/21/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 671281c8-f0d1-42b6-aae3-681d1821e2cf
translationtype: Human Translation
ms.sourcegitcommit: 93444affe94b280db2c9e4e2960c6902e491dec6
ms.openlocfilehash: 977cbf2f45cab75aaca9c2a16dd1564c2af2fe4a


---

# Política do Azure Information Protection predefinida

>*Aplica-se a: pré-visualização do Azure Information Protection*

**[Estas informações são preliminares e estão sujeitas a alterações. ]**

Utilize as seguintes informações para compreender a forma como a política predefinida para a proteção de informações do Azure está configurada. Se modificar a política predefinida, pode referenciar estes valores para voltar à política predefinida.

## Barra Information Protection

Título: **confidencialidade**

Descrição: **a confidencialidade de informação consiste em quatro níveis diferente (Público, Interno, Confidencial, Secreto), permitindo que o utilizador identifique o risco de exposição das informações para utilizadores não autorizados dentro ou fora da empresa.**


## Etiquetas

Existem 5 etiquetas predefinidas que tem as seguintes definições:

### **Pessoal**

Descrição: **apenas para utilização pessoal. Estes dados não serão monitorizados pela organização. As informações pessoais não podem incluir quaisquer dados relacionados com a empresa.**

Cor: verde claro

Marcas visuais: nenhuma

Condições: nenhuma

Proteção: não

----


### **Público**

Descrição: **Esta informação é interna e pode ser utilizada por todas as pessoas dentro ou fora da empresa.**

Cor: verde

Marcas visuais: nenhuma

Condições: nenhuma

Proteção: não

----

### **Interna**

Descrição: **estas informações incluem um largo espetro de dados de negócios internos que podem ser utilizados por todos os funcionários e que podem ser partilhados com clientes autorizados e parceiros de negócios. Exemplos de informações internas são as políticas da empresa e a maior parte das comunicações internas.**

Cor: azul

Marcas de Visual: rodapé (documentos e e-mails)

Condições: nenhuma

Proteção: não

----

### **Confidencial**

Descrição: **estes dados incluem informações empresariais confidenciais. A exposição estes dados a utilizadores não autorizados pode causar danos na organização. Exemplos de informações confidenciais são as informações dos funcionários, projetos de cliente individuais ou contratos e dados de contas de vendas.**

Cor: cor-de-laranja

Marcas de Visual: rodapé (documentos e e-mails)

Condições: nenhuma

Proteção: não

----

### **Secreto**

Descrição: **estes dados incluem informações altamente confidenciais para as empresas e têm de ser protegidas. A exposição de dados Secretos a utilizadores não autorizados pode causar graves danos na organização. Exemplos de informações secretas são informações de identificação pessoal, registos de clientes, código de origem e relatórios financeiros previamente anunciados.**

Cor: vermelho

Marcas de Visual: rodapé (documentos e e-mails)

Condições: nenhuma

Proteção: não

----


## Etiquetas secundárias

Existem 2 etiquetas secundárias predefinidas que tem as seguintes definições:

### Secreto > **Toda a Empresa**

Descrição: **estes dados incluem informações empresariais confidenciais - permitidas para todos os empregados da empresa.**

Marcas visuais: nenhuma

Condições: nenhuma

Proteção: não

----

### Secreto > **Grupo**

Descrição: **estes dados incluem informações empresariais confidenciais - permitidas apenas a grupos de colaboradores.**

Marcas visuais: nenhuma

Condições: nenhuma

Proteção: não

## Definições globais

**Todos os documentos e e-mails devem ter uma etiqueta (aplicada automaticamente ou pelos utilizadores)**: desligado

**Selecione a etiqueta predefinida**: nenhuma

**Os utilizadores têm de fornecer justificação quando reduzirem o nível de sensibilidade (por exemplo, de Confidencial a Público)**: desativado

## Passos seguintes

Para mais informações sobre como configurar a política do Azure Information Protection, utilize as ligações na secção [Configurar política da organização](configure-policy.md#configuring-your-organization-s-policy). 



<!--HONumber=Jul16_HO5-->



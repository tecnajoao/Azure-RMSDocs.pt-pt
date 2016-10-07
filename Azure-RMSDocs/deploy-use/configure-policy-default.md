---
title: "Política predefinida | Azure Information Protection"
description: "Conheça a forma como a política predefinida do Azure Information Protection está configurada. Se modificar a política predefinida, pode referenciar estes valores para voltar à política predefinida."
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 671281c8-f0d1-42b6-aae3-681d1821e2cf
translationtype: Human Translation
ms.sourcegitcommit: 2fd29eb6dec94535d0358fe0a2d9c9285fcd7cd1
ms.openlocfilehash: 531d7a474daeea752fc8cd63b8b39e9fec373a24


---

# Política do Azure Information Protection predefinida

>*Aplica-se a: Azure Information Protection*

Utilize as seguintes informações para compreender a forma como a política predefinida para a proteção de informações do Azure está configurada. Se modificar a política predefinida, pode referenciar estes valores para voltar à política predefinida.

## Barra Information Protection

|Definição|Valor|
|-------------------------------|---------------------------|
|Título|Sensibilidade|
|Descrição|A confidencialidade das informações consiste em quatro níveis diferente (Público, Interno, Confidencial, Secreto), permitindo que o utilizador identifique o risco de exposição das informações para utilizadores não autorizados dentro ou fora da empresa.|

## Etiquetas

|Etiqueta|Descrição|Definições|
|-------------------------------|---------------------------|-----------------|
|Pessoal|Apenas para utilização pessoal. Estes dados não serão monitorizados pela organização. As informações pessoais não podem incluir quaisquer dados relacionados com a empresa.|**Ativado**: ligado <br /><br />**Cor**: verde claro<br /><br />**Marcas visuais**: desligado <br /><br />**Condições**: nenhuma<br /><br />**Proteção**: nenhuma|
|Público|Estas informações são internas e podem ser utilizadas por todas as pessoas dentro ou fora da empresa.|**Ativado**: ligado <br /><br />**Cor**: verde<br /><br />**Marcas visuais**: desligado<br /><br />**Condições**: nenhuma<br /><br />**Proteção**: nenhuma|
|Interna|Estas informações incluem um largo espetro de dados de negócios internos que podem ser utilizados por todos os empregados e que podem ser partilhados com clientes autorizados e parceiros de negócios. Exemplos de informações internas são as políticas da empresa e a maior parte das comunicações internas.|**Ativado**: ligado <br /><br />**Cor**: azul <br /><br />**Marcas visuais**: rodapé (documentos e e-mails)<br /><br />**Condições**: nenhuma<br /><br />**Proteção**: nenhuma|
|Confidencial|Estes dados incluem informações empresariais confidenciais. A exposição estes dados a utilizadores não autorizados pode causar danos na organização. Exemplos de informações confidenciais são as informações dos empregados, projetos de clientes individuais ou contratos e dados de contas de vendas.|**Ativado**: ligado <br /><br />**Cor**: laranja<br /><br />**Marcas visuais**: rodapé (documentos e e-mails)<br /><br />**Condições**: nenhuma<br /><br />**Proteção**: nenhuma|
|Secreto|Estes dados incluem informações altamente confidenciais para as empresas e têm de ser protegidas. A exposição de dados Secretos a utilizadores não autorizados pode causar graves danos na organização. Exemplos de informações secretas são informações de identificação pessoal, registos de clientes, código de origem e relatórios financeiros previamente anunciados.|**Ativado**: ligado <br /><br />**Cor**: vermelho<br /><br />**Marcas visuais**: rodapé (documentos e e-mails)<br /><br />**Condições**: nenhuma<br /><br />**Proteção**: nenhuma|

## Etiquetas secundárias

|Etiqueta|Descrição|Definições|
|-------------------------------|---------------------------|-----------------|
|Secreto \ Toda a Empresa|Estes dados incluem informações empresariais confidenciais, permitidas para todos os empregados da empresa.|**Ativado**: ligado <br /><br />**Marcas visuais**: desligado<br /><br />**Condições**: nenhuma<br /><br />**Proteção**: nenhuma|
|Secreto \ Os Meus Grupos|Estes dados incluem informações empresariais confidenciais, permitidas apenas para grupos de empregados.|**Ativado**: ligado <br /><br />**Marcas visuais**: desligado<br /><br />**Condições**: nenhuma<br /><br />**Proteção**: nenhuma|

## Definições globais

|Definição|Valor|
|-------------------------------|---------------------------|
|Todos os documentos e e-mails devem ter uma etiqueta (aplicada automaticamente ou pelos utilizadores)|Desativada|
|Selecione a etiqueta predefinida|Nenhum|
|Os utilizadores têm de fornecer uma justificação para poderem definir uma etiqueta de classificação inferior e remover uma etiqueta ou proteção|Desativada|


## Passos seguintes

Para mais informações sobre como configurar a política do Azure Information Protection, utilize as ligações na secção [Configurar política da organização](configure-policy.md#configuring-your-organization-s-policy). 



<!--HONumber=Sep16_HO4-->



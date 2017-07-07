---
title: "A política predefinida do Azure Information Protection"
description: "Conheça a forma como a política predefinida do Azure Information Protection está configurada. Se modificar a política predefinida, pode referenciar estes valores para voltar à política predefinida."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/25/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 671281c8-f0d1-42b6-aae3-681d1821e2cf
ms.openlocfilehash: decc5e3462a80e307201933e634c3ecfa03ee074
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/30/2017
---
# <a name="the-default-azure-information-protection-policy"></a>Política do Azure Information Protection predefinida

>*Aplica-se a: Azure Information Protection*

Utilize as seguintes informações para compreender a forma como a política predefinida para o Azure Information Protection está configurada.

Quando um administrador se liga, pela primeira vez, ao serviço Azure Information Protection através do portal do Azure, é criada uma política predefinida para esse inquilino. Ocasionalmente, a Microsoft pode efetuar alterações à política predefinida. No entanto, se já estiver a utilizar o serviço antes de a política predefinida ser revista, a versão anterior da mesma não será atualizada porque poderá tê-la configurado e implementado na produção.

Pode usar os seguintes valores como referência para voltar à política predefinida ou atualizar a política para os valores mais recentes.

## <a name="current-default-policy"></a>Política predefinida atual

Esta versão da política predefinida é de 21 de março de 2017.

Tenha em atenção que as descrições nesta política se referem aos dados que necessitam de proteção, bem como à monitorização e revogação dos mesmos. A política não configura esta proteção para estas etiquetas, por isso tem de efetuar passos adicionais para cumprir esta descrição. Por exemplo, configure a etiqueta para aplicar a proteção do Azure RMS ou utilize uma solução DLP (proteção contra a perda de dados). Para poder monitorizar e revogar um documento através do site de controlo de documentos, o documento tem de estar protegido pelo Azure RMS. 


### <a name="labels"></a>Etiquetas

|Etiqueta|Descrição|Definições|
|-------------------------------|---------------------------|-----------------|
|Pessoal|Dados não empresariais, apenas para utilização pessoal.|**Ativado**: ligado <br /><br />**Cor**: verde claro<br /><br />**Marcas visuais**: desligado <br /><br />**Condições**: nenhuma<br /><br />**Proteção**: nenhuma|
|Público|Dados empresariais que são especialmente preparados e aprovados para o consumo público.|**Ativado**: ligado <br /><br />**Cor**: verde<br /><br />**Marcas visuais**: desligado<br /><br />**Condições**: nenhuma<br /><br />**Proteção**: nenhuma|
|Geral|Dados empresariais que não se destinam ao consumo público. No entanto, estes dados podem ser partilhados com parceiros externos, conforme necessário. Os exemplos incluem um diretório de telefone interno da empresa, organogramas, padrões internos e a maioria da comunicação interna.|**Ativado**: ligado <br /><br />**Cor**: azul <br /><br />**Marcas visuais**: desligado<br /><br />**Condições**: nenhuma<br /><br />**Proteção**: nenhuma|
|Confidencial|Dados empresariais confidenciais que podiam causar danos à empresa se fossem partilhados com pessoas não autorizadas. Os exemplos incluem contratos, relatórios de segurança, resumos de previsões e dados de conta de vendas.|**Ativado**: ligado <br /><br />**Cor**: laranja<br /><br />**Marcas visuais**: desligado<br /><br />**Condições**: nenhuma<br /><br />**Proteção**: nenhuma|
|Altamente Confidencial|Dados empresariais altamente confidenciais que iriam causar danos à empresa se fossem partilhados com pessoas não autorizadas. Os exemplos incluem informações dos funcionários e clientes, palavras-passe, código de origem e relatórios financeiros previamente anunciados.|**Ativado**: ligado <br /><br />**Cor**: vermelho<br /><br />**Marcas visuais**: desligado<br /><br />**Condições**: nenhuma<br /><br />**Proteção**: nenhuma|


### <a name="sub-labels"></a>Etiquetas secundárias

|Etiqueta|Descrição|Definições|
|-------------------------------|---------------------------|-----------------|
|Confidencial\Todos os Funcionários|Dados confidenciais que necessitam de proteção, o que permite que todos os funcionários tenham todas as permissões. Os proprietários de dados podem monitorizar e revogar os conteúdos.|**Ativado**: ligado <br /><br />**Marcas visuais**: rodapé (documentos e e-mails)<br /><br />Classificado como Confidencial<br /><br />**Condições**: nenhuma<br /><br />**Proteção**: nenhuma|
|Confidencial\Todos (não protegidos)|Dados que não necessitam de proteção. Utilize esta opção com cuidado e com uma justificação comercial adequada.|**Ativado**: ligado <br /><br />**Marcas visuais**: rodapé (documentos e e-mails)<br /><br />Classificado como Confidencial <br /><br />**Condições**: nenhuma<br /><br />**Proteção**: nenhuma|
|Altamente Confidencial\Todos os Funcionários|Dados altamente confidenciais que fornecem a todos os funcionários permissões de visualização, edição e resposta para estes conteúdos. Os proprietários de dados podem monitorizar e revogar os conteúdos.|**Ativado**: ligado <br /><br />**Marcas visuais**: rodapé (documentos e e-mails)<br /><br />Classificado como Altamente Confidencial<br /><br />**Condições**: nenhuma<br /><br />**Proteção**: nenhuma|
|Altamente Confidencial\Todos (não protegidos)|Dados que não necessitam de proteção. Utilize esta opção com cuidado e com uma justificação comercial adequada.|**Ativado**: ligado <br /><br />**Marcas visuais**: rodapé (documentos e e-mails)<br /><br />Classificado como Altamente Confidencial<br /><br />**Condições**: nenhuma<br /><br />**Proteção**: nenhuma|

### <a name="information-protection-bar"></a>Barra Information Protection

|Definição|Valor|
|-------------------------------|---------------------------|
|Título|Sensibilidade|
|Descrição|A etiqueta atual para estes conteúdos. Esta definição identifica o risco para a empresa se estes conteúdos forem partilhados com pessoas não autorizadas dentro ou fora da organização.|


### <a name="settings"></a>Definições

|Definição|Valor|
|-------------------------------|---------------------------|
|Todos os documentos e e-mails devem ter uma etiqueta (aplicada automaticamente ou pelos utilizadores)|Desativada|
|Selecione a etiqueta predefinida|Nenhum|
|Os utilizadores têm de fornecer uma justificação para poderem definir uma etiqueta de classificação inferior e remover uma etiqueta ou proteção|Desativada|
|Para mensagens de e-mail com anexos, aplique uma etiqueta que corresponda à classificação mais elevada dos mesmos|Desativada|
|Fornecer um URL personalizado para a página Web "Mais informações" do cliente do Azure Information Protection|Em Branco|

## <a name="default-policy-before-march-21-2017"></a>Política predefinida antes de 21 de março de 2017

### <a name="labels"></a>Etiquetas

|Etiqueta|Descrição|Definições|
|-------------------------------|---------------------------|-----------------|
|Pessoal|Apenas para utilização pessoal. Estes dados não serão monitorizados pela organização. As informações pessoais não podem incluir quaisquer dados relacionados com a empresa.|**Ativado**: ligado <br /><br />**Cor**: verde claro<br /><br />**Marcas visuais**: desligado <br /><br />**Condições**: nenhuma<br /><br />**Proteção**: nenhuma|
|Público|Estas informações são internas e podem ser utilizadas por todas as pessoas dentro ou fora da empresa.|**Ativado**: ligado <br /><br />**Cor**: verde<br /><br />**Marcas visuais**: desligado<br /><br />**Condições**: nenhuma<br /><br />**Proteção**: nenhuma|
|Interna|Estas informações incluem um largo espetro de dados empresariais internos que podem ser utilizados por todos os empregados e que podem ser partilhados com clientes autorizados e parceiros de negócios. Exemplos de informações internas são as políticas da empresa e a maior parte das comunicações internas.|**Ativado**: ligado <br /><br />**Cor**: azul <br /><br />**Marcas visuais**: rodapé (documentos e e-mails): <br /><br />Sensibilidade: interno<br /><br />**Condições**: nenhuma<br /><br />**Proteção**: nenhuma|
|Confidencial|Estes dados incluem informações empresariais confidenciais. A exposição estes dados a utilizadores não autorizados pode causar danos na organização. Exemplos de informações confidenciais são as informações dos empregados, projetos de clientes individuais ou contratos e dados de contas de vendas.|**Ativado**: ligado <br /><br />**Cor**: laranja<br /><br />**Marcas visuais**: rodapé (documentos e e-mails):<br /><br /> Sensibilidade: confidencial<br /><br />**Condições**: nenhuma<br /><br />**Proteção**: nenhuma|
|Secreto|Estes dados incluem informações altamente confidenciais para as empresas e têm de ser protegidas. A exposição de dados Secretos a utilizadores não autorizados pode causar graves danos na organização. Exemplos de informações secretas são informações de identificação pessoal, registos de clientes, código de origem e relatórios financeiros previamente anunciados.|**Ativado**: ligado <br /><br />**Cor**: vermelho<br /><br />**Marcas visuais**: rodapé (documentos e e-mails):<br /><br /> Sensibilidade: secreto<br /><br />**Condições**: nenhuma<br /><br />**Proteção**: nenhuma|


### <a name="sub-labels"></a>Etiquetas secundárias

|Etiqueta|Descrição|Definições|
|-------------------------------|---------------------------|-----------------|
|Secreto\Toda a Empresa|Estes dados incluem informações empresariais confidenciais, permitidas para todos os empregados da empresa.|**Ativado**: ligado <br /><br />**Marcas visuais**: desligado<br /><br />**Condições**: nenhuma<br /><br />**Proteção**: nenhuma|
|Secreto\Os Meus Grupos|Estes dados incluem informações empresariais confidenciais, permitidas apenas para grupos de empregados.|**Ativado**: ligado <br /><br />**Marcas visuais**: desligado<br /><br />**Condições**: nenhuma<br /><br />**Proteção**: nenhuma|

### <a name="information-protection-bar"></a>Barra Information Protection

|Definição|Valor|
|-------------------------------|---------------------------|
|Título|Sensibilidade|
|Descrição|A confidencialidade das informações consiste em quatro níveis diferente (Público, Interno, Confidencial, Secreto), permitindo que o utilizador identifique o risco de exposição das informações para utilizadores não autorizados dentro ou fora da empresa.|


### <a name="settings"></a>Definições

|Definição|Valor|
|-------------------------------|---------------------------|
|Todos os documentos e e-mails devem ter uma etiqueta (aplicada automaticamente ou pelos utilizadores)|Desativada|
|Selecione a etiqueta predefinida|Nenhum|
|Os utilizadores têm de fornecer uma justificação para poderem definir uma etiqueta de classificação inferior e remover uma etiqueta ou proteção|Desativada|
|Fornecer um URL personalizado para a página Web "Mais informações" do cliente do Azure Information Protection|Em Branco|


## <a name="next-steps"></a>Próximos passos

Para mais informações sobre como configurar a política do Azure Information Protection, utilize as ligações na secção [Configurar política da organização](configure-policy.md#configuring-your-organizations-policy). 

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
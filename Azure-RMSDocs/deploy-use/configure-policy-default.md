---
title: "A política predefinida do Azure Information Protection"
description: "Conheça a forma como a política predefinida do Azure Information Protection está configurada. Se modificar a política predefinida, pode referenciar estes valores para voltar à política predefinida."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/21/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 671281c8-f0d1-42b6-aae3-681d1821e2cf
ms.openlocfilehash: da8557be0a70cee0e7a207a8ed285f6e843ac626
ms.sourcegitcommit: 67750454f8fa86d12772a0075a1d01a69f167bcb
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/23/2018
---
# <a name="the-default-azure-information-protection-policy"></a>Política do Azure Information Protection predefinida

>*Aplica-se a: Azure Information Protection*

Utilize as seguintes informações para compreender a forma como a política predefinida para o Azure Information Protection está configurada.

Quando um administrador se liga, pela primeira vez, ao serviço Azure Information Protection através do portal do Azure, é criada uma política predefinida para esse inquilino. Ocasionalmente, a Microsoft pode efetuar alterações à política predefinida. No entanto, se já estiver a utilizar o serviço antes de a política predefinida ser revista, a versão anterior da mesma não será atualizada porque poderá tê-la configurado e implementado na produção.

Pode usar os seguintes valores como referência para voltar à política predefinida ou atualizar a política para os valores mais recentes.

## <a name="current-default-policy"></a>Política predefinida atual

Esta versão da política predefinida é de 31 de Julho de 2017.

Esta política predefinida é criada apenas se o serviço Azure Rights Management foi [ativado](activate-service.md) quando a política foi criada. Se este serviço não foi ativado, a política predefinida não configurar a proteção para os sublabels seguintes:

- **Confidencial\Todos os Funcionários**

- **Confidencial \ destinatários apenas**

- **Altamente Confidencial\Todos os Funcionários** 

- **Altamente confidenciais \ destinatários apenas** 

Quando estes sublabels não são automaticamente configuradas para proteção, a política predefinida permanece o mesmo que o [anterior política predefinida](#default-policy-before-july-31-2017).

Quando a proteção é aplicada para a **todos os funcionários** sublabels, a proteção é configurada utilizando os modelos predefinidos que são automaticamente convertidos para etiquetas no portal do Azure. Para obter mais informações sobre estes modelos, consulte [configurar e gerir modelos do Azure Information Protection](configure-policy-templates.md).

A partir de 30 de Agosto de 2017, esta versão da política predefinida inclui multilingues versões dos nomes de etiqueta e descrições. 

#### <a name="more-information-about-the-recipients-only-sublabel"></a>Obter mais informações sobre o sublabel apenas os destinatários

Os utilizadores veem apenas esta etiqueta no Outlook. Se não vir esta etiqueta no Word, Excel, PowerPoint ou do Explorador de ficheiros. 

Quando os utilizadores selecionarem esta etiqueta, a Outlook opção não reencaminhar é aplicada automaticamente a mensagem de correio eletrónico. Os destinatários que os utilizadores especifiquem não é possível reencaminhar o e-mail e não é possível copiar ou imprimir os conteúdos ou guarde os anexos.


### <a name="labels"></a>Etiquetas

|Etiqueta|Descrição|Definições|
|-------------------------------|---------------------------|-----------------|
|Pessoal|Dados não empresariais, apenas para utilização pessoal.|**Ativado**: ligado <br /><br />**Cor**: verde claro<br /><br />**Marcas visuais**: desligado <br /><br />**Condições**: nenhuma<br /><br />**Proteção**: nenhuma|
|Público|Dados empresariais que são especialmente preparados e aprovados para o consumo público.|**Ativado**: ligado <br /><br />**Cor**: verde<br /><br />**Marcas visuais**: desligado<br /><br />**Condições**: nenhuma<br /><br />**Proteção**: nenhuma|
|Geral|Dados empresariais que não se destinam ao consumo público. No entanto, estes dados podem ser partilhados com parceiros externos, conforme necessário. Os exemplos incluem um diretório de telefone interno da empresa, organogramas, padrões internos e a maioria da comunicação interna.|**Ativado**: ligado <br /><br />**Cor**: azul <br /><br />**Marcas visuais**: desligado<br /><br />**Condições**: nenhuma<br /><br />**Proteção**: nenhuma|
|Confidencial|Dados empresariais confidenciais que podiam causar danos à empresa se fossem partilhados com pessoas não autorizadas. Os exemplos incluem contratos, relatórios de segurança, resumos de previsões e dados de conta de vendas.|**Ativado**: ligado <br /><br />**Cor**: laranja<br /><br />**Marcas visuais**: desligado<br /><br />**Condições**: nenhuma<br /><br />**Proteção**: nenhuma|
|Altamente Confidencial|Dados empresariais altamente confidenciais que iriam causar danos à empresa se fossem partilhados com pessoas não autorizadas. Os exemplos incluem informações dos funcionários e clientes, palavras-passe, código de origem e relatórios financeiros previamente anunciados.|**Ativado**: ligado <br /><br />**Cor**: vermelho<br /><br />**Marcas visuais**: desligado<br /><br />**Condições**: nenhuma<br /><br />**Proteção**: nenhuma|


### <a name="sublabels"></a>Sublabels

|Etiqueta|Descrição|Definições|
|-------------------------------|---------------------------|-----------------|
|Confidencial\Todos os Funcionários|Dados confidenciais que necessitam de proteção, o que permite que todos os funcionários tenham todas as permissões. Os proprietários de dados podem monitorizar e revogar os conteúdos.|**Ativado**: ligado <br /><br />**Marcas visuais**: rodapé (documentos e e-mails)<br /><br />Classificado como Confidencial<br /><br />**Condições**: nenhuma<br /><br />**Proteção**: Azure (chave de nuvem) [[1]](#footnote-1)|
|Confidencial\Todos (não protegidos)|Dados que não necessitam de proteção. Utilize esta opção com cuidado e com uma justificação comercial adequada.|**Ativado**: ligado <br /><br />**Marcas visuais**: rodapé (documentos e e-mails)<br /><br />Classificado como Confidencial <br /><br />**Condições**: nenhuma<br /><br />**Proteção**: nenhuma|
|Confidencial \ destinatários apenas|Dados confidenciais que requer a proteção e que podem ser visualizados, apenas os destinatários.|**Ativado**: ligado <br /><br />**Marcas visuais**: rodapé (e-mail)<br /><br />Classificado como Confidencial <br /><br />**Condições**: nenhuma<br /><br />**Proteção**: defina definidas pelo utilizador as permissões (pré-visualização), no Outlook aplicam não reencaminhar|
|Altamente Confidencial\Todos os Funcionários|Dados altamente confidenciais que fornecem a todos os funcionários permissões de visualização, edição e resposta para estes conteúdos. Os proprietários de dados podem monitorizar e revogar os conteúdos.|**Ativado**: ligado <br /><br />**Marcas visuais**: rodapé (documentos e e-mails)<br /><br />Classificado como Altamente Confidencial<br /><br />**Condições**: nenhuma<br /><br />**Proteção**: Azure (chave de nuvem) [[2]](#footnote-2)|
|Altamente Confidencial\Todos (não protegidos)|Dados que não necessitam de proteção. Utilize esta opção com cuidado e com uma justificação comercial adequada.|**Ativado**: ligado <br /><br />**Marcas visuais**: rodapé (documentos e e-mails)<br /><br />Classificado como Altamente Confidencial<br /><br />**Condições**: nenhuma<br /><br />**Proteção**: nenhuma|
|Altamente confidenciais \ destinatários apenas|Dados altamente confidenciais que requer a proteção e que podem ser visualizados, apenas os destinatários.|**Ativado**: ligado <br /><br />**Marcas visuais**: rodapé (e-mail)<br /><br />Classificado como Altamente Confidencial <br /><br />**Condições**: nenhuma<br /><br />**Proteção**: defina definidas pelo utilizador as permissões (pré-visualização), no Outlook aplicam não reencaminhar|

###### <a name="footnote-1"></a>Nota de rodapé 1
As permissões de proteção correspondem aos existentes no [modelo predefinido](configure-policy-templates.md#default-templates), **confidencial \ todos os funcionários**.

###### <a name="footnote-2"></a>Nota de rodapé 2 
As permissões de proteção correspondem aos existentes no [modelo predefinido](configure-policy-templates.md#default-templates), **altamente confidenciais \ todos os funcionários**.


### <a name="information-protection-bar"></a>Barra Information Protection

|Definição|Valor|
|-------------------------------|---------------------------|
|Title|Sensibilidade|
|Descrição|A etiqueta atual para estes conteúdos. Esta definição identifica o risco para a empresa se estes conteúdos forem partilhados com pessoas não autorizadas dentro ou fora da organização.|


### <a name="settings"></a>Definições

|Definição|Valor|
|-------------------------------|---------------------------|
|Todos os documentos e e-mails devem ter uma etiqueta (aplicada automaticamente ou pelos utilizadores)|Desativada|
|Selecione a etiqueta predefinida|Nenhum|
|Os utilizadores têm de fornecer uma justificação para poderem definir uma etiqueta de classificação inferior e remover uma etiqueta ou proteção|Desativada|
|Para mensagens de e-mail com anexos, aplique uma etiqueta que corresponda à classificação mais elevada dos mesmos|Desativada|
|Fornecer um URL personalizado para a página Web "Mais informações" do cliente do Azure Information Protection|Em Branco|


## <a name="default-policy-before-july-31-2017"></a>Política predefinida antes de 31 de Julho de 2017

Tenha em atenção que as descrições nesta política se referem aos dados que necessitam de proteção, bem como à monitorização e revogação dos mesmos. A política não configura esta proteção para estas etiquetas, por isso tem de efetuar passos adicionais para cumprir esta descrição. Por exemplo, configure a etiqueta para aplicar a proteção ou utilizar uma solução de (DLP) de prevenção de perda de dados. Antes de poder controlar e revogar um documento, utilizando o site de controlo de documentos, o documento tem de ser protegido pelo serviço Azure Rights Management e controlado pela pessoa que o documento protegido. 


### <a name="labels"></a>Etiquetas

|Etiqueta|Descrição|Definições|
|-------------------------------|---------------------------|-----------------|
|Pessoal|Dados não empresariais, apenas para utilização pessoal.|**Ativado**: ligado <br /><br />**Cor**: verde claro<br /><br />**Marcas visuais**: desligado <br /><br />**Condições**: nenhuma<br /><br />**Proteção**: nenhuma|
|Público|Dados empresariais que são especialmente preparados e aprovados para o consumo público.|**Ativado**: ligado <br /><br />**Cor**: verde<br /><br />**Marcas visuais**: desligado<br /><br />**Condições**: nenhuma<br /><br />**Proteção**: nenhuma|
|Geral|Dados empresariais que não se destinam ao consumo público. No entanto, estes dados podem ser partilhados com parceiros externos, conforme necessário. Os exemplos incluem um diretório de telefone interno da empresa, organogramas, padrões internos e a maioria da comunicação interna.|**Ativado**: ligado <br /><br />**Cor**: azul <br /><br />**Marcas visuais**: desligado<br /><br />**Condições**: nenhuma<br /><br />**Proteção**: nenhuma|
|Confidencial|Dados empresariais confidenciais que podiam causar danos à empresa se fossem partilhados com pessoas não autorizadas. Os exemplos incluem contratos, relatórios de segurança, resumos de previsões e dados de conta de vendas.|**Ativado**: ligado <br /><br />**Cor**: laranja<br /><br />**Marcas visuais**: desligado<br /><br />**Condições**: nenhuma<br /><br />**Proteção**: nenhuma|
|Altamente Confidencial|Dados empresariais altamente confidenciais que iriam causar danos à empresa se fossem partilhados com pessoas não autorizadas. Os exemplos incluem informações dos funcionários e clientes, palavras-passe, código de origem e relatórios financeiros previamente anunciados.|**Ativado**: ligado <br /><br />**Cor**: vermelho<br /><br />**Marcas visuais**: desligado<br /><br />**Condições**: nenhuma<br /><br />**Proteção**: nenhuma|


### <a name="sublabels"></a>Sublabels

|Etiqueta|Descrição|Definições|
|-------------------------------|---------------------------|-----------------|
|Confidencial\Todos os Funcionários|Dados confidenciais que necessitam de proteção, o que permite que todos os funcionários tenham todas as permissões. Os proprietários de dados podem monitorizar e revogar os conteúdos.|**Ativado**: ligado <br /><br />**Marcas visuais**: rodapé (documentos e e-mails)<br /><br />Classificado como Confidencial<br /><br />**Condições**: nenhuma<br /><br />**Proteção**: nenhuma|
|Confidencial\Todos (não protegidos)|Dados que não necessitam de proteção. Utilize esta opção com cuidado e com uma justificação comercial adequada.|**Ativado**: ligado <br /><br />**Marcas visuais**: rodapé (documentos e e-mails)<br /><br />Classificado como Confidencial <br /><br />**Condições**: nenhuma<br /><br />**Proteção**: nenhuma|
|Altamente Confidencial\Todos os Funcionários|Dados altamente confidenciais que fornecem a todos os funcionários permissões de visualização, edição e resposta para estes conteúdos. Os proprietários de dados podem monitorizar e revogar os conteúdos.|**Ativado**: ligado <br /><br />**Marcas visuais**: rodapé (documentos e e-mails)<br /><br />Classificado como Altamente Confidencial<br /><br />**Condições**: nenhuma<br /><br />**Proteção**: nenhuma|
|Altamente Confidencial\Todos (não protegidos)|Dados que não necessitam de proteção. Utilize esta opção com cuidado e com uma justificação comercial adequada.|**Ativado**: ligado <br /><br />**Marcas visuais**: rodapé (documentos e e-mails)<br /><br />Classificado como Altamente Confidencial<br /><br />**Condições**: nenhuma<br /><br />**Proteção**: nenhuma|

### <a name="information-protection-bar"></a>Barra Information Protection

|Definição|Valor|
|-------------------------------|---------------------------|
|Title|Sensibilidade|
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


### <a name="sublabels"></a>Sublabels

|Etiqueta|Descrição|Definições|
|-------------------------------|---------------------------|-----------------|
|Secreto\Toda a Empresa|Estes dados incluem informações empresariais confidenciais, permitidas para todos os empregados da empresa.|**Ativado**: ligado <br /><br />**Marcas visuais**: desligado<br /><br />**Condições**: nenhuma<br /><br />**Proteção**: nenhuma|
|Secreto\Os Meus Grupos|Estes dados incluem informações empresariais confidenciais, permitidas apenas para grupos de empregados.|**Ativado**: ligado <br /><br />**Marcas visuais**: desligado<br /><br />**Condições**: nenhuma<br /><br />**Proteção**: nenhuma|

### <a name="information-protection-bar"></a>Barra Information Protection

|Definição|Valor|
|-------------------------------|---------------------------|
|Title|Sensibilidade|
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
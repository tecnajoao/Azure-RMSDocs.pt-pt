---
title: A política predefinida para o Azure Information Protection – AIP
description: Conheça a forma como a política predefinida do Azure Information Protection está configurada. Se modificar a política predefinida, pode referenciar estes valores para voltar à política predefinida.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 04/09/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.openlocfilehash: 18654d3867fd456b8b4ed6eb0ebd01d9c86ff13a
ms.sourcegitcommit: 729b12e1219c6dbf1bb2a6cfa7239f24d1d13cc5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2019
ms.locfileid: "59364594"
---
# <a name="the-default-azure-information-protection-policy"></a>Política do Azure Information Protection predefinida

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Utilize as seguintes informações para compreender a forma como a política predefinida para o Azure Information Protection está configurada.

Quando um administrador ligado pela primeira vez para o serviço Azure Information Protection com o portal do Azure, é criada a política predefinida do Azure Information Protection para esse inquilino. Ocasionalmente, a Microsoft pode efetuar alterações a esta política predefinida mas se já estiver a utilizar o serviço antes da política predefinida ser revista, a versão anterior da política do Azure Information Protection predefinida não é atualizada porque poderá ser necessário configurado e implementado na produção.

Pode referenciar os seguintes valores para voltar a política do Azure Information Protection predefinida ou atualizar a política do Azure Information Protection para os valores mais recentes.

> [!IMPORTANT]
> A partir de Abril de 2019, há uma alteração gradualmente a implementar a novos clientes em que as etiquetas predefinidas não são automaticamente criadas. Estes inquilinos são automaticamente aprovisionados para a plataforma de etiquetagem unificada, para que não é necessário para migrar as etiquetas após ter configurado-las no portal do Azure.
> 
> Para estes inquilinos, caso haja qualquer etiquetas de sensibilidade já criadas na segurança do Office 365 e Centro de conformidade, o Centro de segurança do Microsoft 365 ou o Centro de conformidade do Microsoft 365, pode criar as etiquetas predefinidas da predefinição atual política do Azure Information Protection. Para tal, selecione **gerar etiquetas predefinidas** partir a **etiquetas** painel e adicione as etiquetas para a política global. Para obter instruções detalhadas, consulte a [introdução ao Azure Information Protection no portal do Azure](quickstart-viewpolicy.md) início rápido.


## <a name="current-default-policy"></a>Política predefinida atual

Esta versão da política do Azure Information Protection predefinida é de 31 de Julho de 2017.

Esta política do Azure Information Protection predefinida é criada quando o serviço Azure Rights Management está ativado, que é o caso dos novos inquilinos a partir de Fevereiro de 2018. Para obter mais informações, consulte o anúncio do blogue [melhorias para a proteção da pilha no Azure Information Protection](https://cloudblogs.microsoft.com/enterprisemobility/2018/03/08/improvements-to-the-protection-stack-in-azure-information-protection).

Esta política do Azure Information Protection predefinida também é criada, se tiver manualmente [ativar o serviço](activate-service.md) antes do Azure Information Protection a política foi criada. 

Se o serviço não foi ativado, a política do Azure Information Protection predefinida não configurar a proteção para as subetiquetas seguintes:

- **Confidencial\Todos os Funcionários**

- **Confidencial \ apenas Recetores**

- **Altamente Confidencial\Todos os Funcionários** 

- **Altamente confidencial \ apenas Recetores** 

Quando estas subetiquetas não são automaticamente configuradas para proteção, a política do Azure Information Protection predefinida permanece igual a [política de padrão anterior](#default-policy-before-july-31-2017).

Quando a proteção é aplicada para o **todos os funcionários** subetiquetas, a proteção é configurada utilizando os modelos predefinidos que são automaticamente convertidos em etiquetas no portal do Azure. Para obter mais informações sobre estes modelos, consulte [configurando e gerenciando modelos do Azure Information Protection](configure-policy-templates.md).

A partir de 30 de Agosto de 2017, esta versão da política predefinida do Azure Information Protection inclui as versões de vários idiomas dos nomes de etiqueta e descrições. 

#### <a name="more-information-about-the-recipients-only-sublabel"></a>Obter mais informações sobre a subetiqueta apenas os destinatários

Os utilizadores veem esta etiqueta no Outlook apenas. Eles não veem esta etiqueta no Word, Excel, PowerPoint, ou no Explorador de ficheiros. 

Quando os utilizadores selecionarem esta etiqueta, a opção do Outlook não reencaminhar é automaticamente aplicada à mensagem de e-mail. Os destinatários que os usuários especifiquem não é possível reencaminhar o e-mail e não é possível copiar ou imprimir o conteúdo ou guardar os anexos.


### <a name="labels"></a>Etiquetas

|Etiqueta|Descrição|Definições|
|-------------------------------|---------------------------|-----------------|
|Pessoal|Dados não empresariais, apenas para utilização pessoal.|**Ativado**: Ativado <br /><br />**Cor**: Verde claro<br /><br />**Marcas visuais**: Desativado <br /><br />**Condições**: Nenhum<br /><br />**Proteção**: Nenhum|
|Público|Dados empresariais que são especialmente preparados e aprovados para o consumo público.|**Ativado**: Ativado <br /><br />**Cor**: Verde<br /><br />**Marcas visuais**: Desativado<br /><br />**Condições**: Nenhum<br /><br />**Proteção**: Nenhum|
|Geral|Dados empresariais que não se destinam ao consumo público. No entanto, estes dados podem ser partilhados com parceiros externos, conforme necessário. Os exemplos incluem um diretório de telefone interno da empresa, organogramas, padrões internos e a maioria da comunicação interna.|**Ativado**: Ativado <br /><br />**Cor**: Azul <br /><br />**Marcas visuais**: Desativado<br /><br />**Condições**: Nenhum<br /><br />**Proteção**: Nenhum|
|Confidencial|Dados empresariais confidenciais que podiam causar danos à empresa se fossem partilhados com pessoas não autorizadas. Os exemplos incluem contratos, relatórios de segurança, resumos de previsões e dados de conta de vendas.|**Ativado**: Ativado <br /><br />**Cor**: Cor de laranja<br /><br />**Marcas visuais**: Desativado<br /><br />**Condições**: Nenhum<br /><br />**Proteção**: Nenhum|
|Altamente Confidencial|Dados empresariais altamente confidenciais que iriam causar danos à empresa se fossem partilhados com pessoas não autorizadas. Exemplos: informações dos funcionários e clientes, palavras-passe, código de origem e relatórios financeiros previamente anunciados.|**Ativado**: Ativado <br /><br />**Cor**: Vermelho<br /><br />**Marcas visuais**: Desativado<br /><br />**Condições**: Nenhum<br /><br />**Proteção**: Nenhum|


### <a name="sublabels"></a>Subetiquetas

|Etiqueta|Descrição|Definições|
|-------------------------------|---------------------------|-----------------|
|Confidencial\Todos os Funcionários|Dados confidenciais que necessitam de proteção, o que permite que todos os funcionários tenham todas as permissões. Os proprietários de dados podem monitorizar e revogar os conteúdos.|**Ativado**: Ativado <br /><br />**Marcas visuais**: Rodapé (documentos e e-mails)<br /><br />Classificado como Confidencial<br /><br />**Condições**: Nenhum<br /><br />**Proteção**: O Azure (chave da cloud) [[1]](#footnote-1)|
|Confidencial\Todos (não protegidos)|Dados que não necessitam de proteção. Utilize esta opção com cuidado e com uma justificação comercial adequada.|**Ativado**: Ativado <br /><br />**Marcas visuais**: Rodapé (documentos e e-mails)<br /><br />Classificado como Confidencial <br /><br />**Condições**: Nenhum<br /><br />**Proteção**: Nenhum|
|Confidencial \ apenas Recetores|Dados confidenciais que requerem proteção e que podem ser visualizados apenas por destinatários.|**Ativado**: Ativado <br /><br />**Marcas visuais**: Rodapé (e-mail)<br /><br />Classificado como Confidencial <br /><br />**Condições**: Nenhum<br /><br />**Proteção**: Definir permissões de definidas pelo utilizador (pré-visualização), no Outlook aplicam-se não reencaminhar|
|Altamente Confidencial\Todos os Funcionários|Dados altamente confidenciais que fornecem a todos os funcionários permissões de visualização, edição e resposta para estes conteúdos. Os proprietários de dados podem monitorizar e revogar os conteúdos.|**Ativado**: Ativado <br /><br />**Marcas visuais**: Rodapé (documentos e e-mails)<br /><br />Classificado como Altamente Confidencial<br /><br />**Condições**: Nenhum<br /><br />**Proteção**: O Azure (chave da cloud) [[2]](#footnote-2)|
|Altamente Confidencial\Todos (não protegidos)|Dados que não necessitam de proteção. Utilize esta opção com cuidado e com uma justificação comercial adequada.|**Ativado**: Ativado <br /><br />**Marcas visuais**: Rodapé (documentos e e-mails)<br /><br />Classificado como Altamente Confidencial<br /><br />**Condições**: Nenhum<br /><br />**Proteção**: Nenhum|
|Altamente confidencial \ apenas Recetores|Dados altamente confidenciais que requerem proteção e que podem ser visualizados apenas por destinatários.|**Ativado**: Ativado <br /><br />**Marcas visuais**: Rodapé (e-mail)<br /><br />Classificado como Altamente Confidencial <br /><br />**Condições**: Nenhum<br /><br />**Proteção**: Definir permissões de definidas pelo utilizador (pré-visualização), no Outlook aplicam-se não reencaminhar|

###### <a name="footnote-1"></a>Nota de rodapé 1
As permissões de proteção correspondem à [modelo predefinido](configure-policy-templates.md#default-templates), **confidencial \ todos os funcionários**.

###### <a name="footnote-2"></a>Nota de rodapé 2 
As permissões de proteção correspondem à [modelo predefinido](configure-policy-templates.md#default-templates), **altamente confidencial \ todos os funcionários**.


### <a name="information-protection-bar"></a>Barra Information Protection

|Definição|Valor|
|-------------------------------|---------------------------|
|Título|Sensibilidade|
|Descrição|A etiqueta atual para estes conteúdos. Esta definição identifica o risco para a empresa se estes conteúdos forem partilhados com pessoas não autorizadas dentro ou fora da organização.|


### <a name="settings"></a>Definições

Algumas das configurações foram adicionadas após 31 de Julho de 2017.

|Definição|Valor|
|-------------------------------|---------------------------|
|Selecione a etiqueta predefinida|Nenhum|
|Enviar dados de auditoria para análise do Azure Information Protection|Desativado|
|Todos os documentos e e-mails devem ter uma etiqueta (aplicada automaticamente ou pelos utilizadores)|Desativado|
|Os utilizadores têm de fornecer uma justificação para poderem definir uma etiqueta de classificação inferior e remover uma etiqueta ou proteção|Desativado|
|Para mensagens de e-mail com anexos, aplique uma etiqueta que corresponda à classificação mais elevada dos mesmos|Desativado|
|Apresentar a barra de Information Protection nas aplicações do Office|Desativado|
|Adicionar o botão não reencaminhar ao Friso do Outlook|Desativado|
|Disponibilizar a opção de permissões personalizadas para utilizadores|Desativado|
|Fornecer um URL personalizado para a página Web "Mais informações" do cliente do Azure Information Protection|Em Branco|

## <a name="default-policy-before-july-31-2017"></a>Política predefinida antes de 31 de Julho de 2017

Tenha em atenção que as descrições nesta política se referem aos dados que necessitam de proteção, bem como à monitorização e revogação dos mesmos. A política não configura esta proteção para estas etiquetas, por isso tem de efetuar passos adicionais para cumprir esta descrição. Por exemplo, configure a etiqueta para aplicar a proteção ou utilizar uma solução de (DLP) de prevenção de perda de dados. Antes de poder controlar e revogar um documento através do site de controlo de documentos, o documento tem de ser protegido pelo serviço Azure Rights Management e controlado pela pessoa que protegeu o documento. 


### <a name="labels"></a>Etiquetas

|Etiqueta|Descrição|Definições|
|-------------------------------|---------------------------|-----------------|
|Pessoal|Dados não empresariais, apenas para utilização pessoal.|**Ativado**: Ativado <br /><br />**Cor**: Verde claro<br /><br />**Marcas visuais**: Desativado <br /><br />**Condições**: Nenhum<br /><br />**Proteção**: Nenhum|
|Público|Dados empresariais que são especialmente preparados e aprovados para o consumo público.|**Ativado**: Ativado <br /><br />**Cor**: Verde<br /><br />**Marcas visuais**: Desativado<br /><br />**Condições**: Nenhum<br /><br />**Proteção**: Nenhum|
|Geral|Dados empresariais que não se destinam ao consumo público. No entanto, estes dados podem ser partilhados com parceiros externos, conforme necessário. Os exemplos incluem um diretório de telefone interno da empresa, organogramas, padrões internos e a maioria da comunicação interna.|**Ativado**: Ativado <br /><br />**Cor**: Azul <br /><br />**Marcas visuais**: Desativado<br /><br />**Condições**: Nenhum<br /><br />**Proteção**: Nenhum|
|Confidencial|Dados empresariais confidenciais que podiam causar danos à empresa se fossem partilhados com pessoas não autorizadas. Os exemplos incluem contratos, relatórios de segurança, resumos de previsões e dados de conta de vendas.|**Ativado**: Ativado <br /><br />**Cor**: Cor de laranja<br /><br />**Marcas visuais**: Desativado<br /><br />**Condições**: Nenhum<br /><br />**Proteção**: Nenhum|
|Altamente Confidencial|Dados empresariais altamente confidenciais que iriam causar danos à empresa se fossem partilhados com pessoas não autorizadas. Exemplos: informações dos funcionários e clientes, palavras-passe, código de origem e relatórios financeiros previamente anunciados.|**Ativado**: Ativado <br /><br />**Cor**: Vermelho<br /><br />**Marcas visuais**: Desativado<br /><br />**Condições**: Nenhum<br /><br />**Proteção**: Nenhum|


### <a name="sublabels"></a>Subetiquetas

|Etiqueta|Descrição|Definições|
|-------------------------------|---------------------------|-----------------|
|Confidencial\Todos os Funcionários|Dados confidenciais que necessitam de proteção, o que permite que todos os funcionários tenham todas as permissões. Os proprietários de dados podem monitorizar e revogar os conteúdos.|**Ativado**: Ativado <br /><br />**Marcas visuais**: Rodapé (documentos e e-mails)<br /><br />Classificado como Confidencial<br /><br />**Condições**: Nenhum<br /><br />**Proteção**: Nenhum|
|Confidencial\Todos (não protegidos)|Dados que não necessitam de proteção. Utilize esta opção com cuidado e com uma justificação comercial adequada.|**Ativado**: Ativado <br /><br />**Marcas visuais**: Rodapé (documentos e e-mails)<br /><br />Classificado como Confidencial <br /><br />**Condições**: Nenhum<br /><br />**Proteção**: Nenhum|
|Altamente Confidencial\Todos os Funcionários|Dados altamente confidenciais que fornecem a todos os funcionários permissões de visualização, edição e resposta para estes conteúdos. Os proprietários de dados podem monitorizar e revogar os conteúdos.|**Ativado**: Ativado <br /><br />**Marcas visuais**: Rodapé (documentos e e-mails)<br /><br />Classificado como Altamente Confidencial<br /><br />**Condições**: Nenhum<br /><br />**Proteção**: Nenhum|
|Altamente Confidencial\Todos (não protegidos)|Dados que não necessitam de proteção. Utilize esta opção com cuidado e com uma justificação comercial adequada.|**Ativado**: Ativado <br /><br />**Marcas visuais**: Rodapé (documentos e e-mails)<br /><br />Classificado como Altamente Confidencial<br /><br />**Condições**: Nenhum<br /><br />**Proteção**: Nenhum|

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
|Os utilizadores têm de fornecer uma justificação para poderem definir uma etiqueta de classificação inferior e remover uma etiqueta ou proteção|Desativado|
|Para mensagens de e-mail com anexos, aplique uma etiqueta que corresponda à classificação mais elevada dos mesmos|Desativado|
|Fornecer um URL personalizado para a página Web "Mais informações" do cliente do Azure Information Protection|Em Branco|

## <a name="default-policy-before-march-21-2017"></a>Política predefinida antes de 21 de março de 2017

### <a name="labels"></a>Etiquetas

|Etiqueta|Descrição|Definições|
|-------------------------------|---------------------------|-----------------|
|Pessoal|Apenas para utilização pessoal. Estes dados não serão monitorizados pela organização. As informações pessoais não podem incluir quaisquer dados relacionados com a empresa.|**Ativado**: Ativado <br /><br />**Cor**: Verde claro<br /><br />**Marcas visuais**: Desativado <br /><br />**Condições**: Nenhum<br /><br />**Proteção**: Nenhum|
|Público|Estas informações são internas e podem ser utilizadas por todas as pessoas dentro ou fora da empresa.|**Ativado**: Ativado <br /><br />**Cor**: Verde<br /><br />**Marcas visuais**: Desativado<br /><br />**Condições**: Nenhum<br /><br />**Proteção**: Nenhum|
|Interna|Estas informações incluem um largo espetro de dados empresariais internos que podem ser utilizados por todos os empregados e que podem ser partilhados com clientes autorizados e parceiros de negócios. Exemplos de informações internas são as políticas da empresa e a maior parte das comunicações internas.|**Ativado**: Ativado <br /><br />**Cor**: Azul <br /><br />**Marcas visuais**: Rodapé (documentos e e-mails): <br /><br />Sensibilidade: Interna<br /><br />**Condições**: Nenhum<br /><br />**Proteção**: Nenhum|
|Confidencial|Estes dados incluem informações empresariais confidenciais. A exposição estes dados a utilizadores não autorizados pode causar danos na organização. Exemplos de informações confidenciais são as informações dos empregados, projetos de clientes individuais ou contratos e dados de contas de vendas.|**Ativado**: Ativado <br /><br />**Cor**: Cor de laranja<br /><br />**Marcas visuais**: Rodapé (documentos e e-mails):<br /><br /> Sensibilidade: Confidencial<br /><br />**Condições**: Nenhum<br /><br />**Proteção**: Nenhum|
|Secreto|Estes dados incluem informações altamente confidenciais para as empresas e têm de ser protegidas. A exposição de dados Secretos a utilizadores não autorizados pode causar graves danos na organização. Exemplos de informações secretas são informações de identificação pessoal, registos de clientes, código de origem e relatórios financeiros previamente anunciados.|**Ativado**: Ativado <br /><br />**Cor**: Vermelho<br /><br />**Marcas visuais**: Rodapé (documentos e e-mails):<br /><br /> Sensibilidade: Secreto<br /><br />**Condições**: Nenhum<br /><br />**Proteção**: Nenhum|


### <a name="sublabels"></a>Subetiquetas

|Etiqueta|Descrição|Definições|
|-------------------------------|---------------------------|-----------------|
|Secreto\Toda a Empresa|Estes dados incluem informações empresariais confidenciais, permitidas para todos os empregados da empresa.|**Ativado**: Ativado <br /><br />**Marcas visuais**: Desativado<br /><br />**Condições**: Nenhum<br /><br />**Proteção**: Nenhum|
|Secreto\Os Meus Grupos|Estes dados incluem informações empresariais confidenciais, permitidas apenas para grupos de empregados.|**Ativado**: Ativado <br /><br />**Marcas visuais**: Desativado<br /><br />**Condições**: Nenhum<br /><br />**Proteção**: Nenhum|

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
|Os utilizadores têm de fornecer uma justificação para poderem definir uma etiqueta de classificação inferior e remover uma etiqueta ou proteção|Desativado|
|Fornecer um URL personalizado para a página Web "Mais informações" do cliente do Azure Information Protection|Em Branco|


## <a name="next-steps"></a>Passos Seguintes

Para mais informações sobre como configurar a política do Azure Information Protection, utilize as ligações na secção [Configurar política da organização](configure-policy.md#configuring-your-organizations-policy). 

---
title: Colaboração de documentos segura com o Azure Information Protection
description: Fluxo de trabalho ponto-a-ponto para colaborar em documentos que estão protegidos pelo Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/21/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4895c429-959f-47c7-9007-b8f032f6df6f
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: d5c24747bcb05f7004f7d42b0145ce6cc1bbade5
ms.sourcegitcommit: aae04d78ff301921a4e29ac23bd932fb24a83dbe
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/22/2018
---
# <a name="secure-document-collaboration-by-using-azure-information-protection"></a>Colaboração de documentos segura utilizando o Azure Information Protection

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Quando utilizar o Azure Information Protection, pode proteger os documentos sem sacrificar colaboração para que os utilizadores autorizados. A maioria dos documentos que um utilizador cria e, em seguida, partilhe com outras pessoas para ver e editar irá ser documentos do Office do Word, Excel e PowerPoint. Estes documentos suportam a proteção nativa, o que significa que, além das funcionalidades de proteção de autorização e encriptação, também suportam permissão restrita para um controlo mais detalhado. 

Estas permissões são designadas por direitos de utilização e inclui as permissões como ver, editar, imprimir. Pode definir direitos de utilização individuais quando um documento está protegido, ou pode definir um agrupamento de direitos de utilização, denominado níveis de permissão. Níveis de permissão tornam mais fácil selecionar os direitos de utilização que são normalmente utilizados em conjunto, por exemplo, revisor e Coautor. Para obter mais informações sobre direitos de utilização e níveis de permissão, consulte [configurar direitos de utilização do Azure Rights Management](../deploy-use/configure-usage-rights.md).

Quando configurar estas permissões, também tem de especificar os utilizadores que são para:

- **Para utilizadores na sua própria organização ou outra organização que utiliza o Azure Active Directory**: pode especificar contas de utilizador do Azure AD, grupos do Azure AD ou todos os utilizadores na organização. 

- **Para os utilizadores que não tem uma conta do Azure Active Directory**: Especifique um endereço de e-mail que será utilizado com uma conta Microsoft. Esta conta pode já existir ou, os utilizadores podem criá-la no momento que abrirem o documento protegido. 
    
    Para abrir documentos com uma conta Microsoft, os utilizadores podem utilizar o Office 2016 clique para execução. Outras versões e edições do Office fazê-lo ainda não suporte abrir Office protegido documentos com uma conta Microsoft.

Como administrador, pode configurar uma etiqueta de Azure Information Protection para aplicar as permissões e os utilizadores autorizados. Esta configuração torna muito mais fácil para os utilizadores e de outros administradores para aplicar as definições de proteção correto, porque simplesmente aplicam-se a etiqueta sem ter de especificar os detalhes. As secções seguintes fornecem uma instruções de exemplo para proteger um documento que suporta a colaboração segura com utilizadores internos e externos.


## <a name="example-configuration-for-a-label-to-apply-protection-to-support-internal-and-external-collaboration"></a>Configuração de exemplo para uma etiqueta aplicar a proteção para suportarem a colaboração interna e externa

Este exemplo explica configurar uma etiqueta para aplicar a proteção para que os utilizadores da sua organização podem colaborar em documentos com todos os utilizadores de outra organização que tem o Office 365 ou do Azure AD, um grupo de uma organização diferente que tenha existente Office 365 ou do Azure AD e um utilizador que não tem uma conta no Azure AD e, em vez disso, irá utilizar os seus endereços de e-mail do Gmail. 

1. Selecione a etiqueta que já se encontra na política de global ou de uma política de âmbito. No **proteção** painel, certifique-se de que **Azure (chave de nuvem)** está selecionada.
    
2. Certifique-se **definir permissões** está selecionado e selecione **adicionar permissões**.

3. No **adicionar permissões** painel: 
    
    - Para o grupo de interno: selecione **procurar diretório** para selecionar o grupo, tem de ser ativado por correio eletrónico.
    
    - Para todos os utilizadores na organização externo primeiro: selecione **Introduza detalhes** e escreva o nome de um domínio no inquilino da organização. Por exemplo, fabrikam.com.
    
    - Para o grupo no segundo organização externo: ainda no **Introduza detalhes** separador, escreva o endereço de e-mail do grupo no inquilino da organização. Por exemplo, sales@contoso.com.
    
    - Para o utilizador que não tem uma conta do Azure AD: ainda no **Introduza detalhes** separador, escreva o endereço de correio eletrónico do utilizador. Por exemplo, bengi.turan@gmail.com. 

4. Para conceder as mesmas permissões para todas as estes utilizadores: para **escolher permissões predefinição**, selecione **Coproprietário**, **Coautor**, **revisor**, ou **personalizada** para seleccionar as permissões que pretende conceder.
    
    Por exemplo, as suas permissões configuradas poderão ter um aspeto semelhantes ao seguinte:
        
    ![Configurar permissões para colaboração segura](../media/collaboration-permissions.png)



5. Clique em **OK** no **adicionar permissões** painel.

6. No **proteção** painel, clique em **OK**. 

## <a name="applying-the-label-that-supports-secure-collaboration"></a>Aplicar a etiqueta que suporta a colaboração segura

Agora que esta etiqueta é configurada, pode ser aplicada aos documentos de diversas formas, que incluem o seguinte:

|Diferentes formas de aplicar a etiqueta|Mais informações|
|---------------|----------|
|Um utilizador seleccionar manualmente a etiqueta quando o documento é criado na respetiva aplicação do Office.|Os utilizadores, selecione a etiqueta do **proteger** botão no friso Office ou a partir da barra do Azure Information Protection.|
|Os utilizadores recebem um pedido para selecionar uma etiqueta, quando um novo documento é guardado.|Configurar o Azure Information Protection [definição de política](../deploy-use/configure-policy-settings.md) denominado **todos os documentos e e-mails devem ter uma etiqueta**.|
|Um utilizador partilha o documento por e-mail e seleciona manualmente a etiqueta no Outlook.|Os utilizadores, selecione a etiqueta do **proteger** botão no friso Office ou a partir da barra do Azure Information Protection e o documento anexado está protegido automaticamente com as mesmas definições.|
|Um administrador aplica-se a etiqueta de documentos utilizando o PowerShell.|Utilize o [conjunto AIPFileLabel](/powershell/module/azureinformationprotection/set-aipfilelabel) cmdlet para aplicar a etiqueta para um documento específico ou de todos os documentos numa pasta.|
|Além disso tiver configurado a etiqueta para aplicar a classificação automática que agora pode ser aplicada através da análise do Azure Information Protection, ou do PowerShell.|Consulte [como configurar condições para classificação automática e recomendada para o Azure Information Protection](../deploy-use/configure-policy-classification.md).|

Para concluir estas instruções, aplica manualmente a etiqueta quando criar o documento na aplicação do Office: 

1. Num computador cliente, se já tiver aplicação do Office, abrir, primeiro feche e reabra-o para obter as últimas alterações de política, que incluem a etiqueta recentemente configurada. 

2. Aplicar a etiqueta para um documento e guardá-lo.

Partilhe o documento protegido por ligá-la a um e-mail e envie-o para as pessoas autorizadas para editar o documento.

## <a name="opening-and-editing-the-protected-document"></a>Abrir e editar o documento protegido

Quando os utilizadores que autorizados abrem o documento para edição, o documento abre-se com uma faixa de informações que os informa de que as permissões estão limitadas. Por exemplo:

![Faixa do informações de exemplo de permissões do Azure Information Protection](../media/example-restricted-access-banner.png)

Se o utilizador selecionar o **ver permissão** botão, verão as permissões que têm. No exemplo seguinte, o utilizador pode ver e editar o documento:

![Azure caixa de diálogo do exemplo de permissões de Information Protection](../media/example-permisisons-popup.png)


Antes do documento é aberto, um dos fluxos de autenticação seguintes ocorrem:

- Para os utilizadores que possuem uma conta do Azure AD, que utilizam as respetivas credenciais do Azure AD para ser autenticado pelo Azure AD e o documento é aberto. 

- Para o utilizador que não tem uma conta do Azure AD, se estes não sessão iniciadas no Office com uma conta que tenha permissões para abrir o documento, verá o **contas** página. 
    
   No **contas** página, selecione **adicionar conta**:
   
    ![Adicionar uma conta Microsoft para abrir o documento protegido](../media/add-account-msa.png)

   No **sessão** página, selecione **crie uma!** e siga as instruções para criar uma nova conta Microsoft com o endereço de e-mail que foi utilizado para conceder as permissões:
    
    ![Criar uma conta Microsoft para abrir o documento protegido](../media/create-account-msa.png)
    
    Quando é criada a nova conta Microsoft, a conta local muda a esta nova conta Microsoft e o utilizador pode, em seguida, abra o documento.


### <a name="supported-scenarios-for-opening-protected-documents"></a>Cenários suportados para abrir documentos protegidos

Os seguinte tabela resumos de métodos de autenticação diferentes que são suportados para abrir e editar documentos protegidos.

Além disso, o Visualizador do Azure Information Protection para iOS e Android pode abrir ficheiros para uma visualização utilizando uma conta Microsoft.

|Plataformas para abrir e editar documentos: <br />Word, Excel, PowerPoint|Método de autenticação:<br />Azure AD|Método de autenticação:<br />Conta Microsoft|
|---------------|----------|-----------|-----------|
|Windows|Sim [[1]](#footnote-1)|Sim [[2]](#footnote-2)|
|iOS|Sim [[1]](#footnote-1)|Não|
|Android|Sim [[1]](#footnote-1)|Não |
|MacOS|Sim [[1]](#footnote-1)|Não|

###### <a name="footnote-1"></a>Nota de rodapé 1
Suporta contas de utilizador, grupos de e-mail, todos os membros. Contas de utilizador e grupos com capacidade de correio eletrónico podem incluir as contas de convidados. Todos os membros excluir as contas de convidados.

###### <a name="footnote-2"></a>Nota de rodapé 2
Atualmente suportado pelo Office 2016 clique para executar apenas.


## <a name="next-steps"></a>Próximos passos

Consulte outros [configurações de exemplo](../deploy-use/configure-policy-protection.md#example-configurations) para etiquetas aplicar a proteção para cenários comuns. Este artigo também contém mais detalhes sobre as definições de proteção.

Para obter mais informações sobre as opções e definições que pode configurar para a etiqueta, consulte [política de configuração do Azure Information Protection](../deploy-use/configure-policy.md). 

A etiqueta que foi configurada neste artigo também cria um modelo de proteção com o mesmo nome. Se tiver aplicações e serviços que se integram com modelos de proteção do Azure Information Protection, possam aplicar este modelo. Por exemplo, soluções DLP e as regras do fluxo de correio. Outlook na web apresenta automaticamente modelos de proteção da política global do Azure Information Protection. 


[!INCLUDE[Commenting house rules](../includes/houserules.md)]



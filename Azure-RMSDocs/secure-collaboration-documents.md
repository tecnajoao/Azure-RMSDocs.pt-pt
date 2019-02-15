---
title: Configurar a colaboração de documentos segura com o Azure Information Protection
description: Fluxo de trabalho ponto-a-ponto para colaborar nos documentos que estão protegidos pelo Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 01/24/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 4895c429-959f-47c7-9007-b8f032f6df6f
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 0c9e426fe6025b31f03ed84e65741c4a461e3938
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56257319"
---
# <a name="configuring-secure-document-collaboration-by-using-azure-information-protection"></a>Configuração da colaboração de documentos segura, utilizando o Azure Information Protection

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Quando utiliza o Azure Information Protection, pode proteger os seus documentos sem sacrificar a colaboração para os utilizadores autorizados. A maioria dos documentos que um usuário cria e, em seguida, partilhar com outras pessoas para ver e editar irá ser documentos do Office do Word, Excel e PowerPoint. Estes documentos suportam a proteção nativa, o que significa que as funcionalidades de proteção de autorização e criptografia, além de também suportarem permissão restrita para um controlo mais detalhado. 

Estas permissões são chamadas de direitos de utilização e incluir permissões como ver, editar, imprimir. Pode definir os direitos de utilização individuais quando um documento está protegido, ou pode definir um agrupamento de direitos de utilização, chamado níveis de permissão. Níveis de permissão mais fácil selecionar os direitos de utilização que são normalmente utilizados em conjunto, por exemplo, revisor e Coautor. Para obter mais informações sobre direitos de utilização e níveis de permissão, consulte [configurar direitos de utilização do Azure Rights Management](configure-usage-rights.md).

Quando configurar estas permissões, pode especificar quais os utilizadores que são para:

- **Para os utilizadores na sua própria organização ou de outra organização que utiliza o Azure Active Directory**: Pode especificar contas de utilizador do Azure AD, grupos do Azure AD ou todos os utilizadores nessa organização. 

- **Para os utilizadores que não tem uma conta do Azure Active Directory**: Especifique um endereço de e-mail que será utilizado com uma conta Microsoft. Esta conta pode já existir, ou os utilizadores podem criá-la no momento que abrem o documento protegido. 
    
    Para abrir documentos com uma conta Microsoft, os utilizadores podem utilizar aplicações do Office 365 (clique-e-use). Outras versões e edições do Office fazem ainda não suporte abrir o Office proteger documentos com uma conta Microsoft.

- **Para qualquer utilizador autenticado**: Esta opção é adequada para quando não precisa de controlar quem acede ao documento protegido, fornecendo ao usuário que possa ser autenticado. A autenticação pode ser pelo Azure AD, utilizando uma conta Microsoft, ou até mesmo um provedor social federado ou código de acesso único quando o conteúdo é protegido pelas novas capacidades de encriptação de mensagens do Office 365. 

Como administrador, pode configurar uma etiqueta do Azure Information Protection para aplicar as permissões e os utilizadores autorizados. Esta configuração torna muito fácil para os utilizadores e a outros administradores aplicar as definições de proteção correto, porque eles simplesmente aplicam a etiqueta sem ter de especificar todos os detalhes. As secções seguintes fornecem uma exemplo passo a passo para proteger um documento que oferece suporte à colaboração segura com usuários internos e externos.


## <a name="example-configuration-for-a-label-to-apply-protection-to-support-internal-and-external-collaboration"></a>Exemplo de configuração para uma etiqueta aplicar a proteção para suportarem a colaboração interna e externa

Este exemplo descreve como configurar uma etiqueta existente para aplicar a proteção para que os utilizadores da sua organização podem colaborar com documentos com todos os utilizadores de outra organização que tenha o Office 365 ou do Azure AD, um grupo a partir de uma organização diferente que tenha Office 365 ou do Azure AD e um utilizador que não tem uma conta no Azure AD e em vez disso, irá utilizar o endereço de e-mail do Gmail.

Uma vez que o cenário restringe o acesso a pessoas específicas, ele não inclui a definição para utilizadores autenticados. Para obter um exemplo de como pode configurar uma etiqueta com esta definição, consulte [exemplo 5: Etiqueta, que criptografa o conteúdo, mas não restringe quem pode acessá-lo](configure-policy-protection.md#example-5-label-that-encrypts-content-but-doesnt-restrict-who-can-access-it).  

1. Selecione a etiqueta que já se encontra na política global ou de uma política de âmbito. Sobre o **proteção** painel, certifique-se **Azure (chave da cloud)** está selecionada.
    
2. Certifique-se **definir permissões** está selecionado e selecione **adicionar permissões**.

3. Sobre o **adicionar permissões** painel: 
    
   - Para o seu grupo interno: Selecione **procurar diretório** para selecionar o grupo, o que deve ter o e-mail ativado.
    
   - Para todos os utilizadores na organização externa primeiro: Selecione **introduza os detalhes** e escreva o nome de um domínio no inquilino da organização. Por exemplo, fabrikam.com.
    
   - Para o grupo da organização externa segundo: Ainda na **introduza os detalhes** separador, escreva o endereço de e-mail do grupo no inquilino da organização. Por exemplo, sales@contoso.com.
    
   - Para o utilizador que não tem uma conta do Azure AD: Ainda na **introduza os detalhes** separador, escreva o endereço de e-mail do utilizador. Por exemplo, bengi.turan@gmail.com. 

4. Para conceder as mesmas permissões para todos esses usuários: Para **escolha as permissões da configuração predefinida**, selecione **Coproprietário**, **Coautor**, **revisor**, ou **personalizado**para selecionar as permissões que pretende conceder.
    
    Por exemplo, as suas permissões configuradas podem ter um aspeto semelhantes ao seguinte:
        
    ![Configuração de permissões para colaboração segura](./media/collaboration-permissions.png)

5. Clique em **OK** sobre o **adicionar permissões** painel.

6. Sobre o **proteção** painel, clique em **OK**.

7. Sobre o **rótulo** painel, selecione **guardar**. 

## <a name="applying-the-label-that-supports-secure-collaboration"></a>Aplicar a etiqueta que oferece suporte à colaboração segura

Agora que esta etiqueta está configurada, pode ser aplicada a documentos de diversas formas, que incluem o seguinte:

|Diferentes formas de aplicar a etiqueta|Mais informações|
|---------------|----------|
|Um usuário selecionar manualmente a etiqueta quando o documento é criado na respetiva aplicação do Office.|Os utilizadores selecionem a etiqueta do **Protect** botão da faixa de opções do Office ou a partir da barra Azure Information Protection.|
|É pedido aos utilizadores para selecionar uma etiqueta, quando um novo documento é guardado.|Configurar o Azure Information Protection [definição de política](configure-policy-settings.md) com o nome **todos os documentos e e-mails devem ter uma etiqueta**.|
|Um usuário compartilha o documento por e-mail e manualmente seleciona a etiqueta no Outlook.|Os utilizadores selecionem a etiqueta do **Protect** botão da faixa de opções do Office ou a partir da barra Azure Information Protection e o documento anexado está protegido automaticamente com as mesmas definições.|
|Um administrador aplica-se a etiqueta para o documento com o PowerShell.|Utilize o [Set-AIPFileLabel](/powershell/module/azureinformationprotection/set-aipfilelabel) cmdlet para aplicar a etiqueta a um documento específico ou de todos os documentos numa pasta.|
|Além disso tiver configurado a etiqueta para aplicar a classificação automática que agora pode ser aplicada ao utilizar o scanner do Azure Information Protection ou o PowerShell.|Ver [como configurar condições para classificação automática e recomendada para o Azure Information Protection](configure-policy-classification.md).|

Para concluir este passo a passo, aplica manualmente a etiqueta quando criar o documento na aplicação do Office: 

1. Num computador cliente, se já tiver a aplicação do Office, abrir, primeiro feche e reabra-o para obter as últimas alterações de política, que incluem a etiqueta recém configurada. 

2. Aplicar a etiqueta a um documento e salvá-lo.

Partilhe o documento protegido ao ligá-la para um e-mail e envie-o para as pessoas que tem autorização para editar o documento.

## <a name="opening-and-editing-the-protected-document"></a>Abrir e editar o documento protegido

Quando os utilizadores que autorizou abrem o documento para edição, o documento é aberto com uma faixa de informações que os informa de que permissões são restritas. Por exemplo:

![Azure faixa de informações do exemplo de permissões do Information Protection](./media/example-restricted-access-banner.png)

Se selecionarem a **permissão de visualização** botão, verão as permissões que têm. No exemplo a seguir, o utilizador pode ver e editar o documento:

![Azure caixa de diálogo do exemplo de permissões do Information Protection](./media/example-permisisons-popup.png)

Nota: Se o documento é aberto por utilizadores externos que também estão a utilizar o Azure Information Protection, o aplicativo do Office não apresenta a etiqueta de classificação para o documento, embora permanecem quaisquer marcas visuais da etiqueta. Em vez disso, os utilizadores externos podem aplicar seus próprios etiqueta em conformidade com a taxonomia de classificação da respetiva organização. Se esses utilizadores externos, em seguida, enviar novamente o documento editado para, o Office apresenta a etiqueta de classificação original quando abrir o documento novamente.

Antes de abre o documento protegido, uma após a autenticação flui acontecer:

- Para os utilizadores que têm uma conta do Azure AD, que utilizam as credenciais do Azure AD para ser autenticado pelo Azure AD e o documento é aberto. 

- Para o utilizador que não tem uma conta do Azure AD, se eles não sessão iniciados no Office com uma conta que tem permissões para abrir o documento, verão a **contas** página. 
    
   Sobre o **contas** página, selecione **adicionar conta**:
   
    ![A adicionar uma conta Microsoft para abrir o documento protegido](./media/add-account-msa.png)

   Sobre o **iniciar sessão** página, selecione **criá-lo!** e siga as instruções para criar uma nova conta Microsoft com o endereço de e-mail que foi utilizado para conceder as permissões:
    
    ![Criar uma conta Microsoft para abrir o documento protegido](./media/create-account-msa.png)
    
    Quando é criada a nova conta Microsoft, a conta local muda a esta nova conta Microsoft e o utilizador pode abrir o documento.


### <a name="supported-scenarios-for-opening-protected-documents"></a>Cenários suportados para abrir documentos protegidos

Os resumos de tabela seguintes os métodos de autenticação diferentes que são suportados para visualizar e editar documentos protegidos.

Além disso, os seguintes cenários de suportam de documentos em visualização:

- O Visualizador do Azure Information Protection para Windows e para iOS e Android pode abrir ficheiros com uma conta Microsoft. 

- Um browser pode abrir anexos protegidos quando os fornecedores de redes sociais e códigos de acesso Monouso são utilizados para autenticação com o Exchange Online e as novas capacidades de encriptação de mensagens do Office 365. 

|Plataformas para visualizar e editar documentos: <br />Word, Excel, PowerPoint|Método de autenticação:<br />Azure AD|Método de autenticação:<br />Conta Microsoft|
|---------------|----------|-----------|-----------|
|Windows|Sim [[1]](#footnote-1)|Sim [[2]](#footnote-2)|
|iOS|Sim [[1]](#footnote-1)|Não|
|Android|Sim [[1]](#footnote-1)|Não|
|MacOS|Sim [[1]](#footnote-1)|Não|

###### <a name="footnote-1"></a>Nota de rodapé 1
Suporta contas de utilizador, grupos com capacidade de correio eletrónico, todos os membros. Contas de utilizador e grupos com capacidade de correio eletrónico podem incluir as contas de convidado. Todos os membros excluem contas de convidado.

###### <a name="footnote-2"></a>Nota de rodapé 2
Suporta atualmente aplicações do Office 365 (clique-e-use) apenas.




## <a name="next-steps"></a>Passos Seguintes

Ver outros [as configurações de exemplo](configure-policy-protection.md#example-configurations) para etiquetas aplicar a proteção para cenários comuns. Este artigo também contém mais detalhes sobre as definições de proteção.

Para obter mais informações sobre as opções e definições que pode configurar para a etiqueta, consulte [política de configuração do Azure Information Protection](configure-policy.md). 

A etiqueta que foi configurada neste artigo também cria um modelo de proteção com o mesmo nome. Se tiver aplicações e serviços que se integram nos modelos de proteção do Azure Information Protection, que eles possam aplicar este modelo. Por exemplo, as soluções DLP e as regras de fluxo de correio. Outlook na web apresenta automaticamente modelos de proteção da política global do Azure Information Protection. 





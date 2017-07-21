---
title: "Ajudar os utilizadores a proteger ficheiros com o Azure RMS – AIP"
description: "Informações para fornecer orientações a utilizadores, administradores e suporte técnico após ter implementado e configurado o serviço Azure Rights Management do Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/18/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 58f9a6ff-4121-4c8c-9865-1bb290604ad2
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 8bc262e8f79b0c0485104b5bb0152dd0609c35c5
ms.sourcegitcommit: 1c3ebf4ad64b55db4fec3ad007fca71ab7d38c02
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/18/2017
---
# <a name="helping-users-to-protect-files-by-using-the-azure-rights-management-service"></a>Ajudar os utilizadores a proteger ficheiros com o serviço Azure Rights Management

>*Aplica-se a: Azure Information Protection, Office 365*

Após ter implementado e configurado o Azure Information Protection para a sua organização, forneça ajuda e orientação para utilizadores, administradores e o suporte técnico:

-   **Informações do utilizador final:**

    Informe os utilizadores sobre como e quando proteger documentos e e-mails que contêm informações confidenciais. Sempre que possível, indique estas informações para os seus fluxos de trabalho existentes para que possam incorporar os passos adicionais a um processo já familiar em vez de introduzir processos novos. Certifique-se de que lhes transmite os benefícios (e os riscos) específicos da sua empresa, bem como orientações para quando devem proteger ficheiros e e-mails. Se tiver configurado [modelos personalizados](configure-custom-templates.md), forneça instruções sobre qual deve selecionar se o nome do modelo e a descrição não forem suficientes para escolherem o correto.

    > [!TIP]
    > Vídeos de exemplo para os utilizadores finais:
    >
    > -   [Experiência de utilizador do Azure RMS](http://channel9.msdn.com/Series/Information-Protection/Azure-RMS-user-experience)
    > -   [Revogação e Controlo de Documentos do Azure RMS](http://channel9.msdn.com/Series/Information-Protection/Azure-RMS-Document-Tracking-and-Revocation)

-   **Informações de administrador:**

    Algumas aplicações aplicam automaticamente a proteção de informações através da utilização de políticas e de definições que os administradores configuram. Para estas aplicações, poderá ter de fornecer instruções aos outros administradores que gerem estas aplicações e serviços. Para obter mais informações, veja [Como é que as aplicações suportam o serviço Azure Rights Management](../understand-explore/applications-support.md) e [Configurar aplicações para o serviço Azure Rights Management](configure-applications.md).

-   **Informações do suporte técnico:**

    
    Se os utilizadores estiverem a executar o cliente do Azure Information Protection, os assistentes de suporte técnico poderão pedir-lhes para utilizar a opção **Ajuda e Comentários**, **Executar Diagnósticos** e, em seguida, repor o cliente. No entanto, a reposição não termina a sessão do utilizador nem reinicia o cliente, além de não proceder à remediação automática.

    Se existirem pedidos legítimos para ter acesso de direitos totais a documentos protegidos, garanta que o suporte técnico tem processos para fazer este pedido de acesso através da [funcionalidade de superutilizador](configure-super-users.md) do Azure Rights Management. Por exemplo, estes pedidos poderão ser do departamento jurídico ou de um gestor após um funcionário ter saído da organização, 

    Além disso, alguns dos problemas típicos que os utilizadores poderão comunicar incluem as seguintes categorias:

    -   **Ajuda com o início de sessão:**

        Poderá ser pedido aos utilizadores que introduzam credenciais quando o serviço Azure Rights Management tiver de autenticar um utilizador e não puder utilizar credenciais em cache. As credenciais necessárias são a conta escolar ou profissional e a palavra-passe do utilizador que estão associadas ao seu inquilino do Office 365 ou ao inquilino do Azure Active Directory. As credenciais necessárias não são uma conta Microsoft (anteriormente, Microsoft Live ID) nem a respetiva conta de e-mail pessoal, uma vez que estas contas não são atualmente suportadas pelo serviço Azure Rights Management. Proporcione aos utilizadores e ao suporte técnico instruções sobre a conta a utilizar quando for pedido aos utilizadores que introduzam credenciais quando utilizarem aplicações com o serviço Azure Rights Management.

    -   **Problemas ao proteger ou ao consumir conteúdos:**

        Certifique-se de que os utilizadores têm as instruções adequadas para as aplicações que utilizam e que estão a utilizar aplicações e dispositivos suportados pelo serviço Azure Rights Management. Para obter mais informações sobre as aplicações e os dispositivos suportados, veja [Requisitos do Azure Rights Management](../get-started/requirements-azure-rms.md).

        A autenticação e a autorização dependem de contas e grupos do Azure Active Directory. Para confirmar que um utilizador ou um grupo específico pode ser autorizado a consumir conteúdo protegido, utilize as verificações em [Preparar os utilizadores e os grupos do Azure Information Protection](../plan-design/prepare.md).

        Caso os utilizadores comuniquem que podem abrir conteúdo protegido, mas não têm os direitos necessários, o problema poderá ser que o utilizador não está no grupo correto que foi configurado para um modelo do Rights Management. Ou que o [modelo tem de ser reconfigurado](configure-policy-template.md) para o utilizador ou o grupo. 
        
        Se os direitos dos utilizadores não forem os esperados, verifique a respetiva descrição e qualquer implementação específica da aplicação na [tabela de direitos de utilização](../deploy-use/configure-usage-rights.md#usage-rights-and-descriptions).

Utilize as secções seguintes para obter informações específicas de aplicações para ajudar os utilizadores a proteger e-mails e documentos confidenciais.

## <a name="using-information-protection-with-the-azure-information-protection-client"></a>Utilizar a proteção de informações com o cliente do Azure Information Protection
Caso os utilizadores tenham o Office 2010, o cliente do Azure Information Protection (ou a aplicação mais antiga, a aplicação de partilha RMS) é preciso para proteger e consumir documentos e e-mails protegidos. No entanto, o cliente do Azure Information Protection é também recomendado para todos os computadores e dispositivos móveis.

Para além de tornar mais fácil para os utilizadores protegerem documentos e e-mails importantes, o cliente do Azure Information Protection permite-lhes controlarem os documentos que protegeram. Os documentos rastreados podem também ser revogados se os utilizadores anteriormente autorizados já não puderem ter acesso aos mesmos.

Para obter instruções sobre como utilizar este cliente para computadores Windows, veja o [Guia de utilizador do cliente do Azure Information Protection](../rms-client/client-user-guide.md).


## <a name="using-information-protection-with-office-365-office-2016-or-office-2013"></a>Utilizar a proteção de informações com o Office 365, Office 2016 ou Office 2013
Se estiver a utilizar o serviço Azure Rights Management e não tiver instalado o cliente do Azure Information Protection, os utilizadores não veem a barra do Azure Information Protection nas suas aplicações de ambiente de trabalho do Office, o botão **Proteger** no friso ou **Classificar e proteger** do Explorador de Ficheiros. Estas adições tornam mais fácil para os utilizadores protegerem documentos e e-mails. Estes utilizadores têm de seguir instruções semelhantes aos passos que se seguem.

> [!TIP]
> Para encontrar a ajuda específica da aplicação e instruções para utilizar a proteção de informações com estas aplicações, pesquise a **IRM** e o nome e a versão da aplicação.

#### <a name="to-protect-a-document-in-word-2013"></a>Para proteger um documento no Word 2013

1.  No Microsoft Word, crie um documento.

2.  No menu **Ficheiro**, clique em **Informações**, em **Proteger Documento**e, de seguida, em **Restringir Acesso**.

3. Selecione um modelo para aplicar rapidamente os direitos de utilização adequados ou selecione **Restringir Acesso** e selecione os direitos de utilização.

    > [!NOTE]
    > Se tiver não utilizado anteriormente o Rights Management no seu computador, a opção **Restringir Acesso** estabelece ligação ao serviço [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] e são pedidas as credenciais para configurar o cliente IRM do Office. Em seguida, pode escolher um modelo ou os direitos de utilização.

3.  Guarde o documento.

Quando outras pessoas abrirem o documento, primeiro são autenticadas. Se não estiverem autorizadas a abrir o documento, o documento não abre. Se estiverem autorizadas a abrir o documento, este abre-se com os [direitos de utilização](../deploy-use/configure-usage-rights.md) restrita que foram especificados para esse utilizador. 

Por exemplo, um direito de utilização Ver Apenas não permite que o utilizador edite ou guarde o documento, mesmo que primeiro seja copiado para outra localização. 

Os direitos de utilização são apresentados na parte superior do documento, através de uma faixa de restrição. A faixa pode apresentar as permissões que são aplicadas ao documento ou pode disponibilizar uma ligação para as mostrar.

#### <a name="to-protect-an-email-message-using-outlook-2013-and-exchange-online"></a>Para proteger uma mensagem de e-mail através do Outlook 2013 e do Exchange Online

1.  No Outlook, crie uma mensagem de e-mail endereçada a um destinatário da sua organização.

2.  No separador **OPÇÕES**, clique em **Permissão** e selecione uma opção. Por exemplo: **Não Reencaminhar**, **&lt;Nome da Empresa&gt; – Confidencial** ou **&lt;Nome da Empresa&gt; – Apenas Visualização Confidencial**.

3.  Envie a mensagem.

Tal como na visualização de um documento protegido, quando os destinatários abrem a mensagem de e-mail protegida, primeiro são autenticados. Se estiverem autorizados a ver a mensagem de e-mail, esta abre-se com os [direitos de utilização](../deploy-use/configure-usage-rights.md) restrita que foram especificados para esse utilizador. 

Por exemplo, se a mensagem de e-mail estiver protegida através da opção **Não Reencaminhar**, o botão Reencaminhar no friso não está disponível.

#### <a name="to-protect-an-email-message-using-outlook-on-the-web"></a>Para proteger uma mensagem de e-mail através do Outlook na Web

1.  Através do Outlook na Web, crie uma mensagem de e-mail endereçada a um destinatário da sua organização.

2.  Clique em **…**, clique em **definir permissão** e selecione uma opção. Por exemplo: **Não Reencaminhar**, **Não Responder a Todos**, **&lt;Nome da Empresa&gt; – Confidencial** ou **&lt;Nome da Empresa&gt; – Apenas Visualização Confidencial**.

3.  Envie a mensagem.

Tal como na visualização de um documento protegido, quando os destinatários abrem a mensagem de e-mail, primeiro são autenticados. Se estiverem autorizados a ver a mensagem de e-mail, esta abre-se com os [direitos de utilização](../deploy-use/configure-usage-rights.md) restrita que foram especificados para esse utilizador. 

Por exemplo, se tiver selecionado **Não Responder a Todos**, a opção **RESPONDER A TODOS** na janela da mensagem não está disponível.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


---
title: Ajudar os utilizadores a proteger ficheiros com o Azure RMS – AIP
description: Informações para fornecer orientações a utilizadores, administradores e suporte técnico após ter implementado e configurado o serviço Azure Rights Management do Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/21/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 58f9a6ff-4121-4c8c-9865-1bb290604ad2
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 0243961b4dfdf3bb8c8b04059793098b26880615
ms.sourcegitcommit: aae04d78ff301921a4e29ac23bd932fb24a83dbe
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/22/2018
ms.locfileid: "34444270"
---
# <a name="helping-users-to-protect-files-by-using-the-azure-rights-management-service"></a>Ajudar os utilizadores a proteger ficheiros com o serviço Azure Rights Management

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Após ter implementado e configurado o Azure Information Protection para a sua organização, forneça ajuda e orientação para utilizadores, administradores e o suporte técnico:

-   **Informações do utilizador final**
    
    Informe os utilizadores sobre como e quando proteger documentos e e-mails que contêm informações confidenciais. Sempre que possível, indique estas informações para os seus fluxos de trabalho existentes para que possam incorporar os passos adicionais a um processo já familiar em vez de introduzir processos novos. Certifique-se de que lhes transmite os benefícios (e os riscos) específicos da sua empresa, bem como orientações para quando devem proteger ficheiros e e-mails. Se tiver configurado [modelos](configure-policy-templates.md), fornecer instruções sobre qual para selecionar se o nome do modelo e a descrição não é suficiente para escolherem o correto.
    
    > [!TIP]
    > Vídeos de exemplo para os utilizadores finais:
    > -   [Proteção de informações do Microsoft Azure](https://youtu.be/ToShAUdlrPo?list=PL8nfc9haGeb6qSm1kLU8n3Zqg398764h5)
    > -   [Revogação e Controlo de Documentos do Azure RMS](http://channel9.msdn.com/Series/Information-Protection/Azure-RMS-Document-Tracking-and-Revocation)

-   **Informações de administrador**
    
    Algumas aplicações aplicam automaticamente a proteção de informações através da utilização de políticas e de definições que os administradores configuram. Para estas aplicações, poderá ter de fornecer instruções aos outros administradores que gerem estas aplicações e serviços. 
    
    Para obter mais informações, veja [Como é que as aplicações suportam o serviço Azure Rights Management](../understand-explore/applications-support.md) e [Configurar aplicações para o serviço Azure Rights Management](configure-applications.md).
    
-   **Informações do suporte técnico**
    
    Se os utilizadores têm o cliente Azure Information Protection, operadores do suporte técnico podem pedir-lhe utilizar o **ajuda e comentários** opção informações, tais como se a edição do Office não é possível suportar a proteção e, atualmente assinada na conta de utilizador. Também pode utilizar esta opção para recolher ficheiros de registo e repor o cliente. Para obter mais informações, consulte o Guia do administrador: [instalar verificações e a resolução de problemas](../rms-client/client-admin-guide.md#installation-checks-and-troubleshooting).
    
    Se existirem pedidos legítimos para ter acesso de direitos totais a documentos protegidos, garanta que o suporte técnico tem processos para fazer este pedido de acesso através da [funcionalidade de superutilizador](configure-super-users.md) do Azure Rights Management. Por exemplo, poderão ser estes pedidos de Departamento jurídico ou um gestor depois de um funcionário ter saído da organização.
    
    Além disso, alguns dos problemas típicos que os utilizadores poderão comunicar incluem as seguintes categorias:
    
    - **Ajuda a iniciar sessão**
        
        Poderá ser pedido aos utilizadores que introduzam credenciais quando o serviço Azure Rights Management tiver de autenticar um utilizador e não puder utilizar credenciais em cache. As credenciais necessárias são normalmente para o utilizador trabalho ou conta profissional e a palavra-passe que está associado ao seu inquilino do Office 365 ou inquilino do Azure Active Directory. Embora o serviço Azure Rights Management pode autenticar contas do Azure AD, algumas aplicações podem também abrir conteúdos protegidos quando uma conta Microsoft é utilizada para autenticação. [Mais informações](../get-started/secure-collaboration-documents.md#supported-scenarios-for-opening-protected-documents) 
        
        Forneça aos utilizadores e o suporte técnico com instruções sobre a conta a utilizar quando os utilizadores forem pedidos as credenciais quando têm as aplicações que utilizam o serviço Azure Rights Management.
        
    - **Problemas ao proteger ou consumir conteúdo**
        
        Certifique-se de que os utilizadores têm as instruções adequadas para as aplicações que utilizam e que utilizam aplicações e dispositivos que são suportados pelo serviço do Azure Rights Management. Para obter mais informações sobre as aplicações e os dispositivos suportados, veja [Requisitos do Azure Rights Management](../get-started/requirements-azure-rms.md).
        
        Para confirmar que um grupo ou utilizador específico pode ser autorizado por Azure Active Directory para proteger ou consumir conteúdo protegido, utilize as verificações de verificação no [preparar os utilizadores e grupos do Azure Information Protection](../plan-design/prepare.md).
        
        Se os utilizadores comunicarem que podem abrir conteúdo protegido, mas não têm os direitos que necessitam, o problema poderá ser que o utilizador não está no grupo correto que esteja configurado para um modelo de Rights Management. Em alternativa, o problema poderá ser que o [modelo tem de ser reconfigurado](configure-policy-templates.md) para o utilizador ou grupo. 
        
        Se os direitos de utilizadores não estão como esperado, verifique a descrição dos direitos e de implementação específicos da aplicação do [tabela de direitos de utilização](../deploy-use/configure-usage-rights.md#usage-rights-and-descriptions).

Utilize as secções seguintes para informações específicas de aplicações para ajudar os utilizadores a proteger documentos e e-mails.

## <a name="using-information-protection-with-the-azure-information-protection-client"></a>Utilizar a proteção de informações com o cliente do Azure Information Protection

Caso os utilizadores tenham o Office 2010, o cliente do Azure Information Protection (ou a aplicação mais antiga, a aplicação de partilha RMS) é preciso para proteger e consumir documentos e e-mails protegidos. No entanto, o cliente Azure Information Protection também é recomendado para todos os computadores e dispositivos móveis que suportem este serviço.

Para além de tornar mais fácil para os utilizadores a proteger documentos e e-mails, o cliente Azure Information Protection permite aos utilizadores controlarem os documentos que protegeram. Os documentos rastreados podem também ser revogados se os utilizadores anteriormente autorizados já não puderem ter acesso aos mesmos.

Para obter instruções sobre como utilizar este cliente para computadores Windows, veja o [Guia de utilizador do cliente do Azure Information Protection](../rms-client/client-user-guide.md).


## <a name="using-information-protection-with-office-365-office-2016-or-office-2013"></a>Utilizar a proteção de informações com o Office 365, Office 2016 ou Office 2013
Se estiver a utilizar o serviço Azure Rights Management e não tiver instalado o cliente Azure Information Protection, os utilizadores veem a barra do Azure Information Protection nas suas aplicações de ambiente de trabalho do Office. Também não veem o **proteger** botão no Friso, ou **classificar e proteger** do Explorador de ficheiros. Estas adições tornam mais fácil para os utilizadores protegerem documentos e e-mails. Estes utilizadores têm de seguir instruções semelhantes aos passos que se seguem.

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

1.  No Outlook, crie uma mensagem de correio é endereçada a um destinatário da sua organização.

2.  No separador **OPÇÕES**, clique em **Permissão** e selecione uma opção. Por exemplo: **não reencaminhar**, ou  **\<nome da empresa > - confidencial**, ou  **\<nome da empresa >-apenas visualização confidencial**.

3.  Envie a mensagem.

Tal como na visualização de um documento protegido, quando os destinatários abrem a mensagem de e-mail protegida, primeiro são autenticados. Se estiverem autorizados a ver a mensagem de e-mail, esta abre-se com os [direitos de utilização](../deploy-use/configure-usage-rights.md) restrita que foram especificados para esse utilizador. 

Por exemplo, se a mensagem de e-mail estiver protegida através da opção **Não Reencaminhar**, o botão Reencaminhar no friso não está disponível.

#### <a name="to-protect-an-email-message-using-outlook-on-the-web"></a>Para proteger uma mensagem de e-mail através do Outlook na Web

1.  Através do Outlook na Web, crie uma mensagem de e-mail endereçada a um destinatário da sua organização.

2.  Clique em **…**, clique em **definir permissão** e selecione uma opção. Por exemplo: **não reencaminhar** ou **não responder a todos**. Ou,  **\<da empresa Name > - confidencial** ou  **\<da empresa nome > – confidencial ver apenas**.

3.  Envie a mensagem.

Tal como na visualização de um documento protegido, quando os destinatários abrem a mensagem de e-mail, primeiro são autenticados. Se estiverem autorizados a ver a mensagem de e-mail, esta abre-se com os [direitos de utilização](../deploy-use/configure-usage-rights.md) restrita que foram especificados para esse utilizador. 

Por exemplo, se tiver selecionado **Não Responder a Todos**, a opção **RESPONDER A TODOS** na janela da mensagem não está disponível.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


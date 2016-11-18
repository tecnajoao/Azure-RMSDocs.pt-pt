---
title: "Cenário – Proteger alguns dos seus ficheiros mais importantes | Azure Information Protection"
description: "Este cenário e a documentação do utilizador associada utilizam o Azure Rights Management para proteger de forma manual e personalizada alguns ficheiros que tenha identificado como sendo os mais importantes e que requerem o mais elevado nível de proteção contra acesso não autorizado."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 10/05/2016
ms.topic: get-started-article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 95f1844a-612c-4e67-bbe6-4b6b92295221
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9d8354f2d68f211d349226970fd2f83dd0ce810b
ms.openlocfilehash: ad75734c28c51ac68697f96e0e50a5d90314b76e


---

# <a name="scenario-secure-your-most-few-valuable-files"></a>Cenário – Proteger alguns dos seus ficheiros mais importantes

>*Aplica-se a: Azure Information Protection, Office 365*

Este cenário e a documentação do utilizador associada utilizam a tecnologia do Azure Rights Management do Azure Information Protection para proteger de forma manual e personalizada alguns ficheiros que tenha identificado como sendo os mais importantes e que requerem o mais elevado nível de proteção contra acesso não autorizado. Normalmente, são ficheiros a que apenas algumas pessoas devem conseguir aceder. Por exemplo, instruções da receita do produto alimentar de marca da sua empresa ou planos de aquisição que não devem ser tornados públicos antes de uma data especificada.

As instruções aplicam-se às seguintes circunstâncias:

-   Identificou o pequeno conjunto de ficheiros que pretende proteger.

-   Os ficheiros estão num dos formatos de ficheiro do Office que suportam o Rights Management. Se os ficheiros estiverem noutros formatos de ficheiro (por exemplo, ficheiros CAD), certifique-se de que esses formatos suportam o Azure RMS e de que implementa aplicações que suportam nativamente o Azure RMS. Para obter mais informações, consulte [Como as Aplicações Suportam o serviço Azure Rights Management](../understand-explore/applications-support.md).

-   Os ficheiros contêm informações delicadas e altamente confidenciais que devem estar acessíveis apenas para algumas pessoas.

-   Solicitar uma ligação à Internet para autorizar o acesso de cada indivíduo a um ficheiro é um compromisso aceitável para estas pessoas, uma vez que proporciona uma maior segurança.

-   Estas pessoas não necessitam de partilhar estas informações com outros, mas podem modificar as informações e guardar as alterações.

-   O administrador deve poder controlar quem está a aceder aos ficheiros e quando, bem como revogar o acesso, se necessário.

## <a name="deployment-instructions"></a>Instruções de implementação
![Instruções do administrador para a Implementação Rápida do Azure RMS](../media/AzRMS_AdminBanner.png)

Certifique-se de que os seguintes requisitos são cumpridos e, em seguida, siga as instruções dos procedimentos de suporte antes de avançar para a documentação do utilizador.

## <a name="requirements-for-this-scenario"></a>Requisitos para este cenário
Para este cenário, é necessário que os seguintes aspetos estejam implementados:

|Requisito|Se precisar de mais informações|
|---------------|--------------------------------|
|Preparou contas e grupos para o Office 365 ou o Azure Active Directory:<br /><br />- Um grupo com capacidade de correio com o nome **Acesso privilegiado**, que inclui as poucas pessoas que devem ter acesso a estes documentos altamente confidenciais<br /><br />- Um grupo com capacidade de correio com o nome **Gestores de Conformidade de TI**, que inclui as pessoas cujo trabalho inclui a Deteção de Dados Eletrónicos, a monitorização e a auditoria<br /><br />- Um grupo com capacidade de correio com o nome **Administradores de RMS** e todos os administradores que irão configurar o Azure RMS são membros deste grupo|[Preparação para o Azure Information Protection](../plan-design/deployment-roadmap.md)|
|O Azure Rights Management está ativado|[Ativar o Azure Rights Management](../deploy-use/activate-service.md)|
|Configurou um modelo personalizado, tal como descrito a seguir|[Configurar modelos personalizados para o serviço Azure Rights Management](../deploy-use/configure-custom-templates.md)|
|A aplicação de partilha Rights Management está implementada no seu computador Windows, para que possa proteger estes ficheiros no local, conforme descrito na secção seguinte|[Transferir e instalar a aplicação de partilha Rights Management](../rms-client/install-sharing-app.md)|
|Os utilizadores autorizados têm o Office 2013 como a versão mínima|Se os utilizadores tiverem o Office 2010, também têm de instalar a aplicação de partilha Rights Management.|
|A sua subscrição do Azure Information Protection inclui controlo de documentos|Se a sua subscrição não incluir a revogação e o controlo de documentos, não poderá utilizar o site de controlo de documentos para ver quem está a aceder a estes documentos e revogar o acesso, se necessário. Neste caso, compre uma subscrição que suporte o controlo de documentos ou aceite esta limitação. Também poderá considerar as funcionalidades de [registo de utilização](../deploy-use/log-analyze-usage.md) do serviço Azure Rights Management, que podem fornecer informações tais como quem acedeu a cada ficheiro e quando o fez, para o ajudar a detetar um potencial comportamento suspeito.<br /><br />Consulte a [lista de funcionalidades](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-features) no site do Azure Information Protection.|

### <a name="to-configure-the-custom-template"></a>Para configurar o modelo personalizado

1.  No portal clássico do Azure: crie um novo modelo personalizado para o Azure Rights Management que contenha estes valores e definições:

    -   Nome: **Acesso privilegiado**

    -   Direitos: conceda ao grupo **Acesso privilegiado** com capacidade de correio direitos de **Coautor**

    -   Âmbito: selecione o grupo **Acesso privilegiado** com capacidade de correio, o grupo **Gestores de Conformidade de TI** com capacidade de correio e o grupo **Administradores de RMS** com capacidade de correio.

    -   Acesso offline: **O conteúdo está disponível apenas com uma ligação à Internet**

2.  Publique o novo modelo.

### <a name="to-protect-the-files-inplace"></a>Para proteger os ficheiros no local

1.  No Explorador de Ficheiros, navegue para a primeira pasta que contém os ficheiros a proteger:

    -   Se pretender proteger todos os ficheiros na pasta, selecione a pasta.

    -   Se pretender proteger apenas alguns ficheiros na pasta, selecione todos os ficheiros a proteger.

2.  Clique com o botão direito do rato, selecione **Proteger com RMS** e, em seguida, selecione **Proteger no local**.

3.  Selecione **Acesso privilegiado**.

4.  Poderão ser-lhe pedidas as credenciais. Aguarde que os ficheiros sejam protegidos e, em seguida, clique em **Fechar** quando for apresentada a página **os ficheiros foram protegidos**.

5.  Se tiver mais ficheiros a proteger noutras pastas, repita os passos 1 a 4 para cada pasta.

Para obter mais informações sobre como proteger ficheiros no local, consulte [Proteger um ficheiro num dispositivo (proteger no local) através da aplicação de partilha Rights Management](../rms-client/sharing-app-protect-in-place.md)

> [!TIP]
> Se o número de ficheiros que quer proteger for demasiado elevado para executar este processo manual, considere utilizar a [ferramenta de Proteção RMS](https://www.microsoft.com/en-us/download/details.aspx?id=47256) para proteger os ficheiros em volume com o modelo.

### <a name="to-monitor-and-if-necessary-revoke-access-to-the-files"></a>Para monitorizar e, se necessário, revogar o acesso aos ficheiros

1.  No Explorador de Ficheiros, clique com o botão direito do rato no ficheiro protegido, selecione **Proteger com RMS** e, em seguida, selecione **Controlar a Utilização**.

2.  Se lhe for solicitado, inicie sessão para aceder ao site de controlo de documentos.

3.  Verifique quem acedeu a esse ficheiro e aos outros ficheiros que protegeu, prestando especial atenção a tentativas falhadas caso indiquem um comportamento suspeito. Se considerar adequado, pode revogar o acesso a cada ficheiro.

## <a name="user-documentation-instructions"></a>Instruções da documentação do utilizador
Não existem instruções específicas a dar aos utilizadores para este cenário, uma vez que estes ficheiros não requerem qualquer ação especial por parte deles. Os ficheiros foram protegidos por si e serão monitorizados por si. No entanto, poderá ter de informar os utilizadores e os canais de suporte sobre os ficheiros que estão protegidos e como esta proteção pode restringir a utilização dos documentos. Por exemplo, se um utilizador autorizado não tiver ligação à Internet, não conseguirá abrir o ficheiro.

Utilizando o modelo seguinte, copie e cole o anúncio numa comunicação destinada aos utilizadores finais e efetue estas alterações:

1.  Forneça os nomes reais dos ficheiros ou utilize uma referência clara que os utilizadores autorizados consigam compreender.

2.  Substitua *&lt;detalhes de contacto&gt;* por instruções sobre a forma como estes utilizadores podem contactar o suporte técnico ou o departamento de TI com um canal de suporte escalado correspondente à importância destes documentos. Por exemplo, forneça um número de telefone com atendimento durante 24 horas por dia para as chamadas de suporte de elevada gravidade.

3.  Efetue quaisquer modificações adicionais que pretenda ao anúncio e, em seguida, envie-o aos utilizadores.

A documentação de exemplo mostra que aspeto este anúncio poderá ter para os utilizadores depois das personalizações.

![Modelo de documentação do utilizador para a Implementação Rápida do Azure RMS](../media/AzRMS_UsersBanner.png)

### <a name="it-announcement-protecting-ltorganization-namegts-top-secret-documents"></a>Anúncio de TI: proteger os documentos confidenciais da &lt;nome da organização&gt;
Os ficheiros seguintes estão agora sujeitos a um nível muito elevado de proteção, para que apenas os &lt;utilizadores restritos&gt; possam aceder a estes ficheiros e alterá-los. Para ajudar a protegê-los do acesso não autorizado, a aplicação solicitará automaticamente autorização sempre que abrir estes ficheiros, pelo que agora tem de ter uma ligação à Internet para os abrir, além de poderem ser-lhe pedidas as suas credenciais:

-   &lt;documento confidencial, tipo ou localização 1&gt;

-   &lt;documento confidencial, tipo ou localização 2&gt;

-   &lt;documento confidencial, tipo ou localização 3&gt;

**Precisa de ajuda?**

-   Se não conseguir aceder a estes ficheiros ou se reparar em alterações suspeitas aos mesmos, &lt;ação e detalhes de contacto&gt;.

#### <a name="example-customized-user-documentation"></a>Exemplo de documentação do utilizador personalizada
![Exemplo de documentação do utilizador para a Implementação Rápida do Azure RMS](../media/AzRMS_ExampleBanner.png)

##### <a name="it-announcement-protecting-vanarsdels-top-secret-documents"></a>Anúncio de TI: proteger os documentos confidenciais da VanArsdel
Os ficheiros seguintes estão agora sujeitos a um nível muito elevado de proteção, para que apenas as pessoas incluídas na linha Para desta mensagem de e-mail possam aceder a estes ficheiros e alterá-los. Para ajudar a protegê-los do acesso não autorizado, as aplicações solicitarão automaticamente autorização sempre que abrir estes ficheiros, pelo que agora tem de ter uma ligação à Internet para os abrir, além de poderem ser-lhe pedidas as suas credenciais:

-   Especificações da conceção para o nome de código “Mercúrio”

-   Especificações da conceção para o nome de código “Júpiter”

-   Especificações da conceção para o nome de código “Saturno”

-   Especificações da conceção para o nome de código “Neptuno”

**Precisa de ajuda?**

-   Se não conseguir aceder a estes ficheiros ou se reparar em alterações suspeitas aos mesmos, ligue para a linha do suporte disponível 24 horas por dia que o Departamento de TI lhe indicou numa mensagem de e-mail protegida.




<!--HONumber=Nov16_HO2-->



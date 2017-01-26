---
title: "Como os utilizadores se inscrevem no RMS para indivíduos | Azure Information Protection"
description: "Instruções de inscrição nesta conta gratuita e informações técnicas sobre o funcionamento deste processo."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: a60731bd-f78d-4f00-bb3e-354637b312ab
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c8ffebad1130c8ba084c0feb83aa3ec54692ad54
ms.openlocfilehash: 1de26925961ad560cb9aa86ebc16f7354c7cff1f


---

# <a name="how-users-sign-up-for-rms-for-individuals"></a>Como os utilizadores se inscrevem no RMS para indivíduos

>*Aplica-se a: Azure Information Protection*

Para se inscrever nesta conta gratuita, efetue o seu pedido ao aceder à [página do Microsoft Azure Information Protection](https://portal.office.com/signup?sku=rms&ru=https%3A%2F%2Fportal.azurerms.com%2F%23%2Fdownload) e indicar o seu endereço de e-mail profissional. A forma mais comum de ser direcionado para esta página de inscrição é ao receber uma mensagem de e-mail com um anexo protegido que contém instruções de inscrição. Irá receber uma resposta por e-mail da Microsoft e, em seguida, poderá concluir o processo de inscrição ao introduzir detalhes para criar a sua conta. Quando o processo for concluído, irá ver uma página onde pode transferir a aplicação de partilha para vários dispositivos, uma ligação para o guia de utilizador e uma ligação para a lista atual de aplicações que suportam de forma nativa a proteção da Gestão de Direitos. 

## <a name="to-sign-up-for-rms-for-individuals"></a>Para se inscrever no RMS para indivíduos

1.  Num computador Windows ou Mac ou num dispositivo móvel, aceda à [página do Microsoft Azure Information Protection](https://portal.office.com/signup?sku=rms&ru=https%3A%2F%2Fportal.azurerms.com%2F%23%2Fdownload).

2.  Escreva o endereço de e-mail que utiliza para a sua organização, tal como **janetm@contoso.com** ou **p.dover@fabrikam.com**.

    > [!IMPORTANT]
    > As contas de e-mail pessoais não são suportadas, como tal, não introduza uma conta Microsoft (anteriormente denominada uma conta Microsoft Live ID) ou outra conta pessoal que poderá utilizar em casa através do seu fornecedor de Internet.

3.  Clique em **Inscrever-se**.

    A Microsoft utiliza o seu endereço de e-mail para verificar se a sua organização já tem uma [subscrição paga para o Azure Information Protection](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-pricing) ou uma [subscrição do Office 365 que inclui proteção de dados através do Azure Rights Management](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf). Se for esse o caso, não precisa do RMS para indivíduos, pelo que irá iniciar sessão imediatamente e a inscrição self-service para o RMS para indivíduos é cancelada. Se não for encontrada uma subscrição paga, irá continuar para o passo seguinte.

4.  Aguarde que uma mensagem de e-mail de confirmação seja enviada para o endereço que especificou. Esta será enviada pela equipa do Office 365 (support@email.microsoftonline.com) com o assunto **Concluir a sua inscrição no Microsoft Azure Information Protection**.

5.  Quando receber o e-mail, clique em **Sim, sou eu** para verificar o seu endereço de e-mail e concluir o processo de inscrição.

6.  Verá a página **Mais uma coisa...**, onde pode fornecer os detalhes da sua conta. Escreva o seu nome próprio, o seu apelido, introduza e confirme uma palavra-passe à sua escolha e, em seguida, clique em **Iniciar**.

7. Assim que a sua conta for criada, verá uma nova página do Microsoft Rights Management onde poderá transferir e instalar a aplicação de partilha ou clicar na ligação [Mais informações](../rms-client/sharing-app-user-guide.md) para ler o guia de utilizador da aplicação de partilha.

Agora, a sua conta está criada, está pronto para começar a proteger ficheiros e a ler ficheiros que outros utilizadores protegeram. Se lhe for pedido para iniciar sessão para proteger ou ler ficheiros protegidos, introduza o mesmo endereço de e-mail e palavra-passe que utilizou para criar a conta do RMS para indivíduos.

## <a name="technical-overview-of-the-sign-up-process"></a>Descrição geral técnica do processo de inscrição
O RMS para indivíduos utiliza um processo de inscrição self-service que também é utilizado por outros serviços que utilizam a tecnologia baseada na nuvem da Microsoft para autenticar os utilizadores.

Isto é o que acontece em segundo plano quando um utilizador se inscreve no RMS para indivíduos e a respetiva organização não tem uma subscrição do Office 365 ou do Azure e, por conseguinte, nenhum diretório no Azure para autenticar os utilizadores:

1.  Quando o primeiro utilizador de uma organização solicita uma subscrição do RMS para indivíduos, o nome de domínio fornecido no respetivo endereço de e-mail é verificado para ver se já está associado a um inquilino do Azure. Se não houver um inquilino existente, é criado automaticamente um novo inquilino e um diretório do Azure para a organização, que contém uma conta para este primeiro utilizador. Ao invés de uma subscrição paga do Azure, esta primeira conta não é um administrador global, mas um utilizador padrão. A nova conta utiliza o endereço de e-mail e a palavra-passe que o utilizador forneceu.

    > [!NOTE]
    > Alguns nomes de domínio não podem ser utilizados para criar o diretório e, por conseguinte, não podem ser utilizados para o RMS para indivíduos.

    Se for encontrado um inquilino existente, este é verificado para ver se já tem uma subscrição do Azure RMS. Quando não é encontrada qualquer subscrição, é possível adicionar a subscrição do RMS para indivíduos gratuita.

2.  É concedida à organização a subscrição do RMS para indivíduos. Agora, este utilizador pode ser autenticado pelo Azure e pode, em seguida, proteger ficheiros e ler ficheiros que outras pessoas protegeram utilizando o Azure Rights Management. Para proteger e ler ficheiros protegidos, o utilizador tem de ter uma aplicação otimizada por RMS, tal como a [aplicação de partilha Rights Management](../rms-client/sharing-app-windows.md) gratuita.

3.  Quando o segundo utilizador da mesma organização solicita uma subscrição do RMS para indivíduos, é adicionada uma nova conta de utilizador ao diretório do Azure criado anteriormente, utilizando a subscrição do RMS para indivíduos da organização. Este segundo utilizador pode fazer tudo o que o primeiro utilizador podia fazer (proteger ficheiros e ler ficheiros protegidos), mas, além disso, estes dois utilizadores podem agora colaborar mais facilmente em segurança porque podem aplicar rapidamente modelos predefinidos a ficheiros que restringem o acesso a contas no diretório do Azure da sua organização.

4.  Os utilizadores subsequentes da mesma organização seguem o mesmo padrão, adicionando contas de utilizadores (quando novos utilizadores se inscrevem) ao diretório do Azure da sua organização. Quanto mais contas forem adicionadas ao diretório, mais utilizadores podem colaborar com colegas e parceiros de forma mais segura e impedir mais facilmente que as pessoas não autorizadas leiam os seus ficheiros quando não devem ter acesso aos mesmos.

Ao longo deste processo, não é cobrado qualquer valor à organização e não é necessário qualquer trabalho por parte do departamento de TI. No entanto, o departamento de TI pode optar por efetuar um dos seguintes procedimentos:

-   **Gerir as contas e o processo de inscrição**: os administradores de TI podem tornar-se proprietários das contas e diretórios criados automaticamente no Azure. Em seguida, podem gerir as contas através da implementação de soluções de integração de diretórios como o início de sessão único e a sincronização de palavras-passe. Em alternativa, podem impedir os utilizadores de criarem contas ou de se inscreverem no RMS para indivíduos.

    Para obter mais informações, consulte [Como os administradores podem controlar as contas criadas para o RMS para indivíduos](rms-for-individuals-take-control.md).

-   **Gerir a Gestão de Direitos**: os administradores de TI podem converter a subscrição do RMS para indivíduos da organização numa subscrição paga que inclui o Azure Rights Management. Ao fazê-lo, as contas e o diretório do Azure existentes são preservadas para uma transição sem problemas para utilizadores existentes que estavam a utilizar o RMS para indivíduos. Todos os ficheiros que os utilizadores protegeram anteriormente continuarão a estar protegidos com as mesmas políticas e as pessoas às quais foram concedidas permissões para utilizar os ficheiros continuarão a poder utilizar os ficheiros da mesma forma.

    Ao realizar este procedimento, a sua organização é beneficiada por poder integrar a Gestão de Direitos nos seus fluxos de trabalho, serviços e arquivos de dados. Além disso, já pode gerir a Gestão de Direitos porque tem controlo sobre a chave de inquilino da sua organização para o Azure Rights Management. Agora, pode realizar o seguinte:

    -   Configurar o Exchange e o SharePoint para suportar o Azure Rights Management, mesmo que estas estejam em execução no local. O Exchange e o SharePoint são nativamente suportados para os serviços online e são suportados por um conetor para os servidores no local. Para obter mais informações, consulte o seguinte:

        -   As secções do Exchange Online e do SharePoint Online de [Office 365: configuração para os clientes e os serviços online](../deploy-use/configure-office365.md)

        -   [Implementar o conetor Azure Rights Management](../deploy-use/deploy-rms-connector.md)

    -   Efetue a deteção de dados eletrónicos nos dados pertencentes à empresa para poder, se necessário, desencriptar ficheiros que foram protegidos através da Gestão de Direitos. Para obter mais informações, consulte [Configurar superutilizadores para o Azure Rights Management e serviços de deteção ou recuperação de dados](../deploy-use/configure-super-users.md).

    -   Registe toda a atividade da Gestão de Direitos, conforme utilizada na sua organização. Isto é extremamente útil porque não só pode monitorizar os ficheiros que estão a ser protegidos e quem está a aceder a esses ficheiros protegidos com êxito, como também pode identificar comportamentos potencialmente suspeitos de pessoas não autorizadas que estão a tentar aceder a ficheiros protegidos. Para obter mais informações, consulte [Registar e analisar a utilização do serviço Azure Rights Management](../deploy-use/log-analyze-usage.md).

    -   Forneça aos utilizadores a capacidade de controlar e revogar os seus documentos protegidos, se estas funcionalidades forem suportadas pela sua [Subscrição do Azure RMS](https://technet.microsoft.com/dn858608). Para obter mais informações, consulte [Controlar e revogar os ficheiros](../rms-client/sharing-app-track-revoke.md) no [Guia do utilizador da aplicação de partilha RMS](../rms-client/sharing-app-user-guide.md).

    -   Implemente uma solução "traga a sua própria chave" (BYOK) para que a chave do seu inquilino do Azure Rights Management seja gerada no local, de acordo com as políticas de TI, e seja transferida em segurança para a Microsoft através da utilização de um módulo de hardware de segurança (HSM). Para obter mais informações, consulte [Planear e implementar a sua chave de inquilino do Azure Information Protection](../plan-design/plan-implement-tenant-key.md).


## <a name="next-steps"></a>Passos seguintes
Consulte [Como os administradores podem controlar as contas criadas para o RMS para indivíduos](rms-for-individuals-take-control.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


<!--HONumber=Jan17_HO4-->



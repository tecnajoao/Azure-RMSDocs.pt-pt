---
title: "Como os utilizadores se inscrevem no RMS para indivíduos – AIP"
description: "Instruções de inscrição nesta conta gratuita e informações técnicas sobre o funcionamento deste processo."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/24/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: a60731bd-f78d-4f00-bb3e-354637b312ab
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: d1c45c2b97fb3f278a8ecd3ebe9fe37af3ea5d0f
ms.sourcegitcommit: 0fa5dd38c9d66ee2ecb47dfdc9f2add12731485e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2017
---
# <a name="how-users-sign-up-for-rms-for-individuals"></a>Como os utilizadores se inscrevem no RMS para indivíduos

>*Aplica-se a: Azure Information Protection*

Para se inscrever nesta conta gratuita, efetue o seu pedido ao aceder à [página do Microsoft Azure Information Protection](https://aka.ms/rms-signup) e indicar o seu endereço de e-mail profissional. A forma mais comum que o utilizador é direcionado para esta página de inscrição é se receber uma mensagem de e-mail com um anexo protegido. A mensagem de e-mail contém instruções sobre como inscrever-se. 

Quando seguir estas instruções, receberá uma mensagem de e-mail em resposta da Microsoft e, em seguida, conclua o processo de inscrição, introduzindo os detalhes para criar a sua conta. Quando estiver concluído, a página final apresenta ligações para transferir o cliente Azure Information Protection ou visualizador para diferentes dispositivos, uma ligação para o Guia do utilizador e uma ligação para uma lista atualizada das aplicações que suportam nativamente o proteção Rights Management. 

## <a name="to-sign-up-for-rms-for-individuals"></a>Para se inscrever no RMS para indivíduos

1.  Num computador Windows ou Mac ou num dispositivo móvel, aceda à [página do Microsoft Azure Information Protection](https://aka.ms/rms-signup).

2.  Escreva o endereço de e-mail que utiliza para a sua organização, tal como **janetm@contoso.com** ou **p.dover@fabrikam.com**.

    > [!IMPORTANT]
    > As contas de e-mail pessoais não são suportadas, como tal, não introduza uma conta Microsoft (anteriormente denominada uma conta Microsoft Live ID) ou outra conta pessoal que poderá utilizar em casa através do seu fornecedor de Internet.

3. Clique em **Inscrever-se**.

    A Microsoft utiliza o seu endereço de e-mail para verificar se a sua organização já tem um [subscrição do Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection-pricing) ou um [subscrição do Office 365 que inclui proteção de dados utilizando o Azure Rights Management](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf). Se não for encontrada qualquer uma destas subscrições, não precisa do RMS para indivíduos. Tem sessão iniciada imediatamente e a inscrição self-service para o RMS para indivíduos é cancelada. Se um destas subscrições não for encontrado, continue para o passo seguinte.

4. Aguarde que uma mensagem de e-mail de confirmação seja enviada para o endereço que especificou. Esta será enviada pela Equipa do Office 365 (support@email.microsoftonline.com) com o assunto **Concluir a sua inscrição no Microsoft Azure Information Protection**.

5. Quando receber o e-mail, clique em **Sim, que é-me** para verificar se o seu endereço de e-mail e concluir o processo de inscrição.

6. Verá a página **Mais uma coisa...**, onde pode fornecer os detalhes da sua conta. Escreva o seu nome próprio, o seu apelido, introduza e confirme uma palavra-passe à sua escolha e, em seguida, clique em **Iniciar**.

7. Quando é criada a sua conta, verá uma nova página do Microsoft Azure Information Protection onde pode transferir e instalar o cliente Azure Information Protection ou clique em de [Guia do utilizador](../rms-client/client-user-guide.md) ligação para instruções sobre como proceder para computadores Windows.

Agora, a sua conta está criada, está pronto para começar a proteger ficheiros e a ler ficheiros que outros utilizadores protegeram. Se lhe for pedido para iniciar sessão para proteger ou ler ficheiros protegidos, introduza o mesmo endereço de e-mail e palavra-passe que utilizou para criar a conta do RMS para indivíduos.

## <a name="technical-overview-of-the-sign-up-process"></a>Descrição geral técnica do processo de inscrição
RMS para indivíduos utiliza um processo de inscrição self-service que também é utilizado por outros serviços que utilizam a tecnologia de baseado na nuvem da Microsoft para autenticar os utilizadores.

Isto é o que acontece em segundo plano quando um utilizador se inscreve no RMS para indivíduos e a respetiva organização não tem uma subscrição do Office 365 ou do Azure e, por conseguinte, nenhum diretório no Azure para autenticar os utilizadores:

1. Quando o primeiro utilizador de uma organização solicita uma subscrição do RMS para indivíduos, o nome de domínio fornecido no respetivo endereço de e-mail é verificado para ver se já está associado a um inquilino do Azure. Se não houver um inquilino existente, é criado automaticamente um novo inquilino e um diretório do Azure para a organização, que contém uma conta para este primeiro utilizador. Ao contrário de uma subscrição de avaliação ou paga do Azure, esta primeira conta não é um administrador global, mas um utilizador padrão. A nova conta utiliza o endereço de e-mail e a palavra-passe que o utilizador forneceu.

    > [!NOTE]
    > Alguns nomes de domínio não podem ser utilizados para criar o diretório e, por conseguinte, não podem ser utilizados para o RMS para indivíduos.

    Se for encontrado um inquilino existente, este é verificado para ver se já tem uma subscrição do Azure Information Protection. Quando não é encontrada qualquer subscrição, é possível adicionar a subscrição do RMS para indivíduos gratuita.

2. É concedida à organização a subscrição do RMS para indivíduos. Agora, este possa ser autenticado pelo Azure e este utilizador, em seguida, pode proteger ficheiros e ler ficheiros que outras pessoas protegeram utilizando o serviço Azure Rights Management. Para proteger e ler ficheiros protegidos, o utilizador tem de ter uma aplicação otimizada por RMS, tal como aplicações do Office ou as livre [cliente Azure Information Protection](../rms-client/aip-client.md).

3. Quando o segundo utilizador da mesma organização solicita uma subscrição do RMS para indivíduos, é adicionada uma nova conta de utilizador ao diretório do Azure criado anteriormente, utilizando a subscrição do RMS para indivíduos da organização. Este segundo utilizador pode fazer tudo o que o primeiro utilizador podia fazer (proteger ficheiros e ler ficheiros protegidos). Mas, além disso, estes dois utilizadores podem agora mais facilmente colaborar em segurança porque podem aplicar rapidamente modelos predefinidos a ficheiros que restringem o acesso a contas no diretório do Azure da sua organização.

4. Os utilizadores subsequentes da mesma organização seguem o mesmo padrão, adicionar contas de utilizador ao diretório do Azure da organização, quando se inscrevem no. Quanto mais contas forem adicionadas ao diretório, mais utilizadores podem colaborar com colegas e parceiros de forma mais segura e impedir mais facilmente que as pessoas não autorizadas leiam os seus ficheiros quando não devem ter acesso aos mesmos.

Ao longo deste processo, não é cobrado qualquer valor à organização e não é necessário qualquer trabalho por parte do departamento de TI. No entanto, o departamento de TI pode optar por efetuar qualquer uma das seguintes ações:

- **Gerir as contas e o processo de inscrição**: os administradores de TI podem tornar-se proprietários das contas e diretórios criados automaticamente no Azure. Em seguida, podem gerir as contas através da implementação de soluções de integração de diretórios como o início de sessão único e a sincronização de palavras-passe. Em alternativa, podem impedir os utilizadores de criarem contas ou de se inscreverem no RMS para indivíduos.
    
    Para obter mais informações, consulte [Como os administradores podem controlar as contas criadas para o RMS para indivíduos](rms-for-individuals-take-control.md).

- **Gerir a Gestão de Direitos**: os administradores de TI podem converter a subscrição do RMS para indivíduos da organização numa subscrição paga que inclui o Azure Rights Management. Ao fazê-lo, as contas e o diretório do Azure existentes são preservadas para uma transição sem problemas para utilizadores existentes que estavam a utilizar o RMS para indivíduos. Todos os ficheiros que os utilizadores protegeram anteriormente ainda estão protegidos com as mesmas políticas e as pessoas que foram concedidas permissões para utilizar os ficheiros ainda podem utilizar os ficheiros da mesma forma.
    
    Ao realizar este procedimento, a sua organização é beneficiada por poder integrar a Gestão de Direitos nos seus fluxos de trabalho, serviços e arquivos de dados. Além disso, já pode gerir a Gestão de Direitos porque tem controlo sobre a chave de inquilino da sua organização para o Azure Rights Management. Agora, pode realizar as seguintes ações:
    
    - Configurar o Exchange e SharePoint para suportar o Azure Rights Management, mesmo que estes serviços estão em execução no local. O Exchange e o SharePoint são nativamente suportados para os serviços online e são suportados por um conetor para os servidores no local. Para obter mais informações, consulte o seguinte:
    
        - As secções do Exchange Online e do SharePoint Online de [Office 365: configuração para os clientes e os serviços online](../deploy-use/configure-office365.md)
        
        - [Implementar o conetor Azure Rights Management](../deploy-use/deploy-rms-connector.md)
        
    - Efetuar deteção eletrónica de dados pertencentes à empresa para que o que os utilizadores autorizados e serviços podem, se necessário, desencriptar ficheiros que foram protegidos. Para obter mais informações, consulte [Configurar superutilizadores para o Azure Rights Management e serviços de deteção ou recuperação de dados](../deploy-use/configure-super-users.md).
    
    - Atividade de registo para o serviço Rights Management. O registo é extremamente útil porque não só pode monitorizar os ficheiros que estão a ser protegidos e quem está com êxito a aceder aos ficheiros protegidos, mas também pode identificar comportamentos potencialmente suspeitos de pessoas não autorizadas que está a tentar aceder aos ficheiros protegidos. Para obter mais informações, consulte [Registar e analisar a utilização do serviço Azure Rights Management](../deploy-use/log-analyze-usage.md).
    
    - Fornece aos utilizadores a capacidade de controlar e revogar os seus documentos protegidos, se estas funcionalidades são suportadas pela sua subscrição. Para obter mais informações, veja [Controlar e revogar os documentos](../rms-client/client-track-revoke.md) do [Guia do utilizador do Azure Information Protection](../rms-client/client-user-guide.md).
    
    - Implemente uma traga a sua própria solução de chave (BYOK), para que a chave de inquilino do Azure Information Protection é criada e gerida por si. Para obter mais informações, consulte [Planear e implementar a sua chave de inquilino do Azure Information Protection](../plan-design/plan-implement-tenant-key.md).


## <a name="next-steps"></a>Passos seguintes
Consulte [Como os administradores podem controlar as contas criadas para o RMS para indivíduos](rms-for-individuals-take-control.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
---
title: "Alterar permissões em ficheiros que foram protegidos pela Rights Management | Azure RMS"
description: "Se um ficheiro tiver sido protegido pela Rights Management, pode alterar as permissões voltando a protegê-lo e, em seguida, especificar todos os utilizadores que devem ter acesso à mesma e que permissões pretende conceder-lhes."
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 07/20/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 5ac121b3-d7a0-40e4-8fe7-90bf4cf796f1
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 51050497fe128d94e069d0ac010435bea5623af2
ms.openlocfilehash: 985d3d2f1151b50fcde8f8bb916e984e1de71b00


---

# Alterar permissões em ficheiros que tenham sido protegidos pela Rights Management

*Aplica-se a: Serviços de Gestão de Direitos do Active Directory, Azure Rights Management, Windows 10, Windows 7 com SP1, Windows 8, Windows 8.1*

Se um ficheiro tiver sido protegido pela Rights Management, pode alterar as permissões voltando a protegê-lo e, em seguida, especificar todos os utilizadores que devem ter acesso à mesma e que permissões pretende conceder-lhes.

> [!IMPORTANT]
> Não é uma alteração de incremento, mas uma substituição completa. Está, de fato, a proteger de novo o ficheiro com o conjunto completo de permissões que pretende.
> 
>  Por exemplo, se um ficheiro estiver protegido de forma a que apenas as pessoas no departamento de marketing possam abri-lo e pretender que as pessoas no departamento de vendas também consigam abri-lo, deve proteger novamente o ficheiro para que o departamento de vendas e o departamento de marketing possam abri-lo.
>
> Do mesmo modo, se quiser adicionar ou remover uma permissão, não é possível apenas especificar essa permissão para adicionar ou remover, tem de especificar todas as permissões que pretende que as pessoas tenham.

Se for o proprietário do ficheiro que pretende proteger novamente (por exemplo, se o tiver protegido originalmente utilizando a aplicação de partilha), terá automaticamente permissões para proteger de novo o ficheiro. Se não for o proprietário, poderá ou poderá não ter permissões para proteger novamente o ficheiro, consoante as permissões que o ficheiro protegido tenha atualmente. 

Por exemplo, se outra pessoa protegeu o ficheiro utilizando a aplicação de partilha Rights Management e a pessoa especificou um grupo ao qual pertence e **Coproprietário** como a permissão personalizada, será capaz de voltar a proteger o ficheiro. No entanto, se não especificou um nome ou um grupo ao que pertence ou se tiver selecionado **Revisor - Ver e Editar**, ou um modelo que não lhe permita remover permissões, não poderá voltar a proteger o ficheiro. A forma mais fácil para descobrir é tentar voltar a proteger o ficheiro.

Se quiser remover por completo todas as permissões de modo a que o ficheiro já não fique protegido completamente, veja o artigo [Remover a proteção de um ficheiro](sharing-app-remove-protection.md).

## Voltar a proteger um ficheiro no local

1.  No Explorador de Ficheiros, selecione um ficheiro a proteger. Clique com o botão direito do rato, selecione **Proteger com RMS** e, em seguida, selecione **Proteger no local**. Por exemplo:

    ![Opção de menu Proteger no local](../media/ADRMS_MSRMSApp_SP_CompanyDefined.png)

    > [!NOTE]
    > Se não vir a opção **Proteger com RMS**, é provável que a aplicação de partilha RMS não esteja instalada no seu computador ou que seja necessário reiniciar o computador para concluir a instalação. Para obter mais informações sobre como instalar a aplicação de partilha RMS, consulte [Transferir e instalar a aplicação de partilha Rights Management](install-sharing-app.md).

2.  Efetue uma das seguintes ações:

    -   Selecione um modelo de política: estas são permissões predefinidas que, normalmente, restringem o acesso e a utilização a pessoas na sua organização. Por exemplo, se o nome da sua organização for “Contoso, Lda.”, poderá ver **Contoso, Lda. – Apenas Visualização Confidencial**. Se for a primeira vez que protege um ficheiro neste computador, primeiro terá de selecionar **Proteção Definida pela Empresa** para transferir os modelos.

        Da próxima vez que clicar na opção **Proteger no local**, irá ver até 10 modelos à escolha. Se existirem mais de 10 modelos disponíveis e aquele que pretende não for apresentado, clique em **Proteção Definida pela Empresa** para transferir e ver todos os modelos.

        Quando seleciona um modelo de política, também pode proteger vários ficheiros e uma pasta. Quando seleciona uma pasta, todos os ficheiros nessa pasta são selecionados automaticamente para proteção, mas os novos ficheiros que criar nessa pasta não serão automaticamente protegidos.

    -   Selecione **Permissões Personalizadas**: escolha esta opção se os modelos não fornecerem o nível de proteção de que necessita ou se pretender definir explicitamente as opções de proteção. Especifique as opções que pretende para este ficheiro na [caixa de diálogo adicionar proteção](sharing-app-dialog-box.md) e, em seguida, clique em **Aplicar**.

3. Se não tiver permissões para proteger de novo o ficheiro, será apresentada a mensagem **Não é possível proteger conteúdo**, com o endereço de e-mail da pessoa que pretende contactar (o proprietário do documento) para que possa alterar as suas permissões.

    Se tiver permissões para proteger de novo o ficheiro, poderá ver de imediato uma caixa de diálogo a indicar que o ficheiro está a ser protegido e, em seguida, o foco regressa para o Explorador de Ficheiros. O ficheiro ou ficheiros selecionados estão agora protegidos com as suas alterações. 

> [!NOTE]
> Antes de poder proteger de novo o ficheiro, o RMS tem de confirmar primeiro que tem autorização para fazê-lo para este ficheiro. Para tal, verifique o seu nome de utilizador e palavra-passe. Em alguns casos, estas informações podem estar em cache e não lhe são pedidas as suas credenciais. Noutros casos, ser-lhe-á pedido que forneça as credenciais.
>
> Se a sua organização não utilizar o Azure Rights Management (Azure RMS) ou o AD RMS, pode candidatar-se a uma conta gratuita que aceitará as suas credenciais para que possa utilizar ficheiros protegidos por RMS:
>
> -   Para se candidatar a esta conta, clique na ligação para aderir ao [RMS para indivíduos](http://go.microsoft.com/fwlink/?LinkId=309469).
>
>     Quando se inscrever, utilize o seu endereço de e-mail da empresa em vez de um endereço de e-mail pessoal. Caso se esteja a inscrever porque recebeu um anexo protegido, utilize o mesmo endereço de e-mail que foi utilizado para lhe enviar a mensagem de e-mail.
> -   Para mais informações, consulte [RMS para indivíduos e Azure Rights Management](../understand-explore/rms-for-individuals.md).

## Voltar a proteger um ficheiro enviado por si por e-mail

Se pretende alterar as permissões de um ficheiro que enviou por e-mail:

- **Para permitir que mais pessoas leiam o ficheiro**: envie o ficheiro por e-mail de acordo com as instruções indicadas em [Proteger um ficheiro que partilhar por e-mail](sharing-app-protect-by-email.md).

- **Para alterar as permissões do ficheiro**: envie o ficheiro novamente por e-mail, de acordo com as instruções indicadas em [Proteger um ficheiro que partilhar por e-mail](sharing-app-protect-by-email.md) e escolha as novas permissões pretendidas. 

    Uma vez que não é possível remover as permissões anteriores no ficheiro enviado originalmente por e-mail, substitua-as por uma nova versão, considere revogar o ficheiro enviado anteriormente por e-mail, para que os destinatários já não consigam abrir essa versão do documento. A revogação é adequada se tiver de tornar as permissões mais restritivas (por exemplo, se pretende remover as pessoas que não devem ter acesso ao ficheiro ou pretende que não devem editá-lo).

    Para revogar um ficheiro que tenha enviado por e-mail, veja o artigo [Controlar e revogar os documentos](sharing-app-track-revoke.md).


## Exemplos e outras instruções
Para obter exemplos de como pode utilizar a aplicação de partilha Rights Management e instruções sobre como proceder, veja as secções seguintes do guia do utilizador da aplicação de partilha Rights Management:

-   [Exemplos de utilização da aplicação de partilha RMS](sharing-app-user-guide.md#examples-for-using-the-rms-sharing-application)

-   [O que pretende fazer?](sharing-app-user-guide.md#what-do-you-want-to-do)

## Consulte Também
[Guia do utilizador da aplicação de partilha Rights Management](sharing-app-user-guide.md)



<!--HONumber=Jul16_HO3-->



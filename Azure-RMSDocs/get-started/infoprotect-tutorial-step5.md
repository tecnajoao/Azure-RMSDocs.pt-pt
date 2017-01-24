---
title: "Passo 5 do tutorial de início rápido | Azure Information Protection"
description: "Passo 5 de um tutorial de introdução, com uma duração de aproximadamente 30 minutos, para experimentar rapidamente o Microsoft Azure Information Protection na sua organização."
keywords: 
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/22/2016
ms.topic: get-started-article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4e59a3b3-f0f4-4535-8b96-cac68303d855
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7068e0529409eb783f16bc207a17be27cd5d82a8
ms.openlocfilehash: 5e063b19eb6d4e1b389357155e1cbbb893add73d


---


# <a name="step-5-see-sharing-of-protected-files-in-action-and-track-your-document"></a>Passo 5: ver a partilha de ficheiros protegidos em ação e controlar o seu documento 

>*Aplica-se a: Azure Information Protection*

Para este passo final do tutorial, localize um documento do Word que já tenha criado e que irá enviar a um parceiro ou colega. Para este tutorial, é irrelevante o texto que de facto contém, mas é aconselhável que tenha algum texto para que possa mais facilmente confirmar que o destinatário autorizado o conseguiu ler.

Em seguida, está pronto para partilhar de forma segura este documento por e-mail. 

## <a name="to-safely-share-your-document-by-email"></a>Para partilhar de forma segura o seu documento por e-mail

1.  No Word, abra o documento. Verá que a etiqueta predefinida **Interno** volta a ser aplicada automaticamente. 

2.  No separador **Base**, no grupo **RMS**, clique em **Partilhar Protegido** e, em seguida, clique em **Partilhar Protegido** no menu:

    ![Passo 5 do tutorial de início rápido do Azure Information Protection – Partilhar Protegido](../media/share-protected-callout.png)

    Verá a caixa de diálogo **partilhar protegido**, semelhante a esta imagem:

    ![Passo 5 do tutorial de início rápido do Azure Information Protection – caixa de diálogo partilhar protegido](../media/example-share-protected-dialog.png)

3. Na caixa **UTILIZADORES**, escreva um ou mais endereços de e-mail empresariais, como faria ao enviar um documento a alguém com quem a sua organização trabalha. Em alternativa, pode especificar o endereço de e-mail de um colega. Certifique-se de que especifica um endereço de e-mail empresarial, tal como **janetm@contoso.com** ou **p.dover@fabrikam.com**, porque atualmente o Azure Information Protection não suporta endereços de e-mail pessoais. 

    Não se preocupe se a pessoa a quem está a enviar também tem ou não o Azure Information Protection.

4. Selecione **Visualizador – Ver Apenas**.

    Isto significa que os nossos destinatários poderão visualizar o documento, mas não o poderão editar nem imprimir.

5. Selecione **Enviar-me um e-mail quando alguém tentar abrir estes documentos**.

    Receberá uma notificação por e-mail sempre que os destinatários tentam abrir o anexo e também se outra pessoa tentar abri-lo, por exemplo, o destinatário reencaminha a mensagem de e-mail para um colega de trabalho. Se o documento for reencaminhado, verá que o acesso foi negado e, tendo em conta os detalhes do utilizador, pode decidir se envia uma cópia do documento que essa pessoa possa abrir.

6. Selecione **Revogar instantaneamente o acesso a estes documentos**.

    Esta opção requer que os destinatários tenham ligação à Internet sempre que abrem o anexo, mas com a vantagem que se revogar o documento mais tarde, da próxima vez que o tentarem abrir, não será possível. 

4.  Clique em **Enviar** para ver uma mensagem de e-mail que está pronta para ser enviada para os destinatários especificados e com texto predefinido para obter instruções. Por exemplo:

    ![Exemplo de uma mensagem de e-mail quando partilhar protegido](../media/example-email-share-protected.png)
    
    **NOTA**: se o Outlook estava aberto quando instalou o cliente do Azure Information Protection, não verá a barra Information Protection que vê na imagem anterior: não é utilizada especificamente neste passo que demonstra a partilha de documentos protegidos, pelo que não precisa de fechar e reabrir o Outlook para concluir o tutorial. Se tiver aberto o Outlook depois de instalar o cliente do Azure Information Protection, verá que esta mensagem de e-mail, tal como o documento do Word quando foi aberto pela primeira vez, tem a etiqueta **Interno** aplicada por predefinição, como resultado da configuração desta definição global na política do Azure Information Protection.
    
    Poderá reparar que tem dois anexos; o documento do Word original e um ficheiro que tem o mesmo nome mas uma extensão de nome de ficheiro **.ppdf**. A versão .ppdf é um ficheiro PDF protegido criado automaticamente pela aplicação de partilha Rights Management, caso o destinatário não tenha uma versão do Office que suporte documentos protegidos. Este ficheiro adicional permite ao destinatário ler o documento protegido ao utilizar o visualizador que é instalado com a aplicação de partilha Rights Management.

    Clique em **Enviar** na sua mensagem de e-mail.

Agora que enviou o documento protegido, pode pedir aos destinatários para o abrirem assim que o receberem. No entanto, não feche o Word, pois utilizá-lo-emos novamente no procedimento final para controlar o documento partilhado.

## <a name="ask-your-recipients-to-open-the-emailed-document"></a>Pedir aos destinatários para abrir o documento enviado por e-mail

Os destinatários podem utilizar vários dispositivos para ler o documento protegido que enviou como anexo de e-mail. Os dispositivos incluem iPads, iPhones, tablets e telemóveis Android, computadores Mac, bem como computadores Windows.

Peça-lhes para lerem a mensagem de e-mail que enviou. Partindo do princípio que esta é a primeira vez que receberam anexos protegidos pelo Rights Management, peça-lhes para clicarem na ligação de instruções. Em seguida, verão a página [Bem-vindo ao Microsoft RMS!](https://portal.azurerms.com/#/rmshelp) com instruções para instalarem a aplicação de partilha RMS e, se necessário, para se inscreverem numa conta gratuita. Estarão assim preparados para ler o anexo protegido.

### <a name="instructions-for-recipient-to-view-the-protected-document-attachment"></a>Instruções para o destinatário: para ver o anexo do documento protegido

1. Abra um dos anexos para ler o documento:
    
    - Se tiver uma versão do Office no seu dispositivo que suporte o Rights Management:
    
        -  Abra o documento que tem a extensão de nome de ficheiro**.docx**.
        
    - Se não tiver uma versão do Office que suporte o Rights Management, não tiver a certeza ou simplesmente quiser experimentar o visualizador da aplicação de partilha Rights Management: 
    
        - Abra o documento que tem uma extensão de nome de ficheiro**.ppdf**.

2.  Se lhe for pedido o nome de utilizador e a palavra-passe, introduza o nome de utilizador no mesmo formato que o endereço de e-mail que foi utilizado para lhe enviar a mensagem de e-mail e o anexo. Por exemplo, **janetm@contoso.com** ou **p.dover@fabrikam.com**. Para a palavra-passe, escreva a que especificou quando se inscreveu no RMS para indivíduos. Em alternativa, se a sua organização tiver um serviço em nuvem como o Office 365 ou utilizar o Azure, introduza a palavra-passe profissional habitual.

3. Leia os conteúdos do documento quando este for aberto. Uma vez que é só de leitura, não é possível alterar os conteúdos.

Como passo opcional, o destinatário pode reencaminhar o e-mail para outras pessoas que não tenha especificado no e-mail original. Estas pessoas não poderão abrir o anexo. Quando lhes for solicitado o respetivo nome de utilizador, o acesso ao documento será negado.

Agora que o destinatário abriu o anexo e, opcionalmente, o reencaminhou para outra pessoa, aguarde a receção de uma notificação de e-mail a comunicar esta atividade. No entanto, é fácil perder mensagens de e-mail ao longo do tempo. Como tal, para melhor controlar quem acede ao documento, utilize o site de controlo de documentos, o qual é descrito no último procedimento.

## <a name="to-track-your-protected-document"></a>Para controlar o documento protegido

1.  De volta ao Word, no separador **Base**, no grupo **RMS**, clique em **Partilhar Protegido** e, em seguida, clique em **Controlar Utilização** no menu:

    ![Opção Controlar Utilização](../media/track-usage-callout.png)

    Isto leva-o para o site de controlo de documentos.

2.  Se vir a página **Proteção e partilha à sua medida**, clique em **Iniciar sessão** e indique novamente o nome de utilizador e a palavra-passe.

3.  Na página **Documentos partilhados**, irá ver o nome do documento que partilhou. Neste momento, é o único ficheiro apresentado, mas à medida que partilhar mais documentos protegidos, a lista aumenta.

    Nesta página, verá quando partilhou o documento (quando enviou a mensagem de e-mail com o anexo protegido), a data da última atividade e o nome do destinatário a quem enviou a mensagem de e-mail. Clique no nome do documento para obter mais detalhes.

4.  Na nova página, que tem o nome do ficheiro em que clicou, poderá ver detalhes do resumo apenas desse documento, bem como uma lista de outras opções que estão disponíveis para o documento (**Lista**, **Linha Cronológica**, **Mapa**, **Definições**).

    Clique em cada opção para explorar formas diferentes de controlar o documento protegido. Em alternativa, ainda na página **Resumo**, clique em **Abrir no Excel** para exportar as informações para uma folha de cálculo ou clique em **Revogar acesso** para deixar de partilhar o documento.

Pode voltar a este site para controlar mais atividades do documento protegido ou revogar o acesso, se necessário. Pode, inclusive, aceder ao site a partir do dispositivo móvel ou tablet, utilizando um browser com esta ligação: [controlo de documentos](http://go.microsoft.com/fwlink/?LinkId=529562)



|Se pretender mais informações|Informações adicionais|
|--------------------------------|--------------------------|
|Instruções completas e métodos alternativos para proteger ficheiros que partilha por e-mail|[Proteger um ficheiro que partilha por e-mail ao utilizar a aplicação de partilha Rights Management](../rms-client/sharing-app-protect-by-email.md)|
|Acerca das opções na caixa de diálogo **partilhar protegido**|[Opções da caixa de diálogo da aplicação de partilha Rights Management](../rms-client/sharing-app-dialog-box.md)|
|Acerca da conta gratuita para outros utilizadores se inscreverem|[RMS para utilizadores individuais e Azure Rights Management](../understand-explore/rms-for-individuals.md)|
|Acerca da utilização do site de controlo de documentos|[Controlar e revogar os documentos](../rms-client/sharing-app-track-revoke.md)


## <a name="next-steps"></a>Passos Seguintes

Agora que viu a política predefinida do Azure Information Protection, como personalizá-la e como funciona a etiquetagem para um documento do Word, experimente algumas das outras definições e saiba como funcionam nas outras aplicações do Office que suportam o Azure Information Protection: Excel, PowerPoint, Outlook. Se estas aplicações tiverem sido abertas quando instalou o cliente do Azure Information Protection, feche-as e volte a abri-las antes de tentar utilizá-las com o Azure Information Protection.

Experimente partilhar mais documentos e controlar a forma como estão a ser utilizados, e confirme como funciona a revogação de documentos.

Poderá ser-lhe útil ler algumas das [perguntas mais frequentes](faqs.md) do Azure Information Protection e explorar alguns dos outros artigos da documentação. No entanto, se estiver pronto para iniciar a implementação do Azure Information Protection para a sua organização, o passo seguinte deverá ser o [plano de implementação do Azure Information Protection](../plan-design/deployment-roadmap.md). 

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


<!--HONumber=Jan17_HO4-->


